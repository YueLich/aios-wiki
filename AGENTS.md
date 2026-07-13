# Maintenance rules

These rules govern the automated agent(s) that scan sources and write pages into this repo, and any human maintainer picking up the same job. The crawler/scan logic itself does not live in this repo (see `.meta/sources.json` for the source config); this file is the contract it must follow when it commits here.

## Cadence

- **Scan**: once daily, not hourly. Hourly commit noise drives visitors away and doesn't change the reading experience — batching is strictly better.
- **Commit**: squash each day's changes into one commit: `chore(daily): 2026-07-10 +3 drafts, 1 promoted`.
- **Weekly digest**: every Sunday, generate `docs/weekly/YYYY-Www.md` summarizing the week's promoted pages and publish it as a GitHub Release. Releases are what watchers actually get notified about — this is the primary retention mechanism, treat it as required, not optional.

## New page workflow

1. **Dedupe first.** Normalize the source URL and compare title similarity to existing pages; anything ≥0.85 similar is a duplicate — skip it, don't create a near-copy.
2. **Drafts land in `_inbox/`, not `docs/`.** New pages start with `status: auto-draft` in frontmatter and live in `_inbox/` until reviewed. Nothing in `_inbox/` is linked from `docs/index.md` or the mkdocs nav.
3. **Quality gate before a page is even created**:
   - ≥800 words of body content
   - ≥2 sources, each with `url`, `date`, and `reliability`
   - ≥3 wikilinks to existing pages
   - frontmatter passes the schema in [SCHEMA.md](docs/SCHEMA.md) (or its current location)

   If a candidate can't clear this bar, don't create a stub — leave it out until there's enough material.
4. **Promotion to `docs/`** requires cross-checking the claim against ≥2 independent sources. Once promoted, set `status: reviewed`. Non-trivial promotions (anything more than fixing a typo) go through a PR, not a direct push to `main`.

## Monthly maintenance

- **Link check**: mark dead sources with a ⚠️ next to the citation rather than silently dropping them.
- **Staleness**: pages with no source updates in >6 months get a `stale` tag.
- **Dedup pass**: merge near-duplicate pages that drifted apart over time.
- **Rebuild** `docs/index.json` and the knowledge graph after any structural change.
- **Comparisons refresh**: version numbers and benchmark figures in `docs/comparisons/` get re-checked against current releases.

## Hard rules

- **Never edit a `status: featured` page directly.** Featured pages are hand-curated; changes to them go through a PR for human review, no exceptions.
- **Never delete content a human has edited.** If a page has a non-agent author in its git history, treat it as off-limits for automated rewrites — flag it instead.
- **Circuit breaker**: if a single day's scan would create more than 10 new pages, stop and open an issue instead of committing. That volume usually means a source is malfunctioning (duplicate feed entries, a scraper looping) rather than 10 genuinely new, distinct developments — it needs a human look before it lands in the repo.
- **Never touch `docs/` top-level structure** (renaming `entities/`, `concepts/`, etc.) without a corresponding update to `mkdocs.yml` nav in the same commit — a structural change that breaks the nav breaks the deployed site.
