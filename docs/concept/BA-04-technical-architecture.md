# Bathys — Technical Architecture

## BA-04 · Technical Architecture

> v0.2 · Draft · May 2026
> Updated: OQ-02 and OQ-06 revised to mobile-first; browser
> support, performance budget, project license added (§10);
> i18n section added (§12) with 26-language target.

---

## 1. Architecture Philosophy

Bathys is a UI-first project. The application is a web client
consumes open data APIs and pre-built static assets. No
application backend, no database, no authentication, no SSR.
Everything runs in the browser.

This is a deliberate constraint, not a limitation:
- Zero infrastructure to maintain
- Zero server costs
- Deployable to any static host (Cloudflare Pages, Vercel, Netlify)
- The entire application is auditable and forkable
- Performance is entirely in our control

---

## 2. Frontend Stack

### 2.1 Core framework ✅ LOCKED

| Technology | Version | Rationale |
|-----------|---------|----------|
| **React** | 18+ | Component model, hooks, Three.js integration via R3F. Consistent with orrery. |
| **TypeScript** | 5+ | Type safety for decompression modules is non-negotiable. Scientific computation in untyped JS is a maintenance hazard. |
| **Vite** | 5+ | Fast dev server, excellent Three.js/WebGL handling, static output only. |
| **Tailwind CSS** | 3+ | Utility-first, pairs with the depth-gradient token system. |

Alternatives rejected: Next.js (SSR overhead, no benefit for static client-only app), Vue/Svelte (inconsistent with orrery), Vanilla JS (TypeScript required for scientific trustworthiness).

### 2.2 3D and visualisation layer ✅ LOCKED

| Technology | Purpose |
|-----------|--------|
| **Three.js** | Core 3D engine — globe, depth zone cross-sections |
| **React Three Fiber (R3F)** | React integration for Three.js |
| **@react-three/drei** | OrbitControls, environment maps, loaders |
| **D3.js** | Custom scientific charts and diagrams |
| **Recharts** | Standard statistical charts |
| **Custom GLSL shaders** | Current particle system, depth gradient, bioluminescence |

Alternatives rejected: CesiumJS (overkill, heavy, complex licensing), Deck.gl (bundle weight), Plotly (insufficient customisation).

### 2.3 Build and tooling ✅ LOCKED

| Tool | Purpose |
|-----|--------|
| **Vite** | Build tool and dev server |
| **ESLint + Prettier** | Code quality — enforced in CI |
| **Vitest** | Unit testing — required for decompression algorithm modules |
| **Playwright** | E2E testing for critical UI paths |

Decompression module unit tests are non-negotiable. Scientific computation must be verified against known published dive profiles. See Section 5.

---

## 3. Globe Architecture

### 3.1 Globe engine ✅ LOCKED

Three.js sphere geometry with GEBCO bathymetric tile service as texture layer. OrbitControls for drag, zoom, tilt. Auto-rotation on load, stops on first interaction.

```
GlobeScene
  ├── EarthSphere (Three.js SphereGeometry)
  │     ├── BathymetricLayer (GEBCO WMS tiles)
  │     ├── AtmosphereShader (custom GLSL)
  │     └── DepthGradientMaterial (custom GLSL)
  ├── LayerManager
  │     ├── CurrentFlowLayer (CMEMS particle system)
  │     ├── TemperatureLayer (NOAA/CMEMS WMS overlay)
  │     ├── MPALayer (WDPA GeoJSON polygons)
  │     ├── BiodiversityLayer (OBIS hotspot markers)
  │     ├── ArgoLayer (live float positions)
  │     ├── ChlorophyllLayer (NASA WMS overlay)
  │     ├── DepthZoneLayer (epipelagic/meso/bathy/abyssal/hadal)
  │     └── DiveSiteLayer (curated site markers)
  └── InteractionManager
        ├── MarkerRaycaster
        ├── PolygonRaycaster
        └── SidePanelController
```

### 3.2 Bathymetric depth gradient ✅ LOCKED

| Depth | Colour |
|-------|--------|
| 0–200m (epipelagic) | Warm turquoise — #00B4D8 to #0077B6 |
| 200–1000m (mesopelagic) | Rich blue-green — #0077B6 to #023E8A |
| 1000–4000m (bathypelagic) | Deep indigo — #023E8A to #03045E |
| 4000–6000m (abyssal) | Near-black blue — #03045E to #010018 |
| 6000m+ (hadal) | True black — #010018 to #000000 |
| Land | Desaturated dark — minimal, ocean is the focus |

