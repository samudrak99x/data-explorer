# Agent Workflow

Use this workflow for every implementation in this repository.

## Core Rule

Each implementation must happen on its own branch and finish as a pull request.

## Issue To PR Flow

1. Read the issue and confirm the goal, scope, and acceptance criteria.
2. Inspect the current code before making changes.
3. Create a branch from `main` for the issue.
4. Keep the implementation focused on that issue.
5. Add or update tests when the change has behavior worth protecting.
6. Run the available checks before opening a pull request.
7. Push the branch and open a pull request into `main`.
8. Summarize what changed, how it was verified, and any follow-up work.

## Branch Naming

Use this pattern:

```text
feature/<issue-number>-short-description
fix/<issue-number>-short-description
chore/<issue-number>-short-description
```

Examples:

```text
feature/1-scaffold-app
feature/2-csv-upload
fix/5-invalid-csv-error
```

## Pull Request Expectations

Every pull request should include:

- Linked issue number.
- Short summary of the implementation.
- Verification steps or test results.
- Screenshots or screen recordings for user-facing UI changes when possible.
- Clear notes for anything intentionally left out of scope.

## Guardrails

- Do not mix unrelated features in one branch.
- Do not rewrite unrelated files.
- Do not merge directly into `main`.
- Do not mark work complete if checks were skipped without explanation.

