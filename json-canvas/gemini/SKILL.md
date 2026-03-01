---
name: json-canvas
description: "Create and edit JSON Canvas files (.canvas) with nodes, edges, groups, and connections. Use when working with .canvas files, creating visual canvases, mind maps, flowcharts, or when the user mentions Canvas files in Obsidian."
license: MIT
---

# JSON Canvas Skill

## How This Skill Works

This skill enables the programmatic creation and editing of JSON Canvas files (`.canvas`) based on the [JSON Canvas Spec 1.0](https://jsoncanvas.org/spec/1.0/). It supports adding text nodes, file embeds, external links, and visual groups, as well as defining directed edges between them.

---

## Quick Reference

| Task | Guide |
|------|-------|
| Node Types & Attributes | Section: Nodes below |
| Edge Attributes | Section: Edges below |
| Full Examples | [references/EXAMPLES.md](references/EXAMPLES.md) |

---

## Workflow: Creating a JSON Canvas

1. **Initialize Structure**: Create a `.canvas` file with the base structure: `{"nodes": [], "edges": []}`.
2. **Generate IDs**: Generate unique 16-character hexadecimal IDs for every node and edge.
3. **Position Nodes**: Choose `x` and `y` coordinates for nodes. Standard spacing is 50-100px.
4. **Define Nodes**: Add node objects (type: `text`, `file`, `link`, or `group`) with required dimensions (`width`, `height`).
5. **Connect Nodes**: Add edge objects referencing source (`fromNode`) and target (`toNode`) IDs.
6. **Validate JSON**: Ensure the final output is a valid JSON object and all ID references are internal and correct.

---

## Nodes Configuration

| Type | Required Field | Suggested Size |
|------|----------------|----------------|
| `text` | `text` (Markdown) | 300x150 |
| `file` | `file` (Path) | 400x300 |
| `link` | `url` (Link) | 250x100 |
| `group` | `label` (Optional) | Varies |

---

## Key Principles & Layout Guidelines

- **Z-Index**: The order in the `nodes` array determines z-index (first is bottom, last is top).
- **ID Uniqueness**: All node and edge IDs must be unique within the same file.
- **Color Presets**: Use presets `"1"` (Red) through `"6"` (Purple) or hex strings (e.g., `"#FF0000"`).
- **Coordinate System**: `x` increases right, `y` increases down. Negative coordinates are allowed.

---

## Step 4: Build and QA

Run these checks before finalizing a `.canvas` file:

```
JSON Canvas QA checklist:
□ JSON is valid and parseable
□ All 'id' values are unique 16-character hex strings
□ Every 'fromNode' and 'toNode' references a valid node ID
□ Required fields are present for each type (text, file, url)
□ 'type' is one of: text, file, link, group
□ All paths in 'file' nodes are correct relative to vault root
□ 'fromSide' and 'toSide' use valid anchors: top, right, bottom, left
□ All literal newlines in text are escaped as 

```

---

## Dependencies

- None. This skill produces standard JSON files compatible with any JSON Canvas implementation.
