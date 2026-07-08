---
name: ux-portfolio-website
description: >
  Use this skill whenever the user wants to build, improve, or extend a UX/product design portfolio website. Trigger on phrases like "portfolio site", "case study page", "design portfolio", "showcase my work", "personal website for UX", "add a case study", "make my portfolio better", "world class portfolio", or when the user shares a resume and asks for a website. This skill covers the full stack: homepage architecture, case study page patterns, dark theme system, animation and interaction layer, leadership-focused content strategy, and GitHub Pages deployment. It is built from a real production portfolio for a 14-year UX leader at Western Union. Use it as the authoritative reference — not just for ideas, but for exact CSS, JS, and HTML patterns that are proven to work.
---

# UX Portfolio Website Skill

## Philosophy

A UX portfolio website is itself a UX artefact. It must demonstrate the designer's craft through how it is built, not just what it says. Three principles govern every decision:

1. **Prove craft through execution** — the typography, spacing, transitions, and interactions should feel as intentional as the case study work they showcase
2. **Respect the reader's time** — leadership-first content hierarchy: the executive summary comes before the detail; the full case study is available on demand, not mandatory
3. **Dark theme is not a style choice — it's a positioning choice** — dark backgrounds make screenshots and visual design pop; they signal technical fluency and contemporary aesthetic sensibility

---

## When to Use This Skill

### Must Use
- Building a new UX/product design portfolio website from scratch
- Adding or redesigning case study pages
- Adding interaction patterns (parallax, scroll animations, custom cursor, section nav)
- Converting a light-theme portfolio to dark theme
- Writing the "leadership summary" view for a case study
- Setting up next/previous navigation between case studies

### Recommended
- Reviewing an existing portfolio for content gaps
- Improving homepage engagement (marquee, tilt, parallax)
- Creating a new skill file or template for repeating this pattern

### Skip
- Non-portfolio websites (use the UX_SKILL.md instead)
- Slide decks or presentations (use world-class-presentations.md)

---

## The Design System

Everything is built with plain HTML + CSS + vanilla JS. No framework. Deployable to GitHub Pages with zero build step.

### Color Tokens

```css
:root {
    --yellow:       #FFDD00;          /* primary accent — never overuse */
    --yellow-glow:  rgba(255,221,0,0.15);
    --yellow-dim:   rgba(255,221,0,0.06);
    --bg:           #080808;           /* main background */
    --surface-1:    #101010;           /* elevated surface */
    --surface-2:    #181818;           /* card background */
    --surface-3:    #222222;           /* deepest card */
    --border:       rgba(255,255,255,0.07);
    --border-hover: rgba(255,255,255,0.15);
    --text-1:       rgba(255,255,255,1);
    --text-2:       rgba(255,255,255,0.5);
    --text-3:       rgba(255,255,255,0.25);
    --radius-sm:    10px;
    --radius-md:    18px;
    --radius-lg:    28px;
    --ease-out:     cubic-bezier(0.16, 1, 0.3, 1);
}
```

### Typography

Font: **Inter** via Google Fonts — `wght@300;400;500;600;700;800;900`

```css
body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
```

| Role | Size | Weight | Letter-spacing |
|------|------|--------|----------------|
| Hero title | `clamp(72px, 10vw, 136px)` | 900 | `-4px` |
| Section title | `clamp(30px, 4vw, 46px)` | 800 | `-1.5px` |
| Card title | `clamp(20px, 2.5vw, 28px)` | 800 | `-0.6px` |
| Body | `16px` | 400 | `0` |
| Small body | `13–14px` | 400–500 | `0` |
| Label/eyebrow | `10–11px` | 800 | `2–3.5px` |

**Rule:** Labels are ALWAYS uppercase with wide letter-spacing. Body text always `line-height: 1.7–1.8`. Headings always `line-height: 1.0–1.2`.

### Spacing Scale
Use multiples of 8px: `8, 16, 24, 32, 40, 48, 64, 80, 96, 120`.

