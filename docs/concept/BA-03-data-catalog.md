# Bathys — Data / Content Catalog

## BA-03 · Data / Content Catalog

> v0.2 · Draft · May 2026
> Updated: mission/vessel/habitat/fleet JSON schemas added (§5.1);
> habitat inventory table with treatment column; DEEP data source
> (§5.3); FIU/Aquarius data source (§5.4).

---

## 1. Geospatial & Ocean Data

### 1.1 GEBCO

| Field | Detail |
|-------|--------|
| **What it provides** | Global bathymetric grid — the seafloor elevation model underlying the entire 3D globe |
| **Resolution** | 15 arc-second grid (~500m at the equator), 2023 release |
| **Access** | GEBCO tile service (WMS/WMTS endpoints). Tile service preferred — avoids 15GB raw file download |
| **License** | Open, free with attribution |
| **Characteristics** | Updated periodically. North Atlantic and Mediterranean are high resolution. South Pacific largely estimated from satellite altimetry. Uncertainty worth showing honestly in the UI. |
| **Bathys sections** | Tab 1 (Ocean Globe), Tab 4 (Ocean Geology), Tab 5 (site depth profiles) |

### 1.2 CMEMS

| Field | Detail |
|-------|--------|
| **What it provides** | Ocean currents, sea surface temperature, salinity, chlorophyll. Multiple products at different resolutions. |
| **Access** | WMS tile endpoints (browser-callable). WMS preferred per Decision 1 (option B). |
| **License** | Copernicus open licence — free with registration, attribution required |
| **Bathys sections** | Tab 1 (currents, temperature), Tab 4 (Ocean Physics, Climate) |

### 1.3 NOAA OISST

| Field | Detail |
|-------|--------|
| **What it provides** | Daily global sea surface temperature at 0.25° resolution. Time series back to 1981. |
| **Access** | NOAA ERDDAP server — browser-callable REST API |
| **License** | Public domain |
| **Bathys sections** | Tab 1 (temperature overlay), Tab 4 (Climate, coral bleaching) |

### 1.4 WDPA

| Field | Detail |
|-------|--------|
| **What it provides** | 14,830+ MPAs as polygon geometries with metadata |
| **Access** | Protected Planet API or bulk monthly GeoJSON download |
| **License** | Open with attribution to UNEP-WCMC and IUCN |
| **Bathys sections** | Tab 1 (MPA layer), Tab 2 (Pristine Seas), Tab 6 (conservation status) |

### 1.5 MPA Atlas

| Field | Detail |
|-------|--------|
| **What it provides** | Protection effectiveness layer on WDPA. Fully/highly/less protected classification. Blue Parks designation (34 awarded as of 2024). |
| **Access** | mpatlas.org API |
| **License** | Open |
| **Bathys sections** | Tab 1 (MPA quality tier), Tab 6 |

### 1.6 NASA Ocean Color

| Field | Detail |
|-------|--------|
| **What it provides** | Satellite-derived chlorophyll-a concentration, SST, primary production |
| **Access** | NASA Earthdata OPeNDAP and WMS endpoints |
| **License** | Public domain |
| **Bathys sections** | Tab 1 (productivity overlay), Tab 4 (Ocean Biology, Climate) |

### 1.7 Argo Float Network

| Field | Detail |
|-------|--------|
| **What it provides** | Real-time temperature and salinity profiles from ~4,000 autonomous floats. Each dives to 2,000m every 10 days. |
| **Access** | Argo GDAC ERDDAP server — browser-callable REST API |
| **License** | Open (30+ contributing nations) |
| **Bathys sections** | Tab 1 (Argo overlay), Tab 4 (Ocean Technology) |

---

## 2. Species & Biodiversity Data

### 2.1 OBIS

| Field | Detail |
|-------|--------|
| **What it provides** | 100M+ ocean species occurrence records, 160,000+ species |
| **Access** | OBIS REST API — browser-callable, well documented |
| **License** | CC-BY |
| **Bathys sections** | Tab 1 (biodiversity hotspot layer), Tab 6 (species distribution maps) |

### 2.2 IUCN Red List API

| Field | Detail |
|-------|--------|
| **What it provides** | Conservation status, population trend, threats, conservation measures |
| **Access** | apiv3.iucnredlist.org — free API token, browser-callable |
| **License** | Free for non-commercial use with attribution |
| **Bathys sections** | Tab 6 (species cards), Tab 1 (threatened species overlay) |

### 2.3 WoRMS

