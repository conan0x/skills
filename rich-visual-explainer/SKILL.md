---
name: rich-visual-explainer
description: Use this skill when creating polished visual HTML explainers, diagrams, dashboards, slide-like pages, or publishable visual references where the user has approved richer dependencies such as external fonts, Mermaid, Chart.js, generated images, or sharing.
---

# Rich Visual Explainer

Use this skill when the user wants a high-polish visual explanation, technical diagram, visual plan, project recap, comparison dashboard, or browser-first reference page and explicitly allows richer web features.

## Dependency gate

Before using any rich feature, confirm it is allowed by the task or ask the user:

- CDN fonts.
- Mermaid runtime.
- Chart.js or other charting libraries.
- External images or generated images.
- Publishing, deployment, or sharing links.
- Output outside the current workspace.

If approval is absent, use `offline-visual-explainer` patterns instead.

## Output policy

- Write into the current workspace unless the user names another output path.
- Use a descriptive filename tied to the topic.
- Keep the artifact understandable without reading the prompt history.
- If dependencies are used, document them in the page or final report.
- Prefer graceful degradation when a dependency fails.

## Design rules

- Pick a specific aesthetic before writing: blueprint, editorial, paper/ink, terminal, data-dense, IDE-inspired, or another named direction.
- Avoid generic neon dashboard styling, cyan/magenta/purple gradient meshes, glowing animated cards, and gradient text unless the user explicitly asks for that style.
- Use real typography, strong hierarchy, intentional whitespace, and consistent visual rhythm.
- Use CSS custom properties for palette, surfaces, borders, spacing, shadows, and themes.
- Support dark/light mode when useful.
- Include `@media print` for reference pages.
- Include `@media (prefers-reduced-motion: reduce)` when transitions or animations exist.
- Use real `<table>` elements for comparison matrices and data tables.
- Use namespaced classes such as `.ve-card`, `.ve-label`, `.workflow-step`, `.diagram-shell`, `.toc`, and `.table-scroll`.
- Never define a global `.node` class because Mermaid uses `.node` internally.

## Rendering choices

Choose the simplest rendering that communicates the structure:

- Text-heavy architecture: CSS grid cards and flow arrows.
- Simple workflow: CSS numbered cards or inline SVG.
- Flowchart, sequence, ER, state machine, mind map, class diagram, C4-like topology: Mermaid when approved.
- Data tables, audits, matrices: real HTML `<table>`.
- Timeline: CSS timeline.
- Metrics dashboard: CSS cards; Chart.js only when approved and useful.
- Slide-like walkthrough: full-screen sections with clear navigation and print/export consideration.

## Mermaid rules when approved

- Use Mermaid only when automatic layout materially improves readability.
- Use `theme: 'base'` and custom theme variables matching the page palette.
- Prefer top-down layouts for complex diagrams.
- Scope any Mermaid CSS overrides under the Mermaid container.
- Provide a readable fallback or explanatory text near the diagram.
- Avoid cramming 15+ nodes into one diagram; use a hybrid overview plus detail cards.

## Workflow

1. Read the source material first.
2. Identify the audience, purpose, content type, and aesthetic.
3. Decide offline vs rich mode; confirm rich dependencies if not already approved.
4. Draft the information architecture before styling.
5. Build the page with semantic headings, anchors, cards, diagrams, tables, and details.
6. Open or inspect the result in a browser when practical.
7. Verify content, dependencies, layout, and interactions before reporting completion.

## Verification checklist

Before claiming done, check:

- Required content is present.
- The file exists at the requested path.
- Dependency use matches what the user approved.
- Browser smoke check passes when practical: title, main heading, required sections, diagrams/tables, and controls exist.
- Mermaid or charts render if used.
- Local interactions work if included.
- Mobile layout has no document-level horizontal overflow.
- Print styles exist when the page is a durable reference.

## Reporting

Report:

- Output file path.
- Aesthetic and rendering choices.
- External dependencies used, if any.
- Browser or content verification performed.
- Any limitation or fallback.