Section padding: `120px 0` on desktop, `72px 0` on mobile.
Container max-width: `1200px`, padding: `0 48px` (desktop), `0 24px` (mobile).

---

## Homepage Architecture

### Section Order (never change this sequence)
1. **Navigation** — sticky, blur-on-scroll
2. **Hero** — full viewport, name + title + description + CTAs
3. **Stats Strip** — 4 key metrics from resume, counter animation
4. **Marquee Ticker** — scrolling skill labels
5. **Work / Case Studies** — 2-col image cards
6. **About** — bento grid (philosophy + skills + education)
7. **Experience** — timeline
8. **Contact** — 2-col with contact links
9. **Footer**

### Navigation Pattern

```css
nav {
    position: fixed; top: 0; left: 0; right: 0;
    z-index: 100;
    height: 64px;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 48px;
    transition: background .3s ease, border-color .3s ease;
    border-bottom: 1px solid transparent;
}
nav.on {
    background: rgba(8,8,8,.88);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
    border-bottom-color: var(--border);
}
```

Activate `.on` class on scroll:
```javascript
window.addEventListener('scroll', () => {
    nav.classList.toggle('on', window.scrollY > 50);
}, { passive: true });
```

CTA button in nav: yellow background (`var(--yellow)`), black text, `border-radius: 100px`, `padding: 8px 20px`.

### Hero Pattern

The hero has three layers:
1. **`hero-bg`** — radial gradient glow (yellow tint, very subtle, ~5% opacity)
2. **`hero-grid`** — CSS background-image grid lines, masked with radial gradient to fade at edges
3. **`hero-content`** — z-index 1, the actual text

```css
.hero-bg {
    position: absolute; inset: 0; pointer-events: none;
    background:
        radial-gradient(ellipse 90% 70% at 75% 15%, rgba(255,221,0,0.05) 0%, transparent 55%),
        radial-gradient(ellipse 50% 50% at 10% 85%, rgba(255,221,0,0.025) 0%, transparent 55%);
}
.hero-grid {
    position: absolute; inset: 0; pointer-events: none;
    background-image:
        linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px);
    background-size: 72px 72px;
    -webkit-mask-image: radial-gradient(ellipse at center, black 20%, transparent 75%);
    mask-image: radial-gradient(ellipse at center, black 20%, transparent 75%);
}
```

**Outline text effect** on surname: use `color: transparent` + `-webkit-text-stroke`.

```css
.hero-name em {
    font-style: normal;
    color: transparent;
    -webkit-text-stroke: 1.5px rgba(255,255,255,0.2);
}
```

**Hero load animations** — stagger three elements using `animation: slideUp X var(--ease-out) Ys both`:
- Eyebrow: delay `0.15s`
- Name: delay `0.3s`
- Footer row (desc + CTAs): delay `0.45s`

### Stats Strip

4-column grid, separated by `border-right: 1px solid var(--border)`. Numbers in `var(--yellow)`, animated with counter JS on scroll.

### Marquee Ticker

Insert between stats strip and work section. Duplicate items for seamless loop.

```css
.mq-track {
    display: flex; align-items: center; gap: 48px;
    width: max-content;
    animation: marquee 35s linear infinite;
    font-size: 10px; font-weight: 800; text-transform: uppercase; letter-spacing: 2.5px;
    color: var(--text-3);
}
.mq-wrap:hover .mq-track { animation-play-state: paused; }
@keyframes marquee {
    from { transform: translateX(0); }
    to   { transform: translateX(-50%); }
}
```

Items: skill names separated by `●` (bullet, `color: var(--yellow)`). Always duplicate the full set so the loop is seamless.

### Work Cards

2-column grid per card: left = content, right = screenshot image.

```css
.work-card {
    display: grid; grid-template-columns: 1fr 1fr;
    min-height: 380px;
    background: var(--surface-1);
    border-radius: var(--radius-lg);
    overflow: hidden;
    text-decoration: none; color: inherit;
    transition: background .3s ease;
}
.work-card:hover { background: var(--surface-2); }
```

