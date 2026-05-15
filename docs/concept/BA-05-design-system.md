# Bathys — Design System

## BA-05 · Design System

> v0.2 · Draft · May 2026
> Visual fidelity: Drafted from textual descriptions before
> prototypes exist. Prototype verification required before this
> document is treated as a visual contract. Token names are locked;
> hex values are starting proposals subject to revision.
> Updated: mobile-first responsive (§9), accessibility section (§10).

---

## 1. Design Philosophy

### 1.1 The guiding principle

Bathys is the ocean rendered as a place you can think in.

Not a data dashboard. Not a tourism brochure. Not a scientific
portal. A place — with depth, atmosphere, and the feeling that
what you are looking at was made by someone who has been there.

Every design decision is tested against one question: does this
feel like the ocean, or does it feel like a website about the ocean?

### 1.2 What this means in practice

**Depth is literal and visual.** The interface shifts register as
content goes deeper. Surface-zone content is warm and turquoise.
Reef content is rich blue-green. The mesopelagic is indigo. The
abyss is near-black with bioluminescent accents.

**Light behaves like water.** Caustic light patterns, soft glows,
the way colour bleeds in water. Backgrounds breathe.

**Science is primary, beauty is the delivery mechanism.** No
chart exists purely as decoration. Every illustration has
informational content. All charts and illustrations are custom
to the Bathys visual language.

**Editorial voice in the typography.** Clean, precise, slightly
literary. *National Geographic* meets *Nature* meets a beautifully
designed monograph.

**Photography is real.** The underwater images in Bathys come from
real dives. This is visible in them.

---

## 2. Colour System

### 2.1 The depth-gradient token system

Six depth registers, each a complete palette, applied at the
section level. All components inherit from the active register
via CSS custom properties. Token names are locked. Hex values
are proposals pending prototype verification.

---

**Register 0 — Surface** | Used in: page chrome, navigation, credits page.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#CAF0F8` | Main background |
| `--color-bg-secondary` | `#90E0EF` | Card and panel backgrounds |
| `--color-text-primary` | `#03045E` | Body text |
| `--color-text-secondary` | `#0077B6` | Secondary text |
| `--color-accent` | `#00B4D8` | Interactive elements |
| `--color-surface` | `rgba(255,255,255,0.15)` | Cards, panels (frosted) |
| `--glow-color` | `rgba(0,180,216,0.3)` | Glow effects |
| `--biolum-color` | `none` | Not active |

---

**Register 1 — Epipelagic (0–200m)** | Used in: Ocean Globe default, Expeditions, Dive Lab shallow.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#023E8A` | Main background |
| `--color-bg-secondary` | `#0077B6` | Card and panel backgrounds |
| `--color-text-primary` | `#CAF0F8` | Body text |
| `--color-accent` | `#00B4D8` | Interactive elements |
| `--glow-color` | `rgba(0,180,216,0.4)` | Glow effects |
| `--biolum-color` | `none` | Not active |

---

**Register 2 — Mesopelagic (200–1000m)** | Used in: Science tab, Cousteau deep content.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#03045E` | Main background |
| `--color-bg-secondary` | `#023E8A` | Cards and panels |
| `--color-text-primary` | `#CAF0F8` | Body text |
| `--color-text-secondary` | `#48CAE4` | Secondary text |
| `--color-accent` | `#48CAE4` | Interactive elements |
| `--glow-color` | `rgba(72,202,228,0.25)` | Glow effects |
| `--biolum-color` | `rgba(0,255,200,0.1)` | Subtle biolum begins |

---

**Register 3 — Bathypelagic (1000–4000m)** | Used in: deep Science, deep Dive Lab.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#010018` | Main background |
| `--color-bg-secondary` | `#03045E` | Cards and panels |
| `--color-text-primary` | `#90E0EF` | Body text |
| `--color-accent` | `#0096C7` | Interactive elements |
| `--glow-color` | `rgba(0,150,199,0.2)` | Glow effects |
| `--biolum-color` | `rgba(0,255,200,0.4)` | Bioluminescence active |

---

