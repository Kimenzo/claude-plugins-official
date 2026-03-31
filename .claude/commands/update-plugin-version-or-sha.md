---
name: update-plugin-version-or-sha
description: Workflow command scaffold for update-plugin-version-or-sha in claude-plugins-official.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /update-plugin-version-or-sha

Use this workflow when working on **update-plugin-version-or-sha** in `claude-plugins-official`.

## Goal

Updates a plugin's version or pinned SHA in the marketplace to pull in new features or fixes.

## Common Files

- `.claude-plugin/marketplace.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit .claude-plugin/marketplace.json to update the version or SHA for the plugin
- Optionally, update plugin files if local copy is maintained

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.