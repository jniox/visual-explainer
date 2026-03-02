# ODS Brand Theme

The default theme for all visual-explainer output pages. Based on the Orbus Digital Services (ODS) brand guidelines. **Use this theme unless the user explicitly requests a different aesthetic.**

## Google Fonts Import

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@300;400;600;700&family=DM+Sans:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
```

## CSS Custom Properties

```css
:root {
  /* Typography — Sora for headings, DM Sans for body (Nexa alternative) */
  --font-heading: 'Sora', system-ui, sans-serif;
  --font-body: 'DM Sans', 'Helvetica Neue', Arial, sans-serif;
  --font-mono: 'IBM Plex Mono', 'SF Mono', Consolas, monospace;

  /* Light theme (default) — clean white + beige warmth */
  --bg: #FFFFFF;
  --bg-alt: #F9F6F1;            /* Beige — alternate sections */
  --surface: #FFFFFF;
  --surface2: #F5F6F7;           /* Gray 100 */
  --surface-elevated: #FFFFFF;
  --border: rgba(0, 0, 0, 0.08);
  --border-bright: #DFE6E9;      /* Gray 300 */
  --text: #2D3436;               /* Gray 900 — primary text */
  --text-dim: #636E72;           /* Gray 700 — secondary text */
  --text-disabled: #B2BEC3;      /* Gray 500 */

  /* Brand colors */
  --navy: #1E3A5F;
  --navy-light: #2A4A74;
  --navy-dark: #162E4D;
  --navy-dim: rgba(30, 58, 95, 0.08);
  --accent: #FF8C42;             /* Orange — primary accent, CTA */
  --accent-light: #FFA566;
  --accent-dark: #E67A35;
  --accent-dim: rgba(255, 140, 66, 0.10);

  /* Semantic node colors for diagrams */
  --node-a: #1E3A5F;             /* Navy — primary nodes */
  --node-a-dim: rgba(30, 58, 95, 0.08);
  --node-b: #FF8C42;             /* Orange — accent nodes */
  --node-b-dim: rgba(255, 140, 66, 0.10);
  --node-c: #00B894;             /* Green — success/positive */
  --node-c-dim: rgba(0, 184, 148, 0.10);

  /* Functional colors */
  --success: #00B894;
  --success-dim: rgba(0, 184, 148, 0.10);
  --warning: #FDCB6E;
  --warning-dim: rgba(253, 203, 110, 0.10);
  --error: #D63031;
  --error-dim: rgba(214, 48, 49, 0.10);
  --info: #74B9FF;
  --info-dim: rgba(116, 185, 255, 0.10);
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg: #0F2A47;
    --bg-alt: #162E4D;
    --surface: #1E3A5F;
    --surface2: #162E4D;
    --surface-elevated: #2A4A74;
    --border: rgba(255, 255, 255, 0.08);
    --border-bright: rgba(255, 255, 255, 0.15);
    --text: #F5F6F7;
    --text-dim: #B2BEC3;
    --text-disabled: #636E72;

    --navy: #74B9FF;
    --navy-light: #A4D4FF;
    --navy-dark: #3A8CD6;
    --navy-dim: rgba(116, 185, 255, 0.12);
    --accent: #FFA566;
    --accent-light: #FFBE8A;
    --accent-dark: #FF8C42;
    --accent-dim: rgba(255, 165, 102, 0.12);

    --node-a: #74B9FF;
    --node-a-dim: rgba(116, 185, 255, 0.12);
    --node-b: #FFA566;
    --node-b-dim: rgba(255, 165, 102, 0.12);
    --node-c: #55EFC4;
    --node-c-dim: rgba(85, 239, 196, 0.12);

    --success: #55EFC4;
    --success-dim: rgba(85, 239, 196, 0.12);
    --warning: #FFEAA7;
    --warning-dim: rgba(255, 234, 167, 0.12);
    --error: #FF7675;
    --error-dim: rgba(255, 118, 117, 0.12);
    --info: #74B9FF;
    --info-dim: rgba(116, 185, 255, 0.12);
  }
}
```

## Background Atmosphere

Use the navy + orange brand gradient for subtle background depth:

```css
body {
  background: var(--bg);
  background-image:
    radial-gradient(ellipse at 15% 0%, var(--navy-dim) 0%, transparent 45%),
    radial-gradient(ellipse at 85% 100%, var(--accent-dim) 0%, transparent 35%);
}
```

## Typography Rules

Headings always use Sora. Body text uses DM Sans. Mono uses IBM Plex Mono.

```css
h1, h2, h3, h4, h5, h6 {
  font-family: var(--font-heading);
  color: var(--navy);
}

