---
name: skill-builder
description: Build, adapt, review, install, or update reusable OMP skills directly in the global skill source and runtime.
---

# Skill Builder

## Steps

1. Classify the branch.
   - Branches: `create`, `adapt`, `review`, `install`, `update`.
   - Completion: branch, target skill name, source material, and intended output are known.
2. Read the active source of truth.
   - Read `C:/Users/allen/.omp/agent/AGENTS.md`.
   - Read `C:/Users/allen/.omp/agent/skills/README.md`.
   - If the target skill exists, read its current `SKILL.md` and supporting files before proposing changes.
   - Completion: current behavior, provenance, local preferences, and missing references are known.
3. Read source material.
   - For a new skill, read `C:/Users/allen/OneDrive/Documents/CodexRepo/dev/repos/templates/SKILL_template.md` and one nearby installed skill.
   - For upstream material, read the upstream `SKILL.md` or README, every referenced file needed by the workflow, and the license.
   - Completion: every source and required supporting file is known.
4. Choose the output shape.
   - Default: self-contained `SKILL.md`.
   - Keep separate references, templates, examples, or licenses only when they are required or keep the main skill focused.
   - Split skills when branches have materially different invocation or dependency policies.
   - Completion: output files and ownership are explicit.
5. Draft or edit the skill.
   - Frontmatter starts on line 1.
   - Folder name equals `name`, lowercase kebab-case.
   - `description` is a specific invocation trigger.
   - Steps are ordered actions with checkable completion criteria.
   - Safety gates cover only real install, publish, network, secret, destructive-filesystem, or remote-write risk.
   - Completion: every advertised branch is implemented.
6. Prune.
   - Delete no-op prose, duplication, stale assumptions, unsupported metadata, obsolete aliases, and outdated paths.
   - Preserve intentional local preferences when merging upstream changes.
   - Completion: every remaining line changes invocation, execution, safety, output, or verification.
7. Verify and index.
   - Read back every created or changed file.
   - Confirm frontmatter, folder/name equality, description quality, supporting files, attribution, and licenses.
   - Update the global README inventory and maintenance status.
   - Start a fresh OMP process to verify discovery and relevant `skill://` references.

## Global Skill Root

The sole editable source and active OMP runtime is:

```text
C:/Users/allen/.omp/agent/skills/
```

Skill path:

```text
C:/Users/allen/.omp/agent/skills/<skill-name>/SKILL.md
```

Human-facing index and provenance manifest:

```text
C:/Users/allen/.omp/agent/skills/README.md
```

Global README entry:

```md
| `<skill-name>` | <origin> | <maintenance status> |
```

## Install And Update Guidance

- State the exact source, destination, copy or merge behavior, overwrite behavior, and verification step before modifying the active collection.
- Stage external or upstream material outside the global skill root.
- If the destination is absent, copy the complete reviewed skill folder.
- If the destination exists, compare and merge; never replace intentional local preferences silently.
- Preserve required references, templates, examples, attribution, and licenses.
- Update the global README after any inventory, origin, or maintenance-status change.
- Commit verified changes to the local skills Git repository.
- Create an external snapshot before bulk replacement or deletion.
- Create project-local skills only when explicitly requested, under `<workspace>/.omp/skills/<skill-name>/SKILL.md`.
- Do not create a junction or symlink unless the user explicitly requests shared editable state.

## Upstream Adaptation Rules

Classify upstream work before writing:

- `self-contained adaptation`: rewrite the reusable workflow into one local `SKILL.md`.
- `full import`: retain required supporting files and preserve license and attribution.
- `split skills`: separate branches whose invocation or dependency policies differ.

Adapt upstream instructions to OMP conventions unless the user explicitly approves upstream behavior. Remove unsupported metadata and stale upstream assumptions. Treat future upstream updates as reviewed merges, not automatic replacements.
