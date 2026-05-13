# Bathys — Project Concept

## BA-02 · Project Concept

> v0.1 · Draft · May 2026
> The main concept document. Describes what Bathys is at the idea
> level — all surfaces, the full user journey, how everything
> connects. Written after BA-03 (Data Catalog), BA-04 (Technical
> Architecture), and BA-05 (Design System) are settled.
> A product manager, researcher, or collaborator reads this and
> understands the complete project.

---

## 1. What Bathys Is

Bathys is an interactive learning laboratory for the ocean — a
single web application that combines a real-data 3D globe, a
scientifically rigorous decompression simulator, a global
expedition and vessel catalog, a Cousteau heritage archive, a
full marine science center, and a species library into one
coherent place.

The name comes from the Greek root *bathys*: deep. It is the root
of bathyscaphe, bathymetry, the bathypelagic zone.

Bathys is built on the same philosophy as the orrery that preceded
it: that a single carefully made project can produce something that
feels like it came from a major institution. The orrery proved the
model for space. Bathys applies it to the ocean — a bigger subject,
a broader audience, and a more urgent story.

For the complete statement of why Bathys exists and who it is for,
see BA-01 (Vision). This document describes what it is and how it
works.

---

## 2. How Bathys Is Organised

Bathys is a single-page application with six primary tabs and two
supporting pages. The tabs are the six content sections. The
supporting pages — Credits and Library — are always accessible
from the navigation.

### The six tabs

| Tab | Name | Core idea |
|-----|------|-----------|
| 1 | **Ocean Globe** | The entry point. The whole planet, real data, every ocean layer toggleable. |
| 2 | **Expeditions** | The history of going underwater. Missions, vessels, submersibles, researchers. |
| 3 | **Cousteau** | A dedicated memorial to Jacques-Yves Cousteau — Calypso, the Conshelf stations, the Diving Saucer, the legacy. |
| 4 | **Science** | A full marine science center — six pillars, custom charts, interactive diagrams. |
| 5 | **Dive Lab** | The physics of diving, a real decompression simulator, and the world's top 100 dive sites. |
| 6 | **Flora & Fauna** | The species library — from phytoplankton to blue whales, from coral reefs to hydrothermal vent communities. |

### The two cross-cutting systems

**The depth-gradient visual system** runs through every tab.
The interface shifts colour register as content goes deeper —
surface turquoise through reef blue-green through indigo through
near-black. The user feels the descent. This is not cosmetic —
it is the primary expression of what Bathys is about. Full
specification in BA-05.

**The Science Lens** is a toggleable overlay available in every
tab. When active, scientific annotations appear in context — the
physics of pressure annotates the dive profile, ocean zone biology
annotates the globe, decompression physiology annotates the tissue
compartment bars. Science does not live only in Tab 4. It
permeates everything.

---

## 3. Tab 1 — Ocean Globe

### The concept

The Ocean Globe is the front door of Bathys and its most
technically ambitious surface. It is the first thing a user sees.
It earns its position by being genuinely beautiful and genuinely
informative simultaneously.

The globe is not a map. It is not a data visualisation in the
conventional sense. It is the planet, rendered at the fidelity
of real GEBCO bathymetric data, with the ocean doing what the
ocean actually does — moving, warming, harbouring life, being
protected in some places and exploited in others.

### What the user sees

A full-viewport Three.js globe, slowly auto-rotating. The
bathymetric depth gradient is immediately visible — continental
shelves in warm turquoise, mid-ocean in deep blue, abyssal plains
in near-black, the great trenches as dark scars. The Mid-Atlantic
Ridge is visible as a ridge. The Mariana Trench is visible as an
absence. The continental shelves of Southeast Asia are shallow
and complex. The Pacific is vast and dark.

No chrome on initial load. No cards, no sidebars, no instructions.
The planet fills the screen. The user begins by looking.

### Interaction

The globe responds to drag (rotate), scroll (zoom), and pinch
(mobile zoom). OrbitControls provide full orbital freedom — you
can look at the globe from any angle. A minimal HUD provides
zoom buttons and a reset view. Nothing else interrupts the
planetary view.

### The layer system

A compact floating panel offers toggle switches for overlay
layers. Each layer adds a dimension of data to the same globe:

**Ocean Currents** — a GPU-side particle system driven by CMEMS
current data. Particles flow along the actual surface current
vectors. The Gulf Stream is immediately recognisable as the
dominant North Atlantic feature. The Antarctic Circumpolar Current
circles the Southern Ocean. The Humboldt runs cold up the west
coast of South America. The Indonesian Throughflow — the most
biodiverse water on Earth — funnels between the islands. Each
current system is labelled on hover.

