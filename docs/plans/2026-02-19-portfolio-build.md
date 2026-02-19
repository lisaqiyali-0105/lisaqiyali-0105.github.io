# Portfolio Site Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build and publish `lisaqiyali-0105.github.io` — a minimal builder portfolio with a projects grid and Lisa's AI Corner.

**Architecture:** Single self-contained `index.html` (all CSS + JS inline, no build step). Tag infrastructure built into project cards from day 1; filter UI hidden until 3+ projects. Hosted on GitHub Pages via the special `lisaqiyali-0105.github.io` repo.

**Tech Stack:** HTML5, CSS custom properties, vanilla JS. Google Fonts (Fraunces + Instrument Sans). No frameworks, no dependencies.

---

## Reference: Design Decisions

- **Palette:** bg `#F9F6F1`, accent `#0D9B72`, text `#1E1C19`, text-2 `#5C5852`
- **Fonts:** Fraunces (display/headings), Instrument Sans (body)
- **Aesthetic:** Warm, editorial, minimal — consistent with design-language-course
- **NO:** purple gradients, rounded bento grids, Inter/Roboto, generic AI aesthetics

---

## Reference: Content

### Hero
- Name: Lisa Qiya Li
- Tagline: "I build things to learn things."
- Roles: AI PM at AlphaSense · ex-Morgan Stanley IBD
- Sub-tagline: "Closing the gap between product thinking and technical execution — one project at a time."

### Projects (Day 1)
| Title | Description | Tags | URL |
|-------|-------------|------|-----|
| The Language of Design | A PM's interactive course in design vocabulary — 10 modules, real visual examples | design, learning | https://lisaqiyali-0105.github.io/design-language-course/ |

### People I Follow
| Handle | Name | Why |
|--------|------|-----|
| @joshwoodward | Josh Woodward | Head of Google Labs — AI product strategy at the frontier |
| @karpathy | Andrej Karpathy | Ex-OpenAI/Tesla — teaches AI from first principles |
| @raizamrtn | Raiza Martin | Creator of Huxe and NotebookLM |

### My Writing
**Short form (LinkedIn):**
- "AI can now build everything. But I bet you can tell when AI built it..." → https://www.linkedin.com/posts/lisaqiyali_ai-can-now-build-everything-but-i-bet-you-activity-7430086403079966720-C55d
- "I just published my first Claude Code skill..." → https://www.linkedin.com/posts/lisaqiyali_i-just-published-my-first-claude-code-skill-share-7428281452989124608-cWYR

**Long form (Substack):**
- "I Procrastinated on Claude Code for 4 Months Because of One Word: 'Code'" → https://lisaqiyali.substack.com/p/i-procrastinated-on-claude-code-for

---

### Task 1: Create GitHub repo and local directory

**Files:**
- Create: `~/Documents/portfolio/index.html`

**Step 1: Initialize git repo**
```bash
cd ~/Documents/portfolio && git init && git add docs/ && git commit -m "Add design doc"
```

**Step 2: Create GitHub repo with exact magic name**
```bash
gh repo create lisaqiyali-0105.github.io --public --source=. --remote=origin --description "Lisa Qiya Li — builder portfolio"
```

**Step 3: Verify**
```bash
gh repo view lisaqiyali-0105.github.io --web
```
Expected: GitHub repo page opens in browser.

---

### Task 2: Build the HTML skeleton

**Files:**
- Create: `~/Documents/portfolio/index.html`

**Step 1: Create index.html with head, meta tags, font imports**

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lisa Qiya Li — Builder</title>

<!-- SEO -->
<meta name="description" content="Lisa Qiya Li — AI PM, builder, closing the gap between product thinking and technical execution.">
<link rel="canonical" href="https://lisaqiyali-0105.github.io/">

<!-- Open Graph -->
<meta property="og:type" content="website">
<meta property="og:url" content="https://lisaqiyali-0105.github.io/">
<meta property="og:title" content="Lisa Qiya Li — Builder">
<meta property="og:description" content="I build things to learn things. AI PM at AlphaSense · ex-Morgan Stanley IBD.">

