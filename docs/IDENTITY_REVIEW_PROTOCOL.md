# Identity link review protocol — draft

**Status:** proposed editorial rules for issue #1, 15 November 2026. These rules do not approve any candidate links, package schema, Wikipedia text, image reuse, release or changes to Bible.

## 1. Two independent questions

Every source-to-Wikidata association must answer **both** questions:

1. **What does the target Q-ID describe?** The biblical individual/place *as a subject*, an ancient archaeological site, a modern settlement on an ancient site, a hypothetical location, or only a related topic?
2. **What fields may be reused?** A relevant article is not proof that every Q-ID statement, coordinate, image, date, administrative label or modern statistic refers to the ancient/biblical entity.

An accepted **article-topic** link must never silently turn into a verified geographic site link.

## 2. Candidate review record

For each candidate, preserve the original input untouched and record the following independently reviewable fields. This is a **review log concept**, not a final publication schema:

| Field | Required purpose |
| --- | --- |
| `source_provider`, `source_commit`, `source_record_id`, `entity_type` | Pin the exact STEP TIPNR / OpenBible entity and revision, distinguishing namesakes |
| `candidate_qid`, `candidate_origin` | Preserve what was proposed, including source file and original link modifier/review flag |
| `identity_verdict` | One of `accepted`, `rejected`, `unresolved`. Missing evidence defaults to `unresolved` |
| `relationship_kind` | `biblical_subject`, `related_modern_site`, `proposed_location`, `related_topic`, `not_same` (extend only with documented reason) |
| `biblical_reference_context` | Actual passage(s) disambiguating the source entity |
| `positive_evidence`, `negative_evidence`, `review_reason` | Citable primary/source or independent scholarly/authority evidence, plus conflicts |
| `reviewed_by`, `reviewed_on` | Traceable editorial review, not an implied automatic decision |
| `allowed_uses` | Separately reviewed `article_topic`, `typed_facts`, `location`, `image_subject` gates; deny by default |
| `source_revisions_checked` | Record version of every original input and checked Wikidata page/data claim |

Do not silently convert a weak `relationship_kind` to `biblical_subject`. Do not merge distinct TIPNR person IDs because they share a name, alias, Strong number or candidate Q-ID.

## 3. Decision gates

- **Accepted — topic identity:** the original biblical reference and source ID distinguish the referent, the Q-ID clearly describes that referent, and independently checked evidence does not contradict the linkage. Acceptance must specify `relationship_kind` and permit only the individually validated usages.
- **Accepted — related modern site:** credible evidence places a later settlement/site at or near the ancient referent, but **does not imply sameness across historical periods**. Keep the relationship explicit. Modern population, foundation dates and images must remain described as modern.
- **Proposed location:** an ancient place has several plausible modern identifications. Preserve proposals, evidence and uncertainty. **Do not provide a single definitive coordinate** merely because one Q-ID or article has one.
- **Rejected:** a contradiction in the biblical record, target type, period, genealogy or source modifier demonstrates that the direct identity is wrong. Keep the rejected candidate and rationale in the review log as a regression case.
- **Unresolved:** source/version mismatch, uncertain referent, insufficient supporting evidence or ambiguous ancient/modern relation. Exclude a direct enrichment link until reviewed.

A name match; `P460` (“said to be the same as”); an imported-from-Wikipedia reference; a Wikipedia sitelink; an image (`P18`); or proximity of coordinates is **not independent identity proof**.

## 4. Field-specific safety checks

- **Text:** resolve the actual article and locale **only after** approving its intended subject; every excerpt still needs separate exact-revision and license clearance (#2).
- **Facts:** allow only fields whose semantic subject and time period are correct. A modern municipality's inception/population does not describe an ancient biblical settlement. Wikidata has variable claim sourcing and statements may conflict.
- **Coordinates:** require an explicit geographical identification and evidence; otherwise show no authoritative point. Proposed sites may be listed as proposals, clearly qualified.
- **Images:** require individual media licensing and verified subject relationship. An archaeological-site photo is not a reconstruction of the biblical-era place; an artwork depicting a person is not a portrait photograph.
- **Coverage:** distinguish candidates, accepted links, disallowed links and link kinds in reports. Do not publish a single percentage of “matched” records based on nonempty Q-IDs.

## 5. Regression cases to keep

| Source / candidate | Decision and check |
| --- | --- |
| `Shimon_1Ch.4.20 → Q33923` (Peter) | **Reject**; homonymous Old Testament individual versus New Testament apostle |
| `Hoshea_2Ki.15.30 → Q7734` (Joshua) | **Reject**; king of Israel versus Joshua son of Nun |
| `Azariah_2Ch.26.17 → Q313216` (Uzziah) | **Reject**; priest opposing the king versus king |
| `Mattathias_Luk.3.25/.26 → Q44020` (Matthias) | **Reject**; separate genealogy individuals versus apostle |
| `Emmaus@Luk.24.13 → Q165887` | **Candidate as biblical subject**; do **not** accept Q-ID coordinates or alternative P460 site identities as settled |
| `Bethlehem 2 / a308715 → Q604557` | **Unresolved strict ancient identity; candidate related modern site**; do not apply a modern moshav's 1948 inception to Joshua 19:15 |
| `Moreh 2 → Q1092415` | **Unresolved strict identity**, possible modern geographic relationship only |
| OpenBible records with `modifier=not` | **Exclude direct identity**, regardless of matching Q-ID syntax |

Sources and review details: [pinned input audit](evidence/IDENTITY_SOURCE_AUDIT_2026-11-15.md) and [review cases](evidence/IDENTITY_SPOTCHECK_2026-11-15.md). Additional field checks: [OpenBible Emmaus site](https://www.openbible.info/geo/ancient/ae7274b/emmaus), [Wikidata Emmaus Q165887](https://www.wikidata.org/wiki/Q165887), [BiblIndex Emmaus record](https://www.biblindex.org/en/bible-names/198), [Wikidata Bethlehem of Galilee Q604557](https://www.wikidata.org/wiki/Q604557), and [Aviram Oshri's archaeological discussion](https://library.biblicalarchaeology.org/book/the-new-encyclopedia-of-archaeological-excavations-in-the-holy-land/bethlehem-of-galilee/).

## 6. Remaining #1 audit gate

- Review a stratified sample of original people and places, not just obvious candidates.
- Identify the causes of the **138** OpenBible strict-ID nonmatches and **147** reused TIPNR-place-ID groups before constructing a crosswalk.
- Check whether different original STEP records genuinely denote the same person/site, recording alias-versus-namesake evidence.
- Record a machine-auditable set of review decisions with exact source snapshot and independent counterchecks, including accepted and rejected examples.
- Report measured validation/precision **for the sampled reviewed population only**, and whether a 20–30 entity pilot is defensible.

**No mass import or release** follows from this draft protocol.