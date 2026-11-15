# OpenBible ↔ STEP TIPNR link-structure triage — 15 November 2026

**Related:** issue #1. **Status:** full structural inventory of *candidate* link conflicts; **not an editorial identity review or a publishable crosswalk**. No third-party prose, image bytes or encyclopedia article text are included. The repository remains private.

## Pinned sources / provenance

- **OpenBible**: [Bible-Geocoding-Data](https://github.com/openbibleinfo/Bible-Geocoding-Data), commit `7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f`, `data/ancient.jsonl`, Git blob `b127b4446c6f4ba36ec62dde290c752afeb51bf3`.
- **STEP**: [STEPBible-Data](https://github.com/STEPBible/STEPBible-Data), commit `5de0a47f35f0fc13dfe1430d104e5db8a4285f9c`, `Proper Nouns/TIPNR - Translators Individualised Proper Names with all References - STEPBible.org CC BY.txt`, Git blob `94e636b8806eaa0501d2c7fc2a0fc87b3ffbea96`.
- Read `data/source.jsonl` from the same OpenBible revision to resolve `s3b25cf` as STEP TIPNR and `s7cc8b2` as Wikidata; the identifiers are **not general-purpose constants for future revisions**.
- Both input repositories' READMEs describe CC BY 4.0 data. This report contains a limited analysis of their original names, source IDs and Q-IDs, with source attribution. This is not a license clearance of Wikipedia/Commons, nor of third-party candidate crosswalks.

## Method (repeatable without generating a one-off script)

1. Parse OpenBible's `ancient.jsonl` as one JSON object per nonempty line, then extract only records with `linked_data.s3b25cf.id` (STEP-linked identifier).
2. Parse original TIPNR group headers after its explanatory header: a `$========== PERSON(s)`, `$========== PLACE` or `$========== OTHER` marker followed by a record beginning `<name>@<firstReference>...`. Derive a **comparison-only** simplified key from `<name>_<firstReference>`, cutting the reference suffix at the first `-` or `=`. This transformation is **not a canonical external ID contract**.
3. Compare OpenBible `<name>@<firstReference>` after replacing the first `@` with `_`. An exact match is a **syntactic join only**, not proof that a Q-ID is correct. For mismatches, compare the source name with TIPNR **header names**, then record which categories contain it. Do **not** accept a same-name candidate as a substitute.
4. Independently group OpenBible rows by their unchanged `linked_data.s3b25cf.id`, count distinct ancient entry IDs and distinct **nonempty** `linked_data.s7cc8b2.id` values. Empty Q-IDs are recorded but not counted as alternative Q-IDs.

### Structural results

| Measure | Count |
| --- | ---: |
| TIPNR original records: person / place / other | 3,129 / 1,006 / 102 |
| OpenBible ancient records | 1,342 |
| OpenBible records carrying a STEP TIPNR ID | **1,172** |
| OpenBible rows with strict simplified-key match against any current TIPNR category | **1,034** |
| Of these: current PLACE | **1,032** |
| Of these: current OTHER | **2** |
| OpenBible records without strict match | **138** |
| **Distinct missing simplified IDs** | **76** |
| Same-name current TIPNR PLACE only, but different key | **78** rows |
| Same-name current TIPNR PERSON only, but different key | **7** rows |
| Same-name current TIPNR PLACE and PERSON (ambiguous), different key | **12** rows |
| No identical full header name in current TIPNR | **41** rows |
| TIPNR IDs reused by multiple OpenBible ancient records | **147 groups** |
| Total OpenBible records in these reused-ID groups | **371** |
| Reused-ID groups with two or more **distinct nonempty** Wikidata Q-IDs | **37** |
| Reused-ID groups with exactly one nonempty Q-ID | **71** |
| Reused-ID groups with no nonempty Q-ID | **39** |

**Interpretation:** missing strict keys **do not automatically mean errors**: the same biblical source may have changed its first-reference key, combined/split references, renamed a heading, or used a historic/alternative name. Conversely, matching a name or reusing a TIPNR ID does **not** mean two ancient OpenBible records are interchangeable, or that their different Wikidata subjects must be merged. **No substitute link is accepted by this report.**

### Priority examples requiring manual evidence review

- `Abdon@Jos.21.30` is not an exact current key. Current TIPNR has a **place** `Abdon_Jos.19.28` *and several people named Abdon*. The biblical verse context is essential; selecting by name would risk a person/place mistake.
- `Teman@Gen.36.34` points to a name that TIPNR uses for both a **person** (`Teman_Gen.36.11`) and a **place** (`Teman_Jer.49.7`). No automatic re-link is safe.
- `Jerusalem@Jos.10.1` is linked by seven OpenBible ancient records, including Ariel, Jebus, Jerusalem, Mount Zion, Salem and Zion. The OpenBible Q-IDs vary. These may represent aliases, overlapping geographical areas or distinct topics; **seven entries must not be collapsed into one Wikidata subject**.
- `Babylon@Gen.10.10` likewise groups seven OpenBible entries, including Babylon/Babylonia and additional place names, carrying several different Q-IDs; ancient city, region and literary terms must remain separate.
- `Crete@Deu.2.23` is absent as an exact current TIPNR heading, yet OpenBible's Caphtor and Crete entries share this link and have **different** Wikidata IDs. Their relationship requires editorial evaluation, not a “name fix”.
- `Gadara@Mat.8.28` links Gadara and Gerasa, with different Q-IDs. This touches Gospel place-name/identification variants and must not be silently resolved by joining names.

## Every strict nonmatch, grouped by original OpenBible STEP linked-ID

Classification below is **purely mechanical**: a row category describes only the availability of same-name TIPNR **header entries**, *not an editorial finding*. The `potential current TIPNR keys` column contains **unverified diagnostic suggestions**, not approved links. The Q-ID column is the distinct set of existing OpenBible candidates and is not endorsed.

| OpenBible source-linked ID | Ancient rows | Mechanical category | OpenBible names | Potential current TIPNR keys (NOT approved) | Existing Q-IDs | STEP link modifier |
| --- | ---: | --- | --- | --- | --- | --- |
| `Abdon@Jos.21.30` | 2 | `MIXED_PLACE_PERSON` | Abdon; Ebron | Abdon_1Ch.8.23 (person); Abdon_1Ch.8.30 (person); Abdon_Jdg.12.13 (person); Abdon_Jos.19.28 (place) | — | — |
| `Abel-shittim@Num.33.49` | 2 | `NO_HEADER_NAME` | Abel-shittim; Shittim | none | Q2236536 | — |
| `Achzib@Jos.15.44` | 3 | `PLACE_NAME_ONLY` | Achzib 1; Chezib; Cozeba | Achzib_Gen.38.5 (place); Achzib_Jos.19.29 (place) | Q54991090 | — |
| `Adullam@Jos.12.15` | 1 | `PLACE_NAME_ONLY` | Adullam | Adullam_Gen.38.1 (place) | Q2914860 | — |
| `Ahlab@Jdg.1.31` | 2 | `PLACE_NAME_ONLY` | Ahlab; Mahalab | Ahlab_Jos.19.29 (place) | Q6595658 | — |
| `Ammon@Deu.2.19` | 4 | `PLACE_NAME_ONLY` | Ammon; Ham 1; Rabbah 1; Rabbah 2 | Ammon_Gen.19.38 (place) | Q473433, Q3805 | — |
| `Aram-naharaim@Psa.60.1` | 1 | `PLACE_NAME_ONLY` | Aram-naharaim | Aram-naharaim_Psa.60.0 (place) | Q625636 | — |
| `Avva@2Ki.17.24` | 2 | `NO_HEADER_NAME` | Avva; Ivvah | none | Q6095687 | — |
| `Baalath-beer@Jos.19.8` | 4 | `PLACE_NAME_ONLY` | Baalath-beer; Bealoth 1; Bealoth 2; Ramoth 2 | Baalath-beer_Jos.15.24 (place) | Q4837134 | — |
| `Bamoth-baal@Num.22.41` | 1 | `PLACE_NAME_ONLY` | Bamoth-baal | Bamoth-baal_Num.21.28 (place) | — | — |
| `Beth-haram@Jos.13.27` | 1 | `PLACE_NAME_ONLY` | Beth-haram | Beth-haram_Num.32.36 (place) | Q4898004 | — |
| `Beth-horon_Lower@Jos.16.3` | 2 | `PLACE_NAME_ONLY` | Beth-horon; Lower Beth-horon | Beth-horon_Lower_Jos.10.10 (place) | Q1268514 | — |
| `Beth-rehob@Jdg.18.28` | 2 | `PLACE_NAME_ONLY` | Beth-rehob; Rehob 1 | Beth-rehob_Num.13.21 (place) | — | — |
| `Beth-shan@1Sa.31.10` | 1 | `NO_HEADER_NAME` | Beth-shan | none | Q152368 | — |
| `Bethany@Jdg.7.24` | 2 | `PLACE_NAME_ONLY` | Bethany 2; Beth-barah | Bethany_Mat.21.17 (place) | Q2617848 | — |
| `Bethel@Jos.12.16` | 1 | `PLACE_NAME_ONLY` | Bethel 2 | Bethel_Gen.12.8 (place); Bethel_Jos.19.4 (place) | — | — |
| `Bethuel@1Ch.4.30` | 1 | `PERSON_NAME_ONLY` | Bethuel | Bethuel_Gen.22.22 (person) | — | — |
| `Bethul@Jos.19.4` | 1 | `NO_HEADER_NAME` | Bethul | none | — | — |
| `Beyond_the_River@Ezr.4.10` | 1 | `NO_HEADER_NAME` | Beyond the River | none | Q957854 | — |
| `Cana@Jos.19.28` | 2 | `NO_HEADER_NAME` | Cana; Kanah 2 | none | Q431382 | — |
| `Chesulloth@Jos.19.18` | 3 | `PLACE_NAME_ONLY` | Chesulloth; Chisloth-tabor; Tabor 2 | Chesulloth_Jos.19.12 (place) | — | — |
| `Crete@Deu.2.23` | 2 | `NO_HEADER_NAME` | Caphtor; Crete | none | Q1728546, Q34374 | — |
| `Cuth@2Ki.17.30` | 1 | `NO_HEADER_NAME` | Cuth | none | Q1096108 | — |
| `Dimnah@Jos.21.35` | 3 | `PLACE_NAME_ONLY` | Dimnah; Rimmon 3; Rimmono | Dimnah_Jos.19.13 (place) | — | — |
| `Dor@Jos.12.23` | 1 | `PLACE_NAME_ONLY` | Dor | Dor_Jos.11.2 (place) | Q1243563 | — |
| `El-bethel@Gen.35.7` | 1 | `NO_HEADER_NAME` | El-bethel | none | — | — |
| `Engedi@Jos.15.62` | 2 | `PLACE_NAME_ONLY` | Engedi; Hazazon-tamar 1 | Engedi_Gen.14.7 (place) | Q1011544 | — |
| `Esau@Gen.36.40` | 1 | `PERSON_NAME_ONLY` | Edom | Esau_Gen.25.25 (person) | Q208475 | — |
| `Eshtemoa@Jos.21.14` | 1 | `PLACE_NAME_ONLY` | Eshtemoa | Eshtemoa_Jos.15.50 (place) | Q5397937 | — |
| `Gadara@Mat.8.28` | 2 | `NO_HEADER_NAME` | Gadara; Gerasa | none | Q96379011, Q31565 | — |
| `Galilee_Sea@Num.34.11` | 1 | `NO_HEADER_NAME` | Sea of Galilee | none | Q126982 | — |
| `Gennesaret@Mat.14.34` | 1 | `NO_HEADER_NAME` | Gennesaret | none | — | — |
| `Geshur@Jos.13.13` | 1 | `PLACE_NAME_ONLY` | Geshur | Geshur_Deu.3.14 (place) | Q2669839 | — |
| `Gilboa_Mount@1Sa.31.1` | 1 | `PLACE_NAME_ONLY` | Mount Gilead | Gilboa_Mount_Jdg.7.3 (place) | — | — |
| `Great_Sea@Num.34.6` | 1 | `PLACE_NAME_ONLY` | Great Sea | Great_Sea_Exo.23.31 (place) | Q4918 | — |
| `Ham@1Ch.4.40` | 1 | `MIXED_PLACE_PERSON` | Ham 2 | Ham_Gen.5.32 (person); Ham_Gen.14.5 (place) | — | — |
| `Hammath@Jos.19.35` | 4 | `MIXED_PLACE_PERSON` | Hammath 1; Hammon 1; Hammon 2; Hammoth-dor | Hammath_1Ch.2.55 (person); Hammath_Jos.19.28 (place) | Q19892662, Q6881450 | — |
| `Hermon_Mount@Deu.3.8` | 5 | `PLACE_NAME_ONLY` | Baal-gad; Baal-hamon; Mount Baal-hermon; Mount Hermon; Senir | Hermon_Mount_Num.34.7 (place) | Q4837122, Q83879, Q215471 | — |
| `Hinnom_Valley@Jos.15.8` | 3 | `NO_HEADER_NAME` | Topheth; Valley of Baca; Valley of Hinnom | none | Q1298788, Q558093 | — |
| `Hor_Mount@Num.34.7` | 1 | `PLACE_NAME_ONLY` | Mount Hor 2 | Hor_Mount_Num.20.22 (place) | Q30527282 | — |
| `Horonaim@Isa.15.5` | 2 | `PLACE_NAME_ONLY` | Horonaim 1; Horonaim 2 | Horonaim_2Sa.13.34 (place) | — | — |
| `Italy@Act.18.2` | 1 | `PLACE_NAME_ONLY` | Italy | Italy_Act.10.1 (place) | Q913582 | — |
| `Ituraea@Luk.3.1` | 1 | `NO_HEADER_NAME` | Ituraea | none | Q1514777 | — |
| `Jabesh-gilead@Jdg.21.8` | 1 | `NO_HEADER_NAME` | Jabesh-gilead | none | Q2905361 | — |
| `Javan@Isa.66.19` | 2 | `PERSON_NAME_ONLY` | Greece; Javan | Javan_Gen.10.2 (person) | Q41, Q1684266 | — |
| `Jerusalem@Jos.10.1` | 7 | `PLACE_NAME_ONLY` | Ariel; Jebus; Jerusalem; Mount Zion; Salem; The Lord Is There; Zion | Jerusalem_Gen.14.18 (place) | Q1123697, Q1218, Q332444, Q4377375, Q205318 | — |
| `Kadesh-barnea@Num.32.8` | 2 | `NO_HEADER_NAME` | Kadesh-barnea; Kedesh 2 | none | Q954599 | — |
| `Kadesh@2Sa.24.6` | 1 | `PLACE_NAME_ONLY` | Kadesh 2 | Kadesh_Gen.14.7 (place) | Q690035 | — |
| `Kitron@Jdg.1.30` | 3 | `PLACE_NAME_ONLY` | Kartah; Kattath; Kitron | Kitron_Jos.19.15 (place) | Q6373489, Q6378316 | — |
| `Leb-kamai@Jer.51.1` | 1 | `NO_HEADER_NAME` | Leb-kamai | none | — | — |
| `Media@Ezr.6.2` | 1 | `PLACE_NAME_ONLY` | Media | Media_2Ki.17.6 (place) | Q8735 | — |
| `Mizpah@Jdg.20.1` | 5 | `PLACE_NAME_ONLY` | Arimathea; Mizpah 3; Mizpeh 1; Ramah 4; Ramathaim-zophim | Mizpah_Jos.18.26 (place) | Q2558868, Q1755389, Q1019146 | — |
| `Mizpeh_Valley@Jos.11.8` | 2 | `PLACE_NAME_ONLY` | Mizpah 2; Valley of Mizpeh | Mizpeh_Valley_Jos.11.3 (place) | Q16888067 | — |
| `Moab@Gen.36.35` | 2 | `MIXED_PLACE_PERSON` | Ir-moab; Moab 1 | Moab_Gen.19.37a (person); Moab_Gen.19.37b (place) | Q326304 | — |
| `Nahalol@Jdg.1.30` | 1 | `PLACE_NAME_ONLY` | Nahalal | Nahalol_Jos.19.15 (place) | Q1724338 | — |
| `Nebo_Mount@Deu.32.49` | 2 | `PLACE_NAME_ONLY` | Abarim; Mount Nebo | Nebo_Mount_Num.27.12 (place) | Q337141, Q680161 | — |
| `Neiel@Jos.19.27` | 2 | `NO_HEADER_NAME` | Neah; Neiel | none | Q6987988 | — |
| `Ophrah@Jdg.6.11` | 2 | `MIXED_PLACE_PERSON` | Hapharaim; Ophrah 2 | Ophrah_1Ch.4.14 (person); Ophrah_Jos.18.23 (place); Ophrah_Jos.19.19 (place) | — | — |
| `Paddan-aram@Gen.25.20` | 1 | `NO_HEADER_NAME` | Paddan-aram | none | Q1257454 | — |
| `Philistine@Gen.21.32` | 1 | `PERSON_NAME_ONLY` | Philistia | Philistine_Gen.10.14 (person) | Q7185566 | — |
| `Pirathon@Jdg.12.15` | 1 | `PLACE_NAME_ONLY` | Pirathon | Pirathon_Jdg.12.13 (place) | Q2946726 | — |
| `Put@Isa.66.19` | 1 | `PERSON_NAME_ONLY` | Put | Put_Gen.10.6 (person) | Q946939 | — |
| `Ramoth-gilead@Gen.31.47` | 5 | `NO_HEADER_NAME` | Mizpah 1; Mizpah 4; Ramah 5; Ramath-mizpeh; Ramoth-gilead | none | Q6884729, Q6884740, Q412380, Q2006096 | — |
| `Ramoth@1Ch.6.73` | 1 | `PLACE_NAME_ONLY` | Ramoth 1 | Ramoth_Gen.31.47 (place) | Q7289977 | — |
| `Sardis@Oba.1.20` | 2 | `NO_HEADER_NAME` | Sardis; Sepharad | none | Q232615, Q3305343 | — |
| `Senaah@Ezr.2.35` | 1 | `PERSON_NAME_ONLY` | Senaah | Senaah_1Ch.9.7 (person) | — | — |
| `Shaalbim@Jdg.1.35` | 1 | `PLACE_NAME_ONLY` | Shaalbim | Shaalbim_Jos.19.42 (place) | — | — |
| `Sharuhen@Jos.19.6` | 3 | `PLACE_NAME_ONLY` | Shaaraim 2; Sharuhen; Shilhim | Sharuhen_Jos.15.32 (place) | Q1548392 | — |
| `Shiloah@Isa.8.6` | 1 | `NO_HEADER_NAME` | Shiloah | none | — | — |
| `Shinar@Gen.10.10` | 1 | `NO_HEADER_NAME` | Shinar | none | Q1404297 | — |
| `Sinai@Exo.19.11` | 2 | `PLACE_NAME_ONLY` | Mount Horeb; Mount Sinai | Sinai_Exo.3.1 (place) | Q1420926, Q377485 | — |
| `Tabor_Mount@Jdg.4.6` | 1 | `PLACE_NAME_ONLY` | Mount Tabor | Tabor_Mount_Jos.19.22 (place) | Q193785 | — |
| `Teman@Gen.36.34` | 1 | `MIXED_PLACE_PERSON` | Teman | Teman_Gen.36.11 (person); Teman_Jer.49.7 (place) | Q1546303 | — |
| `Tiberias@Jos.19.35` | 2 | `NO_HEADER_NAME` | Rakkath; Tiberias | none | Q151920 | — |
| `Timnath-heres@Jdg.2.9` | 1 | `PLACE_NAME_ONLY` | Timnath-heres | Timnath-heres_Jos.19.50 (place) | Q2157993 | — |
| `Zephath@Jdg.1.17` | 2 | `NO_HEADER_NAME` | Hormah; Zephath | none | Q5903738 | — |

## Every STEP linked-ID reused in multiple OpenBible ancient records

This second table includes **all 147** groups, not only the groups with conflicting Q-IDs. The `MULTIPLE_QIDS` marker identifies review priority, **not necessarily an error**. The `NO_QID` marker does not imply a place was unmapped in every possible source.

| Original shared STEP ID | Ancient rows | OpenBible ancient labels | Distinct nonempty Wikidata Q-IDs | Structural marker |
| --- | ---: | --- | --- | --- |
| `Babylon@Gen.10.10` | 7 | Babel; Babylon 1; Babylon 2; Babylon 3; Babylonia; Pekod; Sheshach | Q5684, Q47690, Q48968605 | MULTIPLE_QIDS |
| `Jerusalem@Jos.10.1` | 7 | Ariel; Jebus; Jerusalem; Mount Zion; Salem; The Lord Is There; Zion | Q1123697, Q1218, Q332444, Q4377375, Q205318 | MULTIPLE_QIDS |
| `Gilgal@Deu.11.30` | 6 | Beth-gilgal; Geliloth; Gibeath-haaraloth; Gilgal 1; Gilgal 3; Gilgal 4 | — | NO_QID |
| `Bethlehem@Gen.35.16` | 5 | Bethlehem 1; Bethlehem 3; Ephrath; Ephrathah; Lehem | Q5776 | ONE_QID |
| `Gibeon@Jos.9.3` | 5 | Bamah; Geba 2; Gibbar; Gibeon; Valley of Gibeon | Q4144531, Q889398 | MULTIPLE_QIDS |
| `Hermon_Mount@Deu.3.8` | 5 | Baal-gad; Baal-hamon; Mount Baal-hermon; Mount Hermon; Senir | Q4837122, Q83879, Q215471 | MULTIPLE_QIDS |
| `Mizpah@Jdg.20.1` | 5 | Arimathea; Mizpah 3; Mizpeh 1; Ramah 4; Ramathaim-zophim | Q2558868, Q1755389, Q1019146 | MULTIPLE_QIDS |
| `Ramoth-gilead@Gen.31.47` | 5 | Mizpah 1; Mizpah 4; Ramah 5; Ramath-mizpeh; Ramoth-gilead | Q6884729, Q6884740, Q412380, Q2006096 | MULTIPLE_QIDS |
| `Ai@Gen.12.8` | 4 | Ai 1; Ai 3; Aiath; Aija | Q403166 | ONE_QID |
| `Ammon@Deu.2.19` | 4 | Ammon; Ham 1; Rabbah 1; Rabbah 2 | Q473433, Q3805 | MULTIPLE_QIDS |
| `Baalath-beer@Jos.19.8` | 4 | Baalath-beer; Bealoth 1; Bealoth 2; Ramoth 2 | Q4837134 | ONE_QID |
| `Bethel@Gen.12.8` | 4 | Aven; Bethel 3; Bochim; Luz 1 | — | NO_QID |
| `Ebal_Mount@Deu.11.29` | 4 | Mount Ebal; Mount Ephraim; Mount Zalmon; Zalmon | Q1975866, Q12346828 | MULTIPLE_QIDS |
| `Gath@Jos.11.22` | 4 | Gath 1; Gath 2; Gath 3; Metheg-ammah | Q1348441, Q48996107 | MULTIPLE_QIDS |
| `Hammath@Jos.19.35` | 4 | Hammath 1; Hammon 1; Hammon 2; Hammoth-dor | Q19892662, Q6881450 | MULTIPLE_QIDS |
| `Kedesh@Jos.12.22` | 4 | Kedesh 1; Kedesh 4; Kedesh 5; Kedesh-naphtali | Q2585161 | ONE_QID |
| `Kir@1Sa.22.3` | 4 | Kir 1; Kir 2; Kir-hareseth; Mizpeh 3 | Q65086594, Q3782348, Q16943736 | MULTIPLE_QIDS |
| `Kiriath-jearim@Jos.9.17` | 4 | Baalah 2; Baale-judah; Jaar; Kiriath-jearim | Q4837137, Q3303084 | MULTIPLE_QIDS |
| `Red_Sea@Exo.10.19` | 4 | Red Sea 1; Red Sea 2; Red Sea 3; Way of the Red Sea | Q116702 | ONE_QID |
| `Achzib@Jos.15.44` | 3 | Achzib 1; Chezib; Cozeba | Q54991090 | ONE_QID |
| `Aijalon@Jos.10.12` | 3 | Aijalon 1; Aijalon 2; Valley of Aijalon | Q658898 | ONE_QID |
| `Ain@Jos.15.32` | 3 | Ain 2; Ain 3; En-rimmon | — | NO_QID |
| `Aphek@Jos.13.4` | 3 | Aphek 1; Aphek 4; Aphik | Q4779601, Q383537 | MULTIPLE_QIDS |
| `Baal-meon@Num.32.3` | 3 | Baal-meon; Beon; Beth-meon | Q4837123 | ONE_QID |
| `Berothah@2Sa.8.8` | 3 | Berothah; Berothai; Cun | Q4894651 | ONE_QID |
| `Beth-shemesh@Jos.15.10` | 3 | Beth-shemesh 1; Ir-shemesh; Mount Heres | Q152449 | ONE_QID |
| `Calneh@Gen.10.10` | 3 | Calneh 1; Calneh 2; Canneh | — | NO_QID |
| `Chesulloth@Jos.19.18` | 3 | Chesulloth; Chisloth-tabor; Tabor 2 | — | NO_QID |
| `Cyprus@Num.24.24` | 3 | Cyprus; Elishah; Kittim | Q229, Q1760729, Q1743921 | MULTIPLE_QIDS |
| `Dimnah@Jos.21.35` | 3 | Dimnah; Rimmon 3; Rimmono | — | NO_QID |
| `Euphrates@Gen.2.14` | 3 | Euphrates; River 2; River 3 | Q34589 | ONE_QID |
| `Geba@Jos.18.24` | 3 | Geba 1; Geba 3; Geba 4 | — | NO_QID |
| `Gederah@Jos.15.36` | 3 | Gederah 1; Gederah 2; Gederah 3 | — | NO_QID |
| `Gedor@Jos.12.13` | 3 | Gedor 1; Gedor 3; Gedor 4 | — | NO_QID |
| `Gibeah@Jos.18.28` | 3 | Gibeah 1; Gibeah 3; Gibeah 4 | — | NO_QID |
| `Hamath@Num.13.21` | 3 | Hamath 1; Hamath 2; Lebo-hamath | Q173545, Q6467705 | MULTIPLE_QIDS |
| `Hinnom_Valley@Jos.15.8` | 3 | Topheth; Valley of Baca; Valley of Hinnom | Q1298788, Q558093 | MULTIPLE_QIDS |
| `Ibleam@Jos.17.11` | 3 | Bileam; Gath-rimmon 2; Ibleam | Q20108155 | ONE_QID |
| `Kenath@Num.21.30` | 3 | Kenath; Nobah 2; Nophah | Q763167 | ONE_QID |
| `Kitron@Jdg.1.30` | 3 | Kartah; Kattath; Kitron | Q6373489, Q6378316 | MULTIPLE_QIDS |
| `Migdol@Exo.14.2` | 3 | Migdol 1; Migdol 2; Migdol 3 | — | NO_QID |
| `Ramah@Jos.18.25` | 3 | Ramah 1; Ramah 6; Ramah 7 | Q926868 | ONE_QID |
| `Sela@Jdg.1.36` | 3 | Sela 1; Sela 2; Sela 3 | Q489724 | ONE_QID |
| `Sharuhen@Jos.19.6` | 3 | Shaaraim 2; Sharuhen; Shilhim | Q1548392 | ONE_QID |
| `Zarethan@Jos.3.16` | 3 | Zarethan; Zeredah 2; Zererah | Q147911 | ONE_QID |
| `Abdon@Jos.21.30` | 2 | Abdon; Ebron | — | NO_QID |
| `Abel-shittim@Num.33.49` | 2 | Abel-shittim; Shittim | Q2236536 | ONE_QID |
| `Acco@Jdg.1.31` | 2 | Acco; Ptolemais | Q126084, Q92277123 | MULTIPLE_QIDS |
| `Ahlab@Jdg.1.31` | 2 | Ahlab; Mahalab | Q6595658 | ONE_QID |
| `Ain@Num.34.11` | 2 | Ain 1; Rimmon 2 | Q7036743 | ONE_QID |
| `Alemeth@Jos.21.18` | 2 | Alemeth; Almon | Q4716077 | ONE_QID |
| `Arabia@2Sa.23.35` | 2 | Arabia 1; Arabia 2 | Q31945, Q221353 | MULTIPLE_QIDS |
| `Arad@Num.21.1` | 2 | Arad 1; Arad 2 | — | NO_QID |
| `Arnon@Num.21.13` | 2 | Arnon; Valley of the Arnon | Q2120208 | ONE_QID |
| `Aroer@Num.32.34` | 2 | Aroer 2; Aroer 4 | — | NO_QID |
| `Arumah@Jdg.9.41` | 2 | Arumah; Rumah | — | NO_QID |
| `Ashnah@Jos.15.33` | 2 | Ashnah 1; Ashnah 2 | — | NO_QID |
| `Ashtaroth@Deu.1.4` | 2 | Ashtaroth; Beeshterah | — | NO_QID |
| `Ashteroth-karnaim@Gen.14.5` | 2 | Ashteroth-karnaim; Karnaim | Q2915901, Q4703239 | MULTIPLE_QIDS |
| `Assyria@Gen.2.14` | 2 | Asshur; Assyria | Q200200, Q41137 | MULTIPLE_QIDS |
| `Atad@Gen.50.10` | 2 | Abel-mizraim; Atad | Q4666525, Q4812632 | MULTIPLE_QIDS |
| `Ataroth@Jos.16.2` | 2 | Ataroth 2; Ataroth 3 | — | NO_QID |
| `Avva@2Ki.17.24` | 2 | Avva; Ivvah | Q6095687 | ONE_QID |
| `Bashan@Num.21.33` | 2 | Bashan; Mount Bashan | Q612952 | ONE_QID |
| `Beeroth@Jos.9.17` | 2 | Beer 2; Beeroth | Q4880075 | ONE_QID |
| `Beersheba@Gen.21.14` | 2 | Beersheba 1; Beersheba 2 | Q534596 | ONE_QID |
| `Bene-jaakan@Num.33.31` | 2 | Beeroth Bene-jaakan; Bene-jaakan | Q4875424 | ONE_QID |
| `Beth-aven@Jos.7.2` | 2 | Beth-aven 1; Beth-aven 2 | — | NO_QID |
| `Beth-horon_Lower@Jos.16.3` | 2 | Beth-horon; Lower Beth-horon | Q1268514 | ONE_QID |
| `Beth-nimrah@Num.32.36` | 2 | Beth-nimrah; Nimrah | Q4897428 | ONE_QID |
| `Beth-rehob@Jdg.18.28` | 2 | Beth-rehob; Rehob 1 | — | NO_QID |
| `Bethany@Jdg.7.24` | 2 | Bethany 2; Beth-barah | Q2617848 | ONE_QID |
| `Bethsaida@Mat.11.21` | 2 | Bethsaida 1; Bethsaida 2 | Q501773 | ONE_QID |
| `Bezer@Deu.4.43` | 2 | Bezer; Bozrah 2 | Q3376309 | ONE_QID |
| `Brook_of_Egypt@Num.34.5` | 2 | Brook of Egypt; Shihor 2 | Q1252077 | ONE_QID |
| `Cana@Jos.19.28` | 2 | Cana; Kanah 2 | Q431382 | ONE_QID |
| `Carmel@Jos.12.22` | 2 | Carmel 1; Racal | Q2904870 | ONE_QID |
| `Crete@Deu.2.23` | 2 | Caphtor; Crete | Q1728546, Q34374 | MULTIPLE_QIDS |
| `Cush@Gen.2.13` | 2 | Cush 1; Cush 2 | Q241790 | ONE_QID |
| `Ebenezer@1Sa.4.1` | 2 | Ebenezer 1; Ebenezer 2 | Q2915014 | ONE_QID |
| `Edrei@Num.21.33` | 2 | Edrei 1; Edrei 2 | Q238217 | ONE_QID |
| `En-gannim@Jos.19.21` | 2 | Anem; En-gannim 2 | Q6667727 | ONE_QID |
| `Engedi@Jos.15.62` | 2 | Engedi; Hazazon-tamar 1 | Q1011544 | ONE_QID |
| `Ephron_Mount@Jos.15.9` | 2 | Ephron 1; Mount Ephron | — | NO_QID |
| `Ether@Jos.15.42` | 2 | Ether 1; Ether 2 | — | NO_QID |
| `Gadara@Mat.8.28` | 2 | Gadara; Gerasa | Q96379011, Q31565 | MULTIPLE_QIDS |
| `Galilee@Jos.12.23` | 2 | Galilee 1; Galilee 2 | Q83241 | ONE_QID |
| `Gaza@Gen.10.19` | 2 | Ayyah; Gaza | Q47492 | ONE_QID |
| `Gebal@Jos.13.5` | 2 | Gebal 1; Gebal 2 | Q173532 | ONE_QID |
| `Gezer@Jos.10.33` | 2 | Gezer; Gob | Q1466687 | ONE_QID |
| `Gihon@Gen.2.13` | 2 | Gihon 1; Gihon 2 | Q1247896, Q204601 | MULTIPLE_QIDS |
| `Gilead@Gen.31.21` | 2 | Gilead 1; Gilead 2 | Q922498 | ONE_QID |
| `Goshen@Jos.10.41` | 2 | Goshen 2; Goshen 3 | — | NO_QID |
| `Harod@Jdg.7.1` | 2 | Harod 1; Harod 2 | Q603425 | ONE_QID |
| `Havilah@Gen.25.18` | 2 | Havilah 2; Havilah 3 | — | NO_QID |
| `Hazor@Jos.11.1` | 2 | Hazor 1; Hezron | Q740138 | ONE_QID |
| `Helkath@Jos.19.25` | 2 | Helkath; Hukok | — | NO_QID |
| `Holy_Place@Exo.26.33` | 2 | Holy Place 1; Holy Place 2 | Q255481, Q3620148 | MULTIPLE_QIDS |
| `Horonaim@Isa.15.5` | 2 | Horonaim 1; Horonaim 2 | — | NO_QID |
| `Javan@Isa.66.19` | 2 | Greece; Javan | Q41, Q1684266 | MULTIPLE_QIDS |
| `Jokneam@Jos.12.22` | 2 | Jokmeam 1; Jokneam | — | NO_QID |
| `Jordan@Gen.13.10` | 2 | Jordan; Jordan Valley | Q40059, Q2463859 | MULTIPLE_QIDS |
| `Judea@Ezr.9.9` | 2 | Judea 1; Judea 2 | Q1003997, Q104028 | MULTIPLE_QIDS |
| `Kadesh-barnea@Num.32.8` | 2 | Kadesh-barnea; Kedesh 2 | Q954599 | ONE_QID |
| `Kibzaim@Jos.21.22` | 2 | Jokmeam 2; Kibzaim | Q6404107 | ONE_QID |
| `Kidron@2Sa.15.23` | 2 | Kidron; Valley of Jehoshaphat | Q860532, Q531729 | MULTIPLE_QIDS |
| `Kiriathaim@Gen.14.5` | 2 | Kerioth; Kiriathaim 1 | — | NO_QID |
| `Kishion@Jos.19.20` | 2 | Kedesh 3; Kishion | Q6601333 | ONE_QID |
| `Lasha@Gen.10.19` | 2 | Lasha; Nahaliel | Q6493160 | ONE_QID |
| `Lo-debar@Jos.13.26` | 2 | Debir 3; Lo-debar | Q6663061 | ONE_QID |
| `Madmannah@Jos.15.31` | 2 | Beth-marcaboth; Madmannah | — | NO_QID |
| `Magadan@Mat.15.39` | 2 | Dalmanutha; Magadan | Q1158048 | ONE_QID |
| `Mahaneh-dan@Jdg.13.25` | 2 | Mahaneh-dan 1; Mahaneh-dan 2 | — | NO_QID |
| `Manahath@Jdg.20.43` | 2 | Manahath; Nohah | — | NO_QID |
| `Maon@Jos.15.55` | 2 | Maon; Wilderness of Maon | — | NO_QID |
| `Megiddo@Jos.12.21` | 2 | Armageddon; Megiddo | Q208379 | ONE_QID |
| `Migron@1Sa.14.2` | 2 | Migron 1; Migron 2 | — | NO_QID |
| `Mizpeh_Valley@Jos.11.8` | 2 | Mizpah 2; Valley of Mizpeh | Q16888067 | ONE_QID |
| `Moab@Gen.36.35` | 2 | Ir-moab; Moab 1 | Q326304 | ONE_QID |
| `Moriah_Mount@Gen.22.2` | 2 | Moriah; Mount Moriah | Q20978866, Q193163 | MULTIPLE_QIDS |
| `Naaran@Jos.16.7` | 2 | Naarah; Naaran | Q20083909 | ONE_QID |
| `Nebo_Mount@Deu.32.49` | 2 | Abarim; Mount Nebo | Q337141, Q680161 | MULTIPLE_QIDS |
| `Nebo@Ezr.2.29` | 2 | Nebo 2; Nebo 3 | — | NO_QID |
| `Negeb@Gen.12.9` | 2 | Negeb; South 1 | Q162843 | ONE_QID |
| `Neiel@Jos.19.27` | 2 | Neah; Neiel | Q6987988 | ONE_QID |
| `On@Gen.41.45` | 2 | City of Destruction; Heliopolis | Q191687 | ONE_QID |
| `Ophrah@Jdg.6.11` | 2 | Hapharaim; Ophrah 2 | — | NO_QID |
| `Ophrah@Jos.18.23` | 2 | Beth-le-aphrah; Ophrah 1 | — | NO_QID |
| `Samaria@1Ki.13.32` | 2 | Samaria 1; Samaria 2 | Q1757438, Q1294629 | MULTIPLE_QIDS |
| `Sardis@Oba.1.20` | 2 | Sardis; Sepharad | Q232615, Q3305343 | MULTIPLE_QIDS |
| `Shechem@Gen.12.6` | 2 | Shechem; Tower of Shechem | Q7951237 | ONE_QID |
| `Shimron@Jos.11.1` | 2 | Shimron; Shimron-meron | Q2916430 | ONE_QID |
| `Sinai@Exo.19.11` | 2 | Mount Horeb; Mount Sinai | Q1420926, Q377485 | MULTIPLE_QIDS |
| `Socoh@Jos.15.35` | 2 | Socoh 1; Socoh 3 | Q2776782 | ONE_QID |
| `Succoth@Gen.33.17` | 2 | Succoth 1; Valley of Succoth | — | NO_QID |
| `Syria@Jdg.10.6` | 2 | Syria 1; Syria 2 | Q770281, Q207118 | MULTIPLE_QIDS |
| `Taanach@Jos.12.21` | 2 | Aner; Taanach | Q2894475, Q2920206 | MULTIPLE_QIDS |
| `Tadmor@1Ki.9.18` | 2 | Tadmor; Tamar 1 | Q5747 | ONE_QID |
| `Tappuah@Jos.12.17` | 2 | En-tappuah; Tappuah 1 | — | NO_QID |
| `Tarshish@1Ki.10.22` | 2 | Tarshish 1; Tarshish 2 | Q44826 | ONE_QID |
| `Tiberias@Jos.19.35` | 2 | Rakkath; Tiberias | Q151920 | ONE_QID |
| `Timnah@Gen.38.12` | 2 | Timnah 1; Timnah 3 | Q2916736 | ONE_QID |
| `Zemaraim@Jos.18.22` | 2 | Mount Zemaraim; Zemaraim | — | NO_QID |
| `Zephath@Jdg.1.17` | 2 | Hormah; Zephath | Q5903738 | ONE_QID |
| `Zered@Num.21.12` | 2 | Valley of Zered; Zered | Q2451612 | ONE_QID |
| `Ziph@Jos.15.55` | 2 | Wilderness of Ziph; Ziph 1 | Q8072636 | ONE_QID |
| `Zoar@Gen.13.10` | 2 | Zair; Zoar | Q218016 | ONE_QID |

## What still needs human/editorial verification

This report **completes source-wide structural clustering only**. Next, choose a stratified sample including: (a) key changes with a single plausible current place; (b) names shared by people and places; (c) no-header-name cases; (d) reused STEP IDs with multiple Q-IDs; and (e) alternative site/era relationships. For each case, inspect the actual biblical references, original group description **only as unverified source material** (TIPNR AI prose is excluded as verified fact), OpenBible original qualifiers/modifiers, Wikidata referent and independent evidence. Record `accepted/rejected/unresolved`, **relationship type** and field-specific allowance according to [the review protocol](../IDENTITY_REVIEW_PROTOCOL.md). Sample-level precision/false-positive rates must be measured only after that independent verification; never compute them from these structural buckets.

Neither the 76 missing keys nor the 37 multiple-Q-ID groups have been manually cleared as a set. **Issue #1 remains open; no generated resource, package, app change or publication is authorized by this report.**
