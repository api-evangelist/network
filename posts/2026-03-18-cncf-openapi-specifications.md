# Mapping the APIs of Cloud Native Computing: A CNCF OpenAPI Inventory

The Cloud Native Computing Foundation (CNCF) is home to some of the most critical infrastructure powering the modern internet — from Kubernetes and Prometheus to Dapr, Istio, and beyond. But for all the innovation happening across these projects, one thing has been consistently missing: machine-readable API definitions that make it easy to integrate, govern, and understand what these APIs actually do.

Over the past week I've been systematically cataloging every CNCF project hosted under the [api-evangelist GitHub organization](https://github.com/api-evangelist) — cloning repos, updating apis.yml indexes, generating OpenAPI specifications, AsyncAPI event schemas, JSON Schemas, and JSON-LD context files for each one. The result is a comprehensive, structured inventory of the APIs that underpin cloud native computing.

Below is a snapshot of every CNCF project that now has OpenAPI specifications, with direct links to each file. This is a living catalog — if you see gaps, inaccuracies, or want to contribute, PRs are welcome.

---

## CNCF Services with OpenAPI Specifications

### [Cilium](https://github.com/api-evangelist/cilium)

Cilium is an open source networking and security project that uses eBPF to provide high-performance networking, observability, and security for Kubernetes workloads. It operates at the kernel level to enforce network policies, load balance traffic, and provide deep visibility into network flows without modifying application code.

