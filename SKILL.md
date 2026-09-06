---
name: skill-audit-and-hygiene
description: Use when auditing or simplifying a local AI agent skill. Separates reusable procedures from persona, user, project, and environment context, then validates the local result. Use publication scope for repository or open-source checks.
version: 1.1.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [skills, audit, hygiene, reusable, validation, sanitization]
    related_skills: [agent-development-discipline]
---

# Skill Audit and Hygiene

## Overview

A reusable workflow for reviewing, simplifying, and validating AI agent skills. It keeps skills focused on transferable procedures instead of absorbing a user's identity, persona, preferences, business data, project paths, machine configuration, or one-off history.

The default scope is local and read-only. Auditing and editing are separate modes: inspection does not imply permission to change files. Repository, history, release, and publication checks are opt-in additions, not prerequisites for ordinary local skill work.

## When to Use

Use by default when auditing or simplifying a locally installed, locally created, or locally checked-out AI agent skill:

- the skill is too long or slow to load;
- it contains user, persona, business, project, or machine-specific context;
- it has duplicate or conflicting rules;
- its references are poorly separated;
- its workflow is too heavy for the task;
- its evidence and validation language is unclear.

Use the publication audit only when the user explicitly asks to open-source, publish, push, release, or prepare the skill for public reuse.

Do not use for SOUL/persona edits, user-memory edits, product requirements, or implementation review of software described by a skill.

## Default boundary

The default audit is local-only and audit-only. Do not edit files, commit, push, publish, create a release, inspect remote repository state, rewrite Git history, or perform public-release cleanup unless the user explicitly authorizes the corresponding scope.

An instruction to audit, review, inspect, or report findings does not by itself authorize edits. An instruction to simplify, sanitize, or fix may authorize edits only when the target and edit boundary are clear; otherwise stop after the audit and ask for authorization.

## Audit modes

### Local audit-only — default

1. Locate and freeze the local skill group.
2. Inspect `SKILL.md`, references, templates, scripts, examples, metadata, and applicable local instructions.
3. Classify content ownership.
4. Check persona, user, business, project, machine, and environment leakage.
5. Check trigger quality, process weight, duplication, information architecture, and evidence language.
6. Report findings and proposed changes without modifying files.
7. Stop.

A local audit-only run can complete without editing files, GitHub access, remote queries, commits, releases, or publication checks.

### Local audit-and-edit — opt-in

Run only when the user explicitly authorizes changes, or when the task wording clearly requests a bounded edit such as “audit and fix this skill.” Complete the local audit-only steps first, then:

1. Confirm the files and sections allowed to change.
2. Preserve the audit findings and intended scope.
3. Apply only the authorized local edits.
4. Re-inspect the complete skill group for leakage, duplication, and scope drift.
5. Validate the edited local result and report both findings and changes.

If the audit reveals a change outside the authorized boundary, stop and report it instead of extending the edit.

### Publication audit — opt-in

Run only when public reuse or repository delivery is explicitly in scope. State separately whether the publication audit is audit-only or audit-and-edit. Complete the local audit first, then additionally:

1. Inspect repository status, history, examples, and release assets where relevant.
2. Scan tracked and published content for secrets, private information, local paths, and generated artifacts.
3. Verify repository, package, release, and platform states separately.
4. Report public-release readiness separately from local-audit completion.

## Ownership boundary

| Content | Correct location |
|---|---|
| Transferable method, workflow, checklist, or validation rule | Skill |
| Agent identity, personality, relationship, tone, or preferred address | SOUL / persona |
| Stable user facts and broad preferences | User profile / Memory |
| Project architecture, business rules, paths, commands, and decisions | Project instructions and documents |
| Machine-specific setup or platform procedure | Separate environment skill or project context |
| Temporary task state and investigation notes | Task record or session history |

A reusable skill must not contain personal names, forms of address, private paths, real business details, customer data, or rules that only make sense in one project.

## Audit procedure

### 1. Freeze the target

For a local audit, record the local skill path, included files, current local revision when available, local changes, and requested audit scope. Record repository, remote, history, package, and release information only for an explicitly requested publication audit.

Do not silently treat an unclear or changing copy as authoritative.

### 2. Read the whole skill group

Inspect `SKILL.md`, linked references, templates, scripts, examples, metadata, related skills, and applicable repository rules. Do not inspect only the main file; leakage often hides in references and examples.

### 3. Classify before rewriting

For each section or file, classify it as:

- **keep** — already reusable;
- **abstract** — useful experience that must be generalized;
- **move** — belongs in user, persona, project, or environment context;
- **split** — valid but too specialized for the core skill;
- **remove** — duplicate, stale, speculative, or unsupported;
- **verify** — claim or procedure needs real evidence.

Record classifications before making a substantial rewrite.

### 4. Check context leakage

