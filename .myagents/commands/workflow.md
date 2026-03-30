# Workflow

This is the workflow to develop.
You need to follow the steps strictly.
Proceed through the steps autonomously unless blocked, destructive approval is required, or user input is necessary to resolve ambiguity.

## Input

User request.

## Output

DoD check report.
Explain how the implementation satisfies the required changes and verification items,
grounded in the collected facts.
Output the DoD report in Japanese.

## Steps

- [ ] Confirm the relevant facts from the user request and current repository context
- [ ] Create `dod.md` at the repository root using the format below
- [ ] Derive `Required changes based on facts`
- [ ] Define `Verification`
- [ ] Put unresolved blocking items in `Open Questions`
- [ ] Put safe-to-postpone items in `Deferred`
- [ ] If `Open Questions` is non-empty, ask the user in one batch and update `dod.md`
- [ ] Do not proceed to implementation while `Open Questions` is non-empty
- [ ] Loop until implementation and review pass. Up to 5 times.
  - [ ] Implement the change to satisfy `dod.md` in `programmer` agent
  - [ ] Review the implementation against `dod.md` and `project-rules.md` if present in `reviewer` agent
- [ ] Output the DoD check report in Japanese.
- [ ] Wait for user review. If you get feedback, rerun the implementation loop.
- [ ] Update `dod.md` to match the final result
- [ ] Ensure `Open Questions` is empty
- [ ] Save a copy to `.myagents/artifacts/dod/<task-summary>-<timestamp>.md`
- [ ] If the feedback is essential, reflect it in `project-rules.md` to improve future runs.

## `dod.md` Format

```md
# Definition of done

## Facts

- [ ] <Confirmed fact from the repository, API, requirements, or runtime behavior>
- [ ] <Why this fact matters to the requested change>

## Required changes based on facts

- [ ] <Concrete change that becomes necessary once the facts above are confirmed>
- [ ] <Scope or implementation constraint derived from those facts>

## Verification

- [ ] <How to confirm the change is correct>
- [ ] <Command, test, manual check, or review point with a verifiable result>

## Open Questions

- <Critical ambiguity that blocks confirmation, change design, or verification>

## Deferred

- <Unresolved item that is safe to postpone>
```

## Rules

- Keep `dod.md` items specific and verifiable
- Treat `dod.md` as the editable working copy until finalization
- Keep the archived DoD filename short and filesystem-safe
- Use a sortable timestamp such as `YYYYMMDD-HHMMSS`
