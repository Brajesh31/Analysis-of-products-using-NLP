# 📋 Changelog

All notable repository changes should be recorded here. Entries describe changes to tracked project files, not claims about model quality or production deployment. Dates reflect the repository update date; historical entries are retained only where already recorded.

The format uses an Unreleased section followed by dated release sections. Group changes under Added, Changed, Fixed, Security, and Removed where useful.

## [Unreleased]

### Added
- Detailed project overview, repository structure, workflow, data schema, and NLP methodology guides.
- Collection notebook operating guide documenting the exact current selectors, request checks, data fields, and limitations.
- Analysis-reporting standard and reusable report template.
- Accessibility, performance, limitations, responsible-data, and testing guides.
- Editable Mermaid architecture, lifecycle, and CI diagrams.
- Architecture decision record index and reusable ADR template.
- Governance, maintainer, release, accessibility, and technical-debt documents.
- Structured bug, feature, and documentation issue forms.
- Repository quality workflow for notebook JSON structure and Markdown hygiene.

### Changed
- Expanded the root README with project scope, installation, diagrams, data contract, methodology, safeguards, limitations, and documentation navigation.
- Expanded API, database, deployment, development, installation, FAQ, and troubleshooting guides.
- Expanded contribution, security, code-of-conduct, support, roadmap, and pull-request guidance.
- Reworked the Flipkart and Myntra notebooks to include explanatory Markdown, explicit request timeouts, HTTP response validation, narrow candidate review-body selectors, minimal extracted fields, sanitized summary output, and optional local CSV export disabled by default.
- Removed saved notebook outputs from the revised collection notebooks to avoid carrying forward reviewer-identifying page content.
- Refined `.gitignore` to exclude local datasets and generated artefacts without globally ignoring every JSON file.
- Changed README timestamp refresh from hourly to weekly to reduce unnecessary automated commits.

### Security
- Documented that collection must stop on access denial or rate limiting and must not bypass platform restrictions.
- Added explicit guidance against collecting reviewer identities and committing raw personal data, cookies, or credentials.

### Validation notes
- Notebook JSON structure and unique cell IDs were inspected after the notebook rewrites.
- No live retail collection request was executed as part of these repository documentation changes.
- Candidate selectors still require verification against current permitted source markup.
- Structural GitHub Actions checks do not prove selector correctness or model accuracy.

## [0.1.0] - 2025-01-01

### Added
- Exploratory Flipkart and Myntra review-scraping notebooks.
- Static product-analysis and product-listing frontend prototype.

## Changelog maintenance

For each future change:
1. Add the entry under Unreleased.
2. Describe user-visible behaviour, not internal activity alone.
3. Mention data schema or methodology changes explicitly.
4. Record security-relevant fixes without exposing exploit details.
5. Move Unreleased entries into a dated version section when tagging a release.

Do not invent historical entries. If an older release date or feature cannot be verified, leave it undocumented rather than guessing.