| Field | Detail |
|-------|--------|
| **What it provides** | Authoritative taxonomic register. Accepted names, synonyms, classification hierarchy. |
| **Access** | marinespecies.org/rest — browser-callable, no key required |
| **License** | Open, CC-BY |
| **Bathys sections** | Tab 6 (taxonomy, species cards) |

### 2.4 FishBase

| Field | Detail |
|-------|--------|
| **What it provides** | 35,000+ fish species — morphology, ecology, behaviour, distribution, longevity |
| **Access** | fishbase.se/api — browser-callable |
| **License** | Open for non-commercial use |
| **Bathys sections** | Tab 6 (fish species), Tab 5 (species at dive sites) |

### 2.5 SeaLifeBase

| Field | Detail |
|-------|--------|
| **What it provides** | 90,000+ non-fish marine species — invertebrates, reptiles, mammals, seabirds |
| **Access** | Same API structure as FishBase |
| **License** | Open for non-commercial use |
| **Bathys sections** | Tab 6 (non-fish species) |

---

## 3. Photography & Visual Content

### 3.1 Owner Photography

| Field | Detail |
|-------|--------|
| **What it provides** | Original underwater photography by the project owner — a working underwater photographer |
| **Access** | Direct — owner's archive |
| **License** | Owner retains full copyright. Credit line and watermark on every image. |
| **Pipeline note** | Image pipeline required — same approach as orrery. Optimisation, resizing, watermarking. |
| **Bathys sections** | Tab 5 (site galleries), Tab 6 (species images), all section headers |

### 3.2 Creative Commons & Open License Photography

| Field | Detail |
|-------|--------|
| **What it provides** | Licensed photography where owner content does not cover |
| **Primary sources** | Wikimedia Commons (CC-BY/CC-BY-SA), NOAA Photo Library (public domain), MBARI (educational use), Schmidt Ocean Institute (CC-BY), USGS (public domain) |
| **License** | Varies per image. CC-BY-SA images displayed without modification per BA-06 §4. |
| **Pipeline note** | Same pipeline as owner photography. License and attribution metadata preserved and displayed per image. |
| **Bathys sections** | Tab 6, Tab 2, Tab 3 |

### 3.3 Institutional Archives

| Field | Detail |
|-------|--------|
| **What it provides** | Historical and scientific photography from major ocean research institutions |
| **Key sources** | NOAA Ocean Exploration (public domain), JAMSTEC (enquiry required), IFREMER (enquiry required), Cousteau Society (TBD), MBARI |
| **Pipeline note** | Licensing status documented per image in Credits page. Licensing log maintained separately. |
| **Bathys sections** | Tab 2, Tab 3, Tab 4 |

---

## 4. Decompression & Diving Algorithms

### 4.1 Bühlmann ZHL-16C

| Field | Detail |
|-------|--------|
| **What it provides** | Primary decompression algorithm. 16 tissue compartments with published half-times and M-value coefficients for N₂ and He. |
| **Primary source** | Bühlmann, A.A. (1984, revised 2002) *Decompression — Decompression Sickness*. Springer. Baker, E.C. (1998) *Understanding M-values*. |
| **Access** | TypeScript module, runs entirely client-side. |
| **License** | Algorithm public domain. Implementation is original code. |
| **Bathys sections** | Tab 5 (Decompression Simulator) |

### 4.2 VPM-B

| Field | Detail |
|-------|--------|
| **What it provides** | Bubble nuclei model. Models microscopic gas nuclei formation rather than dissolved gas alone. |
| **Primary sources** | Yount & Hoffman (1986); Yount (1979) |
| **License** | Public domain. |
| **Bathys sections** | Tab 5 (model comparison) |

### 4.3 RGBM

| Field | Detail |
|-------|--------|
| **What it provides** | Hybrid dissolved gas and bubble mechanics model. More conservative on repetitive dives. |
| **Primary sources** | Wienke & O'Leary (2002); Wienke (1994) |
| **License** | Public domain. |
| **Bathys sections** | Tab 5 (model comparison) |

### 4.4 Haldane 1908

| Field | Detail |
|-------|--------|
| **What it provides** | Original 1908 Royal Navy decompression model. Educational historical comparison only. |
| **Primary source** | Haldane, J.S. et al. (1908). *Journal of Hygiene*, 8(3), 342–443. |
| **License** | Public domain. |
| **Bathys sections** | Tab 5 (historical arc), Tab 4 (Physics of Diving) |

### 4.5 Freediving Physiology

