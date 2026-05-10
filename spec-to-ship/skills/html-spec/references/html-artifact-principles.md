# HTML Spec Principles

## Why HTML For Specs

The inspiration is Thariq Shihipar's "Using Claude Code: The Unreasonable Effectiveness of HTML" thread and companion examples. The useful idea is not "make everything fancy"; it is that HTML can turn a long linear plan into a navigable artifact people actually read.

Use HTML specs when the work benefits from:

- Information density: tables, diagrams, component mockups, visual state maps, and compact comparisons.
- Visual clarity: layout, hierarchy, color, anchors, and responsive structure.
- Interaction: tabs, toggles, sliders, state explorers, copy/export buttons, and hover annotations.
- Shareability: a single browser-openable file.
- Agent handoff: a concrete artifact a future agent can read alongside the code.

The post also warns against overcomplicating this into ritual. Start from what the artifact needs to do, then choose the HTML affordances that help.

## Lens

Use this format for any implementation work that needs shared understanding before code:

- UI and product behavior specs.
- Prompt engineering and context assembly specs.
- Database, schema, migration, and lifecycle specs.
- Video engine, rendering pipeline, preview/runtime, cache, and timing specs.
- Agent workflow, queue, approval, retry, and recovery specs.
- Architecture redesigns that need diagrams, tradeoffs, invariants, and rollout plans.

The common move is to make the invisible system visible enough to discuss.

## Pattern From `Comments.html`

The Ripple `Comments.html` artifact works because it is a product behavior spec, not a generic PRD:

- It opens with a simple feature name, one-paragraph mental model, audience/surface/status metadata, and a test-marker legend.
- It uses a sticky numbered sidebar only because the page is long.
- It explains the feature through workflow, concepts, UI mockups, states, timeline markers, replies, accept behavior, auto-merge scenarios, edge cases, related specs, constraints, and tests.
- It renders concrete UI states such as working, changes ready, refresh needed, updating, and accepted.
- It uses small interactive state tabs and hoverable test markers to keep dense behavior scannable.
- It keeps implementation safety visible through plain-language rules and a mapped test plan.
- It uses app-like styling: CSS variables, quiet dark surfaces, subdued borders, small radii, system fonts, monospaced metadata, and restrained status colors.
- It was validated for inline script parsing and no horizontal overflow at desktop and mobile widths.

Do not copy its section list by default. Copy the move: make the target system visible, stateful, and reviewable.

## Good Signs

- The user can understand the feature by scanning the page before reading every paragraph.
- The artifact makes tradeoffs, states, and edge cases easier to discuss.
- The design feels like it belongs inside the target app's repo.
- The spec names what is known, what is assumed, and what still needs judgment.
- A future implementation agent can use the artifact as a behavioral contract.

## Anti-Patterns

- Converting Markdown to HTML without using layout, visual hierarchy, or interaction.
- Creating a landing page, pitch page, or decorative hero instead of a spec.
- Mandating a PRD table of contents regardless of the feature.
- Treating HTML specs as UI-only artifacts.
- Inventing a design system when the repo already has one.
- Burying the user's decision points under implementation detail.
- Using loud gradients, decorative blobs, oversized cards, or generic SaaS styling.
- Faking source paths, tests, screenshots, or product constraints.
