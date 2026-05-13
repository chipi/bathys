# Bathys — Design System

## BA-05 · Design System

> v0.1 · Draft · May 2026
> Visual fidelity: Drafted from textual descriptions before
> prototypes exist. Every surface marked accordingly. Prototype
> verification required before this document is treated as a
> visual contract. Token names are locked; hex values and
> typographic specifics are starting proposals subject to
> revision against prototype.

---

## 1. Design Philosophy

### 1.1 The guiding principle

Bathys is the ocean rendered as a place you can think in.

Not a data dashboard. Not a tourism brochure. Not a scientific
portal. A place — with depth, atmosphere, and the feeling that
what you are looking at was made by someone who has been there.

Every design decision is tested against one question: does this
feel like the ocean, or does it feel like a website about the ocean?
The gap between those two things is the entire design challenge.

### 1.2 What this means in practice

**Depth is literal and visual.** The interface shifts register as
content goes deeper. Surface-zone content is warm and turquoise.
Reef content is rich blue-green. The mesopelagic is indigo. The
abyss is near-black with bioluminescent accents. The user feels
the descent.

**Light behaves like water.** Caustic light patterns, soft glows,
the way colour bleeds in water. Not as decoration — as the ambient
quality of the interface. Backgrounds are not flat. They breathe.

**Science is primary, beauty is the delivery mechanism.** No chart
exists purely as decoration. No illustration exists without
informational content. But every chart is custom-designed to the
Bathys visual language, and every illustration was made for this
project, not pulled from a library.

**Editorial voice in the typography.** Clean, precise, slightly
literary. The typographic rhythm should feel like the best science
magazine you have ever read — *National Geographic* meets *Nature*
meets a beautifully designed monograph.

**Photography is real.** The underwater images in Bathys come from
real dives. This is visible in them. Stock photography has a quality
that real underwater photography never has — too clean, too composed,
wrong colour temperature. The owner's images and carefully selected
institutional photography carry the truth of actually being there.

---

## 2. Colour System

### 2.1 The depth-gradient token system

Six depth registers, each a complete palette, each applied at the
section level. Token names are locked. Hex values are proposals
pending prototype verification.

**Register 0 — Surface** | Used in: page chrome, navigation, credits page.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#CAF0F8` | Main background |
| `--color-bg-secondary` | `#90E0EF` | Card and panel backgrounds |
| `--color-text-primary` | `#03045E` | Body text |
| `--color-text-secondary` | `#0077B6` | Secondary text, labels |
| `--color-accent` | `#00B4D8` | Interactive elements |
| `--color-surface` | `rgba(255,255,255,0.15)` | Cards (frosted) |
| `--glow-color` | `rgba(0,180,216,0.3)` | Glow effects |
| `--biolum-color` | `none` | Not active |

**Register 1 — Epipelagic (0–200m)** | Used in: Ocean Globe default, Expeditions, Dive Lab shallow.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#023E8A` | Main background |
| `--color-bg-secondary` | `#0077B6` | Cards and panels |
| `--color-text-primary` | `#CAF0F8` | Body text |
| `--color-accent` | `#00B4D8` | Interactive elements |
| `--glow-color` | `rgba(0,180,216,0.4)` | Glow effects |
| `--biolum-color` | `none` | Not active |

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

**Register 3 — Bathypelagic (1000–4000m)** | Used in: deep Science, deep Dive Lab.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#010018` | Main background |
| `--color-bg-secondary` | `#03045E` | Cards and panels |
| `--color-text-primary` | `#90E0EF` | Body text |
| `--color-accent` | `#0096C7` | Interactive elements |
| `--glow-color` | `rgba(0,150,199,0.2)` | Glow effects |
| `--biolum-color` | `rgba(0,255,200,0.4)` | Bioluminescence active |

**Register 4 — Abyssal / Hadal (4000m+)** | Used in: deepest Science, abyssal Flora & Fauna.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#000000` | True black |
| `--color-bg-secondary` | `#010018` | Near-black panels |
| `--color-text-primary` | `#90E0EF` | Body text |
| `--color-accent` | `#0096C7` | Interactive elements |
| `--biolum-color` | `rgba(0,255,200,0.6)` | Full bioluminescence |
| `--biolum-secondary` | `rgba(100,200,255,0.4)` | Secondary biolum |

**Register 5 — Cousteau (special)** | Warmer, more analog, cinematic.

