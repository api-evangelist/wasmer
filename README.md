# Wasmer (wasmer)

Wasmer is a WebAssembly runtime, package registry, and edge platform. The Wasmer Registry stores and distributes WebAssembly packages and namespaces, Wasmer Edge deploys those packages as auto-scaling apps, and the wasmer CLI and wasmer.sh interact with the platform through a single public GraphQL API at registry.wasmer.io/graphql.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/wasmer/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/wasmer/refs/heads/main/apis.yml)

## Tags

- WebAssembly
- Wasm
- Registry
- Edge
- Runtime

## Timestamps

- **Created:** 2026-06-20
- **Modified:** 2026-06-20

## APIs

### Wasmer Registry GraphQL API

The single public GraphQL API behind wasmer.io, the wasmer CLI, and wasmer.sh. A POST /graphql endpoint with optional Bearer (wap_*) auth that spans the Registry, Edge apps, namespaces, and users.

- **Human URL:** [https://docs.wasmer.io/graphql-api](https://docs.wasmer.io/graphql-api)
- **Base URL:** `https://registry.wasmer.io/graphql`

#### Tags

- GraphQL
- Registry
- WebAssembly

#### Properties

- [Documentation](https://docs.wasmer.io/graphql-api)
- [API Reference](https://docs.wasmer.io/registry)
- [OpenAPI](openapi/wasmer-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/wasmer-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [GitHub](https://github.com/wasmerio/wasmer)
- [Postman Collection](collections/wasmer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wasmer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Wasmer Packages and Namespaces API

GraphQL queries and mutations over WebAssembly packages, their versions and distributions, and the namespaces (users and organizations) that own them - getPackage, getPackageVersion, publishPackage, and namespace resolvers.

- **Human URL:** [https://docs.wasmer.io/registry](https://docs.wasmer.io/registry)
- **Base URL:** `https://registry.wasmer.io/graphql`

#### Tags

- GraphQL
- Packages
- Namespaces

#### Properties

- [Documentation](https://docs.wasmer.io/registry)
- [API Reference](https://docs.wasmer.io/registry/manifest)
- [OpenAPI](openapi/wasmer-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/wasmer-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [GitHub](https://github.com/wasmerio/wasmer)
- [Postman Collection](collections/wasmer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wasmer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Wasmer Apps and Edge Deployments API

GraphQL surface for Wasmer Edge - deploy WebAssembly packages as auto-scaling apps with versioned deployments, custom domains, and rollback via getDeployApp, getAppByGlobalId, and deployApp.

- **Human URL:** [https://docs.wasmer.io/edge](https://docs.wasmer.io/edge)
- **Base URL:** `https://registry.wasmer.io/graphql`

#### Tags

- GraphQL
- Edge
- Deployments

#### Properties

- [Documentation](https://docs.wasmer.io/edge)
- [API Reference](https://docs.wasmer.io/edge/configuration)
- [OpenAPI](openapi/wasmer-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/wasmer-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [GitHub](https://github.com/wasmerio/wasmer)
- [Postman Collection](collections/wasmer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wasmer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Wasmer Users and Auth API

Identity and account resolvers - the viewer query for the authenticated user, getUser, and namespace ownership, authenticated with a wap_* Bearer token created via wasmer login.

- **Human URL:** [https://docs.wasmer.io/registry/cli](https://docs.wasmer.io/registry/cli)
- **Base URL:** `https://registry.wasmer.io/graphql`

#### Tags

- GraphQL
- Users
- Auth

#### Properties

- [Documentation](https://docs.wasmer.io/registry/cli)
- [API Reference](https://docs.wasmer.io/graphql-api)
- [OpenAPI](openapi/wasmer-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/wasmer-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [GitHub](https://github.com/wasmerio/wasmer)
- [Postman Collection](collections/wasmer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wasmer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Wasmer CLI

The wasmer command-line client (wasmer login, publish, deploy, run, ssh) - a first-class consumer of the Registry GraphQL API that wraps publish and Edge deployment workflows.

- **Human URL:** [https://docs.wasmer.io/registry/cli](https://docs.wasmer.io/registry/cli)
- **Base URL:** `https://registry.wasmer.io/graphql`

#### Tags

- CLI
- Tooling
- Publish

#### Properties

- [Documentation](https://docs.wasmer.io/registry/cli)
- [API Reference](https://docs.wasmer.io/install)
- [GraphQL](graphql/wasmer-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [GitHub](https://github.com/wasmerio/wasmer)
- [Postman Collection](collections/wasmer.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wasmer.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/wasmerio)
- [LinkedIn](https://www.linkedin.com/company/wasmer)
- [Website](https://wasmer.io)
- [Documentation](https://docs.wasmer.io)
- [Plans](plans/wasmer-plans-pricing.yml)
- [Rate Limits](rate-limits/wasmer-rate-limits.yml)
- [Fin Ops](finops/wasmer-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
