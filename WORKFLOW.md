# Agent Workflow

Use this workflow for every implementation in this repository.

For issue labels, state transitions, and the manual agent loop, also read `AGENT_LOOP.md`.

## Core Rule

Plan large work before implementation. Each implementation subtask must happen on its own branch and finish as a pull request.

## AI-DLC Flow

Use this lifecycle for feature work:

1. Intake
   - Capture the feature request, problem, user value, and constraints.
   - Create or use a planning issue for the larger feature.
2. Planning
   - Inspect the repo before proposing architecture or tasks.
   - Identify assumptions, risks, dependencies, and test strategy.
   - Define acceptance criteria for the full feature.
3. Task Breakdown
   - Split the plan into small implementation issues.
   - Each implementation issue should be independently reviewable.
   - Capture dependencies between issues when order matters.
4. Implementation
   - Create a branch from `main` for exactly one implementation issue.
   - Keep code changes focused on that issue.
   - Add or update tests when the change has behavior worth protecting.
5. Pull Request
   - Push the branch and open a pull request into `main`.
   - Link the implementation issue.
   - Include verification steps and any screenshots for UI changes.
6. Review and Merge
   - Address review feedback on the same branch.
   - Merge only after checks and review are complete.
7. Learn and Iterate
   - If the implementation reveals follow-up work, create new issues.
   - Update documentation or workflow notes when the repo learns a better pattern.

## Planning Issue Expectations

A planning issue should include:

- Problem statement.
- User or business goal.
- Proposed scope and explicit non-goals.
- Acceptance criteria for the whole feature.
- Technical notes from repo inspection.
- Risks, unknowns, and dependencies.
- Proposed implementation sub-issues.
- Suggested validation plan.

Planning issues should usually end by creating implementation issues, not by changing application code.

## Implementation Issue To PR Flow

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

- Do not start implementation for large features until a planning issue exists.
- Do not use planning branches for application code.
- Do not mix unrelated features in one branch.
- Do not rewrite unrelated files.
- Do not merge directly into `main`.
- Do not mark work complete if checks were skipped without explanation.

## Suggested First Issues

Use these as the starting AI-DLC breakdown for this empty repo:

1. Planning: define the first version of Data Explorer.
2. Implementation: scaffold the app.
3. Implementation: add CSV upload and parsing.
4. Implementation: add data preview table.
5. Implementation: add column summary statistics.
6. Implementation: add filtering and sorting.
