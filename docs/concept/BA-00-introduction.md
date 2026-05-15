# Bathys — Introduction

## BA-00 · Introduction

> v0.2 · Draft · May 2026
> Written last, read first. Entry point to the Bathys concept
> package. Seven documents total.

---

## 1. What This Package Is

This is the concept package for Bathys — an interactive learning
laboratory for the ocean.

Seven documents describing the project at the idea level: what
it is, what it does, what it uses, how it works, how it looks,
and how every asset is audited before it enters the build. It is
the input to formal definition work, not the output.

The package was developed following the conclusion of the Orrery
project, which proved the model: a single-person project, built
carefully, can produce something that feels like it came from a
major institution. Bathys applies that model to the ocean.

All documents are at concept level. Wherever a decision is locked,
it is marked ✅ LOCKED with rationale. Wherever a question was
open during concept phase, it is marked with its resolution.

---

## 2. What This Package Is Not

| Not a... | Because... |
|----------|-----------|
| **PRD set** | Product Requirements Documents come after. |
| **RFC set** | Open questions resolved during concept phase. |
| **ADR set** | Technical decisions described here; formal ADRs come in Phase 2. |
| **Design spec** | BA-05 establishes the visual language. Per-surface UXS documents come in Phase 2. |
| **Build plan** | This package defines what is being built, not when or how. |

---

## 3. Reading Order

| Order | Document | What it answers | Read time |
|-------|----------|----------------|-----------|
| 1st | **BA-00 Introduction** | What is this package and how do I read it? | 10 min |
| 2nd | **BA-01 Vision** | Why does Bathys exist? Who is it for? | 15 min |
| 3rd | **BA-02 Project Concept** | What is being built? All six tabs, all user journeys. | 45 min |
| 4th | **BA-03 Data Catalog** | What feeds the system? Every data source, API, algorithm. | 30 min |
| 5th | **BA-04 Technical Architecture** | How is it built? Every significant decision with rationale. | 30 min |
| 6th | **BA-05 Design System** | How does it look? The visual language, tokens, surfaces. | 30 min |
| 7th | **BA-06 Provenance & Content Pipeline** | How is every asset audited? Schemas, licensing matrix, build pipeline. | 20 min |

### Reading by role

| Role | Primary documents | Secondary |
|------|------------------|-----------|
| Product / stakeholder | BA-01, BA-02 | BA-00 |
| Frontend engineer | BA-04, BA-05, BA-03 | BA-02 |
| Data / science contributor | BA-03, BA-02 | BA-01 |
| Designer | BA-05, BA-02 | BA-01 |
| Content assembler | BA-06, BA-03 | BA-02 |
| Phase 2 author (any) | BA-02, BA-04 | BA-03, BA-05 |

---

## 4. Document Status

| Document | Version | Status |
|----------|---------|--------|
| BA-00 Introduction | v0.2 | Complete — updated for 7 documents, i18n, mobile-first |
| BA-01 Vision | v0.1 | Complete |
| BA-02 Project Concept | v0.1 | Complete — includes mission template, fleet entries, habitat dedicated sections |
| BA-03 Data Catalog | v0.1 | Complete — includes mission/vessel/fleet/habitat schemas |
| BA-04 Technical Architecture | v0.2 | Complete — OQ-02/06 revised to mobile-first; i18n §12 added |
| BA-05 Design System | v0.2 | Complete — mobile-first responsive; accessibility §10 added |
| BA-06 Provenance & Content Pipeline | v0.1 | Complete |

All documents will be reviewed and bumped to v0.2/v0.3 following
the Step 0 prototype phase. BA-05 in particular requires
verification against prototype screenshots.

---

## 5. Phase 1 → Phase 2 Handoff

| Concept package content | Becomes in Phase 2 |
|------------------------|-------------------|
| All six tabs in BA-02 | One PRD per user-facing surface |
| Credits and Library pages | Two PRDs |
| Locked decisions in BA-04 | Stream A ADRs — accepted from day one |
| All OQs resolved | No RFCs required from OQs |
| Visual token vocabulary in BA-05 | Carried unchanged into UXS documents |
| Surface descriptions in BA-05 | One UXS per surface, verified against prototypes |
| Glossary in BA-00 | Canonical term reference for all Phase 2 authors |
| Data sources in BA-03 | ADRs for data architecture decisions |
| Provenance records in BA-06 | `/src/data/credits/` JSON files, populated during content assembly |
| Open provenance questions in BA-06 §11 | Licensing tasks to resolve before each tab's content assembly |

