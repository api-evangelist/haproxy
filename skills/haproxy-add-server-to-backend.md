---
name: haproxy-add-server-to-backend
description: >-
  Add a server to an HAProxy backend through the Data Plane API without losing a concurrent
  change and without leaving the configuration half-applied.
api: HAProxy Data Plane API
generated: '2026-08-28'
method: generated
source: openapi/haproxy-data-plane-api-openapi.yml
operations:
  - getConfigurationVersion
  - getBackends
  - getAllServerBackend
  - createServerBackend
  - getReload
---

# Add a server to a backend

Base URL `http://{haproxy-host}:5555/v3`. Every call uses HTTP Basic auth
(`--user <user>:<pass>`) against the userlist the Data Plane API was started with.

## Steps

1. **Confirm the backend exists.** `GET /services/haproxy/configuration/backends`
   (`getBackends`) and check the name is present. If you already know it,
   `GET /services/haproxy/configuration/backends/{name}` (`getBackend`) is cheaper.
   A missing backend returns 404 — create it first rather than letting the server create
   fail confusingly.

2. **List what is already there.**
   `GET /services/haproxy/configuration/backends/{parent_name}/servers`
   (`getAllServerBackend`). Server names must be unique inside the backend; adding a
   duplicate returns 409.

3. **Read the current configuration version.**
   `GET /services/haproxy/configuration/version` (`getConfigurationVersion`). Do this
   immediately before the write. The value is a plain integer.

4. **Create the server.**
   `POST /services/haproxy/configuration/backends/{parent_name}/servers?version={version}`
   (`createServerBackend`) with the server body — at minimum `name` and `address`, usually
   `port` and `check`.

5. **Handle the response.**
   - `201` — created and applied.
   - `202` — accepted, and a reload was requested. Read the `Reload-ID` response header and
     poll `GET /services/haproxy/reloads/{id}` (`getReload`) until it reports finished. Do
     not report success on the 202 alone.
   - `409` — either the name already exists, or your `version` was stale because something
     else changed the configuration in between. Read the `Configuration-Version` response
     header, and go back to step 3 with the fresh value. Never retry with the same version.
   - `400` — the body failed validation against the `server` definition.

## Rules

- Do not send `version` and `transaction_id` together; the API rejects the combination.
- If you are adding several servers, use the transaction skill instead — a per-call version
  loop will fight itself and you will collect 409s.
- `force_reload=true` bypasses the configured reload-delay. Use it only when the change must
  be live immediately; it costs a reload that HAProxy would otherwise have batched.
- To add a server without touching the configuration file at all — for autoscaling, where the
  slot is expected to disappear again — use the Runtime API surface under
  `/services/haproxy/runtime/backends/{parent_name}/servers` instead. Runtime changes are not
  written to the configuration and do not survive a restart.
