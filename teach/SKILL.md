---
name: teach
description: Use this skill when the user wants to learn a new concept or skill over multiple sessions in a local teaching workspace.
---

# Teach

Use this skill when the user asks to be taught a topic, skill, concept, craft, workflow, or body of knowledge and the learning should persist across sessions in the current workspace.

This is an OMP-compatible adaptation of Matt Pocock's `teach` skill. The upstream project is MIT licensed; see `LICENSE` in this folder.

## Teaching workspace

Treat the current directory as the teaching workspace. The user's learning state is captured in files and folders in that directory:

- `MISSION.md`: the reason the user is learning this topic. Every teaching decision traces back to it. Use `MISSION-FORMAT.md`.
- `RESOURCES.md`: curated high-trust knowledge sources and communities. Use `RESOURCES-FORMAT.md`.
- `GLOSSARY.md`: canonical terms the user has demonstrated they understand. Use `GLOSSARY-FORMAT.md`.
- `learning-records/*.md`: durable records of non-obvious learning, prior knowledge, corrected misconceptions, and mission shifts. Use `LEARNING-RECORD-FORMAT.md`.
- `lessons/*.html`: self-contained lesson files, named `0001-<dash-case-name>.html`, `0002-<dash-case-name>.html`, etc.
- `reference/*.html`: printable quick-reference documents, cheat sheets, algorithms, glossaries, sequences, field guides, and other reusable learning artifacts.
- `assets/*`: reusable lesson components such as CSS, quiz widgets, simulators, diagram helpers, and shared scripts.
- `NOTES.md`: scratchpad for user teaching preferences and working notes.

Create these files and folders lazily. Do not create empty scaffolding unless it is needed for the current lesson or state update.

## Source-of-truth policy

Before teaching:

1. Read `MISSION.md` if it exists.
2. Read relevant `learning-records/` entries if they exist.
3. Read `GLOSSARY.md` if it exists and use its terminology.
4. Read `RESOURCES.md` if it exists and prefer its sources.
5. Inspect `assets/` before authoring lesson HTML so reusable components are not duplicated.

Do not rely on parametric memory for factual claims when source lookup is available. Use high-trust resources, cite claims in lessons, and record useful sources in `RESOURCES.md`.

When a teaching explanation mixes source-backed claims, general background, and interpretation, label or phrase the boundary clearly enough that the learner can tell which is which.

## Mission first

The mission is the compass: the concrete reason the user wants the skill.

If `MISSION.md` is missing or vague, interview the user before writing lessons. Push for an observable real-world outcome, not an abstract goal like "understand X". One workspace should track one mission; unrelated learning goals belong in separate workspaces.

Missions can change. Confirm with the user before changing `MISSION.md`, then create a learning record explaining the shift.

## Learning model

Teach for three layers:

- **Knowledge**: high-quality, high-trust source material.
- **Skills**: guided practice and tight feedback loops.
- **Wisdom**: real-world interaction with practitioners, communities, classes, forums, or field work.

Distinguish:

- **Fluency strength**: the user can retrieve something now.
- **Storage strength**: the user retains and can reuse it later.

Design lessons to build storage strength through desirable difficulty:

- retrieval practice;
- spacing;
- interleaving related skills when useful;
- immediate feedback where possible.

Adjust the balance to the topic. Theoretical topics may require more knowledge acquisition; physical or procedural topics may require more guided practice. Minimize extraneous difficulty while introducing knowledge, then use desirable difficulty during retrieval and skill practice.

### Concept-first instruction

For a concept the learner has not already been taught in this workspace, teach the minimum viable model before asking them to predict, map, diagnose, or choose.

Use prediction-before-explanation only for calibration, review of previously taught material, or when the user explicitly asks to be tested first.

The minimum viable model is: prerequisite map -> why-before-how explanation -> worked example -> misconceptions -> guided practice.

Why-before-how order is: problem -> constraints -> mechanism -> consequences.

Practice still follows the model: ask the learner to apply, map, diagnose, or near-transfer after they have enough structure to reason.


### Visual aids

Use visuals when they reduce cognitive load or make structure, sequence, comparison, mechanism, or spatial relationships easier to understand.

Prefer lightweight visuals first: concise tables, ASCII diagrams, Mermaid diagrams, or simple in-chat sketches. Use heavier artifacts such as HTML, browser surfaces, or Sideshow only when the concept benefits from a reviewable or interactive artifact.

Do not use visuals for visual sake. Skip diagrams that merely restate prose without adding clarity.

Do not confuse coverage with learning. Only add a learning record or glossary term when the user demonstrates understanding, discloses relevant prior knowledge, corrects a misconception, or changes the mission.

## Zone of proximal development

