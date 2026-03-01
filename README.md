# Obsidian Skills for Gemini CLI

A consolidated collection of Gemini CLI skills for interacting with Obsidian vaults, creating Obsidian-flavored Markdown, building visual canvases, and managing database-like views.

## Installation

To install these skills for Gemini CLI:

```bash
gemini skills install https://github.com/Andrei-WongE/obsidian-skills-gemini
```

## Included Skills

| Skill | Description |
|-------|-------------|
| **obsidian-markdown** | Create and edit Obsidian-flavored Markdown (wikilinks, callouts, properties). |
| **obsidian-bases** | Build and manage database-like views with `.base` files. |
| **json-canvas** | Programmatically create and edit visual mind maps and flowcharts (`.canvas`). |
| **obsidian-cli** | Interact with a running Obsidian instance via the command line. |
| **defuddle** | Extract clean, token-efficient Markdown from any web URL. |

## Structure

Each skill in this repository is optimized for dual-platform use:

- **`gemini/`**: Native compatibility with Gemini CLI, featuring enhanced metadata, step-by-step workflows, and QA checklists.
- **`claude/`**: Flat structure compatible with Claude Code and other agent platforms.

## Usage

Once installed, these skills are automatically discovered. Gemini will trigger them based on your intent:

- *"Make a new Obsidian note about project X"* (Triggers `obsidian-markdown`)
- *"Create a table view of all my tasks in my vault"* (Triggers `obsidian-bases`)
- *"Draw a mind map for my research topic"* (Triggers `json-canvas`)
- *"Search my vault for 'ideas' and list the first 5"* (Triggers `obsidian-cli`)
- *"Parse this documentation URL to a note"* (Triggers `defuddle`)

## License

MIT — free to use, adapt, and share.
