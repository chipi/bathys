# Bathys — Provenance & Content Pipeline

## BA-06 · Provenance & Content Pipeline

> v0.1 · Draft · May 2026
> The audit process for every asset and piece of content that enters
> Bathys. Every image, dataset, algorithm, and text claim must pass
> through this process before it appears in the application.
> No asset is admitted without a complete provenance record.

---

## 1. The Provenance Principle

Bathys makes a specific claim: every number traces back to a paper,
every image traces back to a photographer, every dataset traces back
to its source with its license. The Credits page is the public face
of that claim. This document is the process that makes it true.

The provenance pipeline runs before the build pipeline. An asset
without a complete provenance record does not enter the build. This
is not a quality-of-life improvement — it is the mechanism that
keeps the Credits page honest.

**The three rules:**

1. Every asset has exactly one provenance record before it is used.
2. A provenance record is complete when all required fields are
   filled. Partial records block admission.
3. The provenance record is the source of truth. The Credits page
   renders from it. If something appears in the Credits page, its
   record exists. If a record doesn't exist, the asset is not in
   the build.

---

## 2. Content Categories

Six categories of content enter Bathys. Each has different
provenance requirements.

| Category | Volume | Complexity | Primary risk |
|----------|--------|-----------|-|
| **Owner photography** | Medium (~100–300 images) | Low | Watermark and credit line required |
| **Creative Commons photography** | High (~500–1000 images) | Medium | SA licenses restrict derivatives |
| **Institutional photography** | Low (~50–100 images) | High | Cousteau Society TBD |
| **Scientific datasets** | Medium (~20 data sources) | Low | Attribution requirements vary |
| **Algorithm implementations** | Low (~4 algorithms) | Low | Must cite source paper in code |
| **Curated content** | High (~200 expedition entries, ~2000 species cards) | Low | Original writing required, no copying |

---

## 3. The Per-Asset Provenance Record

Every image has exactly one record in `/src/data/credits/photography.json`.
Every dataset has one record in `/src/data/credits/datasets.json`.
Every paper has one record in `/src/data/credits/papers.json`.
Every institution has one record in `/src/data/credits/institutions.json`.
Every algorithm has one record in `/src/data/credits/algorithms.json`.

### 3.1 Photography record schema

```json
{
  "id": "string — unique ID",
  "filename": "string — processed filename in CDN",
  "original_filename": "string",
  "source_url": "string",
  "photographer": "string — full name",
  "photographer_url": "string",
  "institution": "string | null",
  "title": "string | null",
  "date_taken": "string | null",
  "date_obtained": "string — YYYY-MM-DD",
  "license": "owner | CC0 | CC-BY | CC-BY-SA | CC-BY-NC | CC-BY-ND | CC-BY-NC-SA | public-domain | institutional-educational | tbd",
  "license_url": "string | null",
  "source_page_url": "string",
  "attribution_required": "boolean",
  "share_alike_required": "boolean",
  "commercial_use_permitted": "boolean",
  "modifications_permitted": "boolean",
  "credit_line": "string — exact credit line for the UI",
  "watermark_required": "boolean",
  "tabs_used": ["array of tab IDs"],
  "audit_status": "pending | approved | rejected",
  "audit_notes": "string | null",
  "audit_date": "string | null"
}
```

**Example — owner photography:**

```json
{
  "id": "owner-malpelo-hammerhead-001",
  "filename": "malpelo-hammerhead-001.webp",
  "original_filename": "IMG_4521.CR2",
  "source_url": "owner-archive",
  "photographer": "[Owner full name]",
  "photographer_url": "[Owner photography website]",
  "institution": null,
  "title": "Scalloped hammerhead school, Malpelo",
  "date_taken": "2023-03",
  "date_obtained": "2026-05-14",
  "license": "owner",
  "license_url": null,
  "source_page_url": "owner-archive",
  "attribution_required": true,
  "share_alike_required": false,
  "commercial_use_permitted": false,
  "modifications_permitted": false,
  "credit_line": "© [Owner name] — [Owner website]",
  "watermark_required": true,
  "tabs_used": ["dive-lab", "flora-fauna"],
  "audit_status": "approved",
  "audit_notes": null,
  "audit_date": "2026-05-14"
}
```