| Field | Detail |
|-------|--------|
| **What it provides** | Breath-hold diving physiological model — O₂/CO₂ dynamics, shallow water blackout mechanism |
| **Primary source** | Lindholm & Lundgren (2009). *Journal of Applied Physiology*, 106(1), 284–292. |
| **License** | Content paraphrased and cited, not reproduced. |
| **Bathys sections** | Tab 5 (Freediving), Tab 4 (Physics of Diving) |

---

## 5. Expedition & Historical Content

### 5.1 Curated Expedition Database

| Field | Detail |
|-------|--------|
| **What it provides** | Missions, vessels, habitats, researchers, fleets. Content backbone of Tab 2 and Tab 3. |
| **Scope** | ~200 expeditions and missions, 60+ vessels and submersibles, 14 habitats, 80+ researcher profiles, 11 fleet entries |
| **Sources** | Institutional websites, Wikipedia (verified against primary sources), published books, expedition reports |
| **License** | Original writing. Facts are not copyrightable. Each fact cited. |
| **Characteristics** | Manually maintained. Highest-maintenance content in Bathys. Periodic review as new expeditions occur. |
| **Bathys sections** | Tab 2 (Expeditions), Tab 3 (Cousteau) |

#### Mission entry schema

```json
{
  "id": "string",
  "name": "string",
  "type": "expedition | program | dive | survey | habitat",
  "dates": { "start": "YYYY", "end": "YYYY | null" },
  "status": "complete | active | ongoing-program",
  "the_question": "string — the scientific or exploratory question this mission was trying to answer",
  "region": "string",
  "max_depth_m": "number | null",
  "institution": "string",
  "institutions_involved": ["array of institution IDs"],
  "lead_researchers": ["array of researcher IDs"],
  "vessels_used": ["array of vessel IDs"],
  "fleet_tags": ["array of fleet IDs"],
  "key_events": [{ "date": "YYYY-MM-DD", "description": "string" }],
  "what_changed": "string — the specific discovery or outcome. Why this mission matters.",
  "related_missions": ["array of mission IDs"],
  "dive_sites_produced": ["array of dive site IDs"],
  "species_discovered": ["array of species IDs"],
  "links_to_tab3": "boolean",
  "photography": ["array of photography IDs"],
  "primary_sources": ["array of citation strings"]
}
```

#### Vessel entry schema

```json
{
  "id": "string",
  "name": "string",
  "type": "research-vessel | hov | rov | auv | habitat | bathysphere",
  "builder": "string",
  "operator": "string",
  "operator_id": "string",
  "country": "string",
  "commission_year": "number",
  "decommission_year": "number | null",
  "status": "active | retired | lost | in-refit | planned",
  "depth_rating_m": "number | null",
  "length_m": "number | null",
  "displacement_t": "number | null",
  "crew_capacity": "number | null",
  "endurance_days": "number | null",
  "dive_duration_hours": "number | null",
  "propulsion": "string | null",
  "key_systems": ["array of strings"],
  "mother_ship_id": "string | null",
  "deployed_vehicles": ["array of vessel IDs"],
  "fleet_tags": ["array of fleet IDs"],
  "key_missions": ["array of mission IDs"],
  "significance": "string",
  "links_to_tab3": "boolean",
  "photography": ["array of photography IDs"]
}
```

#### Habitat entry schema

Habitats share most vessel fields plus additional habitat-specific fields. `mother_ship_id` is always null (habitats are installed, not deployed).

```json
{
  "id": "string",
  "name": "string",
  "type": "habitat",
  "builder": "string",
  "operator": "string",
  "operator_id": "string",
  "country": "string",
  "commission_year": "number",
  "decommission_year": "number | null",
  "status": "active | retired | lost | planned",
  "operational_depth_m": "number",
  "pressure_mode": "ambient | surface",
  "internal_volume_m3": "number | null",
  "aquanaut_capacity": "number",
  "max_mission_duration_days": "number",
  "total_missions": "number | null",
  "total_aquanaut_days": "number | null",
  "life_support": "string",
  "ingress_method": "moon pool | lock-out chamber | docking port",
  "power_source": "string",
  "location": { "name": "string", "lat": "number", "lng": "number", "country_waters": "string" },
  "space_program_connection": "string | null",
  "fleet_tags": ["array of fleet IDs"],
  "key_missions": ["array of mission IDs"],
  "significance": "string",
  "links_to_tab3": "boolean",
  "links_to_dive_lab": "boolean",
  "photography": ["array of photography IDs"]
}
```

**Full habitat inventory:**

