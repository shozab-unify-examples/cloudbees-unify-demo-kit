# CloudBees Unify Candidate Demo Kit

A lightweight starter kit for SE candidates building a CloudBees Unify demo as part of an interview.

**Everything here is self-contained and mock/echo-based.** The workflows run green in any CloudBees Unify organization with **no clusters, secrets, registries, or third-party integrations required**. Fork it, connect it to Unify, and click **Run** — you get a clean, presentable pipeline in minutes. Then tailor the names and story to your chosen scenario.

## Quick start

1. **Fork** this repository.
2. **Connect** the fork to your CloudBees Unify organization.
3. Open any workflow under `.cloudbees/workflows/` and click **Run workflow** — they all succeed on their own with mock output.
4. Pick a scenario and present the matching staged release workflow.

That's it. No setup beyond connecting the repo.

## What is included

Workflows (all runnable standalone via **Run workflow**):

- `.cloudbees/workflows/ci.yaml` — CI: validate → unit tests → security scan → package (mock)
- `.cloudbees/workflows/deploy.yaml` — standalone component deploy (renders the sample k8s manifest, client-side `kubectl` dry-run — no live cluster)
- `.cloudbees/workflows/release-finsure-bank.yaml` — staged, **regulated** release: governance → staging → validation → approval → production → evidence
- `.cloudbees/workflows/release-horizon-health.yaml` — standardized **golden-path** release: QA → validation → staging → summary
- `.github/workflows/ci.yml` — GitHub Actions CI alternative, to show external-toolchain integration

Supporting assets (used as evidence / talking points):

- `k8s/` — Kubernetes manifests for a simple demo app
- `helm/unify-demo-app/` — basic Helm chart for deployment storytelling
- `manifests/` — sample release manifests per scenario
- `policies/` — mock governance, approval, and change-control YAML
- `mock-data/` — mock Jira, ServiceNow, security, and release evidence data

## The two scenarios

- **FinSure Bank** (`release-finsure-bank.yaml`) — regulated financial services. Emphasize governance, auditability, risk, change tickets, and production approvals.
- **Horizon Health Systems** (`release-horizon-health.yaml`) — healthcare / platform engineering. Emphasize developer experience, release standardization, and health-data compliance. (In this scenario `payments-api` is intentionally not deployed.)

## Suggested demo path

1. Show the repo structure — teams keep their existing tools; Unify orchestrates.
2. Run `ci.yaml` to show a standardized build/test/security pipeline.
3. Run `deploy.yaml` to show component deployment.
4. Run the staged release workflow for your chosen scenario (FinSure or Horizon) to tell the end-to-end story.
5. Use `policies/` and `mock-data/` as governance and audit-evidence talking points.
6. Close on business outcomes: visibility, governance, orchestration, developer productivity, and preserving existing tool investments.

## Customizing

These are intentionally simple building blocks. To make the demo yours:

- Rename the application/components to fit your scenario (e.g. `Customer Portal` / `orders-api`).
- Adjust the mock component versions in the release workflows.
- Add a real manual **approval gate** in the Unify Workflow Composer where the `production-approval` talking-point step is.
- Add or remove a tool integration to match the customer's toolchain.
