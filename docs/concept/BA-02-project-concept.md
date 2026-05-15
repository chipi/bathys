# Bathys — Project Concept

## BA-02 · Project Concept

> v0.2 · Draft · May 2026
> Updated: mission card template and vessel card template added;
> fleet entries and fleet concept introduced; habitats added as
> fifth vessel type with four dedicated sections (Sealab, Tektite,
> Aquarius, DEEP); Cousteau tab expanded to six layers.

---

## 1. What Bathys Is

Bathys is an interactive learning laboratory for the ocean — a
single web application combining a real-data 3D globe, a
scientifically rigorous decompression simulator, a global
expedition and vessel catalog, a Cousteau heritage archive, a
full marine science center, and a species library.

Built on the same philosophy as the orrery that preceded it.
See BA-01 (Vision) for the full statement of why Bathys exists
and who it is for. This document describes what it is and how
it works.

---

## 2. How Bathys Is Organised

Six primary tabs, two supporting pages (Credits and Library).

| Tab | Name | Core idea |
|-----|------|-----------|
| 1 | **Ocean Globe** | The entry point. The whole planet, real data, every ocean layer toggleable. |
| 2 | **Expeditions** | The history of going underwater. Missions, vessels, habitats, researchers. |
| 3 | **Cousteau** | Dedicated memorial — Calypso, Conshelf, Diving Saucer, the legacy. |
| 4 | **Science** | Full marine science center — six pillars, custom charts, interactive diagrams. |
| 5 | **Dive Lab** | The physics of diving, decompression simulator, top 100 dive sites. |
| 6 | **Flora & Fauna** | The species library — from phytoplankton to blue whales. |

**The depth-gradient visual system** runs through every tab.
The interface shifts colour register as content goes deeper.
Full specification in BA-05.

**The Science Lens** is a toggleable overlay available in every
tab. Scientific annotations appear in context. Science does not
live only in Tab 4 — it permeates everything.

---

## 3. Tab 1 — Ocean Globe

The front door of Bathys. Full-viewport Three.js globe, slowly
auto-rotating. Bathymetric depth gradient immediately visible —
continental shelves in warm turquoise, mid-ocean in deep blue,
the great trenches as dark scars.

No chrome on initial load. The planet fills the screen.

**Layer system** (compact floating panel, bottom-left):

- **Ocean Currents** — GPU particle system driven by CMEMS data. Gulf Stream, Humboldt, Antarctic Circumpolar, Indonesian Throughflow all legible on hover.
- **Sea Temperature** — NOAA sea surface temperature colour wash.
- **Chlorophyll** — NASA satellite phytoplankton density. The North Atlantic spring bloom. The unexpectedly blue tropics.
- **Depth Zones** — five ocean depth zones as coloured bands.
- **Marine Protected Areas** — complete WDPA dataset, 14,830+ polygons, colour-coded by IUCN category. 30x30 progress counter.
- **Biodiversity Hotspots** — Raja Ampat / Coral Triangle, Eastern Tropical Pacific corridor, Red Sea, Coral Sea, Azores.
- **Argo Floats** — live positions of ~4,000 autonomous floats.
- **Dive Sites** — top 100 sites from the Dive Lab.

Clicking any marker or polygon opens a side panel (380px from
right edge) with a feature card and links into the relevant tab.

---

## 4. Tab 2 — Expeditions

The history of going underwater. Globally representative —
deliberately correcting the US-centric bias of most ocean
exploration history.

**The timeline** — horizontal, scrubable, 1930s to present.
Key events as sized dots.

**Four sub-sections:** Missions & Expeditions, Vessels &
Submarines, Habitats, Researchers.

---

### Missions & Expeditions

Each entry is a structured mission card answering:

- *The question* — what scientific or exploratory question motivated this mission
- *Who* — lead researchers, institution, vessels deployed
- *When* — date range, phase structure for multi-phase programs
- *Where* — region, depth, geographic scope
- *What happened* — key events narrative, including failures
- *What changed* — the specific discovery or outcome. Why this mission matters.
- *Status* — Complete / Active / Ongoing program
- *Links* — vessels, researchers, dive sites, species discovered

