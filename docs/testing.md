# 🧪 Testing and quality assurance strategy

## 1. What testing means for this repository

The current repository contains two Jupyter notebooks and a static HTML/CSS frontend. A reusable Python package and full parser test suite are not established by the tracked tree. The repository now includes a GitHub Actions workflow, `.github/workflows/repository-quality.yml`, that performs deterministic structural checks on notebooks and Markdown. It does not execute live collection requests or prove that the retail selectors still match the source pages.

Testing should be layered: notebook integrity, request handling, parser behaviour on synthetic fixtures, record validation, frontend browser checks, and NLP evaluation when a model exists.

## 2. Automated checks currently configured

The repository quality workflow runs on relevant pushes, pull requests, and manual dispatch. Its current checks:
- parse every tracked Jupyter notebook as JSON;
- require notebook format version 4;
- verify that the cells property is a list;
- validate supported cell types and source field shape;
- require non-empty cell IDs and reject duplicate IDs;
- check Markdown fenced-code-block balance;
- check Markdown trailing whitespace;
- check ordinary relative Markdown links resolve to tracked files.

These checks are structural. They do not execute notebook cells, access retail websites, validate HTML selectors against live pages, or measure model quality.

## 3. Notebook structural validation

Every notebook should:
- parse as valid JSON;
- declare a supported notebook format;
- contain a list of cells;
- use unique cell IDs;
- have valid cell types and source content;
- avoid embedding credentials and private data;
- keep saved outputs small and appropriate for public review.

Before committing a notebook, restart the kernel and confirm the intended execution order. Inspect the saved JSON for output that may not be visible at first glance.

## 4. Parser tests with synthetic fixtures

Do not use live retailer pages as the only test fixture. Page structure can change, and automated CI should not send requests to external retail platforms. Instead, create small synthetic HTML fragments that represent the expected review container and edge cases.

Test at least:
- one valid review;
- several reviews;
- missing review text;
- missing rating;
- malformed or unexpected markup;
- nested tags and whitespace;
- non-English characters;
- emojis and punctuation;
- duplicate identifiers;
- a page with no review container;
- unrelated page content that must not be captured.

Fixtures must not contain real customer identities or private review data.

## 5. Request-layer tests

When collection code is refactored into functions, test the request layer using mocked responses. Cover successful responses, timeouts, connection errors, non-success HTTP status, redirects, and unexpected content types. These tests should not issue actual retailer requests.

A 401, 403, or 429 response should stop the collection attempt. Do not test or implement logic that bypasses those restrictions.

## 6. Data-quality tests

| Test | Expected result |
|---|---|
| Missing required source field | Reject or quarantine with a reason |
| Missing rating | Preserve null |
| Rating outside known source scale | Flag for review |
| Empty review body | Reject or classify according to documented policy |
| Duplicate stable identifier | Apply deterministic deduplication |
| Invalid timestamp | Reject or normalize with explicit timezone policy |
| Unicode and emoji text | Preserve valid encoding |
| Unexpected markup | Produce a visible parser failure |
| Personal metadata detected | Exclude from analytical record |

## 7. Frontend verification

Open both `Frontend/index.html` and `Frontend/listing.html` through a local HTTP server. Test image and stylesheet paths, filename case on case-sensitive filesystems, desktop and narrow viewport layouts, keyboard access, visible focus, heading hierarchy, meaningful alternative text, link destinations, interactive controls, browser console errors, and failed network requests.

## 8. NLP evaluation tests

When an NLP model is introduced, test preprocessing determinism, label mapping, train/test isolation, class balance, duplicate leakage, and model serialization. Compare with a baseline and report class-wise metrics. Inspect errors manually. Model evaluation must use a held-out dataset that was not used for tuning.

## 9. Release gate

A release is ready only when relevant automated checks pass, manual checks are recorded, notebook outputs have been inspected, and no sensitive data or credentials are present. Record skipped tests and explain why they were not run. Never describe structural CI checks as proof of live scraping correctness or model accuracy.