<!-- Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300..700;1,9..144,300..700&family=Instrument+Sans:ital,wght@0,400;0,500;0,600;1,400&display=swap" rel="stylesheet">
<style>
/* CSS goes here */
</style>
</head>
<body>
<!-- Content goes here -->
<script>
/* JS goes here */
</script>
</body>
</html>
```

**Step 2: Verify file exists**
```bash
ls ~/Documents/portfolio/index.html
```

---

### Task 3: Write CSS tokens and base styles

**Files:**
- Modify: `~/Documents/portfolio/index.html` (inside `<style>`)

**Step 1: Add CSS custom properties and reset**

```css
:root {
  --bg: #F9F6F1;
  --surface: #F2EDE6;
  --border: #E0D9CE;
  --text: #1E1C19;
  --text-2: #5C5852;
  --text-3: #9E9890;
  --accent: #0D9B72;
  --accent-light: rgba(13,155,114,0.1);
  --ff-display: 'Fraunces', Georgia, serif;
  --ff-body: 'Instrument Sans', system-ui, sans-serif;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: var(--ff-body);
  font-size: 16px;
  line-height: 1.6;
  max-width: 780px;
  margin: 0 auto;
  padding: 80px 32px 120px;
}

a { color: var(--accent); text-decoration: none; }
a:hover { text-decoration: underline; }
```

---

### Task 4: Build hero section

**Files:**
- Modify: `~/Documents/portfolio/index.html` (inside `<body>`)

**Step 1: Add hero HTML**

```html
<header class="hero">
  <p class="hero-label">LISA QIYA LI</p>
  <h1 class="hero-title">I build things<br>to learn things.</h1>
  <p class="hero-roles">AI PM at AlphaSense · ex-Morgan Stanley IBD</p>
  <p class="hero-sub">Closing the gap between product thinking and technical execution — one project at a time.</p>
</header>
```

**Step 2: Add hero CSS**

```css
.hero { margin-bottom: 80px; padding-bottom: 64px; border-bottom: 1px solid var(--border); }
.hero-label { font-family: var(--ff-body); font-size: 0.72rem; font-weight: 600; letter-spacing: 0.12em; color: var(--accent); margin-bottom: 20px; }
.hero-title { font-family: var(--ff-display); font-size: clamp(3rem, 7vw, 5rem); font-weight: 300; line-height: 1.05; color: var(--text); margin-bottom: 20px; letter-spacing: -0.02em; }
.hero-roles { font-size: 0.9rem; color: var(--text-3); margin-bottom: 16px; letter-spacing: 0.01em; }
.hero-sub { font-size: 1.05rem; color: var(--text-2); max-width: 520px; line-height: 1.65; }
```

**Step 3: Open in browser and verify hero looks right**
```bash
open ~/Documents/portfolio/index.html
```

---

### Task 5: Build projects section with tag infrastructure

**Files:**
- Modify: `~/Documents/portfolio/index.html`

**Step 1: Add projects HTML**

```html
<section class="section" id="projects">
  <h2 class="section-title">Projects</h2>

  <!-- Filter bar — hidden via CSS until 3+ projects exist. Remove 'filters-hidden' class to enable. -->
  <div class="filters filters-hidden" id="filters">
    <button class="filter-btn active" data-filter="all">All</button>
  </div>

  <div class="projects-grid" id="projects-grid">

    <a class="project-card" href="https://lisaqiyali-0105.github.io/design-language-course/" target="_blank" rel="noopener" data-tags="design,learning">
      <div class="project-card-inner">
        <div class="project-meta">
          <span class="project-tag">design</span>
          <span class="project-tag">learning</span>
        </div>
        <h3 class="project-title">The Language of Design</h3>
        <p class="project-desc">A PM's interactive course in design vocabulary — 10 modules, real visual examples, no fluff.</p>
        <span class="project-link">Explore →</span>
      </div>
    </a>

  </div>
</section>
```

**Step 2: Add projects CSS**

```css
.section { margin-bottom: 72px; padding-bottom: 64px; border-bottom: 1px solid var(--border); }
.section-title { font-family: var(--ff-display); font-size: 0.8rem; font-weight: 400; letter-spacing: 0.1em; color: var(--text-3); text-transform: uppercase; margin-bottom: 32px; }