Featured entries: bathysphere dives (1930–34), Calypso expeditions,
Project Tektite, Titanic discovery, DEEPSEA CHALLENGER, Five Deeps,
Pristine Seas missions, current Schmidt and OceanX expeditions.

---

### Vessels & Submarines

Five categories of vessel cards. Fleet entries as a special
wider card type providing institutional context.

**Vessel card template fields:**
- Type (Research vessel / HOV / ROV / AUV / Habitat)
- Builder, operator, commission/active dates
- Technical specs (length, displacement, depth rating, endurance)
- Deployment method
- Mother ship → deployed vehicle relationship (visual diagram)
- Fleet membership (link to Fleet entry)
- Key missions (3–5, linked)
- Current status
- Significance — what this vessel contributed that no other could

**Research vessels** (tagged to their fleets):
Calypso · RV Atlantis · RV Falkor · RV Petrel · RRS Discovery ·
RRS James Cook · RV Sonne · RV Meteor · RV Polarstern ·
Marion Dufresne · Akademik Mstislav Keldysh · Xuelong 2 ·
RV Kairei · RV Kaimei

**Manned submersibles:**
Bathysphere · Trieste · SP-350 Denise (Tab 3 link) · Alvin ·
Mir-1 and Mir-2 · Nautile · Shinkai 6500 · Limiting Factor ·
DEEPSEA CHALLENGER · Fendouzhe · Deep Sea Warrior

**ROVs and AUVs:**
Jason and Medea · Hercules and Argus · SuBastian · Kaiko ·
VICTOR 6000 · Sentry · Nereid Under Ice

---

### Underwater Habitats

Not vehicles — places. The parallel to the orrery's space stations
concept is exact: permanent human presence in a hostile environment,
sustained by life support, enabling science only possible by being
there. NASA has used underwater habitats as space analogues since
1969 — the connection is operational, not metaphorical.

Four habitats receive **dedicated sections** equivalent to the
orrery's space station treatment. Remaining habitats are standard
cards. Conshelf habitats (dedicated in Tab 3) are cross-referenced
here only.

---

**DEDICATED SECTION 1 — Sealab I, II, and III**

Three acts. One program. A clean arc from ambition through triumph
to tragedy.

*Act I — Sealab I (1964, 58m, Bermuda, 4 aquanauts, 11 days)*
The US Navy's answer to Conshelf. Running simultaneously with
Conshelf, almost entirely forgotten. Sealab I proved the concept.

*Act II — Sealab II (1965, 62m, La Jolla, 3 teams of 10, 45 days)*
Scott Carpenter — one of the original Mercury Seven astronauts —
volunteered to be an aquanaut. He spoke by phone from the habitat
floor to Gordon Cooper, then orbiting in Gemini 5. An astronaut
on the ocean floor, another in space, talking in real time. No
single moment makes the ocean-space parallel more visceral.

A porpoise named Tuffy was trained to carry tools between surface
and habitat and to find aquanauts in simulated emergencies.

*Act III — Sealab III (1969, 185m attempted, La Jolla)*
Diver Berry Cannon died during the attempt to fix a helium leak
before the aquanauts could enter. He was 33. The program was
cancelled. 185m remained the deepest habitat attempt in history
for fifty-six years. DEEP Sentinel plans to exceed it in 2027.

*Illustrated content:* Cutaway of Sealab II; the phone call moment
as an illustrated panel; Tuffy; depth timeline against Conshelf III
and Sentinel planned.

*Fleet tag:* `us-navy-sealab-program`

---

**DEDICATED SECTION 2 — Tektite I and II**

NASA funded an underwater habitat to study team psychology and
physiology for long-duration space missions. Explicit purpose: not
ocean science — space preparation.

*Tektite I (1969, 15m, US Virgin Islands, 4 aquanauts, 60 days)*
Data contributed directly to space station crew schedule design
and psychological support systems.

