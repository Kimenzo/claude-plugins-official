---
name: add-plugin-to-marketplace
description: Workflow command scaffold for add-plugin-to-marketplace in claude-plugins-official.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-plugin-to-marketplace

Use this workflow when working on **add-plugin-to-marketplace** in `claude-plugins-official`.

## Goal

Registers a new plugin in the Claude plugin marketplace, making it available for users.

## Common Files

- `.claude-plugin/marketplace.json`
- `external_plugins/<plugin>/.claude-plugin/plugin.json`
- `external_plugins/<plugin>/.mcp.json`
- `external_plugins/<plugin>/README.md`
- `external_plugins/<plugin>/LICENSE`
- `external_plugins/<plugin>/package.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Add or update entry in .claude-plugin/marketplace.json
- If new plugin: add plugin files under external_plugins/<plugin> or plugins/<plugin> (including .claude-plugin/plugin.json, .mcp.json, README.md, LICENSE, package.json, server.ts, etc.)
- If only updating: bump SHA or version in marketplace.json

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.