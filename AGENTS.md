# Agent instructions — Bible-Resources-Wikipedia

## Purpose and scope
Build an **optional offline resource of verified Wikimedia-derived information** for biblical people and places. The repository is a resource preparation project, **not** the Bible GNOME application and **not** the existing Bible-Resources SWORD repository.

Communicate with the user in **French**. Use **English** for GitHub issues, PRs, commits, code comments and documentation; preserve original Wikipedia source language.

Before making changes, read README.md, docs/PROJECT_PLAN.md, docs/EDITORIAL_POLICY.md, existing issues and PRs. Do not launch a later phase until its explicit evidence gate is satisfied.

## Integrity and editorial policy
- Preserve Bible content and user data; no writes to either application or the other resource repository unless separately requested.
- Inspect primary STEP TIPNR / OpenBible source formats, exact versions, original identity distinctions, provenance and applicable file licenses.
- A similar name, a translated name, a shared Strong number or an unreviewed third-party TIPNR→Wikidata mapping is **not** sufficient identity evidence. Log the evidence, source version, verdict and reviewer/reason for each accepted or rejected link; retain unresolved cases.
- Biblical individual, biblical location, proposed archaeological site and modern city must stay distinct; preserve conflicting identifications and uncertain history.
- Do not republish TIPNR AI-written descriptions as verified facts. Do not use AI to generate summaries, translations, biographical facts or missing links.
- Select small, typed Wikidata fields rather than scraping Wikipedia infobox HTML. Treat unsourced Wikidata statements cautiously.
- Wikipedia introductions are external licensed prose: preserve actual wording, source article/revision, language, authorship attribution route, link, license and any disclosed truncation. Do not merge across editions or silently translate.
- Commons files require per-file author/credit, file page, license, relevant restrictions and subject verification. Ancient people may have **artistic depictions**, not photographic portraits; label them accurately.
- No invented matching examples, placeholder citations, false 100% coverage claims or silent corrections. Missing data is acceptable.

## Production discipline
- Use only documented official upstream APIs or versioned original data, and comply with user-agent, rate limits (429/Retry-After), concurrency and caching rules.
- Scripts should be generic, deterministic, idempotent, documented and justified by repeated use. Do not create a script for a one-time manual action.
- Keep retrieved inputs/metadata and editorial decisions traceable separately from generated output. No raw bulk dumps or uncontrolled giant media assets in Git.
- Validate schemas, identity links, source revisions, licenses, duplicate IDs, ambiguous names, media attribution, Unicode, FR/EN, package checksums and no-match behavior.
- Prefer a small, simple format; no invented SWORD support or new data engine unless real constraints justify it. Preserve backwards compatibility or document migration.
- Keep generated outputs and licenses distinct from source code. **Do not add a blanket license to imported text/media.** Choose any code license only with an explicit repository decision.
- Work in staged, reviewable increments with automated evidence and manual editorial checks. Distinguish research, prepared code, tested package and published release.
- **No publication, public visibility change, release, catalog update or Bible app modification without explicit client authorization.** No work in other repositories by implication.