**Sea Temperature** — a colour wash overlaid on the globe showing
NOAA sea surface temperature. The warm pool of the tropical Pacific.
The cold upwelling off Peru and Namibia. The temperature gradient
between the Gulf Stream and the surrounding North Atlantic.

**Chlorophyll** — NASA satellite-derived phytoplankton density.
The North Atlantic spring bloom appears as a bright green surge
each year. The tropics are unexpectedly blue — warm, clear, and
largely empty of life. The Southern Ocean is intensely productive.
This layer is one of the most counter-intuitive and educational
in the system.

**Depth Zones** — the five ocean depth zones as coloured bands,
epipelagic through hadal, with a legend. The visual relationship
between depth and the globe's topographic colour is made explicit.

**Marine Protected Areas** — the complete WDPA dataset, 14,830+
MPA polygons colour-coded by IUCN protection category. At global
zoom, the distribution of protection is visible immediately —
dense in European waters and parts of the Pacific, sparse across
large swathes of the Indian Ocean and high seas. Zoom in and
individual reserves resolve. A progress counter below the layer
toggle shows the current global percentage of ocean effectively
protected and the 30x30 target.

**Biodiversity Hotspots** — marked locations of the world's
richest marine biodiversity. Raja Ampat and the Coral Triangle
as the dominant node. The Eastern Tropical Pacific corridor —
Galápagos, Cocos, Malpelo, Revillagigedo — as a connected chain.
The Red Sea, the Coral Sea, the Azores. Each marker opens a side
panel with the hotspot's key facts and a link into Flora & Fauna.

**Argo Floats** — live positions of the approximately 4,000
autonomous floats of the international Argo program. Each float
is a dot. Watching them drift with the currents over days makes
the concept of ocean monitoring tangible in a way that a
description cannot.

**Dive Sites** — the top 100 dive sites from the Dive Lab,
plotted as markers. Click any marker to see the site card and
open it in the Dive Lab.

### Click anything

Every marker and polygon on the globe is clickable. Clicking
opens a side panel — 380px from the right edge — with a card
for that feature. Cards contain: name, summary, key facts,
photography where available, and links into the relevant tab for
full content. The globe remains interactive behind the open panel.

Clicking into the Galápagos biodiversity hotspot opens a card
describing the marine reserve, the endemic species count, the
current system that makes it extraordinary, and a link to the
Galápagos content in Flora & Fauna. Clicking a Sha'ab Rumi MPA
polygon links directly to the Cousteau tab's Conshelf II chapter.
Every connection between the globe and the rest of Bathys is
surfaced through these click-through links.

### What makes it different

The globe is not a GIS viewer. It is not a generic Cesium or
Google Maps implementation. The visual language — the custom
depth gradient shader, the particle current system, the
bioluminescent markers in the abyssal zone — makes it feel like
a place made for Bathys, not a mapping library with data loaded.

---

## 4. Tab 2 — Expeditions

### The concept

The history of going underwater is one of the great stories of
the 20th century. Bathys treats it as such. The Expeditions tab
is a structured, browsable, globally representative catalog of
the people, vessels, and missions that have defined ocean
exploration.

The bias of most ocean exploration history is American. Bathys
corrects this deliberately. The Mir submersibles and Shirshov
Institute are as prominent as Alvin and WHOI. JAMSTEC's Shinkai
6500 is as prominent as Woods Hole's Jason ROV. Ifremer's Nautile
discovered the Titanic alongside Robert Ballard's team. China's
Fendouzhe reached Challenger Deep in 2020. The roster reflects
the global reality of ocean science.

### The timeline

A horizontal scrubable timeline runs across the top of the tab,
spanning from the 1930s bathysphere era to the present day.
Key events are marked as dots, sized by significance. Dragging
the timeline filters the card grid to the selected era.

Key timeline anchors:
- **1934** — Beebe and Barton descend to 923m in the bathysphere.
  The first time humans saw the deep ocean alive.
- **1943** — Cousteau and Gagnan co-invent the Aqua-Lung. Scuba
  diving becomes possible.
- **1960** — Walsh and Piccard reach the bottom of Challenger Deep
  in the Trieste. The deepest point on Earth, visited once and
  then not again for decades.
- **1977** — Alvin discovers hydrothermal vents and chemosynthetic
  life. One of the greatest biological discoveries of the 20th
  century.
- **1985** — Ballard and Michel discover the Titanic.
- **2012** — Cameron solos to Challenger Deep in DEEPSEA
  CHALLENGER. Built over seven years in Sydney.
- **2019** — Victor Vescovo completes the Five Deeps, visiting
  the deepest point in every ocean.
- **2020** — China's Fendouzhe reaches Challenger Deep.
- **Present** — Ongoing: Schmidt Ocean Institute, OceanX,
  Nautilus Live, JAMSTEC, Ifremer, AWI expeditions continue.