Arrow icon (`→`) in a circle at bottom-right of content area. On hover: `transform: translate(5px, -5px)` + yellow colour.
Screenshot image: `opacity: 0.65` default, rises to `0.9` + `scale(1.03)` on hover.

**Card tilt effect** (JS — desktop only):
```javascript
card.addEventListener('mousemove', function(e) {
    const r = this.getBoundingClientRect();
    const x = (e.clientX - r.left) / r.width  - 0.5;
    const y = (e.clientY - r.top)  / r.height - 0.5;
    this.style.transform = `perspective(1200px) rotateX(${y * -5}deg) rotateY(${x * 5}deg) scale(1.005)`;
});
card.addEventListener('mouseleave', function() {
    this.style.transform = '';
    this.style.transition = 'background .3s ease, transform .5s cubic-bezier(.16,1,.3,1)';
});
```

### About Bento Grid

3-column CSS grid, `gap: 2px`. Cards: `background: var(--surface-2)`, `border-radius: var(--radius-md)`, `padding: 40px`.

Key bento cells:
- **Wide card** (`grid-column: span 2`) — philosophy/description, longest text
- **Gold card** (`background: var(--yellow); color: #000`) — current role highlight
- **Big number card** — team size, `font-size: 88px`, `color: var(--yellow)`
- **Skills card** — flex-wrap chips
- **Education card**

Skills use two chip variants:
```css
.chip    { background: rgba(255,255,255,0.04); border: 1px solid var(--border); color: var(--text-2); }
.chip--y { background: rgba(255,221,0,0.07); border-color: rgba(255,221,0,0.2); color: var(--yellow); }
```

### Experience Timeline

Each item is a 2-column grid (`220px 1fr`). Company name is yellow, uppercase, tiny letter-spacing. Role is large bold. Date is `var(--text-3)`. Description max-width `600px`.

### Contact Section

2-column grid. Left: large outlined heading + subtext. Right: vertical stack of contact link cards.

Contact link card pattern:
```css
.cl {
    display: flex; align-items: center; justify-content: space-between;
    padding: 22px 26px;
    border: 1px solid var(--border);
    border-radius: var(--radius-md);
    transition: border-color .2s, background .2s;
}
.cl:hover { border-color: rgba(255,221,0,.3); background: var(--yellow-dim); }
.cl:hover .cl-arrow { color: var(--yellow); transform: translate(4px,-4px); }
```

---

## Interaction System

### Custom Cursor (desktop only)

Two elements: a 5px yellow dot (instant follow) and a 32px ring with `border: 1px solid rgba(255,221,0,.35)` (lagged follow).

```javascript
// Ring follows with lerp
(function tickRing() {
    rx += (mx - rx) * 0.11;
    ry += (my - ry) * 0.11;
    ring.style.left = rx + 'px';
    ring.style.top  = ry + 'px';
    requestAnimationFrame(tickRing);
})();

// Hover state
document.addEventListener('mouseover', e => {
    if (e.target.closest('a,button,[role="button"]')) ring.classList.add('hover');
});
document.addEventListener('mouseout', e => {
    if (e.target.closest('a,button,[role="button"]')) ring.classList.remove('hover');
});
```

`ring.hover`: expand to `52px`, brighter border, subtle yellow background tint.

**Always** disable cursor on mobile:
```css
@media (max-width: 960px) {
    body { cursor: auto; }
    #c-dot, #c-ring { display: none; }
}
```

### Scroll Reveal Animations

Every content element below the fold gets class `.r`. IntersectionObserver adds `.in` when ~8% visible.

```css
.r {
    opacity: 0;
    transform: translateY(28px);
    transition: opacity .75s cubic-bezier(0.16, 1, 0.3, 1),
                transform .75s cubic-bezier(0.16, 1, 0.3, 1);
}
.r.in { opacity: 1; transform: translateY(0); }
/* Stagger delays */
.r-d1 { transition-delay: .08s; }
.r-d2 { transition-delay: .16s; }
.r-d3 { transition-delay: .24s; }
.r-d4 { transition-delay: .32s; }
```

