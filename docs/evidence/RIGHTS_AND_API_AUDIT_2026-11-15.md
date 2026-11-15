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

## File-by-file Commons spot check (source pages, no images republished)

The following **actual** Wikimedia Commons file pages were checked. They illustrate why a package needs per-file rights metadata, subject labels and **bounded thumbnails** rather than indiscriminately bundling the full-sized originals. None of these files or their image bytes has been downloaded or committed here, and the Commons API's machine-readable `imageinfo.extmetadata` has **not yet been exercised**.

| Actual file page | Source, identity, original dimensions / bytes | Visible rights evidence and required presentation |
| --- | --- | --- |
| [Panorama of Jerusalem from Mount of Olives](https://commons.wikimedia.org/wiki/File:Panorama_of_Jerusalem_from_Mount_of_Olives.jpg) | Modern Jerusalem panorama photographed by **Jakub CA**, 24 October 2019; original **10,000 × 3,840 pixels / 16.53 MB**. | The Commons file page explicitly lists [**CC BY-SA 4.0**](https://creativecommons.org/licenses/by-sa/4.0/). Credit the photographer, source file page and license; indicate any resizing/cropping. It represents the **modern city**, not an image of ancient Jerusalem. |
| [Jerusalem from the Mount of Olives (53714451089)](https://commons.wikimedia.org/wiki/File:Jerusalem_from_the_Mount_of_Olives_(53714451089).jpg) | Modern Jerusalem panorama by **Mustang Joe**, taken 10 September 2023; original **12,504 × 3,877 / 36.33 MB**, transferred from Flickr. | Commons specifies [**CC0 1.0**](https://creativecommons.org/publicdomain/zero/1.0/); its Flickr-source license was reviewed by FlickreviewR 2 on **9 January 2025**. Preserve source/creator provenance even if legally optional; do not mistake an uploaded-by account for the creator. |
| [Rembrandt, *Abraham and Isaac* (1645)](https://commons.wikimedia.org/wiki/File:Rembrandt_Abraham_and_Isaac.jpg) | Etching and burin print by **Rembrandt van Rijn**, date **1645**, held by the National Gallery of Art, Washington; digital original **3,292 × 4,000 / 5.36 MB**. | Commons states the artwork is **public domain** based on the creator's death and marks the file [Public Domain Mark 1.0](https://creativecommons.org/publicdomain/mark/1.0/), with a separate note about US-public-domain tagging. The displayed object is an **artistic representation of Abraham and Isaac**, never a portrait photograph or a visual proof of the events. Attribute creator, work and archive source in context. |

**Important limitations:** Commons descriptions can include template-generated attribution terms, copyright badges, references to underlying photographs/reproductions, and US/source-country distinctions. These examples document the visible file pages; the actual acquisition stage must **parse the supported media API, select an explicit valid license path and verify relevant rights before shipping a thumbnail**. The bare presence of a Commons page, a Wikidata image statement (`P18`) or a Wikimedia thumbnail URL is **not itself a redistribution clearance**. These three examples are **not approved package records**, because no item-to-biblical-entity image relationship has yet undergone the editorial pilot's acceptance check.

## Reusable acquisition protocol (if the pilot is approved)

1. Start from a **reviewed Q-ID/person/place identity**. Do not search Wikipedia or Commons by name to manufacture correspondence.
2. Resolve the actual FR/EN article using sitelinks; fetch a bounded official article intro and page/revision metadata using supported, maintained APIs. Keep the original text separate by locale and license.
3. Get a main image/optional additional Commons files only if their **subject identity and per-file metadata** can be confirmed. Parse remote markup carefully and safely; metadata may include HTML, and it must not become active UI markup.
4. Use an identifiable **User-Agent with project URL/contact**. Obey Wikimedia's current rules, conservative concurrency (≤3 recommended at present), caching, exponential backoff and `429 Retry-After`. Do not retry indefinitely.
5. Save raw provenance/reference metadata **separately** from the normalized resource. Never regenerate a record with changed text, rights or an unrelated illustration without an auditable source delta.
6. Fail safely on missing article, changed revision, conflicting license, absent media credits or unresolved identity; this means **omit the affected enrichment**, not silently fill a gap.
7. After rights validation, a small optional **offline** resource can package selected text/data/verified thumbnails with credits; Bible itself does not need Wikimedia API access.

## Revision-bound Wikipedia introduction: preferred research approach

The **official MediaWiki REST API reference** [documents](https://www.mediawiki.org/wiki/API:REST_API/Reference) `GET /w/rest.php/v1/page/{title}/with_html`: its response combines **page metadata** (including `latest.id`, `latest.timestamp`, page `license`) and the page HTML, allowing the prepared excerpt to be tied to the same revision as the source text. Individual revision endpoints (`/revision/{id}/with_html`) can also re-read an exact revision. This is better for a frozen offline package than fetching an unversioned introductory sentence and a separate current revision that might change between requests. The specification is documented; **a real authenticated/identified request still needs to be tested with a compliant HTTP client**.

The separate [Page Content Service](https://www.mediawiki.org/wiki/Page_Content_Service) documents a page-summary response with first-paragraph `extract` / `extract_html` and images, attractive for concise previews. However **do not assume the summary text and a separately obtained page revision are from the same revision** without verifying returned revision identifiers and API consistency. If no revision-anchored summary route can be established, derive a carefully delimited opening paragraph from exact-revision HTML rather than silently mixing versions; document any excerpting, HTML sanitation and citation handling.

**Execution limitation in this audit:** public Wikipedia REST endpoint URLs could not be fetched through the available research browser (a disabled-fetch error). This is a **research environment limitation**, not evidence that Wikipedia's own API is unavailable or that an implementation request failed in a compliant Python client. No FR/EN page revision, excerpt or end-to-end API compatibility has been independently verified yet. The #2 acceptance gate remains open.

## Specific unresolved questions for the #2 acceptance gate

- Choose the exact source API endpoints that provide a **revision-bound** lead extract and the correct source license. An API “summary” might reflect a different revision than page metadata if fetched asynchronously: document how to detect/avoid this.
- Inspect **actual French and English articles** for attribution/revision/license details; prepare an example excerpt record without reprinting large third-party texts in Git.
- Inspect **one genuine Commons site photo and one historical artistic depiction** end to end: confirm author, exact reuse license, original file URL, credits, derived thumbnail rights, and subject identity. This has **not** been performed yet.
- Determine whether the original PTA candidate crosswalk can be redistributed as a derived database; **default to using it only as untrusted research input**, without copying its bulk data into any package.
- Confirm practical attribution in Bible's compact native card: Wikipedia excerpt followed by a visible article link and a discreet text-license/author credit, image credit available at least on image details; test accessibility later.
- Select a code license **separately** if requested by the owner; do not change visibility, publish a release, or assert that content license clearance is complete.

**Conclusion:** a mixed, optional offline package is **plausible**, but compliance is **per excerpt and per image**, not by setting one project-wide CC license. No third-party prose/image has been redistributed in this research.