### Three sub-sections

**Missions & Expeditions**
The record of going there — what was attempted, what was found,
what was changed. Scope covers the full history from Haldane's
1908 Royal Navy decompression tables through present-day deep
sea biology expeditions. Each entry is a card: name, dates,
vessel, region, depth reached, key findings, photographs.

Featured entries include:
- The bathysphere dives (1930–1934) — Beebe and Barton
- The Calypso expeditions (1950–1996) — links to Tab 3
- Project Tektite (1969–1970) — NASA-funded saturation diving
- The Titanic discovery (1985) — Ballard, Michel, Argo, Alvin
- DEEPSEA CHALLENGER (2012) — Cameron, Allum, Acheron Project
- The Five Deeps (2018–2019) — Vescovo, Limiting Factor
- Pristine Seas missions — Sala, the protected area portfolio
- Current Schmidt Ocean Institute and OceanX expeditions

**Vessels & Submarines**
The machines that made it possible. Three categories:

*Research vessels* — the surface ships that serve as platforms,
laboratories, and homes. Featured vessels include:
- Calypso (France, 1950–1996) — links to Tab 3
- RV Atlantis (WHOI, USA) — Alvin's current mother ship
- RV Falkor (Schmidt Ocean Institute) — open science model
- RV Petrel (Vulcan Inc) — Paul Allen's legacy vessel
- RRS Discovery, RRS James Cook (NOC, UK)
- RV Sonne, RV Meteor (GEOMAR, Germany)
- RV Polarstern (AWI, Germany) — polar research
- Marion Dufresne (Ifremer, France)
- Akademik Mstislav Keldysh (Shirshov, Russia) — Mir's home
- Xuelong 2 (China) — polar icebreaker
- RV Kairei, RV Kaimei (JAMSTEC, Japan)

*Manned submersibles* — the vehicles that carried humans into the
deep. Each card includes: depth rating, year built, operator,
crew capacity, key dives, current status.
- Bathysphere (USA, 1930) — the beginning
- Trieste (USA/Switzerland, 1953) — Challenger Deep 1960
- SP-350 Denise / Diving Saucer (France, 1959) — links to Tab 3
- Alvin (USA, 1964) — still operating, hydrothermal vents, Titanic
- Mir-1 and Mir-2 (Russia, 1987) — Titanic, Arctic ice
- Nautile (France, 1984) — Ifremer's deep workhorse
- Shinkai 6500 (Japan, 1989) — 6500m depth rating
- Limiting Factor (USA, 2018) — Five Deeps, 10,928m
- DEEPSEA CHALLENGER (Australia/USA, 2012) — Cameron's solo dive
- Fendouzhe (China, 2020) — Challenger Deep
- Deep Sea Warrior (China, 2017)

*ROVs and AUVs* — the unmanned systems that have mapped and
sampled more of the deep ocean than all manned vehicles combined.
- Jason and Medea (WHOI) — the primary US deep ROV system
- Hercules and Argus (Ocean Exploration Trust) — Nautilus Live
- SuBastian (Schmidt Ocean Institute) — open science ROV
- Kaiko (JAMSTEC) — first unmanned vehicle to full Challenger Deep
- VICTOR 6000 (Ifremer) — French deep ROV
- Sentry (WHOI) — AUV, seafloor mapping
- Nereid Under Ice (WHOI) — under-ice exploration AUV

**Researchers & Explorers**
The people. A globally representative roster of the scientists,
engineers, divers, filmmakers, and advocates who have shaped
ocean exploration. Each entry is an editorial card: portrait
(illustrated where photography is unavailable), biography,
key expeditions, institutions, notable discoveries, links to
related expedition and vessel cards.

The roster is organised to correct the US-centric bias of most
ocean exploration history. Featured profiles include:

*Pioneers*
- Hans Hass (Austria) — co-developed rebreather diving and
  underwater camera technology independently of Cousteau in
  the 1940s. The forgotten pioneer.
- Jacques-Yves Cousteau (France) — links to Tab 3
- Don Walsh (USA) — Challenger Deep 1960 with Piccard
- Jacques Piccard (Switzerland) — Trieste, Challenger Deep
- Robert Ballard (USA) — Titanic, Argo, Jason development

*Active scientists*
- Sylvia Earle (USA) — Mission Blue, marine protection advocacy
- Antje Boetius (Germany) — deep sea microbiology, AWI director,
  polar research, anaerobic methane oxidation discovery
- Enric Sala (Spain) — Pristine Seas, marine protected areas
- Laurent Ballesta (France) — Gombessa expeditions, extreme
  diving, underwater photography, Wildlife Photographer of the
  Year 2021 and 2023