### 3.3 Ocean current particle system ✅ LOCKED (approach)

1. CMEMS WMS tiles provide current vector field as u/v components
2. Custom GLSL vertex shader advances particle positions each frame
3. Particles have lifetime — fade in, travel, fade out
4. Gulf Stream, Humboldt, Antarctic Circumpolar, Indonesian Throughflow immediately legible

Data fidelity resolved by prototype (OQ-01, resolved in Section 11).

### 3.4 MPA polygon layer ✅ LOCKED

1. WDPA monthly GeoJSON bulk download, processed at build time
2. Simplified polygon geometries (Douglas-Peucker algorithm)
3. Pre-tiled as static GeoJSON files by geographic region
4. Three.js loads relevant tile(s) as user zooms and pans
5. Colour-coded by IUCN category
6. MPA Atlas effectiveness layer as opacity modifier

---

## 4. Data Layer Architecture

### 4.1 Data strategy ✅ LOCKED

| Tier | Content | Access pattern |
|------|---------|----------------|
| **Static JSON** | Curated content — expeditions, vessels, habitats, researchers, species, dive sites, fleet entries | Pre-built at development time. No API call at runtime. |
| **Tile services** | GEBCO bathymetry, CMEMS currents and temperature, NASA chlorophyll, WDPA polygons (pre-tiled) | Loaded on demand as user navigates. |
| **Live APIs** | OBIS occurrence maps, IUCN Red List status, WoRMS taxonomy, Argo float positions | Called at runtime. Cached in sessionStorage. |

### 4.2 Species data architecture ✅ LOCKED

```
SpeciesCard component
  ├── StaticData (from pre-built JSON, instant)
  ├── ConservationStatus (IUCN API, cached 24h)
  ├── TaxonomyTree (WoRMS API, cached 24h)
  └── OccurrenceMap (OBIS API, loaded on card open)
```

### 4.3 Image pipeline ✅ LOCKED

Build-time pipeline (same approach as orrery):
1. Source images ingested from owner archive and licensed sources
2. Metadata extracted (photographer, license, source URL, date)
3. Resized to 400/800/1200/2400px, converted to WebP with JPEG fallback
4. Watermark applied to owner photography
5. Content-addressed filenames for cache-busting
6. Metadata JSON written — maps image IDs to paths and credit lines
7. Credits page auto-generated from metadata JSON

---

## 5. Decompression Engine Architecture

### 5.1 Module structure ✅ LOCKED

```
/src/deco/
  ├── constants/
  │     ├── buhlmann-zh16c.ts    — ZHL-16C coefficients (cited to Bühlmann 2002)
  │     ├── vpm-b.ts             — VPM-B parameters (cited to Yount 1986)
  │     └── rgbm.ts              — RGBM parameters (cited to Wienke 2002)
  ├── models/
  │     ├── buhlmann.ts          — ZHL-16C dissolved gas model
  │     ├── vpm-b.ts             — Varying permeability bubble model
  │     ├── rgbm.ts              — Reduced gradient bubble model
  │     └── haldane1908.ts       — Historical reference model (educational only)
  ├── freediving.ts
  ├── gases.ts
  ├── profile.ts
  ├── engine.ts
  └── __tests__/
        ├── buhlmann.test.ts
        ├── vpm-b.test.ts
        ├── gases.test.ts
        └── profile.test.ts
```

### 5.2 Bühlmann ZHL-16C implementation ✅ LOCKED

```typescript
// Haldane equation — exponential gas loading
function loadCompartment(
  currentPressure: number,
  alveolarPressure: number,
  halfTime: number,
  intervalMinutes: number
): number {
  return currentPressure +
    (alveolarPressure - currentPressure) *
    (1 - Math.pow(2, -intervalMinutes / halfTime));
}

// M-value ceiling — minimum safe depth for a compartment
function compartmentCeiling(
  compartmentPressure: number,
  a: number,
  b: number
): number {
  return (compartmentPressure - a) * b;
}
```

Unit tests validate against published profiles from Baker (1998) and PADI Technical Diving materials. Any deviation from published expected outputs fails the test suite.

