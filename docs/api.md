# 🔌 API reference and integration status

## 1. Current implementation status

The tracked repository currently contains a static HTML/CSS frontend and two Jupyter notebooks for platform-specific review collection. The repository tree does not show a backend application, route handlers, an OpenAPI document, or an API test suite. The search and navigation elements in the frontend should therefore be understood as interface elements, not proof of live search, price discovery, user accounts, notifications, or NLP inference.

This distinction matters. Documentation must not publish endpoint URLs that do not exist, and frontend code must not silently depend on a future API contract.

## 2. Possible future API boundary

If a backend is introduced after the review-analysis workflow becomes reproducible, keep the first interface read-only and aggregate-oriented. A product insight response should include its data window, source coverage, sample size, analysis version, and caveats.

| Proposed endpoint | Intended responsibility | Current status |
|---|---|---|
| `GET /api/health` | Report service readiness and version | Not implemented |
| `GET /api/products` | Return products available in the approved analysis catalogue | Not implemented |
| `GET /api/products/{product_id}/summary` | Return aggregate review counts and rating distribution | Not implemented |
| `GET /api/products/{product_id}/sentiment` | Return validated sentiment counts and proportions | Not implemented |
| `GET /api/products/{product_id}/aspects` | Return aspect-level summaries and sample sizes | Not implemented |
| `GET /api/analysis-runs/{run_id}` | Return provenance and processing metadata | Not implemented |

These routes are design examples only. Do not build a frontend integration against them until a server implementation, schema, and tests are committed.

## 3. Contract design

A future response should be explicit about units and nullability. For example, a percentage must include the denominator and should not conceal a small sample. A sentiment result should identify whether labels were human annotated, rating-derived proxies, lexicon outputs, or model predictions.

A useful aggregate response may contain:
- stable product and source identifiers that do not expose reviewer identities;
- collection start and end timestamps;
- number of records inspected, accepted, excluded, and analysed;
- missing-value and duplicate rates;
- preprocessing and model version identifiers;
- counts by label, with the denominator;
- a clear statement of the label source;
- confidence or uncertainty information where statistically justified.

## 4. Reliability and security requirements

If an API is added:
1. Validate path parameters, filters, sort keys, and pagination limits.
2. Use stable response schemas and documented error codes.
3. Apply authentication and authorization to restricted operations.
4. Rate-limit expensive analysis requests.
5. Set request and upstream timeouts.
6. Avoid exposing raw review text or personal identifiers by default.
7. Log operational metadata without logging secrets or unnecessary review content.
8. Version breaking changes and publish an OpenAPI specification.
9. Test empty, malformed, unauthorized, and oversized requests.
10. Keep source provenance attached to analytical results.

## 5. Error semantics

Do not return an empty success response when an upstream source failed. Distinguish invalid input, missing product, unavailable analysis, rate limiting, and internal processing failure. A client should be able to tell the difference between “there are no reviews in this approved dataset” and “the data source could not be reached”.

## 6. Frontend integration gate

Before connecting the static pages to a future API, agree on loading, empty, partial, stale, and error states. Display collection dates and sample sizes beside insights. Do not show a confident product verdict when the sample is too small or the analysis method is not validated.

## 7. Change checklist

When the first endpoint is implemented, update this guide with its real method, path, request schema, response example, authentication model, error table, rate limits, and test location. Remove any proposal that was not implemented rather than allowing design sketches to look like shipped functionality.
