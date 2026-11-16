# 🧾 Review data contract, schema, and quality rules

## 1. Purpose

The two source platforms may expose different page structures and metadata. A common schema makes downstream analysis easier, but it must not erase meaningful source differences. The schema below is a proposed contract. It is not a claim that the existing notebooks already emit all fields.

## 2. Recommended record schema

| Field | Type | Required | Meaning and validation |
|---|---|---:|---|
| `review_id` | string | Preferred | Stable source ID or documented local key |
| `source_platform` | enum/string | Yes | Platform identifier, such as Flipkart or Myntra |
| `product_reference` | string | Yes | Product URL or non-sensitive product key |
| `retrieved_at` | ISO-8601 timestamp | Yes | UTC time the record was collected |
| `review_text_raw` | string | Preferred | Original review text, preserved unchanged |
| `review_text_clean` | string | No | Derived normalized text |
| `rating_value` | number/null | No | Numeric rating in the source scale |
| `rating_scale_max` | number/null | No | Maximum rating value for interpretation |
| `language` | string/null | No | Detected language when confidence is adequate |
| `collection_run_id` | string | Yes | Identifier for the run that produced the record |
| `parser_version` | string | Yes | Version or revision of the extraction logic |
| `record_hash` | string | No | Deterministic hash for duplicate detection |
| `validation_status` | enum | Yes | accepted, rejected, or needs_review |
| `validation_notes` | string/list | No | Non-sensitive reason for review or rejection |

Avoid adding reviewer names, profile URLs, contact details, precise locations, or other personal identifiers. They are not required to analyze product feedback.

## 3. Synthetic example

```json
{
  "review_id": "synthetic-review-0001",
  "source_platform": "example-platform",
  "product_reference": "demo-product-01",
  "retrieved_at": "2026-01-01T00:00:00Z",
  "review_text_raw": "The battery lasted through my workday.",
  "review_text_clean": "battery lasted workday",
  "rating_value": 4,
  "rating_scale_max": 5,
  "language": "en",
  "collection_run_id": "demo-run-001",
  "parser_version": "example-parser-v1",
  "record_hash": "synthetic-hash",
  "validation_status": "accepted"
}
```

This record is synthetic and must never be presented as a real customer review.

## 4. Raw versus derived data

Never overwrite raw text with a cleaned version. Keep each transformation in a separate column or derived dataset. A preprocessing change can alter tokenization, sentiment, or topics; retaining raw text allows a later method to be evaluated fairly.

Recommended fields for derived analysis include:
- normalized text;
- detected language and confidence;
- token list or feature representation, where useful;
- sentiment label and label source;
- model or lexicon version;
- prediction confidence, when meaningful;
- analysis timestamp.

Do not store large embeddings or model outputs unless a concrete analysis use case justifies their storage.

## 5. Validation rules

- Required source and product fields must be present.
- Text must not be empty after boilerplate removal unless metadata-only records are explicitly supported.
- Rating must fall within the source's documented scale.
- Missing rating must remain null.
- Dates must parse consistently and include timezone context.
- Duplicate IDs must be handled deterministically.
- Unexpected source markup must trigger a visible parser warning.
- Text encoding must be valid UTF-8 or explicitly converted with a documented policy.

## 6. Deduplication strategy

Prefer stable source review identifiers. If unavailable, create a deterministic hash from normalized review text, product key, source, and any non-personal metadata needed to distinguish records. Document the trade-off: two different customers may write identical short text, so hash-only deduplication can incorrectly collapse legitimate reviews.

## 7. Dataset partitioning

When training models, split data before fitting vectorizers or other learned preprocessing. Keep duplicate and near-duplicate records in the same split. Consider grouping by product or collection period when the goal is generalization to unseen products or future reviews.

## 8. Proposed local data layout

```text
data/
├── samples/       # synthetic, tiny test fixtures
├── raw/           # restricted local source extracts, if permitted
├── processed/     # normalized records and validation outputs
└── metadata/      # run manifests, dictionaries, and schema versions
```

Do not commit raw or processed review datasets by default. Only publish a dataset after confirming rights, licensing, privacy, and reproducibility requirements.
