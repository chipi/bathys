# Bathys — Technical Architecture

## BA-04 · Technical Architecture

> v0.1 · Draft · May 2026
> Every significant technical decision documented with rationale and
> alternatives considered. Two categories throughout: locked decisions
> (marked ✅) and open questions consolidated in Section 10.
> Informed by concept-phase discussions. Prototype phase will resolve
> the remaining open questions before BA-05 is written.

---

## 1. Architecture Philosophy

Bathys is a UI-first project. The application is a web client that
consumes open data APIs and pre-built static assets. There is no
application backend, no database, no authentication, no server-side
rendering. Everything runs in the browser.

This is a deliberate constraint, not a limitation. It means:
- Zero infrastructure to maintain
- Zero server costs
- Deployable to any static host (Cloudflare Pages, Vercel, Netlify)
- The entire application is auditable and forkable
- Performance is entirely in our control

The constraint holds unless a specific capability genuinely requires
a backend and cannot be achieved client-side with acceptable
quality. Three such decisions were evaluated during the concept
phase — all three were resolved in favour of remaining client-side.
See Section 9 for the one remaining open question on this boundary.

---

## 2. Frontend Stack

### 2.1 Core framework ✅ LOCKED

| Technology | Version target | Rationale |
|-----------|---------------|-----------|
| **React** | 18+ | Component model, hooks, excellent Three.js integration via R3F. Consistent with orrery. |
| **TypeScript** | 5+ | Type safety across the decompression modules and data layer is non-negotiable. Scientific computation in untyped JS is a maintenance hazard. |
| **Vite** | 5+ | Fast dev server, excellent Three.js/WebGL handling, clean production builds. No CRA, no Next.js — static output only. |
| **Tailwind CSS** | 3+ | Utility-first, pairs cleanly with the depth-gradient token system. CSS custom properties for the theme layer. |

Alternatives considered:
- **Next.js** — rejected. SSR adds complexity with no benefit for a client-only static application. The routing and API-route machinery is overhead we don't need.
- **Vue / Svelte** — rejected. React is consistent with the orrery codebase and the existing Three.js/R3F ecosystem is mature.
- **Vanilla JS** — rejected. TypeScript is required for the decompression modules to be scientifically trustworthy.

---

### 2.2 3D and visualisation layer ✅ LOCKED

| Technology | Purpose |
|-----------|---------|
| **Three.js** | Core 3D engine — globe, depth zone cross-sections, vessel 3D models |
| **React Three Fiber (R3F)** | React integration for Three.js — component-based scene management |
| **@react-three/drei** | R3F helper library — OrbitControls, environment maps, loaders |
| **D3.js** | Custom scientific charts and diagrams — tissue compartment bars, dive profiles, species distribution maps, depth zone cross-sections |
| **Recharts** | Standard statistical charts where D3 custom work is not required |
| **Custom GLSL shaders** | Ocean current particle system, depth gradient atmosphere, bioluminescence effects |

Alternatives considered:
- **CesiumJS** — evaluated for globe. Rejected: overkill for this use case, heavy dependency, complex licensing. Three.js with GEBCO tiles gives us full control.
- **Deck.gl** — evaluated for data overlay layers. Rejected: adds significant bundle weight. D3 + custom Three.js layers achieve the same result with better visual integration.
- **Plotly** — rejected for scientific charts. D3 custom charts are necessary to match the Bathys visual language. Plotly output cannot be sufficiently customised.

---

### 2.3 Build and tooling ✅ LOCKED

| Tool | Purpose |
|-----|---------|
| **Vite** | Build tool and dev server |
| **ESLint + Prettier** | Code quality — enforced in CI |
| **Vitest** | Unit testing — required for decompression algorithm modules |
| **Playwright** | E2E testing for critical UI paths |

The decompression modules require unit tests. This is non-negotiable — scientific computation must be verified against known published dive profiles and their expected outputs. See Section 5.

---

## 3. Globe Architecture

### 3.1 Globe engine ✅ LOCKED