Search for personal names and address, persona language, real business or customer facts, absolute paths and usernames, machine-specific commands, project ports/databases/services, and historical preferences presented as universal rules.

Do not delete a valid platform principle merely because it has a concrete example. Separate:

```text
portable principle → platform procedure → project implementation
```

Keep the portable principle in the core skill. Move specialized procedures to a triggered reference or separate skill.

### 5. Check process weight

The skill should select the smallest sufficient process and define escalation triggers.

| Task type | Minimum process |
|---|---|
| Small change | Scope, targeted check, diff review |
| Normal feature | Requirements, short plan, behavior verification |
| Migration or high-risk work | Recovery plan, compatibility/platform checks, delivery review |

Escalate for irreversible actions, production data, permissions, public publication, compatibility migrations, or platform-specific artifacts.

### 6. Check information architecture

Verify that the core skill contains the reusable workflow, references are trigger-loaded, each reference has one responsibility, repeated rules have one normative source, examples are not mistaken for mandatory policy, and related skills resolve or are explicitly optional. Keep the description tool- and user-agnostic.

### 7. Check evidence language

A verification rule should identify the action or command, inputs, expected result, actual result, evidence type, status, and limitations. Use explicit states such as `passed`, `failed`, `blocked`, `deferred`, and `unverified`.

Do not treat file existence, syntax success, process startup, automated tests, real user flow, target-platform acceptance, and release publication as equivalent evidence.

### 8. Rewrite conservatively

Preserve transferable rules, generalize concrete examples, retain acceptance logic, remove or move context, split triggered details, and avoid speculative frameworks. Do not change product policy, platform guarantees, or delivery scope while claiming documentation-only cleanup.

## Audit report

```text
Audit mode: local-audit-only | local-audit-and-edit | publication-audit-only | publication-audit-and-edit
Target:
Baseline:
Scope:
Files inspected:

Findings:
- must fix:
- should abstract:
- move to user/persona:
- move to project context:
- split into reference:
- duplicate or stale:
- not verified:

Local validation:
Publication validation:
Remaining risks:
Delivery state:
```

Identify the file and section for every finding. Distinguish observed facts from interpretation. For local audits, publication validation is `not applicable`, not an unfinished task. For audit-only runs, change status is `not applicable`; do not imply that recommended edits were applied.

## Validation checklist

### Local audit-only

- [ ] Frontmatter starts at byte zero; name, trigger description, and body are valid.
- [ ] Size, naming, metadata, and linked references follow the host convention.
- [ ] The complete local skill group was inspected.
- [ ] No personal identity, persona, relationship, or preferred-address rules are embedded.
- [ ] No private business data, personal paths, usernames, or hidden project assumptions remain.
- [ ] Project-specific and environment-specific procedures are separated or clearly scoped.
- [ ] Core workflow is understandable without unrelated context.
- [ ] Task-size and risk escalation are covered where applicable.
- [ ] Duplicate normative rules and stale content are removed or classified.
- [ ] Evidence and status terms are explicit.
- [ ] Local changes and conflict markers were checked where applicable.

### Local audit-and-edit — only when explicitly authorized

- [ ] The edit boundary was confirmed before changing files.
- [ ] Only authorized files and sections were changed.
- [ ] The edited skill group was re-inspected and revalidated.
- [ ] Findings, applied changes, and remaining recommendations are reported separately.

### Publication audit — only when explicitly in scope

- [ ] Audit-only versus audit-and-edit scope was explicit.
- [ ] Repository history and relevant release assets were inspected.
- [ ] Public files were scanned for secrets and private information.
- [ ] Repository, package, release, and platform states are reported separately.
- [ ] Local and remote copies match when synchronization is required.
- [ ] Publication readiness is reported separately from local-audit completion.

## Common pitfalls

1. Treating an audit or review request as permission to edit.
2. Checking repository or release state during a local-only audit.
3. Deleting all concrete examples instead of separating principles from local context.
4. Checking only `SKILL.md` and missing leakage in references, templates, or scripts.
5. Making a skill shorter by removing acceptance criteria and evidence requirements.
6. Keeping a personal rule because it makes the skill feel natural.
7. Creating a reference without a trigger, causing unnecessary loading.
8. Treating frontmatter validation as proof that the workflow is sound.
9. Publishing a cleaned current tree without checking history, examples, and release assets.
10. Changing behavior or delivery scope while calling the work documentation-only.
11. Deleting old material before preserving required historical evidence.

## Completion rule

A local audit-only run is complete when the local target is known, the whole skill group is inspected, ownership is classified, findings are reported, local validation has run, and no unauthorized edits occurred. A local audit-and-edit run additionally requires an explicit edit boundary, revalidation after changes, and separate reporting of applied and unapplied recommendations. A publication audit additionally requires the explicit publication checks and a separate public-readiness result.