```javascript
const obs = new IntersectionObserver(entries => {
    entries.forEach(e => {
        if (e.isIntersecting) { e.target.classList.add('in'); obs.unobserve(e.target); }
    });
}, { threshold: 0.08, rootMargin: '0px 0px -40px 0px' });
document.querySelectorAll('.r').forEach(el => obs.observe(el));
```

### Counter Animation (stats)

Add `data-to`, `data-prefix`, `data-suffix` to the number element.

```javascript
function runCounter(el) {
    const target = parseInt(el.dataset.to, 10);
    const prefix = el.dataset.prefix || '';
    const suffix = el.dataset.suffix || '';
    const dur = 1100;
    const start = performance.now();
    (function tick(now) {
        const p = Math.min((now - start) / dur, 1);
        const v = Math.round((1 - Math.pow(1 - p, 3)) * target);
        el.textContent = prefix + v + suffix;
        if (p < 1) requestAnimationFrame(tick);
    })(start);
}
// Trigger on intersection (threshold 0.6)
```

### Hero Parallax

On scroll: hero content rises at 0.22× scroll speed.
On mouse: grid and bg glow shift at different speeds based on cursor position within the hero.

```javascript
window.addEventListener('scroll', () => {
    const y = window.scrollY;
    if (y < window.innerHeight * 1.4) {
        heroContent.style.transform = `translateY(${y * 0.22}px)`;
    }
}, { passive: true });

heroSection.addEventListener('mousemove', e => {
    const rect = heroSection.getBoundingClientRect();
    const xRel = (e.clientX - rect.left) / rect.width  - 0.5;
    const yRel = (e.clientY - rect.top)  / rect.height - 0.5;
    heroGrid.style.transform = `translate(${xRel*24}px, ${yRel*16}px)`;
    heroBg.style.transform   = `translate(${xRel*12}px, ${yRel*8}px)`;
});
heroSection.addEventListener('mouseleave', () => {
    heroGrid.style.transform = '';
    heroBg.style.transform   = '';
});
```

---

## Case Study Page Architecture

### Page Structure (always in this order)

1. **Cover / Hero** — full dark cover with title, subtitle, project meta (company, platform, year)
2. **My Role bar** — dark strip: Role · Timeline · Scope · Contribution (4-column grid)
3. **Leadership Summary** — compact view shown by default (see below)
4. **Full Case Study wrapper** (`#full-cs`) — hidden by default, expanded on toggle
5. **Showcase image** — full-width section with a key screenshot
6. **Numbered sections** (01, 02, 03…) — The Challenge, Strategy, Evidence, Quality, Outcomes, etc.
7. **Footer**
8. **Case navigation bar** — fixed bottom, prev/next between case studies
9. **Progress bar** — fixed top, reading progress
10. **Section navigation dots** — fixed right side

### Leadership Summary Pattern

This is the most important innovation in the case study pattern. Show only this by default; full detail is available on demand.

