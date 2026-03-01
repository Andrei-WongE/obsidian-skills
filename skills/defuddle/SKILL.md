---
name: defuddle
description: "Extract clean markdown content from web pages using Defuddle CLI, removing clutter and navigation to save tokens. Use instead of WebFetch when the user provides a URL to read or analyze, for online documentation, articles, blog posts, or any standard web page."
license: MIT
---

# Defuddle Skill

## How This Skill Works

This skill uses the `defuddle` CLI to extract semantic, readable Markdown from any web URL. It is highly optimized for LLMs, as it strips away navigation, ads, headers, and footers, leaving only the core content. This significantly reduces token usage compared to raw HTML or generic web fetching.

---

## Quick Reference

| Task | Command Pattern |
|------|-----------------|
| Parse to Markdown | `defuddle parse <url> --md` |
| Save to File | `defuddle parse <url> --md -o note.md` |
| Get Metadata | `defuddle parse <url> -p title` |
| JSON Output | `defuddle parse <url> --json` |

---

## Usage Workflow

1. **Verify URL**: Ensure the URL is accessible and publicly available.
2. **Execute Parse**: Run `defuddle parse <url> --md` to get clean Markdown.
3. **Capture Metadata**: If specific fields are needed (title, description, domain), use the `-p` flag.
4. **Integrate**: Use the resulting Markdown for summarization, analysis, or as content for a new Obsidian note.

---

## Output Formats

| Flag | Format |
|------|--------|
| `--md` | Markdown (Optimized for LLMs) |
| `--json` | JSON (Includes both HTML and Markdown) |
| `-p <name>` | Specific metadata property (e.g., `title`, `author`, `published`) |

---

## Key Principles & Best Practices

- **Token Efficiency**: Always prefer `defuddle` over raw `web_fetch` for articles and documentation to save tokens.
- **Markdown First**: Use the `--md` flag for all content-related tasks to ensure the best compatibility with Gemini.
- **Error Handling**: If a page fails to parse, verify if the site uses a heavy SPA framework or requires authentication.

---

## Step 4: Build and QA

Run these checks when using Defuddle to extract content:

```
Defuddle QA checklist:
□ URL is valid and reachable
□ '--md' flag is used for markdown extraction
□ Content extracted contains the primary article/text (not just navigation)
□ Metadata properties are fetched if needed for citations
□ Output is stored in a .md file if intended for an Obsidian vault
```

---

## Dependencies

- `defuddle-cli` (installed via `npm install -g defuddle-cli`).
