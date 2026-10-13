# Security Policy

## Data and scraping safety

Treat review text, usernames, locations, cookies, request headers, and downloaded pages as potentially sensitive. Do not commit raw personal data or authentication material. Use a dedicated test environment, low request rates, timeouts, and explicit source authorization.

Never bypass CAPTCHAs, access controls, rate limits, paywalls, or privacy settings. Do not reuse production cookies or credentials in notebooks.

## Reporting

Do not publish exposed secrets or personal data in an issue. Report them privately to Brajesh Kumar (`@brajesh31`) with the affected file, impact, reproduction steps, and redacted evidence.
