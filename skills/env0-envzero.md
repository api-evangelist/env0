---
name: Envzero
description: Use when managing infrastructure-as-code deployments, creating and managing cloud environments, orchestrating multi-environment workflows, enforcing governance policies, detecting and remediating infrastructure drift, or automating infrastructure deployments across Terraform, OpenTofu, Pulumi, CloudFormation, Kubernetes, and Helm.
metadata:
    mintlify-proj: envzero
    version: "1.0"
---

# envzero Skill

## Product summary

envzero is an IaC automation platform for deploying and managing cloud infrastructure using Terraform, OpenTofu, Pulumi, Terragrunt, CloudFormation, Kubernetes, and Helm. It provides built-in governance, cost controls, team access management, and drift detection. Agents use envzero to create and manage **environments** (live deployments) from reusable **templates** (IaC configurations), organize them in **projects**, and orchestrate multi-environment workflows with dependencies.

**Key files and concepts:**
- `env0.workflow.yaml` - Declarative workflow configuration defining environment dependencies
- **Templates** - Reusable IaC configurations pointing to VCS repositories
- **Environments** - Live deployments of templates with their own state and variables
- **Projects** - Containers for related environments with scoped credentials and access control
- **API** - REST endpoints at `/api-reference/*` for programmatic access
- **CLI** - `env0` command-line tool for deployment automation

Primary docs: https://docs.envzero.com

## When to use

Reach for this skill when:
- Creating or managing cloud infrastructure environments (dev, staging, production)
- Deploying IaC code from Git repositories (GitHub, GitLab, Bitbucket, Azure DevOps)
- Orchestrating multi-environment deployments with dependencies (workflows)
- Setting up approval policies or governance controls for infrastructure changes
- Detecting and remediating infrastructure drift
- Managing variables, secrets, and credentials across scopes
- Querying deployment history, costs, or environment status via API
- Automating infrastructure operations with the CLI or REST API
- Configuring cost estimation and budget alerts
- Setting up continuous deployment on Git push or pull request

## Quick reference

### Core API endpoints

| Task | Endpoint | Method |
|------|----------|--------|
| List environments | `GET /environments` | List |
| Create environment | `POST /environments` | Create |
| Deploy environment | `POST /environments/{id}/deploy` | Deploy |
| Destroy environment | `POST /environments/{id}/destroy` | Destroy |
| Get deployment logs | `GET /deployments/{id}` | Read |
| List templates | `GET /templates` | List |
| Create template | `POST /templates` | Create |
| List projects | `GET /projects` | List |
| Create API key | `POST /api-keys` | Create |
| Get approval policies | `GET /approval-policies` | List |

### Environment status values

- `ACTIVE` - Successfully deployed and running
- `INACTIVE` - Destroyed or marked as inactive
- `DEPLOY_IN_PROGRESS` - Currently deploying
- `DESTROY_IN_PROGRESS` - Currently being destroyed
- `FAILED` - Deployment or destroy failed
- `WAITING_FOR_USER` - Awaiting approval

### Variable scopes (inheritance order)

1. Organization (lowest precedence)
2. Project
3. Template
4. Environment (highest precedence)

Variables inherit down; lower scopes can override higher scopes.

### IaC tool support

| Tool | Template type | Key files |
|------|---------------|-----------|
| Terraform | `terraform` | `*.tf` files |
| OpenTofu | `opentofu` | `*.tf` files |
| Terragrunt | `terragrunt` | `terragrunt.hcl` + `*.tf` |
| Pulumi | `pulumi` | Language-specific code |
| CloudFormation | `cloudformation` | JSON/YAML templates |
| Kubernetes | `k8s` | YAML/JSON manifests |
| Helm | `helm` | Chart definitions |
| Ansible | `ansible` | Playbook files |

### CLI commands (v1)

```bash
env0 environment create --template <id>      # Create environment from template
env0 environment deploy <id>                 # Deploy environment
env0 environment destroy <id> --yes          # Destroy environment
env0 deployment approve <id>                 # Approve pending deployment
env0 deployment cancel <id>                  # Cancel deployment
env0 context                                 # Show current context
```

### Authentication

- **API Key**: Header `Authorization: Bearer <api-key-id>:<api-key-secret>`
- **Personal API Key**: User-scoped, same permissions as user account
- **Admin API Key**: Full organization permissions
- **User API Key**: Project-scoped with custom RBAC

## Decision guidance

### When to use Template-based vs VCS-based environments

| Aspect | Template-based | VCS-based |
|--------|---|---|
| **Reusability** | Multiple environments from same template | Single environment, direct Git integration |
| **Governance** | Built-in RBAC, policies, variables | Minimal governance overhead |
| **Setup time** | ~5 min (after template created) | <10 min, immediate testing |
| **Best for** | Production, team deployments, consistency | Prototyping, quick testing, one-off deploys |
| **Variable management** | Centralized at template level | Per-environment only |

### When to use Workflows vs individual environments

| Aspect | Workflows | Individual Environments |
|--------|-----------|---|
| **Dependencies** | Manages complex dependency graphs | No dependency management |
| **Orchestration** | Automatic sequential/parallel execution | Manual coordination required |
| **Approval flow** | Per-environment approval control | Single approval per environment |
| **Use case** | Multi-tier infrastructure (VPC → DB → Services) | Single-stack deployments |

### When to use Drift Detection modes

