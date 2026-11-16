# Reused OpenBible–TIPNR place links: four-group editorial probe (16 November 2026)

**Issue:** #1. **Status:** evidence-based, deliberately selected diagnostic sample; **not** a stratified random sample, a complete identity check, an approved mapping, or a resource release.

## Provenance and limitations

The structural universe and source checksums remain those of [the pinned full inventory](OPENBIBLE_TIPNR_JOIN_TRIAGE_2026-11-15.md):

- OpenBible ancient-place data: `openbibleinfo/Bible-Geocoding-Data`, commit `7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f`, `data/ancient.jsonl`, Git blob `b127b4446c6f4ba36ec62dde290c752afeb51bf3`.
- STEP TIPNR: `STEPBible/STEPBible-Data`, commit `5de0a47f35f0fc13dfe1430d104e5db8a4285f9c`, TIPNR proper-nouns text, Git blob `94e636b8806eaa0501d2c7fc2a0fc87b3ffbea96`.
- Pinned inventory: 147 reused linked-ID groups; 37 with multiple distinct nonempty Q-IDs. These are *structural* counts, not confirmed mapping errors.

**Additional evidence inspected 16 November 2026:** public OpenBible *live* ancient-place pages and accessible Wikidata item descriptions, with independent BiblIndex checks for Mizpah. Exact links are below. The live pages are **not revision-pinned snapshots**, and individual Wikidata item revisions were **not captured**. Consequently these findings are reviewer leads, not reproducible final accepted records. Some Wikidata item pages failed retrieval; such failures are not interpreted as missing items. No mass raw source bytes, images, Wikipedia articles or generated summaries were copied.

**Method:** select four high-conflict groups from the complete inventory; inspect a number of their *separate* OpenBible ancient-entry IDs, their own biblical verse contexts, the target concept and any `not` modifier, and the difference between a topic identity and a modern site/coordinate. Maintain the original linked STEP ID unchanged. Do not infer identity from a shared parent STEP ID.

## Case table — source **entry** is the review unit