```html
<section class="lv">
    <div class="lv-inner">
        <div class="lv-hd">
            <div class="lv-badge">⚡ Leadership Summary</div>
            <div class="lv-subtitle">The strategic view — key decisions, contribution & outcomes</div>
        </div>
        <!-- 2-col grid: Problem | My Role -->
        <div class="lv-grid">
            <div class="lv-cell">
                <div class="lv-cell-lbl">The Problem</div>
                <div class="lv-cell-title"><!-- One sharp sentence --></div>
                <p class="lv-cell-body"><!-- 2–3 sentences max --></p>
            </div>
            <div class="lv-cell">
                <div class="lv-cell-lbl">My Role & Contribution</div>
                <div class="lv-cell-title"><!-- Title — duration, ownership scope --></div>
                <p class="lv-cell-body"><!-- What you owned, who you partnered with --></p>
            </div>
        </div>
        <!-- Full-width cell: 3 key decisions -->
        <div class="lv-cell" style="border-radius:16px; margin-top:2px;">
            <div class="lv-cell-lbl">Three Key Design Decisions</div>
            <div class="lv-decisions">
                <div class="lv-d"><div class="lv-d-n">1</div><div class="lv-d-t"><strong>Decision name:</strong> Why it mattered, what changed.</div></div>
                <div class="lv-d"><div class="lv-d-n">2</div><div class="lv-d-t"><strong>Decision name:</strong> Why it mattered, what changed.</div></div>
                <div class="lv-d"><div class="lv-d-n">3</div><div class="lv-d-t"><strong>Decision name:</strong> Why it mattered, what changed.</div></div>
            </div>
        </div>
        <!-- 4-col outcomes metrics row -->
        <div class="lv-metrics">
            <div class="lv-m"><div class="lv-m-n">+34%</div><div class="lv-m-l">Completion rate</div></div>
            <!-- repeat x4 -->
        </div>
        <button class="lv-toggle" id="lv-toggle" onclick="toggleFull()">
            <span id="lv-btn-txt">Read Full Case Study</span>
            <span class="lv-toggle-ic">↓</span>
        </button>
    </div>
</section>
<div id="full-cs">
    <!-- all detailed sections here -->
</div>
```

**Content rules for leadership summary:**
- The Problem: name the specific business/user failure, with a metric if possible ("43% abandonment at amount entry")
- My Role: be specific about ownership ("sole design decision-maker", "14 weeks", "iOS/Android/web")
- Decisions: each starts with **bold decision name**, then explains *why* this was the right call, not just what it was
- Outcomes: exactly 4 metrics, use real numbers from the project

### Full Case Study Toggle JS

```javascript
window.toggleFull = function() {
    var fc  = document.getElementById('full-cs');
    var btn = document.getElementById('lv-toggle');
    var txt = document.getElementById('lv-btn-txt');
    var isOpen = fc.classList.toggle('open');
    btn.classList.toggle('open', isOpen);
    txt.textContent = isOpen ? 'Collapse Case Study' : 'Read Full Case Study';
    if (isOpen) { setTimeout(() => fc.scrollIntoView({behavior:'smooth', block:'start'}), 50); }
    updateNavVis(isOpen);
};
```

CSS:
```css
#full-cs { display: none; }
#full-cs.open { display: block; }
.lv-toggle-ic { transition: transform .3s ease; display: inline-block; }
.lv-toggle.open .lv-toggle-ic { transform: rotate(180deg); }
```

### My Role Bar (dark version)

```css
/* Always dark — never light background */
background: #0f0f0f;
border-bottom: 1px solid rgba(255,255,255,0.07);
padding: 36px 48px;
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 48px;
```

Labels: `font-size: 10px; text-transform: uppercase; letter-spacing: 3px; color: rgba(255,255,255,0.25)`.
Values: `font-size: 15px; font-weight: 700; color: #fff`.

### Section Navigation Dots

Fixed right-side vertical nav. Auto-built from JS scanning `.section-number` (send-money-imt) or `.section-eyebrow` (ux-baseline) elements.

```css
.csn {
    position: fixed; right: 28px; top: 50%;
    transform: translateY(-50%);
    display: flex; flex-direction: column; gap: 10px;
    z-index: 100; align-items: flex-end;
}
.csn-lbl {
    font-size: 10px; font-weight: 700; text-transform: uppercase;
    letter-spacing: 1.5px; color: rgba(255,255,255,.22);
    opacity: 0; transform: translateX(8px);
    transition: opacity .2s, transform .2s, color .2s;
    white-space: nowrap;
}
.csn-dot {
    width: 5px; height: 5px; border-radius: 3px;
    background: rgba(255,255,255,.15);
    transition: all .28s cubic-bezier(.16,1,.3,1);
}
.csn:hover .csn-lbl { opacity: 1; transform: translateX(0); }
.csn-item.active .csn-dot { background: #FFDD00; height: 14px; box-shadow: 0 0 6px rgba(255,221,0,.5); }
.csn-item.active .csn-lbl { opacity: 1; transform: translateX(0); color: #FFDD00; }
@media(max-width:1100px) { .csn { display: none; } }
```

