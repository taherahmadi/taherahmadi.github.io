# Design System Master File

> **LOGIC:** When building a specific page, first check `design-system/pages/[page-name].md`.
> If that file exists, its rules **override** this Master file.
> If not, strictly follow the rules below.

---

**Project:** Taher Ahmadi
**Generated:** 2026-08-27 23:52:09
**Category:** Developer Tool / IDE
**Design Dials:** Variance 4/10 (Balanced / Modern) | Motion 3/10 (Subtle) | Density 4/10 (Standard)

---

## Global Rules

### Color Palette

| Role | Hex | CSS Variable |
|------|-----|--------------|
| Primary | `#1E293B` | `--color-primary` |
| On Primary | `#FFFFFF` | `--color-on-primary` |
| Secondary | `#334155` | `--color-secondary` |
| On Secondary | `#FFFFFF` | `--color-on-secondary` |
| Accent/CTA | `#22C55E` | `--color-accent` |
| On Accent/CTA | `#0F172A` | `--color-on-accent` |
| Background | `#0F172A` | `--color-background` |
| Foreground | `#F8FAFC` | `--color-foreground` |
| Card | `#1B2336` | `--color-card` |
| Card Foreground | `#F8FAFC` | `--color-card-foreground` |
| Muted | `#272F42` | `--color-muted` |
| Muted Foreground | `#94A3B8` | `--color-muted-foreground` |
| Border | `#475569` | `--color-border` |
| Destructive | `#EF4444` | `--color-destructive` |
| On Destructive | `#000000` | `--color-on-destructive` |
| Ring | `#FFFFFF` | `--color-ring` |

**Color Notes:** Code dark + run green

### Typography

- **Heading Font:** JetBrains Mono
- **Body Font:** IBM Plex Sans
- **Mood:** code, developer, technical, precise, functional, hacker
- **Google Fonts:** [JetBrains Mono + IBM Plex Sans](https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;600;700&display=swap)

**CSS Import:**
```css
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;600;700&display=swap');
```

### Spacing Variables

*Density: 4/10 — Standard*

| Token | Value | Usage |
|-------|-------|-------|
| `--space-xs` | `4px` / `0.25rem` | Tight gaps |
| `--space-sm` | `8px` / `0.5rem` | Icon gaps, inline spacing |
| `--space-md` | `16px` / `1rem` | Standard padding |
| `--space-lg` | `24px` / `1.5rem` | Section padding |
| `--space-xl` | `32px` / `2rem` | Large gaps |
| `--space-2xl` | `48px` / `3rem` | Section margins |
| `--space-3xl` | `64px` / `4rem` | Hero padding |

### Shadow Depths

| Level | Value | Usage |
|-------|-------|-------|
| `--shadow-sm` | `0 1px 2px rgba(0,0,0,0.05)` | Subtle lift |
| `--shadow-md` | `0 4px 6px rgba(0,0,0,0.1)` | Cards, buttons |
| `--shadow-lg` | `0 10px 15px rgba(0,0,0,0.1)` | Modals, dropdowns |
| `--shadow-xl` | `0 20px 25px rgba(0,0,0,0.15)` | Hero images, featured cards |

---

## Component Specs

### Buttons

```css
/* Primary Button */
.btn-primary {
  background: #22C55E;
  color: white;
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 600;
  transition: all 200ms ease;
  cursor: pointer;
}

.btn-primary:hover {
  opacity: 0.9;
  transform: translateY(-1px);
}

/* Secondary Button */
.btn-secondary {
  background: transparent;
  color: #1E293B;
  border: 2px solid #1E293B;
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 600;
  transition: all 200ms ease;
  cursor: pointer;
}
```

### Cards

```css
.card {
  background: #0F172A;
  border-radius: 12px;
  padding: 24px;
  box-shadow: var(--shadow-md);
  transition: all 200ms ease;
  cursor: pointer;
}

.card:hover {
  box-shadow: var(--shadow-lg);
  transform: translateY(-2px);
}
```

### Inputs

```css
.input {
  padding: 12px 16px;
  border: 1px solid #E2E8F0;
  border-radius: 8px;
  font-size: 16px;
  transition: border-color 200ms ease;
}

.input:focus {
  border-color: #1E293B;
  outline: none;
  box-shadow: 0 0 0 3px #1E293B20;
}
```

### Modals

```css
.modal-overlay {
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(4px);
}

.modal {
  background: white;
  border-radius: 16px;
  padding: 32px;
  box-shadow: var(--shadow-xl);
  max-width: 500px;
  width: 90%;
}
```

---

## Style Guidelines

**Style:** Dark Mode (OLED)

**Keywords:** Dark theme, low light, high contrast, deep black, midnight blue, eye-friendly, OLED, night mode, power efficient

