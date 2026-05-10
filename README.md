# Conmeara Plugins

Personal Codex plugins and workflow skills.

## Plugins

### Spec to Ship

`spec-to-ship` captures a spec-first development workflow:

1. `/html-spec` to make the future implementation visible as an HTML artifact.
2. Review the spec in depth with Codex annotations and direct edits.
3. `/build-tests` to create the red test contract from the approved spec.
4. QA the spec and tests manually.
5. Use Codex goals to verify red, then implement to green.
6. Test the app manually.
7. Run Codex code review.
8. `/simplify` to clean up without changing behavior.
9. Commit and push.

Open the visual workflow map:

```text
spec-to-ship/workflow.html
```

The plugin lives at:

```text
spec-to-ship/
  .codex-plugin/plugin.json
  skills/
    html-spec/
    build-tests/
    simplify/
    spec-to-ship/
```

## Install Locally

Clone this repo to `~/plugins`:

```bash
git clone https://github.com/conmeara/plugins.git ~/plugins
```

Then add this entry to `~/.agents/plugins/marketplace.json`:

```json
{
  "name": "spec-to-ship",
  "source": {
    "source": "local",
    "path": "./plugins/spec-to-ship"
  },
  "policy": {
    "installation": "AVAILABLE",
    "authentication": "ON_INSTALL"
  },
  "category": "Productivity"
}
```

If the marketplace file does not exist yet, use `marketplace.example.json` as a starting point.
