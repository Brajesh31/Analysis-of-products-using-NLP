# Troubleshooting

## Notebook returns no reviews

Retailer HTML and selectors change. Inspect the current permitted page, verify the selector, check consent or bot interstitials, and stop rather than attempting to bypass controls.

## Requests fail

Check URL validity, network access, timeouts, status codes, terms, and rate limits. Use a small authorized sample and backoff rather than repeated rapid requests.

## Frontend assets are missing

Serve the `Frontend/` directory over HTTP and verify case-sensitive relative paths such as `assets/Mainimg.png`. Check browser developer tools for 404s.