**Best For:** Night-mode apps, coding platforms, entertainment, eye-strain prevention, OLED devices, low-light

**Key Effects:** Minimal glow (text-shadow: 0 0 10px), dark-to-light transitions, low white emission, high readability, visible focus

### Page Pattern

**Pattern Name:** FAQ/Documentation Landing

- **Conversion Strategy:** Reduce support tickets. Track search analytics. Show related articles. Contact escalation path.
- **CTA Placement:** Search bar prominent + Contact CTA for unresolved questions
- **Section Order:** Hero with search bar > Popular categories > FAQ accordion > Contact/support CTA

---

## Motion

**Scroll Reveal** (Subtle) — Trigger: scroll (viewport enter) | Duration: 300-400ms | Easing: `power1.out`

```js
gsap.from(el, { opacity: 0, y: 12, duration: 0.35, ease: 'power1.out', scrollTrigger: { trigger: el, start: 'top 90%', toggleActions: 'play none none reverse' } });
```

**Framework notes:** Requires the ScrollTrigger plugin registered once via gsap.registerPlugin(ScrollTrigger); Use matchMedia('(prefers-reduced-motion: reduce)') to skip non-essential motion and render the final state immediately

- ✅ Keep the y offset small (8-16px) so it reads as a fade, not a slide
- ❌ Don't reveal below-the-fold content needed for SEO/crawlers as invisible-by-default without a no-JS fallback
- ⚡ toggleActions 'play none none reverse' avoids re-triggering on every scroll direction change

---

## Anti-Patterns (Do NOT Use)

- ❌ Light mode default
- ❌ Slow performance

### Additional Forbidden Patterns

- ❌ **Emojis as icons** — Use SVG icons (Heroicons, Lucide, Simple Icons)
- ❌ **Missing cursor:pointer** — All clickable elements must have cursor:pointer
- ❌ **Layout-shifting hovers** — Avoid scale transforms that shift layout
- ❌ **Low contrast text** — Maintain 4.5:1 minimum contrast ratio
- ❌ **Instant state changes** — Always use transitions (150-300ms)
- ❌ **Invisible focus states** — Focus states must be visible for a11y

---

## Pre-Delivery Checklist

Before delivering any UI code, verify:

- [ ] No emojis used as icons (use SVG instead)
- [ ] All icons from consistent icon set (Heroicons/Lucide)
- [ ] `cursor-pointer` on all clickable elements
- [ ] Hover states with smooth transitions (150-300ms)
- [ ] Light mode: text contrast 4.5:1 minimum
- [ ] Focus states visible for keyboard navigation
- [ ] `prefers-reduced-motion` respected
- [ ] Responsive: 375px, 768px, 1024px, 1440px
- [ ] No content hidden behind fixed navbars
- [ ] No horizontal scroll on mobile

---

## Pattern Override (verified from landing domain)

The generator's auto-selected "FAQ/Documentation Landing" pattern was rejected as off-topic for a personal portfolio. Using the verified `portfolio-grid` result instead:

- **Name:** Portfolio Grid (Hero-Centric)
- **Section Order:** Hero (Name/Role) > Credentials strip > About > Experience > Publications > Project Grid > Skills > Awards > Education > Contact
- **CTA Placement:** Hero (resume download + contact) + footer contact
- **Color Strategy:** Neutral dark background, let content shine, single green accent used sparingly.

## Project Notes