- Asha de Vos (Sri Lanka) — blue whale research, Indian Ocean,
  Oceanswell founder, ocean science diversity advocate
- Edith Widder (USA) — bioluminescence, first footage of giant
  squid alive
- Jon Copley (UK) — deep sea biology, hydrothermal vents,
  science communication
- Mensun Bound (UK) — maritime archaeology, Endurance discovery
- Victor Vescovo (USA) — Five Deeps, Limiting Factor
- Anatoly Sagalevitch (Russia) — Mir submersibles chief scientist
- Pinxian Wang (China) — deep sea geology, first Chinese ODP
  co-chief scientist, dived to 1400m at age 82

*Engineers*
- Ron Allum (Australia) — built Cameron's DEEPSEA CHALLENGER,
  engineering lead of Acheron Project Sydney
- James Cameron (Canada) — DEEPSEA CHALLENGER, solo Challenger
  Deep, the Titanic dives, bridge between filmmaking and science

---

## 5. Tab 3 — Cousteau

### The concept

Jacques-Yves Cousteau is not merely a historical figure in Bathys.
He is the emotional centre — the person who, more than any other,
changed the relationship between humanity and the ocean. The
Cousteau tab is a dedicated memorial, a living archive, and an
illustrated celebration of his work and its continuing influence.

