---
name: obsidian-bases
description: "Create and edit Obsidian Bases (.base files) with views, filters, formulas, and summaries. Use when working with .base files, creating database-like views of notes, or when the user mentions Bases, table views, card views, filters, or formulas in Obsidian."
license: MIT
---

# Obsidian Bases Skill

## How This Skill Works

This skill enables the creation and management of Obsidian Bases (`.base` files). Bases provide database-like views (tables, cards, lists, maps) of your Obsidian notes using a YAML-based schema for filters, formulas, and summaries.

---

## Quick Reference

| Task | Guide |
|------|-------|
| Function & Formula Syntax | [references/FUNCTIONS_REFERENCE.md](references/FUNCTIONS_REFERENCE.md) |
| Filter Operators | Section: Filter Syntax below |
| View Configuration | Section: View Types below |

---

## Workflow: Creating an Obsidian Base

1. **Create the File**: Create a file with the `.base` extension and valid YAML content.
2. **Define Scope (Filters)**: Add a `filters` section to select which notes appear (by tag, folder, property, or date).
3. **Add Formulas**: Define computed properties in the `formulas` section using the built-in function library.
4. **Configure Views**: Add one or more views (`table`, `cards`, `list`, or `map`). Specify which properties to display in the `order` array.
5. **Add Summaries**: Map properties to summary formulas (e.g., `Average`, `Sum`, `Count`) for aggregate data.
6. **Validate YAML**: Ensure all strings with special characters are quoted and formula expressions are syntactically correct.

---

## Schema Overview

```yaml
filters:
  and:
    - file.hasTag("task")
    - 'status != "done"'

formulas:
  days_old: '(now() - file.ctime).days'

properties:
  formula.days_old:
    displayName: "Days Old"

views:
  - type: table
    name: "Active Tasks"
    order:
      - file.name
      - status
      - formula.days_old
    summaries:
      formula.days_old: Average
```

---

## Filter Syntax

| Operator | Description |
|----------|-------------|
| `==`, `!=` | Equals, Not Equal |
| `>`, `<` | Greater than, Less than |
| `&&`, `||`, `!` | Logical AND, OR, NOT |

Use `and:`, `or:`, and `not:` keys for complex recursive filtering.

---

## Key Principles & Pitfalls

- **Duration Type**: Subtracting two dates returns a **Duration**, not a number. You **must** access a numeric field (e.g., `.days`) before applying math functions like `.round()`.
- **YAML Quoting**: Formulas containing double quotes **must** be wrapped in single quotes: `'if(done, "Yes", "No")'`.
- **Null Checks**: Properties may not exist on all notes. Use `if(prop, value, "")` to guard against errors.

---

## Step 4: Build and QA

Run these checks before finalizing a `.base` file:

```
Obsidian Bases QA checklist:
□ File extension is .base
□ YAML is valid (all special characters in strings are quoted)
□ Formulas containing double quotes are wrapped in single quotes
□ All Duration math accesses a numeric field (e.g., .days) before rounding
□ All formula.X references in 'order' have a matching entry in 'formulas'
□ At least one view is defined in the 'views' array
□ Global filters are placed at the top level, not inside 'views'
□ Property display names are set for clarity
```

---

## Dependencies

- None. This skill relies on the built-in Obsidian Bases engine.
