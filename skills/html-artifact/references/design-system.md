# Birchline Design System

Reference for HTML artifact generation. Copy the `:root` block below into the artifact's `<style>` to get all tokens at once. Use only the components and tokens needed for the task — the system is selective.

---

## CSS Variables (drop-in)

Paste this into every artifact's `<style>` block:

```css
:root {
  /* Colors — Primary */
  --clay: #D97757;
  --slate: #141413;
  --ivory: #FAF9F5;
  --oat: #E3DACC;

  /* Colors — Neutral */
  --white: #FFFFFF;
  --gray-100: #F0EEE6;
  --gray-300: #D1CFC5;
  --gray-500: #87867F;
  --gray-700: #3D3D3A;

  /* Colors — Semantic */
  --success: #788C5D;
  --warning: #C78E3F;
  --danger:  #B04A4A;
  --info:    #5C7CA3;

  /* Typography */
  --serif: ui-serif, Georgia, serif;
  --sans:  system-ui, -apple-system, sans-serif;
  --mono:  ui-monospace, 'SF Mono', Menlo, monospace;

  /* Spacing */
  --sp-1: 4px;
  --sp-2: 8px;
  --sp-3: 12px;
  --sp-4: 16px;
  --sp-5: 24px;
  --sp-6: 32px;
  --sp-7: 48px;
  --sp-8: 64px;

  /* Radius */
  --r-xs: 4px;
  --r-sm: 8px;
  --r-md: 12px;
  --r-lg: 20px;
  --radius-row:   var(--r-sm);  /* buttons, inputs, list rows */
  --radius-panel: var(--r-md);  /* cards, panels, containers */

  /* Elevation */
  --shadow-sm: 0 1px 2px rgba(20, 20, 19, 0.06);
  --shadow-md: 0 4px 10px rgba(20, 20, 19, 0.08);
  --shadow-lg: 0 12px 28px rgba(20, 20, 19, 0.12);

  /* Border */
  --border: 1.5px solid var(--gray-300);
}

body {
  background: var(--ivory);
  color: var(--slate);
  font-family: var(--sans);
  font-size: 15px;
  line-height: 1.55;
  -webkit-font-smoothing: antialiased;
}
```

---

## Color

### Primary
| Token | Hex | Use |
|---|---|---|
| `--clay` | `#D97757` | Primary actions, accent, focus rings |
| `--slate` | `#141413` | Body text, headings |
| `--ivory` | `#FAF9F5` | Page background |
| `--oat` | `#E3DACC` | Subtle surfaces, secondary backgrounds |

### Neutral
| Token | Hex | Use |
|---|---|---|
| `--white` | `#FFFFFF` | Cards, inputs, panels |
| `--gray-100` | `#F0EEE6` | Hover states, dividers, muted backgrounds |
| `--gray-300` | `#D1CFC5` | Borders |
| `--gray-500` | `#87867F` | Tertiary text, placeholders |
| `--gray-700` | `#3D3D3A` | Secondary text |

### Semantic
| Token | Hex | Use |
|---|---|---|
| `--success` | `#788C5D` | Success states, "done" |
| `--warning` | `#C78E3F` | Warnings, overdue |
| `--danger` | `#B04A4A` | Errors, destructive actions |
| `--info` | `#5C7CA3` | Informational accents |

---

## Typography

Headings use `--serif`; body and UI use `--sans`. Format: `size / line-height / weight`.

| Class | Family | Spec | Use |
|---|---|---|---|
| `.t-display` | serif | 48 / 1.1 / 500, tracking `-0.02em` | Hero / page-level title |
| `.t-h1` | serif | 32 / 1.2 / 500, tracking `-0.01em` | Section title |
| `.t-h2` | serif | 24 / 1.3 / 500 | Subsection title |
| `.t-body` | sans | 16 / 1.55 / 430 | Default body |
| `.t-small` | sans | 14 / 1.5 / 430 | Secondary text, dense UI |
| `.t-caption` | sans | 12 / 1.4 / 500, color `--gray-500` | Metadata, labels |

```css
.t-display { font-family: var(--serif); font-size: 48px; line-height: 1.1;  font-weight: 500; letter-spacing: -0.02em; }
.t-h1      { font-family: var(--serif); font-size: 32px; line-height: 1.2;  font-weight: 500; letter-spacing: -0.01em; }
.t-h2      { font-family: var(--serif); font-size: 24px; line-height: 1.3;  font-weight: 500; }
.t-body    { font-family: var(--sans);  font-size: 16px; line-height: 1.55; font-weight: 430; }
.t-small   { font-family: var(--sans);  font-size: 14px; line-height: 1.5;  font-weight: 430; }
.t-caption { font-family: var(--sans);  font-size: 12px; line-height: 1.4;  font-weight: 500; color: var(--gray-500); }
```

---

## Spacing

8px-based scale. Use these for padding, margin, and gap.

