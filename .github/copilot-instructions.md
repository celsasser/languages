# Copilot Instructions

## Project Overview

This is a **Quarto-based educational website** — the *Computer Language Notebook* — covering systems programming fundamentals: Assembly (dsPIC33F), C, and Rust. Content is authored in `.qmd` files and rendered to static HTML in `docs/` for GitHub Pages.

## Build & Preview Commands

```bash
quarto render          # Build all .qmd files → docs/
quarto preview         # Live-reload dev server
quarto render c.qmd    # Render a single page
```

All rendered output goes to `docs/` (configured in `_quarto.yml`). The `docs/` directory is committed and served directly as GitHub Pages — do not delete it.

## Architecture

- **`_quarto.yml`** — Project config: website type, sidebar nav, global HTML format defaults (theme: cosmo, toc-depth: 4, code-fold: show, styles.css)
- **`_variables.yml`** — Reusable Quarto variables (cross-repo links); reference with `{{< var curtis.D605.notes >}}` syntax
- **Content files** (all `.qmd` at root): `index.qmd` → `assembly.qmd` → `c.qmd` → `rust.qmd` → `glossary.qmd`
- **`docs/`** — Rendered output; committed to repo for GitHub Pages. Never manually edit files here.
- **`reference/`** — Supplementary PDF references (e.g., dsPIC instruction set)

## .qmd File Conventions

### Frontmatter
Pages inherit most defaults from `_quarto.yml`. Per-page frontmatter only needs overrides:
```yaml
---
title: "Page Title"
subtitle: "Optional subtitle"
---
```
Avoid duplicating global settings (`toc`, `theme`, `code-fold`, etc.) already set in `_quarto.yml`.

### Heading Hierarchy
```
## Top-level section
### Subsection
#### Topic
##### Detail
```

### Code Blocks
Python code with figure output uses cell-level directives:
```python
#| label: fig-descriptive-name
#| fig-cap: "Caption text"
#| code-fold: true
```

External links always use `{target=_blank}`:
```markdown
[Link text](https://example.com){target=_blank}
```

### Callouts
```markdown
:::{.callout-note title="Title"}
Content here.
:::
```

### Custom Divs
```markdown
:::{.subheading}
Text styled as a subheading.
:::
```

### Math
Block LaTeX with `$$...$$`, inline with `$...$`.

### Images
```markdown
![Alt text](images/file.png){fig-align="center" width=2.25in}
```

## Navigation

The sidebar is defined in `_quarto.yml` under `website.sidebar.contents`. Adding a new page requires both creating the `.qmd` file **and** adding an entry to `_quarto.yml`.
