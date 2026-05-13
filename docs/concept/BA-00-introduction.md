# Bathys — Introduction

## BA-00 · Introduction

> v0.1 · Draft · May 2026
> Written last, read first. The entry point to the Bathys concept
> package. Describes what the package is, what it is not, how to
> read it, and defines every term used across the six documents.

---

## 1. What This Package Is

This is the concept package for Bathys — an interactive learning
laboratory for the ocean.

The package consists of six documents that describe the project
at the idea level: what it is, what it does, what it uses, how
it works, and how it looks. It is the input to formal definition
work, not the output. Requirements, RFCs, and ADRs come after.
This package is what makes the concept clear enough to argue
about precisely.

The package was developed following the conclusion of the Orrery
project, which proved the model: a single-person project, built
carefully, can produce something that feels like it came from a
major institution. Bathys applies that model to the ocean.

All six documents are at concept level. The language is
intentionally exploratory — describing what is being built at
the idea level, not prescribing how it must be built. Wherever
a decision is locked, it is marked ✅ LOCKED with rationale.
Wherever a question was open during concept phase, it is marked
with its resolution.

---

## 2. What This Package Is Not

| Not a... | Because... |
|----------|-----------|
| **PRD set** | Product Requirements Documents come after this package. The concept package is the input to PRD writing. |
| **RFC set** | Open questions were flagged and resolved during concept phase. Remaining open questions for Phase 2 are consolidated in BA-04 Section 10 — all six were resolved before the package was completed. |
| **ADR set** | Technical decisions are described here with rationale. Formal ADR documents come in Phase 2. |
| **Design spec** | BA-05 establishes the visual language and token vocabulary. Per-surface UXS documents come in Phase 2. |
| **Build plan** | This package defines what is being built. Sprints, milestones, and implementation order are Phase 2 work. |

---

## 3. Reading Order

The documents are numbered in reading order (00–05), not
writing order. Read in the order below for the most coherent
experience of the complete concept.

| Order | Document | What it answers | Read time |
|-------|----------|----------------|-----------|
| 1st | **BA-00 Introduction** (this document) | What is this package and how do I read it? | 10 min |
| 2nd | **BA-01 Vision** | Why does Bathys exist? Who is it for? What makes it different? | 15 min |
| 3rd | **BA-02 Project Concept** | What is being built? All six tabs, all user journeys, how everything connects. | 45 min |
| 4th | **BA-03 Data Catalog** | What feeds the system? Every data source, API, algorithm input, and content type. | 30 min |
| 5th | **BA-04 Technical Architecture** | How is it built? Every significant technical decision with rationale. | 30 min |
| 6th | **BA-05 Design System** | How does it look and feel? The full visual language, token system, and surface descriptions. | 30 min |

### Reading by role

Different readers will weight these documents differently:

| Role | Primary documents | Secondary |
|------|------------------|-----------|
| Product / stakeholder | BA-01, BA-02 | BA-00 |
| Frontend engineer | BA-04, BA-05, BA-03 | BA-02 |
| Data / science contributor | BA-03, BA-02 | BA-01 |
| Designer | BA-05, BA-02 | BA-01 |
| Phase 2 author (any) | BA-02, BA-04 | BA-03, BA-05 |

---

## 4. Document Status

| Document | Version | Status | Visual fidelity |
|----------|---------|--------|----------------|
| BA-00 Introduction | v0.1 | Draft — complete | n/a |
| BA-01 Vision | v0.1 | Draft — complete | n/a |
| BA-02 Project Concept | v0.1 | Draft — complete | Drafted pre-prototype |
| BA-03 Data Catalog | v0.1 | Draft — complete | n/a |
| BA-04 Technical Architecture | v0.1 | Draft — all OQs resolved | n/a |
| BA-05 Design System | v0.1 | Draft — complete | Drafted pre-prototype |

All six documents will be reviewed and bumped to v0.2 following
the Step 0 prototype phase (globe, decompression simulator, zone
cross-section). BA-05 in particular requires verification against
prototype screenshots before it can be treated as a visual
contract.

---

## 5. Phase 1 → Phase 2 Handoff

The concept package maps directly to Phase 2 documentation as
follows:

| Concept package content | Becomes in Phase 2 |
|------------------------|-------------------|
| All six tabs described in BA-02 | One PRD per user-facing surface |
| Credits and Library pages described in BA-02 | Two PRDs — Credits as a data-driven attribution surface, Library as a curated navigation surface |
| Locked decisions in BA-04 | Stream A ADRs — accepted from day one |
| OQ-01 through OQ-06 (all resolved) | No RFCs required from OQs — all closed during concept phase |
| Visual token vocabulary in BA-05 | Carried unchanged into UXS documents |
| Surface descriptions in BA-05 | One UXS per surface, verified against prototypes |
| Glossary in BA-00 (below) | Canonical term reference for all Phase 2 authors |
| Data sources in BA-03 | ADRs for data architecture decisions, PRDs for data-dependent surfaces |

---

## 6. The GitHub Repository

The Bathys repository is at: github.com/chipi/bathys

Short description: *An interactive ocean learning laboratory —
3D bathymetric globe, decompression simulator, expedition catalog,
and marine science center built with Three.js and real ocean data.*

The concept package lives in `docs/concept/` following the same
structure as the orrery project. The six Markdown files are the
working format. PDF versions are generated once the package is
complete and ready to share externally.

```
docs/concept/
  BA-00-introduction.md       ← this document
  BA-01-vision.md
  BA-02-project-concept.md
  BA-03-data-catalog.md
  BA-04-technical-architecture.md
  BA-05-design-system.md
  images/                     ← referenced inline from documents
```

---

## 7. Glossary

All domain terms used across the concept package, defined here
once. Phase 2 authors add new terms to this glossary as they
are introduced. The glossary is the canonical term reference
for the project — when two documents use the same word, this
is what it means.

---

### A

**Abyssal zone**
The ocean depth zone from 4,000m to 6,000m. Vast flat plains,
very low temperature, very high pressure, no sunlight. The most
extensive depth zone by area. Home to sea cucumbers, brittle
stars, and the constant fall of marine snow from above. See
also: depth zone, hadal zone, marine snow.

**Abyssal plain**
The flat, sediment-covered floor of the deep ocean, typically
at 4,000–6,000m depth. Covers more of the Earth's surface than
any other environment.

**ADR (Architecture Decision Record)**
A Phase 2 document type. Records a single locked architectural
decision with rationale, alternatives rejected, and consequences.
Append-only — never edited after acceptance, only superseded.
Not produced in concept phase; locked decisions in BA-04 become
ADRs in Phase 2.

**Alvin**
The primary US deep-sea research submersible. Operated by WHOI
since 1964. Discovered hydrothermal vents in 1977. Dived to
the Titanic in 1986. Still operating. Depth rating 6,500m.

**Amphipod**
A crustacean order whose members are found at all ocean depths,
including the hadal zone. Hadal amphipods thrive under pressures
exceeding 1,000 atmospheres and are among the most abundant
organisms at full ocean depth.

**Aqua-Lung**
The open-circuit self-contained underwater breathing apparatus
co-invented by Jacques-Yves Cousteau and Émile Gagnan in 1943.
The first practical scuba regulator. Its invention made
recreational and scientific diving accessible.

**Argo program**
An international ocean observing program operating approximately
4,000 autonomous profiling floats distributed across the global
ocean. Each float dives to 2,000m, collects temperature and
salinity profiles on ascent, surfaces to transmit data via
satellite, and repeats the cycle every 10 days. Contributing
nations: 30+. Data: open.

**AUV (Autonomous Underwater Vehicle)**
An unmanned underwater vehicle that operates without a tether
or real-time human control, following a pre-programmed mission.
Used for seafloor mapping and water column surveys. Examples:
Sentry (WHOI), Autosub (NOC). Contrast with ROV, HOV.

**AWI (Alfred Wegener Institute)**
German federal research institution for polar and ocean research,
based in Bremerhaven. Operates RV Polarstern. Home institution
of Antje Boetius.

---

### B

**Ballesta, Laurent**
French marine biologist, extreme diver, and underwater photographer.
Born 1974 in Montpellier. Leads the Gombessa Expeditions. First
person to photograph the coelacanth at depth (120m) using scuba.
Spent 28 consecutive days at 100m depth in a pressurised habitat
in 2019. Six-time Wildlife Photographer of the Year, the only
person to win the Grand Title twice (2021 and 2023). The direct
cultural and scientific heir to the Cousteau tradition in French
underwater exploration. Featured prominently in Tab 2 and Tab 3.

**Bathys**
This project. Named from the Greek root *bathys*, meaning deep.
The root of bathyscaphe, bathymetry, the bathypelagic zone.

