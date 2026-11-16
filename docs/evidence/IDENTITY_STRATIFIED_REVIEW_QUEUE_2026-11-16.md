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