**Register 4 — Abyssal / Hadal (4000m+)** | Used in: deepest Science, abyssal Flora & Fauna.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#000000` | True black |
| `--color-bg-secondary` | `#010018` | Near-black panels |
| `--color-text-primary` | `#90E0EF` | Body text |
| `--color-accent` | `#0096C7` | Interactive elements |
| `--biolum-color` | `rgba(0,255,200,0.6)` | Full bioluminescence |
| `--biolum-secondary` | `rgba(100,200,255,0.4)` | Secondary biolum colour |

---

**Register 5 — Cousteau (special)** | Warmer, more analog, cinematic.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#001F3F` | Deep navy |
| `--color-bg-secondary` | `#003366` | Warmer dark blue |
| `--color-text-primary` | `#E8F4F8` | Warm off-white |
| `--color-accent` | `#FF6B35` | Cousteau red — his iconic red beanie |
| `--cousteau-red` | `#FF6B35` | Dedicated Cousteau accent |
| `--calypso-gold` | `#D4A843` | Calypso vessel colour accent |

### 2.2 Semantic tokens — cross-cutting

| Token | Purpose |
|-------|---------|
| `--color-danger` | Error states, O₂ toxicity warning in Dive Lab |
| `--color-warning` | Caution states, approaching limits |
| `--color-success` | Safe states, within limits |
| `--color-iucn-lc` | IUCN Least Concern — green |
| `--color-iucn-nt` | Near Threatened — yellow-green |
| `--color-iucn-vu` | Vulnerable — yellow |
| `--color-iucn-en` | Endangered — orange |
| `--color-iucn-cr` | Critically Endangered — red |
| `--color-iucn-ex` | Extinct — grey |

---

## 3. Typography

> Final font selection confirmed in prototype visual testing.

| Role | Font | Weight | Size (desktop) | Usage |
|------|------|--------|----------------|-------|
| Display | Inter | 200 ExtraLight | 72–96px | Hero titles |
| Headline | Inter | 300 Light | 40–56px | Tab headings |
| Title | Inter | 400 Regular | 28–36px | Card titles |
| Body Large | Inter | 400 Regular | 18–20px | Lead paragraphs |
| Body | Inter | 400 Regular | 15–16px | Standard body |
| Label | Inter | 600 SemiBold | 11–12px | ALL CAPS, wide tracking |
| Data | JetBrains Mono | 400 Regular | 14–15px | Algorithm outputs, depths, coordinates |
| Data Large | JetBrains Mono | 400 Regular | 24–32px | Feature numbers |
| Caption | Inter | 400 Regular | 12px | Image credits, footnotes |

Typographic voice rules:
- Display text is light (200–300 weight). The ocean is vast, not aggressive.
- Data is monospaced, always. Every depth reading, pressure value, tissue percentage.
- Labels are ALL CAPS with wide letter-spacing.
- Body text is ragged right, never justified.
- Line length capped at 72 characters.

---

## 4. Motion & Animation

### 4.1 Principles

- Motion is oceanographic. Things emerge from depth, not slide from edges.
- The current flows continuously. The ocean is always in motion.
- Bioluminescence is triggered on interaction in deep registers, not ambient.

### 4.2 Easing vocabulary

| Easing | Curve | Use |
|--------|-------|-----|
| Ocean ease in | `cubic-bezier(0.0, 0.0, 0.2, 1.0)` | Elements entering |
| Ocean ease out | `cubic-bezier(0.4, 0.0, 1.0, 1.0)` | Elements leaving |
| Float | `cubic-bezier(0.25, 0.46, 0.45, 0.94)` | Subtle positional shifts |
| Drift | `cubic-bezier(0.0, 0.0, 0.6, 1.0)` | Long, slow transitions |

### 4.3 Duration vocabulary

| Duration | Value | Use |
|----------|-------|-----|
| Instant | 80ms | State changes |
| Fast | 150ms | Icon transitions |
| Medium | 300ms | Card transitions, panel opens |
| Slow | 600ms | Page transitions |
| Drift | 1200ms | Depth register transitions |
| Current | continuous | Globe particle system |

### 4.4 Depth register transition

When the active depth register changes, the transition is 1200ms.
Background colour shifts slowly. Text colour crossfades. The effect
is a descent, not a page change. Accomplished via CSS custom property
transitions.

---

## 5. Illustration Style

