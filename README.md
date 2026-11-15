# Bible Resources — Wikipedia

A separate, optional **offline encyclopedia enrichment resource** for [Bible](https://github.com/icfmp/Bible), drawing carefully verified links between biblical people/places and **Wikidata, Wikipedia and Wikimedia Commons**.

**Status: planning only. No data package, importer, application integration or release exists yet.** The repository is currently private. No distribution or public release is authorized by this setup.

## What the resource should provide

For a biblical person or place **with a verified identity match**:

- An identity mapping from a stable **STEP TIPNR** or established **OpenBible** identifier to the correct Wikidata item (Q-ID).
- A small, useful selection of structured Wikidata facts, with language and uncertainty intact.
- A faithful introductory excerpt from the corresponding French/English Wikipedia article, with article/revision attribution and license information, and an **external article link immediately below it** in Bible.
- A verified main illustration and, where available and worthwhile, a small gallery of directly relevant Commons images, with **individual** credits, licenses, captions and source links.
- Enough provenance, identifiers, versions and integrity information for a clean update and offline presentation.

This project **prepares the resource**. The Bible application should eventually **read and display** it; Bible must not be turned into a Wikipedia scraper or duplicate this acquisition pipeline.

## Boundaries

- **Reading first:** no unrelated encyclopedia browser, AI explanations, or new persistent UI in Bible.
- **Identity first:** name equality and third-party bulk matches are candidates, not verified identity links. Missing/ambiguous matches remain missing.
- **Content fidelity:** never silently invent, rewrite, translate or merge Wikipedia prose, source assertions or photographic identities.
- **License first:** Wikidata statements, Wikipedia text and Commons media have **different terms**. Preserve attribution and source licensing per item. A repository software license does not relicense imported content.
- **No forced downloads:** this should be optional, compact and offline once installed. The package format and whether to embed thumbnails must be tested, not assumed.
- **Keep roles separate:** this repository builds/validates data; [Bible-Resources](https://github.com/icfmp/Bible-Resources) manages other curated Bible modules; [Bible](https://github.com/icfmp/Bible) owns the reader, Library and installation UI.
- **No release or app changes now:** publishing, adding this resource to Bible's Library and modifying other repositories are separate work requiring explicit authorization.

## Delivery sequence (gated)

1. **Source audit:** inspect actual TIPNR and OpenBible identifiers, proposed TIPNR/Wikidata crosswalks, licenses and edge cases. Report coverage and false matches.
2. **Editorial and legal rules:** define accept/reject/unresolved identity evidence; verify Wikipedia text attribution and per-image rights.
3. **Resource contract:** agree on a small versioned, source-aware format and manifest that can be consumed offline. Do not assume SWORD is suitable for structured cards and photographs.
4. **Small pilot:** prepare and independently review a deliberately diverse sample (roughly 20–30 entities), including duplicate names, historical disputes and entries with no match. Test French and English.
5. **Repeatable production:** only after a successful pilot, implement generic incremental extraction, validation, reproducibility checks and optional media optimization.
6. **Distribution handoff:** review size, update/rollback, catalog and compatibility requirements with Bible; publish only after explicit approval.

See [the project plan](docs/PROJECT_PLAN.md), [editorial and rights policy](docs/EDITORIAL_POLICY.md) and [agent instructions](AGENTS.md). Issues track implementation tasks; documentation is not evidence of implementation.

## Reference sources

- [STEPBible-Data](https://github.com/STEPBible/STEPBible-Data) — proper names, identifier context and source notices.
- [OpenBible geocoding data](https://github.com/openbibleinfo/Bible-Geocoding-Data) — place IDs and source-linked identifications.
- [Wikidata licensing](https://www.wikidata.org/wiki/Wikidata:Licensing), [Wikimedia API access policy](https://www.mediawiki.org/wiki/Wikimedia_APIs/Access_policy).
- [Wikimedia developer licensing FAQ](https://foundation.wikimedia.org/wiki/Legal:Wikimedia_Developer_App_Guidelines/Frequently_asked_questions), [Commons external reuse](https://commons.wikimedia.org/wiki/Commons:Reusing_content_outside_Wikimedia).

The source links document intended investigation, **not an endorsement of every record**.