| Mode | Use case |
|------|----------|
| `DISABLED` | Development environments, frequent manual changes expected |
| `CODE_TO_CLOUD` | Production: reapply IaC to fix drift (safest) |
| `CLOUD_TO_CLOUD` | Accept cloud changes as source of truth (rare) |
| `SMART_REMEDIATION` | Auto-detect and apply appropriate fix |

## Workflow

### Typical task: Create and deploy an environment

1. **Understand the project structure**
   - Identify the organization, project, and template to use
   - Verify VCS repository is connected and accessible
   - Check required variables and cloud credentials are configured

2. **Check existing templates**
   - Search templates via API: `GET /templates?organizationId=<org-id>`
   - Or browse UI Templates tab
   - If no suitable template exists, create one pointing to your IaC code

3. **Create the environment**
   - Call `POST /environments` with template ID, project ID, environment name
   - Include required variables in `configurationChanges` array
   - Set TTL (time-to-live) for auto-destroy
   - Set `requiresApproval: true` if approval policy applies

4. **Monitor deployment**
   - Poll `GET /deployments/{id}` to track status
   - Check logs: `GET /deployment-logs/{id}/steps`
   - Wait for status to reach `SUCCESS` or `FAILURE`

5. **Verify and access**
   - Retrieve environment outputs: `GET /environments/{id}/outputs`
   - Check deployed resources: `GET /environments/{id}/resources`
   - Confirm status is `ACTIVE`

### Typical task: Set up approval policies

1. **Define policy requirements**
   - Determine when approvals are needed (cost threshold, resource type, etc.)
   - Write OPA policy or use ready-to-use policies

2. **Create approval policy**
   - Call `POST /approval-policy` with policy name, repository, and OPA rules
   - Assign to organization, project, or specific template

3. **Assign to scope**
   - Call `POST /approval-policy/assign` with policy ID and scope
   - Scope can be ORGANIZATION, PROJECT, BLUEPRINT (template), or ENVIRONMENT

4. **Test**
   - Create a test deployment
   - Verify policy is evaluated during plan step
   - Confirm approval is required before apply

### Typical task: Configure drift detection

1. **Enable drift detection**
   - Call `PATCH /scheduling/drift-detection/environments/{id}` with `enabled: true`
   - Set cron schedule (e.g., `0 2 * * *` for daily at 2 AM)

2. **Choose remediation mode**
   - Set `autoDriftRemediation` to `CODE_TO_CLOUD` (reapply IaC) or `DISABLED` (manual only)
   - If using auto-remediation, ensure approval policies are configured

3. **Monitor drift**
   - Check drift status: `GET /environments/{id}/drift-status`
   - View drift causes: `GET /drift/causes?environmentId={id}`
   - Remediate manually: `POST /environments/{id}/remediate-drift`

## Common gotchas

- **Variable inheritance confusion**: Variables defined at organization level apply to all projects/templates/environments. Overriding at lower scopes doesn't delete the inherited variable. Use read-only variables to lock values.

- **Workspace name collision**: If you redeploy an inactive environment with the same workspace name as a remote backend environment, the new environment inherits the old state. This can cause unexpected resource conflicts.

- **TTL already passed**: When redeploying an inactive environment, if the original TTL date has passed, you must set a new TTL before deployment or it will fail.

- **Approval policy not triggering**: Policies are evaluated during plan, not apply. If a policy is assigned after an environment is created, it only applies to new deployments. Existing environments must be redeployed.

- **Drift detection not enabled by default**: Drift detection must be explicitly enabled per environment via scheduling settings. Organization-level drift policies only apply to environments created after the policy is set.

- **API key expiration**: Deleted API keys can take up to 1 hour to fully expire. Don't rely on immediate revocation for security-critical keys.

- **Template changes don't auto-apply**: Changing a template's variables, IaC version, or repository doesn't affect existing environments. You must redeploy environments to pick up template changes.

- **Sensitive variables are masked**: Once saved, sensitive variable values are masked in the UI and cannot be retrieved via API. You must update them by clearing and re-entering the value.

- **Custom flows require explicit tool installation**: If your custom flow uses AWS CLI, kubectl, or other tools, you must set `ENV0_INSTALLED_TOOLS` environment variable or the tools won't be available.

- **Destroy vs Mark as Inactive**: Both result in Inactive status, but Destroy removes cloud resources while Mark as Inactive leaves them running. Verify which action you intend before executing.

## Verification checklist

Before submitting work with envzero:

- [ ] Environment status is `ACTIVE` (or expected status for the task)
- [ ] Deployment logs show `SUCCESS` status with no errors
- [ ] All required variables are set and non-empty (check `configurationChanges`)
- [ ] Cloud resources are deployed and accessible (verify via cloud provider console)
- [ ] Approval policies have been evaluated (check Approval policies step in logs)
- [ ] Cost estimation is displayed (if cost monitoring is enabled)
- [ ] Drift detection is enabled for production environments
- [ ] TTL is set appropriately (infinite for stable, short for dev)
- [ ] API key has correct permissions for the operation
- [ ] VCS repository is accessible and branch/tag is correct
- [ ] No queued deployments are pending (check Deployments tab)

## Resources

**Comprehensive navigation:** https://docs.envzero.com/llms.txt

**Critical documentation pages:**
1. [Getting Started](https://docs.envzero.com/guides/getting-started/getting-started) - Core concepts and first deployment
2. [Environments Overview](https://docs.envzero.com/guides/admin-guide/environments) - Environment lifecycle and operations
3. [API Reference](https://docs.envzero.com/api-reference) - Complete REST API documentation

---

> For additional documentation and navigation, see: https://docs.envzero.com/llms.txt