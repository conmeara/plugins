---
name: html-spec
description: "Create repository-grounded HTML specs instead of large Markdown docs. Use when the user invokes /html-spec or asks for an html spec, aspec, visual spec, interactive spec, living spec, implementation spec, feature spec, architecture spec, prompt spec, database redesign spec, engine redesign spec, UX flow spec, product behavior artifact, or implementation handoff that helps a human understand and refine what should be built before it is implemented."
---

# HTML Spec

## Purpose

Create a self-contained HTML artifact that makes an implementation idea easier to understand, discuss, and later build. This is Conmeara's `/html-spec` phase: make the future implementation visible before tests or production code begin.

Use this beyond UI work. An HTML spec can describe prompt engineering, database redesigns, rendering engines, agent workflows, architecture changes, data lifecycles, eval systems, migration plans, or product surfaces. The point is not "make a webpage"; the point is to make the future implementation visible.

Do not force a fixed table of contents. Documentation does not have one true shape; choose the sections, visuals, and interactions that clarify this change.

## Workflow

1. Ground the spec in the repo.
   - Inspect the relevant code, docs, existing specs, schemas, prompts, evals, tests, routes, components, styles, architecture boundaries, and product language.
   - Match the app's palette, density, radius, typography, and interaction vocabulary when the target repo has a visible product style. For backend or under-the-hood specs, still borrow the app's visual language so the artifact feels native to the project.
   - Prefer real product concepts, runtime names, data names, source paths, and system boundaries over generic architecture language.

2. Name the implementation idea.
   - State the change, audience, affected surface or subsystem, and the moment in the user's or system's workflow.
   - Explain the mental model in one compact opening paragraph.
   - Surface assumptions and open questions directly in the artifact when they affect product behavior, architecture, data, prompts, tests, or rollout.

3. Build the HTML spec.
   - Save a single `.html` file in the repo's spec/docs area, or the user-requested path. If no convention exists, use `docs/specs/<SpecName>.html`.
   - Use inline CSS and minimal inline JS so the file opens directly in a browser with no build step.
   - Include direct navigation when the page is long, but keep the top simple: title, short lede, and a small metadata row are usually enough.

4. Choose the right visual grammar.
   - For UI behavior: use interface anatomy, state explorers, timelines, user journeys, component mockups, edge cases, and acceptance tests.
   - For prompt systems: use prompt layers, context assembly maps, model handoff diagrams, tool-call boundaries, failure modes, eval cases, and before/after examples.
   - For databases: use entity maps, ownership boundaries, lifecycle diagrams, migration phases, query paths, invariants, constraints, and rollback plans.
   - For engines or runtimes: use pipelines, timing models, dependency graphs, queues, caches, state machines, concurrency diagrams, and performance budgets.
   - For agent workflows: use lane maps, job state diagrams, approval gates, retry paths, event streams, observability points, and recovery scenarios.
   - Use interactive elements when they reduce explanation: tabs for states, toggles for alternatives, hover notes for tests, small simulators for flows, or expandable implementation notes.

5. Make the implementation path understandable.
   - Connect behavioral and technical claims to likely implementation areas, source files, tests, migrations, prompts, or evals when known.
   - Map claims to a test plan or verification plan in human-readable language.
   - Keep implementation detail in service of shared understanding; this is not a code dump.

6. Verify before delivering.
   - Check that the HTML opens, inline scripts parse, and important interactions work.
   - Check desktop and mobile widths for horizontal overflow and text collisions.
   - Fix generic-looking styling, overbuilt hero sections, illegible colors, broken links, fake source references, and layout shifts before calling it done.

## Artifact Principles

- Make it doc-first, not marketing-first. The first screen should explain the change, not sell it.
- Keep the design mostly minimal. Use quiet borders, small metadata, restrained cards, clear diagrams, and app-native controls.
- Let the project set the visual language. Do not paste in a generic palette, generic gradient, or unrelated design trend.
- Use HTML's strengths: CSS layout, diagrams, tables, anchors, tabs, hover notes, compact comparisons, and light interactivity.
- Keep the artifact agent-readable. Use semantic headings, stable section IDs, explicit state names, concrete behavior labels, and real system terms.
- Write in plain implementation language. The user should be able to point at a state, prompt layer, table, pipeline, rule, or edge case and say "yes, that's what I mean."
- Avoid mandatory PRD scaffolding. Add objectives, journeys, states, constraints, open questions, tests, diagrams, and handoff notes only when they help.
- Avoid rigid gated spec-driven-development rituals. The artifact can become an implementation handoff, but its first job is shared understanding.
- Do not fake certainty. Mark unknowns, unresolved decisions, and areas needing user judgment.

## Optional Building Blocks

Choose from this menu instead of using it as a required template:

- Frame: audience, subsystem, status, scope, non-goals
- Mental model: the simplest explanation of how the change should work
- Current vs future: what exists now, what should change, why it matters
- Core journey or flow: user flow, data flow, render flow, prompt flow, or agent flow
- Anatomy: UI surface, schema, prompt stack, runtime pipeline, job queue, or module boundary
- Concepts: short definitions for domain terms the user and agent must share
- States and transitions: tabs, table, lifecycle, state machine, or scenario cards
- Rules and invariants: concise claims the implementation must preserve
- Edge cases: failure, empty, loading, permissions, stale state, conflict, recovery, performance, privacy
- Alternatives: side-by-side options with tradeoffs
- Dependencies: related specs, modules, source files, APIs, models, prompts, migrations, data shapes
- Test contract: acceptance criteria, existing tests, desired tests, evals, fixtures, visual QA checks
- Rollout plan: migration steps, compatibility, fallback, monitoring, cleanup
- Implementation handoff: ordered build slices, risk notes, and verification commands

## Style Recipe

- Extract colors and fonts from the app first: CSS variables, Tailwind config, design-token files, theme files, package styles, and existing components.
- Use system fonts unless the app already uses a specific face.
- Prefer a narrow content column plus optional sticky table of contents for longer artifacts.
- Use cards only for repeated items, mock components, callouts, and state examples. Avoid cards inside cards.
- Use diagrams, tables, and compact labels for complex under-the-hood systems; do not turn architecture into walls of prose.
- Use icons or app-native symbols for controls when they communicate faster than text.
- Keep body text readable, labels compact, and line lengths comfortable.
- Use responsive CSS explicitly; do not rely on desktop-only layouts.

## Reference

Read `references/html-artifact-principles.md` when the task is broad, when the user asks for the thinking behind the format, or when you need concrete patterns from `Comments.html` and the HTML-artifact inspiration.
