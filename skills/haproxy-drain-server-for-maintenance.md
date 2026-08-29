---
name: haproxy-drain-server-for-maintenance
description: >-
  Take a server out of rotation for maintenance and put it back, using the HAProxy Runtime
  API surface so the change is immediate and does not rewrite the configuration file.
api: HAProxy Data Plane API
generated: '2026-08-28'
method: generated
source: openapi/haproxy-data-plane-api-openapi.yml
operations:
  - getRuntimeServer
  - replaceRuntimeServer
  - getStats
  - getHaproxyProcessInfo
---

# Drain a server, then bring it back

Runtime changes apply immediately and are **not** transactional. There is no rollback
operation — the only reversal is the opposite call — so read the current state first and
record it before you change anything.

## Steps

1. **Read the server's current runtime state.**
   `GET /services/haproxy/runtime/backends/{parent_name}/servers/{name}` (`getRuntimeServer`).
   Record the admin state and the weight. This recorded value IS your rollback plan.

2. **Drain it.** `PUT /services/haproxy/runtime/backends/{parent_name}/servers/{name}`
   (`replaceRuntimeServer`) with the admin state set to `drain`. Draining stops new sessions
   from being assigned while letting existing ones finish, which is what you want before
   maintenance. Setting `maint` instead cuts it off immediately.

3. **Wait for connections to drain.** `GET /services/haproxy/stats/native` (`getStats`) and
   watch the current-session counter for that server fall to zero. Do not skip this — the
   point of `drain` over `maint` is precisely this wait.

4. **Do the maintenance.**

5. **Bring it back.** `replaceRuntimeServer` again with the admin state set to `ready` and the
   weight restored to the value recorded in step 1. Do not assume the weight was the default;
   weighted pools are common and guessing here silently reshapes traffic.

6. **Confirm.** `getRuntimeServer` to check the state, then `getStats` to confirm it is
   receiving traffic and passing health checks.

## Rules

- Runtime state does not survive an HAProxy restart. A server left in `maint` at runtime comes
  back `ready` after a restart unless the configuration says otherwise. If the server must
  stay out across restarts, make the change in the configuration instead
  (`replaceServerBackend`, under a version or a transaction).
- These operations are not reversible by the API. Capture the prior state before mutating.
- `GET /services/haproxy/runtime/info` (`getHaproxyProcessInfo`) confirms which process you
  are actually talking to — worth checking before a destructive change on a multi-instance host.