*Tektite II (1970, 10 sequential missions)*
Mission 6: five aquanauts, all women, led by Sylvia Earle.
Fourteen days at depth. 1970.

When male crews surfaced they were met by the Governor of the
Virgin Islands. When Earle's team surfaced, the press conference
asked whether they had argued among themselves, missed their
hair dryers, and who did the cooking.

Earle's answer — patient, measured, describing the science they
had done — was the moment that defined the next fifty years of
her career. The through-line from Tektite Mission 6 to Mission
Blue, her NOAA tenure, and her position as the ocean's most
prominent living advocate is direct and documented.

*Illustrated content:* Twin Tektite cylinder cutaway; Tektite II
mission timeline with Mission 6 highlighted; portrait panel of
the five Mission 6 scientists.

*Fleet tag:* `nasa-tektite-program`

---

**DEDICATED SECTION 3 — Aquarius Reef Base**

Florida Keys National Marine Sanctuary, 19m depth, since 1987.
Six aquanauts, missions of ten to fourteen days. Ambient pressure —
6 atmospheres — means nine hours per day outside on the reef.
A standard scuba dive to 19m gives forty minutes. An Aquarius
mission gives nine hours per day for ten days.

*NASA NEEMO* — NASA Extreme Environment Mission Operations. Since
2001, astronaut crews train at Aquarius for spacewalks, robotic
operations, and long-duration mission psychology. The communication
delay, slow deliberate movement, isolation, suit-like constraints
of dive equipment all map onto EVA training. Crews who trained
here went on to conduct EVAs from the ISS. Simultaneously a marine
biology field station and an astronaut training ground.

*The 2014 moment* — Fabien Cousteau spent thirty-one days at
Aquarius, breaking his grandfather's Conshelf record. Three
generations connected by the same idea, in the same body of water.

*Illustrated content:* Aquarius cutaway on seafloor; NEEMO panel;
depth comparison chart tracking all habitats from Tektite to Sentinel.

---

**DEDICATED SECTION 4 — DEEP: Vanguard and Sentinel**

*The fifty-six year gap*
From Sealab III in 1969 to Vanguard in 2025: no new underwater
habitat was built. For more than half a century, living underwater
was a historical curiosity rather than an active program.

*Vanguard — in the water now*
12m × 7.5m, crew of four, a week or more. Unveiled in Miami,
October 2025. Deployed off the Florida Keys — the same waters
as Aquarius. The first new subsea habitat in nearly forty years.

Inside: banquettes that convert to bunks, a microwave, a French
press, crockery. Functional and economical. Until you look at
the door — a massive steel disc with a wheel that spins to lock.
And below the wet porch, the moon pool: a permanent opening in
the floor that doesn't flood because the air pressure inside
matches the water outside.

DNV classified. Built with Triton Submarines — who built Vescovo's
Limiting Factor. The deep ocean engineering community is small
and connected.

*Sentinel — the ambition*
Modular: 6m-wide modules connecting into stations of varying
scale. Eight crew in a small configuration — same as the ISS.
Fifty people in a large one. Depths up to 225 metres. Planned
for 2027.

225m is deeper than any habitat has ever operated. Deeper than
Sealab III attempted in 1969. At 225m — 23 atmospheres — the
aquanauts breathe helium-oxygen trimix.

DEEP makes the ISS comparison explicitly: when the International
Space Station launched in November 2000, it drove research,
capital, and inspiration for an entire generation. DEEP believes
Sentinel can do the same for the ocean.

*The closing line:*
Conshelf I, 1962: 10m, 2 aquanauts, 7 days, a steel cylinder the
size of an elevator. Sentinel, 2027: 225m, 50 aquanauts, permanent.
Sixty-five years. The same idea, finally at the scale it always
deserved.

*Illustrated content:* Scale comparison of all habitats drawn to
the same scale; Sentinel great hall interior render; Vanguard
moon pool cross-section; vertical depth profile with Sealab III's
"never reached" marker as a dashed line.

*Fleet tag:* `deep-program`

---

