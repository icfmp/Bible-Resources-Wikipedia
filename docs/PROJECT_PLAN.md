# Project plan and decision gates

## Product goal
Prepare a **downloadable, self-contained and offline-capable** resource that can enrich Bible's existing person and place cards, without making Bible query Wikimedia itself.

The output is **not** a general Wikipedia mirror and not a new Bible translation/commentary. Initial languages: **French and English** (source content is never silently translated). Other languages may be added after coverage is measured.

## Phase 1 — Source feasibility / identity audit
Inspect:
- Original STEP TIPNR people/places/things: version, stable IDs, variants, occurrences, artificial article descriptions, content license and limits.
- OpenBible place geocoding: TIPNR links, Wikidata Q-IDs, evidence/uncertainty, ancient vs proposed modern location.
- The optional third-party `PatristicTextArchive/tipnr_data/tipnr-persons-wikidata.tsv` only as **untrusted candidate matches**. A preliminary check found duplicated Wikidata IDs assigned to distinct TIPNR individuals; independently assess failures, not just the count of nonblank cells.
- Wikidata item type, sitelinks, languages, coordinates/relationships and qualifying provenance; Wikipedia intro API options; Commons rights and identity.

**Gate 1 output:** exact source commits/versions, licensing inventory, coverage table, misleading match examples, and a reproducible sample. No automatic acceptance of Q-IDs from names alone.

## Phase 2 — Editorial / rights specification
For each entity-to-item match, record: source entity ID, target Q-ID, type, evidence references, classification (verified / rejected / unresolved), uncertainty, review date/reviewer and source versions. Changes must be justified and reversible.

For text/image reuse, specify full source page/revision (when available), creator/contributor attribution mechanism, locale, applicable license URL, transformations (e.g. excerpt/thumbnail) and the exact output fields exposed to the reader. Reject non-free or insufficiently attributed media.

**Gate 2 output:** editorial decision record and a documented rights audit; no unreviewed publication.

## Phase 3 — Minimal reader-facing contract
Propose and validate **one small versioned package**, possibly JSON + a manifest and optional local thumbnails. The exact format remains **undecided** until the pilot and Bible integration requirements are established.

Candidate fields: `schema_version`, `resource_version`, `built_at`, source snapshots/sha256; entries keyed by `source` + `entity_id` + entity type; verified `wikidata_qid`; FR/EN article excerpts and URLs; selected typed facts; primary/secondary media references and per-file rights; uncertainty/status; deterministic ordering. Avoid a bespoke UI schema in the resource.

**Gate 3 output:** a stable schema proposal, size budget, upgrade/migration policy and agreement with Bible reader maintainers. No editing Bible as part of this gate.

## Phase 4 — Diverse pilot, before scaling
Choose ~20–30 **actual** entries with a documented test plan. At minimum include:
- One major unambiguous person (e.g. Abraham) and several **same-name people** (e.g. John/Mary).
- One clear place (e.g. Jerusalem), one **disputed ancient-vs-modern identification** (e.g. Emmaus), one unidentified/unknown place (e.g. Nod).
- Hebrew and Greek name variants; records with no Wikipedia article, no image, FR-only/EN-only articles, historical uncertainty and multiple Commons works.
- A correct modern photograph of a site versus a correctly labeled painting/sculpture of a biblical person.

For each case, compare against sources and report evidence, outcome, false-positive count, coverage, package bytes, runtime display expectations, attribution completeness, missing/unsupported fields. **Accepting zero unsafe matches is preferable to nominal coverage.**

**Gate 4 output:** independently reviewed pilot dataset and signed-off go/no-go for scaling. Do not describe pilot records as publicly released.

## Phase 5 — Generic build/QA
Only after the pilot, produce the smallest reusable acquisition/validation tooling. Require stable IDs, careful API use, retry/backoff, reproducible inputs, schema validation, unchanged source excerpts, media rights validation and deterministic checksums. Add CI coverage; audit the need for every script.

## Phase 6 — Optional package and application handoff
Define the download/update/rollback path via Bible's existing Library/Study tools, but do not implement changes in Bible here. Package source/revision/license manifest and generate a release only after explicit authorization. Verify offline use, resource update and removal preserving notes/highlights.

## Out of scope now
- Automatically fetching all Wikipedia topics, full article copies, mass Commons galleries or large-scale translations.
- AI-proposed biographical facts or auto-merging identities.
- Building yet another SWORD commentary, new API service or user login.
- Direct Wikimedia runtime API calls from the Bible app.
- Public launch, release, or updates in other repositories.

## Workflow
Issues are sequenced by **dependencies/evidence**, not parallel promises. A checked issue means its documented proof is complete; tests and publishing are separate statuses.