**Bathypelagic zone**
The ocean depth zone from 1,000m to 4,000m. Also called the
midnight zone. No sunlight. Bioluminescence is the primary
light source. Home to anglerfish, dragonfish, giant squid.
See also: depth zone.

**Bathymetry**
The measurement of ocean depth and the mapping of the seafloor
topography. The bathymetric data used in Bathys comes from
GEBCO. Analogous to topography for land surfaces.

**Biological pump**
The process by which carbon is transferred from the ocean
surface to the deep ocean via the sinking of organic matter
(dead organisms, faecal pellets, marine snow). One of the most
important climate-regulating mechanisms on Earth.

**Bioluminescence**
The production and emission of light by living organisms through
a chemical reaction involving luciferin and luciferase. The most
widespread form of communication on Earth. Present in
approximately 76% of deep-sea organisms. In Bathys, the visual
language of deep registers incorporates bioluminescent accent
colours as interaction feedback.

**Blue Parks**
A science-based certification system for marine protected areas,
awarded to MPAs that meet standards for conservation effectiveness.
34 Blue Parks awarded globally as of 2024.

**Bühlmann ZHL-16C**
The dissolved gas decompression algorithm developed by Albert
Bühlmann and published in revised form in 2002. 16 tissue
compartments, each with defined nitrogen and helium half-times
and M-value coefficients. The most widely implemented
decompression algorithm in recreational and technical dive
computers. The primary model in the Bathys decompression
simulator. See also: decompression, M-value, tissue compartment.

---

### C

**Calypso**
The research vessel of Jacques-Yves Cousteau from 1950 to 1996.
A converted British Royal Navy minesweeper (J826), 40m long,
purchased for one franc per year from Loël Guinness. Refitted
as a floating oceanographic laboratory. Featured in Tab 3.

**CCR (Closed-Circuit Rebreather)**
A type of underwater breathing apparatus that recirculates the
diver's exhaled gas, removing CO₂ and adding oxygen to maintain
a set partial pressure. Produces no bubbles. Dramatically
extends dive duration and depth compared to open circuit scuba.
Supported in the Bathys decompression simulator.

**Ceiling**
In decompression diving, the minimum depth to which a diver
can safely ascend at any given moment without risking
decompression sickness. Calculated by the decompression model
from the current tissue saturation state. Shown as a real-time
value in the Bathys decompression simulator.

**Chemosynthesis**
The biological production of organic compounds using chemical
energy rather than light. The basis of life at hydrothermal
vents and cold seeps — ecosystems that receive no sunlight.
Discovered in 1977 when Alvin found hydrothermal vents.

**CMEMS (Copernicus Marine Environment Monitoring Service)**
The European ocean data service providing ocean currents, sea
surface temperature, salinity, chlorophyll, and sea level data.
Provides the current vector data and temperature overlays for
the Bathys globe. Access via WMS tile endpoints.

**Cold seep**
A seafloor environment where hydrocarbon-rich fluid seeps through
the sediment, supporting chemosynthetic communities. Parallel
ecosystem to hydrothermal vents but without the extreme
temperatures.

**Conshelf**
The Continental Shelf Station program run by Cousteau in the
1960s. Three stations: Conshelf I (Marseille, 1962), Conshelf
II (Sha'ab Rumi, Red Sea, 1963), Conshelf III (Cap Ferrat,
1965). The program demonstrated that humans could live and work
productively underwater for extended periods. Featured in Tab 3.

**Coral Triangle**
A roughly triangular region of the tropical Indo-Pacific,
covering parts of Indonesia, Malaysia, the Philippines, Papua
New Guinea, Timor-Leste, and the Solomon Islands. Contains
over 75% of all known coral species and more than 3,000 fish
species. The most biodiverse marine region on Earth.

---

### D

**DCS (Decompression Sickness)**
A condition caused by the formation of gas bubbles in tissues
and blood when a diver ascends too rapidly, causing dissolved
inert gas to come out of solution. Ranges from joint pain
("the bends") to paralysis and death depending on severity.
Prevented by following a decompression schedule calculated by
a decompression model.

**DEEPSEA CHALLENGER**
The deep-diving submersible built by the Acheron Project in
Sydney, Australia and used by James Cameron for his solo dive
to Challenger Deep on 26 March 2012. 7.3m long, pilot sphere
43 inches in diameter. Built over seven years.

