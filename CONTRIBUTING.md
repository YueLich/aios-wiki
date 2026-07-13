# Contributing

Thanks for helping improve Mobile AIOS Wiki. A few ways to contribute:

## Suggest a source

If you know an RSS feed, blog, GitHub repo, or publication we should be tracking, [open a "Suggest a source" issue](../../issues/new?template=suggest-source.md). See the current source list in [.meta/sources.json](.meta/sources.json).

## Report an error

Found something wrong, outdated, or a broken link? [Open a "Report an error" issue](../../issues/new?template=report-error.md) with the page URL and what's wrong.

## Submit content directly

PRs are welcome for:

- Fixing typos, broken links, or formatting
- Adding sources/citations to an existing page
- Correcting factual errors

For new pages, please match the existing format — see [AGENTS.md](AGENTS.md) for the quality bar (word count, source count, wikilinks, frontmatter schema) and [SCHEMA.md](docs/SCHEMA.md) for the exact frontmatter fields.

A few things to know before you send a PR:

- Pages under `docs/` with `status: featured` in their frontmatter are hand-curated — changes to them need a clear rationale in the PR description, since they're what the README highlights.
- New pages should go in the correct subfolder (`docs/entities/`, `docs/concepts/`, `docs/comparisons/`, `docs/queries/`) and include wikilinks to related existing pages.
- Keep `docs/index.md` and `mkdocs.yml` nav in sync if you add or move a page.

## Code of conduct

Be respectful, cite your sources, and don't submit AI-generated pages that haven't been fact-checked against real sources — the whole point of this wiki is that its content can be trusted.