| Token | Value |
|---|---|
| `--sp-1` | 4px |
| `--sp-2` | 8px |
| `--sp-3` | 12px |
| `--sp-4` | 16px |
| `--sp-5` | 24px |
| `--sp-6` | 32px |
| `--sp-7` | 48px |
| `--sp-8` | 64px |

---

## Radius & Elevation

### Radius
| Token | Value | Use |
|---|---|---|
| `--r-xs` | 4px | Inline chips, small marks |
| `--r-sm` (= `--radius-row`) | 8px | Buttons, inputs, list rows |
| `--r-md` (= `--radius-panel`) | 12px | Cards, panels, containers |
| `--r-lg` | 20px | Hero blocks, modals |

### Elevation
| Token | Value | Use |
|---|---|---|
| `--shadow-sm` | `0 1px 2px rgba(20,20,19,0.06)` | Resting cards, subtle lift |
| `--shadow-md` | `0 4px 10px rgba(20,20,19,0.08)` | Hover, popovers |
| `--shadow-lg` | `0 12px 28px rgba(20,20,19,0.12)` | Modals, dropdowns |

---

## Core Components

### Button

```html
<button class="btn btn-primary">Create task</button>
<button class="btn btn-secondary">Cancel</button>
<button class="btn btn-ghost">Skip</button>
<button class="btn btn-danger">Delete</button>
```

```css
.btn {
  display: inline-flex; align-items: center; justify-content: center;
  height: 36px; padding: 0 16px;
  font-family: var(--sans); font-size: 14px; font-weight: 500;
  border-radius: var(--radius-row);
  border: 1.5px solid transparent;
  cursor: pointer;
  transition: background 0.12s ease, border-color 0.12s ease;
}
.btn-primary   { background: var(--clay); color: var(--white); }
.btn-primary:hover { background: #C7684C; }
.btn-secondary { background: var(--white); color: var(--slate); border-color: var(--gray-300); }
.btn-secondary:hover { background: var(--gray-100); }
.btn-ghost     { background: transparent; color: var(--gray-700); }
.btn-ghost:hover { background: var(--gray-100); }
.btn-danger    { background: var(--danger); color: var(--white); }
.btn-danger:hover { background: #9A3F3F; }
```

**Variants:** one `primary` per view (the main action). `secondary` for neutral alternates, `ghost` for tertiary/dismissive, `danger` for destructive.

### Input

```html
<input class="input" type="text" placeholder="Search tasks…">
```

```css
.input {
  height: 38px; padding: 0 12px; width: 260px;
  font-family: var(--sans); font-size: 14px; color: var(--slate);
  background: var(--white);
  border: var(--border);
  border-radius: var(--radius-row);
  outline: none;
  transition: border-color 0.12s ease, box-shadow 0.12s ease;
}
.input::placeholder { color: var(--gray-500); }
.input:focus {
  border-color: var(--clay);
  box-shadow: 0 0 0 3px rgba(217, 119, 87, 0.15);
}
```

### Checkbox

```html
<label class="checkbox">
  <input type="checkbox">
  Notify assignees
</label>
```

```css
.checkbox {
  display: inline-flex; align-items: center; gap: 10px;
  font-size: 14px; cursor: pointer; user-select: none;
}
.checkbox input {
  appearance: none;
  width: 18px; height: 18px;
  border: var(--border);
  border-radius: 5px;
  background: var(--white);
  margin: 0; cursor: pointer; position: relative;
  transition: background 0.12s ease, border-color 0.12s ease;
}
.checkbox input:checked {
  background: var(--clay);
  border-color: var(--clay);
}
.checkbox input:checked::after {
  content: "";
  position: absolute;
  left: 5px; top: 1px;
  width: 5px; height: 10px;
  border: solid var(--white);
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}
```

### Badge

```html
<span class="badge badge-neutral">Draft</span>
<span class="badge badge-accent">In review</span>
<span class="badge badge-success">Done</span>
<span class="badge badge-warning">Overdue</span>
```

```css
.badge {
  display: inline-flex; align-items: center;
  height: 22px; padding: 0 9px;
  font-size: 12px; font-weight: 500;
  border-radius: 999px;
}
.badge-neutral { background: var(--gray-100); color: var(--gray-700); }
.badge-accent  { background: rgba(217, 119, 87, 0.14); color: var(--clay); }
.badge-success { background: rgba(120, 140, 93, 0.16); color: var(--success); }
.badge-warning { background: rgba(199, 142, 63, 0.16); color: #A06A2A; }
```

---

## Usage Notes

- **Page background** is always `--ivory`. White (`--white`) is reserved for cards and inputs sitting on top of ivory.
- **Borders** are `1.5px` (not 1px) — use the `--border` token.
- **Clay** is the only accent color. Don't introduce additional accents; use neutrals and semantic colors for variety.
- **Serif** is for headings only. Never use serif at body sizes or smaller.
- **Spacing** should stick to the scale. Don't invent values like `10px` or `18px`.
- **Transitions** are short: `0.12s ease` on interactive states.
- **Avoid** heavy shadows, gradients, or rounded corners larger than `--r-lg`. The aesthetic is calm and editorial.