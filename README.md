# Applied AI Systems Architecture & Engineering

Systems work spanning agent orchestration, tool integration, stateful workflows and reproducible verification.

## Explore the work

[Capability showcase](https://github.com/Khemology/capability-showcase) — selected synthetic demonstrations with source, execution instructions, scope notes and automated checks.

| Area | Demonstrated behavior |
| --- | --- |
| Stateful execution | Validated calculations, conditional routing, bounded execution and synthetic order previews |
| Workflow automation | Record lookup, filtering, guarded synthetic changes and rejection checks |
| Engineering verification | Deterministic Python tests and isolated native n8n execution in GitHub Actions |

[![Verify public capabilities](https://github.com/Khemology/capability-showcase/actions/workflows/verify.yml/badge.svg)](https://github.com/Khemology/capability-showcase/actions/workflows/verify.yml)

Public examples remain disconnected from private systems. Scripted fixtures, tested integrations and live inference are identified separately. The showcase documents what each example proves and what remains unverified.

## Hands-on learning

- [GitHub Actions practice](https://github.com/Khemology/skills-hello-github-actions): event-triggered workflow and verified pull-request comment.
- [Testing and coverage practice](https://github.com/Khemology/skills-test-with-actions): intentional failure, corrected assertion, error-path tests, Python version matrix and an enforced coverage merge gate. Final result: seven passing tests and 100% statement coverage of the exercise's small calculation module.

- [Pull-request review practice](https://github.com/Khemology/skills-review-pull-requests): assignment, COMMENT reviews, an inline suggested edit applied through GitHub and verified merge. Same-account practice; independent peer approval is not claimed.

- [Reusable workflows practice](https://github.com/Khemology/skills-reusable-workflows): shared quality checks, 33 unit tests, 6 browser tests, static deployment and returned output. [Instructor game](https://khemology.github.io/skills-reusable-workflows/) has a separately documented live-site smoke check.

- [CodeQL practice](https://github.com/Khemology/skills-introduction-to-codeql): actual SQL-injection finding, diagnosed runtime failure and verified SQLite parameterization. Six regression checks pass and the alert is fixed on main.

- [Release and hotfix practice](https://github.com/Khemology/skills-release-based-workflow/blob/main/completion-notes.md): published beta, stable and hotfix versions; real Chromium checks reproduced the introduced visual regression and verified recovery at the recorded tag commits.

- [Supply-chain security practice](https://github.com/Khemology/skills-secure-repository-supply-chain/blob/main/completion-notes.md): reproduced and repaired a package vulnerability, reviewed and tested a genuine Dependabot security update, and verified version-update proposal generation. The legacy training application retains known findings and is not production ready.

These follow official GitHub Skills exercises. Course-derived work is attributed and kept separate from original capability demonstrations. Completion is determined from actual workflow and review results; these exercises demonstrate specific engineering mechanisms.
