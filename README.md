# Obsidian Skills for Gemini CLI

A consolidated collection of Gemini CLI skills for interacting with Obsidian vaults, creating Obsidian-flavored Markdown, building visual canvases, and managing database-like views.

## Installation

This collection is a **Gemini Extension**, allowing you to install all 5 skills with a single command:

```bash
gemini extensions install https://github.com/Andrei-WongE/obsidian-skills
```

### For Local Development
If you have cloned this repository locally, you can link it:

```bash
cd obsidian-skills-gemini
gemini extensions link .
```

## Included Skills

| Skill | Description | Path |
|-------|-------------|------|
| **obsidian-markdown** | Create and edit Obsidian-flavored Markdown (wikilinks, callouts, properties). | `skills/obsidian-markdown` |
| **obsidian-bases** | Build and manage database-like views with `.base` files. | `skills/obsidian-bases` |
| **json-canvas** | Programmatically create and edit visual mind maps and flowcharts (`.canvas`). | `skills/json-canvas` |
| **obsidian-cli** | Interact with a running Obsidian instance via the command line. | `skills/obsidian-cli` |
| **defuddle** | Extract clean, token-efficient Markdown from any web URL. | `skills/defuddle` |

## Structure

This repository is organized as a **Gemini Extension** bundle. To bundle multiple skills into a single installation, the following directory structure is required:

```text
obsidian-skills-gemini/
├── gemini-extension.json     # Required: Extension manifest (name, version, etc.)
├── README.md                 # Project documentation
└── skills/                   # Required: Folder containing all bundled skills
    ├── obsidian-markdown/    # Subfolder for a specific skill
    │   ├── SKILL.md          # Required: Skill definition file
    │   └── references/       # Supporting documentation for the skill
    ├── obsidian-cli/
    │   └── SKILL.md
    ├── obsidian-bases/
    │   └── SKILL.md
    ├── defuddle/
    │   └── SKILL.md
    └── json-canvas/
        └── SKILL.md
```

### Key Components

- **`gemini-extension.json`**: The presence of this file at the root tells the Gemini CLI that this repository is an extension bundle. It contains the extension's metadata.
- **`skills/` Directory**: Gemini CLI automatically scans this directory to discover and register all individual skills. Each skill must have its own subfolder containing a `SKILL.md` file.
- **`claude/` (Optional)**: Each skill folder also includes a `claude/` directory for compatibility with Claude Code.

## Usage

Once installed, these skills are automatically discovered. Gemini will trigger them based on your intent:

- *"Make a new Obsidian note about project X"* (Triggers `obsidian-markdown`)
- *"Create a table view of all my tasks in my vault"* (Triggers `obsidian-bases`)
- *"Draw a mind map for my research topic"* (Triggers `json-canvas`)
- *"Search my vault for 'ideas' and list the first 5"* (Triggers `obsidian-cli`)
- *"Parse this documentation URL to a note"* (Triggers `defuddle`)

## Credits

- **Original Author**: [Kepano](https://github.com/kepano) ([obsidian-skills](https://github.com/kepano/obsidian-skills))
- **Gemini Translation**: [Andrei WongE](https://github.com/Andrei-WongE)

## License

MIT — free to use, adapt, and share.
