# Additional identity diagnostics: geographic and biblical-name ambiguities (16 November 2026)

**Related:** #1, PR #7. **Status:** focused, deliberately selected diagnostic cases, NOT approved crosswalk entries, source revisions of live pages unpinned. No packaging or publishing.

## Method and provenance

The source-level structural universe and exact pinned data revision are documented in [OPENBIBLE_TIPNR_JOIN_TRIAGE_2026-11-15.md](OPENBIBLE_TIPNR_JOIN_TRIAGE_2026-11-15.md): OpenBible commit `7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f` and STEP commit `5de0a47f35f0fc13dfe1430d104e5db8a4285f9c`. The original structural table explicitly lists `Gadara@Mat.8.28` and `Teman@Gen.36.34` among its **76 distinct** syntactic STEP-ID nonmatches. The observations below use **live public** OpenBible pages and a readable Wikidata item page; those live pages and the specific Wikidata entity revision were **not captured at a permanent revision**. In particular, this note does not assert that the present live page bytes are identical to the pinned upstream JSONL. Link IDs and names are cross-check observations, not new authoritative identities.

## 1. Gadara and Gerasa: one STEP link, two ancient settlements

| Original OpenBible entry | Live linked STEP ID | Live Wikidata candidate | Location proposed by OpenBible | Verses on its own entry |
| --- | --- | --- | --- | --- |
| [Gadara `afed46a`](https://www.openbible.info/geo/ancient/afed46a/gadara) | `Gadara@Mat.8.28` | [Q96379011](https://www.wikidata.org/wiki/Q96379011) | Umm Qais | Matthew 8:28 |
| [Gerasa `ada6b64`](https://www.openbible.info/geo/ancient/ada6b64/gerasa) | `Gadara@Mat.8.28` | [Q31565](https://www.wikidata.org/wiki/Q31565) | Jerash | Mark 5:1; Luke 8:26,37 |

Although the source cross-reference string is **identical**, OpenBible treats these as separate ancient geographical entries with different Pleiades IDs (Gadara **678142**, Gerasa **678158**). [Wikidata Q31565](https://www.wikidata.org/wiki/Q31565) is expressly about **modern Jerash**, a city in Jordan, and includes a `replaces` statement referring to **Gerasa**. Q31565's coordinate, modern population, modern photographs and administrative fields must **not** be attributed to Gadara or indiscriminately to ancient Gerasa. The Q96379011 page could not be independently retrieved during this pass; do not infer its class, exact subject or revision.

**Decision:** both ancient-entry → Q-ID links remain **UNRESOLVED for independently approved identity**, though the ancient places are distinguishable. The Gerasa → modern Jerash link is a **related-modern-settlement candidate**, not authorization to merge the concepts. Do not implement one-Q-ID-per-STEP-ID or attach Q31565 to the Gadara entry.

**Important biblical-text boundary:** the different Gospel geographical designations and their textual witnesses require their own textual/editorial investigation before treating Matthew 8:28 and Mark 5:1 / Luke 8:26 as proving a single named settlement. This source comparison does **not** settle manuscript variants, textual criticism or the precise site of the episode.

## 2. Teman: a source-ID version mismatch is not a person-to-place correction

[OpenBible Teman `a831506`](https://www.openbible.info/geo/ancient/a831506/teman) identifies a **region or settlement** in passages such as Jeremiah 49:7, Ezekiel 25:13, Obadiah 9, and Habakkuk 3:3. Its live linked STEP ID is `Teman@Gen.36.34` and its candidate is [Q1546303](https://www.wikidata.org/wiki/Q1546303). The pinned structural triage finds the later TIPNR name **Teman** in *two distinct categories*: person `Teman_Gen.36.11` and place `Teman_Jer.49.7`. The text of Genesis 36:11 concerns a person, whereas OpenBible's verse contexts concern the geographical region. **Never substitute the person record merely because the name matches.** Nor is there sufficient source-version evidence to replace the old linked-ID automatically with the new place record.

OpenBible itself lists **nine alternative identifications**, with its top two candidates each at only 25% confidence; the linked data therefore must not generate a single authoritative coordinate or site photograph. Wikidata Q1546303's specific revision/type was not accessible for independent verification in this pass.

**Decision:** `a831506` is a geographical source record; its *current exact STEP-key retargeting* remains **UNRESOLVED**, its Q-ID is **UNAPPROVED**, and modern site, coordinate, and photograph enrichment remain disallowed.

## Regression conditions for future generic validators

1. Retaining `Gadara@Mat.8.28` as cross-reference must **not** collapse `afed46a` and `ada6b64`, must not conflate Q96379011 and Q31565, and must not automatically pass the Jerash photograph or modern demographic fields to an ancient entry.
2. A geographically typed source entry `a831506` must **not** resolve to `Teman_Gen.36.11` (person) through a name-only TIPNR fallback.
3. If a source ID no longer strictly exists in the newer TIPNR revision, preserve the old value and mark a version-sensitive cross-reference unresolved. No silently 'fixed' keys.
4. No site-location, facts or image use becomes allowed just because an article subject is plausible; separate field-level evidence and per-media licensing still apply.
5. For all three diagnostic entries, permanent **source record** and **Wikidata item revisions**, original relation qualifiers and independent authority checks remain necessary prior to any accepted review log row.

These findings are **three deliberately chosen entries, not a sample-derived precision or error-rate estimate**. No original records altered, no automated mappings approved, no app edits or resource publication.
