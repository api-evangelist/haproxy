---
name: haproxy-transactional-config-change
description: >-
  Stage several HAProxy configuration changes as one unit and either commit them together
  or roll them all back, using the Data Plane API transaction lifecycle.
api: HAProxy Data Plane API
generated: '2026-08-28'
method: generated
source: openapi/haproxy-data-plane-api-openapi.yml
operations:
  - getConfigurationVersion
  - startTransaction
  - getTransaction
  - getTransactions
  - commitTransaction
  - deleteTransaction
  - createBackend
  - createServerBackend
  - createFrontend
  - createBindFrontend
  - createBackendSwitchingRule
---

# Make several changes atomically

This is the only reversible write path in the API. Use it whenever a change needs more than
one call — a new backend plus its servers, or a frontend plus its bind plus its routing rule.
Anything staged in a transaction can be thrown away in full until you commit.

## Steps

1. **Read the current version.** `GET /services/haproxy/configuration/version`
   (`getConfigurationVersion`).

2. **Open the transaction.** `POST /services/haproxy/transactions?version={version}`
   (`startTransaction`). The response carries the transaction `id`. Hold on to it — if you
   lose it you cannot commit or cleanly discard, and abandoned transactions eventually
   produce `429 Too many open transactions` for everyone.

3. **Make the changes, passing `transaction_id` instead of `version`.** The individual calls
   carry no version of their own — the transaction holds it. For example:
   - `POST /services/haproxy/configuration/backends?transaction_id={id}` (`createBackend`)
   - `POST /services/haproxy/configuration/backends/{parent_name}/servers?transaction_id={id}`
     (`createServerBackend`)
   - `POST /services/haproxy/configuration/frontends?transaction_id={id}` (`createFrontend`)
   - `POST /services/haproxy/configuration/frontends/{parent_name}/binds?transaction_id={id}`
     (`createBindFrontend`)
   - `POST /services/haproxy/configuration/frontends/{parent_name}/backend_switching_rules/{index}?transaction_id={id}`
     (`createBackendSwitchingRule`)

4. **Inspect before committing.** `GET /services/haproxy/transactions/{id}` (`getTransaction`)
   shows the transaction's state. This is the closest thing the API has to a dry run: you can
   apply everything, look at it, and still walk away.

5. **Decide.**
   - Commit: `PUT /services/haproxy/transactions/{id}` (`commitTransaction`). This is the
     point of no return — there is no undo operation afterwards.
   - Roll back: `DELETE /services/haproxy/transactions/{id}` (`deleteTransaction`). Every
     staged change is discarded and the running configuration is untouched.

## Rules

- **Always resolve the transaction.** On any error path, on any abort, on any timeout — call
  `deleteTransaction`. Leaking transactions is how a fleet ends up returning 429.
- `getTransactions` lists what is currently open. Use it to find and clean up strays.
- After a commit, reversing means issuing the inverse writes yourself. Plan the rollback
  before you commit, not after.
- `force_reload` cannot be combined with `transaction_id`.
- SPOE files have their own parallel transaction lifecycle under
  `/services/haproxy/spoe/spoe_files/{parent_name}/transactions` — same discipline, separate
  operations (`startSpoeTransaction`, `commitSpoeTransaction`, `deleteSpoeTransaction`).
