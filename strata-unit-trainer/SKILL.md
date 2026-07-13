---
name: strata-unit-trainer
description: Use this skill when evaluating Strata Unit responses, drafting Unit-facing training feedback, meta-evaluating feedback prompts, or planning Strata Unit training while preserving source/stimulus/profile separation.
---

# Strata Unit Trainer

## Operating mode

Use this skill for Strata Unit response evaluation, training-feedback drafting, meta-evaluation, and training-plan reasoning. The skill is a procedural guardrail; it never replaces the active Unit profile, workflow prompt, evaluation/meta templates, operator-provided stimulus, or `shared/strata_complete_training_guide.md`.

Treat all Unit outputs as training, diagnostic, evaluation, research, or session-review support for the operator. Do not turn Unit reasoning into financial advice, trade execution instructions, price targets, position sizing recommendations, or new live-market conclusions beyond the supplied task.

## Source-of-truth order

1. Follow the operator's current message first when it names a Unit, workflow, source file, stimulus, output format, or newer procedure.
2. Follow active project/workspace instructions already in context.
3. Read the folder-level Strata operating guide when present, usually `project/strata_units/README.md` or `../README.md` from a Unit folder.
4. Read `shared/strata_complete_training_guide.md` or `../shared/strata_complete_training_guide.md` as the shared training model.
5. Read the Unit profile, such as `<unit>/<unit>_profile.txt`, as the governing identity and risk/scope contract.
6. For evaluations, read the Unit's active workflow prompt first when one exists, then read the response, first-pass evaluation template, meta-evaluation template, and exact source/stimulus file named by the operator or workflow.
7. Read only the files needed for the active task. Do not bulk-load all Strata Unit folders.

If any active Unit-specific workflow conflicts with this skill, use the Unit-specific workflow and keep this skill only as a checklist for safety, source separation, and training hygiene.

## Separation rules

Keep these buckets separate in scratch context and final output:

- Operator-provided stimulus, scenario, market data, or source prompt.
- Source/background facts from files, profiles, training plans, or shared guide.
- Unit output, used as diagnostic evidence only.
- LLM diagnosis/evaluation.
- Unit-facing training feedback, if any.

Never copy, quote, paraphrase, mirror, or structurally reuse a Unit's LLM-articulated response in Unit-facing feedback. Train from the scenario facts, profile rules, market data, and outcomes instead.

## Evaluation workflow

1. Identify the exact Unit and active workflow. If a dedicated evaluation workflow prompt exists, follow it before applying generic Strata judgment.
2. Resolve the immediate stimulus from the operator's instruction or workflow locator. Do not infer the stimulus from the Unit response wording.
3. Confirm the response file or pasted response is current for that stimulus. If it is empty, stale, unrelated, or missing, ask for the current response before evaluating.
4. Evaluate reasoning and substantive claims, not prose style. Verify only claims the response actually makes plus governing constraints required by any proposed action.
5. Check profile-specific constraints before generic intuition: allowed instruments, market scope, signal hierarchy, regime gate, setup type, risk/sizing/leverage/exposure, stops, cooldowns, profit protection, correlation, and thesis lifecycle.
6. Decide the training signal:
   - Use `NO PROMPT` when the response is sound and no durable reasoning pathway needs reinforcement.
   - Use an affirming prompt only when a correct reusable pathway should recur in future market scenarios.
   - Use a corrective prompt for a material reasoning failure, profile violation, risk-posture error, or future-behavior drift.
   - Use a two-step correction when the failed reasoning pathway should be activated before correction.
   - Use mixed affirm/correct only when both sides are material and the prompt can stay narrow.
7. Run independent meta-evaluation when the active workflow or template requires it. Re-derive the diagnosis; do not merely defend the first pass.
8. Return only the output required by the active workflow.

## Training-feedback rules

Any Unit-facing training prompt must begin with exactly:

```text
TRAINING MODE
```

Draft prompts in fresh language grounded in scenario facts and governing profile rules. Prefer scenario-based teaching and principle-level correction over lectures. Before generating any prompt, ask whether the issue would materially change the trading-logic conclusion, risk posture, or future reasoning behavior; if not, choose no-prompt.

Use explicit validation only when the response is correct and the reasoning pathway is worth strengthening. Validate the market/scenario facts, governing rule, and conclusion; do not validate by referring to the Unit's own wording.

Use two-step correction for reasoning-process errors where durable adjustment matters. Use single-step correction for simple factual errors, formatting errors, or low-stakes clarifications.

## Anchor and overtraining discipline

Use permanent-anchor language such as `REMEMBER THIS` or `NEVER FORGET` only when the operator explicitly asks for an anchor or the active workflow says an anchor is intended. Do not anchor temporary regime preferences, calibration thresholds likely to drift, one-off corrections, or concepts that can be reinforced normally.

Avoid overtraining. After foundation work, train only 3-5 regime-relevant concepts per cycle, then let the Unit operate. Prefer no-prompt for marginal residual issues, local edge cases, adjacent refinements after recent corrections, or correct responses without a reusable pathway worth strengthening.

## Generality rule

Keep this skill Unit-agnostic. Do not hard-code any current or future Unit's market scope into the skill itself. Always derive the active Unit's identity, scope, signal hierarchy, risk limits, and workflow output contract from that Unit's profile and local workflow files.

## Verification checklist

Before claiming a Strata evaluation, training prompt, or meta-evaluation is complete:

- The exact Unit, immediate stimulus, source/background file, and response are identified.
- Required Unit-specific workflow files and profile files were read.
- Shared training-guide rules were applied without duplicating stale guide text.
- Response wording was not fed back into Unit-facing feedback.
- Any Unit-facing prompt starts with `TRAINING MODE`.
- Any anchor language is explicitly intended and justified by the active workflow or operator request.
- No-prompt was chosen when durable reinforcement or correction was not needed.
- The final output format matches the active Unit workflow exactly.
