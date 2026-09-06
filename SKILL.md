---
name: skill-audit-and-hygiene
description: Use when auditing, simplifying, or publishing an AI agent skill. Separates reusable procedures from persona, user, project, and environment context, then validates the cleaned skill.
version: 1.0.0
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

Audit structure, ownership boundaries, process weight, duplication, evidence quality, and publication safety. Do not automatically edit, delete, or publish anything without an explicit delivery boundary.

## When to Use

Use when a skill is too long, slow to load, context-specific, duplicated, difficult to follow, or being prepared for public reuse. Also use when the user asks to audit, sanitize, slim down, modularize, or publish a skill.

Do not use for SOUL/persona edits, user-memory edits, product requirements, or implementation review of the software described by a skill.

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

Record the exact path, revision or hash, included files, local changes, requested delivery boundary, and whether the target is local-only, reusable, or public. Do not silently treat an unclear or changing copy as authoritative.

### 2. Read the whole skill group

Inspect `SKILL.md`, linked references, templates, scripts, examples, metadata, related skills, and repository rules when applicable. Do not inspect only the main file; leakage often hides in references and examples.

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

Rewrite summary:
Validation:
Remaining risks:
Delivery state:
```

Identify the file and section for every finding. Distinguish observed facts from interpretation.

## Validation checklist

- [ ] Frontmatter starts at byte zero; name, trigger description, and body are valid.
- [ ] Size, naming, metadata, and linked references follow the host convention.
- [ ] No personal identity, persona, relationship, or preferred-address rules are embedded.
- [ ] No private business data, personal paths, usernames, or hidden project assumptions remain.
- [ ] Project-specific and environment-specific procedures are separated or clearly scoped.
- [ ] Core workflow is understandable without unrelated context.
- [ ] Task-size and risk escalation are covered where applicable.
- [ ] Duplicate normative rules and stale content are removed.
- [ ] Evidence and status terms are explicit.
- [ ] Conflict markers and sensitive-data leaks are absent.
- [ ] `git diff --check` passes when Git is involved.
- [ ] Local/repository copies match when synchronization is required.
- [ ] Push, package, release, and platform acceptance are reported separately.
- [ ] Destructive cleanup was authorized.

## Common pitfalls

1. Deleting all concrete examples instead of separating principles from local context.
2. Checking only `SKILL.md` and missing leakage in references, templates, or scripts.
3. Making a skill shorter by removing acceptance criteria and evidence requirements.
4. Keeping a personal rule because it makes the skill feel natural.
5. Creating a reference without a trigger, causing unnecessary loading.
6. Treating frontmatter validation as proof that the workflow is sound.
7. Publishing the current tree without checking history, examples, or release assets.
8. Changing behavior or delivery scope while calling the work documentation-only.
9. Deleting old material before preserving required historical evidence.

## Completion rule

The audit is complete only when the target and baseline are known, the whole skill group is inspected, ownership is classified, context is removed/moved/scoped, the reusable workflow remains executable, validation has run, and remaining unverified items and delivery state are reported honestly.
