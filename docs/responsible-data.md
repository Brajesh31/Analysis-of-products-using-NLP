# 🔐 Responsible data collection, privacy, and platform compliance

## 1. Core principle

A review being visible in a browser does not automatically mean it can be collected, stored indefinitely, republished, or used to profile its author. The project must evaluate platform terms, applicable law, privacy expectations, and the proposed use before collecting data.

This guide is an engineering safeguard, not legal advice. If a planned use is commercially significant or involves large-scale processing, obtain appropriate legal review.

## 2. Pre-collection review

Before running a notebook:
1. Identify the source platform and exact product page.
2. Read the platform's current terms, robots directives, API policies, and applicable law.
3. Confirm that the method and purpose are permitted.
4. Prefer official documented interfaces where they are available and authorized.
5. Define the smallest set of fields needed for the research question.
6. Decide where data will be stored, who can access it, and when it will be deleted.
7. Establish a conservative request rate and stop conditions.

Do not assume that a previous successful request establishes current permission.

## 3. Prohibited collection behaviour

Do not:
- bypass login requirements, CAPTCHAs, paywalls, access controls, or rate limits;
- rotate identities, proxies, or user agents to evade enforcement;
- use another person's session cookies or browser profile;
- collect private or restricted content;
- harvest reviewer names, contact information, profile URLs, or precise locations;
- infer sensitive personal characteristics from review text;
- republish raw user-generated content without a lawful basis and permission.

If a platform denies access or signals that collection is restricted, stop. Do not attempt to defeat the restriction.

## 4. Data minimization

For product-feedback analysis, the required information is usually product context, review text, rating when available, source platform, and retrieval timestamp. Reviewer identity is not necessary to determine whether customers discuss battery life, fit, durability, or delivery.

Remove unrelated page text and metadata as early as possible. Avoid retaining request headers, cookies, session identifiers, or full HTML pages unless there is a specific permitted debugging need and an appropriate retention control.

## 5. Personal data in notebook outputs

The existing Flipkart notebook output contains reviewer-related names and location strings because the broad selector captures more than review body text. Treat these outputs as sensitive. Do not copy them into documentation, screenshots, fixtures, or public reports. A revised notebook should extract only the review body and any minimal non-identifying metadata required for analysis.

Before committing a notebook:
- inspect every saved output cell;
- clear raw page dumps and reviewer metadata;
- search for tokens, cookies, email addresses, phone numbers, and session values;
- verify that the notebook JSON does not retain hidden output data.

## 6. Retention and deletion

Document the source, purpose, retention period, storage location, and deletion procedure for every dataset. Delete raw and derived copies when the permitted retention period ends or when a valid deletion requirement applies. Include local backups and exported analysis files in the deletion plan.

## 7. Publication and visualizations

Prefer aggregate statistics. Include sample size and collection date. Avoid long verbatim review excerpts unless publication is authorized. Small groups, rare phrases, and combinations of product/date/metadata may identify a reviewer even after a name is removed.

## 8. Credentials and secrets

Never commit API keys, passwords, cookies, browser storage, or access tokens. Use local environment variables or a managed secret store. If a secret is exposed, revoke or rotate it immediately and review Git history and copies.

## 9. Incident response

If private data or credentials are exposed:
1. Stop further publication or collection.
2. Revoke or rotate affected credentials.
3. Restrict access to exposed data.
4. Identify affected commits, artefacts, and copies.
5. Assess notification and deletion obligations.
6. Record the incident and corrective action without reproducing the secret.

Report security concerns through [SECURITY.md](../SECURITY.md), not a public issue.
