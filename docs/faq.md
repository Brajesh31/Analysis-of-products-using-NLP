# ❓ Frequently asked questions

## Is this a production sentiment-analysis service?
No. The inspected repository contains review-collection notebooks and a static frontend prototype. It does not establish a production sentiment model, backend API, or persistent analysis service.

## Which review sources are represented?
The repository contains separate notebooks named for Flipkart customer reviews and Myntra customer reviews. Their page selectors and assumptions are platform-specific and may become outdated.

## Can the notebooks scrape any product page?
No. They were written for particular page structures. Use only collection methods permitted by the relevant platform and applicable law. Do not bypass login requirements, CAPTCHAs, access controls, or rate limits.

## Does the frontend compare live prices?
The tracked project does not establish a live price API. Do not interpret static product presentation or mock interface elements as live market data.

## Is a database required?
No database schema or persistence layer is established by the tracked tree. For small permitted experiments, local files may be enough. Add a database only when a real query, concurrency, or access-control requirement justifies it.

## Why can a notebook return no reviews?
The source page may have changed, the selected product may have no visible reviews, a request may have failed, or access may be restricted. Inspect the response and selector assumptions. Stop if access is denied; do not try to evade restrictions.

## Can star ratings be used as sentiment labels?
They can be explored as proxy labels, but they are not equivalent to human-annotated sentiment. A review may contain mixed opinions, sarcasm, or comments about delivery and service rather than the product itself.

## What should be committed to Git?
Commit code, documentation, small synthetic fixtures, and approved non-sensitive examples. Do not commit credentials, cookies, private review data, large unreviewed exports, or local notebook checkpoints.

## How should results be reported?
Include sample size, source, collection period, language coverage, preprocessing method, label provenance, baseline, metrics, and limitations. Never publish percentages without denominators.

## How do I contribute?
Read [CONTRIBUTING.md](../CONTRIBUTING.md), open a focused issue where useful, and submit a pull request with reproducible validation steps. Never include personal data or secrets in issue attachments.