- [cilium-api-openapi.yml](https://github.com/api-evangelist/cilium/blob/main/openapi/cilium-api-openapi.yml) — The Cilium REST API provides access to the Cilium daemon and agent endpoints for managing Kubernetes network policy, security, and connectivity.

### [Kubernetes](https://github.com/api-evangelist/kubernetes)

Kubernetes is the de facto standard for container orchestration, providing automated deployment, scaling, and management of containerized applications. It groups containers into logical units called Pods and manages their lifecycle across a cluster of machines through a declarative API.

- [kubernetes-api-openapi.yml](https://github.com/api-evangelist/kubernetes/blob/main/openapi/kubernetes-api-openapi.yml) — The Kubernetes API lets you query and manipulate the state of objects in Kubernetes. The core of the control plane is the API server and the HTTP API.

### [Kubernetes Services](https://github.com/api-evangelist/kubernetes-services)

Kubernetes Services is a collection of networking APIs that handle how traffic flows into, out of, and between workloads in a cluster. It covers Services, Ingress, NetworkPolicies, EndpointSlices, and the newer Gateway API — the building blocks for everything from internal service discovery to external load balancing.

- [kubernetes-services-openapi.yml](https://github.com/api-evangelist/kubernetes-services/blob/main/openapi/kubernetes-services-openapi.yml) — The Kubernetes Services API provides an abstraction for exposing groups of Pods over a network with a stable virtual IP address and DNS name.
- [kubernetes-ingress-openapi.yml](https://github.com/api-evangelist/kubernetes-services/blob/main/openapi/kubernetes-ingress-openapi.yml) — The Kubernetes Ingress API manages external HTTP and HTTPS access to services within a cluster, providing load balancing, SSL/TLS termination, and name-based virtual hosting.
- [kubernetes-network-policies-openapi.yml](https://github.com/api-evangelist/kubernetes-services/blob/main/openapi/kubernetes-network-policies-openapi.yml) — The Kubernetes NetworkPolicy API controls how groups of Pods communicate with each other and with external network endpoints.
- [kubernetes-endpoint-slices-openapi.yml](https://github.com/api-evangelist/kubernetes-services/blob/main/openapi/kubernetes-endpoint-slices-openapi.yml) — The Kubernetes EndpointSlices API tracks the IP addresses, ports, readiness, and topology information for Pods backing a Service.
- [kubernetes-gateway-api-openapi.yml](https://github.com/api-evangelist/kubernetes-services/blob/main/openapi/kubernetes-gateway-api-openapi.yml) — The Kubernetes Gateway API is a role-oriented, extensible API for managing ingress and mesh traffic routing in Kubernetes clusters.

### [Kubernetes Operators](https://github.com/api-evangelist/kubernetes-operators)

Kubernetes Operators extend the Kubernetes API to manage complex, stateful applications using the same declarative model as native Kubernetes resources. This collection covers CustomResourceDefinitions (CRDs) and the Operator Lifecycle Manager (OLM), which together form the foundation for the operator ecosystem on Kubernetes.

- [kubernetes-crd-openapi.yml](https://github.com/api-evangelist/kubernetes-operators/blob/main/openapi/kubernetes-crd-openapi.yml) — The CustomResourceDefinition (CRD) API extends the Kubernetes API by defining new resource types with custom schemas.
- [kubernetes-olm-openapi.yml](https://github.com/api-evangelist/kubernetes-operators/blob/main/openapi/kubernetes-olm-openapi.yml) — The Operator Lifecycle Manager (OLM) extends Kubernetes with a declarative API for installing, upgrading, and managing the lifecycle of Operators and their dependencies in a cluster.

### [Helm](https://github.com/api-evangelist/helm)

Helm is the package manager for Kubernetes, allowing users to define, install, and upgrade complex Kubernetes applications using reusable, versioned packages called charts. It provides templating, dependency management, and release lifecycle management for Kubernetes workloads.

- [helm-chart-repository-openapi.yml](https://github.com/api-evangelist/helm/blob/main/openapi/helm-chart-repository-openapi.yml) — The Helm Chart Repository API defines the HTTP endpoints used by Helm clients to discover and download charts from a repository server.

### [Prometheus](https://github.com/api-evangelist/prometheus)

Prometheus is the standard for metrics-based monitoring in cloud native environments. It scrapes metrics from instrumented targets, stores them in a time-series database, and provides a powerful query language (PromQL) for analysis and alerting. The Prometheus ecosystem includes Alertmanager and Pushgateway as companion services.

- [prometheus-http-api-openapi.yml](https://github.com/api-evangelist/prometheus/blob/main/openapi/prometheus-http-api-openapi.yml) — The Prometheus HTTP API provides endpoints for executing instant and range queries using PromQL, querying metadata such as label names, label values, and series.
- [prometheus-management-api-openapi.yml](https://github.com/api-evangelist/prometheus/blob/main/openapi/prometheus-management-api-openapi.yml) — The Prometheus Management API provides administrative endpoints for managing a running Prometheus server, including configuration reloads and TSDB snapshots.
- [prometheus-pushgateway-api-openapi.yml](https://github.com/api-evangelist/prometheus/blob/main/openapi/prometheus-pushgateway-api-openapi.yml) — The Prometheus Pushgateway API accepts metrics pushed from short-lived batch jobs and ephemeral processes that cannot be scraped by Prometheus directly.
- [prometheus-alertmanager-api-openapi.yml](https://github.com/api-evangelist/prometheus/blob/main/openapi/prometheus-alertmanager-api-openapi.yml) — The Prometheus Alertmanager HTTP API v2 provides endpoints for querying active alert status, creating and managing silences, and retrieving receiver configurations.

### [Envoy](https://github.com/api-evangelist/envoy)

Envoy is a high-performance, programmable proxy designed for cloud native applications. Originally built at Lyft, it has become the data plane of choice for service meshes and API gateways. It supports advanced load balancing, observability, and protocol translation, and now powers an AI Gateway for routing traffic to generative AI backends.

- [envoy-admin-api-openapi.yml](https://github.com/api-evangelist/envoy/blob/main/openapi/envoy-admin-api-openapi.yml) — The Envoy Admin API provides local administrative access to a running Envoy proxy instance, exposing endpoints for inspecting configuration and checking health.
- [envoy-ai-gateway-openapi.yml](https://github.com/api-evangelist/envoy/blob/main/openapi/envoy-ai-gateway-openapi.yml) — The Envoy AI Gateway provides a unified proxy layer for accessing Generative AI services built on top of Envoy Gateway, exposing OpenAI-compatible endpoints.

### [Envoy Proxy](https://github.com/api-evangelist/envoy-proxy)

Envoy Proxy is the runtime component of Envoy that processes traffic according to dynamically delivered configuration. It exposes an administration interface for runtime inspection and the xDS (Discovery Service) APIs that allow control planes to push routing, cluster, listener, and endpoint configuration dynamically without restarting the proxy.

- [envoy-proxy-admin-api-openapi.yml](https://github.com/api-evangelist/envoy-proxy/blob/main/openapi/envoy-proxy-admin-api-openapi.yml) — The Envoy Proxy Administration Interface provides a local HTTP-based management API for querying and modifying various aspects of the Envoy server at runtime.
- [envoy-proxy-xds-discovery-api-openapi.yml](https://github.com/api-evangelist/envoy-proxy/blob/main/openapi/envoy-proxy-xds-discovery-api-openapi.yml) — The Envoy xDS (x Discovery Service) REST API provides endpoints for dynamically discovering and configuring Envoy proxy resources.

### [Jaeger](https://github.com/api-evangelist/jaeger)

Jaeger is an end-to-end distributed tracing system originally developed at Uber. It helps engineers monitor and troubleshoot complex microservices architectures by capturing and visualizing the full lifecycle of requests as they propagate across services, making latency bottlenecks and failure points visible.

- [jaeger-query-api.yml](https://github.com/api-evangelist/jaeger/blob/main/openapi/jaeger-query-api.yml) — The Jaeger Query API provides HTTP endpoints for retrieving trace data, service information, operations, and dependency graphs from the Jaeger distributed tracing backend.

### [Fluentd](https://github.com/api-evangelist/fluentd)

Fluentd is an open source data collector that provides a unified logging layer for cloud native environments. It decouples data collection from data consumption by acting as a central aggregation point that can accept logs from many sources and route them to many destinations through a pluggable architecture.

- [fluentd-http-input-openapi.yml](https://github.com/api-evangelist/fluentd/blob/main/openapi/fluentd-http-input-openapi.yml) — The Fluentd HTTP Input plugin exposes an HTTP endpoint that accepts log records posted as JSON, MessagePack, or form-encoded data.

### [Linkerd](https://github.com/api-evangelist/linkerd)

Linkerd is an ultralight, security-first service mesh for Kubernetes. It adds mutual TLS, observability, and traffic management to services transparently without requiring application changes. Its focus on simplicity and low resource overhead has made it a popular alternative to heavier service mesh implementations.

- [linkerd-proxy-admin-openapi.yml](https://github.com/api-evangelist/linkerd/blob/main/openapi/linkerd-proxy-admin-openapi.yml) — The Linkerd proxy exposes an admin HTTP server on each meshed pod, providing health check endpoints, readiness probes, and Prometheus-compatible metrics.
- [linkerd-tap-openapi.yml](https://github.com/api-evangelist/linkerd/blob/main/openapi/linkerd-tap-openapi.yml) — The Linkerd Tap API is a Kubernetes aggregated API server that provides real-time streaming access to requests flowing through the Linkerd service mesh.
- [linkerd-viz-metrics-openapi.yml](https://github.com/api-evangelist/linkerd/blob/main/openapi/linkerd-viz-metrics-openapi.yml) — The Linkerd Viz extension provides a metrics API that powers the linkerd viz CLI commands and the Linkerd dashboard.

### [CoreDNS](https://github.com/api-evangelist/coredns)

CoreDNS is the default DNS server for Kubernetes, responsible for service discovery within the cluster. It is built on a plugin-based architecture that allows it to serve DNS, health checks, metrics, and other capabilities through a composable chain of middleware.

- [coredns-health-openapi.yml](https://github.com/api-evangelist/coredns/blob/main/openapi/coredns-health-openapi.yml) — The CoreDNS health plugin exposes an HTTP health check endpoint reporting the overall health of the CoreDNS process.
- [coredns-metrics-openapi.yml](https://github.com/api-evangelist/coredns/blob/main/openapi/coredns-metrics-openapi.yml) — The CoreDNS prometheus plugin exposes a Prometheus-compatible metrics endpoint providing DNS request counters and latency histograms.

### [Containerd](https://github.com/api-evangelist/containerd)

Containerd is the industry-standard container runtime used by Kubernetes and many other platforms. It manages the full container lifecycle — image pulls, storage, networking, and execution — through a stable, gRPC-based API, and exposes Prometheus metrics for runtime observability.

- [containerd-metrics-openapi.yml](https://github.com/api-evangelist/containerd/blob/main/openapi/containerd-metrics-openapi.yml) — The containerd metrics plugin exposes a Prometheus-compatible HTTP endpoint for scraping runtime metrics.

### [Argo](https://github.com/api-evangelist/argo)

Argo is a suite of Kubernetes-native tools for running workflows, managing GitOps deployments, and handling progressive delivery. Argo CD brings declarative GitOps continuous delivery, while Argo Workflows provides a DAG-based workflow engine for data pipelines, CI, and batch processing.

- [argo-cd-openapi.yml](https://github.com/api-evangelist/argo/blob/main/openapi/argo-cd-openapi.yml) — The Argo CD API provides REST endpoints for managing GitOps continuous delivery on Kubernetes, enabling creating and managing applications, projects, and repositories.
- [argo-workflows-openapi.yml](https://github.com/api-evangelist/argo/blob/main/openapi/argo-workflows-openapi.yml) — REST API for Argo Workflows, a Kubernetes-native workflow engine for orchestrating parallel jobs, providing endpoints for managing workflows and templates.

### [Istio](https://github.com/api-evangelist/istio)

Istio is a feature-rich service mesh that provides traffic management, mutual TLS security, observability, and policy enforcement across microservices running on Kubernetes. It uses the Envoy proxy as its data plane and exposes a rich set of CRD-based APIs for configuring every aspect of service-to-service communication.

- [istio-networking-api-openapi.yml](https://github.com/api-evangelist/istio/blob/main/openapi/istio-networking-api-openapi.yml) — The Istio Networking API provides configuration resources for traffic management within an Istio service mesh, including VirtualService, DestinationRule, and Gateway.
- [istio-security-api-openapi.yml](https://github.com/api-evangelist/istio/blob/main/openapi/istio-security-api-openapi.yml) — The Istio Security API provides configuration resources for managing security policies within an Istio service mesh, including AuthorizationPolicy and PeerAuthentication.
- [istio-telemetry-api-openapi.yml](https://github.com/api-evangelist/istio/blob/main/openapi/istio-telemetry-api-openapi.yml) — The Istio Telemetry API provides configuration resources for managing observability within an Istio service mesh.
- [istio-extensions-api-openapi.yml](https://github.com/api-evangelist/istio/blob/main/openapi/istio-extensions-api-openapi.yml) — The Istio Extensions API provides configuration resources for extending the Istio service mesh with custom functionality via WebAssembly plugins.

### [Harbor](https://github.com/api-evangelist/harbor)

Harbor is an open source community platform that lets brands build owned superfan ecosystems with engagement, loyalty, and rewards features. It provides tools for managing fan communities, guilds, analytics, and multi-platform identity linking across Discord, Steam, and blockchain platforms.

- [harbor-api-openapi.yml](https://github.com/api-evangelist/harbor/blob/main/openapi/harbor-api-openapi.yml) — The Harbor API provides programmatic access to the Harbor community platform, enabling brands to manage superfan communities, rewards programs, guilds, and analytics.
- [harbor-openapi.yml](https://github.com/api-evangelist/harbor/blob/main/openapi/harbor-openapi.yml) — The Harbor API enables programmatic access to the Harbor community platform, allowing brands to manage their superfan community, rewards programs, and engagement features.

### [Harbor Compliance](https://github.com/api-evangelist/harbor-compliance)

Harbor Compliance is a compliance management platform that helps businesses streamline licensing, registered agent services, and regulatory tracking across US jurisdictions. It is primarily a partner API that enables SaaS platforms to embed compliance workflows directly into their products.

- [harbor-compliance-api-openapi.yml](https://github.com/api-evangelist/harbor-compliance/blob/main/openapi/harbor-compliance-api-openapi.yml) — The Harbor Compliance API enables partners to integrate compliance management capabilities into their platforms, with resource-oriented URLs and JSON responses.
- [harbor-compliance-openapi.yml](https://github.com/api-evangelist/harbor-compliance/blob/main/openapi/harbor-compliance-openapi.yml) — The Harbor Compliance API provides programmatic access to compliance management capabilities including entities, licenses, registered agents, and filings.

### [etcd](https://github.com/api-evangelist/etcd)

etcd is a distributed, strongly consistent key-value store that serves as the primary data store for Kubernetes cluster state. Every object in Kubernetes — Pods, Services, ConfigMaps, Secrets — is persisted in etcd, making its reliability and consistency guarantees fundamental to the entire control plane.

- [etcd-http-gateway-openapi.yml](https://github.com/api-evangelist/etcd/blob/main/openapi/etcd-http-gateway-openapi.yml) — The etcd HTTP/JSON gateway translates HTTP requests into gRPC calls, enabling clients without gRPC support to interact with the etcd v3 key-value store.

### [Rook](https://github.com/api-evangelist/rook)

Rook is a cloud native storage orchestrator for Kubernetes that turns distributed storage systems into self-managing, self-scaling storage services. It primarily orchestrates Ceph, providing block storage, shared file systems, and S3-compatible object storage as Kubernetes-native resources.

- [rook-ceph-object-storage-openapi.yml](https://github.com/api-evangelist/rook/blob/main/openapi/rook-ceph-object-storage-openapi.yml) — Rook provisions Ceph Object Storage gateways (Ceph RGW) that expose an S3-compatible REST API for object storage operations.

### [SPIFFE](https://github.com/api-evangelist/spiffe)

SPIFFE (Secure Production Identity Framework for Everyone) is a set of open standards for workload identity in dynamic, heterogeneous environments. It defines how services prove their identity to each other without relying on shared secrets, using cryptographic SVIDs (SPIFFE Verifiable Identity Documents) instead.

- [spiffe-federation-openapi.yml](https://github.com/api-evangelist/spiffe/blob/main/openapi/spiffe-federation-openapi.yml) — The SPIFFE Federation Bundle Endpoint is an HTTP REST API that SPIFFE implementations expose to allow foreign trust domains to retrieve the current trust bundle.

### [SPIRE](https://github.com/api-evangelist/spire)

SPIRE (SPIFFE Runtime Environment) is the reference implementation of the SPIFFE standard. It issues and renews SVIDs to workloads automatically, integrating with Kubernetes, cloud provider APIs, and hardware attestation to verify workload identity before issuing certificates.

- [spire-health-openapi.yml](https://github.com/api-evangelist/spire/blob/main/openapi/spire-health-openapi.yml) — SPIRE Server and SPIRE Agent both expose an optional HTTP health checking endpoint that provides liveness and readiness probes.
- [spire-oidc-discovery-openapi.yml](https://github.com/api-evangelist/spire/blob/main/openapi/spire-oidc-discovery-openapi.yml) — The SPIRE OIDC Discovery Provider is a helper component that exposes a minimal OpenID Connect discovery document and JWKS endpoint.

### [Open Policy Agent](https://github.com/api-evangelist/open-policy-agent)

Open Policy Agent (OPA) is a general-purpose policy engine that decouples policy decision-making from application code. It uses the Rego policy language to express authorization rules, admission control, data filtering, and any other policy logic, and exposes a rich REST API for querying, compiling, and managing policies.

- [data-api.yml](https://github.com/api-evangelist/open-policy-agent/blob/main/openapi/data-api.yml) — API for reading and writing documents in OPA (Open Policy Agent).
- [policy-api.yml](https://github.com/api-evangelist/open-policy-agent/blob/main/openapi/policy-api.yml) — API for managing policy modules, allowing CRUD operations.
- [query-api.yml](https://github.com/api-evangelist/open-policy-agent/blob/main/openapi/query-api.yml) — API for executing simple and ad-hoc queries in OPA (Open Policy Agent).
- [compile-api.yml](https://github.com/api-evangelist/open-policy-agent/blob/main/openapi/compile-api.yml) — API for partially evaluating Rego queries in OPA (Open Policy Agent).
- [health-api.yml](https://github.com/api-evangelist/open-policy-agent/blob/main/openapi/health-api.yml) — API for checking the health and readiness of an OPA server.
- [config-api.yml](https://github.com/api-evangelist/open-policy-agent/blob/main/openapi/config-api.yml) — API for retrieving OPA's active configuration, including discovered configurations.
- [status-api.yml](https://github.com/api-evangelist/open-policy-agent/blob/main/openapi/status-api.yml) — API for accessing OPA status information via a pull-based mechanism.

### [KEDA](https://github.com/api-evangelist/keda)

KEDA (Kubernetes Event-driven Autoscaling) extends Kubernetes with the ability to scale workloads based on external event sources — queues, streams, databases, and HTTP endpoints — rather than just CPU and memory. It acts as a Kubernetes metrics server and custom controller, enabling fine-grained, demand-driven scaling.

- [keda-metrics-api-openapi.yml](https://github.com/api-evangelist/keda/blob/main/openapi/keda-metrics-api-openapi.yml) — KEDA's Metrics API scaler connects to an HTTP endpoint that exposes a numeric metric value, which KEDA uses to drive scaling decisions.

### [Dapr](https://github.com/api-evangelist/dapr)

Dapr (Distributed Application Runtime) is a portable, event-driven runtime that makes it easy to build resilient, stateless, and stateful microservices. It provides a set of building block APIs — pub/sub, state management, service invocation, actors, secrets, and more — that abstract away the complexity of distributed systems infrastructure.

- [dapr-actors-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-actors-openapi.yml) — The Dapr Actors API provides virtual actor capabilities for distributed applications, including actor method invocation, state management, timers, and reminders.
- [dapr-bindings-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-bindings-openapi.yml) — The Dapr Bindings API enables applications to trigger and invoke external resources through output bindings, and receive events from external resources.
- [dapr-configuration-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-configuration-openapi.yml) — The Dapr Configuration API enables applications to retrieve and subscribe to configuration items from supported configuration stores.
- [dapr-cryptography-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-cryptography-openapi.yml) — The Dapr Cryptography API enables applications to perform cryptographic operations such as encrypting and decrypting data using configured cryptographic components.
- [dapr-distributed-lock-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-distributed-lock-openapi.yml) — The Dapr Distributed Lock API enables applications to acquire and release locks on shared resources, ensuring mutual exclusion across multiple application instances.
- [dapr-health-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-health-openapi.yml) — The Dapr Health API provides health check endpoints for the Dapr sidecar, usable with container orchestrators like Kubernetes for liveness and readiness probes.
- [dapr-jobs-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-jobs-openapi.yml) — The Dapr Jobs API enables applications to schedule, retrieve, and delete jobs for future execution at specific times or on recurring schedules.
- [dapr-metadata-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-metadata-openapi.yml) — The Dapr Metadata API provides information about the Dapr sidecar, including application connection details, registered components, and active subscriptions.
- [dapr-pubsub-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-pubsub-openapi.yml) — The Dapr Pub/Sub API enables publish and subscribe messaging between applications, supporting publishing events to topics and bulk publishing.
- [dapr-secrets-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-secrets-openapi.yml) — The Dapr Secrets API provides a consistent way to retrieve application secrets from various secret stores including Vault, AWS Secrets Manager, and Kubernetes.
- [dapr-service-invocation-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-service-invocation-openapi.yml) — The Dapr Service Invocation API enables applications to communicate with each other through well-known endpoints using HTTP methods.
- [dapr-state-management-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-state-management-openapi.yml) — The Dapr State Management API provides key/value-based state management capabilities for distributed applications, supporting saving, retrieving, deleting, and transactional state.
- [dapr-workflow-openapi.yml](https://github.com/api-evangelist/dapr/blob/main/openapi/dapr-workflow-openapi.yml) — The Dapr Workflow API provides the ability to manage workflow instances, including starting, getting status, pausing, resuming, terminating, and purging workflows.

### [Crossplane](https://github.com/api-evangelist/crossplane)

Crossplane is a Kubernetes add-on that transforms a Kubernetes cluster into a universal control plane for provisioning and managing cloud infrastructure. It allows platform teams to define custom APIs for infrastructure — databases, queues, networks — and expose them to developers as Kubernetes-native resources.

- [crossplane-kubernetes-api-openapi.yml](https://github.com/api-evangelist/crossplane/blob/main/openapi/crossplane-kubernetes-api-openapi.yml) — The Crossplane Kubernetes API extends the Kubernetes API server with custom resources for managing cloud infrastructure declaratively.

### [Backstage](https://github.com/api-evangelist/backstage)

Backstage is an open source developer portal platform originally built at Spotify. It provides a centralized hub for managing software catalogs, documentation, scaffolding templates, and plugins, giving engineering teams a single pane of glass for discovering and managing their services and infrastructure.

- [backstage-catalog-openapi.yml](https://github.com/api-evangelist/backstage/blob/main/openapi/backstage-catalog-openapi.yml) — The Backstage Software Catalog REST API provides JSON-based endpoints for managing and querying catalog entities, locations, and related metadata.
- [backstage-scaffolder-openapi.yml](https://github.com/api-evangelist/backstage/blob/main/openapi/backstage-scaffolder-openapi.yml) — The Backstage Scaffolder REST API provides endpoints for creating, managing, and monitoring scaffolder tasks via Software Templates.
- [backstage-search-openapi.yml](https://github.com/api-evangelist/backstage/blob/main/openapi/backstage-search-openapi.yml) — The Backstage Search API provides endpoints for querying the Backstage search index with full-text search across all indexed content.
- [backstage-auth-openapi.yml](https://github.com/api-evangelist/backstage/blob/main/openapi/backstage-auth-openapi.yml) — The Backstage Auth API provides endpoints for authenticating users and services with the Backstage backend, supporting multiple authentication providers.
- [backstage-permissions-openapi.yml](https://github.com/api-evangelist/backstage/blob/main/openapi/backstage-permissions-openapi.yml) — The Backstage Permissions API provides endpoints for evaluating and managing authorization decisions within Backstage.
- [backstage-techdocs-openapi.yml](https://github.com/api-evangelist/backstage/blob/main/openapi/backstage-techdocs-openapi.yml) — The Backstage TechDocs API provides endpoints for generating, publishing, and serving technical documentation for catalog entities using MkDocs.

### [Knative](https://github.com/api-evangelist/knative)

Knative extends Kubernetes with primitives for building, deploying, and managing serverless and event-driven applications. Its two core components — Serving and Eventing — handle auto-scaling containerized workloads to zero and routing events through brokers, triggers, and channels.

- [knative-serving-api-openapi.yml](https://github.com/api-evangelist/knative/blob/main/openapi/knative-serving-api-openapi.yml) — The Knative Serving API extends the Kubernetes API with custom resources for deploying and managing serverless workloads.
- [knative-eventing-api-openapi.yml](https://github.com/api-evangelist/knative/blob/main/openapi/knative-eventing-api-openapi.yml) — The Knative Eventing API extends Kubernetes with custom resources for building event-driven architectures using the Broker and Trigger pattern.

### [CubeFS](https://github.com/api-evangelist/cubefs)

CubeFS is a cloud native distributed storage platform that supports multiple storage engines including object storage, POSIX-compliant file systems, and block storage. It is designed for large-scale data-intensive workloads and provides an S3-compatible object interface alongside a master API for cluster administration.

- [cubefs-master-api-openapi.yml](https://github.com/api-evangelist/cubefs/blob/main/openapi/cubefs-master-api-openapi.yml) — The CubeFS Master API provides HTTP endpoints for administering a CubeFS distributed storage cluster, serving as the control plane for all cluster operations.
- [cubefs-s3-api-openapi.yml](https://github.com/api-evangelist/cubefs/blob/main/openapi/cubefs-s3-api-openapi.yml) — The CubeFS ObjectNode provides an S3-compatible object storage interface allowing applications using AWS S3 SDKs and tools to interact with CubeFS.

### [Longhorn](https://github.com/api-evangelist/longhorn)

Longhorn is a lightweight, reliable distributed block storage system for Kubernetes originally developed by Rancher. It implements persistent volumes using microservices, with each volume getting its own controller and replicas, making it resilient and operationally simple to manage through a REST API and web UI.

- [longhorn-manager-api-openapi.yml](https://github.com/api-evangelist/longhorn/blob/main/openapi/longhorn-manager-api-openapi.yml) — The Longhorn Manager REST API provides programmatic access to all Longhorn storage management operations following the Rancher REST API specification.

### [Falco](https://github.com/api-evangelist/falco)

Falco is a cloud native runtime security tool that uses eBPF to detect unexpected behavior in applications and containers at the kernel level. It evaluates a stream of system calls against a rule set to identify security threats, policy violations, and anomalous activity in real time across Kubernetes workloads.

- [falco-openapi.yml](https://github.com/api-evangelist/falco/blob/main/openapi/falco-openapi.yml) — The Falco HTTP API provides health check, version, and rules management endpoints for the Falco cloud-native runtime security engine using eBPF.

### [Chaos Mesh](https://github.com/api-evangelist/chaos-mesh)

Chaos Mesh is a cloud native chaos engineering platform for Kubernetes that lets teams inject controlled failures — network delays, pod kills, CPU stress, disk I/O faults — to validate system resilience. It provides a dashboard and REST API for orchestrating and scheduling chaos experiments as Kubernetes CRDs.

- [chaos-mesh-dashboard-api-openapi.yml](https://github.com/api-evangelist/chaos-mesh/blob/main/openapi/chaos-mesh-dashboard-api-openapi.yml) — The Chaos Mesh Dashboard API provides REST endpoints for managing chaos experiments, schedules, workflows, and events on Kubernetes clusters.
- [chaos-mesh-dashboard-openapi.yml](https://github.com/api-evangelist/chaos-mesh/blob/main/openapi/chaos-mesh-dashboard-openapi.yml) — The Chaos Mesh Dashboard API provides HTTP REST endpoints for managing chaos engineering experiments on Kubernetes served by the chaos-dashboard component.

### [Kyverno](https://github.com/api-evangelist/kyverno)

Kyverno is a policy engine designed specifically for Kubernetes. It allows cluster administrators to validate, mutate, and generate Kubernetes resources using policies written as Kubernetes resources themselves — no new language to learn. The Policy Reporter component exposes query APIs for reporting on policy compliance across the cluster.

- [kyverno-policy-reporter-openapi.yml](https://github.com/api-evangelist/kyverno/blob/main/openapi/kyverno-policy-reporter-openapi.yml) — The Kyverno Policy Reporter REST API provides endpoints for querying PolicyReport and ClusterPolicyReport custom resources generated by Kyverno.

### [Litmus](https://github.com/api-evangelist/litmus)

Litmus is an email testing and analytics platform that helps developers and marketers validate how emails render across 40+ clients and devices before sending. It provides instant preview generation, spam filter testing, link checking, and post-send engagement analytics through a set of REST APIs.

- [litmus-instant-openapi.yml](https://github.com/api-evangelist/litmus/blob/main/openapi/litmus-instant-openapi.yml) — The Litmus Instant API provides REST endpoints for generating email preview screenshots across 40+ email clients by submitting HTML directly.
- [litmus-legacy-previews-openapi.yml](https://github.com/api-evangelist/litmus/blob/main/openapi/litmus-legacy-previews-openapi.yml) — The Litmus Legacy Previews API provides endpoints for email preview tests, spam filter tests, link checks, and code analysis.
- [litmus-email-analytics-openapi.yml](https://github.com/api-evangelist/litmus/blob/main/openapi/litmus-email-analytics-openapi.yml) — The Litmus Email Analytics API provides REST endpoints for retrieving email campaign engagement metrics including read rates, deletion rates, and device types.

### [Thanos](https://github.com/api-evangelist/thanos)

Thanos extends Prometheus with long-term storage, global query federation, and high availability. It deploys as a set of components — Sidecar, Store Gateway, Querier, Ruler, Receiver, and Compactor — that together enable Prometheus to scale across multiple clusters and retain metrics indefinitely in object storage.

- [thanos-query-api.yml](https://github.com/api-evangelist/thanos/blob/main/openapi/thanos-query-api.yml) — The Thanos Query API provides a Prometheus-compatible HTTP API for querying metrics across multiple Prometheus servers and long-term storage backends.
- [thanos-store-gateway-openapi.yml](https://github.com/api-evangelist/thanos/blob/main/openapi/thanos-store-gateway-openapi.yml) — The Thanos Store Gateway HTTP API provides operational endpoints for the Store Gateway component, which serves metrics stored in object storage buckets.
- [thanos-sidecar-openapi.yml](https://github.com/api-evangelist/thanos/blob/main/openapi/thanos-sidecar-openapi.yml) — The Thanos Sidecar HTTP API provides operational endpoints for the Sidecar component deployed alongside Prometheus instances, exposing health and readiness probes.
- [thanos-ruler-openapi.yml](https://github.com/api-evangelist/thanos/blob/main/openapi/thanos-ruler-openapi.yml) — The Thanos Ruler HTTP API exposes Prometheus-compatible endpoints for querying alerting and recording rules evaluated by the Ruler component.
- [thanos-receive-openapi.yml](https://github.com/api-evangelist/thanos/blob/main/openapi/thanos-receive-openapi.yml) — The Thanos Receive HTTP API implements the Prometheus Remote Write protocol to accept metrics pushed from Prometheus instances.
- [thanos-compact-openapi.yml](https://github.com/api-evangelist/thanos/blob/main/openapi/thanos-compact-openapi.yml) — The Thanos Compact HTTP API provides operational endpoints for the Compactor component, which applies Prometheus compaction and downsampling to object storage.

### [Contour](https://github.com/api-evangelist/contour)

Contour is a Kubernetes ingress controller that uses Envoy proxy as its data plane. It provides a safe, multi-team-friendly ingress model through its HTTPProxy CRD, and also implements the Kubernetes Gateway API — making it a flexible choice for teams that want advanced routing without the complexity of a full service mesh.

- [contour-httpproxy-openapi.yml](https://github.com/api-evangelist/contour/blob/main/openapi/contour-httpproxy-openapi.yml) — The Contour HTTPProxy API is a Kubernetes CRD that extends the standard Ingress API with advanced routing features including multi-team support and TLS delegation.
- [contour-gateway-openapi.yml](https://github.com/api-evangelist/contour/blob/main/openapi/contour-gateway-openapi.yml) — Contour's implementation of the Kubernetes Gateway API, providing support for GatewayClass, Gateway, HTTPRoute, TLSRoute, and related resources.

### [Pixie](https://github.com/api-evangelist/pixie)

Pixie is a Kubernetes observability platform that uses eBPF to automatically capture telemetry — request traces, resource metrics, network flows, application profiles — without any code instrumentation. It provides a scripting interface (PxL) and REST API for querying live cluster data and executing custom observability scripts.

- [pixie-openapi.yml](https://github.com/api-evangelist/pixie/blob/main/openapi/pixie-openapi.yml) — The Pixie API provides programmatic access to the Pixie Kubernetes observability platform, enabling listing and managing clusters and executing PxL scripts.

### [Porter](https://github.com/api-evangelist/porter)

Porter is a package manager for cloud native applications that implements the Cloud Native Application Bundle (CNAB) specification. It allows teams to package, distribute, and deploy complex multi-component applications — including their infrastructure, tools, and configuration — as a single, self-contained bundle.

- [porter-bundle-openapi.yml](https://github.com/api-evangelist/porter/blob/main/openapi/porter-bundle-openapi.yml) — The Porter Bundle API provides programmatic access to managing Cloud Native Application Bundles (CNAB) using Porter.

### [Volcano](https://github.com/api-evangelist/volcano)

Volcano is a batch scheduling system for Kubernetes designed for high-performance computing workloads such as machine learning training, big data processing, and scientific simulation. It extends Kubernetes with gang scheduling, fair-share queuing, and job preemption through CRD-based APIs for Jobs, Queues, and PodGroups.

- [volcano-job-openapi.yml](https://github.com/api-evangelist/volcano/blob/main/openapi/volcano-job-openapi.yml) — The Volcano Job API provides Kubernetes CRD endpoints for defining and managing batch workloads using Volcano's Job resource with gang-scheduling support.
- [volcano-queue-openapi.yml](https://github.com/api-evangelist/volcano/blob/main/openapi/volcano-queue-openapi.yml) — The Volcano Queue API provides Kubernetes CRD endpoints for managing Queue resources that collect PodGroups and apply weight-based fair-share scheduling.
- [volcano-podgroup-openapi.yml](https://github.com/api-evangelist/volcano/blob/main/openapi/volcano-podgroup-openapi.yml) — The Volcano PodGroup API provides Kubernetes CRD endpoints for managing PodGroup resources representing groups of pods with strong co-scheduling guarantees.

### [KubeVirt](https://github.com/api-evangelist/kubevirt)

KubeVirt extends Kubernetes to support running virtual machines alongside containers using the same orchestration primitives. It allows teams to manage VMs as Kubernetes workloads, enabling hybrid scenarios where legacy VM-based applications can coexist and interoperate with modern containerized services.

- [kubevirt-vm-openapi.yml](https://github.com/api-evangelist/kubevirt/blob/main/openapi/kubevirt-vm-openapi.yml) — The KubeVirt VM Management API extends the Kubernetes API with custom resources for running and managing virtual machines alongside containers.
- [kubevirt-cdi-openapi.yml](https://github.com/api-evangelist/kubevirt/blob/main/openapi/kubevirt-cdi-openapi.yml) — The KubeVirt Containerized Data Importer (CDI) API provides Kubernetes CRD endpoints for managing virtual machine disk image import and cloning pipelines.

### [Emissary-Ingress](https://github.com/api-evangelist/emissary-ingress)

Emissary-Ingress (formerly Ambassador) is a Kubernetes-native API gateway and ingress controller built on the Envoy proxy. It is configured entirely through Kubernetes CRDs, making it deeply integrated with Kubernetes RBAC and GitOps workflows, and supports advanced routing, authentication, rate limiting, and circuit breaking.

- [emissary-ingress-openapi.yml](https://github.com/api-evangelist/emissary-ingress/blob/main/openapi/emissary-ingress-openapi.yml) — Emissary-Ingress is a CNCF incubating Kubernetes-native API gateway and ingress controller built on the Envoy proxy, configured through Kubernetes CRDs.

### [CloudEvents](https://github.com/api-evangelist/cloudevents)

CloudEvents is a specification for describing event data in a common, portable format. It defines a vendor-neutral envelope for event metadata that makes it possible to route, process, and deliver events consistently across clouds, platforms, and languages — including a Subscriptions API for managing event stream subscriptions.

- [cloudevents-subscriptions-openapi.yml](https://github.com/api-evangelist/cloudevents/blob/main/openapi/cloudevents-subscriptions-openapi.yml) — The CloudEvents Subscriptions API provides a vendor-neutral REST interface for managing subscriptions to event streams.

---

This is what API-first infrastructure looks like in practice. Not just building APIs, but documenting them in ways that machines — and people — can actually use. With OpenAPI specs in place, these projects become easier to integrate into API gateways, generate SDKs from, lint for breaking changes, and surface in developer portals like Backstage.

This is just the start. Next steps include running the same treatment across Apache, Linux Foundation, and other open source foundations — building toward a comprehensive, open index of the APIs that run the world's infrastructure.

If this kind of work interests you, follow along at [api-evangelist.com](https://apievangelist.com) or connect with me here. And if you maintain one of these projects and want to improve or correct the specs, every repo is open for contributions.

\#CNCF #CloudNative #OpenAPI #APIs #Kubernetes #Infrastructure #OpenSource #DeveloperExperience