| Token | Proposed value | Purpose |
|-------|---------------|---------|
| `--color-bg-primary` | `#001F3F` | Deep navy |
| `--color-bg-secondary` | `#003366` | Warmer dark blue |
| `--color-text-primary` | `#E8F4F8` | Warm off-white |
| `--color-accent` | `#FF6B35` | Cousteau red — his iconic red beanie |
| `--cousteau-red` | `#FF6B35` | Dedicated accent |
| `--calypso-gold` | `#D4A843` | Calypso vessel accent |

### 2.2 Semantic tokens — cross-cutting

| Token | Purpose |
|-------|---------|
| `--color-danger` | Error states, O₂ toxicity warning |
| `--color-warning` | Caution states, approaching limits |
| `--color-success` | Safe states |
| `--color-iucn-lc` | IUCN Least Concern — green |
| `--color-iucn-nt` | Near Threatened — yellow-green |
| `--color-iucn-vu` | Vulnerable — yellow |
| `--color-iucn-en` | Endangered — orange |
| `--color-iucn-cr` | Critically Endangered — red |
| `--color-iucn-ex` | Extinct — grey |

---

## 3. Typography

> Visual fidelity: Drafted from description. Final font selection confirmed in prototype visual testing.

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
| Drift | `cubic-bezier(0.0, 0.0, 0.6, 1.0)` | Long slow transitions |

### 4.3 Duration vocabulary

| Duration | Value | Use |
|----------|-------|-----|
| Instant | 80ms | State changes |
| Fast | 150ms | Icon transitions |
| Medium | 300ms | Card transitions |
| Slow | 600ms | Page transitions |
| Drift | 1200ms | Depth register transitions |
| Current | continuous | Globe particle system |

---

## 5. Illustration Style

### 5.1 Principles

All illustrations are custom to Bathys. Scientific accuracy with editorial warmth. Dark backgrounds with internal light sources (bioluminescence, sunlight, hydrothermal vents). Three-dimensional depth in every composition.

### 5.2 Illustration inventory

**Tab 2 — Expeditions:** Calypso cutaway, SP-350 3D profile, Conshelf II cross-section, timeline icons.

**Tab 3 — Cousteau:** Full-bleed Calypso opening, Conshelf II village at Sha'ab Rumi, SP-350 launch sequence, Cousteau portrait, The Calypso Journeys map.

**Tab 4 — Science:** Ocean cross-section hero (full water column, all zones, most complex illustration in the project), hydrothermal vent cross-section, thermocline, biological pump, plate tectonics map, decompression physics figure, bioluminescence mechanism.

**Tab 5 — Dive Lab:** Diver in light beam opener, 16-compartment tissue diagram, freediving physiology figure.

**Tab 6 — Flora & Fauna:** Zone cross-section (reused/expanded), ~20 featured species illustrations, coral polyp diagram, vent community.

---

## 6. Surface Descriptions

> Visual fidelity: All surfaces drafted from textual descriptions before prototypes exist. Screenshots added in v0.2 after prototype phase.

### 6.1 Global chrome

**Navigation:** Persistent horizontal bar, surface register, dark and minimal. Six ALL CAPS tab labels with accent-colour underline on active tab. Bathys wordmark left. Label-only, no icons. Does not shift register with content below.

**Depth indicator:** Subtle vertical scale on right edge in depth-sensitive tabs. Monospaced, small, informational only.

---

### 6.2 Tab 1 — Ocean Globe

> Visual fidelity: Drafted. Globe appearance depends on GEBCO tile rendering and shader implementation.

- Full-viewport Three.js globe, no chrome on initial load
- Compact layer toggle panel, bottom-left (Currents, Temperature, MPAs, Biodiversity, Argo, Chlorophyll, Depth Zones, Dive Sites)
- Side panel 380px from right edge on click, scrollable feature card, globe stays interactive behind it
- Minimal HUD: zoom buttons, reset, compass rose

---

### 6.3 Tab 2 — Expeditions

> Visual fidelity: Drafted. Card and timeline pending prototype.

- Scrubable horizontal timeline, early 1900s to present, key events as sized dots
- 3D flip card grid below: front (image + name + type), back (key facts + links)
- Three sub-sections: Missions & Expeditions, Vessels & Submarines, Researchers
- Filter chips: Era, Ocean/Region, Type, Depth Range

---

### 6.4 Tab 3 — Cousteau