| ID | Name | Year | Depth | Capacity | Status | Treatment |
|----|------|------|-------|----------|--------|-----------|
| `conshelf-i` | Conshelf I | 1962 | 10m | 2 | retired | Dedicated — Tab 3 |
| `conshelf-ii` | Conshelf II | 1963 | 11m/27m | 7 | retired | Dedicated — Tab 3 |
| `conshelf-iii` | Conshelf III | 1965 | 102m | 6 | retired | Dedicated — Tab 3 |
| `sealab-i` | Sealab I | 1964 | 58m | 4 | retired | **Dedicated — Tab 2 §1** |
| `sealab-ii` | Sealab II | 1965 | 62m | 10/team | retired | **Dedicated — Tab 2 §1** |
| `sealab-iii` | Sealab III | 1969 | 185m (attempted) | — | lost | **Dedicated — Tab 2 §1** |
| `tektite-i` | Tektite I | 1969 | 15m | 4 | retired | **Dedicated — Tab 2 §2** |
| `tektite-ii` | Tektite II | 1970 | 15m | 4 | retired | **Dedicated — Tab 2 §2** |
| `hydrolab` | Hydrolab | 1966 | 15–18m | 4 | retired | Card only |
| `ben-franklin` | Ben Franklin mesoscaphe | 1969 | 200–600m drift | 6 | retired | Card only |
| `aquarius` | Aquarius Reef Base | 1987 | 19m | 6 | **active** | **Dedicated — Tab 2 §3** |
| `deep-vanguard` | DEEP Vanguard | 2025 | 20m | 4 | **active** | **Dedicated — Tab 2 §4** |
| `proteus` | Proteus | TBD | 18m | 12 | planned | Card only (until built) |
| `deep-sentinel` | DEEP Sentinel | 2027 (planned) | up to 225m | 8–50 | planned | **Dedicated — Tab 2 §4** |

#### Fleet entry schema

```json
{
  "id": "string",
  "name": "string",
  "institution": "string",
  "institution_id": "string",
  "country": "string",
  "active_since": "number",
  "description": "string — what this fleet was built to do",
  "fleet_concept": "string — how the vehicles relate; mother ship / deployed vehicle relationship",
  "vessels": ["array of vessel and habitat IDs"],
  "primary_vessel_id": "string",
  "notable_achievements": ["array of strings"],
  "status": "active | historical | partially-active",
  "photography": ["array of photography IDs"]
}
```

**Planned fleet entries (11):**
`cousteau-fleet`, `whoi-fleet`, `jamstec-fleet`, `ifremer-fleet`,
`shirshov-fleet`, `chinese-deepsea-fleet`, `schmidt-fleet`,
`noc-uk-fleet`, `us-navy-sealab-program`, `nasa-tektite-program`,
`deep-program`

---

### 5.2 Cousteau Society Archives

| Field | Detail |
|-------|--------|
| **What it provides** | Calypso records, Conshelf photographs, film stills, SP-350 documentation |
| **Access** | Enquiry required — licensing TBD |
| **License** | To be negotiated |
| **Open question** | Highest-risk content dependency. Must resolve before Tab 3 content assembly. Tracked in BA-06 §5. |
| **Bathys sections** | Tab 3 (Cousteau) |

### 5.3 DEEP — Vanguard and Sentinel

| Field | Detail |
|-------|--------|
| **What it provides** | Content and imagery for Vanguard (deployed late 2025) and Sentinel (planned 2027). The most significant current development in underwater habitation. |
| **Access** | deep.com press assets. Enquiry for higher-resolution imagery and technical documentation. |
| **License** | Press imagery for editorial/educational use — enquiry required |
| **Key facts** | Vanguard: 12m × 7.5m, 4 crew, 7+ days, ambient pressure, moon pool, DNV classified. Sentinel: modular, 8–50 crew, up to 225m depth. |
| **Note** | Content will evolve as program progresses. Bathys should track Sentinel milestones actively. |
| **Bathys sections** | Tab 2 (Habitats), Tab 4 (Ocean Technology) |

### 5.4 Florida International University / Aquarius

| Field | Detail |
|-------|--------|
| **What it provides** | Content and imagery for Aquarius Reef Base, 19m depth, Florida Keys. Also used by NASA NEEMO for astronaut training. |
| **Access** | FIU open educational resources. NOAA archives (public domain). |
| **License** | NOAA imagery public domain. FIU material — educational use enquiry. |
| **Bathys sections** | Tab 2 (Habitats), Tab 4 (Ocean Technology) |

---