The globe is a Three.js sphere geometry with the GEBCO bathymetric
tile service applied as a texture layer. OrbitControls provides
drag, zoom, and tilt. Auto-rotation on load, stops on first user
interaction.

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
        ├── MarkerRaycaster (click detection on markers)
        ├── PolygonRaycaster (click detection on MPA polygons)
        └── SidePanelController (opens detail cards on click)
```

Tile loading uses Three.js TextureLoader with the GEBCO WMTS
endpoint. Tiles load progressively by zoom level — coarse global
view loads fast, detail resolves on zoom.

---

### 3.2 Bathymetric depth gradient ✅ LOCKED

| Depth | Colour |
|-------|--------|
| 0–200m (epipelagic) | Warm turquoise — #00B4D8 to #0077B6 |
| 200–1000m (mesopelagic) | Rich blue-green — #0077B6 to #023E8A |
| 1000–4000m (bathypelagic) | Deep indigo — #023E8A to #03045E |
| 4000–6000m (abyssal) | Near-black blue — #03045E to #010018 |
| 6000m+ (hadal) | True black — #010018 to #000000 |
| Land | Desaturated dark — kept minimal, ocean is the focus |

---

### 3.3 Ocean current particle system ✅ LOCKED (approach)

1. CMEMS WMS tiles provide the current vector field as u/v components
2. A custom GLSL vertex shader reads this field and advances particle positions each frame
3. Particles have a lifetime — fade in, travel along current, fade out
4. Gulf Stream, Humboldt, Antarctic Circumpolar and Indonesian Throughflow immediately legible

Whether WMS tile resolution is sufficient for visually compelling animation is resolved by prototype (OQ-01, resolved below).

---

### 3.4 MPA polygon layer ✅ LOCKED

1. WDPA monthly GeoJSON bulk download, processed at build time
2. Simplified polygon geometries (Douglas-Peucker algorithm)
3. Pre-tiled as static GeoJSON files by geographic region
4. Three.js loads relevant tile(s) as user zooms and pans
5. Colour-coded by IUCN category
6. MPA Atlas effectiveness layer applied as opacity modifier

---

## 4. Data Layer Architecture

### 4.1 Data strategy ✅ LOCKED

| Tier | Content | Access pattern |
|------|---------|----------------|
| **Static JSON** | Curated content — ~200 expeditions, ~60 vessels, ~80 researchers, ~2,000 featured species, 100 dive sites, 50 featured MPAs | Pre-built at development time. Served as static files. |
| **Tile services** | Spatial data — GEBCO bathymetry, CMEMS currents and temperature, NASA chlorophyll, WDPA polygons (pre-tiled) | Loaded on demand as the user navigates the globe. |
| **Live APIs** | Long-tail data — OBIS occurrence maps, IUCN Red List status, WoRMS taxonomy, Argo float positions | Called at runtime. Cached in sessionStorage. |

---

### 4.2 Species data architecture ✅ LOCKED

```
SpeciesCard component
  ├── StaticData (from pre-built JSON, instant)
  ├── ConservationStatus (IUCN API, cached 24h)
  ├── TaxonomyTree (WoRMS API, cached 24h)
  └── OccurrenceMap (OBIS API, loaded on card open)
```

---

### 4.3 Image pipeline ✅ LOCKED

Build-time pipeline (same approach as orrery):
1. Source images ingested from owner archive and licensed sources
2. Metadata extracted and stored
3. Images resized to responsive breakpoints (400/800/1200/2400px), WebP with JPEG fallback
4. Watermark applied to owner photography
5. Content-addressed filenames for cache-busting
6. Metadata JSON written
7. Credits page auto-generated from metadata JSON

---

## 5. Decompression Engine Architecture

### 5.1 Module structure ✅ LOCKED

```
/src/deco/
  ├── constants/
  │     ├── buhlmann-zh16c.ts    — ZHL-16C coefficients (all 32 values, cited to Bühlmann 2002)
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

Core computation per time step:

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

Unit tests validate against published dive profiles from Baker (1998) and PADI Technical Diving materials.

### 5.3 Gas handling ✅ LOCKED

