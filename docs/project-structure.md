# 🗂️ Repository structure and file responsibilities

## 1. Current tracked layout

This inventory reflects the tracked paths inspected on the default branch after the documentation expansion. The many individual image and SVG files under `Frontend/assets/` are grouped below. The structure is intentionally split between current files and proposed future folders.

```text
Analysis-of-products-using-NLP/
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.yml
│   │   ├── feature_request.yml
│   │   ├── documentation.yml
│   │   └── config.yml
│   ├── workflows/
│   │   ├── update-readme.yml
│   │   └── repository-quality.yml
│   └── PULL_REQUEST_TEMPLATE.md
├── .editorconfig
├── .env.example
├── .gitattributes
├── .gitignore
├── .idea/
│   └── .gitignore
├── ACCESSIBILITY.md
├── CHANGELOG.md
├── CITATION.cff
├── CODEOWNERS
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── GOVERNANCE.md
├── LICENSE
├── MAINTAINERS.md
├── README.md
├── RELEASE.md
├── ROADMAP.md
├── SECURITY.md
├── SUPPORT.md
├── TECHNICAL_DEBT.md
├── Frontend/
│   ├── assets/
│   │   ├── product and team photographs
│   │   ├── page illustrations and logo
│   │   ├── social media SVGs
│   │   └── interface icons
│   ├── index.html
│   ├── index.css
│   ├── listing.html
│   └── listing.css
├── Web Scraping – Flipkart Customer Reviews.ipynb
├── Web Scraping – Myntra Customer Reviews.ipynb
└── docs/
    ├── README.md
    ├── accessibility.md
    ├── analysis-reporting.md
    ├── api.md
    ├── architecture.md
    ├── collection-notebook-guide.md
    ├── data-and-schema.md
    ├── database.md
    ├── deployment.md
    ├── diagrams.md
    ├── development.md
    ├── faq.md
    ├── future-scope.md
    ├── installation.md
    ├── limitations.md
    ├── nlp-methodology.md
    ├── performance.md
    ├── project-overview.md
    ├── project-structure.md
    ├── responsible-data.md
    ├── testing.md
    ├── troubleshooting.md
    ├── workflow.md
    ├── decisions/
    │   └── README.md
    └── templates/
        ├── analysis-report-template.md
        └── architecture-decision-record.md
```

## 2. Root-level project files

| File | Purpose | Maintenance expectation |
|---|---|---|
| `README.md` | Project introduction, setup, diagrams, and navigation | Keep claims aligned with actual code |
| `LICENSE` | Legal terms for use and distribution | Change only through an explicit license decision |
| `CONTRIBUTING.md` | Contribution and review process | Keep validation steps actionable |
| `SECURITY.md` | Vulnerability and data-exposure handling | Never request public secrets or private data |
| `CODE_OF_CONDUCT.md` | Community expectations and enforcement | Keep reporting route clear |
| `GOVERNANCE.md` | Decision and stewardship process | Record consequential policy changes |
| `MAINTAINERS.md` | Maintainer identity and responsibilities | Keep role information current |
| `ACCESSIBILITY.md` | Top-level accessibility expectations | Do not claim formal conformance without an audit |
| `SUPPORT.md` | Support request guidance | Ask for sanitized reproducible diagnostics |
| `CHANGELOG.md` | Historical user-visible changes | Do not invent historical entries |
| `ROADMAP.md` | Planned engineering phases | Mark complete only with evidence |
| `RELEASE.md` | Release and rollback procedure | Include tests and known limitations |
| `TECHNICAL_DEBT.md` | Verified gaps and recommended priorities | Close items only after validation |
| `CITATION.cff` | Citation metadata | Keep author, title, repository, and license accurate |
| `CODEOWNERS` | Default review ownership | Keep ownership aligned with maintainers |
| `.env.example` | Safe configuration documentation | Use placeholders only |
| `.gitignore` | Local data, secrets, and generated files | Avoid broad patterns that hide source files |

