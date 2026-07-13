# Global OMP Skills

This directory is the active user-level OMP skill runtime:

```text
C:/Users/allen/.omp/agent/skills/
```

OMP discovers one skill per child directory using:

```text
<skill-name>/SKILL.md
```

Use an installed skill through `skill://<skill-name>`. Supporting files resolve through `skill://<skill-name>/<relative-path>`.

OMP does not use this README for skill discovery. It is a human-facing deployment manifest and maintenance reference; the authoritative workflow for each skill remains its `SKILL.md`.

## Source And Maintenance Model

- This directory is both the sole editable skill source and the active OMP runtime.
- Maintain skills directly under `C:/Users/allen/.omp/agent/skills/<skill-name>/`.
- Use local Git history for diffs and rollback, and keep external snapshots for disaster recovery.
- Compare an existing skill before replacing or merging upstream material.
- Preserve supporting files, attribution, and licenses when installing or updating.
- Stage external sources outside this directory before copying or merging them into the active collection.
- Do not copy global skills into projects merely to reference them; use `skill://<skill-name>`.
- Create project-local skills only when explicitly requested, under `<workspace>/.omp/skills/<skill-name>/SKILL.md`.

## Installed Skills

| Skill | Origin | Maintenance status |
| --- | --- | --- |
| `company-tech-research` | Local | Locally maintained |
| `domain-modeling` | `mattpocock/skills` | Upstream baseline installed |
| `first-principles-explainer` | Local | Locally maintained |
| `grilling` | `mattpocock/skills` | Upstream baseline installed |
| `improve-codebase-architecture` | `mattpocock/skills` | Upstream baseline installed |
| `offline-visual-explainer` | Local | Locally maintained |
| `research-source-analyzer` | Local | Locally maintained |
| `research-to-omp-experiment` | Local | Locally maintained |
| `rich-visual-explainer` | Local | Locally maintained |
| `sideshow` | Adapted from `modem-dev/sideshow` | Locally adapted and maintained; MIT license included |
| `skill-builder` | Local | Locally maintained |
| `strata-unit-trainer` | Local | Locally maintained |
| `tdd` | `mattpocock/skills` | Upstream baseline installed |
| `teach` | `mattpocock/skills` plus local preferences | Locally merged and maintained |
| `to-spec` | `mattpocock/skills` | Upstream baseline installed |
| `wayfinder` | `mattpocock/skills` | Upstream baseline installed |
| `workspace-builder` | Local | Locally maintained |

## Maintenance

When adding, removing, renaming, or changing an installed skill:

1. Read `C:/Users/allen/.omp/agent/AGENTS.md`.
2. Edit directly in this global skill root.
3. Stage external or upstream material outside the active root.
4. Compare before overwriting or merging an existing skill.
5. Preserve required supporting files, attribution, and licenses.
6. Update this table when the inventory, origin, or maintenance status changes.
7. Verify frontmatter, folder/name equality, supporting files, and `skill://` resolution in a fresh OMP process.
8. Commit the verified change to the local skills Git repository.
9. Create an external snapshot before bulk replacement or deletion.