**Decompression model**
A mathematical model that calculates the safe rate of ascent
for a diver based on the depth, duration, and gas mix of their
dive. Three models are implemented in the Bathys decompression
simulator: Bühlmann ZHL-16C, VPM-B, and RGBM. A historical
fourth model, Haldane 1908, is included for educational
comparison.

**Decompression simulator**
The centrepiece of Bathys Tab 5 (Dive Lab). An interactive
tool that computes and visualises tissue gas loading and
decompression schedules in real time as a dive profile is
drawn. Built on real published algorithms. Not a dive planning
tool — an educational simulator.

**Decompression stop**
A pause at a specific depth during ascent, held for a specified
duration to allow inert gas to safely exit the tissues before
the diver ascends further. Required when tissue saturation
approaches the M-value ceiling. Shown in the Bathys decompression
simulator as depth and duration pairs.

**Depth register**
The visual colour system applied at any given section of Bathys,
corresponding to an ocean depth zone. Six registers: surface,
epipelagic, mesopelagic, bathypelagic, abyssal/hadal, and the
special Cousteau register. Defined as CSS custom property sets.
Full specification in BA-05.

**Depth zone**
One of the five standard ocean depth classifications used in
oceanography and in Bathys: epipelagic, mesopelagic,
bathypelagic, abyssal, hadal. See individual entries.

---

### E

**Eastern Tropical Pacific corridor**
The ecological network linking the marine protected areas of
Galápagos (Ecuador), Cocos Island (Costa Rica), Malpelo
(Colombia), Revillagigedo (Mexico), Coiba (Panama), and Gorgona
(Colombia). A connected highway for pelagic megafauna —
hammerheads, whale sharks, sea turtles — tracked by satellite
tagging. Featured in Tab 1 (globe), Tab 5 (Dive Lab), and
Tab 6 (Flora & Fauna).

**eDNA (Environmental DNA)**
Genetic material collected from environmental samples — water,
sediment, air — rather than directly from organisms. Traces of
DNA shed by organisms into their environment (via skin cells,
mucus, faeces) can be detected and identified by sequencing.
Revolutionising marine biodiversity surveys: a single water
sample can reveal every species present in an area without
capturing or even seeing a single animal. Featured in Tab 4
(Science — Ocean Technology) and Tab 6 (Flora & Fauna).

**Endemic**
A species found naturally only in a specific geographic
location and nowhere else on Earth. Marine endemism is rarer
than terrestrial endemism due to ocean connectivity. The
Galápagos Marine Reserve has 18.2% endemic marine species.
Shown with a gold badge in Tab 6.

**Epipelagic zone**
The ocean depth zone from 0 to 200m. Also called the sunlit
zone or photic zone. Where almost all marine photosynthesis
occurs. Home to coral reefs, most commercial fish species,
and the phytoplankton that produce half of Earth's oxygen.

---

### F

**Fendouzhe**
Chinese manned deep-sea submersible. Reached Challenger Deep
in November 2020 with a crew of three, to a depth of 10,909m.
Currently active. Operated by IDSSE.

**Five Deeps**
The expedition led by Victor Vescovo between 2018 and 2019 to
reach the deepest point in each of the world's five oceans,
using the submersible Limiting Factor. The first person to
dive all five. Set the record for the deepest manned dive at
10,928m in Challenger Deep.

---

### G

**Galápagos Marine Reserve**
A 133,000 km² UNESCO World Heritage marine reserve surrounding
the Galápagos Archipelago, Ecuador. Nearly 20% endemic marine
species. At the convergence of three ocean current systems —
Humboldt, Panama, and Cromwell. One of the two primary poles
of global marine biodiversity in Bathys alongside Raja Ampat.

**GEBCO (General Bathymetric Chart of the Oceans)**
The international authority for ocean bathymetric mapping.
Produces the GEBCO grid — a global seafloor elevation model
at 15 arc-second resolution — updated annually. The data
backbone of the Bathys globe. Joint project of IOC and IHO.
Data is open and free.

**GEOMAR**
Helmholtz Centre for Ocean Research, Kiel, Germany. One of
Europe's leading ocean research institutions. Operates RV
Sonne and RV Meteor.

**Gombessa**
The expedition series led by Laurent Ballesta, each focused
on solving a scientific mystery through extreme diving. Named
for the local name of the coelacanth in the Comoros Islands,
which Ballesta photographed at 120m depth.

---

### H

