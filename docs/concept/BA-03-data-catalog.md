# Bathys — Data / Content Catalog

## BA-03 · Data / Content Catalog

> v0.1 · Draft · May 2026
> Technical reference. Lists every data source, content type, external
> service and algorithm input that feeds Bathys. For each entry: what it
> provides, how to access it, license, characteristics, and which
> Bathys section it feeds.

---

## 1. Geospatial & Ocean Data

### 1.1 GEBCO — General Bathymetric Chart of the Oceans

| Field | Detail |
|-------|--------|
| **What it provides** | Global bathymetric grid — the seafloor elevation model that underlies the entire 3D globe. The most authoritative publicly available ocean depth dataset. |
| **Resolution** | 15 arc-second grid (approximately 500m at the equator) in the 2023 release |
| **Access** | GEBCO tile service (WMS/WMTS endpoints). Full grid download also available. Tile service preferred — avoids the 15GB raw file download entirely |
| **License** | Open, free to use with attribution |
| **Characteristics** | Updated periodically as new multibeam survey data arrives. Coastal and well-surveyed areas (North Atlantic, Mediterranean) are high resolution. Vast regions of the South Pacific remain estimated from satellite altimetry and are notably less accurate. This uncertainty is worth showing honestly in the UI — "surveyed" vs "estimated" regions |
| **Functional potential** | The visual and scientific backbone of Tab 1 (Ocean Globe). Drives the depth gradient colour system. Feeds the depth zone layer. Topographic drama of Mid-Atlantic Ridge, Mariana Trench, continental shelves all come from here |
| **Bathys sections** | Tab 1 (Ocean Globe), Tab 4 (Science — Ocean Geology), Tab 5 (Dive Lab — site depth profiles) |

---

### 1.2 CMEMS — Copernicus Marine Environment Monitoring Service

| Field | Detail |
|-------|--------|
| **What it provides** | Ocean currents, sea surface temperature, salinity, sea level anomaly, chlorophyll concentration, ice cover. Multiple products at different resolutions and depths |
| **Access** | WMS tile endpoints (browser-callable, no backend required). Also REST API and FTP download for raw NetCDF files if needed. WMS approach preferred per Decision 1 (option B first) |
| **Key products** | OSCAR near-real-time surface currents at 0.25° resolution; GLOBAL_ANALYSIS_FORECAST_PHY for 3D current fields; SST products updated daily |
| **License** | Copernicus open licence — free with registration, attribution required |
| **Characteristics** | Live, updated daily to weekly depending on product. High quality over open ocean, less reliable in complex coastal zones. Current vectors available as u/v components (east/west + north/south) — need to be converted to flow direction and magnitude for the particle animation system |
| **Functional potential** | The animated ocean current flow field on Tab 1. Sea surface temperature colour overlay. Seasonal animation (show the Gulf Stream strengthen in winter). The thermohaline conveyor belt visualisation in Tab 4 |
| **Bathys sections** | Tab 1 (Ocean Globe — currents, temperature overlays), Tab 4 (Science — Ocean Physics, Climate) |

---

### 1.3 NOAA OISST — Optimum Interpolation Sea Surface Temperature

| Field | Detail |
|-------|--------|
| **What it provides** | Daily global sea surface temperature at 0.25° resolution. Long time series back to 1981 |
| **Access** | NOAA ERDDAP server — browser-callable REST API. Returns NetCDF, CSV or JSON |
| **License** | Public domain (US government data) |
| **Characteristics** | Highly reliable, long time series makes it excellent for showing temperature change over time. Complements CMEMS for temperature data |
| **Functional potential** | Historical temperature animation — show 40 years of SST change as an animated overlay. Coral bleaching context — temperature anomaly maps overlaid on reef sites |
| **Bathys sections** | Tab 1 (Ocean Globe — temperature overlay), Tab 4 (Science — Climate, coral bleaching) |

---

### 1.4 UNEP-WCMC WDPA — World Database on Protected Areas

