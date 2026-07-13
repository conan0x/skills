---
name: research-source-analyzer
description: Analyze a single paper, article, talk, docs page, benchmark, repository, or note into source metadata, claim evidence, AI-work lessons, and OMP experiments.
---

# Research Source Analyzer

## Steps

1. Resolve the source and mode.
   - Modes: `triage`, `standard`, `deep dive`.
   - Default: `standard`.
   - Completion: source locator and mode are known.
2. Read workspace context before writing.
   - Read `AGENTS.md` if present.
   - Read `README.md` if present and relevant.
   - Read existing target-folder notes before updating them.
   - Completion: target folder state is known.
3. Read the source directly.
   - Triage may use an abstract, headline, or secondary summary only when the user asks for quick relevance.
   - Standard/deep-dive runs must identify thesis, major claims, support, assumptions, and limitations before writing.
   - Completion: every major claim used in the note has a source locator or is explicitly labeled as background/interpretation.
4. Choose the output shape.
   - Substantial source: create or update `<source-slug>/source.md`, `analysis.md`, `ai-lessons.md`, and `experiments.md`.
   - Small source: use fewer files; do not create empty scaffolding.
   - Slug: lowercase dash-case source title, max 8 meaningful words.
   - Completion: every created file has source-derived content.
5. Write the notes using the schemas below.
6. Verify by reading back every created or materially changed file.

## Source File Schema

`source.md` contains:

- Title
- Author or organization
- URL or local path
- Publication date, or `Unknown`
- Date analyzed
- Source type: paper, article, docs, talk, benchmark, repo, essay, or other
- Analysis mode
- Short source description

## Analysis Schema

`analysis.md` contains the sections required by the mode.

### Triage

- Thesis
- Relevance
- Recommendation: keep / skip / defer
- Likely AI-work relevance

### Standard

- Core thesis
- Context and problem
- Prerequisite map
- Claim table
- Caveats and uncertainty
- Useful or reusable ideas
- Weak, speculative, or context-dependent points
- Open questions

### Deep Dive

Include everything from `standard`, plus:

- Methodology or argument structure
- Counterarguments
- Replication or implementation ideas
- Stronger grounding with quotes, sections, pages, timestamps, or URLs

## Prerequisite Map

For prerequisite-heavy sources, add a table:

| Prerequisite | One-sentence grounding | Why it matters here |
| --- | --- | --- |

## Claim Table

For dense or technical sources, map each major claim:

| Claim | Source support | Assumption | Limitation | Confidence | Boundary |
| --- | --- | --- | --- | --- | --- |

Confidence values:

- `High`: directly supported by the source, well-established, or independently verified.
- `Medium`: plausible with limited evidence or partial corroboration.
- `Low`: speculative, contested, emerging, or incomplete.

Boundary labels:

- `Source claim`: directly stated or clearly supported by the source.
- `Background`: established context from general technical knowledge or another source.
- `Interpretation`: reasoned inference beyond the source.
- `AI-work extrapolation`: practical lesson for using AI systems.

## AI Lessons Schema

`ai-lessons.md` uses lesson cards. Each card contains:

- Category: OMP harness / prompting and chat / research-to-implementation
- Behavior change: do / don't
- Why
- Source basis: source claim / background / interpretation / AI-work extrapolation
- Applicability limit

If the source supports no AI-work lesson, write `No supported AI-work lesson found` and explain why.

## Experiments Schema

`experiments.md` uses experiment cards. Each card contains:

- Hypothesis
- Steps
- Success criteria
- Failure criteria
- Risk or confounder
- Session fit: one-session / long-running

If no experiment is supported, write `No supported experiment found` and explain why.

## Grounding Rules

- Use `Unknown` for missing metadata; do not guess.
- Cite or quote major, surprising, technical, or high-impact claims.
- Mark interpretation and AI-work extrapolation; do not present them as source claims.
- Keep critique separate from summary.
- Do not invent results, author intent, methodology, or source details.

## Safety

- Do not delete source material.
- Do not overwrite existing notes without reading them first.
- Do not install packages, clone repositories, access paid systems, submit forms, or mutate remote services unless explicitly requested.
- Do not create corpus indexes, teaching lessons, or comparison reports unless requested; this skill is single-source focused.

## Verification

Before reporting completion:

- Read back every created or materially changed file.
- Confirm `source.md` contains title, locator, date analyzed, source type, and mode.
- Confirm `analysis.md` matches the selected mode.
- Confirm every major claim is grounded or boundary-labeled.
- Confirm `ai-lessons.md` contains lesson cards or `No supported AI-work lesson found`.
- Confirm `experiments.md` contains experiment cards with success/failure criteria or `No supported experiment found`.