### 5.3 Gas handling ✅ LOCKED

| Gas | Definition | Key constraint |
|-----|-----------|----------------|
| Air | 21% O₂, 79% N₂ | MOD: 56m (1.4 ppO₂) |
| Nitrox | 22–40% O₂, balance N₂ | MOD calculated per mix |
| Trimix | O₂ + He + N₂ (user defined) | Narcotic equivalent depth calculated |
| Heliox | O₂ + He, no N₂ | Extreme technical use |
| Pure O₂ | 100% O₂ | Deco gas only, max 6m |

No dive plan saving. Simulator is stateless by design. See BA-01 §The diver.

---

## 6. Visual Theme System Architecture

### 6.1 Depth-gradient multi-register system ✅ LOCKED

CSS custom property token system. Active register set at section level, cascades to all child components.

```css
[data-depth="surface"] {
  --color-bg-primary: #CAF0F8;
  --color-text-primary: #03045E;
  --color-accent: #00B4D8;
}
[data-depth="mesopelagic"] {
  --color-bg-primary: #023E8A;
  --color-text-primary: #90E0EF;
  --color-accent: #48CAE4;
  --biolum-color: rgba(0,255,200,0.1);
}
[data-depth="abyssal"] {
  --color-bg-primary: #010018;
  --color-text-primary: #90E0EF;
  --color-accent: #0096C7;
  --biolum-color: rgba(0,255,200,0.6);
}
```

Full token specification in BA-05.

Tab-to-register mapping:
| Tab | Depth register |
|-----|---------------|
| Ocean Globe | surface → abyssal (dynamic, follows zoom depth) |
| Expeditions | reef |
| Cousteau | reef → mesopelagic |
| Science | mesopelagic |
| Dive Lab | reef → bathypelagic (follows dive profile) |
| Flora & Fauna | surface → abyssal (follows depth zone filter) |

### 6.2 Typography ✅ LOCKED

| Use | Font | Weight |
|-----|------|--------|
| Display / Hero | Inter | 300 Light |
| Body | Inter | 400 Regular |
| Scientific data | JetBrains Mono | 400 |
| Section labels | Inter | 600 SemiBold + wide letter-spacing |

---

## 7. Application Architecture

### 7.1 Routing ✅ LOCKED

```
/                   → Ocean Globe (Tab 1)
/expeditions        → Expeditions (Tab 2)
/cousteau           → Cousteau (Tab 3)
/science            → Science (Tab 4)
/dive-lab           → Dive Lab (Tab 5)
/flora-fauna        → Flora & Fauna (Tab 6)
```

Deep linking: `/expeditions/vessel/calypso`, `/dive-lab/sites/malpelo`,
`/flora-fauna/species/architeuthis-dux` etc.

### 7.2 State management ✅ LOCKED

Zustand. Simple, bounded state shape. No Redux ceremony.

```typescript
interface GlobeState {
  activeLayer: LayerType[];
  viewportDepth: number;
  selectedFeature: Feature | null;
}
interface DecoState {
  divePlan: DivePlan;
  gasMix: GasMix[];
  activeModel: DecoModel;
  tissueState: TissueState[];
  decoSchedule: DecoStop[];
}
interface UIState {
  activeScienceLens: boolean;
  activeTab: TabId;
  depthRegister: DepthRegister;
}
```

### 7.3 Performance strategy ✅ LOCKED

| Concern | Mitigation |
|---------|----------|
| Globe initial load | Progressive tile loading, coarse-first |
| Current particle system | GPU-side, configurable particle count, reduced on mobile |
| 14,830 MPA polygons | Pre-simplified, pre-tiled, loaded by viewport only |
| Species images | WebP with JPEG fallback, responsive sizes, lazy loading |
| Three.js bundle | Dynamic import — globe loaded only when Tab 1 is active |
| D3 chart renders | Canvas-based D3 for large datasets, SVG for small |

---

## 8. Deployment Architecture ✅ LOCKED

| Component | Platform |
|-----------|----------|
| Static application | Cloudflare Pages |
| Image CDN | Cloudflare CDN |
| Pre-tiled WDPA GeoJSON | Cloudflare Pages static assets |
| Pre-built species JSON | Cloudflare Pages static assets |

CI/CD: GitHub Actions. Vitest decompression module tests are a blocking deployment gate.