**Hadal zone**
The ocean depth zone below 6,000m. Found only in ocean
trenches. Characterised by extreme pressure (over 600
atmospheres), cold temperatures, and total darkness. Inhabited
by amphipods, snailfish, foraminifera, and xenophyophores.
Named from *bathys* — the same Greek root as the project name.

**Hass, Hans**
Austrian marine biologist, underwater filmmaker and diving pioneer.
Born 1919, died 2013. Developed rebreather diving technology and
underwater camera systems independently of and simultaneously with
Cousteau in the 1940s. Made some of the first underwater films,
including *Under the Red Sea* (1951). Conducted pioneering shark
behaviour research. The forgotten pioneer — his scientific
contributions were equal to Cousteau's but he received far less
international recognition. Featured in Tab 2 (Expeditions —
Researchers).

**Haldane model**
The first quantitative decompression model, developed by John
Scott Haldane and published in 1908 for the Royal Navy. Five
tissue compartments, the 2:1 supersaturation ratio rule. The
origin of all modern decompression theory. Included in the
Bathys decompression simulator as a historical educational
comparison.

**Heliox**
A breathing gas mixture of helium and oxygen, with no nitrogen.
Used in extreme deep diving to eliminate nitrogen narcosis.
Supported in the Bathys decompression simulator.

**HOV (Human-Occupied Vehicle)**
A manned submarine used for deep sea research. Examples: Alvin,
Nautile, Shinkai 6500, Limiting Factor, Fendouzhe. Contrast
with ROV, AUV.

**Hydrothermal vent**
A fissure in the seafloor from which geothermally heated water
emerges. Black smokers (sulfide-rich, up to 400°C) and white
smokers (silica-rich, cooler) are the two primary types.
Home to chemosynthetic ecosystems — life powered by chemical
energy rather than sunlight. Discovered in 1977 by Alvin.
Featured in Tab 4 (Science) and Tab 6 (Flora & Fauna).

---

### I

**IDSSE (Institute of Deep-sea Science and Engineering)**
Chinese Academy of Sciences institute, based in Sanya. Operates
Fendouzhe and Deep Sea Warrior submersibles. China's primary
deep-sea research institution.

**IFREMER (Institut Français de Recherche pour l'Exploitation
de la Mer)**
France's primary ocean research institution. Operates the
Nautile submersible, RV Pourquoi Pas? and L'Atalante. Co-led
the Titanic discovery with Ballard.

**Indonesian Throughflow**
The ocean current system that funnels warm Pacific water
through the Indonesian Archipelago into the Indian Ocean. One
of the most powerful current systems on Earth. Directly
responsible for the extreme marine biodiversity of Raja Ampat
by acting as a species highway between two oceans.

**IOC-UNESCO (Intergovernmental Oceanographic Commission)**
The United Nations body responsible for promoting international
cooperation in ocean science. Hosts the Ocean Decade (2021–2030)
and co-manages GEBCO.

**IUCN Red List**
The International Union for Conservation of Nature's global
assessment of species conservation status. Categories range
from Least Concern (LC) through Near Threatened, Vulnerable,
Endangered, Critically Endangered, to Extinct in the Wild and
Extinct. Used in every Bathys species card to show conservation
status.

---

### J

**JAMSTEC (Japan Agency for Marine-Earth Science and Technology)**
Japan's primary ocean and earth science institution. Operates
Shinkai 6500 (manned), Kaiko (ROV, first to full Challenger
Deep), and RV Kairei. World-class deep-sea research capability.

---

### L

**Limiting Factor**
The submersible used by Victor Vescovo in the Five Deeps
expedition. Built by Triton Submarines. Rated to full ocean
depth. Set the record for deepest manned dive at Challenger
Deep (10,928m) in 2019.

---

### M

**Marine snow**
The continuous shower of mostly organic material falling from
the upper ocean to the deep sea floor. Consists of dead
organisms, faecal matter, and organic aggregates. The primary
food source for deep-sea benthic communities and a major
vector of the biological pump.

**MBARI (Monterey Bay Aquarium Research Institute)**
A major US ocean research institution in Pacific Grove,
California. Operates ROVs Doc Ricketts and Ventana. Produces
extensive open-access deep-sea imagery. A credited data and
photography source for Bathys.

**Mesopelagic zone**
The ocean depth zone from 200m to 1,000m. Also called the
twilight zone or disphotic zone. The deep scattering layer —
billions of small organisms migrating vertically each day —
resides here. The least understood and most ecologically
important zone for carbon cycling.

