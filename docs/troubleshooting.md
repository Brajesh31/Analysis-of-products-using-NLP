# 🧰 Troubleshooting guide

## 1. Notebook fails to import a package

Activate the same virtual environment used to launch Jupyter. Install the missing dependency into that environment and restart the kernel. A common cause is installing a package into one Python interpreter while Jupyter is using another.

Check the active interpreter from a notebook:

```python
import sys
print(sys.executable)
print(sys.version)
```

Do not guess a dependency version. Inspect the imports, test a clean environment, and document the version that worked.

## 2. Notebook returns zero reviews

Possible causes include changed HTML, an empty product review section, pagination behaviour, an HTTP error, a consent page, or access restrictions. Inspect the response status and a small sanitized portion of the page. Confirm the selector still matches the permitted page structure.

Do not treat an empty list as proof that a product has no reviews. Do not bypass login, CAPTCHAs, access controls, or rate limits.

## 3. Request times out or returns an error

Check the source URL, network connection, request timeout, response status, and whether the source permits the request. Use conservative retries only for transient failures and respect any retry guidance. Do not retry aggressively after throttling or access denial.

## 4. Selector matches too much content

A broad class selector may return product descriptions, navigation text, reviewer metadata, and unrelated page sections. Inspect a few returned elements and narrow the selector to the review body only. Avoid collecting reviewer names, locations, profile links, or report controls.

## 5. Duplicate or malformed records

Keep the original record for debugging in a restricted local environment, then add a synthetic regression fixture. Define a stable deduplication key. Validate rating scale, missing text, encoding, and field types before analysis.

## 6. Frontend styles or images are missing

Serve `Frontend/` as the web root. Check case-sensitive paths such as `assets/Mainimg.png`, verify the file exists in the repository, and inspect browser network requests for 404 responses. Preserve the existing assets folder when changing HTML.

## 7. Frontend layout breaks on small screens

Use browser responsive tools and test narrow widths. Look for fixed-width containers, overflowing images, long unbroken text, and navigation elements that cannot wrap. Test keyboard focus after changing layout.

## 8. Notebook output contains sensitive information

Clear the output, inspect saved notebook JSON, and ensure no raw review records, cookies, request headers, tokens, or personal details remain. If a credential was committed, rotate it immediately; deleting the visible cell does not remove it from Git history.

## 9. Still blocked?

Open a focused issue with the file name, operating system, Python/browser version, sanitized error, expected behaviour, actual behaviour, and exact reproduction steps. Never attach credentials, cookies, or private source responses.
