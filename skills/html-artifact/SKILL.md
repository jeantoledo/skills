---
name: html-artifact
description: Generate self-contained HTML deliverables (reports, dashboards, mockups, one-pagers, summaries) styled with the Birchline design system. Use when the user asks for an HTML file they will open directly in a browser.
---

## When to use

Trigger on requests like: "make an HTML report", "generate a dashboard", "build a one-pager", "give me an HTML summary", or edits to files inside `.claude/artifacts/`.

Do NOT use for:
- Framework components (React, Vue, Svelte, etc.) — different rules apply.
- HTML email — has its own constraints (table layouts, inline styles only, no `<style>` blocks in some clients).
- Files that are part of a site with its own existing design — match that design instead.

## Workflow

1. Read `references/design-system.md` — the single source of truth for tokens (colors, typography, spacing, radius, elevation) and component patterns (`.btn`, `.input`, `.checkbox`, `.badge`).
2. Copy the `:root` block from the design system into the artifact's `<style>` — this installs all tokens at once.
3. Add **only** the component CSS the artifact actually uses. Don't bundle the entire library if the page only needs buttons and badges.
4. Generate **self-contained** HTML — no external `<link>`, no `@import`, no required fonts. The artifact must open standalone in any browser.
5. If you need something the design system doesn't cover, stay within the token scale (existing colors, spacing values, radius tokens). Don't invent new hex values or arbitrary sizes.
6. Save to `.claude/artifacts/` with a descriptive kebab-case filename (e.g. `q2-review.html`). Override only if the user specifies a different location.

## Quality checks before finishing

- File opens standalone — no broken `<link>`, no missing assets, no external fonts required.
- Uses design tokens, not ad-hoc hex values.
- Page background is `--ivory`; `--white` is reserved for cards and inputs.
- Borders are `1.5px` via `var(--border)`, not `1px`.
- Readable line length (max-width ~720–980px for prose).
- Visible focus states on interactive elements.
- Sufficient contrast: avoid `--gray-500` on `--ivory` for body copy.
- Serif (`--serif`) is for headings only — never body text.