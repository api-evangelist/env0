# Env0 (env0)

env0 -- now trading as "env zero" -- is an infrastructure-as-code automation and cloud governance platform for Terraform, OpenTofu, Terragrunt, Pulumi, CloudFormation, Kubernetes and Helm. It provisions and manages cloud environments from reusable templates, orchestrates multi-environment workflows with dependencies, enforces custom approval and guardrail policies, detects and remediates infrastructure drift, runs a private module and provider registry, and adds cost estimation, actual-cost visibility and budget thresholds on top. The public REST API at https://api.env0.com publishes 327 operations across 30 areas and authenticates with HTTP Basic using an API Key ID and Secret. env zero also ships a first-party CLI, a Terraform provider, an official MCP server, a published Agent Skill and a conformant A2A agent card.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/env0/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/env0/refs/heads/main/apis.yml)

## Scope

- **Type:** Index

## Tags

- FinOps
- Infrastructure as Code
- DevOps
- Cloud
- Terraform
- OpenTofu
- Platform Engineering
- Cloud Governance
- Drift Detection

## Timestamps

- **Created:** 2026-03-27
- **Modified:** 2026-09-06

## APIs

### Env0

env0 is an infrastructure-as-code automation platform providing cost estimation, policy enforcement, and self-service environments. The public REST API is available at https://api.env0.com/ and uses HTTP Basic authentication with API key credentials. Rate limits are 1,000 requests per 60 seconds.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- FinOps
- Infrastructure as Code

#### Properties

- [Documentation](https://docs.envzero.com/)
- [API Reference](https://docs.envzero.com/api-reference)
- [Getting Started](https://docs.envzero.com/guides/getting-started/getting-started)
- [Authentication](https://docs.envzero.com/guides/admin-guide/user-role-and-team-management/api-keys)
- [M C P Server](mcp/env0-mcp.yml)
- [Tool Crosswalk](mcp/env0-tool-crosswalk.yml)
- [Postman Collection](collections/env0-agents-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-agents-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-approvalpolicies-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-approvalpolicies-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-configuration-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-configuration-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-deployments-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-deployments-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-environments-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-environments-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-modules-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-modules-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-organizations-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-organizations-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-projects-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-projects-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-templates-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-templates-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-users-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-users-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0-webhooks-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-webhooks-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/env0.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Agents API

The Agents API from Env0 — 1 operation(s) for agents.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- Agents

#### Properties

- [OpenAPI](openapi/env0-agents-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-agents-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-agents-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 ApprovalPolicies API

The ApprovalPolicies API from Env0 — 1 operation(s) for approvalpolicies.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- ApprovalPolicies

#### Properties

- [OpenAPI](openapi/env0-approvalpolicies-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-approvalpolicies-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-approvalpolicies-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Configuration API

The Configuration API from Env0 — 1 operation(s) for configuration.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- Configuration

#### Properties

- [OpenAPI](openapi/env0-configuration-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-configuration-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-configuration-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Deployments API

The Deployments API from Env0 — 2 operation(s) for deployments.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- Deployment

#### Properties

- [OpenAPI](openapi/env0-deployments-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-deployments-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-deployments-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Environments API

The Environments API from Env0 — 2 operation(s) for environments.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- Environments

#### Properties

- [OpenAPI](openapi/env0-environments-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-environments-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-environments-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Modules API

The Modules API from Env0 — 1 operation(s) for modules.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- Modules

#### Properties

- [OpenAPI](openapi/env0-modules-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-modules-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-modules-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Organizations API

The Organizations API from Env0 — 1 operation(s) for organizations.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- Organization

#### Properties

- [OpenAPI](openapi/env0-organizations-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-organizations-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-organizations-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Projects API

The Projects API from Env0 — 2 operation(s) for projects.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- Project

#### Properties

- [OpenAPI](openapi/env0-projects-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-projects-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-projects-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Templates API

The Templates API from Env0 — 1 operation(s) for templates.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- Templates

#### Properties

- [OpenAPI](openapi/env0-templates-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-templates-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-templates-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Users API

The Users API from Env0 — 1 operation(s) for users.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- User

#### Properties

- [OpenAPI](openapi/env0-users-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-users-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-users-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Env0 Webhooks API

The Webhooks API from Env0 — 1 operation(s) for webhooks.

- **Human URL:** [https://www.envzero.com/](https://www.envzero.com/)
- **Base URL:** `https://api.env0.com/`

#### Tags

- Webhook

#### Properties

- [OpenAPI](openapi/env0-webhooks-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/env0-webhooks-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/env0-webhooks-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Agentic Access](agentic-access/env0-agentic-access.yml)
- [Domain Security](security/env0-domain-security.yml)
- [Authentication](authentication/env0-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/env0)
- [Website](https://www.envzero.com/)
- [Developer Portal](https://docs.envzero.com/)
- [Documentation](https://docs.envzero.com/)
- [API Reference](https://docs.envzero.com/api-reference)
- [Getting Started](https://docs.envzero.com/guides/getting-started/getting-started)
- [Support](https://docs.envzero.com/guides/community-and-resources/support-and-help/support)
- [Pricing](https://www.envzero.com/pricing)
- [Sign Up](https://app.env0.com/)
- [Terms of Service](https://www.envzero.com/terms-and-conditions)
- [Privacy Policy](https://www.envzero.com/privacy-policy)
- [Blog](https://www.envzero.com/resources)
- [GitHub Organization](https://github.com/env0)
- [Status Page](https://status.env0.com)
- [Compliance](https://docs.envzero.com/guides/overview/security-overview)
- [L L Ms Txt](llms/env0-llms.txt)
- [Agent Card](a2a/env0-a2a.yml)
- [Agent Skill](skills/_index.yml)
- [Well Known](well-known/env0-well-known.yml)
- [M C P Server](mcp/env0-mcp.yml)
- [Packages](packages/env0-packages.yml)
- [S D Ks](packages/env0-packages.yml)
- [C L I](cli/env0-cli.yml)
- [Changelog](changelog/env0-changelog.yml)
- [Lifecycle](lifecycle/env0-lifecycle.yml)
- [Conventions](conventions/env0-conventions.yml)
- [Conformance](conformance/env0-conformance.yml)
- [Trust Center](security/env0-trust-center.yml)
- [Webhooks](asyncapi/env0-webhooks.yml)
- [Data Model](data-model/env0-data-model.yml)
- [Plans](plans/env0-plans-pricing.yml)
- [Rate Limits](rate-limits/env0-rate-limits.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
