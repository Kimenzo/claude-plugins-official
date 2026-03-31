```markdown
# claude-plugins-official Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you the core development patterns, coding conventions, and common workflows for contributing to the `claude-plugins-official` repository. This repository manages official plugins for the Claude platform, including their registration, updates, feature additions, and multi-channel support. You'll learn how to structure code, follow naming conventions, and execute key workflows using both manual steps and suggested slash commands.

## Coding Conventions

- **File Naming:**  
  Use camelCase for file names.  
  _Example:_  
  ```
  myPluginFeature.py
  pluginHandler.py
  ```

- **Import Style:**  
  Use absolute imports.  
  _Example:_  
  ```python
  import plugins.telegram.server
  from external_plugins.discord import server
  ```

- **Export Style:**  
  Use named exports (explicitly export functions/classes).  
  _Example:_  
  ```python
  # server.py
  def start_server():
      pass

  __all__ = ["start_server"]
  ```

- **Commit Messages:**  
  - Freeform, but often prefixed with plugin/channel name or feature (e.g., `feat`, `imessage`, `telegram`)
  - Keep messages concise (~53 characters on average)
  _Example:_  
  ```
  feat: add message reply support to telegram plugin
  imessage: fix attachment handling
  ```

## Workflows

### Add Plugin to Marketplace
**Trigger:** When you want to register a new plugin in the Claude plugin marketplace.  
**Command:** `/add-plugin-marketplace`

1. Add or update the entry for your plugin in `.claude-plugin/marketplace.json`.
2. If it's a new plugin, add plugin files under `external_plugins/<plugin>` or `plugins/<plugin>`, including:
   - `.claude-plugin/plugin.json`
   - `.mcp.json`
   - `README.md`
   - `LICENSE`
   - `package.json`
   - `server.ts`
3. If you're only updating, bump the SHA or version in `marketplace.json`.

_Example:_
```json
// .claude-plugin/marketplace.json
{
  "telegram": {
    "version": "1.2.0",
    "sha": "abc123..."
  }
}
```

---

### Update Plugin Version or SHA
**Trigger:** When you want to update an existing plugin to a new version or commit.  
**Command:** `/update-plugin-version`

1. Edit `.claude-plugin/marketplace.json` to update the version or SHA for the plugin.
2. Optionally, update plugin files if you maintain a local copy.

---

### Add or Update Plugin Feature
**Trigger:** When you want to add a new feature or fix a bug in a plugin.  
**Command:** `/plugin-feature`

1. Edit `<plugin>/server.ts` to implement the feature or fix.
2. Update `<plugin>/README.md` to document the change.
3. Update `<plugin>/.claude-plugin/plugin.json` or `package.json` to bump the version if needed.

_Example:_
```typescript
// server.ts
export function newFeature() {
  // implementation
}
```

---

### Add New Skill or Reference to Plugin
**Trigger:** When you want to expand a plugin's functionality or documentation.  
**Command:** `/add-skill`

1. Add a new `SKILL.md`, reference `.md`, or script `.sh` under `skills/<skill>/` or `references/`.
2. Update `plugin.json` or `README.md` as needed.

_Example:_
```
plugins/myPlugin/skills/mySkill/SKILL.md
plugins/myPlugin/skills/mySkill/references/example.md
```

---

### Sync or Regenerate Lockfile
**Trigger:** When you want to update dependencies or fix registry issues for a plugin.  
**Command:** `/regen-lockfile`

1. Regenerate `bun.lock` or the equivalent lockfile for the plugin.
2. Commit the updated lockfile.

---

### Multi-Channel Feature Parity Update
**Trigger:** When you want to ensure all channel plugins (e.g., telegram, discord, imessage) have the same capabilities or bugfixes.  
**Command:** `/sync-channels`

1. Edit `server.ts` in each relevant channel plugin (e.g., `telegram/server.ts`, `discord/server.ts`, `imessage/server.ts`).
2. Update `plugin.json` to bump the version if needed.
3. Edit `README.md` if documentation changes.

---

## Testing Patterns

- **Test Framework:** Unknown (not explicitly detected).
- **Test File Pattern:** Files are named with the pattern `*.test.*`.
- _Example:_
  ```
  telegramServer.test.py
  pluginHandler.test.ts
  ```
- Place tests alongside the code or in a dedicated test directory.

## Commands

| Command                | Purpose                                                                 |
|------------------------|-------------------------------------------------------------------------|
| /add-plugin-marketplace| Register a new plugin in the Claude marketplace                         |
| /update-plugin-version | Update a plugin's version or SHA in the marketplace                     |
| /plugin-feature        | Add or update a feature in an existing plugin                           |
| /add-skill             | Add a new skill, reference, or script to a plugin                       |
| /regen-lockfile        | Regenerate or sync a plugin's lockfile                                  |
| /sync-channels         | Ensure feature/fix parity across multiple channel plugins                |
```