**Example — Creative Commons photography:**

```json
{
  "id": "mbari-anglerfish-biolum-001",
  "filename": "anglerfish-biolum-001.webp",
  "original_filename": "anglerfish_2847.jpg",
  "source_url": "https://mbari.org/product/anglerfish-bioluminescence/",
  "photographer": "MBARI",
  "photographer_url": "https://mbari.org",
  "institution": "MBARI",
  "title": "Melanocetus johnsonii bioluminescent lure",
  "date_taken": "2021",
  "date_obtained": "2026-05-20",
  "license": "CC-BY",
  "license_url": "https://creativecommons.org/licenses/by/4.0/",
  "source_page_url": "https://mbari.org/product/anglerfish-bioluminescence/",
  "attribution_required": true,
  "share_alike_required": false,
  "commercial_use_permitted": true,
  "modifications_permitted": true,
  "credit_line": "MBARI — CC BY 4.0",
  "watermark_required": false,
  "tabs_used": ["flora-fauna"],
  "audit_status": "approved",
  "audit_notes": null,
  "audit_date": "2026-05-20"
}
```

### 3.2 Dataset record schema

```json
{
  "id": "string",
  "name": "string",
  "provider": "string",
  "provider_url": "string",
  "description": "string",
  "access_url": "string",
  "license": "string",
  "license_url": "string | null",
  "attribution_required": "boolean",
  "attribution_text": "string",
  "version_or_date": "string",
  "refresh_cadence": "annual | monthly | daily | live | static",
  "bathys_usage": "string",
  "tabs_used": ["array of tab IDs"],
  "audit_status": "pending | approved",
  "audit_date": "string | null"
}
```

### 3.3 Algorithm record schema

```json
{
  "id": "string",
  "name": "string",
  "description": "string",
  "primary_source": {
    "citation": "string",
    "doi": "string | null",
    "url": "string | null"
  },
  "secondary_sources": ["array of citations"],
  "license": "public-domain",
  "implementation_file": "string",
  "coefficient_source": "string",
  "unit_test_file": "string",
  "test_validation_source": "string",
  "audit_status": "pending | approved",
  "audit_date": "string | null"
}
```

### 3.4 Institution record schema

```json
{
  "id": "string",
  "name": "string",
  "abbreviation": "string | null",
  "url": "string",
  "country": "string",
  "description": "string",
  "contribution_to_bathys": "string",
  "datasets_provided": ["array of dataset IDs"],
  "photography_provided": ["array of photography IDs"],
  "licensing_contact": "string | null",
  "licensing_status": "open | educational-use | enquiry-required | tbd | declined",
  "licensing_notes": "string | null",
  "audit_status": "pending | approved",
  "audit_date": "string | null"
}
```

---

## 4. The Licensing Decision Matrix

| License | Attribution | Commercial use | Modifications | Share-alike | Bathys verdict |
|---------|------------|----------------|---------------|-------------|----------------|
| **Owner** | Yes — credit + watermark | No | No | No | ✅ Admitted |
| **CC0** | No (recommended) | Yes | Yes | No | ✅ Admitted freely |
| **Public domain** | No (recommended) | Yes | Yes | No | ✅ Admitted freely |
| **CC-BY** | Yes | Yes | Yes | No | ✅ Admitted |
| **CC-BY-SA** | Yes | Yes | Yes | Yes | ⚠️ Admitted — display without modification. Colour-register grading not permitted on these images. |
| **CC-BY-NC** | Yes | No | Yes | No | ✅ Admitted — Bathys is non-commercial |
| **CC-BY-ND** | Yes | Yes | No | No | ⚠️ Admitted — no modifications. Resize and WebP conversion acceptable, no colour grading. |
| **CC-BY-NC-SA** | Yes | No | Yes | Yes | ✅ Admitted — non-commercial |
| **Institutional educational** | Yes — per terms | No | Per terms | Per terms | ⚠️ Only after written confirmation |
| **TBD** | — | — | — | — | ❌ Not admitted until resolved |