/* Filters — hidden until 3+ projects */
.filters { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 28px; }
.filters-hidden { display: none; }
.filter-btn { padding: 6px 14px; border: 1px solid var(--border); background: transparent; border-radius: 100px; font-family: var(--ff-body); font-size: 0.78rem; color: var(--text-2); cursor: pointer; transition: all 0.15s; }
.filter-btn:hover, .filter-btn.active { background: var(--accent); border-color: var(--accent); color: #fff; }

/* Project cards */
.projects-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 20px; }
.project-card { display: block; background: var(--surface); border: 1px solid var(--border); border-radius: 8px; padding: 28px; text-decoration: none; transition: border-color 0.15s, transform 0.15s; }
.project-card:hover { border-color: var(--accent); transform: translateY(-2px); text-decoration: none; }
.project-meta { display: flex; gap: 6px; margin-bottom: 14px; flex-wrap: wrap; }
.project-tag { font-size: 0.68rem; font-weight: 600; letter-spacing: 0.08em; text-transform: uppercase; color: var(--accent); background: var(--accent-light); padding: 3px 8px; border-radius: 3px; }
.project-title { font-family: var(--ff-display); font-size: 1.25rem; font-weight: 500; color: var(--text); margin-bottom: 10px; line-height: 1.25; }
.project-desc { font-size: 0.88rem; color: var(--text-2); line-height: 1.6; margin-bottom: 20px; }
.project-link { font-size: 0.82rem; font-weight: 600; color: var(--accent); letter-spacing: 0.02em; }
```

**Step 3: Add JS for tag filtering (wired up, activates when filter-hidden removed)**

```javascript
const filterBtns = document.querySelectorAll('.filter-btn');
const cards = document.querySelectorAll('.project-card');

// Build filter buttons dynamically from tags
const allTags = new Set();
cards.forEach(card => card.dataset.tags.split(',').forEach(t => allTags.add(t.trim())));
const filtersEl = document.getElementById('filters');
allTags.forEach(tag => {
  const btn = document.createElement('button');
  btn.className = 'filter-btn';
  btn.dataset.filter = tag;
  btn.textContent = tag;
  filtersEl.appendChild(btn);
});

// Filter logic
filtersEl.addEventListener('click', e => {
  if (!e.target.classList.contains('filter-btn')) return;
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  e.target.classList.add('active');
  const filter = e.target.dataset.filter;
  cards.forEach(card => {
    const tags = card.dataset.tags.split(',').map(t => t.trim());
    card.style.display = (filter === 'all' || tags.includes(filter)) ? 'block' : 'none';
  });
});
```

---

### Task 6: Build Lisa's AI Corner

**Files:**
- Modify: `~/Documents/portfolio/index.html`

**Step 1: Add AI Corner HTML**

```html
<section class="section" id="ai-corner">
  <h2 class="section-title">Lisa's AI Corner</h2>

  <div class="corner-block">
    <h3 class="corner-heading">People I Follow</h3>
    <ul class="corner-list">
      <li class="corner-item">
        <a href="https://x.com/joshwoodward" target="_blank" rel="noopener" class="corner-handle">@joshwoodward</a>
        <span class="corner-name">Josh Woodward</span>
        <span class="corner-why">Head of Google Labs — AI product strategy at the frontier</span>
      </li>
      <li class="corner-item">
        <a href="https://x.com/karpathy" target="_blank" rel="noopener" class="corner-handle">@karpathy</a>
        <span class="corner-name">Andrej Karpathy</span>
        <span class="corner-why">Ex-OpenAI/Tesla — teaches AI from first principles, makes the hard stuff accessible</span>
      </li>
      <li class="corner-item">
        <a href="https://x.com/raizamrtn" target="_blank" rel="noopener" class="corner-handle">@raizamrtn</a>
        <span class="corner-name">Raiza Martin</span>
        <span class="corner-why">Creator of Huxe (AI-generated personalized podcast) and NotebookLM</span>
      </li>
    </ul>
  </div>

  <div class="corner-block">
    <h3 class="corner-heading">My Writing</h3>
    <p class="corner-sub">Short form</p>
    <ul class="corner-list writing-list">
      <li><a href="https://www.linkedin.com/posts/lisaqiyali_ai-can-now-build-everything-but-i-bet-you-activity-7430086403079966720-C55d" target="_blank" rel="noopener">AI can now build everything. But I bet you can tell when AI built it...</a><span class="corner-source"> LinkedIn</span></li>
      <li><a href="https://www.linkedin.com/posts/lisaqiyali_i-just-published-my-first-claude-code-skill-share-7428281452989124608-cWYR" target="_blank" rel="noopener">I just published my first Claude Code skill...</a><span class="corner-source"> LinkedIn</span></li>
    </ul>
    <p class="corner-sub">Long form</p>
    <ul class="corner-list writing-list">
      <li><a href="https://lisaqiyali.substack.com/p/i-procrastinated-on-claude-code-for" target="_blank" rel="noopener">I Procrastinated on Claude Code for 4 Months Because of One Word: "Code"</a><span class="corner-source"> Substack</span></li>
    </ul>
  </div>