### 5.1 Principles

All illustrations are custom to Bathys. Scientific accuracy with
editorial warmth. Dark backgrounds with internal light sources
(bioluminescence, sunlight, hydrothermal vents). Three-dimensional
depth in every composition.

### 5.2 Illustration inventory

**Tab 2 — Expeditions:** Calypso cutaway; SP-350 Denise 3D profile;
Conshelf II cross-section; Sealab II cutaway; timeline icons.

**Tab 3 — Cousteau:** Full-bleed Calypso opening; Conshelf II
village at Sha'ab Rumi; SP-350 launch sequence; Cousteau portrait;
The Calypso Journeys map.

**Tab 4 — Science:** Ocean cross-section hero (the most complex
illustration in the project); hydrothermal vent cross-section;
thermocline; biological pump; plate tectonics map; decompression
physics figure; bioluminescence mechanism.

**Tab 5 — Dive Lab:** Diver in light beam opener; 16-compartment
tissue diagram; freediving physiology figure.

**Tab 6 — Flora & Fauna:** Zone cross-section (expanded from Tab
4); ~20 featured species illustrations; coral polyp diagram;
vent community.

---

## 6. Surface Descriptions

> All surfaces drafted from textual descriptions. Screenshots
> added in v0.3 after prototype phase.

### 6.1 Global chrome

**Navigation:** Persistent horizontal bar, surface register, dark
and minimal. Six ALL CAPS tab labels, accent-colour underline on
active tab. Bathys wordmark left. Label-only, no icons. Does not
shift register with content below.

**Depth indicator:** Subtle vertical scale on right edge in
depth-sensitive tabs. Monospaced, small, informational only.

### 6.2 Tab 1 — Ocean Globe

Full-viewport Three.js globe, no chrome on initial load. Compact
layer toggle panel bottom-left (Currents, Temperature, MPAs,
Biodiversity, Argo, Chlorophyll, Depth Zones, Dive Sites). Side
panel 380px from right edge on click. Minimal HUD: zoom buttons,
reset, compass rose.

### 6.3 Tab 2 — Expeditions

Scrubable horizontal timeline, early 1900s to present. 3D flip
cards: front (image + name + type), back (key facts + links).
Four sub-sections: Missions & Expeditions, Vessels & Submarines,
Habitats, Researchers. Filter chips: Era, Ocean/Region, Type,
Depth Range.

### 6.4 Tab 3 — Cousteau

Full-bleed cinematic opening illustration. Six narrative layers:
The Man, The Calypso Journeys map, Calypso vessel cutaway, SP-350
Diving Saucer profile, Conshelf chapters (I, II, III), Legacy
thread (Cousteau to Jean-Michel to Fabien, Ballesta parallel).

### 6.5 Tab 4 — Science

Ocean cross-section hero at top, interactive zone navigation.
Six pillars via secondary nav. Every pillar opens with a 101 card.
Custom charts below with title, explanation, citation line.
Science Lens toggle top-right.

### 6.6 Tab 5 — Dive Lab

**Desktop simulator — three panels:**
- Left: Dive Plan Builder (depth/time canvas, free-draw, gas cards)
- Centre: 16 Tissue Compartment bars (Bühlmann compartments,
  real-time fill, ceiling depth shown large)
- Right: Deco Schedule (stop depths/durations, model selector:
  ZHL-16C / VPM-B / RGBM / Haldane 1908)

**Mobile simulator:** Preset depth profiles via swipeable card
picker. All three panels fully functional stacked vertically.

World Dive Sites: focused map, top 100 sites, filter chips,
site card with "Plan This Dive" loading profile into simulator.

### 6.7 Tab 6 — Flora & Fauna

Four entry paths: By Taxonomy, By Depth Zone, By Geography, By
Theme. Depth zone view: cross-section illustration becomes
interactive selector, entering abyssal zone shifts to Register 4.

Collapsed species card: hero image, common name, scientific name,
IUCN badge, depth range bar. Expanded card: hero image + all
facts + taxonomy tree + OBIS occurrence map + literature
citation + related species + dive sites + researcher cards.

Gold endemic badge on endemic species.

---

## 7. Photography Treatment

