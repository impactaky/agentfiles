# Workflow

You need to follow the steps strictly.
Proceed through the steps autonomously unless blocked, destructive approval is required, or user input is necessary to resolve ambiguity.

## Principles

- Keep the task small enough that one agent can implement and review it with sufficient attention
- Prefer simple, reviewable changes
- Reuse existing libraries and project patterns when they fit
- Keep only tests tied to the user request
- Remove scaffolding tests before finishing
- Use a subagent only when the task is too large, too parallel, or too review-heavy for one focused pass

## `dod.md` Format

```md
## User request

- [ ] <What the user asked for, restated concretely and minimally>

## Relevant context

- [ ] <Confirmed fact from the repository, API, requirements, or runtime behavior>

## Required changes based on facts

- [ ] <Concrete change required by the facts above>

## Constraints

- [ ] <Implementation or scope constraint derived from the facts above>

## Verification for user request

- [ ] <Test, command, manual check, or review point that confirms the user request is satisfied>

## Deferred

- <Unresolved item that is safe to postpone>
```

## Steps

Please output `== X. Phase name ==` before starting each phase

### 1. Prepare DoD

- [ ] Confirm the relevant facts from the user request and current repository context
- [ ] If critical ambiguity remains, ask the user in one batch before implementation
- [ ] Create `.myagents/dod.md` with User request, Relevant context, Required changes, Constraints, Verification for user request, and Deferred

### 2. Implement

Repeat Steps 2 and 3 until implementation and review pass, up to 5 times.

- [ ] Implement the change to satisfy `.myagents/dod.md`

### 3. Internal Review

- [ ] Review the implementation against `.myagents/dod.md` and `project-rules.md`
- [ ] If review finds issues, return to Step 2

#### Review Points

- Check for defects, regressions, test gaps, unnecessary complexity, and avoidable custom code
- Report findings first, ordered by severity, with file references
- End review with an explicit pass/fail decision

### 4. User Review

- [ ] Output the user review report. And wait user action. Don't propose next step. Don't commit.
- [ ] If the user requests follow-up changes, rerun Steps 2 and 3
- [ ] If follow-up fixes a reusable review issue, update `project-rules.md` before rerunning Steps 2 and 3

#### User Review Format

```md
## Review report

### Request
- <Request>

### Before
- <Before state>
- <Why it was not satisfied>

### Resolution
- [path/to/file.ext:line] <Change>. <Why it matters>
- [path/to/file.ext:line] <Change>. <Why it matters>
```

- `Resolution` must cover all meaningful changes.
- Each bullet must include a file path and line.
- Each bullet must say what changed and why.