h1 {
  font-size: 38px;
  font-weight: 700;
  letter-spacing: -0.02em;
}

h2 {
  font-size: 28px;
  font-weight: 700;
  letter-spacing: -0.01em;
}

h3 {
  font-size: 22px;
  font-weight: 600;
}

body, p, li {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 1.5;
  color: var(--text);
}

.subtitle, .section-label, code {
  font-family: var(--font-mono);
}
```

## Section Card Patterns

Use navy border accents for primary cards, orange for highlighted/CTA cards:

```css
/* Default card — navy accent border */
.section--navy { border-left: 3px solid var(--navy); }
.section--navy .section-label { color: var(--navy); }
.section--navy .section-label .dot { background: var(--navy); }

/* Accent card — orange highlight */
.section--accent { border-left: 3px solid var(--accent); }
.section--accent .section-label { color: var(--accent); }
.section--accent .section-label .dot { background: var(--accent); }

/* Hero card — elevated with orange-tinted background */
.section--hero {
  background: var(--surface-elevated);
  border: 1px solid color-mix(in srgb, var(--border) 50%, var(--accent) 50%);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
}

/* Callout — navy left border */
.callout {
  border-left: 3px solid var(--navy);
  background: var(--bg-alt);
}
```

## Code Blocks

```css
code {
  font-family: var(--font-mono);
  font-size: 0.9em;
  background: var(--navy-dim);
  color: var(--navy);
  padding: 2px 6px;
  border-radius: 4px;
}

pre {
  background: var(--navy-dark);
  color: var(--text);
  padding: 16px;
  border-radius: 8px;
  overflow-x: auto;
  font-family: var(--font-mono);
  font-size: 14px;
  line-height: 1.6;
}
```

## Status Indicators

Match the ODS functional colors:

```css
.badge--success { background: var(--success-dim); color: var(--success); }
.badge--warning { background: var(--warning-dim); color: var(--warning); }
.badge--error   { background: var(--error-dim);   color: var(--error); }
.badge--info    { background: var(--info-dim);     color: var(--info); }
```

## Mermaid Theme Variables

```javascript
const isDark = window.matchMedia('(prefers-color-scheme: dark)').matches;

mermaid.initialize({
  startOnLoad: true,
  theme: 'base',
  look: 'classic',
  themeVariables: {
    primaryColor: isDark ? '#1E3A5F' : '#E8F0FE',
    primaryBorderColor: isDark ? '#74B9FF' : '#1E3A5F',
    primaryTextColor: isDark ? '#F5F6F7' : '#1E3A5F',
    secondaryColor: isDark ? '#2A4A74' : '#FFF2E0',
    secondaryBorderColor: isDark ? '#FFA566' : '#FF8C42',
    secondaryTextColor: isDark ? '#F5F6F7' : '#2D3436',
    tertiaryColor: isDark ? '#162E4D' : '#F9F6F1',
    tertiaryBorderColor: isDark ? '#55EFC4' : '#00B894',
    tertiaryTextColor: isDark ? '#F5F6F7' : '#2D3436',
    lineColor: isDark ? '#636E72' : '#B2BEC3',
    fontSize: '16px',
    fontFamily: "'Sora', 'DM Sans', system-ui, sans-serif",
    noteBkgColor: isDark ? '#162E4D' : '#F9F6F1',
    noteTextColor: isDark ? '#F5F6F7' : '#2D3436',
    noteBorderColor: isDark ? '#FFA566' : '#FF8C42',
  }
});
```

## Chart.js Colors

When using Chart.js, apply ODS palette:

```javascript
const odsColors = {
  navy: '#1E3A5F',
  orange: '#FF8C42',
  success: '#00B894',
  info: '#74B9FF',
  warning: '#FDCB6E',
  error: '#D63031',
  navyLight: '#2A4A74',
  orangeLight: '#FFA566',
};

// Use as dataset backgroundColor array:
// [odsColors.navy, odsColors.orange, odsColors.success, odsColors.info, odsColors.warning]
```

## Design Principles

1. **Navy dominates, orange accents.** Use navy (#1E3A5F) for headers, section labels, primary surfaces. Use orange (#FF8C42) sparingly for CTAs, highlights, and interactive elements.
2. **Beige warmth.** Use #F9F6F1 for alternate section backgrounds to create visual rhythm without harshness.
3. **Sora speaks, DM Sans reads.** Headings and labels in Sora (distinctive, geometric). Body text in DM Sans (comfortable reading).
4. **Functional colors are semantic.** Green for success, amber for warning, red for error, light blue for info. Never use them decoratively.
5. **Depth through subtlety.** Navy-tinted shadows, low-opacity borders, gentle gradients. The brand is professional, not flashy.
