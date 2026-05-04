# GitHub Agent Loop

This repo uses GitHub Issues and Pull Requests as a lightweight Symphony-style loop.

## Loop Goal

Turn GitHub into the control plane for AI-assisted development:

```text
planning issue -> implementation issues -> ready label -> agent branch -> pull request -> review -> merge
```

## Labels

Use these labels as the issue state machine:

```text
planning
implementation
ready
in-progress
blocked
needs-review
follow-up
done
```

## State Transitions

### Planning

Use `planning` for larger feature design work.

Exit criteria:

- Feature scope is clear.
- Acceptance criteria are written.
- Risks and dependencies are listed.
- Implementation subtasks are created as separate issues.

Next state:

- Close the planning issue when the subtask issues exist.
- Mark implementation issues as `ready` when they are unblocked.

### Ready

Use `ready` for implementation issues an agent can pick up.

Entry criteria:

- The issue has a clear goal.
- Acceptance criteria are specific.
- Dependencies are resolved or listed.
- The issue is small enough for one focused pull request.

Next state:

- Move to `in-progress` when an agent starts work.

### In Progress

Use `in-progress` while an agent is actively implementing the issue.

Agent responsibilities:

- Create a branch from `main`.
- Implement only the linked issue.
- Run available checks.
- Push the branch.
- Open a pull request into `main`.

Next state:

- Move to `needs-review` after the pull request is open.

### Needs Review

Use `needs-review` when a pull request is ready for human review.

Exit criteria:

- Review feedback is addressed.
- Checks pass or skipped checks are explained.
- The pull request is merged.

Next state:

- Move to `done` or close the issue through the linked pull request.

### Blocked

Use `blocked` when implementation cannot safely continue.

The issue must explain:

- What is blocked.
- What decision, dependency, or information is needed.
- Who or what can unblock it.

### Follow Up

Use `follow-up` for work discovered during planning, implementation, or review that should not be mixed into the current pull request.

## Manual Agent Loop

Until there is a daemon that watches GitHub automatically, run this loop manually:

1. Find the oldest open issue with `ready` and without `blocked`.
2. Assign it to the agent by asking Codex to work that issue.
3. Change the label from `ready` to `in-progress`.
4. Let the agent create a branch and pull request.
5. Change the label to `needs-review`.
6. Review and merge the pull request.
7. Close the issue or let the pull request close it with `Closes #<issue>`.
8. Repeat.

## Agent Start Prompt

Use this prompt when starting work on an implementation issue:

```text
Work issue #<number> using WORKFLOW.md and AGENT_LOOP.md.

Create a new branch from main, implement only this issue, run available checks,
push the branch, and open a pull request into main. Link the PR with
"Closes #<number>".
```

## Automation Path

The manual loop can later become a small daemon or GitHub Action:

1. Poll GitHub Issues for `ready` issues.
2. Claim one issue by changing `ready` to `in-progress`.
3. Create an isolated workspace for that issue.
4. Start a coding agent with the issue body and repo workflow docs.
5. Watch for branch, pull request, checks, and review status.
6. Move labels forward as the work progresses.

The first version should remain conservative: one issue at a time, one branch per issue, and human review before merge.

