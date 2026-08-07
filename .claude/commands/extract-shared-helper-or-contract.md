---
name: extract-shared-helper-or-contract
description: Workflow command scaffold for extract-shared-helper-or-contract in SurfSense.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /extract-shared-helper-or-contract

Use this workflow when working on **extract-shared-helper-or-contract** in `SurfSense`.

## Goal

Centralizes duplicated logic (such as permission checks or OAuth contracts) into a shared helper or type, then updates all consumers to use the new shared code.

## Common Files

- `surfsense_web/atoms/**`
- `surfsense_web/contracts/types/**`
- `surfsense_web/lib/**`
- `surfsense_web/components/settings/roles-manager.tsx`
- `surfsense_web/app/dashboard/[search_space_id]/team/team-content.tsx`
- `surfsense_web/components/assistant-ui/connector-popup/hooks/use-connector-dialog.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify duplicated logic or contract (e.g., permission checks, cookie payload types).
- Extract logic/type into a new shared file (e.g., atoms, types, or lib/).
- Update all consumers to use the new shared helper/type.
- Remove old, duplicated implementations.
- Fix any orphaned or leftover code from the extraction.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.