---
name: offline-visual-explainer
description: Use this skill when creating self-contained local HTML explainers, field guides, comparison matrices, workflow diagrams, visual plans, recaps, or browser-first reference pages that must work offline.
---

# Offline Visual Explainer

Use this skill when the user asks for a visual explanation, self-contained HTML page, field guide, visual plan, recap, comparison table, workflow diagram, or durable browser-first technical reference and offline/local reliability matters.

## Default mode

Default to a local, self-contained artifact:

- Write into the current workspace unless the user names another output path.
- Use one HTML file unless the user asks for multiple files.
- Use inline CSS and minimal inline JavaScript.
- Use local font stacks only.
- Do not use external scripts, CDN fonts, remote images, Mermaid runtime, Chart.js, or publishing/deployment.
- Make the page open fully from disk without network access.

## Design rules

- Pick a specific aesthetic before writing: paper/ink, editorial, blueprint, terminal, data-dense, or IDE-inspired.
- Avoid generic neon dashboard styling, cyan/magenta/purple gradients, glowing animated cards, and gradient text.
- Use CSS custom properties for palette, surfaces, borders, spacing, shadows, and themes.
- Support dark mode with `@media (prefers-color-scheme: dark)` when useful.
- Include `@media print` for printable pages.
- Include `@media (prefers-reduced-motion: reduce)` when transitions or animations exist.
- Use real `<table>` elements for comparison matrices and data tables.
- Use cards, grids, callouts, details/summary, sticky navigation, and visual hierarchy.
- Use namespaced classes such as `.ve-card`, `.ve-label`, `.workflow-step`, `.toc`, and `.table-scroll`.
- Never define a global `.node` class.

## Structure patterns

For pages with 4+ sections, prefer:

- Hero summary with title, short description, and primary reference link when relevant.
- Sticky table of contents on desktop.
- Horizontal sticky navigation on mobile.
- Optional local-only filter/search when it materially improves lookup.
- Main content sections with stable anchor IDs.
- Real tables with sticky headers and horizontal overflow wrappers.
- Collapsible `<details>` for secondary examples.

For workflow diagrams, prefer CSS numbered cards or inline SVG. Do not use Mermaid unless the user explicitly switches to a rich/external mode.

## Workflow

1. Read the source material first.
2. Identify the audience, purpose, content type, and aesthetic.
3. Draft the information architecture before styling.
4. Build the HTML with semantic headings, anchors, cards, tables, and diagrams.
5. Keep scripts small and local-only.
6. Verify the result before reporting completion.

## Verification checklist

Before claiming done, check:

- Required content is present.
- The file exists at the requested path.
- No unwanted external dependencies are present: `http://`, `https://`, `<script src=`, `<link href=`, `cdn`, `fonts.googleapis`, `mermaid`, `chart.js`.
- If an external link is intentionally included, it is the one the user requested.
- Browser smoke check passes when practical: title, main heading, required sections, and key controls exist.
- Local filter/search works if included.
- Mobile layout has no document-level horizontal overflow.
- Print styles exist for durable references.

## Reporting

Report:

- Output file path.
- Design mode and aesthetic chosen.
- Verification performed.
- Any intentionally included external link or dependency.