| Reused linked STEP ID | OpenBible entry / verse context | Existing Q-ID (if any) | Finding / tentative disposition |
| --- | --- | --- | --- |
| `Babylon@Gen.10.10` | [Babylon 1, a217d18](https://www.openbible.info/geo/ancient/a217d18/babylon-1); many OT references | [Q5684 Babylon](https://www.wikidata.org/wiki/Q5684) | **CANDIDATE**, Babylon *city*. The source calls it a settlement. No transfer of this city identity to every child row. |
| same | [Babylonia, a8394b8](https://www.openbible.info/geo/ancient/a8394b8/babylonia); Ezra and Jeremiah | [Q47690 Babylonia](https://www.wikidata.org/wiki/Q47690) | **CANDIDATE, distinct subject**, geographic region rather than the Babylon city Q-ID. |
| same | [Pekod, a4b9865](https://www.openbible.info/geo/ancient/a4b9865/pekod); Jer 50:21 / Ezek 23:23 | [Q48968605](https://www.wikidata.org/wiki/Q48968605) | **UNRESOLVED independent item check**; OpenBible calls it a separate region. Wikidata page was inaccessible during this pass. Never collapse onto the city merely because its linked STEP ID is Babylon. |
| same | [Babel, ab8fdbc](https://www.openbible.info/geo/ancient/ab8fdbc/babel); Gen 10:10 / 11:9 | no Q-ID listed | **CANDIDATE for an alias relation**, not an automatically authorized Q5684 mapping. OpenBible says another name for Babylon 1 with a qualified identification. |
| same | [Babylon 3, a3f0756](https://www.openbible.info/geo/ancient/a3f0756/babylon-3); Revelation 14–18 | no Q-ID listed | **UNRESOLVED literal/symbolic referent**. OpenBible proposes Rome and several alternatives, including a symbolic non-place. Do not attach ancient Babylon coordinates or a real city image by inheritance. |
| `Hermon_Mount@Deu.3.8` | [Mount Hermon, a341fe8](https://www.openbible.info/geo/ancient/a341fe8/mount-hermon); Deut 3:8 etc. | [Q215471 Mount Hermon](https://www.wikidata.org/wiki/Q215471) | **CANDIDATE**, mountain subject; separate later field verification for coordinates and imagery. |
| same | [Baal-gad, ae12e43](https://www.openbible.info/geo/ancient/ae12e43/baal-gad); Josh 11:17 etc. | [Q4837122 Baal-gad](https://www.wikidata.org/wiki/Q4837122) | **CANDIDATE as a distinct ancient settlement** near Hermon, *not* the mountain itself. OpenBible offers several possible site identifications. |
| same | [Baal-hamon, a304bb7](https://www.openbible.info/geo/ancient/a304bb7/baal-hamon); Song 8:11 | [Q83879 Baal-hamon](https://www.wikidata.org/wiki/Q83879) | **REJECT DIRECT**. OpenBible explicitly labels the Wikidata link `(not)`; the Wikidata item describes a Carthaginian deity, not the biblical place/poetic expression. Preserve as a negative link test. |
| `Mizpah@Jdg.20.1` | [Mizpah 3, a736f6c](https://www.openbible.info/geo/ancient/a736f6c/mizpah-3); Judg 20:1 / Jer 40 | [Q1755389 Mizpah in Benjamin](https://www.wikidata.org/wiki/Q1755389) | **CANDIDATE**, specific Benjamin location. [BiblIndex](https://www.biblindex.org/en/bible-names/1278) independently pairs the Q-ID with Josh 18:26 and Jer 40:6; site locations still require their own evidence. |
| same | [Arimathea, af3d9fc](https://www.openbible.info/geo/ancient/af3d9fc/arimathea); Matt 27:57 etc. | [Q2558868 Arimathea](https://www.wikidata.org/wiki/Q2558868) | **CANDIDATE as a distinct NT subject**, not automatically Mizpah of Benjamin. Modern identification disputed, possible relationship to Ramathaim-zophim remains qualified. |
| same | [Ramathaim-zophim, a54ef72](https://www.openbible.info/geo/ancient/a54ef72); 1 Sam 1:1 | [Q1019146 Ramathaim-Zophim](https://www.wikidata.org/wiki/Q1019146) | **CANDIDATE, distinct OT subject**. Some proposed identification with Arimathea, not proven identity; no one-to-one parent-ID mapping. |
| `Ramoth-gilead@Gen.31.47` | [Ramoth-gilead, a2fe63c](https://www.openbible.info/geo/ancient/a2fe63c/ramoth-gilead); 1 Kgs 22 / 2 Kgs 8 | [Q2006096 Ramoth-Gilead](https://www.wikidata.org/wiki/Q2006096) | **CANDIDATE for biblical place topic; site unresolved.** OpenBible lists five proposed modern identifications; not one authoritative coordinate. |
| same | [Mizpah 1, a0f8af9](https://www.openbible.info/geo/ancient/a0f8af9/mizpah-1); Judg 10:17 / 11:11 | [Q6884729](https://www.wikidata.org/wiki/Q6884729) | **UNRESOLVED independent Wikidata check**; OpenBible identifies a Gilead site with several proposed modern locations. Not safely identical to Ramoth-gilead. |
| same | [Mizpah 4, a694ea2](https://www.openbible.info/geo/ancient/a694ea2/mizpah-4); Gen 31:47–49 | [Q6884740](https://www.wikidata.org/wiki/Q6884740) | **UNRESOLVED independent Wikidata check**; OpenBible marks a **stone heap**, and a qualified proposed alias of Mizpah 1. Not the same type as an urban settlement. |
| same | [Ramah 5, ad27541](https://www.openbible.info/geo/ancient/ad27541/ramah-5); 2 Kgs 8:29 / 2 Chr 22:6 | [Q412380](https://www.wikidata.org/wiki/Q412380) | **UNRESOLVED independent Wikidata check**; OpenBible proposes an alias of Ramoth-gilead with high confidence, but that is no basis to equate every row sharing this STEP link. |

**Interpretation:** this is **15 hand-selected OpenBible entries**, spanning 4 reused TIPNR-linked groups, not 15 approved correspondences. The *multiple-Q-ID* signal includes (1) distinct type-level concepts (city versus region, mountain versus town), (2) actual explicit negative links, (3) proposed geographic aliases, and (4) uncertain/symbolic referents. A one-Q-ID-per-linked-STEP-ID lookup would create false results even if every Q-ID string were syntactically valid.

## Required safety decisions to carry forward

1. Use a **source-namespaced OpenBible ancient entry ID plus exact pinned source revision** as the primary unit for these place candidates. Keep its linked TIPNR ID as **source-provided cross-reference evidence**, not a uniqueness guarantee or an assertion that every child denotes the same historical entity. Do not claim the OpenBible ID is stable across all future revisions without testing.
2. Interpret `linked_data` **modifiers** first. `not` explicitly forbids direct identity import; `modern` identifies a relationship requiring separate review. An ID collector must not strip the modifier. Retain modifiers and unmodified upstream rows in review evidence.
3. Preserve **relationship kind** (identity, possible alias, nearby/related site, symbolic referent, explicit non-identity), original verse contexts and alternative identifications. A topic-level article link does not validate coordinate, photograph or factual claims.
4. The TIPNR linked-ID string may drift against the later TIPNR revision: the 138 strict-match nonmatches are **diagnostic**, not 138 confirmed wrong geographic assignments. Do not retarget them by fuzzy name.
5. Keep review log fields from [the protocol](../IDENTITY_REVIEW_PROTOCOL.md): source ID/revisions, candidate Q-ID, original modifier, biblical context, positive/negative evidence, relation type, independent reviewer, verdict and separately allowed article/facts/location/image uses. This sample supplies *leads* for those fields, **not a signed-off machine-importable review log**.
6. Do not create a special-case fixer or start the generation pipeline (#5); wait for #1 validation and #4 pilot gates. No new rights for Wikipedia excerpts/Commons media are implied.

## Next verification tasks / known blockers

- Obtain **pinned individual Wikidata item revisions**, exact version-bound upstream row payloads and an independent biblical/authority countercheck before changing any `CANDIDATE` to `accepted`.
- Resolve inaccessible Wikidata item pages (Q48968605, Q6884729, Q6884740, Q412380) using a compliant API client rather than guessing; also test whether source `not`/`modern` modifiers in the pinned JSONL match the live presentation.
- Extend to **stratified** cases among the 37 MULTIPLE_QIDS groups, 110 other reused-ID groups and 76 distinct strict TIPNR-ID nonmatches. Record counts by cause only after evidence-level review. The present sample is intentionally biased toward problems and supplies **no error rate or precision estimate**.
- Build a separate negative regression fixture: the combination `Baal-hamon a304bb7 → Q83879 (not)` must never enrich a biblical place; `Mizpah 3 a736f6c` must not inherit Arimathea's article simply because both carry `Mizpah@Jdg.20.1`.

**Outcome:** editorial risks clarified; no identity link approved, no raw source altered, no resource package generated, no app changes, no public release.
