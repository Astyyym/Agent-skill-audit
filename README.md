# Agent Skill Audit

A reusable, local-first workflow for auditing and simplifying AI agent skills.

## What this repository provides

`SKILL.md` helps an agent review a skill group for:

- persona, user, business, project, machine, and environment context leakage;
- unclear ownership boundaries;
- excessive length or process weight;
- duplicate or conflicting rules;
- weak trigger and reference structure;
- ambiguous evidence and validation language.

The workflow keeps reusable procedures in Skills, while directing personal identity and tone to persona configuration, stable user facts to user memory, and project facts to project instructions.

## Default scope: local audit-only

The default workflow is **local and read-only**. It can audit a locally installed, locally created, or locally checked-out skill without editing files, GitHub access, or remote repository operations.

An audit, review, inspection, or findings request does not by itself authorize edits.

A local audit does **not** automatically:

- edit files;
- commit or push;
- inspect remote repository state;
- create a release or package;
- rewrite Git history;
- perform public-release cleanup.

## Local audit-and-edit: opt-in

Use this mode only when the user explicitly authorizes changes or clearly requests a bounded audit-and-fix task. Confirm the allowed files and sections, apply only those edits, re-inspect the complete skill group, and report findings separately from applied changes.

## Publication audit: opt-in

Repository, history, release-asset, public-security, package, and platform checks run only when the user explicitly requests open-source publication, repository delivery, release preparation, or a publication audit.

The skill reports local-audit completion and public-release readiness as separate results.

## Suggested usage

1. Read [`SKILL.md`](SKILL.md).
2. Locate the target skill group and freeze the local audit scope.
3. Choose `local-audit-only` unless edits are explicitly authorized; choose `local-audit-and-edit` only with a clear edit boundary.
4. Inspect the main file and all locally linked material.
5. Classify content as keep, abstract, move, split, remove, or verify.
6. In audit-only mode, report proposed changes without editing. In audit-and-edit mode, apply only the explicitly authorized changes.
7. Run the matching local validation checklist.
8. Use the publication scope only when public delivery is explicitly part of the task.

## Repository boundary

This repository contains only the reusable audit skill. It does not contain a user's persona, personal memory, business context, project instructions, machine paths, or local configuration.

## License

MIT
