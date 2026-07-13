---
name: workspace-builder
description: Design, create, retrofit, or review LLM-ready workspaces with durable AGENTS.md instructions, optional README files, skill references, and minimal purpose-fit structure.
---

# Workspace Builder

Use this skill to design or update a workspace so future LLM agents can understand its purpose, source-of-truth order, allowed actions, artifact locations, relevant skills, and verification expectations.

## Branches

1. Classify the branch.
   - `design`: produce a workspace plan only; do not edit files.
   - `create`: initialize a new target workspace with the approved durable files and structure.
   - `retrofit`: improve an existing workspace while preserving its conventions and user-owned files.
   - `review`: report gaps, risks, duplication, stale paths, and recommended edits; do not edit files unless the user asks after the review.
   - `install-skills`: prepare or change skills in the global OMP source and runtime; do not copy, overwrite, junction, or symlink until the user approves the exact operation.
   - Completion: branch, target root, and output mode are known.
2. Establish the target root.
   - Do not assume the current directory if the user names another path.
   - If the target is another workspace, explain planned writes before editing it.
   - Completion: every read and write path is relative to the target root or explicitly absolute.
3. Read source material before designing.
   - Read existing target `AGENTS.md` if present.
   - Read existing target `README.md` if present and relevant.
   - Read existing target `.omp/skills/*/SKILL.md` files only when project-local skills are actually present.
   - Read project config, docs, or command files only as needed to discover real conventions and verification commands.
   - If adding global skill references, read the global skills README and each selected skill through `skill://<skill-name>`.
   - Completion: source-of-truth files, existing conventions, and missing references are known.
4. Read templates when producing derived files.
   - For a new or substantially replaced `AGENTS.md`, read `C:/Users/allen/OneDrive/Documents/CodexRepo/dev/repos/templates/AGENTS_template.md` first.
   - For a new workspace-local skill, read `C:/Users/allen/OneDrive/Documents/CodexRepo/dev/repos/templates/SKILL_template.md` first.
   - If a template path is unavailable, report that and proceed with file creation only when the user approves proceeding without the template.
   - Completion: every template used is read, unavailable, or explicitly waived by the user.
5. Define the workspace contract.
   - Mission: what durable outcome the workspace supports.
   - Audience: user only, agents, collaborators, or public readers.
   - Agent role: maintainer, researcher, teacher, reviewer, writer, analyst, coordinator, or another explicit role.
   - Workflows: repeated actions future agents should handle.
   - Artifacts: files, folders, generated outputs, records, and state that persist across sessions.
   - Source order: which instructions, docs, skills, configs, and user messages govern decisions.
   - Safety gates: destructive filesystem actions, Git writes, package installs, network access, external-system writes, publishing, credentials, long-running processes, and global or project-local skill installation.
   - Verification: the smallest checks that prove workspace work is correct for this workspace type.
   - Completion: the contract can be written without unresolved generic placeholders.
6. Choose artifacts.
   - `AGENTS.md`: primary LLM operating contract. Prefer this for durable agent behavior.
   - `README.md`: human-facing purpose, layout, setup, and quickstart. Create only when it helps humans navigate or reuse the workspace.
   - Globally installed OMP skill: reference it by name and `skill://<skill-name>`; do not copy it into the workspace.
   - `<workspace>/.omp/skills/<skill-name>/SKILL.md`: create only when the user explicitly requests a workflow that must remain project-local.
   - Folders: create only when they have an immediate artifact, source file, or tool requirement. Do not scaffold empty folders just to imply structure.
   - Completion: every file or folder has a concrete purpose.
7. Plan edits before writing.
   - State exact files and folders to create or modify.
   - State which template or existing file each derived artifact follows.
   - State whether the plan installs or changes global skills, creates project-local skills, installs packages, accesses the network, starts processes, modifies Git state, or writes outside the target root.
   - Ask only load-bearing questions that cannot be answered from source files.
   - Completion: the user can see the effect before broad or cross-workspace changes occur.
8. Write or report.
   - For `design` and default `review`, return the plan or review report without edits.
   - For `create` and `retrofit`, write the smallest durable artifact set that satisfies the workspace contract.
   - For `install-skills`, follow `skill://skill-builder` install guidance and preserve approval boundaries.
   - Remove unresolved `TODO` placeholders before yielding.
   - Completion: the requested branch output is produced.

