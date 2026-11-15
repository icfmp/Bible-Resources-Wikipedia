# Candidate identity spot checks — 15 November 2026

**Issue:** #1. **Purpose:** give human reviewers a useful negative/positive/ambiguous sample before any automated acceptance of TIPNR→Wikidata links. This document is **research evidence**, not the final machine-importable approved link index. The related source and coverage measurements are in [IDENTITY_SOURCE_AUDIT_2026-11-15.md](IDENTITY_SOURCE_AUDIT_2026-11-15.md).

## Sources and review method

- [PTA candidate crosswalk](https://github.com/PatristicTextArchive/tipnr_data/blob/6d359501643edfd9520d3a26fc77b6bd9d599cae/tipnr-persons-wikidata.tsv) at exact commit `6d359501643edfd9520d3a26fc77b6bd9d599cae`.
- [Original TIPNR](https://github.com/STEPBible/STEPBible-Data/blob/5de0a47f35f0fc13dfe1430d104e5db8a4285f9c/Proper%20Nouns/TIPNR%20-%20Translators%20Individualised%20Proper%20Names%20with%20all%20References%20-%20STEPBible.org%20CC%20BY.txt) at commit `5de0a47f35f0fc13dfe1430d104e5db8a4285f9c`.
- [OpenBible ancient places](https://github.com/openbibleinfo/Bible-Geocoding-Data/blob/7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f/data/ancient.jsonl), [its interpretation rules](https://github.com/openbibleinfo/Bible-Geocoding-Data/blob/7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f/readme.md) and linked Q-IDs at commit `7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f`.
- Each named Wikidata item was inspected by its public item page where accessible. **An item title matching the Bible name is corroboration, not independent proof of historical identification.** The original biblical reference and source relationships remain required.

**Verdicts below:** `REJECT` = explicit contradiction prevents direct identity match; `CANDIDATE` = plausible identity to include in the independently reviewed pilot, **not yet authorized for automatic import**; `UNRESOLVED` = more evidence needed; `EXCLUDE_DIRECT` = link explicitly not about the same entity (or not a geographical identity link).

## People: identity records must not collapse onto names

| Original STEP / PTA candidate | Wikidata item | Review verdict and evidence |
| --- | --- | --- |
| `Aaron_Exo.4.14` | [Q51676 — Aaron](https://www.wikidata.org/wiki/Q51676) | **CANDIDATE.** Identifier, name and biblical context align. Relationship/source verification still required. |
| `Abraham_Gen.11.26` | [Q9181 — Abraham](https://www.wikidata.org/wiki/Q9181) | **CANDIDATE.** Item is the Abraham of the patriarchal narratives; verify exact TIPNR entity and attributes before approval. |
| `Moses_Exo.2.10` | [Q9077 — Moses](https://www.wikidata.org/wiki/Q9077) | **CANDIDATE.** Same apparent Exodus referent. |
| `David_Rut.4.17` | [Q41370 — David](https://www.wikidata.org/wiki/Q41370) | **CANDIDATE.** The Ruth genealogy refers to David the king; confirm TIPNR reference and target item attributes. |
| `Abel_Gen.4.2` | [Q313421 — Abel](https://www.wikidata.org/wiki/Q313421) | **CANDIDATE.** The Genesis person is identified by the item. |
| `Peter_Mat.4.18` | [Q33923 — Saint Peter](https://www.wikidata.org/wiki/Q33923) | **CANDIDATE.** Disciple Peter appears in Matthew 4:18. This is not a reason to attach all forms of Simon/Shimon to him. |
| `Shimon_1Ch.4.20` | [Q33923 — Saint Peter](https://www.wikidata.org/wiki/Q33923) | **REJECT.** The Chronicles individual is not the first-century apostle. The Q-ID's alias “Shimon” likely caused a misleading name-based association. |
| `Joshua_Exo.17.9` | [Q7734 — Joshua son of Nun](https://www.wikidata.org/wiki/Q7734) | **CANDIDATE.** Identifies Moses' successor; compare Exodus reference and person's relationships. |
| `Hoshea_2Ki.15.30` | [Q7734 — Joshua son of Nun](https://www.wikidata.org/wiki/Q7734) | **REJECT.** Hoshea in 2 Kings 15:30 is the Israelite king, not Joshua. A shared earlier name/alias is not identity. |
| `Azariah_2Ch.26.17` | [Q313216 — Uzziah](https://www.wikidata.org/wiki/Q313216) | **REJECT.** The Azariah in 2 Chronicles 26:17 is the priest opposing King Uzziah; the target is the king. |
| `Mattathias_Luk.3.25` / `Mattathias_Luk.3.26` | [Q44020 — Matthias the Apostle](https://www.wikidata.org/wiki/Q44020) | **REJECT.** Figures in Luke's genealogy are not the Matthias chosen to replace Judas in Acts. The same Q-ID is legitimately used for `Matthias_Act.1.23`, but that does not rescue these two links. |
| `Abihud_1Ch.8.3` | [Q321170 — Abiud](https://www.wikidata.org/wiki/Q321170) | **UNRESOLVED / unsafe.** Q-ID is labeled for Abiud; the Chronicles Benjaminite must not automatically be merged with the individual in Matthew 1:13. Requires specific genealogical source evidence. |
| `Mary_Mat.1.16` and `Mary_Luk.10.39` | *(blank in the PTA file)* | **UNRESOLVED.** Correctly leaving these separate Mary identities unlinked is preferable to a general “Mary” lookup. |

## Places: ancient referent is not always the modern site

| OpenBible ancient identity | Wikidata candidate | Review verdict and evidence |
| --- | --- | --- |
| `Jerusalem` (`a15257a`; `Jerusalem@Jos.10.1`) | [Q1218 — Jerusalem](https://www.wikidata.org/wiki/Q1218) | **CANDIDATE**, but the item also represents the living modern city. Distinguish that from biblical-era boundaries and from a photo of a modern part of the city. |
| `Emmaus` (`ae7274b`; `Emmaus@Luk.24.13`) | [Q165887 — Emmaus](https://www.wikidata.org/wiki/Q165887) | **CANDIDATE for the biblical place concept**, not approval of coordinates. OpenBible preserves **six** proposed modern locations. Wikidata currently assigns a point and several `said to be the same as` statements to alternative sites; these are **not** six confirmed identities or a settled site. |
| `Nod` (`a1ad8e1`; `Nod@Gen.4.16`) | Q1929769 (as present in OpenBible) | **UNRESOLVED for article identity; no physical-site link**. OpenBible's resolution is `special: unknown_place`; no real-world location or photograph may be inferred. Wikidata page retrieval was not available for independent review in this pass. |
| `Bethlehem 1` (`a112427`) | [Q5776 — Bethlehem](https://www.wikidata.org/wiki/Q5776) | **CANDIDATE** for the Bethlehem associated with Genesis 35:16; do not merge with the other Bethlehem. |
| `Bethlehem 2` (`a308715`) | [Q604557 — Bethlehem of Galilee](https://www.wikidata.org/wiki/Q604557) | **UNRESOLVED as a strict ancient-entity identity; CANDIDATE for a related modern site.** Joshua 19:15 concerns ancient Bethlehem of Zebulun, while the Wikidata item describes the current settlement/moshav (including its 1948 inception). A published archaeological discussion identifies the present settlement as occupying the ancient site; this supports **site continuity/association**, not unqualified transfer of contemporary facts or photos to the biblical place. Do not confuse it with Bethlehem of Judea. |
| `Moreh 1` (`a38ad9f`) | *(no Q-ID)* | **UNRESOLVED.** Three ancient-place identification possibilities; no name-based fallback to `Moreh 2`. |
| `Moreh 2` (`a772880`) | [Q1092415 — Givat HaMoreh](https://www.wikidata.org/wiki/Q1092415) | **UNRESOLVED as exact same entity**. Q-ID denotes a modern geographical feature; accept only a reviewed *related modern place* relationship if supported, not unconditional ancient-entity equivalence. |
| `Adamah` (`afe1143`), `Avvim` (`a6d7a41`), `Baal-hamon` (`a304bb7`) | Q2605670, Q4828853, Q83879, respectively; each marked OpenBible `modifier=not` | **EXCLUDE_DIRECT**. OpenBible explicitly warns these Wikidata links are not about the same place; never load their articles/images as a verified place match. |

## Implications for the pilot and QA

- **Four concrete erroneous *person* patterns have been confirmed**: Shimon/Peter, Hoshea/Joshua, Azariah priest/Uzziah king, Mattathias/Matthias the Apostle. These cover name/alias sharing across eras, distinct persons in the same chapter and mixed NT genealogy identities. This is not an estimate of total table error rate.
- Even apparently obvious associations such as Aaron and Jerusalem remain **CANDIDATE**, pending documented identity evidence checks, because an editor must distinguish *plausible link* from *validated and publishable match*.
- The correct pilot should include accepted identity candidates, explicit rejections, unknowns and **relationship-only modern sites**. An offline resource should store the **kind of relationship**, not only a Q-ID.
- Full historical/genealogical attribution and source data reuse rights are not yet completed; #2 separately controls any redistribution. The master audit issue #1 should remain open until reviewers sign off on evidence rules and the outstanding cross-version cases.

No files copied from Wikimedia, no machine-readable published match index, no downloadable resource and no changes to the Bible application resulted from this check.

## Second-pass geographic identity warning (15 November 2026)

Reinspection identified a **relation-type problem even where the name and approximate geography are correct**:

1. **Emmaus**: the [OpenBible record](https://www.openbible.info/geo/ancient/ae7274b/emmaus) records six possible modern locations, with differing and incomplete confidence scores. [Wikidata Q165887](https://www.wikidata.org/wiki/Q165887) contains a coordinate and multiple [\"said to be the same as\" (P460)](https://www.wikidata.org/wiki/Property:P460) relationships. Neither property is enough to settle Luke 24's geographical identification. For an encyclopedia card, the article about the **biblical concept** may be relevant; a pinpoint marker or site-specific photograph requires a **separate** supported location decision. [BiblIndex's Emmaus name record](https://www.biblindex.org/en/bible-names/198) independently corroborates the Luke 24:13 / Q165887 *concept* cross-reference, but does not establish a modern site.
2. **Bethlehem of Zebulun**: [Wikidata Q604557](https://www.wikidata.org/wiki/Q604557) describes a **modern settlement**, including a 1948 inception and modern population/photographs. [Aviram Oshri's archaeological site description](https://library.biblicalarchaeology.org/book/the-new-encyclopedia-of-archaeological-excavations-in-the-holy-land/bethlehem-of-galilee/) discusses the ancient site underneath the present settlement. Treat the Wikidata link as a **related present-day site candidate** until the editorial contract specifies how to represent continuity; never import modern settlement facts as the biblical city's attributes.
3. **General rule**: a candidate Q-ID can be *about a place*, *located at the proposed ancient site*, or *about a successor settlement*. These are distinct relationships. An accepted **bibliographic/topic link** does **not** authorize imported Q-ID coordinates, date of inception, modern statistics, images, or other statements without their own period and referent checks.

This is an **editorial hazard finding**, not a measured false-match rate. No Q-ID is approved for bulk import by this note.
