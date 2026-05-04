# Data Explorer

Data Explorer is a small app project for exploring uploaded datasets.

## AI-DLC Development Flow

This repo uses an AI-assisted development lifecycle: plan first, split work into issues, then implement each issue through its own branch and pull request.

1. Capture a feature idea as a planning issue.
2. Expand the idea into goals, assumptions, risks, and acceptance criteria.
3. Break the plan into small implementation issues.
4. Create one branch per implementation issue.
5. Implement only that issue's scope.
6. Run the available checks.
7. Open a pull request back to `main`.
8. Review, update, and merge.

Branch names should be short and issue-focused:

```text
feature/1-scaffold-app
feature/2-csv-upload
fix/7-empty-file-error
```

Planning issues should not contain implementation code changes. Their job is to create clear, reviewable sub-issues that can move through the branch-and-PR flow independently.