- Light mode kept as a supported toggle (existing site behavior); light tokens derived from the same palette with AA contrast (accent text on light backgrounds uses green-700 #15803D).
- No em dashes in any copy (owner style rule).
- Motion dial 3/10: reveal and hover micro-interactions only, full reduced-motion support.

## Craft Pass (awesome-ux-skills)

Applied `craft` (12 rules), `cognitive-load-conversion`, and `dieter-rams-principles` from the awesome-ux-skills collection:
- One primary CTA per decision point (hero reduced to Download CV + Get in touch)
- Featured emphasis: ICRA 2023 publication (left accent bar, larger type), first project card spans 2 columns
- Alternating section backgrounds (publications, awards on sunken band) to break monotony
- Spacing normalized to the 4px scale; tabular-nums on stat and date figures
- Elevation language is borders only (portrait shadow removed); designed :active states
- Motion tightened to 400-550ms ease-out entrances; no gradients (dot texture only), no glow, no transition:all

## v4 Direction Change: Editorial Monograph

The IDE-dark direction was replaced at the owner's request for a structurally different design (the previous three iterations shared one skeleton). Current system:

- **Layout:** sticky sidebar index (numbered sections, scroll-spy) + single flowing content column; ruled sections instead of card grids
- **Typography:** Fraunces (display serif, optical sizing) + Inter (text); system mono for metadata labels only
- **Palette:** warm paper light default `#F6F4EE` / ink `#211D16` / oxblood accent `#8A3324`; warm dark mode `#191510` / terracotta accent `#D98E6B`
- **Component language:** reference-list publications ([1][2][3], venue in italics, featured entry tinted with left rule), figure plates with Fig. numbers for projects, definition-list skills, ledger-style awards
- **Craft rules carried over:** no gradients, no glow, named transitions at 150-350ms ease-out, 4px spacing rhythm, tabular-nums, designed hover/focus/active states, reduced-motion support, no em dashes

## v5 Direction: Minimal Single Column (current)

Owner asked for a more minimal design with no projects on the first page.

- **Homepage:** one 620px column: name, three-paragraph bio, compact ruled entries for experience, publications (reference lines with citation counts), awards ledger, education, footer links. No hero, no stats row, no images except none.
- **Projects:** moved to `projects.html` (thumbnail + text rows, same language), linked from the bio and footer; old Pelican archive still at pages/research-projects.html.
- **Type:** Inter only; system mono for labels/dates. **Color:** near-monochrome, warm off-white `#FCFCFA` / ink `#1C1C1A`, underlined links, no accent color. Dark: `#151514` / `#E9E9E4`.
- Theme toggle is a small text link in the footer; preference shared across pages via localStorage.

## v6 Direction: Minimal + Kinetic (current)

Owner feedback on v5: too static; wants clean and smooth with mesmerizing yet lightweight animation, minimal information, broader intro (not only determinism).

- **Hero:** full-viewport canvas flow field: particle trajectories drifting through a layered-sine vector field (a nod to motion-prediction research). No libraries, ~520 particles, theme-aware opacity (airy pencil traces in light, glowing threads in dark), gentle pointer swirl, pauses when offscreen, static texture under reduced motion.
- **Tagline:** "Teaching machines to see, predict, and act." with the three verbs pulsing in accent on a slow 9s cycle.
- **Type:** Space Grotesk display + Inter text. **Color:** near-monochrome plus one periwinkle/cobalt accent (#3450C8 light, #8FA3FF dark).
- **Motion language:** eased staggered reveals (550-600ms), animated link underlines, floating scroll cue; full reduced-motion fallback.
- **Content:** as v5 minus awards (in CV); intro rewritten to span vision, motion prediction, robotics, and agentic AI. Projects remain on projects.html.

## v6.1 Hero Animation: Attention Stream (current)

Replaced the generic flow field with a scene about the work itself:

- Three token streams of ML-theory symbols (theta, grad-l, sigma(x), QK^T, sqrt-d, softmax, argmax, KL, logits, x_t, h_t, ...) slide left like a context window; new tokens are emitted autoregressively at the right edge and appear in accent color.
- Causal attention arcs: each new token, and a roving query among visible tokens, casts quadratic arcs back to context tokens; arc opacity plays the role of a recency-biased softmax weight, fading over ~2.4s.
- Middle lane dimmed to keep the tagline legible; lanes drift a few px toward the pointer.
- Theme-aware alphas via MutationObserver recolor; static frame under reduced motion; pauses offscreen; no libraries.

## v6.2 Hero: Story Ribbon + New Tagline (current)

- Animation now runs 5 lanes (two dimmed behind the headline) walking one cohesive story in plain words: the life of a learning machine, from data and attention through the agent loop (goal, observe, retrieve, reason, tool call, verify, reflect, memory, reward, gradient) to shipping, drift, and earning trust; ~34 beats, one cycle roughly 30s per lane, staggered offsets. Attention arcs hop between story beats.
- Tagline: "Building systems that reason, act, and earn trust." with the three key phrases pulsing in accent; display sized clamp(32px,6vw,58px) for a two-line break.
- The story's closing beats intentionally echo the tagline ("it earns trust slowly, the way good systems do").

## v6.3 Hero: Bidirectional Semantic Attention + Dominant Name (current)

- 7 lanes at random directions and speeds (13-30 px/s), two center lanes dimmed to .35 for headline legibility; lanes prefill the full width in story order on load.
- Attention model: each query token scores nearby tokens both behind and ahead; same semantic family (12 keyword groups: data, model, vectors, attention, goal/agent, see/predict/act, memory, reasoning, tools, gradients, evaluation, trust) binds strongly (+0.55..0.75), others decay exp(-gap/6). Top 2-4 become arcs.
- Rendering: backward arcs curve above the baseline, forward arcs below; color maps weight on a heat scale (faint gray-blue -> accent periwinkle -> hot orange #D9480F light / #FFA94D dark); alpha and stroke width also scale with weight.
- Hero hierarchy: name "Taher Ahmadi" dominant (Space Grotesk 600, clamp 46-92px), mono uppercase meta line, tagline stepped down to clamp 22-38px in ink-2.
