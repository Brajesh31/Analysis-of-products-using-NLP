# 📓 Collection notebook guide

## 1. Purpose of the notebooks

The repository contains two separate Jupyter notebooks:
- `Web Scraping – Flipkart Customer Reviews.ipynb`
- `Web Scraping – Myntra Customer Reviews.ipynb`

Both are exploratory examples using Requests and BeautifulSoup. They are not a general-purpose crawler, a production ingestion service, or a guarantee that the current platform page will remain parseable.

## 2. Important findings in the current notebook code

The Flipkart notebook currently:
- imports BeautifulSoup and Requests;
- uses a hard-coded product URL;
- calls `requests.get` without an explicit timeout;
- does not check the HTTP status before parsing;
- selects every `div` with class `row`, a broad selector that may capture unrelated page content;
- saves output containing reviewer names and location strings.

The Myntra notebook currently:
- imports BeautifulSoup and Requests;
- uses a hard-coded product URL;
- calls `requests.get` without an explicit timeout or status validation;
- selects a platform-specific review container;
- extracts the full container text rather than a formally validated common schema.

These are concrete limitations to address. Do not assume the existing selectors are still correct or that the returned content is safe to publish.

## 3. Safe execution expectations

Before execution, review the source platform's current terms and confirm the method is permitted. Use a small sample. A revised notebook should use an explicit timeout, validate the response, inspect content type, and stop on access denial or throttling. It must not attempt to bypass a CAPTCHA or other technical restriction.

## 4. Selector verification

Inspect only a small, permitted portion of the returned page. Identify the element that contains the review body and avoid parent containers that include reviewer names, locations, report links, navigation, product details, or other page chrome.

A selector change should be accompanied by a synthetic HTML fixture and a parser test. Do not use a live website as the only test fixture.

## 5. Recommended notebook sections

1. Title, research question, source, and collection date.
2. Responsible collection notice and stop conditions.
3. Environment and dependency information.
4. Product URL and non-secret configuration.
5. Request and response validation.
6. Page parsing and selector diagnostics.
7. Review-body extraction.
8. Record schema and validation.
9. Duplicate and missingness checks.
10. Sanitized exploratory output.
11. Export instructions for approved local data.
12. Limitations and next steps.

## 6. Output hygiene

The saved output of a notebook is part of the committed file. Clear outputs that contain reviewer identities, location information, raw HTML, cookies, headers, or large record dumps. Keep only synthetic examples or aggregate diagnostics that are safe to publish.

## 7. Reproducibility

Record Python and dependency versions, collection timestamp, source page, parser version, number of records inspected, number accepted, number rejected, and reason categories. A notebook should run from a fresh kernel in top-to-bottom order. Avoid hidden state and manually edited output cells.
