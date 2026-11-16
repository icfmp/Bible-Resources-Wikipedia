# Theographic geographic identity diagnostics and cross-source comparison (16 November 2026)

**Issue:** #8; related #1 and PR #9. **Status:** reproducible full-file **structural** analysis plus focused entity diagnostics, **not** independent historical identity validation, an overall false-positive rate, or an approved architecture decision.

## Provenance and method

Source: [Theographic Bible Metadata](https://github.com/robertrouse/theographic-bible-metadata), commit [`18cb045bece3b0a3754d1603dc94df81307bae43`](https://github.com/robertrouse/theographic-bible-metadata/tree/18cb045bece3b0a3754d1603dc94df81307bae43) (16 November 2026 06:52 UTC); original [`CSV/Places.csv`](https://github.com/robertrouse/theographic-bible-metadata/blob/18cb045bece3b0a3754d1603dc94df81307bae43/CSV/Places.csv), Git blob `93b8e17b13f9aee904f8ec633867dc154f7eb2b0`.

- A single read-only audit parsed the **entire original UTF-8 CSV** with a proper quote-aware CSV parser (handling embedded commas, doubled quotes, and multiline fields). No dataset was rewritten or normalization published.
- Each well-formed record was analyzed as one CSV row; latitude/longitude comparisons used decimal degrees, valid coordinate bounds and haversine distance on an Earth-radius 6,371 km sphere. Only complete numeric coordinate pairs entered pairwise comparisons.
- The comparison treats `recogitoStatus` and `precision` as **distinct metadata fields**. A `VERIFIED` Recogito candidate is **not automatically an archaeological proof** or a guarantee of close-to-point agreement. Regional features can legitimately have different representative centroids.
- No general cutoff was used to label a mismatch an identity *error*. Distances over 100/500 km are **triage flags**, not false-match or precision statistics.
- Cross-references: source's [geospatial guide](https://github.com/robertrouse/theographic-bible-metadata/blob/18cb045bece3b0a3754d1603dc94df81307bae43/docs/geospatial-data.md), [source bibliography](https://github.com/robertrouse/theographic-bible-metadata/blob/18cb045bece3b0a3754d1603dc94df81307bae43/docs/data-source-bibliography.md), [data-quality ledger](https://github.com/robertrouse/theographic-bible-metadata/blob/18cb045bece3b0a3754d1603dc94df81307bae43/data-quality/issues.yaml), and the separately [pinned ACAI spot-check](ACAI_BACKBONE_SPOTCHECK_2026-11-16.md).

## Complete structural counts — current CSV revision

| Metric (CSV only) | Observed |
| --- | ---: |
| Complete, well-formed place rows | **1,296** |
| Rows with both chosen `latitude` and `longitude` | **1,271** |
| Rows with a nonblank `precision` | **542** |
| Rows with blank `precision` | **754** |
| `precision=Rough` | 348 |
| `precision=Related-Surrounding` | 111 |
| `precision=Related-Within` | 57 |
| `precision=Unlocated` | 22 |
| `precision=Center` / `Precise` | 2 / 2 |
| Rows with `canonicalPlace` | **255** |
| `recogitoStatus=UNVERIFIED` | **998** |
| `recogitoStatus=VERIFIED` | **179** |
| `recogitoStatus=NOT_IDENTIFIABLE` | **95** |
| Blank `recogitoStatus` | **24** |
| Valid Recogito-coordinate / chosen-coordinate pairs | **416** |
| Such pairs differing by more than 100 km | **171** |
| Such pairs differing by more than 500 km | **136** |
| Over-100 km pairs with `recogitoStatus=UNVERIFIED` | **150** |
| Over-100 km pairs with `recogitoStatus=VERIFIED` | **21** |
| Valid OpenBible-coordinate / chosen-coordinate pairs | **1,269** |
| Such pairs differing by more than 100 km | **19** |

**Documentation mismatch to investigate:** the checked [geospatial guide](https://github.com/robertrouse/theographic-bible-metadata/blob/18cb045bece3b0a3754d1603dc94df81307bae43/docs/geospatial-data.md) describes 1,298 place rows and 1,272 with coordinates, whereas this exact CSV yields 1,296 and 1,271. Its **542 populated precision fields** agree with this revision. This may be an outdated document or a different export scope, *not proven missing historical locations*. Do not silently choose the larger count.

**Interpretation:** many >100 km comparisons concern **large regions, countries, seas and rivers** where different centroids can be defensible. For example, the `VERIFIED` cases of the Mediterranean Sea and Nile necessarily cannot be judged by a point-to-point threshold. The observed Recogito pairs from modern homonyms (e.g. a town in the United States) are, however, useful **specific negative regression candidates** for an automated place-identity importer.

## Selected same-entity comparisons — exact record values

| Referent | Theographic record(s) and original data | Comparison with ACAI / OpenBible | Editorial outcome |
| --- | --- | --- | --- |
| Emmaus (Luke 24:13) | `emmaus_382`: `recogitoLat/Lon=56.78055,36.115`, `recogitoStatus=UNVERIFIED`; selected `latitude/longitude=31.83945022,34.98952933`. | The **same** Recogito candidate appears in [ACAI `place:Emmaus`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Emmaus.json). OpenBible has multiple proposed ancient sites. | **Confirmed unsuitable candidate for biblical Emmaus; chosen alternative still unresolved**. Theographic's *chosen point* is **not** the implausible Recogito point. |
| Bethlehem in Zebulun (Josh 19:15) | `bethlehem_219`: `recogito=31.70487,35.20376`, `UNVERIFIED`; chosen `32.735379,35.189704`. | Identical discrepant Recogito proposal in [ACAI `place:Bethlehem.2`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Bethlehem.2.json); the northern coordinate matches OpenBible. | **Reject borrowing that Recogito candidate as a northern-Bethlehem pin**; no blanket approval of northern site. |
| Bethlehem of Judah / judge Ibzan | `bethlehem_218` has Judges 12:8/10 **in addition to** clear Judah-place verses, while `bethlehem_219` has Joshua 19:15. | OpenBible distinguishes Bethlehem 3 for Ibzan and provisionally favors the Galilean city, while also recording alternatives. | **Unresolved verse-occurrence association**. Do not automatically infer that Judges 12:8/10 is specifically Bethlehem of Judah. |
| Lehem (1 Chr 4:22) | `lehem_725` has only 1 Chr 4:22, selected coordinate near Judah Bethlehem, `recogitoStatus=UNVERIFIED`, and **no** `canonicalPlace`. | ACAI instead has `place:Lehem` marked `is_person=true` **yet** `primary_id=place:Bethlehem`. OpenBible records a possible non-place interpretation. | **Unresolved person/place kind and location.** Theographic avoids one type of identity collapse but still provides a pin for an uncertain referent. |
| Mizpah in Benjamin / Arimathea | `mizpah_811` has `otherNames=arimathea_90,ramathaim-zophim_977,mizpeh_812,ramah_975`, and `recogitoStatus=NOT_IDENTIFIABLE`. | OpenBible tracks distinct ancient entries and proposed identity relations under the same linked TIPNR ID. | **Do not collapse Arimathea and Mizpah identities** merely because `otherNames` groups them. No validated physical-site pin. |
| Nod (Gen 4:16) | `nod_902` is `Unlocated`, with no chosen coordinates. | ACAI `place:Nod` also has no `geocoordinates`. | **Good no-location behavior**, but not an identity sign-off. |
| Gadara and Gerasa | **No rows with `placeLookup` or `displayTitle` containing `gadara`, `gerasa` or `gerges` were found in this CSV.** | ACAI groups `place:Gadara` under `place:Gerasa`; OpenBible distinguishes ancient settlement IDs. | **Coverage gap in this particular Theographic CSV for the pilot**, not evidence that the source judges those sites identical or that no other table or export has a relevant mention. |
| Abana (2 Kgs 5:12) | `abana_1` has OpenBible `33.545097,36.224661`, Recogito `41.97858,34.011` (UNVERIFIED), and a different selected `33.514135,36.294504`. | Selected source-specific coordinates are not universal identities. | **Require source-level review**; never overwrite the original candidate or promote Recogito's coordinate. |
| Abel (2 Sam 20) | `abel_4` is a **place** with `verses=2Sam.20.14,15,18`; `dictText` begins with Easton's **Abel son of Adam** article; `canonicalPlace=abel-beth-maacah_5`. | The dictionary entry covers *several homonymous subjects*; a name-indexed dictionary text is not a validated identity mapping. | **Separate lexical/dictionary article and biblical place identity**; no automatic reuse of entire article for that place. |

This table deliberately compares *the same referents*, but the choice of cases is diagnostic and biased toward known anomalies. It provides **no measured error rate** or evidence that one provider's entire corpus is superior.

## Existing upstream tracking and provenance independence

Theographic's own [data-quality ledger](https://github.com/robertrouse/theographic-bible-metadata/blob/18cb045bece3b0a3754d1603dc94df81307bae43/data-quality/issues.yaml) includes **DQ-0031**, a `needs-research` issue on **678 coordinate discrepancies between its Airtable places and GeoJSON**: 390 at 1–25 km and 288 above 25 km. This is **a different comparison** from our Recogito/selected-coordinate counts; do not add the two figures. The geographic follow-up should link to that existing issue rather than create duplicate reports.

Theographic's [bibliography](https://github.com/robertrouse/theographic-bible-metadata/blob/18cb045bece3b0a3754d1603dc94df81307bae43/docs/data-source-bibliography.md) says it uses TIPNR for **people**, OpenBible and Recogito for **places**, and Easton for text. ACAI independently **imports Theographic as one of its inputs**. Thus Theographic + ACAI agreement can be *correlated reuse* rather than two separate historical attestations; even agreement on an ancient-site coordinate is not archaeological proof.

## Quality gates that this audit suggests (generic, not one-off fix code)

1. Keep **source row ID, provider, source commit, relationship type, occurrence context, and source-specific precision** together. A selected coordinate is a reviewed output with its own provenance, never automatically the coordinates of every linked name or site.
2. Separate **biblical referent**, alternative toponym used in a textual tradition, modern city, named region, uncertain ancient identification and homonymous dictionary headword.
3. Treat `recogitoStatus`, `canonicalPlace`, `otherNames` and ACAI `primary_id` as **provider-native claims**, not unconditional same-place equivalence. Never use `not`-qualified OpenBible links as identities.
4. Test no-pin cases and unsupported word-to-person assignments as **successful abstention**, not missing-data faults.
5. Keep source-specific attribution/licensing: Theographic is CC BY-SA 4.0 and combines externally sourced prose; that license cannot silently relicense Wikipedia text, Commons images or other imports.
6. Compare the source data and previous source revisions before asking upstream maintainers for a specific, reproducible correction. Do **not** fix open-source originals locally solely to satisfy a downstream bulk join.

**No package, importer, approval of candidate Q-IDs, source rewrite, new production script, or Bible application change was made.**
