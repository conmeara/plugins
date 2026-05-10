# Downloaded Upstream Skills Used By This Workflow

The plugin includes local downloaded copies of these upstream skills. Treat the local files as editable working copies for Conmeara's workflow.

## Test-Driven Development

Source: https://github.com/addyosmani/agent-skills/blob/main/skills/test-driven-development/SKILL.md

Local command name: `/build-tests`

Local file: `../build-tests/SKILL.md`

Workflow overlay:

- Write tests before production implementation.
- Red phase must fail for the right reason.
- Tests are the executable version of the HTML spec contract.
- Prefer behavior/state tests over implementation-detail tests.
- Keep tests DAMP: descriptive and meaningful, even if a little repetitive.
- Prefer real implementations, then fakes, then stubs, then mocks.
- For UI/browser work, combine unit/integration tests with runtime verification.

In this plugin, TDD is split into two gates: first `/build-tests` writes the tests from the spec, then a goal proves the tests are meaningfully red before implementation begins.

## Code Simplification

Source: https://github.com/addyosmani/agent-skills/blob/main/skills/code-simplification/SKILL.md

Local command name: `/simplify`

Local file: `../simplify/SKILL.md`

Workflow overlay:

- Simplify only after the implementation works and tests pass.
- Preserve externally observable behavior exactly.
- Follow local project conventions instead of importing outside style preferences.
- Prefer clarity over cleverness and line-count reduction.
- Scope simplification to recently changed code unless the user asks for broader cleanup.
- Run tests after simplification and revert any simplification that changes behavior.

In this plugin, `/simplify` happens after code review and before commit/push.
