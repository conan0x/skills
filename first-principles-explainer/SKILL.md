---
name: first-principles-explainer
description: Explain a dense concept from a source with a prerequisite map, why-before-how mechanics, examples, misconceptions, and a learning path.
---

# First-Principles Explainer

## Steps

1. Resolve the concept and source.
   - Source may be a paper, article, docs page, talk transcript, repository, prior note, or pasted text.
   - Completion: concept, source locator, and requested depth are known.
2. Read before explaining.
   - Read the source directly when available.
   - Read existing analysis notes if the concept comes from a research folder.
   - Completion: every source-derived claim in the explanation has a locator or boundary label.
3. Build the prerequisite map.
   - Include only prerequisites needed to understand this concept.
   - Completion: every unexplained term used in the main explanation is either common knowledge for the user context or appears in the map.
4. Write the why-before-how explanation.
   - Order: problem -> constraints -> mechanism -> consequences.
   - Completion: the mechanism follows from the stated constraints instead of appearing as a detached fact.
5. Add examples and misconceptions.
   - Completion: each example names what it demonstrates; each misconception has a correction.
6. Add a learning path.
   - Completion: each step has a practice task and success check.
7. Verify any created or materially changed file by reading it back.

## Output Schema

Use Markdown unless the user requests another format.

### Concept

- Name
- Source
- Depth: quick / standard / deep
- Boundary note: source claim / background / interpretation

### Prerequisite Map

| Prerequisite | Grounding | Needed for | Check |
| --- | --- | --- | --- |

### Why Before How

1. Problem: why the concept exists.
2. Constraints: pressures or invariants that shape it.
3. Mechanism: how it works.
4. Consequences: what follows, breaks, or becomes possible.

### Examples

| Example | What it demonstrates | Limit of the example |
| --- | --- | --- |

### Misconceptions

| Misconception | Correction | Source basis |
| --- | --- | --- |

### Learning Path

| Step | Goal | Practice | Success check |
| --- | --- | --- | --- |

## Boundary Labels

- `Source claim`: directly stated or clearly supported by the source.
- `Background`: established context from general technical knowledge or another source.
- `Interpretation`: reasoned inference beyond the source.

## Safety

- Do not replace source analysis with teaching; if the source itself has not been analyzed and the user asks for analysis, use `research-source-analyzer` first.
- Do not create lessons, HTML, quizzes, or a teaching workspace unless requested.
- Do not invent source results, author intent, or methodology.

## Verification

Before reporting completion:

- Confirm the output includes prerequisite map, why-before-how explanation, examples, misconceptions, and learning path.
- Confirm source-derived claims have locators or boundary labels.
- Confirm examples are tied to the concept, not decorative analogies.
- Confirm each learning-path step has a practice task and success check.
