# Reused OpenBible–TIPNR place links: six-group editorial probe (16 November 2026)

**Issue:** #1. **Status:** evidence-based, deliberately selected diagnostic sample; **not** a stratified random sample, a complete identity check, an approved mapping, or a resource release.

## Provenance and limitations

The structural universe and source checksums remain those of [the pinned full inventory](OPENBIBLE_TIPNR_JOIN_TRIAGE_2026-11-15.md):

- OpenBible ancient-place data: `openbibleinfo/Bible-Geocoding-Data`, commit `7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f`, `data/ancient.jsonl`, Git blob `b127b4446c6f4ba36ec62dde290c752afeb51bf3`.
- STEP TIPNR: `STEPBible/STEPBible-Data`, commit `5de0a47f35f0fc13dfe1430d104e5db8a4285f9c`, TIPNR proper-nouns text, Git blob `94e636b8806eaa0501d2c7fc2a0fc87b3ffbea96`.
- Pinned inventory: 147 reused linked-ID groups; 37 with multiple distinct nonempty Q-IDs. These are *structural* counts, not confirmed mapping errors.

**Additional evidence inspected 16 November 2026:** public OpenBible *live* ancient-place pages and accessible Wikidata item descriptions, with independent BiblIndex checks for Mizpah. Exact links are below. The live pages are **not revision-pinned snapshots**, and individual Wikidata item revisions were **not captured**. The exact original OpenBible JSONL contents and link modifiers were independently re-checked in the pinned Git blob (counts below); this is still not a reproducible final set of accepted identities. Some Wikidata item pages failed retrieval; such failures are not interpreted as missing items. No mass raw source bytes, images, Wikipedia articles or generated summaries were copied.

**Method:** select four high-conflict groups plus two contrasting groups (one or zero Q-IDs) from the complete inventory; inspect a number of their *separate* OpenBible ancient-entry IDs, their own biblical verse contexts, the target concept and any `not` modifier, and the difference between a topic identity and a modern site/coordinate. Maintain the original linked STEP ID unchanged. Do not infer identity from a shared parent STEP ID.

## Follow-up: qualified links verified in the **pinned** JSONL

This pass also parsed **all 1,342** source lines of the exact OpenBible Git blob named above, selecting the source keys `linked_data.s3b25cf.id` (STEP) and `linked_data.s7cc8b2.id` / `linked_data.s7cc8b2.modifier` (Wikidata). The two source-key meanings are revision-bound, as already checked in the original structural audit.

- **1,172** entries have a STEP linked ID; **574** of these also have a nonempty Wikidata Q-ID.
- Among these **574** candidate Q-IDs, **564** have no modifier, **4** explicitly say `not`, and **6** say `modern`. Across all OpenBible rows there are **655** nonempty Q-IDs: 645 unqualified + the **same** 4 `not` and 6 `modern` rows.
- Thus neither a populated Q-ID nor the absence of a modifier is equivalent to editorial acceptance. `not` is negative evidence against strict identity; `modern` requires separate ancient/modern relationship assessment.

All **ten** qualified records, with the original 1-based JSONL line numbers:

| Modifier | Source line | OpenBible entry | Original Q-ID |
| --- | ---: | --- | --- |
| `not` | 22 | Adamah (afe1143) | Q2605670 |
| `not` | 137 | Avvim (a6d7a41) | Q4828853 |
| `not` | 152 | Baal-hamon (a304bb7) | Q83879 |
| `not` | 938 | New Gate (aa85961) | Q1256221 |
| `modern` | 364 | Dung Gate (a1611b6) | Q204719 |
| `modern` | 518 | Gimzo (a5dd9e3) | Q2613825 |
| `modern` | 549 | Halhul (afca9ce) | Q2574933 |
| `modern` | 556 | Hamath 1 (ac62cbc) | Q173545 |
| `modern` | 602 | Helbon (a8a8e54) | Q16892062 |
| `modern` | 640 | Iconium (ae425aa) | Q79857 |

To reproduce the summary: parse each nonempty JSONL line; count rows by presence of the two source-specific `linked_data` IDs; group Wikidata-bearing rows by their exact modifier string, using `none` for a missing modifier. For reused STEP groups, count the distinct nonempty Q-IDs before and after removing entries whose Wikidata modifier is `not` or `modern`.