## AGENTS.md Rules

When creating or changing `AGENTS.md`:

- Start from `AGENTS_template.md` when a new full file is needed, then adapt it to the workspace.
- Preserve the template's safety floor unless the workspace needs stricter rules.
- For non-code workspaces, replace code-specific fields such as stack, commands, and code verification with workflow-specific equivalents.
- Use `Workspace Context` instead of `Project Context` when the target root is not a single project.
- Keep only durable instructions that should guide future sessions.
- Do not store transient task state, chat summaries, or one-off preferences in `AGENTS.md`.
- Do not duplicate full skill instructions; name the skill and trigger, then require agents to read `skill://<skill-name>` before using a global skill.
- Prefer existing workspace conventions over new sections when the existing convention is clear.
- Remove unsupported assumptions, stale paths, and unresolved placeholders.

Useful sections, selected only when they change behavior:

- `Workspace Purpose` or `Project Context`
- `Source-of-Truth Order`
- `Expected Agent Role`
- `Working Style`
- `Workspace Structure`
- `Skills`
- `Common Workflows`
- `Verification`
- `Safety Gates`
- `Secrets And Private Data`
- `External Systems`
- `File Ownership`
- `Git And Filesystem Safety`
- `GitHub Safety`

## README.md Rules

Use `README.md` for humans, not agent governance.

Include only useful human-facing content:

- workspace purpose;
- layout and key files;
- setup or quickstart;
- common commands when real commands are known;
- available skills by name and use case;
- notes collaborators need before using the workspace.

Do not paste `AGENTS.md` rules or full skill instructions into `README.md`.

## Skill Rules

When referencing or installing skills:

- Read each global skill through `skill://<skill-name>` before adding a durable reference to it.
- Add only skills that match repeated workspace workflows.
- Prefer globally installed OMP skills; do not copy them into a workspace merely to reference them.
- The default global runtime root is `C:/Users/allen/.omp/agent/skills/`.
- For global skill installation or updates, follow `skill://skill-builder`, inspect the global README, and compare an existing destination before overwriting it.
- Create a project-local skill only when explicitly requested, under `<workspace>/.omp/skills/<skill-name>/SKILL.md`.
- For a new project-local skill, use `SKILL_template.md`, ensure frontmatter starts at line 1, ensure folder name equals `name`, and write a trigger-specific `description`.

## Interview Rules

For a blank workspace, ask only the minimum questions needed to avoid guessing:

- What durable work should this workspace support?
- Who will use it: user only, agents, collaborators, or public readers?
- What should future agents be allowed to do without asking?
- What actions should always require approval?
- What artifacts or state should persist across sessions?
- Which global OMP skills or explicitly project-local skills should this workspace use?
- Should this pass produce a plan only, or create/update files?

For an existing workspace, read available context first and ask only questions the files cannot answer.

## Output

- `design`: workspace plan with target root, proposed artifacts, skill references, safety gates, verification model, and open questions.
- `create`: created `AGENTS.md` and any approved `README.md`, project-local skill, or purposeful structure.
- `retrofit`: narrow updates to existing workspace instructions and related human docs.
- `review`: findings grouped by correctness, safety, duplication, missing context, skill usage, and verification gaps.
- `install-skills`: approved global installation plan, then installed global skill paths when approved.

## Verification

After creating or changing a workspace:

- Read back every changed `AGENTS.md`, `README.md`, and `SKILL.md`.
- Confirm all paths target the intended workspace root.
- Confirm `AGENTS.md` has no unresolved `TODO` placeholders.
- Confirm `AGENTS.md` separates durable agent rules from transient task state.
- Confirm source-of-truth order, safety gates, file ownership, and verification rules match the workspace contract.
- Confirm global skill references resolve through `skill://<skill-name>` and project-local references point to existing `.omp/skills` files or explicitly planned missing skills.
- Confirm `README.md`, when present, is human-facing and does not duplicate full skill instructions.
- Confirm each created folder has an immediate artifact, source file, or tool requirement.
- For every new project-local skill, confirm it is under `.omp/skills`, frontmatter starts at line 1, `name` equals the folder name, `description` is a specific trigger, and referenced local files exist or are explicitly planned.