JS that auto-builds the nav:
```javascript
function buildNav() {
    var csn = document.getElementById('csn');
    var markers = document.querySelectorAll('.section-number'); // or .section-eyebrow
    var navSecs = [];
    var idx = 0;
    markers.forEach(function(m) {
        var sec = m.closest('section');
        if (!sec) return;
        var id = 'csn-' + idx++;
        sec.setAttribute('data-csn', id);
        var label = m.textContent.trim().replace(/^\d+\s*[—\-]\s*/, '').trim();
        var inFull = !!sec.closest('#full-cs');
        navSecs.push({ id, label, sec, inFull });
    });
    navSecs.forEach(function(ns) {
        var a = document.createElement('a');
        a.className = 'csn-item' + (ns.inFull ? ' cs-full' : '');
        a.setAttribute('data-csn-id', ns.id);
        a.href = 'javascript:void(0)';
        a.innerHTML = '<span class="csn-lbl">' + ns.label + '</span><span class="csn-dot"></span>';
        if (ns.inFull) a.style.display = 'none';
        a.addEventListener('click', () => ns.sec.scrollIntoView({behavior:'smooth',block:'start'}));
        csn.appendChild(a);
    });
    // IntersectionObserver tracks active section
    var obs = new IntersectionObserver(function(entries) {
        entries.forEach(function(e) {
            if (e.isIntersecting) {
                var id = e.target.getAttribute('data-csn');
                document.querySelectorAll('.csn-item').forEach(function(item) {
                    item.classList.toggle('active', item.getAttribute('data-csn-id') === id);
                });
            }
        });
    }, { threshold: 0.25, rootMargin: '-10% 0px -65% 0px' });
    navSecs.forEach(ns => obs.observe(ns.sec));
}
function updateNavVis(isOpen) {
    document.querySelectorAll('.csn-item.cs-full').forEach(item => {
        item.style.display = isOpen ? '' : 'none';
    });
}
buildNav();
```

### Reading Progress Bar

```css
#cs-pb {
    position: fixed; top: 0; left: 0; height: 2px;
    background: #FFDD00; z-index: 600; width: 0;
    transition: width .08s linear;
    box-shadow: 0 0 8px rgba(255,221,0,.5);
}
```

```javascript
var pb = document.getElementById('cs-pb');
window.addEventListener('scroll', function() {
    var pct = window.scrollY / (document.documentElement.scrollHeight - window.innerHeight) * 100;
    if (pb) pb.style.width = Math.min(pct, 100) + '%';
}, { passive: true });
```

### Case Navigation Bar (Next / Previous)

Fixed at bottom. Always visible. On first case study: show `← Portfolio` · `1 of N` · `Next Case →`. On last: `← Prev Case` · `N of N` · `Portfolio →`.

```css
.cs-nav {
    position: fixed; bottom: 0; left: 0; right: 0; z-index: 200;
    background: rgba(8,8,8,.93);
    backdrop-filter: blur(24px); -webkit-backdrop-filter: blur(24px);
    border-top: 1px solid rgba(255,255,255,.07);
    height: 60px; display: flex; align-items: center;
    padding: 0 48px; justify-content: space-between;
}
.cs-nav a { font-size: 12px; font-weight: 600; color: rgba(255,255,255,.4); text-decoration: none; display: flex; align-items: center; gap: 8px; transition: color .2s; }
.cs-nav a:hover { color: #FFDD00; }
.cs-nav-mid { font-size: 10px; font-weight: 700; text-transform: uppercase; letter-spacing: 2.5px; color: rgba(255,255,255,.18); }
```

**Always** add `body { padding-bottom: 60px; }` to prevent content being hidden by the fixed bar.

---

## Dark Theme Strategy for Existing Light-Theme Case Studies

When converting a light-theme case study to dark, never rewrite the entire CSS. Instead, add a targeted override block at the END of the existing `<style>` tag:

