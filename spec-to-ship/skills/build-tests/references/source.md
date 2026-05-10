# Source

Upstream skill: https://github.com/addyosmani/agent-skills/blob/main/skills/test-driven-development/SKILL.md

This local `SKILL.md` started as a downloaded copy of the upstream skill. It is now the editable `/build-tests` skill for Conmeara's workflow. Current local overlay:

- Tests are written from the approved HTML spec.
- Red verification is its own gate before production implementation.
- The implementation goal is complete only when the spec's tests pass.
- UI/runtime work still gets live app verification and human QA.
