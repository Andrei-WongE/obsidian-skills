---
name: obsidian-cli
description: "Interact with Obsidian vaults using the Obsidian CLI to read, create, search, and manage notes, tasks, properties, and more. Also supports plugin and theme development with commands to reload plugins, run JavaScript, capture errors, and take screenshots. Use when the user asks to interact with their Obsidian vault, manage notes, or develop Obsidian plugins."
license: MIT
---

# Obsidian CLI Skill

## How This Skill Works

This skill provides a programmatic interface to a running Obsidian instance via the `obsidian` CLI. It allows for high-level vault operations (reading, creating, appending, searching) as well as low-level developer tools for plugin and theme debugging.

---

## Quick Reference

| Task | Command Pattern |
|------|-----------------|
| Read a note | `obsidian read file="Note Name"` |
| Create a note | `obsidian create name="New" content="# Hello"` |
| Set a property | `obsidian property:set name="key" value="val" file="Note"` |
| Search vault | `obsidian search query="term" limit=10` |
| Reload plugin | `obsidian plugin:reload id="my-plugin"` |

---

## Workflow: Common Vault Operations

1. **Target the File**: Use `file=<name>` (wikilink style) or `path=<path>` (vault root style).
2. **Execute Command**: Run the appropriate `obsidian <command>` with parameters using `<key>=<value>`.
3. **Handle Multiline**: Use `
` for newlines and `	` for tabs in content strings.
4. **Use Flags**: Add boolean switches like `silent` (don't open file) or `overwrite`.
5. **Copy Output**: Append `--copy` to any command to copy the result to the clipboard.

---

## Plugin Development Workflow

1. **Reload**: After code changes, run `obsidian plugin:reload id=plugin-id`.
2. **Debug**: Check for errors using `obsidian dev:errors`.
3. **Verify**: Use `obsidian dev:screenshot` or `obsidian dev:dom` to inspect the UI state.
4. **Console**: Monitor logs with `obsidian dev:console level=error`.

---

## Key Principles & Best Practices

- **Required State**: Obsidian **must** be open and running for the CLI to function.
- **Vault Targeting**: Commands target the last focused vault by default. Use `vault="Name"` as the first parameter to target a specific one.
- **Parameters vs. Flags**: Parameters always use `=`. Flags are standalone keywords.

---

## Step 4: Build and QA

Run these checks before executing or finalizing a series of CLI commands:

```
Obsidian CLI QA checklist:
□ Obsidian app is currently running
□ Parameters use the 'key=value' syntax (no spaces around '=')
□ Values with spaces are enclosed in double quotes
□ Newlines in content are escaped as 

□ 'silent' flag is used for background operations
□ Vault is explicitly specified if multiple vaults are open
□ Plugin ID is correct for dev commands
```

---

## Dependencies

- `obsidian-cli` (installed via `npm install -g obsidian-cli` or similar).
- A running instance of [Obsidian](https://obsidian.md).
