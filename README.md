# HAProxy (haproxy)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

HAProxy is a free, very fast and reliable reverse-proxy offering high availability, load balancing, and proxying for TCP and HTTP-based applications. It exposes a Data Plane API for dynamic configuration management and a stats socket for runtime management.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/haproxy/refs/heads/main/apis.yml)

## Scope

- **Type:** Index 
- **Position:** Consuming 
- **Access:** 3rd-Party 

## Tags:

 - Load Balancing, Reverse Proxy, High Availability, Networking

## Timestamps

- **Created:** 2026-03-16 
- **Modified:** 2026-03-18 

## APIs

### HAProxy Data Plane API
The HAProxy Data Plane API is a REST API for managing HAProxy configuration dynamically. It allows runtime configuration of frontends, backends, servers, ACLs, and other HAProxy objects without requiring configuration file changes or restarts.

**Human URL:** [https://www.haproxy.com/documentation/dataplaneapi/latest/](https://www.haproxy.com/documentation/dataplaneapi/latest/)


#### Tags:

 - Load Balancing, Configuration, REST API

#### Properties

- [Documentation](https://www.haproxy.com/documentation/dataplaneapi/latest/)
- [OpenAPI](https://raw.githubusercontent.com/haproxytech/dataplaneapi/master/swagger.yaml)
- [Getting Started](https://www.haproxy.com/documentation/dataplaneapi/latest/#getting-started)
- [GitHubRepository](https://github.com/haproxytech/dataplaneapi)
- [Change Log](https://github.com/haproxytech/dataplaneapi/releases)

### HAProxy Runtime API
The HAProxy Runtime API (formerly known as the stats socket) is a socket-based interface for dynamically managing HAProxy at runtime. It allows operators to enable or disable servers, adjust weights, inspect stick tables, view statistics, and perform other live configuration changes without reloading the process.

**Human URL:** [https://www.haproxy.com/documentation/haproxy-runtime-api/](https://www.haproxy.com/documentation/haproxy-runtime-api/)


#### Tags:

 - Load Balancing, Runtime Management, Statistics

#### Properties

- [Documentation](https://www.haproxy.com/documentation/haproxy-runtime-api/)
- [Reference](https://www.haproxy.com/documentation/haproxy-runtime-api/reference/)

### HAProxy Kubernetes Ingress Controller
The HAProxy Kubernetes Ingress Controller implements routing rules defined in Kubernetes Ingress resources, dynamically updating HAProxy configuration as pods are added or removed from the cluster. It supports the Gateway API, custom resources, and certificate management via the HAProxy Runtime API.

**Human URL:** [https://www.haproxy.com/documentation/kubernetes-ingress/](https://www.haproxy.com/documentation/kubernetes-ingress/)


#### Tags:

 - Kubernetes, Ingress Controller, Load Balancing

#### Properties

- [Documentation](https://www.haproxy.com/documentation/kubernetes-ingress/)
- [Getting Started](https://www.haproxy.com/documentation/kubernetes-ingress/overview/)
- [Change Log](https://www.haproxy.com/documentation/kubernetes-ingress/community/release-notes/)
- [GitHubRepository](https://github.com/haproxytech/kubernetes-ingress)

## Common Properties

- [Website](https://www.haproxy.org/)
- [Documentation](https://docs.haproxy.org/)
- [GitHub Organization](https://github.com/haproxy)
- [GitHub Organization](https://github.com/haproxytech)
- [Community](https://discourse.haproxy.org/)
- [Blog](https://www.haproxy.com/blog/)
- [Support](https://www.haproxy.com/support/support-options)
- [Terms of Service](https://www.haproxy.com/legal)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
