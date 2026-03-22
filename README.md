# HAProxy (haproxy)
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