---

## 9. Credits & Attribution Architecture ✅ LOCKED

```
/src/data/credits/
  ├── institutions.json
  ├── papers.json
  ├── datasets.json
  ├── photography.json
  └── people.json
```

All attribution data in structured JSON. Credits and Library pages render from these files automatically. Full schema in BA-06.

---

## 10. Browser Support, Performance & Project License

### 10.1 Browser support matrix ✅ LOCKED

Bathys requires WebGL 2.0. Binding requirement for Three.js globe.

| Browser | Minimum version |
|---------|----------------|
| Chrome / Chromium | 88+ |
| Firefox | 85+ |
| Safari | 15+ (WebGL 2.0 from Safari 15) |
| Edge | 88+ |
| Mobile Chrome (Android) | 88+ |
| Mobile Safari (iOS) | iOS 15+ |
| Samsung Internet | 14+ |

WebGL 2.0-incapable browsers receive a clear "browser not supported" message and prompt to upgrade. No 2D canvas fallback — the 3D globe is core to Bathys.

### 10.2 Performance budget ✅ LOCKED

Mobile is the primary performance target. Desktop is secondary.

| Metric | Mobile target | Desktop target | Critical threshold |
|--------|--------------|----------------|-------------------|
| First Contentful Paint | < 2s | < 1.5s | 4s |
| Time to Interactive | < 4s | < 3s | 6s |
| Globe initial render | < 3s (mid-range mobile) | < 2s | 5s |
| Lighthouse performance | ≥ 80 (mobile) | ≥ 85 | 70 |
| JS bundle (initial, gzipped) | < 150KB | < 150KB | 300KB |
| Globe module (lazy-loaded) | < 500KB | < 500KB | 1MB |
| Image load (hero, above fold) | < 1.5s on 4G | < 1s | 3s |
| Decompression calculation | < 100ms per update | < 100ms | 500ms |

Target device: mid-range Android (Samsung Galaxy A54-class) and iPhone SE 3rd gen. Mobile Lighthouse score is the gating CI metric.

### 10.3 Project license ✅ LOCKED

Codebase: **MIT License**. Covers `src/`, `scripts/`, `docs/`.

Does NOT cover: owner photography (all rights reserved), institutional photography (per institution terms), CC-licensed photography (per image terms), scientific data (per dataset terms).

`LICENSE` at repo root for code. `CONTENT-LICENSE.md` at repo root explaining the content licensing separately, pointing to Credits page for per-asset detail. Full provenance system in BA-06.

---

## 11. Open Questions — All Resolved

**OQ-01 — CMEMS WMS vs raw NetCDF**
✅ RESOLVED — Try WMS tiles first (option B). Switch to raw NetCDF client-side if animation quality insufficient. Globe prototype decides.

**OQ-02 — Mobile performance**
✅ REVISED TO MOBILE-FIRST — Bathys is mobile-first, consistent with the orrery. Mobile is the primary design and performance target. Desktop is a progressive enhancement. Globe particle count scales to device capability. Touch gestures are the primary interaction model.

**OQ-03 — Cousteau Society image licensing**
✅ RESOLVED — Ship Tab 3 with public domain fallback. Send formal request once project is demonstrable.

**OQ-04 — Science Lens implementation**
✅ RESOLVED — Context-based system. Each tab component subscribes to Lens state and renders its own annotations.

**OQ-05 — WDPA polygon simplification tolerance**
✅ RESOLVED — Calibrated visually during prototype phase as build-time tuning parameter.

**OQ-06 — Decompression simulator UI on mobile**
✅ REVISED TO MOBILE-FIRST — Mobile layout is the primary design target. Three panels stack vertically. Preset-profile card picker is the canonical mobile interaction. Desktop free-draw canvas is a progressive enhancement. Both are first-class experiences designed independently.

---

## 12. Internationalisation (i18n) ✅ LOCKED

### 12.1 Language targets

Bathys supports 26 languages. Base 14 from the orrery; 12 new additions with explicit ocean rationale.

**Base 14 — carried from orrery (confirm from orrery i18n docs):**

