# CLAUDE.md — Logan Smith Portfolio

This file is the source of truth for Claude Code and any AI assistant working on this portfolio.
Read this fully before making any changes.

---

## Project Overview

**Owner:** Logan Smith  
**Type:** Game design portfolio — static HTML/CSS, no frameworks, no build tools  
**Deployed via:** GitHub Pages  
**Live URL:** `https://yourusername.github.io` (update when live)

**Role being presented:** Combat Designer / Technical Designer / Systems Designer  
**Engine focus:** Unreal Engine 5  

---

## File Structure

```
/
├── index.html                  # Homepage — project grid, skills, contact
├── project-style.css           # Shared styles for ALL project pages
├── about.html                  # About page
├── beast-of-the-west.html      # Project page
├── off-air.html                # Project page
├── project-potion.html         # Project page
├── unsanctified.html           # Project page
├── devils-in-the-details.html  # Project page
└── images/                     # Project screenshots (add manually from Wix)
    ├── beast-of-the-west.jpg
    ├── off-air.jpg
    ├── project-potion.jpg
    ├── unsanctified.jpg
    └── devils-in-the-details.jpg
```

**Important:** `index.html` has its own self-contained `<style>` block.
All project pages (`beast-of-the-west.html`, etc.) share `project-style.css` via `<link>`.
Do NOT move index styles into project-style.css — they are intentionally separate.

---

## Design System

### Colors

```css
--white:  #ffffff;   /* Primary text */
--off:    #111111;   /* Card/surface background */
--black:  #000000;   /* Page background */
--light:  #666666;   /* Secondary/body text, muted labels */
--rule:   #222222;   /* Borders, dividers */
--purple: #8405F7;   /* Primary accent — borders, bullets, hover states */
--green:  #01E0A2;   /* Secondary accent — subtext, labels, hover text, WIP */
```

**Color usage rules:**
- Page background: always `--black`
- Body text: `--white` for headings/titles, `--light` for body copy and secondary info
- `--purple` is for borders, bullet points, and structural accents
- `--green` is for labels, eyebrows, genre tags, hover text, WIP indicators, and callout titles
- `--rule` for divider lines and subtle borders
- `--off` for card/surface backgrounds (slightly lighter than pure black)
- Never use `--green` for large blocks of body text — it is accent only

### Typography

```css
font-family: 'DM Sans', sans-serif;
/* Loaded from Google Fonts — include in every page <head> */
```

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
```

**Weight usage:**
- `300` — body text, taglines, descriptions
- `400` — titles, section headings, nav links
- `500` — labels, eyebrows, uppercase tags, nav name

**Size scale:**
- Page/project titles: `clamp(36px, 5.5vw, 64px)`
- Section headings: `22px`
- Body text: `14–15px`
- Labels/eyebrows: `11px`, `font-weight: 500`, `letter-spacing: 0.12em`, `text-transform: uppercase`
- Meta/tag text: `10–12px`

### Spacing

- Page horizontal padding: `48px` (desktop), `20px` (mobile below 768px)
- Section vertical padding: `56px 0`
- Content max-width: `1100px`, always centered with `margin: 0 auto`
- Card gaps on homepage grid: `20px`
- Card internal padding: `20px 24px 24px`

### Borders & Surfaces

- Project cards on homepage: `border: 1px solid var(--purple)`
- Meta bar on project pages: `border: 1px solid var(--purple)`
- Enemy cards: `border: 1px solid var(--purple)`
- Callout blocks: `border-left: 2px solid var(--purple)`
- Dividers / rules: `1px solid var(--rule)`
- No border-radius anywhere — all corners are sharp/square
- Hover on cards: border switches to `--green`, subtle `box-shadow: 0 0 16px rgba(1,224,162,0.15)`

---

## Component Patterns

### Nav (used on every page)

```html
<nav>
  <a href="index.html" class="nav-name">Logan Smith</a>
  <ul class="nav-links">
    <li><a href="index.html">Work</a></li>
    <li><a href="about.html">About</a></li>
    <li><a href="[RESUME_URL]" target="_blank" class="resume">Resume ↗</a></li>
  </ul>
</nav>
```

Nav is sticky, `height: 60px`, `background: rgba(0,0,0,0.96)`, `backdrop-filter: blur(8px)`.

### Project Card (homepage only)

```html
<a href="page.html" class="project-card">
  <div class="card-img">
    <!-- With image: -->
    <img src="images/filename.jpg" alt="Project Name">
    <!-- Without image (placeholder): -->
    <div class="img-ph">
      <span>Add screenshot</span>
      <code>images/filename.jpg</code>
    </div>
    <!-- Optional WIP tag: -->
    <span class="tag-wip">In Progress</span>
  </div>
  <div class="card-info">
    <div class="card-text">
      <div class="card-genre">Design Type · Another Type</div>
      <div class="card-title">Project Name</div>
      <div class="card-sub">Genre · Team of N · Role</div>
    </div>
    <span class="card-arrow">↗</span>
  </div>
