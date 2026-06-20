# Wasmer Registry GraphQL API

Representative GraphQL schema for the [Wasmer](https://wasmer.io) Registry and Edge
platform. Wasmer exposes a single public GraphQL API that powers wasmer.io, the
`wasmer` CLI, and wasmer.sh.

- GraphQL API docs: <https://docs.wasmer.io/graphql-api>
- Registry docs: <https://docs.wasmer.io/registry>
- Edge docs: <https://docs.wasmer.io/edge>
- GitHub: <https://github.com/wasmerio>

---

## Overview

Wasmer is a WebAssembly runtime, package registry, and edge platform. The Registry
stores and distributes WebAssembly packages (organized under user and organization
namespaces), Wasmer Edge deploys those packages as auto-scaling apps with versioned
deployments, and authenticated identity is exposed through the `viewer` query. All of
these surfaces are reachable through one GraphQL endpoint.

---

## Endpoint

| | |
|--|--|
| **URL** | `https://registry.wasmer.io/graphql` |
| **Method** | `POST` |
| **Content-Type** | `application/json` |
| **GraphiQL** | `https://registry.wasmer.io/graphql` (browser playground) |

A request body is the standard GraphQL JSON envelope:

```json
{
  "query": "{ getPackageVersion(name: \"python/python\") { version } }",
  "variables": {}
}
```

---

## Authentication

Many read queries (e.g. resolving public packages) are unauthenticated. Mutations and
account-scoped queries require a **Bearer token** in the `Authorization` header.

```
Authorization: Bearer wap_xxxxxxxxxxxxxxxxxxxxxxxx
```

- Tokens use the `wap_*` prefix and may be supplied via the `WASMER_TOKEN`
  environment variable for the CLI and SDKs.
- Create a token by running `wasmer login` (opens the browser auth flow) or from the
  Wasmer dashboard under account settings.
- The GraphQL endpoint is overridable via `WASMER_GRAPHQL_URL`.

---

## Schema file

See [`wasmer-schema.graphql`](./wasmer-schema.graphql) for a representative SDL
subset. The schema is large and evolving; the SDL here models the package, namespace,
app/deployment, and user surfaces that the public docs, CLI, and SDKs exercise. It is
representative, not the authoritative generated schema.

---

## Key queries

### Resolve a package version

```graphql
query {
  getPackageVersion(name: "python") {
    version
    repository
    homepage
    distribution {
      downloadUrl
      size
    }
  }
}
```

### Look up a package and its versions

```graphql
query {
  getPackage(name: "wasmer/winterjs") {
    name
    namespace
    private
    versions {
      version
      createdAt
      distribution {
        downloadUrl
        size
      }
    }
  }
}
```

### Resolve packages by interface (e.g. WASI)

```graphql
query {
  getInterfaceVersion(name: "wasi", version: "latest") {
    interface {
      name
      description
    }
    packageVersions {
      edges {
        node {
          version
          package {
            name
          }
          distribution {
            downloadUrl
          }
        }
      }
    }
  }
}
```

### The authenticated user (viewer)

```graphql
query {
  viewer {
    username
    email
    namespaces {
      edges {
        node {
          name
        }
      }
    }
  }
}
```

### Fetch an Edge app and its active version

```graphql
query {
  getDeployApp(owner: "wasmer", name: "my-app") {
    id
    name
    url
    activeVersion {
      id
      version
      url
      createdAt
    }
  }
}
```

---

## Key mutations

### Publish a package

```graphql
mutation PublishPackage($input: PublishPackageInput!) {
  publishPackage(input: $input) {
    success
    packageVersion {
      version
      package {
        name
      }
    }
  }
}
```

### Deploy an app to Wasmer Edge

```graphql
mutation DeployApp($input: DeployAppInput!) {
  deployApp(input: $input) {
    deployAppVersion {
      id
      url
      app {
        name
      }
    }
  }
}
```

### Create a namespace (organization)

```graphql
mutation CreateNamespace($input: CreateNamespaceInput!) {
  createNamespace(input: $input) {
    namespace {
      name
    }
  }
}
```

---

## Subscriptions

The public GraphQL API is request/response (POST). Wasmer does not document a public
GraphQL subscription / streaming transport, so no AsyncAPI document is modeled for this
provider. Streaming app logs are surfaced through the CLI (`wasmer app logs`) rather
than a documented GraphQL subscription.
