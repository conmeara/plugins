---
name: spec-to-ship
description: "Orchestrate Conmeara's current Codex development workflow from implementation idea to shipped commit. Use when the user asks to run the full dev workflow, go from spec to implementation, build tests from an HTML spec, use /goal for test-first implementation, review or simplify before shipping, or follow the personal sequence of HTML spec, review, tests, human QA, implementation, app QA, code review, simplify, commit, and push."
---

# Spec To Ship

## Purpose

Run the user's current high-trust development workflow without collapsing the gates. The shape is:

1. Build the HTML spec.
2. Review it in depth with the user.
3. Build tests from the spec.
4. Pause for the user's own QA.
5. Use Codex goals to prove the tests fail for missing implementation.
6. Use Codex goals to implement the spec until tests pass.
7. Pause for the user's app QA.
8. Run Codex code review.
9. Simplify the implementation.
10. Commit and push.

The important thing is sequencing. Do not blur spec-writing, testing, implementation, review, simplification, and shipping into one mushy "make it work" pass.

## Phase Gates

### 1. HTML Spec

Use `/html-spec` first. Build or update a repository-grounded HTML spec that makes the intended change visible before code changes begin.

The spec can cover UI behavior, prompt engineering, database redesign, video-engine architecture, agent workflow, or any other implementation idea. It should include the diagrams, state maps, tables, mocks, invariants, and test contracts the change needs, not a mandatory PRD template.

Deliverable: a browser-openable `.html` spec in the repo's docs/specs area or the user-requested path.

### 2. In-Depth Review

Treat the spec as the shared object of discussion. Review it with the user before implementation:

- Invite Codex annotations or direct comments on specific lines, sections, states, diagrams, or decisions.
- Preserve user intent over neatness. If the user pushes back, update the spec rather than defending the first draft.
- Resolve contradictions, missing states, unclear implementation boundaries, and untestable claims.
- Keep iterating until the user says the spec is ready for tests.

Deliverable: an updated spec whose open questions, choices, and implementation contract are clear enough to test.

### 3. Tests From Spec

Use `/build-tests` for this phase. It is bundled in this plugin from Addy Osmani's downloaded test-driven-development skill so we can modify it locally. Read `references/upstream-skills.md` for source links and the local workflow overlay.

Create tests that encode the spec before implementing the production code:

- Prefer behavior and state assertions over implementation-detail assertions.
- Cover the spec's critical flows, invariants, edge cases, failure paths, and regression risks.
- Use the repo's existing test patterns and file locations.
- Make tests read like executable specification sentences.

Deliverable: tests that describe the desired implementation and are expected to fail while the feature is not built.

### 4. Human QA Gate

Pause after the tests are written. The user QA's the spec and tests manually.

Do not continue to implementation until the user approves the spec/test contract or explicitly asks to proceed anyway.

### 5. Goal: Verify Red

When the user invokes this stage with Codex `/goal` or asks to use a goal, create or use a goal for the red phase.

Run the focused tests and verify they fail for the right reason:

- The failures should correspond to missing or incomplete implementation, not broken setup, syntax errors, incorrect imports, or wrong assumptions in the tests.
- Fix test mistakes until the red phase is meaningful.
- Do not implement production code in this phase except for unavoidable test harness scaffolding.

Deliverable: a clear red-phase result naming the failing tests and why the failures are expected.

### 6. Goal: Implement To Green

Use a Codex goal for implementation when the user invokes this stage with `/goal` or asks for goal-tracked implementation.

Implement everything stated in the approved HTML spec, using the tests as the completion contract:

- Keep edits scoped to the spec.
- Run the focused tests repeatedly until they pass.
- Run broader relevant tests when the change touches shared systems.
- Update the spec only when implementation reveals a real product or architecture decision that the spec should capture.

Deliverable: implementation complete against the spec with passing verification.

### 7. Human App QA Gate

Pause for the user's own app testing. If the app has a UI or runtime surface, help launch it and point the user to the right URL/window/state, but do not treat automated tests as a substitute for this gate.

If the user reports issues, return to the smallest necessary phase: spec update, test update, or implementation fix.

### 8. Codex Code Review

Run a code-review pass before simplification and shipping:

- Lead with bugs, regressions, missing tests, risky behavior, and scope creep.
- Inspect staged, unstaged, and untracked changes when reviewing local work.
- Treat the approved spec and tests as the review contract.
- Fix actionable issues before proceeding.

Deliverable: no unresolved blocking review findings, or a clear user decision to proceed with known risks.

### 9. Simplify

Use `/simplify` for this phase. It is bundled in this plugin from Addy Osmani's downloaded code-simplification skill so we can modify it locally. Read `references/upstream-skills.md` for source links and the local workflow overlay.

Simplify only after behavior works and tests pass:

- Preserve behavior exactly.
- Scope simplification to the changed implementation unless the user asks to broaden.
- Prefer clarity and project conventions over cleverness or fewer lines.
- Run tests after simplification.

Deliverable: cleaner implementation with behavior still verified.

### 10. Commit And Push

Only commit and push after the gates are satisfied:

- Spec reviewed.
- Tests prove the contract.
- Implementation passes.
- User app QA is complete or the user explicitly accepts skipping it.
- Code review issues are resolved or accepted.
- Simplification did not change behavior.

Use the repo's normal branch, commit, and push conventions. Summarize the commit hash, branch, and remote push result.

## Operating Rules

- Keep the current phase visible in status updates.
- Do not skip a human gate silently.
- Do not implement production code before the red-phase tests are meaningful.
- Do not simplify before tests are green.
- Do not push with known failing relevant tests unless the user explicitly chooses to.
- When a phase uncovers a wrong assumption, update the spec first if it changes the intended behavior.
- Keep artifacts together: spec path, test files, implementation files, review notes, verification commands, commit/push result.

## Reference

Read `references/upstream-skills.md` when entering the testing or simplification phases, or when the user asks how this workflow relates to the upstream Addy Osmani skills.