**CC-BY-SA special note:** Displaying a CC-BY-SA image in Bathys does not make Bathys CC-BY-SA. The share-alike obligation applies to derivative works. Standard display is acceptable. Colour-register grading constitutes a modification — do not apply it to CC-BY-SA images. Apply colour grading only to owner and CC-BY images.

---

## 5. The Cousteau Society Licensing Tracker

| Item | Status | Notes |
|------|--------|-------|
| Calypso deck and interior photography | TBD | Enquiry not yet sent |
| Conshelf II photographs — Sha'ab Rumi | TBD | Enquiry not yet sent |
| SP-350 Denise operational imagery | TBD | Enquiry not yet sent |
| Film stills from The Silent World | Separate rights | Les Requïns Associés — different pathway |
| Film stills from World Without Sun | Separate rights | Different pathway |
| Cousteau portrait photography | TBD | Enquiry not yet sent |

**Action plan:**
1. Build Tab 3 with public domain fallback content first
2. Draft formal request: educational, non-commercial, full attribution
3. Send to cousteau.org and Ocean Futures Society in parallel
4. If approved: replace fallback images, update photography records
5. If declined: document decision, maintain fallback permanently

**Fallback content if licensing fails:**
- Wikimedia Commons historical Cousteau photographs (CC-BY or public domain)
- NOAA archival Conshelf II photographs (public domain)
- Own illustrations (Calypso cutaway, SP-350 profile) are original work — fully clear
- Published book cover imagery: NOT usable without separate rights

---

## 6. The Content Audit Checklist

### For every image:

```
□ Source URL documented and reachable
□ Photographer name confirmed (not "unknown")
□ License confirmed directly from source, not inferred
□ License URL documented
□ Attribution text composed and stored in credit_line
□ License implications understood per Section 4 matrix
□ share_alike_required correctly set
□ commercial_use_permitted correctly set (Bathys = non-commercial)
□ modifications_permitted correctly set
□ If modifications not permitted, image used unmodified
□ If owner photography: watermark applied, credit links to website
□ tabs_used populated with every tab where image appears
□ Image processed through build pipeline (resized, WebP converted)
□ Image ID unique in photography.json
```

### For every dataset:

```
□ Dataset name and provider confirmed
□ Access URL working and documented
□ License confirmed from provider's own documentation
□ Attribution text confirmed from provider's requirements
□ Refresh cadence confirmed
□ Bathys usage description accurate
□ Registration/API key requirements documented in project secrets
```

### For every algorithm:

```
□ Primary source paper cited with DOI
□ Coefficient tables cited to specific pages in source
□ Implementation file exists in /src/deco/
□ Unit tests exist in /src/deco/__tests__/
□ Unit tests validate against at least one published dive profile
□ Test validation source documented in algorithm record
```

### For every curated text entry:

```
□ Every specific claim traceable to a source
□ Source cited inline or in a notes field
□ Text is original writing — not copied from Wikipedia
□ If fact from Wikipedia, verified against a primary source
□ No image used without a corresponding photography record
```

---

## 7. The Build Pipeline Specification

Provenance validation CI gate runs before the build. Assets with
`audit_status: pending` or `audit_status: rejected` are excluded.

```
scripts/pipeline/
  ├── images.ts         — image processing pipeline
  ├── validate.ts       — provenance validation (CI gate)
  ├── credits.ts        — credits page generation from JSON
  └── audit-report.ts   — full audit report output
```

### Image processing steps

For each image with `audit_status: approved`:

