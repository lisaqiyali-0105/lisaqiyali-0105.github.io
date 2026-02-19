# Portfolio Site Design
**Date:** 2026-02-19
**Repo:** `lisaqiyali-0105.github.io`
**Live URL:** `https://lisaqiyali-0105.github.io`

---

## Goal
A minimal builder portfolio that grows over time. Targets Google-caliber hiring managers and the tech/builder community simultaneously. Signals: "I don't just spec — I build."

---

## Architecture
- Single `index.html` in repo `lisaqiyali-0105.github.io` (GitHub's magic portfolio repo)
- Self-contained HTML/CSS/JS (no build step, same pattern as design course)
- Tag infrastructure built in from day 1; filter UI activates at 3+ projects

---

## Sections

### 1. Hero
- Name: **Lisa Qiya Li**
- Tagline: *"I build things to learn things."*
- Roles sprinkled in: AI PM at AlphaSense · ex-Morgan Stanley IBD
- Sub-tagline: *"Closing the gap between product thinking and technical execution — one project at a time."*

### 2. Projects
Cards in a clean grid. Each card:
- Title
- One-line description
- Tags (hidden filter UI until 3+ projects exist in the DOM)
- External link

**Day 1 projects:**
| Title | Description | Tags | URL |
|-------|-------------|------|-----|
| The Language of Design | A PM's interactive course in design vocabulary — 10 modules, real visual examples | `design` `learning` | https://lisaqiyali-0105.github.io/design-language-course/ |

### 3. Lisa's AI Corner

**People I Follow**
| Handle | Name | Why |
|--------|------|-----|
| @joshwoodward | Josh Woodward | Head of Google Labs — follows AI product strategy at the frontier |
| @karpathy | Andrej Karpathy | Ex-OpenAI/Tesla — teaches AI from first principles, makes the hard stuff accessible |
| @raizamrtn | Raiza Martin | Creator of Huxe (AI-generated personalized podcast) and NotebookLM |

**Articles That Changed How I Think**
- *(Lisa to add on day 1 or leave as "more coming soon" placeholder)*

**My Writing**
- **Short form (LinkedIn):**
  - "AI can now build everything. But I bet you can tell when AI built it..." → https://www.linkedin.com/posts/lisaqiyali_ai-can-now-build-everything-but-i-bet-you-activity-7430086403079966720-C55d
  - "I just published my first Claude Code skill..." → https://www.linkedin.com/posts/lisaqiyali_i-just-published-my-first-claude-code-skill-share-7428281452989124608-cWYR
- **Long form (Substack):**
  - "I Procrastinated on Claude Code for 4 Months Because of One Word: 'Code'" → https://lisaqiyali.substack.com/p/i-procrastinated-on-claude-code-for

---

## Visual Direction
- Consistent with design course aesthetic (warm light palette, editorial fonts)
- Fonts: Fraunces (display) + Instrument Sans (body)
- Accent: `#0D9B72` teal
- Background: `#F9F6F1` warm off-white
- Minimal — confidence through restraint

---

## What's Explicitly Excluded
- MBA coaching / admissions consulting work
- Personal/private projects (exist at unlisted URLs, never linked from homepage)

---

## Future Growth Pattern
1. Ship a project → add a card
2. Read something great → add to AI Corner
3. Publish a post → add to My Writing
4. At 3+ projects → enable tag filters