---

## 6. The GitHub Repository

The Bathys repository is at: github.com/chipi/bathys

The concept package lives in `docs/concept/`. Seven Markdown
files are the working format. PDF versions generated when the
package is ready to share externally.

---

## 7. Glossary

---

### A

**Abyssal zone**
The ocean depth zone from 4,000m to 6,000m. Vast flat plains,
very low temperature, very high pressure, no sunlight. Home to
sea cucumbers, brittle stars, and marine snow. See also: depth
zone, hadal zone, marine snow.

**Abyssal plain**
The flat, sediment-covered floor of the deep ocean at 4,000–6,000m.
Covers more of the Earth's surface than any other environment.

**ADR (Architecture Decision Record)**
A Phase 2 document type. Records a single locked architectural
decision. Append-only. Not produced in concept phase.

**Alvin**
The primary US deep-sea research submersible. Operated by WHOI
since 1964. Discovered hydrothermal vents in 1977. Dived to
the Titanic in 1986. Depth rating 6,500m.

**Amphipod**
A crustacean order found at all ocean depths including the hadal
zone. Hadal amphipods thrive under pressures exceeding 1,000
atmospheres.

**Aqua-Lung**
The open-circuit scuba regulator co-invented by Cousteau and
Émile Gagnan in 1943. Made recreational and scientific diving
accessible.

**Argo program**
Approximately 4,000 autonomous profiling floats distributed
across the global ocean. Each dives to 2,000m, collects
temperature and salinity profiles, surfaces to transmit data
via satellite, repeats every 10 days. 30+ contributing nations.

**AUV (Autonomous Underwater Vehicle)**
An unmanned underwater vehicle following a pre-programmed
mission. Examples: Sentry (WHOI), Autosub (NOC). Contrast
with ROV, HOV.

**AWI (Alfred Wegener Institute)**
German federal institution for polar and ocean research,
Bremerhaven. Operates RV Polarstern. Home of Antje Boetius.

---

### B

**Ballesta, Laurent**
French marine biologist, extreme diver, underwater photographer.
Born 1974. Leads the Gombessa Expeditions. First to photograph
the coelacanth at depth (120m) using scuba. 28 consecutive days
at 100m in 2019. Six-time Wildlife Photographer of the Year,
only person to win the Grand Title twice (2021 and 2023). The
direct cultural heir to the Cousteau tradition. Tab 2 and Tab 3.

**Bathys**
This project. Named from the Greek root *bathys*, meaning deep.
The root of bathyscaphe, bathymetry, the bathypelagic zone.

**Bathypelagic zone**
The ocean depth zone from 1,000m to 4,000m. The midnight zone.
No sunlight. Bioluminescence is the primary light source.
Anglerfish, dragonfish, giant squid. See also: depth zone.

**Bathymetry**
The measurement of ocean depth and mapping of the seafloor.
Bathymetric data in Bathys comes from GEBCO.

**Biological pump**
The process by which carbon transfers from the ocean surface to
the deep ocean via sinking organic matter. One of the most
important climate-regulating mechanisms on Earth.

**Bioluminescence**
The production and emission of light by living organisms via a
luciferin/luciferase chemical reaction. Present in approximately
76% of deep-sea organisms. In Bathys, the visual language of
deep registers incorporates bioluminescent accent colours.

**Blue Parks**
Science-based certification for marine protected areas meeting
standards for conservation effectiveness. 34 awarded globally
as of 2024.

**Bühlmann ZHL-16C**
The dissolved gas decompression algorithm published by Albert
Bühlmann in revised form in 2002. 16 tissue compartments with
defined nitrogen and helium half-times and M-value coefficients.
The most widely implemented decompression algorithm in dive
computers. Primary model in the Bathys decompression simulator.
See also: decompression, M-value, tissue compartment.

---

### C