Each lesson should feel challenging but reachable.

If the user names the exact thing they want to learn, teach that thing while tying it to the mission. If they do not, infer the next lesson from:

1. the mission;
2. existing learning records;
3. glossary terms already mastered;
4. gaps in resources;
5. the smallest skill that unlocks a tangible win.

Avoid overloading working memory. Each lesson teaches one tightly scoped thing.

## Lessons

A lesson is the primary teaching artifact. It is a self-contained HTML file in `lessons/` named with the next sequential number: `0001-<dash-case-name>.html`, `0002-<dash-case-name>.html`, and so on.

A lesson must:

- teach one tightly scoped skill or concept;
- tie directly to `MISSION.md`;
- stay short enough to complete quickly;
- use clean, readable, printable layout;
- cite high-trust sources for factual claims;
- recommend one primary source to read or watch next;
- include concept-first instruction for new concepts, then practice, retrieval, or feedback when the topic allows it;
- include a short prerequisite map when unexplained terms would otherwise block the lesson;
- explain dense concepts in problem -> constraints -> mechanism -> consequences order;
- include at least one worked example and name what it demonstrates;
- name likely misconceptions and corrections when the topic commonly produces wrong mental models;
- link by relative paths or anchors to related lessons and reference documents;
- remind the user to ask follow-up questions when anything is unclear.

For quizzes, avoid accidental answer clues. Keep options the same number of words when practical and similar character length when possible.

When practical, verify the lesson in a browser or by checking the HTML structure before reporting completion.

After verification, open the lesson for the user when the environment permits.

## Assets

Reuse assets by default.

Before authoring a lesson, inspect `assets/`. If a second lesson could reuse a stylesheet, quiz widget, simulator, diagram helper, or script, place it in `assets/` and link it from lessons instead of inlining duplicated code.

A shared stylesheet is the first reusable asset most teaching workspaces should gain. Lessons should look like one coherent course, not unrelated one-offs.

Keep assets local unless the user explicitly approves external dependencies. Lessons should work from disk where practical.

## Reference documents

Create reference documents while lessons reveal reusable units of knowledge.

Reference documents live in `reference/*.html`. They should be compressed, beautiful, printable quick references the user can revisit later:

- syntax and snippets;
- algorithms and flowcharts;
- poses, routines, drills, or sequences;
- comparison matrices;
- checklists;
- glossaries or term maps;
- field guides.

Lessons teach. References help the user retrieve and apply.

## Resources and wisdom

`RESOURCES.md` should stay curated, not comprehensive. Prefer primary sources, recognised experts, peer-reviewed work, official docs, and strongly moderated communities.

When the user asks something that requires wisdom, answer as far as sources support, then recommend a real community or practitioner path when useful. Respect an explicit preference not to join communities and record it in `RESOURCES.md` or `NOTES.md`.

## Notes

Use `NOTES.md` for teaching preferences, accessibility needs, pace, tone, constraints, or durable working notes that do not belong in the mission, glossary, resources, or learning records.

## Workflow

1. Establish or read the mission.
2. Read existing learning state: records, glossary, resources, notes, assets.
3. Identify the next smallest useful lesson or reference artifact; decide whether it is new instruction, review, or calibration.
4. Gather or verify source material from high-trust resources.
5. Update `RESOURCES.md` when a source becomes part of the teaching basis.
6. Build the lesson and any reusable assets or reference docs it needs; for new conceptual instruction, teach prerequisite map, why-before-how explanation, worked example, and misconceptions before guided practice.
7. Verify the created artifact exists and behaves locally.
8. Update `GLOSSARY.md` or `learning-records/` only when the criteria are met.
9. Report the created paths, sources used, verification performed, and the suggested next learning step.

## Verification checklist

Before claiming a teaching step is complete:

- `MISSION.md` exists or the user explicitly chose a one-off lesson before mission setup.
- New lesson files are in `lessons/` and use the next sequential number.
- New learning records are in `learning-records/` and use the next sequential number.
- `RESOURCES.md` includes every source that became part of the lesson basis.
- Lesson links are relative and resolve locally where practical.
- Reusable CSS or scripts are in `assets/`, not duplicated across lesson files.
- New conceptual lessons teach the minimum viable model before asking for prediction or mapping, unless the lesson is explicitly calibration, review, or user-requested test-first practice.
- Dense-concept lessons include prerequisite map, why-before-how order, worked example, misconceptions when relevant, and a practice or success check.
- The lesson was smoke-checked in a browser or structurally checked for title, main heading, practice section, source links, and print/local usability.

## Reporting

Report briefly:

- created or changed files;
- the mission tie-in;
- primary sources used;
- verification performed;
- what the user should do next.