| Field | Detail |
|-------|--------|
| **What it provides** | The global authoritative database of marine and terrestrial protected areas. 14,830+ MPAs as polygon geometries with metadata — name, country, IUCN category, area, year established, designation type |
| **Access** | Protected Planet API (protectedplanet.net/api). Returns GeoJSON polygons. Also bulk download available as Shapefile/GeoJSON (updated monthly) |
| **License** | Open, free with attribution to UNEP-WCMC and IUCN |
| **Characteristics** | Updated monthly. Most comprehensive MPA dataset available. Coverage is global but data quality varies — some entries lack geometry, some have outdated status. IUCN category field is often blank for national designations. MPA Atlas is the quality layer on top |
| **Functional potential** | The MPA toggle layer on Tab 1 globe. Every polygon is live WDPA data. Click any polygon for the full MPA card. The 30x30 progress counter |
| **Bathys sections** | Tab 1 (Ocean Globe — MPA layer), Tab 2 (Expeditions — Pristine Seas missions), Tab 6 (Flora & Fauna — site conservation status) |

---

### 1.5 MPA Atlas — Marine Protection Atlas

| Field | Detail |
|-------|--------|
| **What it provides** | Protection effectiveness layer on top of WDPA. Classifies MPAs as fully protected, highly protected, or less protected. Blue Parks designation (34 awarded globally as of 2024) |
| **Access** | mpatlas.org — API available |
| **License** | Open data |
| **Characteristics** | Smaller dataset than WDPA but far more actionable. The distinction between "designated" and "effectively protected" is one of the most important facts in ocean conservation and this is the authoritative source for it |
| **Functional potential** | The protection effectiveness colour coding on the MPA layer. Blue Parks gold markers. The honest gap between 8% designated and effectively protected percentage |
| **Bathys sections** | Tab 1 (Ocean Globe — MPA layer quality tier), Tab 6 (Flora & Fauna — reserve effectiveness) |

---

### 1.6 NASA Ocean Color — Chlorophyll and Primary Production

| Field | Detail |
|-------|--------|
| **What it provides** | Satellite-derived chlorophyll-a concentration (phytoplankton density), sea surface temperature, particulate organic carbon. Long time series from MODIS-Aqua and VIIRS instruments |
| **Access** | NASA Earthdata OPeNDAP and WMS endpoints — browser-callable |
| **License** | Public domain (NASA) |
| **Characteristics** | Cloud cover creates gaps in daily data; monthly composites are cleaner. Spectacular for showing seasonal productivity blooms — the North Atlantic spring bloom, upwelling off Peru and Namibia |
| **Functional potential** | Chlorophyll overlay on Tab 1 globe — one of the most visually striking layers. Shows where the ocean is "alive" with phytoplankton. Direct visual link to the carbon pump section in Tab 4 |
| **Bathys sections** | Tab 1 (Ocean Globe — productivity overlay), Tab 4 (Science — Ocean Biology, Climate) |

---

### 1.7 Argo Float Network

| Field | Detail |
|-------|--------|
| **What it provides** | Real-time temperature and salinity profiles from approximately 4,000 autonomous floats distributed across the global ocean. Each float dives to 2,000m, collects data on ascent, surfaces to transmit, repeats every 10 days |
| **Access** | Argo GDAC ERDDAP server — browser-callable REST API. Returns float positions and profile data as JSON |
| **License** | Open (international program, 30+ contributing nations) |
| **Characteristics** | Live, updated continuously. The most comprehensive in-situ ocean monitoring system ever built. Float positions shift as they drift with currents — showing real ocean circulation |
| **Functional potential** | Live dot map of 4,000 floats on Tab 1 globe. Connects to the Technology section of Tab 4. Makes the abstract concept of ocean monitoring tangible |
| **Bathys sections** | Tab 1 (Ocean Globe — Argo overlay), Tab 4 (Science — Ocean Technology) |

---

## 2. Species & Biodiversity Data

### 2.1 OBIS — Ocean Biodiversity Information System

| Field | Detail |
|-------|--------|
| **What it provides** | Global ocean species occurrence records. Over 100 million occurrence records, 160,000+ species. Every record has a species ID, location, depth, date and data provider |
| **Access** | OBIS REST API — browser-callable. Returns JSON. Well documented |
| **License** | CC-BY (Creative Commons Attribution) |
| **Characteristics** | The most comprehensive marine biodiversity database available. Data quality varies by region — excellent for well-studied areas, sparse for the deep sea. Updates continuously as contributing institutions submit new records |
| **Functional potential** | Species distribution maps in Tab 6 cards. Live occurrence data showing where a species has been recorded globally. Feeds the "rarity at depth" visualisations |
| **Bathys sections** | Tab 1 (Ocean Globe — biodiversity hotspot layer), Tab 6 (Flora & Fauna — species distribution maps) |

