# 🚀 Deployment and distribution guide

## 1. What can currently be deployed

The tracked project includes static HTML, CSS, and local visual assets under `Frontend/`. These files can be hosted by a static web server without introducing a backend or a build system. The tracked repository does not establish a production API, database, scheduled collection service, or deployed NLP inference endpoint.

Jupyter notebooks are research artefacts. They should not be treated as production crawlers or scheduled jobs without a separate review of authorization, reliability, monitoring, and data retention.

## 2. Local preview

From the repository root:

```bash
python -m http.server 8000 --directory Frontend
```

Open `http://localhost:8000/` and check both the home and listing pages. Serving the directory over HTTP helps reveal relative-path and browser behaviour that may differ from opening an HTML file directly.

## 3. Static hosting procedure

1. Choose a static host that supports HTTPS and custom domains if needed.
2. Configure the publish directory to the contents of `Frontend/`, not the repository root, unless the host is explicitly configured for that layout.
3. Preserve the `assets/` directory and the exact case of every filename.
4. Verify that `index.html`, `listing.html`, stylesheets, images, and SVG files return successfully.
5. Check mobile and desktop layouts.
6. Inspect the browser console and network panel for failed requests.
7. Confirm that external font, icon, or script resources are intentionally used and available.
8. Review the published page for accidental personal data or misleading live-data claims.

## 4. Notebook distribution

For reproducible notebook execution, document Python and package versions, input provenance, collection dates, notebook revision, and expected outputs. Do not publish authentication cookies, browser profiles, private retailer responses, or raw user-generated data without a lawful basis and permission.

A notebook should be executed manually against a small permitted sample before anyone considers automation. Do not schedule a collector merely because a notebook can be run in CI.

## 5. Future service deployment

A future backend or analysis service would need its own deployment guide covering runtime, dependency locking, environment configuration, health checks, logs, secret rotation, database migrations, request limits, and rollback. A model-serving endpoint would additionally require model artefact versioning, resource limits, latency measurement, and input validation.

## 6. Release checklist

- [ ] The deployed commit is the intended commit.
- [ ] Static pages and all local assets load successfully.
- [ ] HTTPS is enabled.
- [ ] Responsive behaviour and keyboard navigation are checked.
- [ ] No secrets, cookies, private datasets, or unapproved review excerpts are published.
- [ ] Product claims have a visible source and freshness context.
- [ ] The deployment does not imply an API or model that is not present.
- [ ] Known limitations are recorded.
- [ ] A rollback target is identified.

## 7. Rollback

For a static-site defect, redeploy the last known-good commit and verify the published asset paths. If a credential or private dataset was exposed, rollback alone is insufficient: revoke credentials, restrict access, investigate copies, and follow the security incident process.
