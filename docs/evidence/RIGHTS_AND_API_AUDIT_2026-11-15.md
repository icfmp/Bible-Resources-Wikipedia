# Wikimedia rights and API audit — first verified pass (15 November 2026)

**Related issue:** #2. **Status:** general legal/source policy and API best practices verified against publisher guidance; **no individual Wikipedia excerpt or Commons image has yet been cleared for redistribution**. This is an engineering/editorial checklist, **not legal advice**, not a license clearance for a finished package, and not authorization to publish.

## Official references inspected

1. [Wikidata licensing](https://www.wikidata.org/wiki/Wikidata:Licensing): Wikidata main structured data is CC0; wiki narrative pages outside structured-data namespaces can have different terms.
2. [Wikimedia Foundation's developer app guidelines](https://foundation.wikimedia.org/wiki/Legal:Wikimedia_Developer_App_Guidelines): most Wikipedia text is CC BY-SA 4.0, potentially dual-licensed with GFDL depending on the content; author acknowledgement can use an appropriate link back to the article/history; changes must be indicated, and attribution/license retained. Do not imply Wikimedia sponsorship or misuse trademarks.
3. [Commons reuse rules](https://commons.wikimedia.org/wiki/Commons:Reusing_content_outside_Wikimedia) and [license-specific explanations](https://commons.wikimedia.org/wiki/Commons:Reusing_content_outside_Wikimedia/licenses): every hosted work has its own copyright/license and attribution, and an uploader is not necessarily the original author. Multilicensed files may allow a choice of terms; public domain still has provenance/other-rights considerations. **An image hosted locally on Wikipedia may be non-free** even if associated with a Wikipedia page.
4. [Wikimedia API access policy](https://www.mediawiki.org/wiki/Wikimedia_APIs/Access_policy) and [2026 rate limits](https://www.mediawiki.org/wiki/Wikimedia_APIs/Rate_limits): identify clients with a useful User-Agent and contact; current operational recommendations include at most **three concurrent requests**, handling `429` with `Retry-After`, and sensible caching/rate limits. The published thresholds are subject to change.
5. [MediaWiki REST reference](https://www.mediawiki.org/wiki/API:REST_API/Reference): revision and page metadata are available separately; page license and latest revision fields must be captured as **actual source evidence**, not guessed from a generic Wikipedia rule.
6. [Wikimedia Attribution API](https://www.mediawiki.org/wiki/Attribution_API) is **beta**. It may assist presentation, but its stability must be assessed before making the resource dependent on it.
7. [STEPBible-Data](https://github.com/STEPBible/STEPBible-Data/blob/5de0a47f35f0fc13dfe1430d104e5db8a4285f9c/README.md) declares CC BY 4.0 for its data and requires attribution/recorded changes. [OpenBible readme](https://github.com/openbibleinfo/Bible-Geocoding-Data/blob/7eb18a5ee62f27b9b93bd6689ea272d76dd23b8f/readme.md) declares CC BY 4.0 for its geocoding dataset; imagery, OpenStreetMap/geometry and further supplied materials may have **different** rights. The candidate [PTA crosswalk](https://github.com/PatristicTextArchive/tipnr_data) has **not** had its own distribution/database rights independently established.

## Rights matrix — do not merge these licenses

| Source element | Expected governing rights / conditions | Intended resource handling | Publication gate |
| --- | --- | --- | --- |
| TIPNR stable IDs / references / facts | STEP source notices, generally **CC BY 4.0**; source attribution, modifications recorded | Preserve exact source commit and key; only reviewed identity mapping; **exclude AI-written TIPNR descriptions** | Original file headers, rights/provenance and changes checked |
| OpenBible biblical-place IDs and candidate evidence | OpenBible's **CC BY 4.0** dataset; other provenance and geometry/OSM terms may apply separately | Preserve ancient/modern distinction, qualifiers and exact snapshot; no bulk third-party image/geometry transfer by default | Dataset attribution and imported-field rights validated |
| Wikidata statements / labels | **CC0 structured data**, but factual reliability remains an editorial issue | Minimal type-aware statements with Q-ID, property/qualifier references, capture timestamp/revision where available | Identity must be approved by #1; disputed information omitted or marked |
| Wikipedia FR/EN introductory passage | **Usually CC BY-SA 4.0**, verify actual page/revision and imported exceptions; comply with attribution and share-alike for adaptations | Store a **faithful, bounded excerpt**, source language/article URL/revision/license, appropriate contributor credit route; mark excerpt/truncation clearly, no AI summary or silent translation | Verify exact article version and authorship attribution method for each locale |
| Wikimedia Commons photo / historical depiction | **Per-file** public domain, CC BY, CC BY-SA or another compatible free license; creator, credit, license, link, alterations, relevant rights | Include only a verified relevant file with actual metadata. Distinguish modern photos from paintings/sculptures; optional optimized thumbnails with modification note | **Each file** separately cleared; reject unknown/non-free/non-redistributable images |
| File returned by a Wikipedia image endpoint | **Not proof** that image can be redistributed | Confirm actual Commons file page and underlying creator/license (and whether image is local/fair-use) | No implicit approval based on thumbnail response |
| Source code of this repository | License choice **not yet set** | Keep code license separate from content licenses | Client approval of software license, no blanket license for combined data |

**Important:** “Everything under the least restrictive CC license” cannot be applied to **copyrighted Wikipedia excerpts or third-party images**. The independent output package may aggregate differently licensed assets with a per-file manifest, but it cannot silently convert those source terms into CC0/GPL or waive attribution/share-alike obligations. Additional rights and trademark review may be needed for particular use cases.

## Minimum metadata contract — editorial, not yet a chosen file schema

### For a Wikipedia excerpt
- `source_project` (e.g. `frwiki`), exact article ID/title/URL, article language.
- Page **revision ID and retrieval timestamp**, source text as faithfully obtained, and a stable link to the actual revision/history.
- Applicable text **license ID and URL**, attribution/contributor route and a visible credit phrase.
- Explicit `excerpted=true`, how the excerpt was selected/truncated (avoid mid-sentence loss), and any other changes/formatting. Do not present it as a newly authored Bible summary.
- Exact verified `wikidata_qid` and source TIPNR/OpenBible ID to ensure it belongs to the right subject. No cross-wiki translation assumption.

### For each image
- Commons (or verified hosting) **file page/title and stable source URL**, creator/artist, uploader only if relevant, credit line and original caption/description.
- Per-file license name, canonical license URL, attribution requirements and verified public-domain basis where applicable; avoid a generic “all images CC BY” flag.
- Source image URL and metadata acquisition timestamp/revision where available; distinguish original, derived thumbnail and any crop/resize/conversion.
- Subject-identity evidence: *actual modern archaeological-site photo*, *historical artwork/depiction*, or *other*, with uncertainty/relationship type. A later artistic depiction must not be called a photographic portrait.
- Avoid large original media in the package unless measured size and rights justify it; the gallery is optional.

## Reusable acquisition protocol (if the pilot is approved)

1. Start from a **reviewed Q-ID/person/place identity**. Do not search Wikipedia or Commons by name to manufacture correspondence.
2. Resolve the actual FR/EN article using sitelinks; fetch a bounded official article intro and page/revision metadata using supported, maintained APIs. Keep the original text separate by locale and license.
3. Get a main image/optional additional Commons files only if their **subject identity and per-file metadata** can be confirmed. Parse remote markup carefully and safely; metadata may include HTML, and it must not become active UI markup.
4. Use an identifiable **User-Agent with project URL/contact**. Obey Wikimedia's current rules, conservative concurrency (≤3 recommended at present), caching, exponential backoff and `429 Retry-After`. Do not retry indefinitely.
5. Save raw provenance/reference metadata **separately** from the normalized resource. Never regenerate a record with changed text, rights or an unrelated illustration without an auditable source delta.
6. Fail safely on missing article, changed revision, conflicting license, absent media credits or unresolved identity; this means **omit the affected enrichment**, not silently fill a gap.
7. After rights validation, a small optional **offline** resource can package selected text/data/verified thumbnails with credits; Bible itself does not need Wikimedia API access.

## Specific unresolved questions for the #2 acceptance gate

- Choose the exact source API endpoints that provide a **revision-bound** lead extract and the correct source license. An API “summary” might reflect a different revision than page metadata if fetched asynchronously: document how to detect/avoid this.
- Inspect **actual French and English articles** for attribution/revision/license details; prepare an example excerpt record without reprinting large third-party texts in Git.
- Inspect **one genuine Commons site photo and one historical artistic depiction** end to end: confirm author, exact reuse license, original file URL, credits, derived thumbnail rights, and subject identity. This has **not** been performed yet.
- Determine whether the original PTA candidate crosswalk can be redistributed as a derived database; **default to using it only as untrusted research input**, without copying its bulk data into any package.
- Confirm practical attribution in Bible's compact native card: Wikipedia excerpt followed by a visible article link and a discreet text-license/author credit, image credit available at least on image details; test accessibility later.
- Select a code license **separately** if requested by the owner; do not change visibility, publish a release, or assert that content license clearance is complete.

**Conclusion:** a mixed, optional offline package is **plausible**, but compliance is **per excerpt and per image**, not by setting one project-wide CC license. No third-party prose/image has been redistributed in this research.
