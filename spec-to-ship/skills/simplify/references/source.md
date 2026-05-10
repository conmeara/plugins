# Source

Upstream skill: https://github.com/addyosmani/agent-skills/blob/main/skills/code-simplification/SKILL.md

This local `SKILL.md` started as a downloaded copy of the upstream skill. It is now the editable `/simplify` skill for Conmeara's workflow. Current local overlay:

- Simplification happens after tests and review, before commit/push.
- Behavior must remain exactly the same.
- Scope defaults to the implementation just changed.
- The tests from the HTML spec remain the contract while simplifying.
