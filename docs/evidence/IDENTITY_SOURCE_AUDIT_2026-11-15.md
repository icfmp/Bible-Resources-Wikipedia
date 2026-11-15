# Identity source audit — baseline, 15 November 2026

**Related issue:** #1. **Status:** first full source-structure / crosswalk-count audit completed; editorial validation of individual links and cross-source upgrades **not complete**. These figures are reproducible *candidate counts*, **not** verified Wikipedia matching coverage. No encyclopedia resource has been generated, tested in Bible or released.

## 1. Exact source snapshots

| Source | Pinned commit | Relevant path / Git blob SHA |
| --- | --- | --- |
| [STEPBible-Data](https://github.com/STEPBible/STEPBible-Data) | [`5de0a47f35f0fc13dfe1430d104e5db8a4285f9c`](https://github.com/STEPBible/STEPBible-Data/commit/5de0a47f35f0fc13dfe1430d104e5db8a4285f9c) (2026-11-02) | [`Proper Nouns/TIPNR - Translators Individualised Proper Names with all References - STEPBible.org CC BY.txt`](https://github.com/STEPBible/STEPBible-Data/blob/5de0a47f35f0fc13dfe1430d104e5db8a4285f9c/Proper%20Nouns/TIPNR%20-%20Translators%20Individualised%20Proper%20Names%20with%20all%20References%20-%20STEPBible.org%20CC%20BY.txt); blob `94e636b8806eaa0501d2c7fc2a0fc87b3ffbea96` |
| [OpenBible Geocoding Data](https://github.com/openbibleinfo/Bible-Geocoding-Data) | [`7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f`](https://github.com/openbibleinfo/Bible-Geocoding-Data/commit/7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f) (2021-11-01) | `data/ancient.jsonl`: blob `b127b4446c6f4ba36ec62dde290c752afeb51bf3`; also `data/source.jsonl` and `readme.md` |
| [PatristicTextArchive/tipnr_data](https://github.com/PatristicTextArchive/tipnr_data) | [`6d359501643edfd9520d3a26fc77b6bd9d599cae`](https://github.com/PatristicTextArchive/tipnr_data/commit/6d359501643edfd9520d3a26fc77b6bd9d599cae) (2024-07-13) | `tipnr-persons-wikidata.tsv`: blob `abc3e21b9d08dc310066152f9b62858c4818f4eb`; also `README.md` and `scripts/Convert_TIPNR_data.py` |

*Blob identifiers above are Git object hashes, not independent SHA-256 checksums.* They pin exact Git content together with commit IDs; package checksums will be specified separately later.

**Upstream notices:** STEP declares CC BY 4.0 in its current README and original TIPNR header. Its README explicitly says TIPNR's descriptive prose was generated with Claude 3. **Exclude that prose from any verified biography or source evidence.** OpenBible's README declares its own dataset CC BY 4.0, but its images have varying licenses. The third-party PTA crosswalk has not undergone a separate rights or editorial provenance clearance; it is for research/candidate matching only. See #2 before redistribution.

## 2. What the source identifiers actually mean

The current original TIPNR file contains **multiline grouped records**, introduced by `$========== PERSON`, `$========== PLACE` and `$========== OTHER`. A group header's first tab-separated field looks like `Abraham@Gen.11.26-1Pe=H0085`. Its name plus disambiguating first-reference component is an **entity identifier**, not simply a search term. The suffix after the first reference contains additional reference-range / Strong-related annotations; do not conflate all names or Strong numbers.

The PTA conversion script derives simplified keys by taking `name@reference` and replacing `@` with `_`, truncating after `-` or `=`. This may not remain stable across TIPNR source revisions or distinguish added suffixed cases (e.g. `...a`/`...b`). A source-version-specific alias/canonical-ID migration mechanism will be needed for safe linking. For this audit the same simplified rule was applied to original headers only to **measure candidate overlap**, *not* to approve links.

OpenBible makes a crucial distinction in its README: an **ancient biblical place** is not necessarily the same as its **proposed modern location**. Its `linked_data` fields refer to dataset identifiers listed in `data/source.jsonl`: `s3b25cf` = TIPNR, `s7cc8b2` = Wikidata, `sf42caf` = Wikipedia. These opaque source keys should be resolved by `source.jsonl` in future reusable tools, rather than hardcoded. The `review` field may be `automatic` or `uncertain` (not individually reviewed); the `modifier` field may explicitly mean `not`, `modern`, `partial`, `redirect`, etc. A source link is **not** permission to ignore those qualifications.

## 3. Measured inventory and source overlap

### Original TIPNR (2026 snapshot)

Count the **actual records** after the explanatory template examples at the start of the file, not `$==========` headings in the documentation:

| Category | Records |
| --- | ---: |
| PERSON | **3,129** |
| PLACE | **1,006** |
| OTHER | **102** |
| **Total** | **4,237** |

The simplified keys derived from these 4,237 group headers were unique **within this snapshot**. This does **not** guarantee stability between snapshots.

### Third-party PTA person-to-Wikidata crosswalk (2024 snapshot)

| Property | Measured count |
| --- | ---: |
| Data rows | **3,237** |
| Distinct simplified TIPNR IDs | **3,236** |
| Rows with a syntactically valid `Q...` identifier | **856** (26.4% of rows) |
| Rows with an empty Q-ID | **2,381** |
| Distinct nonempty Q-IDs | **457** |
| Q-IDs attached to multiple rows | **136** |
| Of those, Q-ID groups spanning visibly different names | **13** |
| Rows whose simplified ID is absent from the current TIPNR source | **142** (**10** with nonempty Q-ID) |
| Rows matching current TIPNR PERSON / PLACE / OTHER categories | **3,006 / 2 / 87** |
| Nonempty Q-IDs among matching PERSON / PLACE / OTHER | **841 / 0 / 5** |

There is one exact duplicate row for `Malchijah_Ezr.10.25` (both links empty). **Do not interpret 856 populated cells as 856 verified distinct people.** Many Q-IDs have been assigned to several independently distinguished TIPNR records; some may be legitimate aliases or the same entity, but **the association is not independently validated**.

The mismatching 142 IDs are evidence of **cross-version or normalization differences**, not automatically 142 upstream errors. A public example with a nonempty Q-ID is `Jesus_Mat.1.1 → Q302` in the PTA table, whose exact simplified key does not occur in current TIPNR; this shows why source-version pinning is necessary, not that the referent is false.

### OpenBible ancient places (2021 snapshot)

| Property | Measured count |
| --- | ---: |
| `ancient.jsonl` valid records | **1,342** |
| Ancient records with a TIPNR linked-data ID | **1,172** |
| Ancient records with a Wikidata Q-ID | **655** |
| Ancient records with **both** TIPNR and Wikidata | **574** |
| Ancient records with a direct Wikipedia linked-data URL | **301** |
| Wikidata links marked `modifier=not` | **4** |
| Wikidata links marked `modifier=modern` | **6** |
| TIPNR linked IDs reused by multiple ancient entries | **147** groups |
| Wikidata Q-IDs reused by multiple ancient entries | **8** groups |

The 1,172 linked TIPNR IDs were compared to **current** simplified original TIPNR records:

- **1,032** reference a current **PLACE** record.
- **138** do not resolve by this strict simple-ID comparison: may be older keys, aliases, splits or unavailable entries; **investigate** rather than automatically guessing.
- **2** resolve to a current **PERSON** record: OpenBible's `Dedan` references `Dedan@Gen.10.7`, and `Perez-uzzah` references `Uzzah@2Sa.6.3`. These require source-context distinction, not blind person/place coercion.
- Of the 1,032 PLACE-resolving records, **493** also have a Wikidata Q-ID. **This is a technical intersection, not 493 verified place matches.**

OpenBible's 655 nonempty Wikidata links comprise **645 without a `modifier`**, **6 explicitly `modern`** and **4 explicitly `not`**. Reject `not` as an identity link; a modern-place target needs a separate modern-site relationship. The lack of a modifier is not enough on its own to prove scholarly identification.

## 4. Concrete ambiguous or incorrect candidate links

| Example | Evidence from snapshots | Required decision |
| --- | --- | --- |
| `Shimon_1Ch.4.20 → Q33923` | PTA maps Shimon in 1 Chronicles to [Saint Peter](https://www.wikidata.org/wiki/Q33923), a person appearing in the New Testament. | **Reject** as a person identity match. Q33923 has `Shimon` among its aliases, which is insufficient. |
| `Hoshea_2Ki.15.30 → Q7734` | PTA maps the Hoshea in 2 Kings to [Joshua son of Nun](https://www.wikidata.org/wiki/Q7734), which has `Hoshea` among its aliases. | **Reject** as a person identity match. The biblical figure in 2 Kings is not Moses' successor. |
| `John_Mat.3.1` and `John_Mat.4.21` | Separate TIPNR entries both have **empty** Q-IDs in PTA. | Keep unresolved until independently distinguished, not one generic “John” match. |
| `Mary_Mat.1.16`, `Mary_Luk.10.39` and other Marys | PTA has several separate Mary entries, all blank in that name group. | No automatic matching by a common given name. |
| `Jerusalem@Jos.10.1 → Q1218` | OpenBible links ancient Jerusalem with Wikidata Q1218. | Good *pilot candidate*, but distinguish ancient city from modern sites and photographs. |
| `Emmaus@Luk.24.13 → Q165887` | OpenBible has **6** candidate identifications for this ancient place. | A linked article must not choose one archaeological location as certain. |
| `Nod@Gen.4.16 → Q1929769` | A Wikidata ID is present even though the location is not established. | Do not infer coordinates or contemporary photos from the existence of the Q-ID. |
| `Bethlehem 1` and `Bethlehem 2` | OpenBible distinguishes `Q5776` and `Q604557` with different TIPNR identities. | Maintain separate places; never match on “Bethlehem” alone. |
| `Adamah`, `Avvim`, `Baal-hamon` | Their OpenBible Q-ID links carry `modifier=not`. | Exclude these negative links explicitly. |

**Editorial status:** the two obvious false person links above can be rejected on their individual evidence; no comprehensive per-record external Wikidata verification has been performed. All other candidate links remain **unreviewed**, including apparent positive examples.

## 5. Minimum decision procedure for an identity link

1. Pin original TIPNR/OpenBible source revisions and preserve the raw source identifier. Record any normalized alias separately. **Never silently replace an entity key because its first reference changed.**
2. Preserve entity class: PERSON, PLACE, OTHER, ancient place and modern location are **different types**. A geographic place can have several proposed modern identifications; one personal name can refer to several people.
3. Resolve a candidate Q-ID only from a **documented, source-backed connection**. Name equality, Wikidata label/alias, Strong number or verse similarity is insufficient.
4. Check the **actual Wikidata item class and identifying attributes**, the TIPNR references/relationships and OpenBible qualifiers. Explicit `modifier=not` rejects the link; `modifier=modern` may represent a **related modern location**, not the ancient entity.
5. Mark each proposed link **accepted / rejected / unresolved**. Store source IDs/versions, Q-ID, evidence URLs/references, kind of link (`same_entity`, `possible_site`, `related`), reviewer/date and rationale. Only separately reviewed **accepted same-entity** matches may power automatic article lookup.
6. Retain **both sides** of ambiguity: a rejected false match should not delete the original TIPNR entry or force an alternate match. Allow zero enrichment rather than a wrong biography/photo.
7. Do not treat inherited Wikipedia lead text, Wikidata assertions, STEP AI-written prose or image identity as independent validation of a candidate match. Licensing/media suitability are separately audited in #2.

A deterministic source ID is necessary for **reproducibility**, but not sufficient for **semantic truth**. Never promote a Q-ID solely because a line passes structural validation.

## 6. Reproduction method

The measurements above were made by reading pinned source blobs directly and applying these deterministic rules:

1. Split TIPNR on UTF-8 newlines. For each actual `$========== PERSON|PLACE|OTHER` group marker (not explanatory template blocks), take the first field of the following header line; identify `name@firstRef`, stop the firstRef at the first `-` or `=`, and construct the simplified comparison key `name_firstRef`.
2. Parse PTA `tipnr-persons-wikidata.tsv` as tab-separated rows. Count blank/nonblank Q-IDs, distinct IDs/Q-IDs, reverse Q-ID groups and simple-ID intersection with the current source.
3. Parse OpenBible `data/source.jsonl` to identify linked-data provider keys by `friendly_id`, then each `data/ancient.jsonl` JSONL object. Count presence and overlap of TIPNR/Wikidata/Wikipedia links and preserve `review`, `modifier` and ancient-vs-modern identity.
4. For cross-source intersection only, apply the *same simplified first-reference comparison* to OpenBible's TIPNR `name@reference` field. Report unresolved links as unresolved, not incorrect.
5. Keep a distinct manual review stage for the **actual Q-ID item** and historical identity. No calculation above establishes link precision.

For a future repeatable implementation, the audit should become an independently tested standard-library check over **local pinned input files**; avoid hardcoding OpenBible's opaque source keys or publishing bulk input datasets as proof. The source sizes (current original TIPNR about 8.2 MB, OpenBible ancient about 11.6 MB) are small enough for an ordinary one-pass local audit.

## 7. Decision and remaining work

**Decision:** a narrow pilot is **feasible**, especially for places where OpenBible already supplies candidate IDs and explicit geography/uncertainty; a fully automatic people-import based on the PTA crosswalk is **not safe**. Prioritize **precision over nominal coverage**.

**Still required before issue #1 can be considered fully complete:**
- Independently review a stratified set of real proposed Q-IDs against actual Wikidata item types, genealogy, citations and original TIPNR references; log decisions explicitly rather than relying on two easy negative examples.
- Audit the **138** strict OpenBible↔current-TIPNR nonmatches and the **147** reused TIPNR IDs at least by cause/sample, to distinguish obsolete aliases from split entities and valid place relations.
- Investigate additional category collisions and semantic differences across original versions, particularly 2024 PTA vs 2026 STEP, without rewriting upstream data.
- Agree on review evidence required to accept a verified pilot record. The rights/redistribution audit belongs to #2, and publication is not authorized.

**No package, downloadable release, app changes or changes to other repositories were made during this audit.**
