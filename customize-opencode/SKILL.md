---
name: customize-opencode
description: Use ONLY when the user is editing or creating opencode's own configuration: opencode.json, opencode.jsonc, files under .opencode/, or files under ~/.config/opencode/. Also use when creating or fixing opencode agents, subagents, skills, plugins, MCP servers, or permission rules. Do not use for the user's own application code, or for any project that is not configuring opencode itself.
---

# Customize OpenCode Skill

This skill is a **built-in** system skill (no local SKILL.md file exists). It activates automatically when the task involves opencode's own configuration.

## Triggers

- Editing `opencode.json` or `opencode.jsonc`
- Modifying files under `.opencode/`
- Modifying files under `~/.config/opencode/`
- Creating or fixing opencode agents, subagents, skills, plugins
- Setting up MCP servers
- Configuring permission rules

## When NOT to use

- For the user's own application code
- For any project that is not configuring opencode itself