---

### 2.2 IUCN Red List API

| Field | Detail |
|-------|--------|
| **What it provides** | Conservation status for assessed species — Least Concern through Critically Endangered and Extinct. Assessment rationale, population trend, threats, conservation measures |
| **Access** | IUCN Red List API (apiv3.iucnredlist.org) — requires free API token, browser-callable |
| **License** | Free for non-commercial use with attribution |
| **Characteristics** | Not all marine species have been assessed — assessment coverage is higher for vertebrates, lower for invertebrates and deep-sea species. Status updated as new assessments are completed |
| **Functional potential** | Conservation status badge on every species card in Tab 6. The shark status dashboard (37% of shark species threatened). Vaquita counter. Links conservation status directly to MPA coverage |
| **Bathys sections** | Tab 6 (Flora & Fauna — species cards, conservation status), Tab 1 (Ocean Globe — threatened species overlay) |

---

### 2.3 WoRMS — World Register of Marine Species

| Field | Detail |
|-------|--------|
| **What it provides** | Authoritative taxonomic register for all marine species. Accepted names, synonyms, classification hierarchy, links to other databases |
| **Access** | WoRMS REST API (marinespecies.org/rest) — browser-callable, no key required |
| **License** | Open, CC-BY |
| **Characteristics** | The canonical source for marine species names and taxonomy. Essential for ensuring consistent species identification across all data sources |
| **Functional potential** | Taxonomy display in species cards. Resolving synonyms when OBIS and other sources use different names for the same species. The classification tree in Tab 6 |
| **Bathys sections** | Tab 6 (Flora & Fauna — taxonomy, species cards) |

---

### 2.4 FishBase

| Field | Detail |
|-------|--------|
| **What it provides** | Comprehensive data on 35,000+ fish species — morphology, ecology, behaviour, distribution, fisheries data, images, references |
| **Access** | FishBase API (fishbase.se/api) — browser-callable |
| **License** | Open for non-commercial use |
| **Characteristics** | The gold standard for fish species data. Depth range, diet, maximum size, longevity all reliably documented for most species. Image library is extensive |
| **Functional potential** | Fish species cards in Tab 6. Depth range bars. The shark and ray sub-sections. Pelagic fish profiles |
| **Bathys sections** | Tab 6 (Flora & Fauna — fish species), Tab 5 (Dive Lab — species at dive sites) |

---

### 2.5 SeaLifeBase

| Field | Detail |
|-------|--------|
| **What it provides** | The non-fish equivalent of FishBase. Marine invertebrates, marine reptiles, marine mammals, seabirds — 90,000+ species |
| **Access** | SeaLifeBase API — same structure as FishBase |
| **License** | Open for non-commercial use |
| **Characteristics** | Coverage less complete than FishBase for some groups but the most comprehensive non-fish marine life database available |
| **Functional potential** | All non-fish species cards in Tab 6. Invertebrate gallery. Marine mammal profiles |
| **Bathys sections** | Tab 6 (Flora & Fauna — non-fish species) |

---

## 3. Photography & Visual Content

### 3.1 Owner Photography

| Field | Detail |
|-------|--------|
| **What it provides** | Original underwater photography by the project owner — a working underwater photographer. Primary visual content for species encountered, dive sites visited, reef environments |
| **Access** | Direct — owner's archive |
| **License** | Owner retains full copyright. Used in Bathys with explicit credit line and watermark linking to owner's photography website on every image |
| **Characteristics** | Authentic, high quality, irreplaceable. Gives Bathys a character no institutional photography can match. Coverage is personal — not comprehensive across all species or regions, but genuine where it exists |
| **Functional potential** | Hero images for species cards where owner has photographed that species. Dive site gallery primary images. Atmospheric section headers. The personal human dimension that separates Bathys from a data portal |
| **Pipeline note** | Image pipeline required — same approach as orrery. Optimisation, resizing for responsive delivery, metadata preservation, watermarking |
| **Bathys sections** | Tab 5 (Dive Lab — site galleries), Tab 6 (Flora & Fauna — species images), all section headers |