**Card-only habitats:**
- *Ben Franklin mesoscaphe (1969)* — Piccard fils, 30 days drifting the Gulf Stream. Card only.
- *Hydrolab (1966–1985)* — 19 years, 700+ scientists. Scientific workhorse. Card only.
- *Proteus (planned)* — Fabien Cousteau, Yves Béhar, Curaçao. Card only until built.
- *Conshelf I, II, III* — dedicated sections in Tab 3. Cross-reference cards here.

---

**Fleet entries** are a special wider card type in the vessel grid.
They explain the institutional program and link to all member
vessels. Not a navigation level — an index card providing context.

11 planned fleet entries:

*Cousteau Fleet* — Calypso, SP-350, Sea Fleas, Conshelf I/II/III.
*WHOI Fleet* — RV Atlantis, Alvin, Jason/Medea, Sentry, Nereid.
*JAMSTEC Fleet* — RV Kairei, Shinkai 6500, Kaiko.
*Ifremer Fleet* — Marion Dufresne, Nautile, VICTOR 6000.
*Shirshov Fleet* — Akademik Mstislav Keldysh, Mir-1, Mir-2.
*Chinese Deep Sea Fleet* — Xuelong 2, Fendouzhe, Deep Sea Warrior.
*Schmidt Fleet* — RV Falkor, SuBastian. Open science model.
*NOC / UK Fleet* — RRS Discovery, RRS James Cook, Autosub.
*US Navy Sealab Program* — Sealab I, II, III.
*NASA Tektite Program* — Tektite I, Tektite II.
*DEEP Program* — Vanguard, Sentinel.

---

### Researchers & Explorers

Globally representative roster. Each entry is an editorial card:
portrait, biography, key expeditions, notable discoveries,
links to related vessel and expedition cards.

*Pioneers:* Hans Hass (Austria) · Jacques-Yves Cousteau (France, links to Tab 3) · Don Walsh (USA) · Jacques Piccard (Switzerland) · Robert Ballard (USA)

*Active scientists:* Sylvia Earle (USA) · Antje Boetius (Germany) · Enric Sala (Spain) · Laurent Ballesta (France) · Asha de Vos (Sri Lanka) · Edith Widder (USA) · Jon Copley (UK) · Mensun Bound (UK) · Victor Vescovo (USA) · Anatoly Sagalevitch (Russia) · Pinxian Wang (China)

*Engineers:* Ron Allum (Australia) · James Cameron (Canada)

---

## 5. Tab 3 — Cousteau

