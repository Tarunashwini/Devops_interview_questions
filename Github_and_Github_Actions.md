# GitHub & GitHub Actions Interview Q&A (100+) — Study Guide


## GitHub Interview Questions (55)

**1. What is GitHub and how is it different from Git?**

Git is a distributed version control system; GitHub is a hosted platform built on top of Git that adds collaboration features like pull requests, issues, code review, permissions, CI/CD (Actions), and project management.

**2. Explain the difference between a fork and a clone.**

Clone creates a local copy of a repository. Fork creates a new repository under your GitHub account that is linked to the upstream repo, enabling you to propose changes via pull requests without write access.

**3. What is a pull request (PR)?**

A PR proposes merging changes from one branch or fork to another. It enables code review, automated checks, and discussion before merge.

**4. Merge vs Rebase—when would you use each on GitHub?**

Merge preserves commit history; rebase rewrites it to be linear. Use merge for traceability on shared branches; rebase your feature branch to keep history clean before opening/merging a PR.

**5. GitHub Flow vs Git Flow—difference?**

GitHub Flow is lightweight: main branch + short-lived feature branches & PRs. Git Flow adds long-lived develop, release, and hotfix branches, suitable for scheduled releases.

**6. What are protected branches?**

Branch protection rules prevent force-pushes, require PR reviews, passing checks, signed commits, linear history, and status checks before merging to critical branches like main.

**7. How do you squash commits in a PR?**

Use 'Squash and merge' in the PR UI, or rebase interactively locally (git rebase -i) and force-push. Squash produces a single commit on the target branch.

**8. How do you resolve merge conflicts in GitHub?**

Pull the conflicting branches locally, fix conflicts in files, add and commit. Alternatively, use GitHub’s conflict editor if enabled; ensure tests and checks pass after resolving.

**9. What are draft pull requests?**

Draft PRs signal work-in-progress. They run checks (unless disabled) but can’t be merged until marked 'Ready for review'.

**10. What is CODEOWNERS and why use it?**

CODEOWNERS maps file path patterns to owners. It automatically requests reviews and can be required for merges via branch protection.

**11. How does GitHub handle large files?**

Use Git LFS to store large binary files outside normal Git history, keeping repo sizes manageable. Configure tracking and ensure LFS is enabled in the repo/org.

**12. What is the difference between Issues and Discussions?**

Issues track actionable work with states. Discussions enable open-ended Q&A/ideation. Convert between them when appropriate.

**13. How do you link commits/PRs to Issues?**

Use keywords like 'Fixes #123' in commit messages or PR descriptions to auto-close issues when merged and to create traceability.

**14. What is a release in GitHub?**

A release is a snapshot based on a tag with notes and downloadable assets; it is used to package and distribute software versions.

**15. What’s semantic versioning and how do you handle it on GitHub?**

SemVer uses MAJOR.MINOR.PATCH. Enforce via tag names, release automation, changelogs, and checks that gate breaking changes.

**16. How do you review code effectively on GitHub?**

Use small PRs, review commit-by-commit, comment with suggestions, request changes when needed, and ensure checks are green before approval.

**17. What’s a signed commit and how do you enforce it?**

A commit signed with GPG/SSH attests authorship. Enforce via branch protection 'require signed commits' and educate devs to sign locally.

**18. How do you handle monorepos on GitHub?**

Use path-based CODEOWNERS, required checks scoped by paths, sparse-checkout, partial clones, and tooling like Nx/Bazel to limit builds/tests.

**19. What is Dependabot?**

GitHub’s dependency scanner and updater that opens PRs for vulnerable/outdated dependencies; combine with security advisories and code scanning.

**20. How do you enforce PR quality at org level?**

Org policies, required reviews, templates, checklists, status checks, required conversations resolved, and auto-merge rules.

**21. What is a fork sync and how do you keep forks updated?**

Pull upstream changes into your fork by adding upstream remote and merging/rebasing; or use GitHub 'Sync fork' button.

**22. How do you speed up cloning very large repos from GitHub?**

Use shallow clones (depth), partial clone, sparse-checkout, or mirror clones if needed.

**23. How do you manage permissions in GitHub?**

Use orgs, teams, repo roles (read, triage, write, maintain, admin), and fine-grained personal access tokens for automation.

**24. What are fine-grained PATs vs classic PATs?**

Fine-grained tokens are scoped to specific repos and permissions with expiration; classic tokens are broader and being phased out.

**25. How do you migrate repos to GitHub?**

Use GitHub Importer, 'git push --mirror', or GH Enterprise migration tools; plan for users, issues, attachments, and CI migration.

**26. How do you build a good PR description?**