## 3. Dependency manifests\n\n- `requirements.txt` lists the direct runtime packages used by the collection notebooks.\n- `requirements-dev.txt` adds JupyterLab and notebook-format tooling for local development.\n- These files use bounded version ranges and are not a hash-locked dependency solution. See [Reproducibility](reproducibility.md).\n\n## 4. Frontend responsibilities

- `Frontend/index.html`: main page structure and content.
- `Frontend/index.css`: styling for the main page.
- `Frontend/listing.html`: product/listing interface structure.
- `Frontend/listing.css`: listing page styling.
- `Frontend/assets/`: existing product images, team imagery, logo, icons, and social assets.

The inspected tree does not show a frontend package manifest or build configuration. Do not assume a React application, bundler, or backend framework. Preserve relative paths and exact filename case when changing HTML or CSS.

See [Frontend README](../Frontend/README.md) and [Frontend guide](frontend-guide.md) for local preview, asset handling, accessibility, screenshots, and review standards.\n\n## 5. Notebook responsibilities

### Flipkart notebook

The notebook uses Requests and BeautifulSoup. Its earlier version selected every `div.row`, a broad selector that captured unrelated product content and reviewer metadata. The revised notebook uses a narrow candidate review-body selector, explicit request timeout and response validation, and optional local CSV export disabled by default. The selector still requires verification against current permitted markup.

### Myntra notebook

The notebook uses Requests and BeautifulSoup with a candidate review-body selector based on the original notebook's review-text wrapper. It now documents the collection assumptions, validates the HTTP response, avoids reviewer identity fields, and keeps local CSV export disabled by default. The selector can become stale and must be checked before execution.

Both notebooks are exploratory. Neither implements a production crawler, pagination service, shared Python package, or sentiment model.

## 6. Documentation responsibilities

The `docs/` directory is the detailed technical reference:
- project scope, structure, and architecture;
- collection and data workflow;
- notebook-specific operating guidance;
- schema and data quality;
- NLP methodology and evaluation;
- responsible collection and privacy;
- testing, performance, and accessibility;
- analysis reporting, diagrams, and templates;
- API/database status, deployment, setup, and troubleshooting;
- limitations and future scope.

The documentation index at `docs/README.md` is the navigation source of truth. Update it whenever a guide is added, renamed, or removed.

## 7. GitHub automation responsibilities

- `.github/ISSUE_TEMPLATE/` provides structured bug, feature, and documentation reports.
- `.github/PULL_REQUEST_TEMPLATE.md` asks contributors for scope, validation, privacy, accessibility, and rollback information.
- `.github/workflows/repository-quality.yml` validates notebook JSON structure and Markdown hygiene. It must not make live requests to retail platforms.
- `.github/workflows/update-readme.yml` refreshes the README timestamp weekly or manually. It should not create noisy hourly commits.

## 8. Proposed future application layout

If reusable collection and analysis code is added, consider the following structure:

```text
src/
├── collection/
│   ├── base.py
│   ├── flipkart.py
│   └── myntra.py
├── schemas/
├── preprocessing/
├── analysis/
└── reporting/
tests/
├── fixtures/
├── unit/
└── integration/
data/
├── samples/
├── raw/          # local/restricted only, never committed by default
└── processed/    # local/generated, never committed by default
reports/
└── generated/    # local output, reviewed before publication
```

This is a proposal, not the current tree. Do not move the existing notebooks or frontend assets simply to match it. A migration should preserve history where practical, update all links, and include a compatibility note.

## 9. File-change and review rule

When a tracked file or directory is added or removed:
1. Update this inventory.
2. Update the documentation index.
3. Update README navigation when the change affects users or contributors.
4. Add tests or a validation procedure.
5. Check that no local caches, credentials, private datasets, or generated artefacts have been added accidentally.