</section>
```

**Step 2: Add AI Corner CSS**

```css
.corner-block { margin-bottom: 40px; }
.corner-heading { font-family: var(--ff-display); font-size: 1.1rem; font-weight: 500; color: var(--text); margin-bottom: 20px; }
.corner-sub { font-size: 0.72rem; font-weight: 600; letter-spacing: 0.1em; text-transform: uppercase; color: var(--text-3); margin-bottom: 12px; margin-top: 20px; }
.corner-list { list-style: none; display: flex; flex-direction: column; gap: 14px; }
.corner-item { display: grid; grid-template-columns: 120px 1fr; grid-template-rows: auto auto; gap: 2px 12px; padding-bottom: 14px; border-bottom: 1px solid var(--border); }
.corner-item:last-child { border-bottom: none; }
.corner-handle { grid-row: 1; grid-column: 1; font-size: 0.82rem; font-weight: 600; color: var(--accent); }
.corner-name { grid-row: 2; grid-column: 1; font-size: 0.75rem; color: var(--text-3); }
.corner-why { grid-row: 1 / 3; grid-column: 2; font-size: 0.88rem; color: var(--text-2); line-height: 1.55; display: flex; align-items: center; }
.writing-list { gap: 10px; }
.writing-list li { font-size: 0.9rem; }
.writing-list a { color: var(--text); }
.writing-list a:hover { color: var(--accent); }
.corner-source { font-size: 0.72rem; color: var(--text-3); margin-left: 6px; font-weight: 500; }
```

---

### Task 7: Add footer and final polish

**Step 1: Add footer HTML**

```html
<footer class="footer">
  <p>Made by Lisa Qiya Li · <a href="https://github.com/lisaqiyali-0105" target="_blank" rel="noopener">GitHub</a> · <a href="https://lisaqiyali.substack.com" target="_blank" rel="noopener">Substack</a></p>
</footer>
```

**Step 2: Add footer CSS**

```css
.footer { padding-top: 48px; font-size: 0.8rem; color: var(--text-3); }
.footer a { color: var(--text-3); }
.footer a:hover { color: var(--accent); }
```

**Step 3: Open in browser and do a full visual check**
- Hero reads cleanly
- Project card hovers correctly
- AI Corner layout looks right
- Footer is present

---

### Task 8: Commit and push to GitHub Pages

**Step 1: Stage and commit**
```bash
cd ~/Documents/portfolio && git add index.html && git commit -m "Launch portfolio — hero, projects, AI corner"
```

**Step 2: Push**
```bash
git push -u origin main
```

**Step 3: Enable GitHub Pages**
```bash
gh api repos/lisaqiyali-0105/lisaqiyali-0105.github.io/pages \
  --method POST \
  --input - <<'EOF'
{"source": {"branch": "main", "path": "/"}}
EOF
```

**Step 4: Verify live**
```bash
curl -s -o /dev/null -w "%{http_code}" https://lisaqiyali-0105.github.io/
```
Expected: `200`

---

## How to Add Projects in the Future

1. Copy a `<a class="project-card" ...>` block in index.html
2. Update title, description, tags, and href
3. When you have 3+ projects: remove `filters-hidden` class from the `<div class="filters">` element
4. Commit and push — live in ~2 min