```css
/* ─── DARK MODE OVERRIDES ─── */
body { background: #080808; color: rgba(255,255,255,.88); }

/* Cards */
.challenge-card, .outcome-card, .value-card, .roadmap-phase {
    background: #141414;
    border-color: rgba(255,255,255,.08);
}
/* Headings inside light cards */
.challenge-card h3, .outcome-label, .principle-title,
.timeline-title, .roadmap-phase-title { color: #fff; }
/* Body text inside light cards */
.challenge-card p, .principle-desc, .timeline-desc,
.outcome-desc, .roadmap-phase-items li { color: rgba(255,255,255,.45); }

/* Grids and borders */
.principles-grid, .principle-item { border-color: rgba(255,255,255,.07); }
.principle-number { color: rgba(255,255,255,.07); }
.timeline::before { background: rgba(255,255,255,.1); }
.timeline-item { border-color: rgba(255,255,255,.05); }
/* Timeline bullet border must match the dark body background */
.timeline-item::before { border-color: #080808; }

/* Architecture diagrams */
.arch-diagram { background: #141414; border-color: rgba(255,255,255,.08); }
.arch-node { background: #1e1e1e; border-color: rgba(255,255,255,.1); }
.arch-node-label { color: rgba(255,255,255,.3); }

/* Section text */
.section-title { color: #fff; }
.section-subtitle, .section-lead { color: rgba(255,255,255,.45); }

/* Comparison tables */
.comparison-row { border-color: rgba(255,255,255,.07); }
.comparison-row--header { background: #161616; }
.comparison-cell--bad  { background: rgba(229,57,53,.08); color: rgba(229,57,53,.8); }
.comparison-cell--good { background: rgba(0,182,122,.08); color: rgba(0,182,122,.85); }

/* Light-background sections */
.section { background: #080808; }
.section--light, .section-accent { background: #0d0d0d; }
```

**Key principle:** Always override `border-color` of timeline bullets to match the new dark body background (they use `border: 3px solid var(--wu-white)` to create a gap effect).

---

## Content Strategy for Case Studies

### The 8-Section Template

| # | Section Name | What to Include |
|---|--------------|-----------------|
| 01 | The Challenge / Problem | 3–6 problem cards with specific statistics. Use real data: "43% drop-off at amount entry", not "users struggled with complexity" |
| 02 | Definition / Context | What does the solution category mean? Why does it matter at org scale? |
| 03 | Strategy | Org-level rationale. Why this approach over alternatives. Governance model. |
| 04 | Evidence / The Work | Visual evidence: screenshots, flows, validated patterns |
| 05 | Quality Framework | Non-negotiable standards. Prioritised (Critical → High → Medium). Specific numbers. |
| 06 | Business Impact | Quantified cost of the problem, not just the solution |
| 07 | Comparison | With/without baseline or before/after table |
| 08 | Outcomes | Results with exact metrics, framed as business outcomes not design outputs |
| 09 | Roadmap | Phased implementation (Audit → Define → Build → Embed) |
| 10 | Recommendation | One-sentence closing statement. CTA to contact or other work. |

### Leadership Summary Content Rules

The **problem** must name a specific failure with a metric. Bad: "The experience was complex." Good: "43% of users who entered an amount never completed the transfer."

The **role** must specify: title, duration, who you reported to or partnered with, what you personally owned vs. what others did. Bad: "Led UX design." Good: "UX Lead — 14 weeks, sole design decision-maker on the full flow, partnered with compliance and engineering."

**Key decisions** follow this format:
> **[Decision name]:** [What you decided], because [why this was the right call over alternatives].

**Outcomes** must be business metrics, not design metrics. Bad: "Improved the design." Good: "+34% completion rate (41% → 55%)". Always show direction (+ or −) and the comparison point if available.

---

## File Structure

