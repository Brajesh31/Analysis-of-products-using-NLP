# 🧪 Testing and quality assurance strategy

## 1. What testing means for this repository

The repository currently contains Jupyter notebooks and a static HTML/CSS frontend. The tracked tree does not establish a full Python package or a mature automated test suite. Testing should therefore begin with notebook integrity, parser behaviour against synthetic fixtures, data validation, and browser checks.

Do not claim tests passed unless the command was run against the current commit and the result was inspected.

## 2. Notebook structural validation

Every notebook should:
- parse as valid JSON;
- declare a supported notebook format;
- contain a list of cells;
- use unique cell IDs;
- have valid cell types and source content;
- avoid embedding credentials and private data;
- keep saved outputs small and appropriate for public review.

A future CI job can validate JSON and cell structure without executing web requests. CI must not scrape retail platforms as part of routine pull-request validation.

## 3. Parser tests with synthetic fixtures

Do not use live retailer pages as the only test fixture. Page structure can change and automated CI should not send requests to external platforms. Instead, create small synthetic HTML fragments that represent the expected review container and edge cases.

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

## 4. Request-layer tests

When collection code is refactored into functions, test the request layer using mocked responses. Cover successful responses, timeouts, connection errors, non-success HTTP status, redirects, and unexpected content types. These tests should not issue actual retailer requests.

## 5. Data-quality tests

| Test | Expected result |
|---|---|
| Missing required source field | Reject or quarantine with a reason |
| Missing rating | Preserve null |
| Rating outside known source scale | Flag for review |
| Empty review body | Reject or classify according to documented policy |
| Duplicate stable identifier | Apply deterministic deduplication |
| Invalid timestamp | Reject or normalize with an explicit timezone policy |
| Unicode and emoji text | Preserve valid encoding |
| Unexpected markup | Produce a visible parser failure |
| Personal metadata detected | Exclude from analytical record |

## 6. Frontend verification

Open both `Frontend/index.html` and `Frontend/listing.html` through a local HTTP server. Test:
- image and stylesheet paths;
- filename case on a case-sensitive filesystem;
- desktop, tablet, and narrow viewport layouts;
- keyboard navigation and visible focus;
- heading hierarchy and semantic landmarks;
- meaningful alternative text;
- link destinations and interactive controls;
- browser console errors and failed network requests.

A visual screenshot is useful evidence only when captured from the real current page.

## 7. NLP evaluation tests

When an NLP model is introduced, test preprocessing determinism, label mapping, train/test isolation, class balance, duplicate leakage, and model serialization. Compare with a baseline and report class-wise metrics. Inspect errors manually.

## 8. Release gate

A release is ready only when its relevant tests are repeatable, limitations are documented, notebook outputs have been inspected, and no sensitive data or credentials are present. Record skipped tests and explain why they were not run.
