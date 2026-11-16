# 🗂️ Repository structure and file responsibilities

## 1. Current tracked layout

This is a conceptual inventory of the tracked paths inspected on the default branch. The `Frontend/assets/` directory contains multiple existing image and SVG files; they are grouped below to keep the tree readable.

```text
Analysis-of-products-using-NLP/
├── .github/
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
│       └── update-readme.yml
├── .editorconfig
├── .env.example
├── .gitattributes
├── .gitignore
├── .idea/
│   └── .gitignore
├── CHANGELOG.md
├── CITATION.cff
├── CODEOWNERS
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
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
├── LICENSE
├── README.md
├── ROADMAP.md
├── SECURITY.md
├── SUPPORT.md
├── Web Scraping – Flipkart Customer Reviews.ipynb
├── Web Scraping – Myntra Customer Reviews.ipynb
└── docs/
    ├── README.md
    ├── api.md
    ├── architecture.md
    ├── database.md
    ├── deployment.md
    ├── development.md
    ├── faq.md
    ├── installation.md
    └── troubleshooting.md
```

## 2. Root-level responsibilities

| File | Responsibility | Maintenance rule |
|---|---|---|
| `README.md` | First point of orientation | Keep concise enough to scan, link deep guides |
| `LICENSE` | Legal license terms | Do not alter casually; review license changes explicitly |
| `CONTRIBUTING.md` | Contribution workflow | Keep steps actionable and consistent with CI |
| `SECURITY.md` | Vulnerability and data-exposure reporting | Never request public disclosure of secrets |
| `CODE_OF_CONDUCT.md` | Community expectations | Keep reporting and enforcement process clear |
| `SUPPORT.md` | Help and troubleshooting entry point | Request sanitized diagnostics only |
| `CHANGELOG.md` | Historical change record | Add dated, user-visible changes |
| `ROADMAP.md` | Planned work | Distinguish planned, active, and completed items |
| `CITATION.cff` | Citation metadata | Keep author, title, repository, and license accurate |
| `.env.example` | Safe environment-variable documentation | Never include real values |
| `.gitignore` | Exclude local and generated artefacts | Avoid broad rules that hide important source files |

## 3. Frontend responsibilities

- `Frontend/index.html`: main page structure and content.
- `Frontend/index.css`: styling associated with the main page.
- `Frontend/listing.html`: product/listing interface structure.
- `Frontend/listing.css`: listing page styling.
- `Frontend/assets/`: images, logos, icons, and social artwork.

The inspected tree does not show a frontend package manifest or build configuration. Do not assume React, a bundler, or a backend framework. Preserve relative paths and exact filename case when changing HTML or CSS.

## 4. Notebook responsibilities

- `Web Scraping – Flipkart Customer Reviews.ipynb`: an exploratory Requests/BeautifulSoup collection notebook with a broad `row` selector in its current code.
- `Web Scraping – Myntra Customer Reviews.ipynb`: an exploratory Requests/BeautifulSoup notebook using a platform-specific review container selector.

The current notebooks are not a reusable crawler framework. Their selectors may become stale and their outputs must be checked for personal data before publication.

## 5. Documentation responsibilities

The `docs/` directory should contain project-specific guides for architecture, workflow, schema, NLP methodology, responsible collection, testing, deployment, and troubleshooting. The documentation index is the navigation source of truth.

## 6. Proposed future structure

If reusable code and tests are added, a future layout could be:

```text
src/
├── collection/
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

This is a proposal, not the current tree. Do not move the existing notebooks or frontend assets simply to match it. Any migration should preserve history where practical, update links, and include a compatibility note.

## 7. File-change rule

When a file is added or removed, update this guide and the documentation index. Do not document local caches, credentials, private datasets, or generated artefacts as public repository contents.