> Visual fidelity: Drafted. Requires prototype and Cousteau Society licensing before contract is reliable.

### Six layers

**The Man — biography section:** Flowing prose, Body Large, generous line spacing, archival photography in text flow.

**The Calypso Journeys — interactive map:** Illustrated world map, nautical chart aesthetic, animated voyage lines on scroll, clickable waypoints.

**Calypso vessel section:** Annotated cutaway illustration with hotspot labels, data typography specifications.

**SP-350 Diving Saucer section:** Illustrated 3D profile, hotspot labels, specification table.

**Conshelf chapters:** Three scrollable chapters I/II/III, illustrated scenes, Conshelf II most detailed.

**Legacy thread:** Visual genealogy — Cousteau → Jean-Michel → Fabien, Ballesta parallel line.

---

### 6.5 Tab 4 — Science

> Visual fidelity: Drafted. Chart and diagram appearance pending prototype.

- Ocean cross-section hero at top, interactive zone navigation
- Six pillars via secondary nav: Physics, Chemistry, Biology, Geology, Climate, Technology
- Every pillar opens with a 101 card (Display statement + Data Large number + Body paragraph)
- Custom charts below with title, explanation, citation line
- Science Lens toggle top-right (lens icon)

---

### 6.6 Tab 5 — Dive Lab

> Visual fidelity: Drafted. Decompression simulator is the most complex surface. Prototype required.

**Decompression Simulator — three panels:**

*Left — Dive Plan Builder:* Depth/time coordinate canvas, drag to draw profile, ascent rate colour-coded (green/amber/red), gas cards dragged to depth ranges, open circuit / CCR toggle.

*Centre — Tissue Compartment Display:* 16 vertical bars (Bühlmann compartments), fill colour transitions safe→amber→red, real-time updates, ceiling depth shown in monospaced large.

*Right — Deco Schedule:* Stop depths and durations, real-time, model selector (ZHL-16C / VPM-B / RGBM / Haldane 1908).

**World Dive Sites:** Focused map (not full globe), top 100 sites, filter chips by type, site card with "Plan This Dive" button loading profile into simulator.

---

### 6.7 Tab 6 — Flora & Fauna

> Visual fidelity: Drafted. Species card pending prototype.

- Four entry paths: By Taxonomy, By Depth Zone, By Geography, By Theme
- Depth zone view: cross-section illustration becomes interactive selector, entering abyssal zone shifts to Register 4
- Collapsed species card: hero image, common name, scientific name, IUCN badge, depth range bar
- Expanded card: hero image + all facts + taxonomy tree + OBIS occurrence map + literature citation + related species + dive sites + researcher cards
- Gold endemic badge on endemic species

---

## 7. Photography Treatment

**Owner photography:** Full quality, subtle depth-register colour harmony, visible credit line linking to photography website, subtle watermark.

**Institutional / CC photography:** Caption always present (photographer / institution / license), no meaning-changing crops, CC-SA derivatives share alike.

**Historical / archival photography:** Subtle film grain texture, no sepia or desaturation, caption includes date and source.

---

## 8. Component Patterns

**Data card:** Compact, monospaced values, label headings. Species facts, vessel specs, deco schedules.

**Editorial card:** Body typography, editorial image, generous whitespace. Expeditions, researchers.

**Feature card:** Large Display typography, full-bleed illustration/image, minimal text. 101 cards, zone cards.

**Depth indicator:** Vertical bar + marker + monospaced label. Consistent across Dive Lab, species cards, globe side panel.

**Citation lines:** Caption-size, below every chart/illustration/data point/image, DOI links, not optional, not hidden.

**Science Lens annotations:** Floating panel at bathypelagic register, thin accent-colour border, Caption-size body text, Lens icon, link to Tab 4. Rendered via React portals above page content.

---

## 9. Responsive Behaviour

> Desktop-first. Mobile behaviour confirmed in prototype. See BA-04 OQ-02, OQ-06.

- **Desktop (1200px+):** Full experience. Three-panel Dive Lab, full globe.
- **Tablet (768–1199px):** Globe scales cleanly. Dive Lab two-panel. Cards 2-column.
- **Mobile (<768px):** Globe and Dive Lab free-draw are nice-to-have. All other tabs single-column, full-width cards, 44px min touch targets.

---

*Bathys — BA-05 Design System · v0.1 · May 2026*