---

### 3.2 Creative Commons & Open License Photography

| Field | Detail |
|-------|--------|
| **What it provides** | Licensed underwater and marine photography from public sources where owner photography does not cover |
| **Primary sources** | Wikimedia Commons (CC-BY and CC-BY-SA), NOAA Photo Library (public domain), MBARI image library (licensed for educational use), Schmidt Ocean Institute (CC-BY), USGS (public domain) |
| **Access** | Direct download with license verification per image |
| **License** | Varies per image — CC-BY, CC-BY-SA, or public domain. All licenses require attribution. SA licenses require derivative works to share alike |
| **Characteristics** | Quality and coverage vary significantly. Institutional photography (MBARI, Schmidt) is excellent for deep-sea species. Wikimedia coverage strong for charismatic species, weaker for obscure invertebrates and deep-sea organisms |
| **Pipeline note** | Same image pipeline as owner photography. License and attribution metadata must be preserved and displayed per image. Credits page must list every image with source and license |
| **Bathys sections** | Tab 6 (Flora & Fauna — species images), Tab 2 (Expeditions — vessel and mission imagery), Tab 3 (Cousteau — archival imagery) |

---

### 3.3 Institutional Archives

| Field | Detail |
|-------|--------|
| **What it provides** | Historical and scientific photography from major ocean research institutions |
| **Key sources** | NOAA Ocean Exploration (public domain), JAMSTEC image library (enquiry required), IFREMER media library (enquiry required), Cousteau Society archives (licensing TBD — enquiry required), MBARI video and still library |
| **Access** | Varies — some direct download, some require written permission request |
| **License** | Varies — some public domain, some educational use licence, some requiring specific attribution |
| **Characteristics** | Irreplaceable for historical content — Cousteau era, early ROV footage stills, submersible imagery. Licensing complexity is real and must be resolved per image before use |
| **Pipeline note** | Licensing status must be documented per image in the Credits page. A licensing log should be maintained separately during content assembly |
| **Bathys sections** | Tab 2 (Expeditions), Tab 3 (Cousteau), Tab 4 (Science — Technology section) |

---

## 4. Decompression & Diving Algorithms

### 4.1 Bühlmann ZHL-16C — Dissolved Gas Model

| Field | Detail |
|-------|--------|
| **What it provides** | The primary decompression algorithm. 16 tissue compartments with published half-times and M-value coefficients for nitrogen and helium. The most widely implemented model in recreational and technical dive computers |
| **Primary source** | Bühlmann, A.A. (1984, revised 2002) *Decompression — Decompression Sickness*. Springer. Coefficient tables in Appendix. Baker, E.C. (1998) *Understanding M-values*. Immersed Magazine |
| **Access** | Published coefficients implemented as a TypeScript module. No external API — runs entirely client-side |
| **License** | Algorithm in public domain (published in primary literature). Implementation is original code |
| **Characteristics** | ZHL-16C is the conservative gradient factor variant used in modern dive computers. Half-times range from 4 min (compartment 1) to 635 min (compartment 16). All 32 coefficients (a and b values for N₂ and He, 16 compartments each) sourced from Bühlmann's published tables |
| **Functional potential** | The tissue compartment bar visualisation. The ceiling calculation. The core computation underpinning the deco simulator |
| **Bathys sections** | Tab 5 (Dive Lab — Decompression Simulator) |

---

### 4.2 VPM-B — Varying Permeability Model with Boyle's Law Compensation