| Language | Locale |
|----------|--------|
| English | `en` |
| Spanish | `es` |
| French | `fr` |
| German | `de` |
| Italian | `it` |
| Portuguese | `pt` |
| Dutch | `nl` |
| Russian | `ru` |
| Chinese Simplified | `zh-CN` |
| Chinese Traditional | `zh-TW` |
| Japanese | `ja` |
| Korean | `ko` |
| Arabic | `ar` |
| Polish | `pl` |

**New additions — 12 languages with ocean rationale:**

| Language | Locale | Ocean rationale |
|----------|--------|----------------|
| Danish | `da` | Nordic ocean nation, North Sea and Baltic |
| Norwegian (Bokmål) | `nb` | Norwegian Sea, world-leading marine management |
| Swedish | `sv` | Baltic and North Sea, completes the Scandinavian set |
| Icelandic | `is` | Entire national identity around the ocean; geothermal vent connections |
| Indonesian | `id` | Heart of the Coral Triangle; Indonesian Throughflow |
| Malay | `ms` | Coral Triangle nation; South China Sea |
| Filipino / Tagalog | `tl` | Centre of the Coral Triangle; Tubbataha Reef; 7,600 islands |
| Vietnamese | `vi` | Long South China Sea coastline; growing marine science |
| Thai | `th` | Major global dive destination — Similan Islands, Richelieu Rock |
| Hindi | `hi` | Third-largest EEZ; NIO and INCOIS; the Indian Ocean is named after India |
| Greek | `el` | The project name *Bathys* is Greek; longest EU coastline |
| Swahili | `sw` | East African coast, Indian Ocean; Asha de Vos's research community |

**Not included:** Finnish.
**Total: 26 languages.**

### 12.2 i18n framework ✅ LOCKED

**Paraglide-js** (Inlang ecosystem) — consistent with the orrery.
Same toolchain: `project.inlang` + `messages/` folder structure.
React integration: `@inlang/paraglide-react` adapter.

### 12.3 Translation file structure ✅ LOCKED

```
messages/
  en.json  es.json  fr.json  de.json  it.json  pt.json
  nl.json  ru.json  zh-CN.json  zh-TW.json  ja.json  ko.json
  ar.json  pl.json  da.json  nb.json  sv.json  is.json
  id.json  ms.json  tl.json  vi.json  th.json  hi.json
  el.json  sw.json

project.inlang/settings.json
```

English is the source language. All others translate from English.

### 12.4 Script and layout requirements ✅ LOCKED

| Script family | Languages | Key requirement |
|--------------|-----------|----------------|
| Latin | en, es, fr, de, it, pt, nl, pl, da, nb, sv, is, id, ms, tl, vi, sw | Standard. Icelandic uses ð and þ — font must cover. |
| Cyrillic | ru | Ensure full Cyrillic range in font. |
| Arabic | ar | **RTL layout required.** Full page layout mirrors. |
| CJK | zh-CN, zh-TW, ja, ko | CJK-compatible font stack. Different line break rules. |
| Devanagari | hi | Requires Devanagari font support. |
| Thai | th | Unique script, no word separators. Thai-capable font. |
| Greek | el | Standard rendering. |

**RTL must be built in from day one** using CSS logical properties throughout:
`margin-inline-start`, `padding-inline-end`, `inset-inline-start`, `border-inline-start`, `text-align: start`.

### 12.5 Scientific content translation ✅ LOCKED

**Translate:** UI chrome, navigation, explanatory prose, 101 cards, section headers.

**Do not translate:** Scientific names, algorithm names (Bühlmann ZHL-16C, VPM-B, RGBM), institution abbreviations (MBARI, JAMSTEC), measurement values and units.

**Translate with care:** Depth zone names (use oceanographic standard per language). Decompression terminology (use diving federation standard per language). The name *Bathys* is not translated.

### 12.6 Translation completeness policy ✅ LOCKED

Languages below 80% completeness show a banner: *“This language translation is in progress. Some content appears in English.”*

**Tier 1 — complete before launch:** en, es, fr, de, pt, id, ms, tl, ja, zh-CN

**Tier 2 — within 3 months:** it, nl, ru, ko, ar, zh-TW, vi, th, hi

**Tier 3 — within 6 months:** pl, da, nb, sv, el, sw, is

Coral Triangle languages (Filipino, Indonesian, Malay) are deliberately in Tier 1 because Bathys's most featured content is their home.

---

*Bathys — BA-04 Technical Architecture · v0.2 · May 2026*
