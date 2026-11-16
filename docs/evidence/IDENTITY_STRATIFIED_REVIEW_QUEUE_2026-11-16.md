# Fixed stratified identity-candidate review queue (16 November 2026)

**Scope:** issue #8 source-backbone evaluation, complementary to #1 and #4. **Status:** source-derived **selection frame**, not 24 individually approved identities or an editorial pass. No candidate Q-ID or location is accepted merely by appearing in a table.

## Source frame and reproducibility

- **People candidates:** [PTA TIPNR→Wikidata TSV](https://github.com/PatristicTextArchive/tipnr_data/blob/6d359501643edfd9520d3a26fc77b6bd9d599cae/tipnr-persons-wikidata.tsv) at exact commit `6d359501643edfd9520d3a26fc77b6bd9d599cae`. This is an **untrusted third-party candidate table**, *not* the exact original current STEP TIPNR dataset or a set of verified identities. The existing source audit records version mismatches against current STEP TIPNR.
- **Places candidate groups:** [complete OpenBible / TIPNR structural group inventory](OPENBIBLE_TIPNR_JOIN_TRIAGE_2026-11-15.md), whose upstream data are pinned to [OpenBible commit `7eb18a5`](https://github.com/openbibleinfo/Bible-Geocoding-Data/tree/7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f) and [STEP commit `5de0a47`](https://github.com/STEPBible/STEPBible-Data/tree/5de0a47f35f0fc13dfe1430d104e5db8a4285f9c). **Place units here are linked STEP ID groups**, not source-unique ancient sites. Every member ancient entry and its own Q-ID must be reviewed later, individually.
- **Algorithm:** within each source stratum, sort its records by unsigned 32-bit **FNV-1a** over the exact UTF-16-code-unit string `BibleResourcesWikipedia|2026-11-16|<original_id>`, breaking ties lexicographically by `<original_id>`. Start with the standard FNV-1a initial value `2166136261`, XOR each code unit, multiply by `16777619` with modulo `2^32`. Select the first four of each people stratum (within repeated-QID rows, retain the first selected record **per Q-ID**); select the first three of each place stratum, skipping any repeated STEP ID already selected in a prior stratum. The two source universes and distinct group types have intentionally **not** been pooled.
- **Why stratify:** naive random sampling from the PTA table would draw mostly *blank* Q-IDs (2,381 / 3,237), giving little insight into risky positive associations; oversampling risky strata lets us characterize failure **types**, but does not yield a population-wide accuracy estimate without proper weighting, completed independent review and version reconciliation.
- The repeated-place group inventory includes one-QID/no-QID and multiple-QID groups **not because every group member denotes the same entity** but specifically to test that assumption. The 76 syntactic nonmatching STEP IDs are *another overlapping stratum*; duplicate IDs are skipped here.

## Full-frame counts

| People (PTA rows) | Count |
| --- | ---: |
| Rows with blank Q-ID | **2,381** |
| Rows with a Q-ID occurring on exactly one PTA row | **321** |
| Rows whose Q-ID occurs on multiple PTA rows | **535** |
| **Total** | **3,237** |

856 populated Q-ID rows represent 457 distinct Q-IDs; **136** Q-IDs occur on multiple rows. This is a *frequency distribution*, not 535 false matches or 136 proven collisions.

| Place group / diagnostic category | Count |
| --- | ---: |
| Reused OpenBible STEP IDs with multiple different Q-IDs | **37** |
| Reused STEP IDs with one Q-ID | **71** |
| Reused STEP IDs with no Q-ID | **39** |
| **Total distinct reused-ID groups** | **147** |
| Distinct STEP-linked IDs with no strict current TIPNR key | **76**, overlapping the reused groups |

## Selected **people source candidates** — four from each stratum

| Stratum | Original PTA TIPNR ID | Q-ID from PTA (candidate ONLY) |
| --- | --- | --- |
| Unique-QID row | `Lois_2Ti.1.5` | Q25344412 |
| Unique-QID row | `Asenath_Gen.41.45` | Q723681 |
| Unique-QID row | `Ishbak_Gen.25.2` | Q594903 |
| Unique-QID row | `Bartimaeus_Mrk.10.46` | Q809440 |
| Repeated-QID row | `Shemaiah_Ezr.8.16` | Q2090113 |
| Repeated-QID row | `Azariah_2Ch.28.12` | Q313216 |
| Repeated-QID row | `Jachin_Gen.46.10` | Q18088109 |
| Repeated-QID row | `Abdon_Jdg.12.13` | Q308320 |
| No Q-ID | `Zuriel_Num.3.35` | *(blank)* |
| No Q-ID | `Uzzi_Neh.12.19` | *(blank)* |
| No Q-ID | `Jehiel_1Ch.15.18` | *(blank)* |
| No Q-ID | `Eliehoenai_Ezr.8.4` | *(blank)* |

**Do not label all “unique-QID” rows correct.** That label means only that *a Q-ID occurs once inside this particular PTA file*; it is not an authority check. Likewise an empty cell is not evidence the historical referent has no Wikidata item. Because the sample is from PTA, not all original TIPNR people, a weighted estimate cannot be generalized to the entire STEP corpus.

## Selected **place linked-ID group** checks — three from each stratum

| Stratum | Original linked STEP ID | Original ancient source names / concern |
| --- | --- | --- |
| MULTIPLE_QIDS | `Syria@Jdg.10.6` | Syria 1; Syria 2 (Q770281 / Q207118) |
| MULTIPLE_QIDS | `Nebo_Mount@Deu.32.49` | Abarim; Mount Nebo (Q337141 / Q680161) |
| MULTIPLE_QIDS | `Samaria@1Ki.13.32` | Samaria 1; Samaria 2 (Q1757438 / Q1294629) |
| ONE_QID | `Beersheba@Gen.21.14` | Beersheba 1; Beersheba 2 (one populated Q534596) |
| ONE_QID | `Beth-horon_Lower@Jos.16.3` | Beth-horon; Lower Beth-horon (one populated Q1268514) |
| ONE_QID | `Zoar@Gen.13.10` | Zair; Zoar (one populated Q218016) |
| NO_QID | `Helkath@Jos.19.25` | Helkath; Hukok |
| NO_QID | `Gilgal@Deu.11.30` | Beth-gilgal; Geliloth; Gibeath-haaraloth; Gilgal 1/3/4 |
| NO_QID | `Arad@Num.21.1` | Arad 1; Arad 2 |
| STRICT_KEY_NONMATCH | `Shiloah@Isa.8.6` | Shiloah, no same-name full STEP header |
| STRICT_KEY_NONMATCH | `Shinar@Gen.10.10` | Shinar, no same-name full STEP header |
| STRICT_KEY_NONMATCH | `Shaalbim@Jdg.1.35` | Shaalbim, same-name PLACE header but different first-reference ID |

**Size distinction:** 12 people rows + 12 *place groups* = **24 selected review units**, but the latter include multiple original OpenBible ancient entries (at least **25** child ancient records for these particular groups). Do **not** report these 24 units as 24 verified biblical entities, 24 independently checked Q-IDs, or a 24-record population accuracy estimate. The next review must annotate **every** original entry and check the named passage/variant before any identity vote.

## Review fields and stopping rule

For each selected *person* and **each selected place child entry**, preserve provider, original source ID/commit, original exact label, historical category, occurrence context, candidate Q-ID and source modifier; then record independent original-language/biblical countercheck, source-independent authority evidence (or inability to establish it), `accepted/rejected/unresolved`, relationship kind and field-specific permissions (article/facts/coordinate/image).

**Next actions:** inspect exact upstream per-entry source rows and changed TIPNR keys; compare the same individuals and place subjects with version-pinned ACAI and Theographic; resolve enough candidates to assess practical coverage **only within each sampled stratum**. Reconcile third-party source dependence and differing versifications. Avoid a single all-source “match accuracy” percentage unless a valid weighted population estimate is possible.

No script was committed for this one-time deterministic sample; the rule above can be reproduced with common language libraries and the pinned source records. Do not launch Codex or build an importer from this review queue.

## First sampled-person identity checks (16 November 2026)

The following checks use **source-pinned PTA candidate rows** (table above), the actual cited biblical passages, and external public identity/authority pages. **The external Wikidata and BiblIndex page revisions have not all been pinned**; this is strong editorial triage evidence, *not* a final machine-readable accepted identity index or independent signed-off review. Source link data and explicit biblical facts should not be mistaken for proof that every Wikidata statement is correct.

| Reviewed association / diagnostic control | Source-backed evidence | Provisional direct-identity disposition |
| --- | --- | --- |
| `Shemaiah_Ezr.8.16 → Q2090113` | Ezra 8:16 names a leader summoned **during Ezra's return**, whereas [BiblIndex Shemaiah](https://dapytains.biblindex.org/en/bible-names/1673) ties [Q2090113](https://www.wikidata.org/wiki/Q2090113) to the **prophet addressing Rehoboam** (1 Kings 12:22); [Ezra 8:16 passage](https://www.biblegateway.com/passage/?search=Ezra+8%3A16&version=NIV). | **REJECT DIRECT (high-confidence contradiction).** Different historical people/eras; preserve the erroneous candidate and the correct prophet row separately. |
| `Azariah_2Ch.28.12 → Q313216` | [2 Chronicles 28:12](https://tips.translation.bible/story/sil-translators-notes-on-2-chronicles-2812/) names **Azariah son of Jehohanan**, an Ephraimite leader; [Wikidata Q313216](https://www.wikidata.org/wiki/Q313216) and [BiblIndex](https://www.biblindex.org/fr/bible-names/5) identify **Uzziah/Azariah the king of Judah**, son of Amaziah. | **REJECT DIRECT (high-confidence contradiction).** A king's alternative name does not make every Azariah in Scripture the king. |
| `Jachin_Gen.46.10 → Q18088109` | [BiblIndex Jachin](https://jerihna.sourceschretiennes.org/en/bible-names/1007) links this Q-ID to **Simeon's son** and lists Genesis 46:10 and Exodus 6:15. | **CANDIDATE (supported; not independently signed off)** for this particular person. |
| `Abdon_Jdg.12.13 → Q308320` | [Wikidata Q308320](https://www.wikidata.org/wiki/Q308320) and [BiblIndex](https://www.biblindex.org/en/bible-names/17) expressly describe **Abdon the judge in Judges 12:13**. The Wikidata page retrieved in this pass exposed a previous [page revision `2521607466`](https://www.wikidata.org/w/index.php?title=Q308320&oldid=2521607466); verify an exact entity revision before approval of downstream fields. | **CANDIDATE (supported; not independently signed off)** for this particular judge. |

### Two important *same-Q-ID* negative sibling controls

The same pinned PTA TSV assigns:

- `Q18088109` to `Jachin_Gen.46.10`, `Jachin_1Ch.9.10`, `Jachin_1Ch.24.17`, and **`Jachin_1Ki.7.21`**. But [1 Kings 7:21](https://www.biblegateway.com/passage/?search=1+Kings+7%3A21&version=ESV) identifies **Jachin as the name of a temple pillar**, not a person at all. Thus the last association is a **clear category-error direct-identity rejection**; it must not be silently replaced by the biblical person Q-ID.
- `Q308320` to `Abdon_Jdg.12.13`, `Abdon_1Ch.8.23` and `Abdon_1Ch.8.30`. The selected Judges row has a plausible correct anchor, but the other Chronicles rows refer to Benjaminite genealogy contexts and require independent namesake disambiguation, **not automatic inheritance** of the judge's Q-ID. This report does not sign off on these sibling rows.

### Why this matters for choosing TIPNR or ACAI

- A **repeated Q-ID is not always wrong**: some source records may legitimately refer to the same person under several names or translations, while others are definitively unrelated.
- A Q-ID that is valid for **one** source row must **never be inherited by every same-name row**.
- These negative examples arise from the **third-party PTA→Wikidata crosswalk**. They are **not evidence that the original TIPNR naming inventory contains these erroneous Wikidata links**: the distinction between **source entity** and **external candidate association** is central to the audit.
- ACAI's original-language per-token `explicit_instances` can potentially resolve *which occurrence* a user clicked; its broader `references` list and `primary_id` must not be conflated with an approved historical entity identity. For example, in pinned ACAI `place:Gadara` the `references` list has four Gospel verses but `explicit_instances.SBLGNT` contains one Matthew token; `place:Gerasa` contains four SBLGNT token groups and shares the verses. The historical cities still remain distinct regardless of editorial grouping for verse occurrences.

**Partial status only:** two sampled PTA associations show clear direct-identity contradictions, two are promising contextually supported candidates; no weighted error-rate estimate is defensible from these four checked rows, and the rest of the fixed sample remains unreviewed.

## Four sampled unique-QID candidates — positive-control triage

The first four **unique-QID-in-PTA** rows were also compared with the corresponding pinned ACAI original people JSON. The following are **supported identity candidates**, not editorially approved crosswalk entries, and have no approved Wikidata facts, images or prose:

| PTA candidate | Independently inspectable occurrence/authority data | ACAI source file (release 7 Nov 2026) | Preliminary result |
| --- | --- | --- | --- |
| `Lois_2Ti.1.5 → Q25344412` | [BiblIndex Lois](https://www.biblindex.org/en/bible-names/1195): grandmother of Timothy, 2 Tim 1:5, that Q-ID | [`person:Lois`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Lois.json), blob `32a23f4cc70e14e40ae142d6d661a35e2e6adfcd`, exact TIPNR source identifier, `references=[55001005]` | **SUPPORTED CANDIDATE**, full article facts/media unapproved. |
| `Asenath_Gen.41.45 → Q723681` | [BiblIndex Asenath](https://www.biblindex.org/en/bible-names/319): daughter of Poti-phera, wife of Joseph, Gen 41:45 | [`person:Asenath`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Asenath.json), blob `0d4aff6af3d636ba811a8f99896fa96e3ca13f8e`, TIPNR `Asenath@Gen.41.45-` | **SUPPORTED CANDIDATE**. |
| `Ishbak_Gen.25.2 → Q594903` | [BiblIndex Ishbak](https://www.biblindex.org/en/bible-names/1079): Abraham and Keturah's son, Gen 25:2 | [`person:Ishbak`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Ishbak.json), blob `d01b3161feb54e9ade0c6575369c37837248238c` | **SUPPORTED CANDIDATE**. |
| `Bartimaeus_Mrk.10.46 → Q809440` | [BiblIndex Bartimaeus](https://www.biblindex.org/en/bible-names/427) and [Wikidata Q809440](https://www.wikidata.org/wiki/Q809440): blind man healed near Jericho, Mark 10:46 | [`person:Bartimaeus`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Bartimaeus.json), blob `bc89a2a5ce1ac48d8a0699fd738423839e30623c` | **SUPPORTED CANDIDATE**. |

**Important limits:** this checks a person-name/type/reference combination across sources, but ACAI incorporates TIPNR, and a BiblIndex page carrying the same Q-ID is not by itself an independent historical proof for all assertions in Wikidata. The biblical passages and explicit person relationships do support these subject-level candidate identities; independent signed-off review and exact Wikidata item revisions still have to be recorded. **Do not treat 4/4 supported on this selected stratum as a global accuracy statistic.**

**Cumulative person-candidate triage in this file:** 8 out of the 12 selected PTA source rows have some externally checkable evidence: 2 **direct identity rejected**, 6 **contextually supported candidates** (four unique-QID and two repeated-QID). The remaining **four blank-QID** candidates have not yet been reviewed. The additional Jachin temple-pillar sibling case is a **separate negative control**, not a ninth selected person row.