| Field | Detail |
|-------|--------|
| **What it provides** | Bubble nuclei model. Models the growth and suppression of microscopic gas nuclei rather than dissolved gas alone. Produces deeper stops and shorter shallow stops compared to Bühlmann |
| **Primary sources** | Yount, D.E. & Hoffman, D.C. (1986) *On the use of a bubble formation model to calculate diving tables*. Aviation, Space & Environmental Medicine 57(2). Yount, D.E. (1979) *Skins of varying permeability*. Journal of the Acoustical Society of America |
| **Access** | Algorithm implemented as a TypeScript module. Runs entirely client-side |
| **License** | Algorithm in public domain. Implementation is original code |
| **Characteristics** | More conservative on deeper dives than Bühlmann. The -B extension (Boyle's Law compensation) accounts for bubble expansion during ascent. Educational value in showing contrast with Bühlmann on the same profile |
| **Bathys sections** | Tab 5 (Dive Lab — Decompression Simulator, model comparison) |

---

### 4.3 RGBM — Reduced Gradient Bubble Model

| Field | Detail |
|-------|--------|
| **What it provides** | Hybrid dissolved gas and bubble mechanics model. Adds bubble growth term to Haldanean base. More conservative on repetitive dives than Bühlmann |
| **Primary sources** | Wienke, B.R. & O'Leary, T.R. (2002) *Reduced Gradient Bubble Model: Diving Algorithm, Basis and Format*. NAUI Technical Diving. Wienke, B.R. (1994) *Basic Decompression Theory and Application*. Best Publishing |
| **Access** | Algorithm implemented as TypeScript module. Runs entirely client-side |
| **License** | Algorithm in public domain. Implementation is original code |
| **Characteristics** | Used by NAUI, some Suunto computers. The repetitive dive penalty is the key differentiator. Multi-day dive scenarios will show meaningful differences from Bühlmann |
| **Bathys sections** | Tab 5 (Dive Lab — Decompression Simulator, model comparison) |

---

### 4.4 Haldane 1908 — Historical Reference Model

| Field | Detail |
|-------|--------|
| **What it provides** | The original 1908 Royal Navy decompression model. Five tissue compartments, the 2:1 supersaturation ratio rule. The origin of all modern decompression theory |
| **Primary source** | Haldane, J.S., Boycott, A.E. & Damant, G.C.C. (1908) *The Prevention of Compressed Air Illness*. Journal of Hygiene, 8(3), 342–443 |
| **Access** | Historical model implemented as a lightweight TypeScript module for educational comparison only |
| **License** | Public domain |
| **Characteristics** | Not for dive planning — historical and educational use only. The contrast between 1908 (5 compartments, single ratio) and ZHL-16C (16 compartments, continuous M-value curves) is one of the most educational comparisons in the Dive Lab |
| **Bathys sections** | Tab 5 (Dive Lab — historical arc section), Tab 4 (Science — Physics of Diving) |

---

### 4.5 Freediving Physiology Reference

| Field | Detail |
|-------|--------|
| **What it provides** | The physiological model for breath-hold diving — mammalian dive reflex, oxygen and CO₂ dynamics, shallow water blackout mechanism, depth limits |
| **Primary source** | Lindholm, P. & Lundgren, C.E.G. (2009) *The physiology and pathophysiology of human breath-hold diving*. Journal of Applied Physiology, 106(1), 284–292 |
| **Access** | Educational content module — no live computation, illustrative visualisation |
| **License** | Published paper; content paraphrased and cited, not reproduced |
| **Characteristics** | Fundamentally different from scuba decompression — no nitrogen loading, but the CO₂ tolerance / O₂ depletion dynamic and the danger of hyperventilation are critical safety knowledge |
| **Bathys sections** | Tab 5 (Dive Lab — Freediving section), Tab 4 (Science — Physics of Diving) |

---

## 5. Expedition & Historical Content

### 5.1 Curated Expedition Database

| Field | Detail |
|-------|--------|
| **What it provides** | Hand-assembled database of major ocean expeditions, vessels, submersibles and key figures. The content backbone of Tab 2 and Tab 3 |
| **Scope** | Approximately 200 expeditions and missions, 60+ vessels and submersibles, 80+ researcher profiles |
| **Sources** | Institutional websites, Wikipedia (for dates and basic facts, always verified against primary sources), institutional publications, published books, peer-reviewed expedition reports |
| **License** | Original writing — facts are not copyrightable, text is original. Each fact cited to its source |
| **Characteristics** | Manually maintained. This is the highest-maintenance content in Bathys — no live API, requires periodic review as new expeditions occur and new research is published |
| **Functional potential** | The timeline, cards and gallery system of Tab 2. The Calypso Journeys map and chapter content of Tab 3 |
| **Bathys sections** | Tab 2 (Expeditions), Tab 3 (Cousteau) |

---

### 5.2 Cousteau Society Archives

| Field | Detail |
|-------|--------|
| **What it provides** | Historical documentation of Cousteau expeditions, Calypso records, Conshelf photographs and film stills, SP-350 technical documentation |
| **Access** | Enquiry required — licensing TBD. Cousteau Society is active and responsive to educational projects |
| **License** | To be negotiated — likely educational use licence with attribution |
| **Characteristics** | Irreplaceable for Tab 3. The Conshelf II photographs from Sudan, the SP-350 operational imagery, the Calypso deck and interior photography. No substitute source |
| **Open question** | Licensing must be resolved before Tab 3 content is finalised. This is the highest-risk content dependency in the project |
| **Bathys sections** | Tab 3 (Cousteau) |

---

## 6. Dive Site Content

### 6.1 Curated Dive Site Database

| Field | Detail |
|-------|--------|
| **What it provides** | Top 100 global dive sites with structured data — location, depth profile, type, best season, species highlights, difficulty, decompression considerations |
| **Scope** | 100 curated sites across all major dive regions. Includes the Eastern Tropical Pacific corridor sites (Galápagos, Cocos, Malpelo, Revillagigedo), Raja Ampat nodes, Red Sea classics, Pacific wrecks, cold water sites, historic sites |
| **Sources** | PADI dive site guides, DAN (Divers Alert Network) site data, liveaboard operator published information, personal dive knowledge, published dive guides |
| **License** | Original compiled database — facts verified, text original |
| **Characteristics** | Manually curated and maintained. A static JSON file pre-built at development time. Periodic review required as conditions change (reef health, wreck deterioration, access restrictions) |
| **Special entries** | Cousteau's Conshelf II site at Sha'ab Rumi (links to Tab 3), Five Deeps sites, all Pristine Seas featured locations |
| **Bathys sections** | Tab 5 (Dive Lab — World Dive Sites), Tab 1 (Ocean Globe — dive site markers) |

---

## 7. Science Reference Content

### 7.1 Primary Literature — Decompression

Full bibliography maintained in Credits page. Key papers underpinning the decompression simulator. All DOI-linked. See BA-03 Appendix A for full citation list.

---

### 7.2 Primary Literature — Ocean Science

Full bibliography maintained in Credits page. Papers underpinning Tab 4 content across all six pillars — Physics, Chemistry, Biology, Geology, Climate, Technology. See BA-03 Appendix A for full citation list.

---

### 7.3 IOC-UNESCO Ocean Decade Data

| Field | Detail |
|-------|--------|
| **What it provides** | Data and resources from the UN Decade of Ocean Science for Sustainable Development 2021–2030. Ocean health indicators, research priorities, global monitoring frameworks |
| **Access** | ocean-decade.org — open data portal |
| **License** | Open |
| **Functional potential** | The 30x30 progress bar. Ocean health indicators in the Climate section of Tab 4. Conservation context throughout |
| **Bathys sections** | Tab 1 (Ocean Globe — MPA progress), Tab 4 (Science — Climate) |

---

## 8. Library Content

### 8.1 Curated Library

| Field | Detail |
|-------|--------|
| **What it provides** | Hand-curated reading and viewing recommendations for users who want to go deeper. Organised by Bathys section — recommendations tied to the content area that sparked the interest |
| **Scope** | ~30 books, ~15 documentaries and films, ~10 institutions to follow, ~8 journals |
| **Access** | Static JSON, pre-built at development time. No API |
| **License** | Bibliographic data (titles, authors, dates) is factual and not copyrightable. Cover images are not used |
| **Characteristics** | Manually curated and maintained. Intentionally selective — the best next step for each area, not a comprehensive bibliography. Periodically reviewed |
| **Key books** | Cousteau & Dumas — *The Silent World*; Sylvia Earle — *The World Is Blue*; Robert Ballard — *The Eternal Darkness*; Edith Widder — *Below the Edge of Darkness*; Helen Scales — *The Brilliant Abyss*; Callum Roberts — *The Ocean of Life* |
| **Key documentaries** | *The Silent World* (1956); *World Without Sun* (1964); *Blue Planet I & II* (BBC); *Mission Blue* (Netflix); Ballesta's Gombessa films; OceanX Media productions |
| **Key journals** | *Deep-Sea Research I & II*; *Journal of the Acoustical Society of America*; *Marine Biology*; *Oceanography Magazine* |
| **Bathys sections** | Credits & Library page |

---

## 9. Content Summary by Tab

| Tab | Primary data sources | Secondary sources |
|-----|---------------------|-------------------|
| **1 — Ocean Globe** | GEBCO, CMEMS, WDPA, OBIS, NASA Ocean Color, Argo | NOAA OISST, MPA Atlas |
| **2 — Expeditions** | Curated expedition DB, institutional archives | Wikipedia (verified), published books |
| **3 — Cousteau** | Cousteau Society archives, curated content | IFREMER archives, published books |
| **4 — Science** | Primary literature (all pillars), CMEMS, OBIS, IUCN | NOAA, NASA, IOC-UNESCO |
| **5 — Dive Lab** | Bühlmann ZHL-16C, VPM-B, RGBM, curated dive site DB | DAN, FishBase (site species) |
| **6 — Flora & Fauna** | OBIS, IUCN Red List, WoRMS, FishBase, SeaLifeBase | Owner photography, CC photography |

---

## 10. Open Data Questions for BA-04

The following data questions require architectural decisions in BA-04 Technical Architecture:

1. **CMEMS WMS vs raw NetCDF** — WMS tile approach confirmed as Decision 1 option B. If current animation fidelity proves insufficient, switching to raw data with client-side processing (option A) requires a revisit. Flag as open question for prototype phase.

2. **GEBCO tile service refresh rate** — GEBCO tiles are updated annually. Acceptable for bathymetry (seafloor doesn't change on human timescales). No caching concern.

3. **WDPA bulk download vs API** — Monthly bulk GeoJSON download preferred over per-request API for MPA polygon layer (14,830+ polygons would be slow to query individually). Pre-processed at build time into tiles or clustered GeoJSON.

4. **Image CDN** — Owner photography and CC photography served via static CDN (Cloudflare or equivalent). Pipeline required for optimisation, resizing, watermarking. Same approach as orrery.

5. **Cousteau Society licensing** — Content dependency, not a data architecture question. Must resolve before Tab 3 development begins. If licensing fails, Tab 3 falls back to publicly available archival content only.

6. **Species database size** — OBIS has 100M+ records. Full download not feasible. API strategy: pre-build JSON cards for the ~2,000 featured species, call OBIS API live for occurrence maps and long-tail queries.

---

## Appendix A — Primary Literature (working list)

### Decompression Science
- Bühlmann, A.A. (1984, revised 2002). *Decompression — Decompression Sickness*. Springer. ISBN 3-540-42979-5
- Yount, D.E. & Hoffman, D.C. (1986). On the use of a bubble formation model to calculate diving tables. *Aviation, Space & Environmental Medicine*, 57(2), 149–156
- Yount, D.E. (1979). Skins of varying permeability: A stabilization mechanism for gas cavitation nuclei. *Journal of the Acoustical Society of America*, 65(6), 1430–1439
- Wienke, B.R. & O'Leary, T.R. (2002). *Reduced Gradient Bubble Model: Diving Algorithm, Basis and Format*. NAUI Technical Diving
- Haldane, J.S., Boycott, A.E. & Damant, G.C.C. (1908). The prevention of compressed-air illness. *Journal of Hygiene*, 8(3), 342–443. doi:10.1017/S0022172400003399
- Baker, E.C. (1998). Understanding M-values. *Immersed Magazine*, 3(3)
- Lindholm, P. & Lundgren, C.E.G. (2009). The physiology and pathophysiology of human breath-hold diving. *Journal of Applied Physiology*, 106(1), 284–292. doi:10.1152/japplphysiol.90991.2008

### Ocean Science (working list — to be expanded in BA-04)
- GEBCO Compilation Group (2023). *GEBCO 2023 Grid*. doi:10.5285/f98b053b-0cbc-6c23-e053-6c86abc0af7b
- Costello, M.J. et al. (2010). A census of marine biodiversity knowledge, resources, and future challenges. *PLoS ONE*, 5(8), e12110
- Hoegh-Guldberg, O. et al. (2007). Coral reefs under rapid climate change and ocean acidification. *Science*, 318(5857), 1737–1742

---

*Bathys — BA-03 Data / Content Catalog · v0.1 · May 2026*
