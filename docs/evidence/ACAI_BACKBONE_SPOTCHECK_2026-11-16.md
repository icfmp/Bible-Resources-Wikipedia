# ACAI identity backbone: pinned pilot diagnostics (16 November 2026)

**Related issue:** #8. **Status:** evidence-only review of deliberately selected original records; **not** an approved crosswalk, a representative sample, a license clearance, or a decision to replace TIPNR. This report does not authorize source modification, Bible integration, automated bulk matching or publication.

## Exact inspected revision and scope

- **ACAI:** [BibleAquifer/ACAI commit `5375d0d334bb6d635ef1813e4d3df58eb30efcca`](https://github.com/BibleAquifer/ACAI/tree/5375d0d334bb6d635ef1813e4d3df58eb30efcca), committed **2026-11-07 00:23:36 UTC**, matching the tagged 2026-11-07 release date. Individual file Git blobs are recorded below where relevant. Follow-up must verify release tag resolves to this exact commit and pin the distribution assets if used.
- **Source-level documentation:** [root README](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/README.md), blob `5efdc49f779a37b803d858d22da9cf076239e616`; [people README](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/README.md), blob `7a684c71635bd43c529d5f4359059319d5729832`; [places README](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/README.md), blob `4cc9d8bdd3cd22065075bc634459fa288ed0a0e9`; [license](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/LICENSE.md), blob `132b6b53c8577f7f0d893c6b4be9d48975ed4384`.
- Comparison context: the project's [pinned STEP/OpenBible structural audit](OPENBIBLE_TIPNR_JOIN_TRIAGE_2026-11-15.md) and [identity spot checks](IDENTITY_SPOTCHECK_2026-11-15.md). Those record the **different** original STEP/OpenBible revisions; this is not a synchronized three-source snapshot.
- Method: fetch actual selected ACAI `people/json/*.json` and `places/json/*.json` at this **full commit SHA**, inspect type, `id`, `primary_id`, `alternate_sources`, `referred_to_as`, `possibly_same_as`, `references`, `is_person` and provider-tagged `geocoordinates`. Check English/French descriptions for explicit ambiguity. Hand-picked diagnostic records are neither random nor sufficient to compute dataset-wide precision or completeness.

**Source dependence is explicit.** ACAI's people and places READMEs say TIPNR performed best among their inputs at grouping alternate references, so they used it as a base and combined Macula, UBS dictionaries, Theographic/viz.bible, and (for places) OpenBible and other curated inputs. Two datasets that both rely on TIPNR **are not independent identity witnesses**. ACAI says word-level Hebrew coverage and referent annotations are still incomplete. Its localized prose (including French `fra`) is *curated external text*, not evidence merely by being published.

## Strengths verified in concrete people entries

| ACAI original file / ID | Distinguishing original fields | Observed result / limit |
| --- | --- | --- |
| [`Abraham.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Abraham.json), blob `4405b87d52f12d01f10aff2305181b9423bad3f2`; [`Abram.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Abram.json), blob `70b87fdd69da0b77863b4dbaa3fc2e6fa81335e1` | `person:Abraham` is primary; `person:Abram` has `primary_id: person:Abraham` and reciprocal `referred_to_as` | Correctly represents two biblical names of one referent in this selected case, while retaining each name form's own record. Not proof of global correctness. |
| [`Shimon.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Shimon.json), blob `ea4b8f36f80841e265aae7bd77107127b0869870`; [`Simon.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Simon.json), blob `10a64487315a5d1b1ce1085af4aae427564cb464` | `person:Shimon` is primary with `13004020` (1 Ch 4:20); `person:Simon` has primary `person:Peter`, NT references | Unlike the tested **external PTA→Wikidata** false link, ACAI keeps the Old Testament Shimon separate from Peter. |
| [`Hoshea.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Hoshea.json), blob `bae8e82affb13245d7d9c216d7eb8153c66928b0`; [`Joshua.2.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Joshua.2.json), blob `1ea2830bb29c1a278833e24aed7aad8f69e9d69d` | `person:Hoshea` references 2 Kgs 15:30 (king of Israel), distinct from `person:Joshua.2`, Moses' successor, whose variants include `person:Hoshea.4` | Distinguishes similarly named individuals, provided consumers use full IDs and biblical occurrence context; not the same `Hoshea`. |
| [`Mattathias.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Mattathias.json) and [`Mattathias.2.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Mattathias.2.json), blob `89fbb076a8fcebaac9e115874d1f889f4ede07be`; [`Matthias.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Matthias.json), blob `f06d88215bb50069e989fd4218b35854cad42e8f` | Two Mattathias records explicitly reference **Luke 3:25** vs **Luke 3:26**; Matthias references Acts 1:23/26 and has a different ID | Avoids the external crosswalk's erroneous collapse of Luke's genealogical names onto the apostle. |
| [`Mary.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Mary.json), [`Mary.2.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Mary.2.json), [`Mary.3.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Mary.3.json), [`Mary.4.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Mary.4.json) | Separate IDs for Jesus' mother, mother of James/Joses, sister of Martha/Lazarus (Luke 10:39), wife of Clopas | Preserves named individuals, not a catch-all Mary. A versioned ID-stability study remains necessary before treating `.2`, `.3`, etc. as permanent across releases. |
| [`Teman.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/people/json/Teman.json), blob `139dfaba2ed51bf0229ba2bdba86541f50dd4e57`; [place `Teman.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Teman.json), blob `c50b76841b761fea2e8d4c03d0d0417b3881ebab` | `person:Teman` uses Gen 36:11 and `place:Teman` is an Edomite region | Namespaced type is essential, even when user-visible name is identical; historic source IDs and exact references must be kept. |

**Limited positive finding:** ACAI is a compelling candidate for a *typed source of named-entity occurrences and alternate names*. These findings do **not** endorse it as an infallible canonical identity index, prove its whole word-level alignment, or approve any Wikidata enrichment.

## Non-negotiable place-level hazards seen in the actual JSON

### A. Gadara / Gerasa: distinct ancient cities, merged primary ID

- [`places/json/Gadara.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Gadara.json), Git blob `ec11654d4f81a2dfd5eed39a121cbb5069c98f54`: `id=place:Gadara`, **`primary_id=place:Gerasa`**, `referred_to_as=[place:Gerasa]`, `geocoordinates.biblica-maps=(32.65592, 35.67815)`, French descriptive label locates the Decapolis city at **Umm Qais**.
- [`places/json/Gerasa.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Gerasa.json), Git blob `5128101608ec8a411f3ef3d0dfac0b16cbd0b373`: `id=primary_id=place:Gerasa`, `referred_to_as=[place:Gadara]`, `geocoordinates.biblica-maps=(32.2736, 35.89071)`, French description places it as a **different Decapolis city** southeast of Galilee.
- Both records include the same Gospel pericope references (Matthew 8:28, Mark 5:1, Luke 8:26/37), but their own coordinates and descriptions distinguish their *physical* sites. The [pinned OpenBible triage](OPENBIBLE_TIPNR_JOIN_TRIAGE_2026-11-15.md) also has two separate ancient entries and Q-IDs under one source-linked STEP ID.

**Failure mode:** interpreting `primary_id` as strict geographical sameness collapses distinct physical settlements. This may be an editorial decision to group alternative Gospel *designations*, not necessarily an upstream editorial mistake; it still **must not** authorize a place identity merge, one coordinate, or one place image. Preserve the source's original relationship and uncertain biblical text identification as distinct from physical-site identity. Passage name variants require their own textual-evidence study.

### B. Lehem: classified as possibly person, inherits Bethlehem place identity and coordinates

[`places/json/Lehem.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Lehem.json), blob `6b0139235458f7141d7ec728a772e13087c1f2ed`:

- `id=place:Lehem`, **`primary_id=place:Bethlehem`**, `referred_to_as=[place:Bethlehem]`, **`is_person=true`**.
- One verse: 1 Chronicles 4:22 (`13004022`). English/French localized description **explicitly notes a man of Judah with an uncertain possible place-name interpretation**.
- Despite this uncertainty, `geocoordinates` includes `obi=(31.70536129,35.2102663)`, `recogito=(31.70487,35.20376)` and `vizbible=(31.70536129,35.2102663)`, corresponding to the Bethlehem-of-Judah vicinity.

**Failure mode:** an implicit primary-ID join or coordinate import would show a definitive place pin for a record that the source itself flags as a person/possible place. **No validated identity or coordinate use.** This is distinct from the source preserving an alternative hypothesis and must not be automatically 'cleaned' upstream.

### C. Bethlehem of Zebulun: provider coordinates disagree across homonymous places

[`places/json/Bethlehem.2.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Bethlehem.2.json), blob `4dc0a74d2f0df8d292cbe5fc12c679eb27b1f54a`:

- `primary_id=place:Bethlehem.2`, Joshua 19:15, English description: the **Zebulun** town.
- `obi=(32.735379,35.189704)` and `vizbible=(32.735379,35.189704)`, consistent with the Galilean locality.
- `recogito=(31.70487,35.20376)` instead points near **Bethlehem of Judah** (compare [`places/json/Bethlehem.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Bethlehem.json): `recogito=(31.70431,35.20746)`).

