---
name: research-to-omp-experiment
description: Turn an already analyzed source into actionable OMP experiments with hypotheses, workflows, prompts, verification criteria, and failure modes.
---

# Research To OMP Experiment

## Steps

1. Locate the analyzed source.
   - Read `source.md`, `analysis.md`, `ai-lessons.md`, and `experiments.md` when present.
   - If no analysis exists, stop and use `research-source-analyzer` first unless the user explicitly wants a rough experiment sketch.
   - Completion: source thesis, relevant AI lesson, and source basis are known.
2. Select experiment candidates.
   - Use only claims or lessons with a source basis or explicit interpretation label.
   - Completion: each candidate names the claim or lesson it tests.
3. Convert candidates into experiment cards.
   - Completion: every card has hypothesis, workflow, prompt or agent instruction, verification criteria, and failure modes.
4. Fit the experiment to OMP.
   - Use OMP capabilities only when they are part of the hypothesis: files, tools, browser, search, verification commands, subagents, structured artifacts, or repeatable scripts.
   - Completion: required OMP capabilities are listed and justified.
5. Define the evaluation.
   - Completion: success, failure, baseline, and confounders are explicit enough that another run can reproduce the judgment.
6. Verify any created or materially changed file by reading it back.

## Output Schema

Use Markdown unless the user requests another format.

### Experiment Card

- Name
- Source basis: source claim / AI lesson / interpretation
- Hypothesis
- Baseline or comparison
- OMP capabilities used
- Workflow
- Prompt or agent instruction
- Artifacts to create
- Verification criteria
- Failure modes
- Confounders
- Session fit: one-session / long-running
- Next action

## Workflow Requirements

Each workflow must include ordered steps and an observable output.

Each prompt or agent instruction must include:

- role or task
- source material to use
- output format
- verification request

Each verification criterion must state:

- what is measured or inspected
- pass condition
- fail condition

## Failure Mode Checklist

Check every experiment for:

- source lesson too vague to test
- no baseline or comparison
- success criteria rewarding fluent prose instead of behavior
- missing source grounding
- OMP tool use added without testing anything
- result dependent on one model sample only
- hidden manual judgment with no rubric

## Safety

- Do not mutate remote services, install packages, run long jobs, or spend paid API credits unless explicitly requested.
- Do not present an experiment result unless it was actually run.
- Do not upgrade a rough sketch into a validated workflow without evidence.

## Verification

Before reporting completion:

- Confirm every experiment card has hypothesis, workflow, prompt or agent instruction, verification criteria, and failure modes.
- Confirm each card traces to an analyzed source claim, AI lesson, or marked interpretation.
- Confirm success and failure criteria are behavior-based, not prose-quality praise.
- Confirm required OMP capabilities are listed.
