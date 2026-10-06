# git-practice

Practice repository for a human-in-the-loop GitHub workflow using Codex and VS Code.

## Development workflow

1. Define the task and acceptance criteria in a GitHub Issue.
2. Create a focused branch from `main`.
3. Let Codex edit repository files directly while VS Code is used for inspection, debugging, and diff review.
4. Run local checks and review the final diff.
5. Push the branch and open a Pull Request.
6. Wait for CI and human review.
7. Merge only after explicit human approval.

Repository-specific instructions for Codex and other AI agents are in [AGENTS.md](AGENTS.md).

## Local tools

- Git and GitHub CLI for version control and GitHub operations
- VS Code for code, diffs, notebooks, and debugging
- Codex for implementation and review
- Python 3.13 for local scripts and tests

Google Colab/GPU integration is intentionally deferred until the local workflow is verified.
