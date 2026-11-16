# 📓 Collection notebook guide

## 1. Purpose and current scope

The repository contains two platform-specific Jupyter notebooks:
- `Web Scraping – Flipkart Customer Reviews.ipynb`
- `Web Scraping – Myntra Customer Reviews.ipynb`

Both use Requests and BeautifulSoup to inspect a single product-page response. They are exploratory examples, not a general-purpose crawler, production ingestion service, or guarantee that the source platform will continue to expose the same HTML.

The notebooks were revised to document the collection assumptions, use explicit request timeouts, validate HTTP responses, target review-body elements, avoid extracting reviewer identity fields, and keep local CSV export disabled by default. These improvements do not prove that the selectors work against the current live pages. They still require verification in a permitted environment.

## 2. Flipkart notebook: current behaviour

The current notebook:
- imports Requests and BeautifulSoup;
- retains the original Oppo F19 product page as an editable example URL;
- sets a 15-second request timeout;
- stops on HTTP 401, 403, and 429;
- validates the response status and HTML content type;
- uses the candidate selector `div.ZmyHeo` for review-body text;
- stores source platform, product reference, retrieval time, and raw review text in memory;
- prints counts and text lengths rather than printing full review content;
- offers an optional local CSV export, disabled by default.

The previous notebook version used a broad `div.row` selector. That captured unrelated product-page content and reviewer names/location strings in saved output. The revised notebook clears the old output and narrows the extraction target. Do not restore the broad selector or republish the old output.

## 3. Myntra notebook: current behaviour

The current notebook:
- imports Requests and BeautifulSoup;
- retains the original Sassafras product page as an editable example URL;
- sets a 15-second request timeout;
- stops on HTTP 401, 403, and 429;
- validates the response status and HTML content type;
- uses the candidate selector `#user-review-reviewTextWrapper`;
- stores source platform, product reference, retrieval time, and raw review text in memory;
- prints counts and text lengths rather than full review content;
- offers an optional local CSV export, disabled by default.

The selector is a hypothesis based on the original notebook's review-text wrapper reference. It may no longer exist or may return a different structure.

## 4. Safe execution expectations

Before executing a request:
1. Review current platform terms, robots directives, API policies, and applicable requirements.
2. Confirm that the method and purpose are permitted.
3. Use a product URL you are authorized to access.
4. Run the notebook from a fresh kernel.
5. Stop on access denial, throttling, or an unexpected response.
6. Do not bypass login, CAPTCHA, paywall, or technical restrictions.
7. Do not use cookies, browser profiles, or session tokens from another user.

The notebook does not retry failed requests. This is intentional. A denied request should not trigger repeated attempts or evasion.

## 5. Selector verification

A selector returning no elements may mean the page changed, reviews are not present in the returned HTML, the content is loaded dynamically, or the request did not return the expected product page. Inspect only a small permitted sample of the markup.

If the selector needs changing:
- identify the narrowest review-body element;
- exclude parent containers that contain reviewer identity, location, report links, navigation, and product information;
- document the new selector and the date it was verified;
- add a synthetic HTML fixture for the expected structure;
- add a parser test for valid and malformed markup.

Never replace a failed selector with a page-wide selector merely to make the notebook return data.

## 6. Data contract

Each extracted record currently contains:
- `source_platform`;
- `product_reference`;
- `retrieved_at`;
- `review_text_raw`.

This is a minimal exploratory record, not yet the complete shared schema described in [Data and schema](data-and-schema.md). Ratings, stable source review IDs, language metadata, collection run IDs, and parser versions are not currently extracted by these notebooks.

## 7. Export and retention

CSV export is disabled by default. If export is enabled, it writes to `data/exports/`, which is ignored by Git. Enable export only after confirming that retaining the review text is permitted and necessary. Do not commit the resulting files without reviewing rights, privacy, and retention requirements.

## 8. What these notebooks do not do

They do not implement pagination, dynamic browser interaction, a scheduler, retry/backoff, a common data validation package, sentiment classification, topic modelling, model evaluation, or product ranking. Do not claim those capabilities.

## 9. Reproducibility checklist

- [ ] Python and package versions recorded.
- [ ] Product URL and source platform recorded.
- [ ] Collection method and purpose permitted.
- [ ] Selector verified against current permitted markup.
- [ ] Notebook executed from a fresh kernel.
- [ ] HTTP status and content type checked.
- [ ] Extracted text inspected privately for relevance and personal data.
- [ ] Output cells contain no raw personal data or secrets.
- [ ] Local exports remain outside public Git unless explicitly approved.