- Before filtering, **37** of the 147 reused STEP groups have more than one distinct nonempty Q-ID.
- After removing `not` and `modern` candidates, **36** still have multiple Q-IDs. The **one** group to drop out is `Hamath@Num.13.21`: Hamath 1 carries Q173545 (`modern`), while Lebo-hamath carries Q6467705 (unqualified). **Neither one is approved simply because this filter leaves one candidate.**
- This is a **source-revision verification** of the exact modifiers and counts, but not a historical/subject identity validation of the 36 remaining groups.

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

**Interpretation of the first four groups:** these are **15 hand-selected OpenBible entries**, not 15 approved correspondences. The *multiple-Q-ID* signal includes (1) distinct type-level concepts (city versus region, mountain versus town), (2) actual explicit negative links, (3) proposed geographic aliases, and (4) uncertain/symbolic referents. A one-Q-ID-per-linked-STEP-ID lookup would create false results even if every Q-ID string were syntactically valid.

## Contrast groups: **one** or **zero** Q-IDs do not guarantee identity

The full inventory also includes reused STEP-linked IDs with **only one nonempty Q-ID** or **no Q-ID**. To avoid focusing solely on obvious MULTIPLE_QIDS cases, the following **11 original entries across two additional groups** were inspected in the same pinned Git blob (1-based line numbers). This deliberately covers all three structural Q-ID categories; it is **not** a random or statistically representative sample.

