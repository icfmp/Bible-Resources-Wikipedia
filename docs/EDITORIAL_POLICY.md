# Editorial and licensing policy — draft

**Status:** initial guardrails; not a completed legal clearance or approval to redistribute any content.

## Identity matching
1. Use original, stable TIPNR/OpenBible identifiers. Do **not** join entities by visible name alone.
2. Verify each candidate Wikidata ID refers to the **same individual or geographic entity**. Type-check it: person, geographic place, proposed archaeological site and present-day settlement are different concepts.
3. Accept only with cited evidence adequate to distinguish namesakes; record `accepted`, `rejected` or `unresolved`. An absent match is not an error to repair by guessing.
4. Preserve the origin of each link, exact source revision/commit, reviewer and reason. Corrections are additive editorial decisions, never silent source overwrites.
5. TIPNR's AI-generated short/long descriptions are **not independently verified scholarship**. Do not turn them into output narratives or evidence for other matches.
6. Keep theological, historiographical and archaeological uncertainty in their original qualified terms. A Wikidata statement alone does not guarantee historical consensus.

## Sources have different rights
- **Wikidata main structured data:** CC0, subject to factual verification and correct source tracking. See https://www.wikidata.org/wiki/Wikidata:Licensing.
- **Wikipedia introductory text:** usually CC BY-SA 4.0; check article/project conditions, revision/attribution route, links and any relevant source exceptions. Include sufficient attribution and any change/excerpt notice. Treat French and English texts as independently authored articles, not automatic translations. See https://foundation.wikimedia.org/wiki/Legal:Wikimedia_Developer_App_Guidelines/Frequently_asked_questions.
- **Wikimedia Commons images:** licensing **per image**, not per gallery; verify author, credit, original description/file page, allowed reuse, license link and thumbnail derivation. Do not assume all assets on Wikipedia are Commons/free files; reject unsupported non-free files. See https://commons.wikimedia.org/wiki/Commons:Reusing_content_outside_Wikimedia.
- **STEP TIPNR / OpenBible input records:** read actual file headers, terms and provenance at the pinned source revision; inspect conditions for redistribution, modification and attribution.

Do not claim an entire combined archive is CC0, CC BY-SA or GPL merely because one component is. Distinguish **software license**, **source-data licenses**, **Wikipedia excerpt license** and **each image license** in both metadata and release documentation.

## Presentation contract (for Bible later)
- Bible may show a verified main image, optional small gallery, selected Wikidata facts, a faithful short introduction, and **the original Wikipedia article link immediately below the introduction**.
- The reader should have the actual article language, original label and source visible. No generated/extrapolated text, silently translated prose or invented history.
- Artistic paintings/icons of biblical individuals must be labeled as **representations**, not contemporary photographs; modern site photos must not be presented as ancient scenes.
- Unverified identities, unsupported images and absent fields are **omitted**, not replaced by unrelated content.
- Preserve the rest of the existing Bible card, biblical references and reader navigation; no application change in this repository.

## Review and audit
Every published record should have a machine-verifiable source and license trail, with independently reviewable identity decisions. Include negative regression tests: ambiguous people, uncertain locations, false matches, missing articles, conflicting sources, missing image attribution, and invalid license metadata.

Before any release, perform legal/attribution review, schema validation, provenance audit, independent identity sample audit and packaging tests. A technically passing generator does not imply editorial correctness or authorization to publish.
