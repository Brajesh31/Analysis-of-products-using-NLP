# 🔐 Security policy

## 1. Scope

This policy covers the repository, its notebooks, static frontend, documentation, and any future data-processing components. Security includes more than software vulnerabilities: notebook outputs, cookies, raw review data, and accidentally committed credentials can expose people or systems.

## 2. Supported project surface

The current tracked project includes two exploratory Jupyter notebooks and a static HTML/CSS frontend. No production backend, API, or database is established by the inspected tree. Do not assume there is a server endpoint or a credential-management service to report against.

## 3. Sensitive material

Treat the following as sensitive:
- API keys, passwords, access tokens, and private keys;
- cookies, browser storage, request authorization headers, and session identifiers;
- private or restricted page content;
- reviewer names, profile URLs, precise locations, and contact information;
- raw datasets whose collection or publication rights are unclear;
- logs or notebook outputs that contain any of the above.

Do not commit these materials. Use local environment variables or a managed secret store for any future integration. Keep `.env` files out of Git and use `.env.example` only for placeholder variable names and explanations.

## 4. Safe collection requirements

Review current source terms and applicable requirements before collecting. Use only authorized access methods. Never bypass CAPTCHAs, authentication, paywalls, rate limits, or technical controls. Do not use another person's cookies or credentials. Stop when the source denies access or indicates that collection is restricted.

Collect the minimum fields required for product feedback analysis. Reviewer identity is not required for sentiment or aspect analysis and should not be extracted.

## 5. Reporting a vulnerability or exposure

Do not create a public issue containing an exploit, secret, cookie, personal information, or private source response. Use GitHub's private vulnerability reporting feature if it is enabled for this repository. Otherwise contact the repository maintainer privately through GitHub at [@Brajesh31](https://github.com/Brajesh31).

Include:
- affected file, workflow, or component;
- a concise impact description;
- reproduction steps using synthetic or redacted values;
- the commit or branch where the issue occurs;
- suggested mitigation, if known.

Never include the actual secret or private data in the report.

## 6. Response expectations

The maintainer will assess severity, reproducibility, and impact, then coordinate a fix. Do not assume a fixed response-time guarantee. Avoid public disclosure until a fix or mitigation is available and coordinated.

## 7. If a secret is committed

1. Revoke or rotate the credential immediately.
2. Disable affected integrations if necessary.
3. Identify the commits, branches, releases, logs, and artefacts containing it.
4. Remove the secret from current files and clean history where appropriate.
5. Check whether the credential was used.
6. Review copies, caches, and backups.
7. Document the incident without reproducing the secret.

Deleting a line in the latest commit is not sufficient because Git history may still contain it.

## 8. Data incident response

If reviewer information or restricted data is exposed, restrict access, identify affected copies, stop further publication, assess deletion and notification obligations, and record corrective actions. Do not repost the exposed content while discussing the incident.

## 9. Security review checklist

- [ ] No credentials or cookies in source files or notebooks.
- [ ] No reviewer identities or unnecessary personal data in outputs.
- [ ] No unapproved datasets committed.
- [ ] No access-control bypass or evasion logic.
- [ ] Dependencies and workflow permissions are justified.
- [ ] Logs contain operational context only.