```
portfolio-root/
├── index.html                    ← Homepage (portfolio landing)
├── send-money-imt-case-study.html ← Case study 1
├── ux-baseline-case-study.html   ← Case study 2
├── case-study-assets/            ← Screenshots, images
│   ├── 01-hero-send-money-imt.png
│   ├── 03-payments-hub.png
│   └── ...
├── .nojekyll                     ← Needed for GitHub Pages
└── .github/
    └── workflows/                ← Optional: GitHub Actions
```

### GitHub Pages Deployment

1. Create a public GitHub repository
2. Add `.nojekyll` file (empty file, prevents Jekyll processing)
3. Push all files to `main` branch
4. In repo settings → Pages → Source: Deploy from branch `main` / `root`
5. Site is live at `https://[username].github.io/[repo-name]/`

**Always test locally first:**
```bash
# Simple local server (Python)
python3 -m http.server 3000
# Then open http://localhost:3000
```

---

## Responsive Breakpoints

| Breakpoint | Changes |
|------------|---------|
| `960px` | Nav padding reduces. Hero padding reduces. Stats go 2×2. Work cards stack. Bento goes 2-col. Timeline single-col. Contact single-col. **Cursor disabled.** |
| `600px` | Bento goes single-col. Nav links hidden (only CTA remains). |
| `1100px` | Section nav dots hidden (not enough space). |

Always disable custom cursor on mobile:
```css
@media (max-width: 960px) {
    body { cursor: auto; }
    #c-dot, #c-ring { display: none; }
}
```

---

## Common Mistakes to Avoid

| Mistake | Fix |
|---------|-----|
| White text on white background | Always check that section background is dark before using `color: rgba(255,255,255,...)`. The My Role bar and Leadership Summary both need dark backgrounds. |
| Full case study visible on load | `#full-cs { display: none; }` must be in CSS. The toggle button must call `toggleFull()`. |
| Timeline bullet dots blending in | `timeline-item::before { border-color: <dark-bg-color>; }` — the border creates the gap effect and must match the body background. |
| Section nav not showing up | Check selector — `send-money-imt` uses `.section-number`, `ux-baseline` uses `.section-eyebrow`. Make sure `m.closest('section')` returns something. |
| Marquee not looping seamlessly | You must duplicate the full list of items in HTML so the track width is 2× the visible set. The `translateX(-50%)` animation moves exactly one set. |
| Parallax fighting scroll on mobile | Guard with `if (y < window.innerHeight * 1.4)` and disable entirely on touch devices. |
| Case nav hiding page content | Add `body { padding-bottom: 60px; }` to account for the fixed 60px nav bar. |
| Progress bar not reaching 100% | Use `Math.min(pct, 100)` in the calculation. |
| Counter animation flickering | Trigger via IntersectionObserver at `threshold: 0.6`, not on `DOMContentLoaded`. |

---

## Adding a New Case Study

1. Duplicate an existing case study HTML file
2. Update the `<title>` and all section content
3. Update the Case Nav bar: change `href`, title label, and "X of N" counter
4. Add the new page to `index.html` work section (new `.work-card`)
5. Update the other case study pages' Case Nav to include the new entry
6. Add screenshots to `case-study-assets/`
7. Test the section nav by opening the page and checking that `.section-number` or `.section-eyebrow` elements exist in every section

---

## Quick Reference: The Leadership Summary for Any Project

Fill in this template from the project brief/resume:

```
THE PROBLEM:
What specifically failed? (name a metric if possible)
Who was affected and how?
What was the business cost?

MY ROLE:
Title: [exact role title]
Duration: [N weeks/months]
Ownership: [what I personally owned — be specific]
Partners: [who I collaborated with — Product, Eng, Compliance, etc.]
Platforms: [iOS / Android / Web / etc.]

THREE KEY DECISIONS:
1. [Decision name]: [What I chose + why it was right over the alternative]
2. [Decision name]: [What I chose + why it was right over the alternative]
3. [Decision name]: [What I chose + why it was right over the alternative]

OUTCOMES (4 metrics):
1. [Metric with direction and comparison: "+34% completion rate (41% → 55%)"]
2. [Metric with direction]
3. [Metric with direction]
4. [Metric with direction]
```