## 6. Dive Site Content

### 6.1 Curated Dive Site Database

| Field | Detail |
|-------|--------|
| **What it provides** | Top 100 global dive sites with location, depth profile, type, best season, species highlights, difficulty, decompression considerations |
| **Scope** | 100 curated sites. Eastern Tropical Pacific corridor, Raja Ampat, Red Sea, Pacific wrecks, cold water, historic. |
| **Special entries** | Conshelf II at Sha'ab Rumi (links to Tab 3), Five Deeps sites, all Pristine Seas locations |
| **Bathys sections** | Tab 5 (World Dive Sites), Tab 1 (dive site markers) |

---

## 7. Science Reference Content

### 7.1–7.3 Primary Literature

Full bibliography maintained in Credits page. DOI-linked. See Appendix A.

---

## 8. Library Content

| Field | Detail |
|-------|--------|
| **Scope** | ~30 books, ~15 documentaries, ~10 institutions to follow, ~8 journals |
| **Access** | Static JSON, pre-built at development time |
| **Key books** | Cousteau & Dumas — *The Silent World*; Earle — *The World Is Blue*; Ballard — *The Eternal Darkness*; Widder — *Below the Edge of Darkness*; Scales — *The Brilliant Abyss* |
| **Key documentaries** | *The Silent World* (1956); *World Without Sun* (1964); *Blue Planet I & II*; *Mission Blue*; Ballesta Gombessa films |
| **Bathys sections** | Credits & Library page |

---

## 9. Content Summary by Tab

| Tab | Primary data sources | Secondary sources |
|-----|---------------------|-------------------|
| **1 — Ocean Globe** | GEBCO, CMEMS, WDPA, OBIS, NASA Ocean Color, Argo | NOAA OISST, MPA Atlas |
| **2 — Expeditions** | Curated expedition DB, institutional archives | Wikipedia (verified), published books |
| **3 — Cousteau** | Cousteau Society archives, curated content | IFREMER archives, published books |
| **4 — Science** | Primary literature (all pillars), CMEMS, OBIS, IUCN | NOAA, NASA, IOC-UNESCO |
| **5 — Dive Lab** | Bühlmann ZHL-16C, VPM-B, RGBM, curated dive site DB | DAN, FishBase |
| **6 — Flora & Fauna** | OBIS, IUCN Red List, WoRMS, FishBase, SeaLifeBase | Owner photography, CC photography |

---

## 10. Open Data Questions

1. **CMEMS WMS vs raw NetCDF** — option B confirmed; revisit if animation quality insufficient.
2. **GEBCO tile service refresh** — annual. Acceptable (seafloor doesn't change).
3. **WDPA bulk vs API** — monthly bulk download preferred. Pre-processed at build time.
4. **Image CDN** — Cloudflare. Pipeline required. Same approach as orrery.
5. **Cousteau Society licensing** — must resolve before Tab 3 development begins.
6. **Species database size** — pre-build JSON for ~2,000 featured species; live OBIS API for long tail.

---

## Appendix A — Primary Literature

### Decompression Science
- Bühlmann, A.A. (1984, revised 2002). *Decompression — Decompression Sickness*. Springer. ISBN 3-540-42979-5
- Yount, D.E. & Hoffman, D.C. (1986). On the use of a bubble formation model to calculate diving tables. *Aviation, Space & Environmental Medicine*, 57(2), 149–156
- Yount, D.E. (1979). Skins of varying permeability. *Journal of the Acoustical Society of America*, 65(6), 1430–1439
- Wienke, B.R. & O'Leary, T.R. (2002). *Reduced Gradient Bubble Model*. NAUI Technical Diving
- Haldane, J.S. et al. (1908). *Journal of Hygiene*, 8(3), 342–443. doi:10.1017/S0022172400003399
- Baker, E.C. (1998). Understanding M-values. *Immersed Magazine*, 3(3)
- Lindholm, P. & Lundgren, C.E.G. (2009). *Journal of Applied Physiology*, 106(1), 284–292. doi:10.1152/japplphysiol.90991.2008

### Ocean Science
- GEBCO Compilation Group (2023). *GEBCO 2023 Grid*. doi:10.5285/f98b053b-0cbc-6c23-e053-6c86abc0af7b
- Costello, M.J. et al. (2010). *PLoS ONE*, 5(8), e12110
- Hoegh-Guldberg, O. et al. (2007). *Science*, 318(5857), 1737–1742

---

*Bathys — BA-03 Data / Content Catalog · v0.2 · May 2026*