**Mir-1 and Mir-2**
Soviet/Russian manned deep-sea submersibles operated by the
Shirshov Institute. Depth rating 6,000m. Dived to the Titanic,
the Bismarck, and under Arctic sea ice. Their mother ship is
the Akademik Mstislav Keldysh.

**MPA (Marine Protected Area)**
A geographically defined marine space managed to achieve
long-term conservation of nature. Currently 14,830+ MPAs
globally, covering approximately 8% of the ocean. Data source:
WDPA. Quality layer: MPA Atlas. Target: 30% by 2030.

**M-value**
In decompression theory, the maximum allowable supersaturation
pressure in a tissue compartment at a given depth. The boundary
defined by the Bühlmann ZHL-16C a and b coefficients for each
compartment. Exceeding the M-value risks bubble formation and
decompression sickness.

---

### N

**Nitrox**
A breathing gas mixture containing a higher percentage of
oxygen than air (21%), with the balance nitrogen. Common
recreational nitrox mixes are 32% and 36% oxygen. Extends
no-decompression limits at moderate depths by reducing
nitrogen loading. Supported in the Bathys decompression
simulator.

**NOC (National Oceanography Centre)**
The UK's primary ocean research institution, based in
Southampton. Operates RRS Discovery and RRS James Cook.

---

### O

**OBIS (Ocean Biodiversity Information System)**
The primary global database for marine species occurrence
records. Over 100 million records, 160,000+ species. Used in
Bathys species cards for occurrence distribution maps. License:
CC-BY. Managed by the IOC-UNESCO.

---

### P

**Pelagic**
Of or relating to the open ocean water column, as opposed to
the seafloor (benthic) or the coast. The pelagic zones —
epipelagic through hadal — are the primary depth classification
system used in Bathys.

**Phytoplankton**
Microscopic photosynthetic organisms in the ocean surface layer.
Responsible for approximately 50% of Earth's oxygen production.
The base of almost all marine food webs. Visualised in Bathys
via NASA satellite chlorophyll data.

**Pristine Seas**
A National Geographic Society project led by Enric Sala that
conducts scientific expeditions to the most remote ocean areas,
produces evidence for their protection, and works with
governments to establish marine protected areas. Has contributed
to the protection of over 6.6 million km² of ocean.

**PRD (Product Requirements Document)**
A Phase 2 document type. Makes the user-value argument for a
specific surface or feature. Not produced in concept phase.
Each user-facing surface in BA-02 becomes one PRD in Phase 2.

---

### R

**Raja Ampat**
An archipelago of approximately 1,500 islands in West Papua,
Indonesia, at the heart of the Coral Triangle. Contains over
550 species of reef-building corals (75% of all known species)
and over 1,800 species of reef fish. The most biodiverse
marine area on Earth. Featured in Tab 1 (globe), Tab 2
(Pristine Seas expeditions), Tab 5 (dive sites), and Tab 6
(Flora & Fauna).

**RFC (Request for Comments)**
A Phase 2 document type. Explores an open technical question
with alternatives and proposes a path forward. Closes into one
or more ADRs once a decision is made. No RFCs were required
from this concept package — all open questions were resolved
during concept phase.

**RGBM (Reduced Gradient Bubble Model)**
A decompression model developed by B.R. Wienke that extends
the Haldanean dissolved gas model with bubble mechanics. More
conservative on repetitive dives than Bühlmann. Used by NAUI
and some Suunto dive computers. The third model in the Bathys
decompression simulator.

**ROV (Remotely Operated Vehicle)**
An unmanned underwater vehicle tethered to a surface ship and
operated by a pilot at the surface via the tether. The primary
tool for deep-sea exploration and sampling. Examples: Jason
(WHOI), Hercules (OET), SuBastian (Schmidt), VICTOR 6000
(Ifremer). Contrast with AUV, HOV.

---

### S

**Sala, Enric**
Spanish marine biologist and National Geographic Explorer-in-Residence.
Born 1968. Founder and lead scientist of Pristine Seas — the
project that has contributed to the protection of over 6.6 million
km² of ocean through scientific expeditions to remote areas
followed by evidence-based advocacy for protection. Key figure
in the establishment of Galápagos-Cocos Swimway protections
and Revillagigedo National Park. Featured in Tab 2 (Expeditions
— Researchers) and linked throughout the MPA and biodiversity
content.

