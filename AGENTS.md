# Repository instructions for AI agents

## Source of truth

Follow instructions in this order:

1. The current human request
2. The current GitHub Issue and its acceptance criteria
3. This file
4. Project documentation
5. Tests
6. Existing implementation

Report material conflicts instead of silently choosing one source.

## Workflow

- Inspect the relevant Issue, documentation, code, and tests before editing.
- Define observable acceptance criteria and classify risk before implementation.
- Work on a task-specific branch; do not use `main` as a normal workspace.
- Make the smallest coherent change that satisfies the Issue.
- Add or update tests for behavior changes.
- Run the relevant tests, linting, formatting, type checks, and build checks.
- Review the final diff for unrelated changes, secrets, hard-coded paths, and missing documentation.
- Prepare a Pull Request with evidence for each acceptance criterion.
- Stop at the Pull Request. Never merge into `main` without explicit human approval.

## Repository safety

- Do not commit passwords, tokens, API keys, private keys, credentials, `.env` files, datasets, checkpoints, or generated outputs.
- Do not force-push, rewrite history, delete branches, or perform destructive operations without explicit human approval.
- Keep commits focused and avoid unrelated cleanup.

## Current validation

This repository is a workflow practice repository. Until project-specific checks are added:

- Verify text-file requirements directly.
- Run `python -m compileall .` when Python files are present.
- Run `python -m pytest` when a Python test suite is present.
- Ensure GitHub Actions passes before requesting human merge approval.
- Keep lightweight tests local and in CI; use Colab only for GPU validation or workloads that need remote acceleration.
- When Colab is used, record the Git commit, environment, accelerator, configuration, and result location.

## Pull Request expectations

Every Pull Request must include:

- summary and motivation
- related Issue
- acceptance criteria with PASS / FAIL / PARTIAL / UNKNOWN
- tests and evidence
- risks and assumptions
- compatibility and documentation notes
- a short human-review focus section