</a>
```

### Project Hero (project pages)

```html
<div class="project-hero">
  <a href="index.html" class="back-link">← All Work</a>
  <div class="project-eyebrow">Design Type · Role · Engine</div>
  <h1 class="project-title">Project Name</h1>
  <p class="project-tagline">One or two sentence description.</p>
  <div class="meta-bar">
    <div class="meta-item"><span class="label">Platform</span><span class="value">PC</span></div>
    <div class="meta-item"><span class="label">Engine</span><span class="value">Unreal Engine 5</span></div>
    <div class="meta-item"><span class="label">Duration</span><span class="value">X Months</span></div>
    <div class="meta-item"><span class="label">Team Size</span><span class="value">N</span></div>
    <div class="meta-item"><span class="label">Playtime</span><span class="value">X min</span></div>
    <div class="meta-item"><span class="label">Role</span><span class="value">Title</span></div>
  </div>
</div>
```

### Content Section

```html
<div class="content-section">
  <h2 class="section-heading">Section Title</h2>
  <p class="body-text">Body copy here.</p>
</div>
```

Sections are separated by `border-bottom: 1px solid var(--rule)`. Last section has no border.

### Callout Block

```html
<div class="callout">
  <div class="callout-title">Label / Decision Name</div>
  <p>Explanation text here.</p>
</div>
```

Use for design decisions, key insights, or anything worth highlighting. Left border is `--purple`.

### Responsibilities List

```html
<ul class="resp-list">
  <li>Responsibility one</li>
  <li>Responsibility two</li>
</ul>
```

### Enemy / Feature Cards

```html
<div class="enemy-grid">
  <div class="enemy-card">
    <div class="enemy-name">Name</div>
    <div class="enemy-desc">Description paragraph.</div>
    <ul class="enemy-traits">
      <li>Trait one</li>
      <li>Trait two</li>
    </ul>
  </div>
</div>
```

Enemy cards use `border: 1px solid var(--purple)`, enemy name is `--green`.
The `.enemy-grid` class uses `auto-fill, minmax(260px, 1fr)` — cards reflow automatically.

### WIP Banner

```html
<div class="wip-banner">Work in progress — content expanding with each milestone.</div>
```

Place at the top of the first `content-section` on any incomplete project page.

### Image Placeholder

```html
<div class="img-placeholder" style="height:260px;">
  <div class="ph-l">Image Label</div>
  <div class="ph-s">images/filename.png</div>
</div>
```

Replace with a real `<img>` tag once screenshots are saved locally.

### Project Footer (project pages)

```html
<div class="project-footer">
  <a href="previous-page.html">← Previous Project</a>
  <a href="next-page.html">Next Project →</a>
</div>
```

---

## Adding a New Project Page

1. Copy any existing project page (e.g. `off-air.html`) as a starting template
2. Update `<title>`, `.project-eyebrow`, `.project-title`, `.project-tagline`, and all `.meta-item` values
3. Replace content sections with the new project's writeup
4. Add the new card to `index.html` in the `.projects` grid
5. Update the `project-footer` prev/next links on neighboring pages
6. Add a screenshot to the `images/` folder and uncomment the `<img>` tag in the card

**Project order (for prev/next nav):**
1. Beast of the West → `beast-of-the-west.html`
2. Off Air → `off-air.html`
3. Project Potion → `project-potion.html`
4. Unsanctified → `unsanctified.html`
5. Devil's in the Details → `devils-in-the-details.html`

---

## Changing the Color Scheme

All colors are CSS custom properties. To retheme the entire site:

1. Open `project-style.css` — update the `:root` block
2. Open `index.html` — update the `:root` block inside its `<style>` tag
3. Both files must be updated — they are not linked to each other

Current accent colors:
- Purple `#8405F7` → swap for any color, update `--purple`
- Green `#01E0A2` → swap for any color, update `--green`

---

## Rules — Do Not Break These

- **No frameworks.** No React, no Tailwind, no build step. Plain HTML and CSS only.
- **No border-radius.** All corners are sharp. This is intentional.
- **No centered body text.** Text is always left-aligned inside containers. Containers are centered.
- **`project-style.css` is shared.** Changes there affect every project page. Do not add page-specific overrides to it — add a `<style>` block in the individual HTML file instead.
- **`index.html` styles are self-contained.** Do not link `project-style.css` to `index.html`.
- **Images go in `/images/`.** Never inline base64 images or link to external CDNs for screenshots.
- **Keep pages static.** No JavaScript required for any current feature. Only add JS if strictly necessary for a new interactive feature.
- **Responsive breakpoint is 768px.** Mobile styles use `padding: 0 20px` and single-column layouts.

---

## Current Projects

| Page | Status | Team | Role |
|------|--------|------|------|
| Beast of the West | In Progress | 3 | Combat Designer |
| Off Air | Complete | 5 | Technical Designer · Combat Designer · Team Lead |
| Project Potion | Complete | 7 | Player Designer · Enemy Designer · Team Lead |
| Unsanctified | Complete (expanding) | 23 | Combat Designer |
| Devil's in the Details | Complete | 5 | Player Designer · Enemy Designer · Team Lead |

---

## Contact & Links

- Email: `logansmithnyan@gmail.com`
- LinkedIn: `https://www.linkedin.com/in/logan-smith-73a0a2197/`
- Resume PDF: `https://46e893d5-50cf-40f7-a3d0-64df644efd2d.filesusr.com/ugd/50c0f4_ea0fd42890f64529af179328ad628935.pdf`

> **Note:** The resume PDF is currently hosted on Wix's CDN. Move it to GitHub or another permanent host before cancelling your Wix plan.