The tab has its own visual register — warmer than the rest of
Bathys, with the Cousteau red accent (#FF6B35, his iconic beanie)
and calypso gold as secondary accents. It feels different from
the other tabs. That is deliberate. You are stepping into
someone's world.

### Six layers

**The Man**
A flowing editorial biography — not a Wikipedia summary, a
genuine telling of the story. Born 1910 in Saintonge. Naval
officer. The car accident in 1936 that broke his arms and turned
him toward swimming to rehabilitate them. That accident changed
ocean history. The collaboration with Émile Gagnan that produced
the Aqua-Lung in 1943. The purchase of Calypso from Loël Guinness
in 1950 for one dollar a year. The Palme d'Or at Cannes in 1956
for The Silent World. The decade of the Undersea World of Jacques
Cousteau (1966–1976) — watched by hundreds of millions. His
directorship of the Musée Océanographique de Monaco.

The biography includes his contradictions — early films show
dynamiting reefs and hunting marine life. He later deeply regretted
this and became one of the most important conservation voices of
the 20th century. His evolution from exploiter to protector is
part of the story, not hidden from it.

**Calypso — The Ship**
A dedicated section for Calypso, including the full illustrated
cutaway diagram of the vessel. A converted British Royal Navy
minesweeper (J826), built in 1942, purchased by Cousteau in 1950
for one dollar a year from Irish businessman Loël Guinness. Refitted
as a floating oceanographic laboratory in Antibes.

The cutaway illustration is annotated with hotspot labels:
- The bow observation chamber — below the waterline, portholes
  looking forward through the hull, used in The Silent World
- The main deck crane — which launched and recovered the SP-350
- The onboard laboratory and darkroom for film processing
- The helicopter deck added in 1960
- The crew quarters — home for up to 30 people on extended
  expeditions
- The dive deck at the stern

Key facts in monospaced data typography: 40m length, 400 tonnes,
built 1942, Antibes to global oceans. Calypso was sunk in Singapore
harbour in January 1996 when struck by a barge. She was raised and
has never been fully restored. Her final fate is an open note in
the section — honest about the loss.

**The SP-350 Diving Saucer**
A full illustrated profile of the Denise — the first underwater
vehicle designed expressly for scientific exploration.

Diameter 2.85m. Weight 3.5 tonnes. Crew of two, lying on
mattresses, watching through tilted portholes within centimetres
of the subject. Depth rating 350m. Propulsion by water jets,
drawing water in and expelling it through two steerable tubes —
the same principle as a squid. Mercury ballast for depth control.
A sampling arm. Multiple camera positions.

Over 1,500 dives across its lifetime. Launched from Calypso's
crane by a team of divers who guided it into the water. The
operational relationship between Calypso and the saucer — the
crane lift, the diver-assisted water entry, the recovery — is
described and illustrated as a sequence.

The later Sea Fleas — two one-person successor submersibles
built in 1965, capable of 500m — are also covered here as
direct descendants of the Denise.

**The Conshelf Stations**
Three chapters, told chronologically. This is the section that
most people don't know — that Cousteau built and inhabited
underwater villages, not just visited the deep from submersibles.

*Conshelf I — 1962, Marseille*
A steel cylinder 5m long, 2.5m in diameter, submerged 10m
underwater off the coast of Marseille in September 1962. Albert
Falco and Claude Wesly became the first humans to live underwater
for a week — seven days, sleeping, eating, working, spending
at least five hours per day outside exploring. The first proof
that extended subsea habitation was physiologically possible.

*Conshelf II — 1963, Sha'ab Rumi, Red Sea, Sudan*
The centrepiece. A multi-structure underwater village 11m deep
on a reef at Sha'ab Rumi, with a deeper station at 27m. The
village — five structures including the Starfish House — housed
five oceanauts for a month. The deeper station housed two divers
for a week. The saucer garage was an underwater hangar for the
SP-350, with service divers who could maintain it between dives.

A parrot was sent down as an atmospheric canary. The structure
of the habitat, the daily routine of the oceanauts, the logistics
of keeping five people alive at 11m depth for a month — all told
in detail. The film World Without Sun was made here and won the
Academy Award for Best Documentary in 1964.

The Conshelf II structures still exist at Sha'ab Rumi today —
encrusted in coral, fully intact, diveable. This is one of the
most extraordinary dive sites on Earth. Its Dive Lab card links
directly here from Tab 5.

*Conshelf III — 1965, Cap Ferrat, Mediterranean*
The most technically ambitious and the last. Six oceanauts at
102m depth, off the coast of Cap Ferrat between Nice and Monaco,
for three weeks. They performed industrial tasks on a mock oil
rig — the stated goal was to prove humans could perform productive
work at extreme depth. Philippe Cousteau was among the crew.

After Conshelf III, Cousteau moved away from habitat technology
and toward conservation. The political and funding reasons for
this shift are noted.

**The Calypso Journeys**
An illustrated world map in the nautical chart aesthetic. All of
Calypso's major expeditions shown as animated voyage lines —
each route draws itself as the user scrolls or as the expedition
is selected. Markers at key waypoints.

Clicking a waypoint opens a journey card: dates, region,
scientific objectives, key findings, crew, connection to films
or Conshelf activity. The Red Sea node connects to Conshelf II.
The Antarctic voyages connect to the polar Science content.

A timeline of voyages runs below the map, clickable. 1951 Red
Sea and Indian Ocean through 1994 final expeditions.

**The Legacy Thread**
A visual genealogy closing the tab. Cousteau to Jean-Michel
Cousteau (son, still active, founder of Ocean Futures Society)
to Fabien Cousteau (grandson, building the Proteus underwater
habitat — a 21st-century Conshelf). On a parallel line: Laurent
Ballesta as the cultural and scientific heir to the French
underwater exploration tradition — his Gombessa expeditions as
the living continuation of what Cousteau began.

---

## 6. Tab 4 — Science

### The concept

Tab 4 is the knowledge engine of Bathys. A full marine science
center — not a textbook, not a data portal, but a place where
every scientific concept connects to something visual, interactive,
or discoverable elsewhere in the application.

The Science Lens (available in every other tab) pulls from Tab 4
content. Every annotation the Lens applies elsewhere links back
to the relevant pillar here for fuller explanation.

### Structure

The tab opens with the ocean cross-section hero illustration —
the most complex and important graphic in the project. The full
water column from sea surface to the hadal trench, all five depth
zones shown, key organisms at correct depths, depth and pressure
indicators on the vertical axis. Hovering any zone highlights it.
Clicking navigates into that zone's biology content.

Six pillars, accessible via secondary navigation:

**Pillar 1 — Ocean Physics**

101 card: *"Every 10 metres underwater adds one full atmosphere
of pressure. At 40 metres you are breathing air compressed to
one fifth of its surface volume. At the bottom of the Mariana
Trench, the pressure is over 1,000 atmospheres."*

Custom diagrams:
- *Pressure gauge* — drag-to-explore. Drag the depth slider down
  and watch pressure climb. Human physiological effects annotated.
- *Colour absorption spectrum* — a vertical bar from surface to
  200m. Red gone at 5m, orange at 25m, yellow at 50m, green at
  100m. Below 200m only blue and violet penetrate. This is why
  Ballesta must carry artificial lights in his deep photographs.
- *Sound speed profile* — SOFAR channel highlighted as a natural
  acoustic waveguide. How whales communicate across ocean basins.
- *Thermocline cross-section* — why cold water sits below warm.
  Why submarines hide in thermoclines.

**Pillar 2 — Ocean Chemistry**

101 card: *"Seawater contains every naturally occurring element
on the periodic table. It is not just salty — it is a weak
solution of almost everything."*

Custom diagrams:
- *pH timeline* — pre-industrial (~8.2) through present (~8.1) to
  three 2100 scenarios. The 0.1 unit change: pH is logarithmic,
  representing a 26% increase in acidity.
- *Bioluminescence mechanism* — organism-level and molecular-level
  (luciferin/luciferase reaction). The most widespread form of
  communication on Earth, invisible because it happens in the dark.
- *Salinity variation map* — globe overlay. Saltiest: Mediterranean,
  Red Sea. Freshest: Baltic, near river outflows.

**Pillar 3 — Ocean Biology — Zones of Life**

The zone cross-section illustration is the primary navigation.
Five depth zones, each clickable:

*Epipelagic (0–200m) — the sunlit zone*
Where almost all photosynthesis happens. Coral reefs as the
most biodiverse ecosystems on the planet. Phytoplankton base of
the food web — responsible for half of Earth's oxygen production.

*Mesopelagic (200–1000m) — the twilight zone*
The deep scattering layer — billions of small organisms that rise
to the surface each night to feed and descend at dawn, creating
the largest daily animal migration on Earth. Their role in the
biological carbon pump is central to ocean climate science.

*Bathypelagic (1000–4000m) — the midnight zone*
No sunlight. Bioluminescence is the primary light source.
Anglerfish, dragonfish, viperfish. Where the giant squid lives
and hunts.

*Abyssal (4000–6000m) — the abyssal plain*
The vast flat floor of the deep ocean. Marine snow falls from
the zones above, feeding a sparse but persistent community.
The abyssal plain covers more of the Earth's surface than any
other environment.

*Hadal (6000m+) — the trenches*
Amphipods thriving under 1,000 atmospheres. Snailfish filmed
at 8,336m — the deepest fish ever recorded. Xenophyophores —
the largest single-celled organisms on Earth. And in the Mariana
Trench sediment: the highest concentrations of persistent organic
pollutants found anywhere in the biosphere.

**Pillar 4 — Ocean Geology**

101 card: *"The longest mountain range on Earth is entirely
underwater. The Mid-Atlantic Ridge stretches 16,000 kilometres
from the Arctic to the Southern Ocean, growing 2.5cm per year."*

Custom diagrams:
- *Plate tectonics map* — spreading ridges, subduction zones,
  hotspots, transform faults. The seafloor as a dynamic surface.
- *Hydrothermal vent cross-section* — animated. Superheated water
  (up to 400°C), mineral chimneys, chemosynthetic bacteria at the
  base of a food chain that has never seen sunlight.
- *Cold seep communities* — the parallel deep ecosystem.
- *Sediment core timeline* — a climate archive going back millions
  of years. How we know the history of ocean temperature and ice.

**Pillar 5 — Ocean & Climate**

101 card: *"The ocean has absorbed 90% of the excess heat
generated by human activity since 1970. It has also absorbed
about 30% of the CO₂ we have emitted. The question is how long
the ocean can continue to absorb at this rate."*

Custom diagrams:
- *Thermohaline conveyor belt* — the signature diagram. Animated,
  interactive slider to slow or stop the conveyor and see
  projected regional climate impacts.
- *Coral bleaching timeline* — real years for major bleaching
  events (1998, 2010, 2015–2016, 2022, 2024).
- *Sea level projections* — past 20,000 years to 2100, multiple
  emissions scenarios.
- *Ocean acidification* — CO₂ emissions, absorption, pH change,
  and coral/shellfish response as a connected causal chain.

**Pillar 6 — Ocean Technology**

101 card: *"We have better maps of the surface of the Moon
than of our own ocean floor. As of 2023, approximately 25% of
the ocean floor has been mapped at high resolution. The other
75% is estimated."*

Custom diagrams:
- *Tool spectrum diagram* — ocean observing technology plotted
  against depth, from satellites to hadal landers.
- *Multibeam sonar animation* — how a vessel's sonar swath maps
  the seafloor as the ship moves.
- *Argo float cycle* — one float's complete 10-day cycle.
- *eDNA technology* — how a water sample reveals every species
  present without capturing a single animal.

---

## 7. Tab 5 — Dive Lab

### The concept

The Dive Lab is the most technically unique tab in Bathys. Its
centrepiece — a decompression simulator built on real published
algorithms — does not currently exist anywhere as a free,
beautiful, educational tool. This is Bathys's most novel
contribution to the field.

The tab is explicitly not a dive planning tool. It is the science
behind the dive, made explorable. Divers use it to understand
what their dive computer is actually computing. Students use it
to learn decompression physiology. Curious non-divers use it to
understand why diving is physically complex and genuinely
dangerous when done wrong.

### Section 1 — Physics of Diving

Custom diagrams covering the physical environment of diving.
Depth, pressure, gas behaviour, light, sound, thermal effects.
Presented in diver-specific context — not "how the ocean works"
but "what the ocean does to you when you are in it."

Nitrogen narcosis, the Martini effect, individual variability.
The oxygen toxicity window shown as an interactive chart that
updates with the selected gas mix.

### Section 2 — Decompression Simulator

The centrepiece. Built on three real published decompression
algorithms: Bühlmann ZHL-16C, VPM-B, and RGBM. All coefficient
tables sourced from primary literature and cited inline in the
module code. Unit tests validate outputs against known published
dive profiles. Full specification in BA-04 Section 5.

**What the user experiences:**

On desktop, a three-panel canvas. The user draws a dive profile
by dragging — depth on the Y axis, time on the X axis. As they
draw, 16 tissue compartment bars update in real time, each
filling as nitrogen loads into the modelled tissue. Watching
the slow compartments continue to fill during a supposed ascent
is the core educational moment — this is why decompression
stops exist.

Gas mixes assigned to depth ranges by dragging gas cards onto
the profile. Air, nitrox, trimix, heliox, pure oxygen for
decompression stops.

The decompression schedule panel updates in real time. Switch
between Bühlmann, VPM-B, and RGBM and watch the schedule change.
The Haldane 1908 model is available as a fourth option for
historical comparison.

The freediving module shows O₂ depletion and CO₂ accumulation
during breath-hold. The shallow water blackout mechanism — why
hyperventilating before a freedive is lethal — explained with
a live simulation.

On mobile, preset depth profiles replace the free-draw canvas.
The tissue compartment display and deco schedule remain fully
functional.

### Section 3 — World Dive Sites

A focused map of the top 100 global dive sites. Filterable by
type: reef, wreck, wall, cave, blue hole, drift, cold water,
historic. Each site has a card with depth profile, species
highlights, best season, gallery, and decompression considerations.

A "Plan This Dive" button on any site card loads that site's
typical depth profile into the decompression simulator.

Featured sites in full detail:

*Eastern Tropical Pacific corridor*
Galápagos (Darwin and Wolf) — hammerhead schools, whale sharks
year-round. Cocos Island — remoteness, megafauna density.
Malpelo — silky sharks, vertical walls, the world's most remote
seriously dived site. Revillagigedo (Socorro) — giant manta rays,
humpback whales.

*Cousteau heritage sites*
Sha'ab Rumi, Sudan — the Conshelf II structures still intact at
11m and 27m, the saucer garage dome on the reef. One of the most
historically significant dive sites on Earth. Links directly to
Tab 3.

*Biodiversity*
Raja Ampat — the world's highest coral diversity. Tubbataha Reef
— Philippines, UNESCO. Great Barrier Reef nodes with current
health data.

*Wrecks*
SS Thistlegorm (Red Sea), Ghost Fleet of Chuuk Lagoon (60+ vessels),
USAT Liberty (Bali), The Yongala (Australia).

*Cold water and kelp*
Poor Knights Islands (New Zealand), Monterey Bay (USA), British
Columbia cold water sites.

---

## 8. Tab 6 — Flora & Fauna

### The concept

The species library of Bathys. A natural history museum layer
covering all marine life — from the microbes that produce half
the oxygen we breathe to the largest animal that has ever existed.

Four entry paths that lead to the same species cards: By Taxonomy,
By Depth Zone, By Geography, By Theme. The depth zone path is the
most distinctive — entering a depth zone shifts the interface to
the corresponding depth register.

Data backbone: OBIS (occurrence records), IUCN Red List
(conservation status), WoRMS (taxonomy), FishBase (fish data),
SeaLifeBase (non-fish data). Every species card cites its sources.

### Six content sections

**Marine Plants & Microbes**
Phytoplankton — approximately 50% of Earth's oxygen production,
base of almost all marine food webs. Diatoms, dinoflagellates,
coccolithophores. Seagrass meadows. Kelp forests with giant kelp
*Macrocystis pyrifera* growing 30cm per day. Mangroves.

**Invertebrates**
Corals — hard and soft, their animal nature, bleaching mechanism.
Cephalopods — the giant squid *Architeuthis dux* finally filmed
alive by JAMSTEC in 2004. The immortal jellyfish *Turritopsis
dohrnii*. Echinoderms, crustaceans, sponges — including glass
sponge individuals potentially thousands of years old.

**Fish**
Sharks: 500+ species, the 17cm dwarf lanternshark to the 12m
whale shark. The Greenland shark living 400 years. 37% of shark
species now threatened, shown as an IUCN status breakdown.
The corridor sites as their refuge.

The blobfish properly explained — a normal deep pressure fish
that only collapses into its famous appearance at the surface.

The ocean sunfish *Mola mola* — the heaviest bony fish alive,
up to 2.3 tonnes, living on jellyfish.

**Marine Mammals**
The blue whale — the largest animal ever to exist. 30 metres,
up to 190 tonnes. The Asha de Vos connection: the northern
Indian Ocean population that does not migrate.

The sperm whale — deepest diving mammal, over 2km, 90 minutes
breath-hold, hunting giant squid in total darkness.

The vaquita — fewer than 10 individuals remaining. The most
critically endangered marine mammal and likely the next marine
extinction.

**Marine Reptiles & Birds**
Seven sea turtle species, all threatened or endangered. Their
magnetic-field navigation. The Galápagos marine iguana — the
only aquatic lizard on Earth. The wandering albatross with a
3.5m wingspan.

**Deep Sea & Extremophiles**
Hydrothermal vent communities — discovered 1977, one of the
greatest biological discoveries of the 20th century. Life powered
by chemosynthesis. Tube worms 3m long. Yeti crabs. Vent shrimp.

Each known major vent field mapped with its discovery date and
the expedition that found it.

Hadal species: the snailfish, the amphipods, the foraminifera.
And the disturbing Five Deeps finding: amphipods at Challenger
Deep with PCB concentrations higher than the most polluted rivers
in China. The deep ocean is not separate from what we put above.

### The endemism thread

A recurring gold endemic badge wherever a species is found only
in one place. An endemic species counter for each major
biodiversity hotspot on the Geography filter view.

---

## 9. Cross-Cutting Systems

### Science Lens

A persistent toggle button in the navigation (lens icon). When
active, scientific annotations appear in context throughout the
application. Each annotation is a floating panel in the
bathypelagic register — dark, precise, small — with a link
to the relevant Tab 4 pillar.

Implementation: React context. Each tab component subscribes to
the Lens state and renders its own annotations. The Science tab
does not inject annotations into other tabs — each tab is
responsible for its own annotation layer. See BA-04 OQ-04 (resolved).

### Depth register transitions

The depth register is a section-level CSS attribute. When the
user navigates to a deeper section, the register transitions
over 1200ms. Background colour shifts slowly. Text colour
crossfades. The effect is a descent, not a page change.

### Credits & Library

Two supporting pages, always accessible from the navigation.

**Credits** — data-driven, rendering from structured JSON.
Every institution, dataset, photograph, algorithm, and paper
traced back to its origin. The audit trail of Bathys.

**Library** — the reading room. Curated books, documentaries,
institutions to follow, journals. Organised by section of Bathys.

---

## 10. User Journeys

Three primary audience journeys, from BA-01.

**The curious non-specialist**
Arrives at the globe. Enables the current layer and watches the
Gulf Stream. Clicks into the Galápagos hotspot. Reads the side
panel, follows the link to Flora & Fauna. Spends twenty minutes
in the shark section. Follows the Enric Sala link to the Pristine
Seas expeditions in Tab 2. Reads the Cousteau biography. Has not
thought about the ocean this way before. Returns.

**The diver**
Arrives at the Dive Lab. Runs a familiar dive profile — their
last Thistlegorm dive, 32m for 45 minutes. Watches the tissue
compartment bars fill in real time and recognises the pattern
from their dive computer. Switches from Bühlmann to VPM-B and
sees the stop schedule change. Runs the same dive on nitrox 32
and watches the bottom time extend. Discovers the oxygen toxicity
curve explained visually for the first time. Finds the Cocos
Island dive site card, clicks "Plan This Dive", links through to
Galápagos and Cocos content in Flora & Fauna.

**The student or researcher**
Arrives at Tab 4 Science. Checks the Bühlmann coefficient table
in the source code (linked from Credits). Finds the primary paper
citation — Bühlmann 2002 — and follows the DOI. Returns to
explore the hydrothermal vent section. Finds the 1977 Alvin
expedition in Tab 2 with crew names and discovery documentation.
Uses the species card for *Riftia pachyptila* to find OBIS
occurrence data. Notes MBARI credited with data license.
Considers the project citable.

---

## 11. What Bathys Is Not

Following the process guide's "not a" discipline:

| Not a... | Because... |
|----------|-----------|
| **Dive planning software** | Bathys does not save dive plans, does not connect to dive computers, does not compete with Subsurface, Garmin Dive, or Shearwater Cloud. It is the science behind the dive, not the operational tool. |
| **Conservation campaign** | Bathys presents the conservation data honestly and completely. It does not advocate for a specific position or organisation. The 30x30 progress bar is a fact, not a call to action. |
| **Species identification app** | Bathys does not support photo identification, field notes, or dive logging. It is a reference and learning tool, not a field companion. |
| **Encyclopaedia** | Bathys covers approximately 2,000 species in full cards, not 200,000. Coverage is curated, not comprehensive. The OBIS and FishBase APIs provide the long tail for specific queries. |
| **Academic journal** | Bathys cites primary literature and uses real data. It is not peer-reviewed. The Credits page distinguishes between data sources, scientific literature, and curated content. |
| **Tourism site** | Bathys lists the top 100 dive sites with honest depth and decompression information. It does not promote dive operators, liveaboards, or specific travel products. |

---

*Bathys — BA-02 Project Concept · v0.1 · May 2026*
