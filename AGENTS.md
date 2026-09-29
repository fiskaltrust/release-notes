# Agent instructions for the fiskaltrust release notes

This repository contains the customer-facing release notes published at https://docs.fiskaltrust.cloud/changelog.

## How files are built and published

- Every `**/*.md` / `**/*.mdx` file becomes a changelog post, except `_*` files, `_*/` folders, `README.md`, `AGENTS.md`, `CLAUDE.md` and dot-folders such as `.github/`.
  Any other non-release-note Markdown file must be excluded the same way (frontmatter `draft: true` and/or an exclude entry in `service-docs-ui`).
- The URL is `/changelog/<slug>`, taken from the `slug:` frontmatter.
- The post date is taken from the `YYYY-MM-DD-` filename prefix (two-digit month and day), unless `date:` is set in the frontmatter.
- The title is taken from the first `# H1` heading, unless `title:` is set in the frontmatter.
- `authors:` must reference a key in `authors.yml`.
- Every post needs a `<!--truncate-->` marker. Broken links, broken anchors and duplicate slugs fail the build.
- Pull requests run a lychee link check and a full site build.
  **Merging to `main` publishes immediately**, so don't merge release notes for an unreleased version.