1. **Validate** — confirm source file exists, record complete
2. **Resize** — four responsive variants: 400px, 800px, 1200px, 2400px
3. **Convert** — WebP primary, JPEG fallback
4. **Compress** — quality 85 WebP, 80 JPEG
5. **Watermark** — owner photography only. Small semi-transparent mark,
   bottom-right. Links to owner photography website in the UI.
6. **Hash** — content-addressed filename: `{id}-{size}-{hash}.webp`
7. **Write metadata** — update record with processed filenames
8. **Output** — write to CDN output directory

### Provenance validation checks

```bash
# No images with audit_status pending
jq '[.[] | select(.audit_status == "pending")] | length' src/data/credits/photography.json
# (should return 0)

# No images without credit_line
jq '[.[] | select(.credit_line == "" or .credit_line == null)] | length' src/data/credits/photography.json
# (should return 0)

# No datasets pending
jq '[.[] | select(.audit_status == "pending")] | length' src/data/credits/datasets.json
# (should return 0)

# No algorithms without unit test file
jq '[.[] | select(.unit_test_file == null)] | length' src/data/credits/algorithms.json
# (should return 0)
```

---

## 8. Folder Structure

```
docs/provenance/
  ├── README.md              — summary + quick-start
  ├── AUDIT-LOG.md           — running log of audit decisions
  ├── COUSTEAU-TRACKER.md    — Cousteau Society licensing log
  ├── LICENSE-DECISIONS.md   — non-obvious license decisions
  └── SOURCES.md             — master list of all content sources

src/data/credits/
  ├── photography.json
  ├── datasets.json
  ├── algorithms.json
  ├── institutions.json
  ├── papers.json
  └── people.json

src/data/library/
  ├── books.json
  ├── documentaries.json
  ├── institutions.json
  └── journals.json

scripts/pipeline/
  ├── images.ts
  ├── validate.ts
  ├── credits.ts
  └── audit-report.ts
```

---

## 9. Credits Page Generation

The Credits page renders entirely from `/src/data/credits/` JSON.
No credits content is hand-written in React components. Adding an
asset and updating the JSON is the only step.

**Sections generated:**
- **Institutions** — cards sorted by country then name
- **Photography** — searchable/filterable gallery by license type
- **Datasets** — table with provider, license, refresh cadence
- **Algorithms** — citation with DOI, link to implementation file
- **Academic papers** — full bibliography with DOIs, grouped by section
- **Researchers & Explorers** — formal acknowledgment of people documented

---

## 10. Library Page Generation

**Book record schema (key fields):**

```json
{
  "id": "string",
  "title": "string",
  "authors": ["array"],
  "year": "number",
  "description": "string — why this book for Bathys readers",
  "bathys_sections": ["array of tab IDs"],
  "purchase_url": "string | null — Bookshop.org preferred",
  "open_access_url": "string | null"
}
```

**Documentary record schema (key fields):**

```json
{
  "id": "string",
  "title": "string",
  "director": "string",
  "year": "number",
  "description": "string",
  "bathys_sections": ["array of tab IDs"],
  "streaming_url": "string | null",
  "notes": "string | null"
}
```

---

## 11. Open Provenance Questions for Phase 2

| Question | Priority | When to resolve |
|----------|----------|-----------------|
| Cousteau Society licensing — all Section 5 items | High | Before Tab 3 content assembly |
| JAMSTEC image library terms | Medium | Before Tab 2 vessel imagery |
| IFREMER media library terms | Medium | Before Tab 2 Ifremer expedition imagery |
| Film stills from The Silent World (Les Requïns Associés) | High | Before Tab 3 content assembly |
| Film stills from World Without Sun | High | Before Tab 3 content assembly |
| CC-BY-SA colour-register grading constraint | Low | Before image pipeline runs |
| Owner photography watermark design | Medium | Before image pipeline builds |
| Owner photography website URL for watermark link | Medium | Before image pipeline builds |

---

*Bathys — BA-06 Provenance & Content Pipeline · v0.1 · May 2026*