The emotional centre of Bathys. A dedicated memorial and illustrated
celebration. Its own visual register (Register 5): warmer, with
Cousteau red (#FF6B35) and calypso gold accents.

### Six layers

**The Man** — Flowing editorial biography. Born 1910 Saintonge.
The 1936 car accident that turned him toward swimming. The
Aqua-Lung co-invented with Gagnan in 1943. Calypso purchased
for one franc per year from Loël Guinness in 1950. Palme d'Or
at Cannes in 1956. His evolution from exploiter to conservationist.

**Calypso — The Ship** — Full illustrated cutaway. Converted
Royal Navy minesweeper J826. Annotated hotspot labels: bow
observation chamber, main deck crane (SP-350), laboratory,
helicopter deck, crew quarters, dive deck. Calypso sunk in
Singapore January 1996. Her final fate noted honestly.

**The SP-350 Diving Saucer** — Full illustrated profile of the
Denise. Diameter 2.85m. Depth rating 350m. Crew of two on
mattresses. Water jet propulsion (squid principle). Mercury
ballast. Over 1,500 dives. The operational relationship between
Calypso and the saucer described and illustrated as a sequence.
The later Sea Fleas (500m, one-person) as direct descendants.

**The Conshelf Stations** — Three chapters:

*Conshelf I (1962, Marseille)* — 5m × 2.5m cylinder, 10m depth,
Albert Falco and Claude Wesly, 7 days. First proof of extended
subsea habitation.

*Conshelf II (1963, Sha'ab Rumi, Red Sea)* — The centrepiece.
Starfish House at 11m, deeper station at 27m, saucer garage.
Five oceanauts for a month. A parrot as atmospheric canary.
*World Without Sun* won Academy Award for Best Documentary 1964.
Conshelf II structures still exist on the reef today, diveable.
Dive Lab card links here.

*Conshelf III (1965, Cap Ferrat)* — Six oceanauts at 102m for
three weeks. Industrial tasks on a mock oil rig. Philippe
Cousteau among crew. After this, Cousteau turned toward
conservation.

**The Calypso Journeys** — Illustrated world map, nautical chart
aesthetic. Voyage lines animate as user scrolls. Clickable
waypoints open journey cards. Timeline below. 1951 Red Sea
through 1994 final expeditions.

**The Legacy Thread** — Cousteau → Jean-Michel → Fabien (building
Proteus). Ballesta on a parallel line as cultural heir.

---

## 6. Tab 4 — Science

The knowledge engine of Bathys. The Science Lens pulls from Tab 4
content and annotates every other tab.

Opens with the ocean cross-section hero illustration — the most
complex graphic in the project. Full water column, all zones,
organisms at correct depths, interactive zone navigation.

**Six pillars** (secondary navigation):

**1 — Ocean Physics** — 101 card + pressure gauge (drag-to-explore), colour absorption spectrum, sound speed profile (SOFAR channel), thermocline cross-section.

**2 — Ocean Chemistry** — 101 card + pH timeline (pre-industrial to 2100 scenarios), bioluminescence mechanism, salinity variation globe overlay.

**3 — Ocean Biology — Zones of Life** — Zone cross-section as primary navigation. Five zones clickable: epipelagic, mesopelagic (deep scattering layer, biological pump), bathypelagic, abyssal, hadal (PCB concentrations in Challenger Deep amphipods).

**4 — Ocean Geology** — 101 card + plate tectonics map, hydrothermal vent cross-section (animated), cold seep communities, sediment core timeline.

**5 — Ocean & Climate** — 101 card + thermohaline conveyor belt (animated, interactive slider), coral bleaching timeline, sea level projections, ocean acidification causal chain.

**6 — Ocean Technology** — 101 card + tool spectrum diagram (all technology types by depth), multibeam sonar animation, Argo float cycle, eDNA technology.

---

## 7. Tab 5 — Dive Lab

The most technically unique tab in Bathys. The decompression
simulator does not exist anywhere as a free, beautiful, educational
tool. Explicitly not a dive planning tool.

**Section 1 — Physics of Diving** — Nitrogen narcosis (Martini effect), oxygen toxicity window (interactive chart updating with gas mix selection), pressure, light, sound, thermal effects in diver-specific context.

**Section 2 — Decompression Simulator**

Desktop: three-panel canvas.
- Left: Dive Plan Builder (drag-to-draw depth/time profile, gas cards dragged to depth ranges)
- Centre: 16 Tissue Compartment bars (Bühlmann compartments, real-time fill, ceiling shown)
- Right: Deco Schedule (updates real-time, model selector: ZHL-16C / VPM-B / RGBM / Haldane 1908)

Mobile: preset depth profiles via swipeable card picker. All three panels fully functional stacked vertically.

Freediving module: O₂ depletion and CO₂ accumulation during breath-hold. Shallow water blackout mechanism with live O₂ curve simulation.

**Section 3 — World Dive Sites** — Top 100 sites. Filter by type. "Plan This Dive" button loads site's depth profile into simulator.

Featured: Eastern Tropical Pacific corridor (Galápagos, Cocos, Malpelo, Revillagigedo) · Sha'ab Rumi/Conshelf II (links to Tab 3) · Raja Ampat · Tubbataha · Thistlegorm · Chuuk Lagoon · USAT Liberty · The Yongala · Poor Knights · Monterey Bay.

---

## 8. Tab 6 — Flora & Fauna

The species library. Four entry paths: By Taxonomy, By Depth Zone,
By Geography, By Theme. Entering a depth zone shifts the interface
to the corresponding depth register.

Data backbone: OBIS, IUCN Red List, WoRMS, FishBase, SeaLifeBase.
Every species card cites its sources.

**Six content sections:**

**Marine Plants & Microbes** — Phytoplankton (50% of Earth's O₂), diatoms/dinoflagellates/coccolithophores, seagrass, kelp forests (*Macrocystis pyrifera*, 30cm/day), mangroves.

**Invertebrates** — Corals (animal, not plant; bleaching mechanism), cephalopods (*Architeuthis dux* filmed alive by JAMSTEC 2004), immortal jellyfish *Turritopsis dohrnii*, echinoderms, crustaceans, glass sponges (potentially thousands of years old).

**Fish** — Sharks (500+ species; 37% threatened; IUCN breakdown; corridor sites as refuge). Blobfish properly explained — a normal deep fish, only collapses at surface. *Mola mola* — heaviest bony fish, up to 2.3 tonnes.

**Marine Mammals** — Blue whale (largest animal ever, 30m, 190t). Asha de Vos connection: northern Indian Ocean population doesn't migrate. Sperm whale (2km+ depth, 90-minute breath-hold, giant squid in darkness). Vaquita (fewer than 10 remaining).

**Marine Reptiles & Birds** — Seven sea turtle species (magnetic navigation). Galápagos marine iguana (only aquatic lizard). Wandering albatross (3.5m wingspan).

**Deep Sea & Extremophiles** — Hydrothermal vents (discovered 1977, Alvin). Chemosynthesis. Tube worms, yeti crabs, vent shrimp. Each known vent field mapped with discovery date and expedition. Hadal species. PCB concentrations in Challenger Deep amphipods.

**The endemism thread** — Gold endemic badge on endemic species. Counter per biodiversity hotspot. 18.2% endemism in Galápagos.

---

## 9. Cross-Cutting Systems

**Science Lens** — React context. Each tab subscribes and renders its own annotations. Floating panels in bathypelagic register. Links to Tab 4 for full explanation.

**Depth register transitions** — Section-level CSS attribute, 1200ms transition. The effect is a descent, not a page change.

**Credits** — Data-driven page from JSON. Every institution, dataset, photograph, algorithm, and paper traceable. See BA-06 for the full provenance system.

**Library** — Curated reading room. Organised by Bathys section.

---

## 10. User Journeys

**The curious non-specialist** — Globe → Gulf Stream current → Galápagos hotspot → Flora & Fauna shark section → Sala/Pristine Seas in Tab 2 → Cousteau biography.

**The diver** — Dive Lab → Thistlegorm 32m/45min profile → tissue bars recognisable from dive computer → Bühlmann vs VPM-B comparison → nitrox 32 bottom time extension → oxygen toxicity curve explained visually → Cocos Island "Plan This Dive".

**The student or researcher** — Tab 4 Science → Bühlmann coefficient table in source code (Credits link) → DOI to Bühlmann 2002 → 1977 Alvin expedition in Tab 2 → *Riftia pachyptila* OBIS occurrence data → MBARI credited with data license. Considers the project citable.

---

## 11. What Bathys Is Not

| Not a... | Because... |
|----------|-----------|
| **Dive planning software** | Does not save dive plans, does not connect to dive computers. It is the science behind the dive, not the operational tool. |
| **Conservation campaign** | Presents conservation data honestly. Does not advocate for a specific position. The 30x30 progress bar is a fact, not a call to action. |
| **Species identification app** | Does not support photo identification, field notes, or dive logging. |
| **Encyclopaedia** | ~2,000 species in full cards, not 200,000. Coverage is curated. Long tail via OBIS and FishBase APIs. |
| **Academic journal** | Cites primary literature and uses real data. Not peer-reviewed. Credits page distinguishes data sources, literature, and curated content. |
| **Tourism site** | Lists top 100 dive sites with honest depth and decompression information. Does not promote operators, liveaboards, or travel products. |

---

*Bathys — BA-02 Project Concept · v0.2 · May 2026*
