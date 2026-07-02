# Suggested Demo Path

## Opening story

"In discovery, we learned that your teams already have tools they like: GitHub, Jenkins, GitLab, Jira, ServiceNow, Kubernetes, and security scanners. The problem is not that these tools are bad. The problem is that leadership lacks end-to-end visibility, release coordination is manual, and governance is inconsistent. CloudBees Unify helps connect and orchestrate the toolchain without forcing a rip-and-replace migration."

## Suggested flow

1. Show the repo structure and explain that teams can keep their existing tools.
2. Show `.github/workflows/ci.yml` as an example of existing external CI.
3. Run `.cloudbees/workflows/ci.yaml` to show a standardized CloudBees build/test/security pattern.
4. Run `.cloudbees/workflows/deploy.yaml` to show a component deployment.
5. Pick one staged release workflow and run it end to end:
   - `release-finsure-bank.yaml` for regulated financial services (governance → staging → validation → approval → production → evidence)
   - `release-horizon-health.yaml` for healthcare/platform engineering (QA → validation → staging → summary)
6. Use `policies/` to explain governance and approvals.
7. Use `mock-data/` to explain release evidence and auditability.
8. (Optional) In the Unify Workflow Composer, add a real manual approval gate where the `production-approval` step is, to show governance live.
9. Close with business outcomes: visibility, governance, orchestration, developer productivity, and preserving existing tool investments.

> Note: every workflow is self-contained and mock/echo-based, so each one runs green on its own with no clusters, secrets, or integrations. The application-orchestration story (one platform workflow driving many components) is now told through the staged release workflows rather than a separate `deployer.yaml`.