**Failure mode:** the correct **name and person/tribe association** can coexist with a wrongly attributed coordinate from one provider. Never choose an arbitrary first/last provider or average coordinates. Keep provider coordinates as source claims, with separate geographical identity and accuracy review.

### D. Emmaus: one provider's point is plainly outside the biblical region

[`places/json/Emmaus.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Emmaus.json), blob `a4318f2886b1c7eec4337719f810fee80be037b0`:

- `obi=(31.83945022,34.98952933)`, `vizbible` the same; `biblica-maps=(31.83929,34.98943)`.
- **`recogito=(56.78055,36.115)`**, entirely outside the geographical area of Luke 24.
- Distinct deeper issue: original [OpenBible Emmaus record](https://www.openbible.info/geo/ancient/ae7274b/emmaus) explicitly gives multiple disputed ancient-site proposals. Agreement between two data providers (when one derives from another) is **not proof** of the true site.

**Failure mode:** a single `geocoordinates` field object is not a vetted pin. Reject the implausible candidate as a location for biblical Emmaus; other candidate positions still require an independent historical-site judgment before use.

### E. Good no-pin control: Nod

[`places/json/Nod.json`](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/places/json/Nod.json), blob `5e98523233c30cb6b72ea2c606c7010ed679c5cc`, has a verse reference Genesis 4:16, but **no `geocoordinates`**. This is appropriate no-data behavior; do not infer a point from a name-based geographical search.

## Engineering consequences — proposals, not settled architecture

1. **Do not replace TIPNR with ACAI by bulk copying:** ACAI imports TIPNR itself; both should remain separately versioned sources with traceable dependency.
2. **Do not use any source's `primary_id` blindly as universal real-world strict identity.** ACAI's `primary_id` and `referred_to_as` encode its own concept grouping. A biblically synonymous designation, an alternative text tradition, an ancient city, a modern successor settlement and an uncertain place hypothesis are **not** the same type of link.
3. **Separate occurrence and subject levels:** verse occurrence, original-language token/phrase referent, canonical biblical person/place, Wikipedia article topic, independently verified physical location and media subject. A verse linking two alternative Gospel designations is not direct evidence of archaeological identity.
4. **Preserve original provider coordinate claims** while keeping any selected pin *absent* unless its referent, period and proposed location are reviewed. Do not silently overwrite upstream coordinates, filter only by lat/lon range, or generate transliterated fallback identity matches.
5. **Version and rights:** ACAI released JSON/Markdown is [CC BY-SA 4.0](https://github.com/BibleAquifer/ACAI/blob/5375d0d334bb6d635ef1813e4d3df58eb30efcca/LICENSE.md); this can constrain redistribution and derivative packaging. Verify exact upstream inputs and share-alike implications before any import. `ORG` biblical references may need controlled Copenhagen Alliance `ENG` conversion for translations; do not change Bible source text or its native versification.
6. **No new canonical system yet:** a minimal provider-aware crosswalk with typed relations may be sufficient; only decide after the fixed stratified pilot compares TIPNR, ACAI, OpenBible, Theographic and other independently attested evidence.
7. **Stable IDs remain unproven across versions.** Numeric name suffixes (`person:Mary.2`, `person:Joshua.2`, etc.) worked in this release; they are not guaranteed permanent without checking a prior release and upstream compatibility policy.

## Next measured checks / quality gate

- [ ] Compare exact ACAI JSON entries and identifiers between releases `v2026-10-30` and `v2026-11-07`, documenting changes and candidate ID continuity.
- [ ] Reproduce the above findings from immutable JSON snapshots and add a *generic* typed-invariant evaluator only if useful on multiple sources. No one-off fix scripts.
- [ ] Verify Theographic's original independent value beyond the subset already imported into ACAI; avoid counting derived duplicates as independent confirmations.
- [ ] Construct an **unbiased or explicitly stratified** 20–30-entity review set that includes positive, rejected and unresolved decisions, with measured safe coverage and abstention. This hand-picked report establishes specific failure modes, **not accuracy statistics**.
- [ ] Re-examine source-vs-article provenance and license obligations in #2 and identity validation #1 before proposing a definitive canonical backbone.

**Outcome:** ACAI adds actual typed and word-level concepts useful for the reader, but selected place records prove it cannot safely be treated as the sole authoritative crosswalk or as a vetted coordinate database. No identities newly approved and no source data, Bible application, package or public release changed.

## Limited release-to-release comparison: 30 October → 7 November 2026

A second pass fetched **the same eight exact JSON paths** at `v2026-10-30` and commit `5375d0d334bb6d635ef1813e4d3df58eb30efcca` (7 November 2026). **All eight file contents changed** at the Git blob level between the two snapshots, but `id` and `primary_id` values were identical for every tested entry. **This proves only continuity of these eight source-native IDs across these two snapshots**, not global stability.

| JSON record | Same `id` and `primary_id` across snapshots? | Relevant diagnostic field unchanged? |
| --- | --- | --- |
| `people/json/Mary.2.json` | yes | no geo field; checked identity keys only |
| `people/json/Joshua.2.json` | yes | no geo field; checked identity keys only |
| `people/json/Shimon.json` | yes | no geo field; checked identity keys only |
| `places/json/Gadara.json` | yes | `primary_id=place:Gerasa`, Biblica maps coordinate unchanged |
| `places/json/Lehem.json` | yes | `is_person=true`, `primary_id=place:Bethlehem`, all provider coordinates unchanged |
| `places/json/Bethlehem.2.json` | yes | the discrepant `recogito` coordinate and the two northern coordinates unchanged |
| `places/json/Emmaus.json` | yes | `recogito=(56.78055,36.115)` unchanged |
| `places/json/Nod.json` | yes | no geo coordinate; unchanged no-pin behavior |

**Meaning:** the observed geographic hazards were **not introduced only in the 7 November release**. The changed Git blob SHA means other fields changed and were **not** fully diffed in this pass. This comparison does **not** prove the full release migration contract, schema stability, provenance of a coordinate, or whether maintainers consider these anomalies bugs.

These results are source-revision snapshots, **not** eight independently confirmed historical identities. The earlier checkbox “compare exact entries across releases” is **partially addressed** for this selected set, not completed globally.