| Group / structural category | Pinned line / ancient entry | Q-ID on **that entry** | Biblical context and editorial issue |
| --- | --- | --- | --- |
| `Bethlehem@Gen.35.16` / **ONE_QID** | 233 — [Bethlehem 1 (a112427)](https://www.openbible.info/geo/ancient/a112427/bethlehem-1) | [Q5776](https://www.wikidata.org/wiki/Q5776) | Candidate **Bethlehem of Judea** topic (Gen 35:19; Ruth 1). |
| same | 235 — [Bethlehem 3 (ab1a343)](https://www.openbible.info/geo/ancient/ab1a343/bethlehem-3) | **none** | Judges 12:8,10, concerning Ibzan. OpenBible favors a proposed alias of Bethlehem **2** (Galilee), while allowing Bethlehem 1 as a minority alternative. **Do not inherit Q5776.** |
| same | 423 — [Ephrath (af4e985)](https://www.openbible.info/geo/ancient/af4e985/ephrath) | **none** | Genesis 35:16,19 and 48:7; plausible alias for Bethlehem 1 but identity still needs individual approval. |
| same | 424 — [Ephrathah (af6c09e)](https://www.openbible.info/geo/ancient/af6c09e/ephrathah) | **none** | Ruth 4:11; Psalm 132:6; possible Bethlehem 1 relation, not automatically an identity or coordinate. |
| same | 765 — [Lehem (a9ea180)](https://www.openbible.info/geo/ancient/a9ea180/lehem) | **none** | 1 Chronicles 4:22; OpenBible explicitly offers *not a place (personal name or part of a phrase)* **versus** a Bethlehem 1 alias. Do not assign a Q-ID or map marker. |
| `Gilgal@Deu.11.30` / **NO_QID** | 224 — [Beth-gilgal (aea5552)](https://www.openbible.info/geo/ancient/aea5552/beth-gilgal) | **none** | Nehemiah 12:29; multiple proposed Gilgal aliases. |
| same | 488 — [Geliloth (a0c9a06)](https://www.openbible.info/geo/ancient/a0c9a06/geliloth) | **none** | Joshua 18:17; 22:10–11; several proposed sites. |
| same | 506 — [Gibeath-haaraloth (a97126d)](https://www.openbible.info/geo/ancient/a97126d/gibeath-haaraloth) | **none** | Joshua 5:3; a **hill near** Gilgal/Jericho, not an automatic identity with Gilgal. |
| same | 513 — [Gilgal 1 (ab94aea)](https://www.openbible.info/geo/ancient/ab94aea/gilgal-1) | **none** | Joshua 4–5, several proposed locations. |
| same | 515 — [Gilgal 3 (aed8df9)](https://www.openbible.info/geo/ancient/aed8df9/gilgal-3) | **none** | Joshua 15:7; could be linked to Geliloth or Gilgal 1, not yet resolved. |
| same | 516 — [Gilgal 4 (a84a509)](https://www.openbible.info/geo/ancient/a84a509/gilgal-4) | **none** | Deuteronomy 11:30; OpenBible considers alternatives Gilgal 1 and Gilgal 2, and uncertain modern sites. |

**Important contrasts:** in the **ONE_QID** group the sole Q-ID belongs only to Bethlehem 1, yet Bethlehem 3 is provisionally associated with a *different* Bethlehem and Lehem may not even be a place. In the **NO_QID** group, the lack of Wikidata matches tells us nothing about whether the six ancient entries share one referent. See the directly inspected [Bethlehem 3](https://www.openbible.info/geo/ancient/ab1a343/bethlehem-3), [Lehem](https://www.openbible.info/geo/ancient/a9ea180/lehem), [Gilgal 4](https://www.openbible.info/geo/ancient/a84a509/gilgal-4) and [Gibeath-haaraloth](https://www.openbible.info/geo/ancient/a97126d/gibeath-haaraloth) source pages. Original entry values were checked in the pinned JSONL; live page and Wikidata revisions remain unpinned.

**Totals for this diagnostic pass:** **26 distinct OpenBible entries** from **six** selected reused-STEP groups: four MULTIPLE_QIDS groups (15 entries), one ONE_QID group (5), one NO_QID group (6). This balances *categories*, but **does not sample proportionately from the 147-group universe**, has no independent per-link sign-off and supplies no validated coverage/precision estimate.

## Required safety decisions to carry forward

1. Use a **source-namespaced OpenBible ancient entry ID plus exact pinned source revision** as the primary unit for these place candidates. Keep its linked TIPNR ID as **source-provided cross-reference evidence**, not a uniqueness guarantee or an assertion that every child denotes the same historical entity. Do not claim the OpenBible ID is stable across all future revisions without testing.
2. Interpret `linked_data` **modifiers** first. `not` explicitly forbids direct identity import; `modern` identifies a relationship requiring separate review. An ID collector must not strip the modifier. Retain modifiers and unmodified upstream rows in review evidence.
3. Preserve **relationship kind** (identity, possible alias, nearby/related site, symbolic referent, explicit non-identity), original verse contexts and alternative identifications. A topic-level article link does not validate coordinate, photograph or factual claims.
4. The TIPNR linked-ID string may drift against the later TIPNR revision: the 138 strict-match nonmatches are **diagnostic**, not 138 confirmed wrong geographic assignments. Do not retarget them by fuzzy name.
5. Keep review log fields from [the protocol](../IDENTITY_REVIEW_PROTOCOL.md): source ID/revisions, candidate Q-ID, original modifier, biblical context, positive/negative evidence, relation type, independent reviewer, verdict and separately allowed article/facts/location/image uses. This sample supplies *leads* for those fields, **not a signed-off machine-importable review log**.
6. Do not create a special-case fixer or start the generation pipeline (#5); wait for #1 validation and #4 pilot gates. No new rights for Wikipedia excerpts/Commons media are implied.

## Next verification tasks / known blockers

- Obtain **pinned individual Wikidata item revisions**, exact version-bound upstream row payloads and an independent biblical/authority countercheck before changing any `CANDIDATE` to `accepted`.
- Resolve inaccessible Wikidata item pages (Q48968605, Q6884729, Q6884740, Q412380) using a compliant API client rather than guessing; the upstream `not`/`modern` modifiers are now verified against pinned JSONL, but do not solve missing Wikidata revision checks.
- Extend to **stratified** cases among the 37 MULTIPLE_QIDS groups, 110 other reused-ID groups and 76 distinct strict TIPNR-ID nonmatches. Record counts by cause only after evidence-level review. The present sample is intentionally biased toward problems and supplies **no error rate or precision estimate**.
- Build a separate negative regression fixture: the combination `Baal-hamon a304bb7 → Q83879 (not)` must never enrich a biblical place; `Mizpah 3 a736f6c` must not inherit Arimathea's article simply because both carry `Mizpah@Jdg.20.1`.

**Outcome:** editorial risks clarified; no identity link approved, no raw source altered, no resource package generated, no app changes, no public release.