| Gas | Definition | Key constraint |
|-----|-----------|----------------|
| Air | 21% O₂, 79% N₂ | MOD: 56m (1.4 ppO₂) |
| Nitrox | 22–40% O₂, balance N₂ | MOD calculated per mix |
| Trimix | O₂ + He + N₂ (user defined) | Narcotic equivalent depth calculated |
| Heliox | O₂ + He, no N₂ | Extreme technical use |
| Pure O₂ | 100% O₂ | Deco gas only, max 6m |

No dive plan saving. The simulator is stateless by design. See BA-01 §The diver.

---

## 6. Visual Theme System Architecture

### 6.1 Depth-gradient multi-register system ✅ LOCKED

```css
[data-depth="surface"] {
  --color-bg-primary: #CAF0F8;
  --color-text-primary: #03045E;
  --color-accent: #00B4D8;
}
[data-depth="reef"] {
  --color-bg-primary: #0077B6;
  --color-text-primary: #CAF0F8;
  --color-accent: #00B4D8;
}
[data-depth="mesopelagic"] {
  --color-bg-primary: #023E8A;
  --color-text-primary: #90E0EF;
  --color-accent: #48CAE4;
}
[data-depth="bathypelagic"] {
  --color-bg-primary: #03045E;
  --color-text-primary: #CAF0F8;
  --color-accent: #48CAE4;
}
[data-depth="abyssal"] {
  --color-bg-primary: #010018;
  --color-text-primary: #90E0EF;
  --color-accent: #0096C7;
  --biolum-color: rgba(0,255,200,0.6);
}
```

Full token specification with all values in BA-05.

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

Final font selection confirmed in BA-05 after prototype visual testing.

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

Deep linking: `/expeditions/vessel/calypso`, `/flora-fauna/species/architeuthis-dux`, `/dive-lab/sites/malpelo` etc.

### 7.2 State management ✅ LOCKED

Zustand. Chosen over Redux for simplicity.

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
|---------|-----------|
| Globe initial load | Progressive tile loading, coarse-first |
| Current particle system | GPU-side, configurable particle count, reduced on mobile |
| 14,830 MPA polygons | Pre-simplified, pre-tiled, loaded by viewport only |
| Species images | WebP with JPEG fallback, responsive sizes, lazy loading |
| Three.js bundle size | Dynamic import — globe module loaded only when Tab 1 is active |
| D3 chart renders | Canvas-based D3 for large datasets, SVG for small |

---

## 8. Deployment Architecture ✅ LOCKED

| Component | Platform |
|-----------|----------|
| Static application | Cloudflare Pages |
| Image CDN | Cloudflare CDN |
| Pre-tiled WDPA GeoJSON | Cloudflare Pages static assets |
| Pre-built species JSON | Cloudflare Pages static assets |

CI/CD: GitHub Actions. Vitest decompression module tests are a blocking gate.

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

Credits and Library pages auto-generated from these JSON files.

---

## 10. Open Questions for Phase 2

All six open questions resolved in concept phase.

**OQ-01 — CMEMS WMS vs raw NetCDF for current animation**
✅ RESOLVED — Try WMS tiles first. Switch to raw NetCDF client-side if animation quality insufficient.

**OQ-02 — Mobile performance with Three.js globe**
✅ RESOLVED — Desktop-first. Mobile is nice-to-have, not a requirement.

**OQ-03 — Cousteau Society image licensing**
✅ RESOLVED — Ship with fallback content. Request access once project is demonstrable.

**OQ-04 — Science Lens implementation**
✅ RESOLVED — Context-based system. Each tab subscribes to Lens state and renders its own annotations.

**OQ-05 — WDPA polygon simplification tolerance**
✅ RESOLVED — Calibrated visually during prototype phase as a build-time tuning parameter.

**OQ-06 — Decompression simulator UI on mobile**
✅ RESOLVED — Hybrid: desktop gets free-draw canvas, mobile gets preset depth profiles with full tissue/deco display.

---

*Bathys — BA-04 Technical Architecture · v0.1 · May 2026*
