---
name: obsidian-markdown
description: "Create and edit Obsidian Flavored Markdown with wikilinks, embeds, callouts, properties, and other Obsidian-specific syntax. Use when working with .md files in Obsidian, or when the user mentions wikilinks, callouts, frontmatter, tags, embeds, or Obsidian notes. This skill covers Obsidian-specific extensions beyond standard CommonMark/GFM."
license: MIT
---

# Obsidian Flavored Markdown Skill

## How This Skill Works

This skill enables the creation and editing of valid Obsidian Flavored Markdown. It extends standard Markdown (headings, bold, italic, lists, quotes, code blocks, tables) with Obsidian-specific features like wikilinks, embeds, callouts, properties, and comments.

---

## Quick Reference

| Task | Guide |
|------|-------|
| Frontmatter & properties | [references/PROPERTIES.md](references/PROPERTIES.md) |
| Callouts (`> [!type]`) | [references/CALLOUTS.md](references/CALLOUTS.md) |
| Internal & media embeds | [references/EMBEDS.md](references/EMBEDS.md) |

---

## Workflow: Creating an Obsidian Note

1. **Add Frontmatter**: Place properties (title, tags, aliases) at the top of the file within `---` blocks.
2. **Write Content**: Use standard Markdown for structure and Obsidian-specific syntax for rich features.
3. **Link Related Notes**: Use wikilinks `[[Note]]` for internal vault connections. Use `[[Note|Display Text]]` for aliases.
4. **Embed Content**: Prefix wikilinks with `!` to embed notes, images, or PDFs inline: `![[embed]]`.
5. **Add Callouts**: Highlight information using the `> [!type]` syntax.
6. **Verify Rendering**: Ensure all links and embeds follow the correct syntax to prevent broken references in Obsidian.

---

## Internal Links (Wikilinks)

```markdown
[[Note Name]]                          Link to note
[[Note Name#Heading]]                  Link to heading
[[Note Name#^block-id]]                Link to block
[[Note Name|Display Text]]             Custom display text
```

Define a block ID by appending `^block-id` to a paragraph or block.

---

## Callouts

```markdown
> [!note]
> Basic callout.

> [!warning] Custom Title
> Callout with a custom title.

> [!faq]- Collapsed by default
> Foldable callout (- collapsed, + expanded).
```

Common types: `note`, `tip`, `warning`, `info`, `example`, `quote`, `bug`, `danger`, `success`, `failure`, `question`, `abstract`, `todo`.

---

## Properties (Frontmatter)

```yaml
---
title: My Note
date: 2024-01-15
tags:
  - project
  - active
aliases:
  - Alternative Name
---
```

---

## Obsidian-Specific Formatting

- **Highlight**: `==Highlighted text==`
- **Comments**: `%%Hidden text%%`
- **Math (LaTeX)**: `$e^{i\pi} + 1 = 0$` or `$$block math$$`
- **Diagrams**: Mermaid blocks are supported. Use `class NodeName internal-link;` to link nodes to notes.

---

## Step 4: Build and QA

Run these checks before finalizing an Obsidian note:

```
Obsidian QA checklist:
□ Frontmatter starts on line 1 and ends with ---
□ All internal links use [[wikilinks]] (not standard Markdown links)
□ All embeds use ![[wikilink]] syntax
□ Callouts use valid types (e.g., [!info], [!warning])
□ Block IDs (^id) are unique within the note
□ Math blocks use valid LaTeX syntax
□ Mermaid diagrams are correctly formatted
□ YAML properties use correct types (lists for tags/aliases)
```

---

## Key Principles

- **Prefer Wikilinks**: Use `[[wikilinks]]` for internal notes so Obsidian can track renames. Use `[text](url)` only for external web links.
- **Atomic Notes**: Aim for one concept per note, linking them together to form a "second brain."
- **Consistent Metadata**: Use the `tags` and `aliases` properties consistently for better discoverability.

---

## Dependencies

- No external CLI dependencies for core markdown editing.
- Optional: `defuddle` skill for extracting markdown from web pages.