**Calypso**
Cousteau's research vessel 1950–1996. A converted British Royal
Navy minesweeper (J826), 40m, purchased for one franc per year
from Loël Guinness. Featured in Tab 3.

**CCR (Closed-Circuit Rebreather)**
Recirculates exhaled gas, removing CO₂ and adding oxygen.
Produces no bubbles. Extends dive duration and depth compared
to open circuit. Supported in the Bathys decompression simulator.

**Ceiling**
In decompression diving, the minimum depth for safe ascent at
any moment. Calculated from tissue saturation state. Shown
real-time in the Bathys decompression simulator.

**Chemosynthesis**
Biological production of organic compounds using chemical energy
rather than light. The basis of life at hydrothermal vents and
cold seeps. Discovered 1977 when Alvin found hydrothermal vents.

**CMEMS (Copernicus Marine Environment Monitoring Service)**
European ocean data service providing currents, temperature,
salinity, chlorophyll, sea level. Current vector data and
temperature overlays for the Bathys globe via WMS endpoints.

**Cold seep**
Seafloor environment where hydrocarbon-rich fluid seeps through
sediment, supporting chemosynthetic communities. Parallel
ecosystem to hydrothermal vents.

**Conshelf**
Cousteau's Continental Shelf Station program. Three stations:
Conshelf I (Marseille, 1962), Conshelf II (Sha'ab Rumi, 1963),
Conshelf III (Cap Ferrat, 1965). Featured in Tab 3.

**Coral Triangle**
Tropical Indo-Pacific region covering Indonesia, Malaysia,
Philippines, Papua New Guinea, Timor-Leste, Solomon Islands.
Over 75% of all known coral species and 3,000+ fish species.
The most biodiverse marine region on Earth.

---

### D

**DCS (Decompression Sickness)**
Gas bubbles in tissues and blood from ascending too rapidly.
Ranges from joint pain to paralysis and death. Prevented by
following a decompression schedule.

**DEEPSEA CHALLENGER**
Submersible built by the Acheron Project in Sydney, used by
James Cameron for his solo dive to Challenger Deep on 26 March
2012. 7.3m long, pilot sphere 43 inches diameter. Built over
seven years.

**DEEP (company)**
UK-based company building underwater habitats. Vanguard
(deployed 2025) is the first new subsea habitat in nearly 40
years. Sentinel (planned 2027) targets 225m depth, 8–50 crew.
See BA-02 Tab 2 dedicated habitat sections.

**Decompression model**
Mathematical model calculating safe ascent rate from depth,
duration, and gas mix. Three models in Bathys: Bühlmann
ZHL-16C, VPM-B, RGBM. Haldane 1908 for historical comparison.

**Decompression simulator**
The centrepiece of Tab 5 (Dive Lab). Interactive tool computing
tissue gas loading and decompression schedules in real time.
Built on real published algorithms. Educational, not a planning
tool.

**Decompression stop**
A pause at a specific depth during ascent to allow inert gas
to safely exit tissues. Required when saturation approaches
the M-value ceiling.

**Depth register**
The visual colour system applied at any given section of Bathys.
Six registers: surface, epipelagic, mesopelagic, bathypelagic,
abyssal/hadal, and the special Cousteau register. CSS custom
property sets. Full specification in BA-05.

**Depth zone**
One of five standard ocean depth classifications: epipelagic,
mesopelagic, bathypelagic, abyssal, hadal. See individual entries.

---

### E

**Eastern Tropical Pacific corridor**
The ecological network linking Galápagos (Ecuador), Cocos
(Costa Rica), Malpelo (Colombia), Revillagigedo (Mexico),
Coiba (Panama), Gorgona (Colombia). A highway for hammerheads,
whale sharks, and sea turtles tracked by satellite. Tab 1,
Tab 5, Tab 6.

**eDNA (Environmental DNA)**
Genetic material from environmental samples — water, sediment,
air — rather than directly from organisms. Reveals every species
present in an area without capturing any. Revolutionising marine
biodivers surveys. Tab 4 (Science — Ocean Technology), Tab 6.

**Endemic**
A species found naturally only in one specific location. The
Galápagos Marine Reserve has 18.2% endemic marine species.
Shown with a gold badge in Tab 6.

**Epipelagic zone**
The ocean depth zone 0–200m. The sunlit zone. Where almost
all marine photosynthesis occurs. Home to coral reefs, most
commercial fish, and the phytoplankton producing half of
Earth's oxygen.

---

### F

**Fendouzhe**
Chinese manned deep-sea submersible. Reached Challenger Deep
November 2020 with a crew of three, to 10,909m. Active.
Operated by IDSSE.

**Five Deeps**
Expedition led by Victor Vescovo 2018–2019 to reach the
deepest point in each of the world's five oceans. Used the
Limiting Factor. Set the deepest manned dive record at 10,928m
in Challenger Deep.

---

### G

**Galápagos Marine Reserve**
133,000 km² UNESCO World Heritage reserve. Nearly 20% endemic
marine species. Convergence of three ocean current systems.
One of the two primary poles of global marine biodiversity
in Bathys alongside Raja Ampat.

**GEBCO (General Bathymetric Chart of the Oceans)**
The international authority for ocean bathymetric mapping.
Produces the global seafloor elevation model at 15 arc-second
resolution. Data backbone of the Bathys globe. Open and free.

**GEOMAR**
Helmholtz Centre for Ocean Research, Kiel, Germany. Operates
RV Sonne and RV Meteor.

**Gombessa**
Expedition series led by Laurent Ballesta, each focused on
solving a scientific mystery through extreme diving. Named for
the local name of the coelacanth.

---

### H

**Hadal zone**
The ocean depth zone below 6,000m. Found only in ocean trenches.
Extreme pressure, cold, total darkness. Amphipods, snailfish,
foraminifera, xenophyophores. Named from *bathys* — the same
Greek root as the project name.

**Hass, Hans**
Austrian marine biologist and diving pioneer. Born 1919, died
2013. Developed rebreather diving and underwater camera technology
independently of Cousteau in the 1940s. The forgotten pioneer.
Tab 2 (Expeditions — Researchers).

**Haldane model**
The first quantitative decompression model, published 1908 for
the Royal Navy. Five tissue compartments, 2:1 supersaturation
ratio. The origin of all modern decompression theory. Included
in Bathys as a historical educational comparison.

**Heliox**
Helium and oxygen breathing gas mixture. Used in extreme deep
diving to eliminate nitrogen narcosis. Supported in the Bathys
decompression simulator.

**HOV (Human-Occupied Vehicle)**
A manned submarine for deep sea research. Examples: Alvin,
Nautile, Shinkai 6500, Limiting Factor, Fendouzhe.

**Hydrothermal vent**
A seafloor fissure from which geothermally heated water emerges.
Black smokers (sulfide-rich, up to 400°C) and white smokers.
Home to chemosynthetic ecosystems — life without sunlight.
Discovered 1977 by Alvin. Tab 4 (Science), Tab 6 (Flora & Fauna).

---

### I

**IDSSE (Institute of Deep-sea Science and Engineering)**
Chinese Academy of Sciences institute, Sanya. Operates
Fendouzhe and Deep Sea Warrior. China's primary deep-sea
research institution.

**IFREMER**
Institut Français de Recherche pour l'Exploitation de la Mer.
France's primary ocean research institution. Operates Nautile,
RV Pourquoi Pas? and L'Atalante. Co-led the Titanic discovery.

**Indonesian Throughflow**
The current system funnelling warm Pacific water through the
Indonesian Archipelago into the Indian Ocean. Directly
responsible for the extreme biodiversity of Raja Ampat.

**i18n (Internationalisation)**
Designing and building Bathys so it can be adapted for multiple
languages without engineering changes. Bathys supports 26
languages. Implementation uses Paraglide-js (Inlang ecosystem),
consistent with the orrery. See BA-04 §12.

**IOC-UNESCO (Intergovernmental Oceanographic Commission)**
UN body for international ocean science cooperation. Hosts the
Ocean Decade (2021–2030) and co-manages GEBCO.

**IUCN Red List**
Global assessment of species conservation status. Categories
from Least Concern through Extinct. Used in every Bathys
species card.

---

### J

**JAMSTEC (Japan Agency for Marine-Earth Science and Technology)**
Japan's primary ocean and earth science institution. Operates
Shinkai 6500, Kaiko ROV (first to full Challenger Deep), RV
Kairei. World-class deep-sea capability.

---

### L

**Limiting Factor**
Submersible used by Victor Vescovo in the Five Deeps. Built by
Triton Submarines. Set the record for deepest manned dive at
Challenger Deep (10,928m) in 2019.

---

### M

**Mobile-first**
A design and development approach where the mobile experience
is designed and built first, and desktop is a progressive
enhancement. Bathys is mobile-first, consistent with the orrery.
All CSS uses `min-width` breakpoints. All layouts begin as
single-column. Performance targets use mobile as the primary
metric. See BA-04 §OQ-02 (revised), BA-05 §9.

**Marine snow**
The continuous shower of mostly organic material falling from
upper ocean to deep seafloor. Primary food source for deep-sea
benthic communities. A major vector of the biological pump.

**MBARI (Monterey Bay Aquarium Research Institute)**
US ocean research institution, Pacific Grove, California.
Operates ROVs Doc Ricketts and Ventana. Produces extensive
open-access deep-sea imagery. A credited data and photography
source for Bathys.

**Mesopelagic zone**
The ocean depth zone 200m–1,000m. The twilight zone. The deep
scattering layer — billions of organisms migrating vertically
each day. The least understood and most ecologically important
zone for carbon cycling.

**Mir-1 and Mir-2**
Soviet/Russian manned deep-sea submersibles. Depth rating 6,000m.
Dived to the Titanic, Bismarck, under Arctic ice. Mother ship:
Akademik Mstislav Keldysh.

**MPA (Marine Protected Area)**
A geographically defined marine space managed for conservation.
14,830+ MPAs globally, covering approximately 8% of the ocean.
Data source: WDPA. Quality layer: MPA Atlas. Target: 30% by 2030.

**M-value**
In decompression theory, the maximum allowable supersaturation
pressure in a tissue compartment at a given depth. Defined by
the Bühlmann ZHL-16C a and b coefficients per compartment.

---

### N

**Nitrox**
Breathing gas mixture with more oxygen than air (21%), balance
nitrogen. Common mixes: 32% and 36% O₂. Extends no-decompression
limits at moderate depths. Supported in the Bathys simulator.

**NOC (National Oceanography Centre)**
UK's primary ocean research institution, Southampton. Operates
RRS Discovery and RRS James Cook.

---

### O

**OBIS (Ocean Biodiversity Information System)**
Primary global database for marine species occurrence records.
100M+ records, 160,000+ species. Used in Bathys species cards
for occurrence distribution maps. License: CC-BY. IOC-UNESCO.

---

### P

**Paraglide-js**
The i18n framework used by Bathys. Part of the Inlang ecosystem
— the same toolchain as the orrery. Framework-agnostic,
TypeScript-first, type-safe translation functions. React
integration via `@inlang/paraglide-react`. Translation files
in `messages/` as JSON, one file per locale. See BA-04 §12.

**Pelagic**
Of or relating to the open ocean water column. The pelagic
zones — epipelagic through hadal — are the primary depth
classification system used in Bathys.

**Phytoplankton**
Microscopic photosynthetic ocean surface organisms. Approximately
50% of Earth's oxygen production. Base of almost all marine
food webs. Visualised in Bathys via NASA satellite chlorophyll.

**Pristine Seas**
National Geographic Society project led by Enric Sala.
Scientific expeditions to remote ocean areas followed by
evidence-based advocacy for protection. Has contributed to
protecting over 6.6 million km² of ocean.

**PRD (Product Requirements Document)**
A Phase 2 document type. Makes the user-value argument for a
specific surface or feature. Not produced in concept phase.

---

### R

**Raja Ampat**
Approximately 1,500 islands in West Papua, Indonesia. Over
550 coral species (75% of all known), 1,800+ reef fish species.
The most biodiverse marine area on Earth. Tab 1, Tab 2, Tab 5,
Tab 6.

**RFC (Request for Comments)**
A Phase 2 document type. Explores an open technical question.
No RFCs were required from this concept package — all open
questions resolved during concept phase.

**RGBM (Reduced Gradient Bubble Model)**
Decompression model developed by B.R. Wienke extending the
Haldanean dissolved gas model with bubble mechanics. More
conservative on repetitive dives than Bühlmann. The third
model in the Bathys decompression simulator.

**ROV (Remotely Operated Vehicle)**
An unmanned underwater vehicle tethered to a surface ship.
Primary tool for deep-sea exploration and sampling. Examples:
Jason (WHOI), Hercules (OET), SuBastian (Schmidt), VICTOR
6000 (Ifremer).

---

### S

**Sala, Enric**
Spanish marine biologist. Born 1968. Founder of Pristine Seas.
Contributed to protection of 6.6 million km² of ocean. Key
figure in Galápagos-Cocos Swimway and Revillagigedo National
Park protections. Tab 2 (Expeditions — Researchers).

**Science Lens**
A toggleable overlay available in every tab bringing scientific
annotations into context. Physics annotations on dive profiles,
zone biology on the globe, decompression physiology on tissue
bars. Implemented as a React context system.

**Shinkai 6500**
JAMSTEC's primary manned deep-sea submersible. Depth rating
6,500m. Operational since 1989. Over 1,500 dives.

**Shirshov Institute of Oceanology**
Russia's primary ocean research institution, Moscow. Home of
the Mir submersible program.

**SOFAR channel**
A layer at approximately 600–900m depth where sound speed
reaches a minimum. Sound waves refract into this channel and
travel thousands of kilometres. Exploited by whales to
communicate across ocean basins.

**SP-350 Denise (Diving Saucer)**
The first underwater vehicle designed expressly for scientific
exploration. Built by OFRS in France, operated by Cousteau
from 1959. Diameter 2.85m, depth rating 350m, crew of two.
Over 1,500 dives. Featured in Tab 3.

---

### T

**Thermohaline circulation**
The global ocean circulation system driven by temperature and
salinity differences. Also called the ocean conveyor belt or
AMOC. Regulates climate across the entire planet.

**Thermocline**
A layer where temperature decreases rapidly with depth.
Acoustic and thermal barrier. Used by submarines for
concealment. Tab 4 Science.

**Tissue compartment**
A theoretical model of a body tissue with a specific rate of
gas uptake and release. Bühlmann ZHL-16C uses 16 compartments
with half-times from 4 to 635 minutes. Shown as vertical bars
in the Bathys decompression simulator.

**Trimix**
Oxygen, helium, and nitrogen breathing gas mixture. Used in
deep technical diving to reduce nitrogen narcosis while
controlling oxygen partial pressure. Supported in the Bathys
decompression simulator.

**Trieste**
The deep-diving bathyscaphe that carried Don Walsh and Jacques
Piccard to the bottom of Challenger Deep on 23 January 1960.
The first vessel to reach that depth. Built by Auguste Piccard.

---

### V

**VPM-B (Varying Permeability Model with Boyle's Law compensation)**
Decompression model by David Yount modelling bubble nuclei
formation rather than dissolved gas alone. Produces deeper
stops and shorter shallow stops compared to Bühlmann. The
second model in the Bathys decompression simulator.

---

### W

**WDPA (World Database on Protected Areas)**
Authoritative global database of marine and terrestrial
protected areas. Joint UNEP-WCMC and IUCN project. Updated
monthly. 14,830+ MPAs as polygon geometries. Data source for
the MPA overlay in the Bathys globe. Open with attribution.

**WHOI (Woods Hole Oceanographic Institution)**
Primary US private ocean research institution, Woods Hole,
Massachusetts. Operates Alvin, Jason ROV, RV Atlantis.

**WoRMS (World Register of Marine Species)**
Authoritative taxonomic register for all marine species.
Maintained at the Flanders Marine Institute. Used in Bathys
species cards for taxonomy. License: CC-BY.

---

### X

**Xenophyophore**
A single-celled organism (foraminifera) found in the deep sea,
reaching up to 20cm diameter — the largest single-celled
organisms on Earth. Found at abyssal and hadal depths.

---

### Z

**ZHL-16C**
See Bühlmann ZHL-16C.

---

*Bathys — BA-00 Introduction · v0.2 · May 2026*
*Concept Package · Seven documents · May 2026*
