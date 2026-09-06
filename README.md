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

## Default scope: local audit

The default workflow is **local-only**. It can audit a locally installed, locally created, or locally checked-out skill without GitHub access or remote repository operations.

A local audit does **not** automatically:

- commit or push;
- inspect remote repository state;
- create a release or package;
- rewrite Git history;
- perform public-release cleanup.

## Publication audit: opt-in

Repository, history, release-asset, public-security, package, and platform checks run only when the user explicitly requests open-source publication, repository delivery, release preparation, or a publication audit.

The skill reports local-audit completion and public-release readiness as separate results.

## Suggested usage

1. Read [`SKILL.md`](SKILL.md).
2. Locate the target skill group and freeze the local audit scope.
3. Inspect the main file and all locally linked material.
4. Classify content as keep, abstract, move, split, remove, or verify.
5. Apply edits only when authorized.
6. Run the local validation checklist.
7. Use the publication scope only when public delivery is explicitly part of the task.

## Repository boundary

This repository contains only the reusable audit skill. It does not contain a user's persona, personal memory, business context, project instructions, machine paths, or local configuration.

## License

MIT