**Owner photography:** Full quality, subtle depth-register colour
harmony, visible credit line linking to photography website,
subtle watermark. Colour grading permitted.

**Institutional / CC photography:** Caption always present
(photographer / institution / license). No meaning-changing
crops. CC-BY-SA images displayed without modification.

**Historical / archival photography:** Subtle film grain texture.
No sepia or desaturation. Caption includes date and source.

---

## 8. Component Patterns

**Data card:** Compact, monospaced values, label headings.
Species facts, vessel specs, decompression schedules.

**Editorial card:** Body typography, editorial image, generous
whitespace. Expeditions, researchers, habitat dedicated sections.

**Feature card:** Large Display typography, full-bleed illustration
or image, minimal text. 101 cards, zone cards, habitat openings.

**Depth indicator:** Vertical bar + marker + monospaced label.
Consistent across Dive Lab, species cards, globe side panel.

**Citation lines:** Caption-size, below every chart, illustration,
data point, and image. DOI links. Not optional, not hidden.

**Science Lens annotations:** Floating panel at bathypelagic
register, thin accent-colour border, Caption-size body text,
Lens icon, link to Tab 4. Rendered via React context, not portals.

---

## 9. Responsive Behaviour — Mobile-First

Bathys is mobile-first, consistent with the orrery. Mobile is
the primary design target. Desktop is a progressive enhancement.

> See BA-04 OQ-02 (revised to mobile-first) and OQ-06 (mobile-
> first Dive Lab design).

**Mobile (< 768px) — the primary target**
Single-column layouts. Full-width cards. Touch-friendly tap
targets (minimum 44px). Globe fully functional via touch. Dive
Lab uses preset-profile card picker as primary interaction.
All six tabs fully functional at mobile width.

**Tablet (768–1199px) — enhancement layer**
Globe and content scale cleanly. Dive Lab panels stack vertically.
Cards 2-column. Side-by-side layouts begin to appear.

**Desktop (1200px+) — full enhancement**
Three-panel Dive Lab with free-draw canvas. Globe side panel
opens alongside globe. Card grids at 3+ columns.

All CSS written mobile-first: base styles target mobile, `min-width`
breakpoints layer in enhancements. No `max-width` queries for layout.

---

## 10. Accessibility

> Requirements locked at concept level. Implementation verified
> against prototype in v0.3.

Bathys is a scientific and educational resource. Accessibility
is part of the claim that anyone can use it.

### 10.1 Contrast ✅ LOCKED

All text meets WCAG 2.1 AA:
- Normal text (< 18px): minimum 4.5:1
- Large text (≥ 18px or ≥ 14px bold): minimum 3:1
- UI components and graphical objects: minimum 3:1

Every depth register's token values must be audited for contrast
before BA-05 v0.3 is locked. Mesopelagic and bathypelagic
registers are highest risk — dark backgrounds with blue text.
Cousteau red (#FF6B35) on dark navy must be verified for small text.

### 10.2 Keyboard navigation ✅ LOCKED

All interactive elements keyboard-accessible. Tab order follows
reading order. Focus indicators visible — accent colour ring,
minimum 2px solid. Globe navigable by keyboard (arrow keys
rotate, +/- zoom, Escape dismisses panels). Free-draw Dive Lab
canvas is pointer-only; keyboard equivalent is the preset-profile
mode.

### 10.3 Screen reader support ✅ LOCKED

All images have meaningful `alt` text. Decorative images use
`alt=""`. The globe has `role="application"` with `aria-label`
and keyboard instructions. All charts have a visually-hidden
text alternative. Tissue compartment bars have live `aria-valuenow`
attributes. The deco schedule is a proper `<table>` with `<th>`
headers.

### 10.4 Reduced motion ✅ LOCKED

All animations respect `prefers-reduced-motion`. Globe particle
system switches to static directional arrows. Depth register
transition becomes instant. Card flips become crossfades.

### 10.5 Colour independence ✅ LOCKED

IUCN status, depth zones, and MPA categories use colour AND a
text label — never colour alone. The depth register system must
be tested against deuteranopia and protanopia. Surface turquoise
and Cousteau red must be specifically tested.

---

*Bathys — BA-05 Design System · v0.2 · May 2026*
