---
name: haproxy-inspect-load-balancer-state
description: >-
  Read-only inspection of a running HAProxy instance — process information, statistics, the
  live configuration and the API contract itself.
api: HAProxy Data Plane API
generated: '2026-08-28'
method: generated
source: openapi/haproxy-data-plane-api-openapi.yml
operations:
  - getInfo
  - getHaproxyProcessInfo
  - getStats
  - getStatsEndpoints
  - getBackends
  - getFrontends
  - getConfigurationVersion
  - getSpecification
  - getOpenapiv3Specification
  - getHealth
---

# Inspect a running instance

Every operation here is a GET and none of them changes anything. This is the safe first move
for an agent that has just been pointed at an HAProxy instance it does not know.

## Steps

1. **Check the API is up.** `GET /health` (`getHealth`).

2. **Identify what you are talking to.** `GET /info` (`getInfo`) returns Data Plane API and
   system information. `GET /services/haproxy/runtime/info` (`getHaproxyProcessInfo`) returns
   the HAProxy process itself — version, uptime, pid, connection counters.

3. **Learn the API you actually have.** `GET /specification` (`getSpecification`) returns the
   running instance's own Swagger 2.0 contract, and `GET /specification_openapiv3`
   (`getOpenapiv3Specification`) returns an OpenAPI 3 rendering of it. Prefer these over any
   cached copy: they describe the version in front of you, which may not be 3.4.

4. **Map the traffic path.** `GET /services/haproxy/configuration/frontends` (`getFrontends`)
   for entry points, then `GET /services/haproxy/configuration/backends` (`getBackends`) for
   the pools, then the servers under each backend
   (`GET /services/haproxy/configuration/backends/{parent_name}/servers`).

5. **Read the numbers.** `GET /services/haproxy/stats` (`getStatsEndpoints`) lists what is
   available; `GET /services/haproxy/stats/native` (`getStats`) returns per-process,
   per-frontend, per-backend and per-server counters.

6. **Note the version.** `GET /services/haproxy/configuration/version`
   (`getConfigurationVersion`). Even on a read-only pass, capturing this tells you whether the
   configuration shifted under you between calls.

## Rules

- Collections are returned whole. There is no pagination anywhere in this API, so a large
  configuration means a large response — budget for it rather than looking for a page parameter.
- Configuration reads and runtime reads are different views of the same objects. The
  configuration is what is written down; `/services/haproxy/runtime/*` is what is currently
  true. They diverge whenever someone has made a runtime-only change.
