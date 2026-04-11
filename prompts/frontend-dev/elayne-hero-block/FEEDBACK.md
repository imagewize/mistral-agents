# Feedback — Elayne Hero Block

## Critical failure: CSS spacing variable dash bug

All spacing variable references drop the second dash before the numeric suffix.

**Defined correctly in `:root`:**
```css
--wp--preset--spacing--40: 2.5rem;
--wp--preset--spacing--60: 3.75rem;
```

**Referenced incorrectly throughout the canvas:**
```css
gap: var(--wp--preset--spacing-60);     /* wrong — missing dash */
padding: var(--wp--preset--spacing-80); /* wrong — missing dash */
```

This affects every spacing usage in the file. All spacing vars silently resolve to `undefined`, breaking the layout. FRONTEND-DEV.md explicitly calls this a hard requirement: "Never drop a dash."

**Fix:** Replace all `--wp--preset--spacing-{n}` references with `--wp--preset--spacing--{n}` (double dash before the number).

---

## Invalid variable namespace: border-radius

The canvas uses `--wp--preset--border-radius--small` and `--wp--preset--border-radius--large`, but `--wp--preset--` is not a valid WordPress namespace for border radius — WordPress does not expose border radius presets via this naming convention in theme.json.

**Fix:** Use plain custom properties (e.g. `--elayne--border-radius--small`) or hardcode the values directly.

---

## What the agent got right

- Correct split layout: CSS Grid, content left / visual right (Elayne default)
- No background image overlay hero (forbidden pattern avoided)
- Browser mockup fully rendered: mock nav, image placeholder div, 2 text lines, button
- Color variable naming correct: `--wp--preset--color--primary`, `--wp--preset--color--accent`, etc.
- Responsive breakpoint collapses to single column on mobile