Explain context, changes, testing, risks, roll-back plan, and link issues. Use PR templates to standardize.

**27. How to revert a merged PR?**

Use 'Revert' button to create a new PR that inverses the commit(s), or locally 'git revert -m 1 <merge-commit>' for merge commits.

**28. How to handle binary files review on GitHub?**

Avoid in PRs; store binaries via LFS or as release assets; if necessary, include checksums and document generation steps.

**29. What is a submodule and its pitfalls?**

A submodule pins another repo at a specific commit. Pitfalls: detached HEADs, needing explicit updates, and added complexity for contributors.

**30. How do you implement code owners for microservices within a monorepo?**

Create path rules per service (e.g., services/api/**) mapped to teams; require owner approvals via branch protection.

**31. How do you handle confidential data in GitHub?**

Use secret scanning, block pushes with secrets, use environments/Actions secrets, and avoid committing secrets; rotate if leaked.

**32. How do you enforce changelog updates?**

Require a changelog label/check in PRs, use release-please or semantic-release, and gate merges when missing.

**33. How do you automatically label PRs?**

Use labeler (actions/labeler) with path rules or semantic PR titles, plus bots like Probot to enforce conventions.

**34. What’s the best way to manage multiple repositories?**

Use org teams and CODEOWNERS, reusable workflows, repository templates, and governance policies across the org.

**35. What is a repository template?**

A repo marked as a template lets you create new repos pre-populated with chosen files and settings; good for standardizing setups.

**36. How do you measure repo health?**

Track PR throughput/lead time, review latency, flaky tests, security alerts, release cadence; use Insights and third-party analytics.

**37. How do you enforce linear history?**

Enable 'Require linear history' in branch protection and use rebase merges or squash merges; avoid merge commits.

**38. How to handle large histories?**

Use git filter-repo to rewrite history (e.g., to remove secrets or large files) and force-push after coordinating downtime.

**39. How do you triage issues efficiently?**

Use issue templates, forms, labels, assignees, milestones, and saved replies. Automate stale issue handling as needed.

**40. How do you secure GitHub organizations?**

Enable SSO/2FA, restrict PATs, review third-party app access, enforce SAML, and audit via org security overview.

**41. How do you manage binaries and artifacts?**

Use GitHub Releases and Packages registries (npm, Maven, Docker) with proper permissions and retention policies.

**42. What is GitHub Pages and typical use case?**

Static site hosting from a branch/folder; use for docs, portfolios, or project pages with CI to build and deploy.

**43. How to implement ADRs in a repo?**

Store Architecture Decision Records in /docs/adr; require an ADR for significant changes and review via PRs.

**44. How do you automate backports?**

Use labels/PR titles and a backport bot or Action to cherry-pick merged commits to release branches.

**45. What is a commit convention (e.g., Conventional Commits)?**

A structured commit message format enabling automated changelogs, semantic versioning, and enforceable via checks.

**46. How to handle multi-PR features?**

Use feature branches, 'tracking issues', or 'umbrella PRs' that link sub-PRs; merge behind feature flags.

**47. How to avoid 'works on my machine'?**

Use devcontainers/Codespaces, lock dependency versions, pre-commit hooks, and CI parity with local tooling.

**48. How do you discover flaky tests?**

Rerun strategies, test impact analysis, quarantine labels, and dashboards to track flake rate over time.

**49. How do you use GitHub CLI (gh) for PR workflows?**

gh pr create, gh pr checkout, gh pr view; script reviews, comments, and merge actions to speed up developer flow.

**50. What are organization-level secrets/variables?**

Reusable across repositories with access policies for selected repos; helps centralize shared credentials and config.

**51. How to implement CODEOWNERS exceptions?**

Order matters; the last matching rule wins. Add specific path rules after broad ones to tailor ownership.

**52. How to govern licenses and IP?**

Add LICENSE, DCO/CLA checks, require sign-offs, and scan dependencies for license compliance before release.

**53. Additional GitHub topic #53: scenario-based question**

Discuss approach, trade-offs, risks, and how to validate with PR checks, code owners, and branch protections.

**54. Additional GitHub topic #54: scenario-based question**

Discuss approach, trade-offs, risks, and how to validate with PR checks, code owners, and branch protections.

**55. Additional GitHub topic #55: scenario-based question**

Discuss approach, trade-offs, risks, and how to validate with PR checks, code owners, and branch protections.


## GitHub Actions Interview Questions (55)

**1. What is GitHub Actions?**

A CI/CD and automation platform built into GitHub. It runs workflows on events (push, PR, schedule, etc.) using hosted or self-hosted runners.

**2. Workflow vs Job vs Step?**

Workflow: top-level automation file. Job: group of steps that run in the same runner. Step: an individual action or shell command within a job.

**3. What triggers can start a workflow?**

Events like push, pull_request, release, workflow_dispatch (manual), schedule (cron), issue_comment, repository_dispatch and many more.

**4. How do runners work?**

Jobs run on ephemeral GitHub-hosted VMs/containers or your own self-hosted machines. Matrix strategy fans out parallel jobs.

**5. How do you pass secrets?**

Store secrets in repo/org/environment settings and reference via ${{ secrets.NAME }}. Never echo secrets; mask outputs.

**6. What are environments in Actions?**

Named stages (e.g., dev, prod) with scoped secrets, required reviewers, and protection rules for deployments.

**7. How do you cache dependencies?**

Use actions/cache with a key based on lockfiles. Restore speeds up builds; update key when deps change.

**8. What is a reusable workflow?**

A sharable workflow called via workflow_call from other workflows, promoting DRY pipelines across repos.

**9. How to share logic across jobs?**

Use composite actions, reusable workflows, or action-repo checkouts; pass inputs/outputs between steps/jobs via outputs and artifacts.

**10. How to create and publish a custom action?**

Create a repo with action.yml, implement as JavaScript or Docker action, version with tags, and document inputs/outputs.

**11. How to set env vars?**

Use env: at workflow/job/step scope or echo 'NAME=value' >> $GITHUB_ENV to set dynamically for later steps.

**12. How to handle artifacts?**

Upload with actions/upload-artifact and download later. Useful for test reports, binaries, coverage, etc.

**13. How to handle monorepos in Actions?**

Use path filters and 'paths'/'paths-ignore' to run jobs only when relevant folders change; matrix by package path.

**14. Self-hosted runner—when and why?**

Needed for custom hardware, private networking, licensed tools, or long-running workloads. Secure and auto-update runners.

**15. How to secure secrets from PRs from forks?**

By default secrets are not passed to workflows for forked PRs. Use 'pull_request_target' carefully with hardened patterns.

**16. pull_request vs pull_request_target?**

pull_request runs in the context of the source branch; pull_request_target runs in the base repo context (has secrets)—use only with trusted code.

**17. How to gate deploys on approvals?**

Use environments with required reviewers, or manual approval jobs, or status checks on PRs.

**18. How to do matrix builds?**

Use strategy.matrix to test across OS, language versions, or dependency sets. Combine with include/exclude.

**19. How to speed up builds?**

Cache dependencies, reuse containers, limit triggers/paths, split slow tests, and run in parallel with matrix.

**20. How to persist data between jobs?**

Artifacts and job outputs; or use a shared cache. Jobs are isolated runners, so no shared filesystem by default.

**21. How to conditionally run a job/step?**

Use 'if:' expressions (e.g., if: github.ref == 'refs/heads/main'). Combine with success(), failure(), cancelled() contexts.

**22. How to handle deployment secrets safely?**

Store per-environment, use OIDC to cloud providers for short-lived tokens instead of static keys.

**23. What is OIDC in GitHub Actions?**

OpenID Connect trust between GitHub and cloud provider to exchange a short-lived token for cloud access without long-lived secrets.

**24. How to reuse job outputs?**

Set outputs in one job and refer in dependent jobs via needs.<job_id>.outputs.<name>.

**25. How to run Docker in Actions?**

Use Docker actions or setup Docker, build images, and push to registries. For DinD, use appropriate service containers or privileged runners.

**26. What are services in a job?**

Ephemeral containers (e.g., Postgres, Redis) spun up for a job, accessible via localhost:port.

**27. How to test and lint Actions workflows?**

Use actionlint locally/CI; create small sample repos; leverage --dry-run for actionlint and YAML schema validation.

**28. How to handle concurrency?**

Use 'concurrency:' to cancel in-progress runs in the same group, preventing duplicate deployments.

**29. How to require successful checks before merge?**

Protect branches to require specific checks (workflow jobs) to pass before PRs can merge.

**30. How to build a reusable workflow library across org?**

Create a dedicated repo 'org/actions' with versioned reusable workflows and pin consumers to tags/SHAs.

**31. How to pin third-party actions securely?**

Pin to a specific commit SHA; avoid 'latest'. Regularly update; use Dependabot for actions.

**32. How to pass data between steps?**

Use step outputs: echo 'name=value' >> $GITHUB_OUTPUT, then reference via steps.id.outputs.name.

**33. How to fail a workflow intentionally?**

Exit non-zero in a run step, or use 'fail-fast' in matrix; use assertions in scripts and test runners.

**34. How to skip jobs for docs-only changes?**

Use paths-ignore with patterns for docs; or conditionally check changed files list via actions/checkout + git diff.

**35. How to run on schedule?**

Use 'schedule:' with cron expressions in UTC; avoid overlapping runs using 'concurrency' or job conditions.

**36. How to mask sensitive logs?**

GitHub masks ${{ secrets.* }} automatically; additionally add '::add-mask::value' to hide custom secrets.

**37. How to debug failing jobs?**

Enable step debug logs (ACTIONS_STEP_DEBUG), add 'continue-on-error: true' for exploratory steps, or use tmate debugging action on trusted branches.

**38. How to share code across actions?**

Use composite actions for shell-based logic; publish JS/Docker actions for reusable blocks across repos.

**39. How to deploy to AWS from Actions?**

Use OIDC with aws-actions/configure-aws-credentials, then run CLI/CDK/Terraform commands; avoid long-lived keys.

**40. How to implement canary deploys with Actions?**

Model stages as jobs (build→deploy-staging→tests→deploy-prod), gate prod with approvals, and use progressive rollout scripts.

**41. What is job 'needs'?**

Defines dependencies and execution order; allows fan-out/fan-in patterns.

**42. How to handle monorepo selective tests?**

Use a script to detect changed packages and create a dynamic matrix for only impacted test suites.

**43. How to use composite actions for DRY setup?**

Encapsulate repeated steps like setting up language tools, caching, and lint/test commands in a composite action.

**44. How to store build numbers and changelogs?**

Publish artifacts, release notes via actions/create-release, or push tags; generate changelogs with release-please.

**45. How to run workflows on specific paths only?**

Use 'paths' and 'paths-ignore' at trigger level; for more control, use a first job to compute conditions.

**46. How to ensure idempotent deployments?**

Use declarative IaC (Terraform/CloudFormation), tags, and checks; re-running the job should yield same state.

**47. How to manage long-running jobs?**

Increase timeouts as needed, use self-hosted runners, checkpoint via artifacts, or split into smaller stages.

**48. How to enforce minimum test coverage?**

Run coverage tools and fail the job if threshold is not met; expose a coverage badge.

**49. How to set default permissions?**

Use 'permissions:' at workflow level to set least-privilege (e.g., contents: read). Grant write only when needed.

**50. What are workflow run artifacts retention limits?**

Artifacts have retention policies (default is limited days). Configure per workflow or at repo level to manage storage costs.

**51. How to run a workflow from another repo?**

Use repository_dispatch (API) or call a reusable workflow across repos with workflow_call and proper permissions.

**52. How to prevent secret exfiltration in PRs?**

Never run untrusted code with write tokens. Use pull_request (not target), disable dangerous actions, and add policy checks.

**53. How to build containers with Buildx and cache?**

Use docker/setup-buildx-action and build-push-action with cache-from/cache-to to speed multi-platform builds.

**54. How to use matrices with include/exclude smartly?**

Define base axes then 'include' for special cases; 'exclude' to remove combinations, keeping matrix efficient.

**55. How to make workflows composable with inputs?**

Expose 'inputs:' in workflow_call and use defaults, required flags, and types for safer consumption.


## Important Concepts & Tricks

- **Master the Fundamentals** — Practice core Git commands (add/commit/branch/rebase/merge/cherry-pick/revert) and understand objects (blob/tree/commit/tag).
it
- **Branching Strategy Clarity** — Be ready to explain GitHub Flow vs Git Flow and when to use each. Tie to your release cadence.

- **Code Review Excellence** — Small PRs, clear descriptions, link issues, request specific feedback; use CODEOWNERS to route reviewers.

- **Security Hygiene** — Use protected branches, required checks, signed commits, Dependabot, and secret scanning. Rotate leaked secrets.

- **Actions Hardening** — Least-privilege 'permissions:', pin third-party actions by SHA, avoid pull_request_target for untrusted code, and use OIDC.

- **Performance & Cost** — Cache dependencies, narrow triggers with 'paths', use matrices wisely, and set artifact retention policies.

- **Monorepo Patterns** — Path filters, dynamic matrices, per-folder CODEOWNERS, and selective builds/tests.

- **Debugging Playbook** — Enable step debug logs, artifact logs, reruns with diagnostics, and tmate for trusted branches.

- **Interview Storytelling** — Use STAR (Situation, Task, Action, Result). Bring 2–3 concrete CI/CD incidents (a failure you fixed, a rollout you improved).

- **Hands-on Prep** — Build a sample repo with a complete workflow: lint, test, build image, scan, deploy to a sandbox using OIDC.



To know more about Github Actions click [here](https://github.com/lm-academy/github-actions-course)