**Science Lens**
A cross-cutting feature of Bathys — a toggleable overlay
available in every tab that brings scientific annotations into
context. When active, physics annotations appear on dive
profiles, zone biology annotations appear on the globe, and
decompression physiology annotations appear on tissue compartment
bars. Each annotation links to Tab 4 Science for fuller
explanation. Implemented as a React context system.

**Shinkai 6500**
JAMSTEC's primary manned deep-sea research submersible.
Depth rating 6,500m. Operational since 1989. Has completed
over 1,500 dives. One of the most capable and productive HOVs
in the world.

**Shirshov Institute of Oceanology**
The primary ocean research institution of Russia, based in
Moscow. Home of the Mir submersible program. One of the oldest
and most decorated ocean research institutions in the world.
Extensive Pacific, Atlantic, and Arctic expedition history.

**SOFAR channel (Sound Fixing and Ranging channel)**
A layer in the ocean at approximately 600–900m depth where the
speed of sound reaches a minimum. Sound waves refract into this
channel and can travel thousands of kilometres without
significant loss of intensity. Exploited by whales to
communicate across ocean basins.

**SP-350 Denise (Diving Saucer)**
The first underwater vehicle designed expressly for scientific
exploration. Built by OFRS in France, operated by Cousteau
from 1959. Diameter 2.85m, depth rating 350m, crew of two.
Over 1,500 dives. Featured in Tab 3.

---

### T

**Thermohaline circulation**
The global ocean circulation system driven by differences in
water temperature and salinity. Also called the ocean conveyor
belt or AMOC (Atlantic Meridional Overturning Circulation) in
its Atlantic component. Regulates climate across the entire
planet by transporting heat from the tropics toward the poles.

**Thermocline**
A layer in the ocean where temperature decreases rapidly with
depth, separating warmer surface water from colder deep water.
A significant acoustic and thermal barrier. Used by submarines
for concealment. Featured in Tab 4 Science.

**Tissue compartment**
In decompression theory, a theoretical model of a body tissue
with a specific rate of gas uptake and release. Bühlmann ZHL-16C
uses 16 compartments with half-times ranging from 4 minutes
to 635 minutes. Each compartment is shown as a vertical bar
in the Bathys decompression simulator.

**Trimix**
A breathing gas mixture of oxygen, helium, and nitrogen. Used
in deep technical diving to reduce nitrogen narcosis (by
replacing some nitrogen with helium) while controlling oxygen
partial pressure. Supported in the Bathys decompression
simulator.

**Trieste**
The deep-diving bathyscaphe that carried Don Walsh and Jacques
Piccard to the bottom of Challenger Deep on 23 January 1960 —
the deepest point in the ocean. The first and, at the time,
only vessel to reach that depth. Built by Auguste Piccard.

---

### V

**VPM-B (Varying Permeability Model with Boyle's Law
compensation)**
A decompression model developed by David Yount that models
bubble nuclei formation rather than dissolved gas alone.
Produces deeper stops and shorter shallow stops compared to
Bühlmann. The second model in the Bathys decompression
simulator.

---

### W

**WDPA (World Database on Protected Areas)**
The authoritative global database of marine and terrestrial
protected areas. Joint project of UNEP-WCMC and IUCN. Updated
monthly. Contains 14,830+ MPAs as polygon geometries with
metadata. The data source for the MPA overlay in the Bathys
globe. License: open with attribution.

**WHOI (Woods Hole Oceanographic Institution)**
The primary US private ocean research institution, based in
Woods Hole, Massachusetts. Operates Alvin, Jason ROV, and RV
Atlantis. One of the most important ocean research institutions
in the world.

**WoRMS (World Register of Marine Species)**
The authoritative taxonomic register for all marine species.
Maintained at the Flanders Marine Institute. The canonical
source for marine species names, accepted/synonym status, and
classification hierarchy. Used in Bathys species cards for
taxonomy. License: CC-BY.

---

### X

**Xenophyophore**
A single-celled organism (foraminifera) found in the deep sea,
reaching up to 20cm in diameter — the largest single-celled
organisms on Earth. Found at abyssal and hadal depths.

---

### Z

**ZHL-16C**
See Bühlmann ZHL-16C.

---

*Bathys — BA-00 Introduction · v0.1 · May 2026*
*Concept Package complete · All six documents drafted · May 2026*
