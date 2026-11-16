# 🔭 Future scope and phased engineering plan

This roadmap expands the current exploratory repository in a sequence that prioritizes correctness, permission, and reproducibility. Every item below is proposed work until the corresponding code and evidence are committed.

## Phase 1: Make the existing notebooks safe and reproducible

- Add clear Markdown introductions and execution instructions to both notebooks.
- Use explicit timeouts and HTTP status handling.
- Narrow selectors to review-body content and avoid reviewer identity fields.
- Clear saved outputs containing names, locations, or raw page dumps.
- Record source URL, collection date, parser assumptions, and run outcome.
- Add a tested dependency manifest only after validating package versions.
- Add synthetic HTML fixtures for parser regression tests.

**Exit criteria:** notebooks open from a clean environment, have no secrets or sensitive outputs, and fail visibly when the page structure is unexpected.

## Phase 2: Establish a shared data contract

- Define required and optional fields.
- Keep raw and normalized text separate.
- Standardize timestamps and rating-scale metadata.
- Add validation and rejection reasons.
- Define deduplication rules and limitations.
- Store a run manifest with parser version and record counts.

**Exit criteria:** both source adapters produce records that pass the same schema checks without discarding platform provenance.

## Phase 3: Build an exploratory analysis layer

- Add review-count, missingness, duplicate, and language summaries.
- Analyze review length and rating distributions.
- Explore term and n-gram frequency.
- Document sample selection and collection windows.
- Generate charts with denominators and source context.

**Exit criteria:** exploratory reports can be regenerated from a documented dataset snapshot and do not expose reviewer identities.

## Phase 4: Evaluate NLP methods

- Define sentiment or aspect-analysis tasks precisely.
- Establish label provenance and annotation guidance.
- Build majority and transparent lexical/TF-IDF baselines.
- Use grouped or time-based splits where appropriate.
- Report class-wise metrics and error analysis.
- Add language-specific limitations and a model card.

**Exit criteria:** performance claims are supported by a held-out evaluation and reproducible configuration.

## Phase 5: Improve the product interface

- Audit current static pages for accessibility and responsive behaviour.
- Decide whether a backend is genuinely needed.
- Define an API contract only after analysis outputs are stable.
- Add loading, empty, stale, and error states.
- Display source, sample size, and analysis date with every insight.

**Exit criteria:** the interface only presents real validated data and communicates uncertainty clearly.

## Phase 6: Operational maturity

- Add CI for deterministic notebook and documentation checks.
- Add versioned releases and a changelog.
- Define retention and deletion procedures.
- Add monitoring only if an authorized scheduled pipeline exists.
- Document rollback, incident response, and maintenance ownership.

## Prioritization rule

Do not start with a complex transformer model, database, or dashboard just because those technologies look impressive. Fix collection correctness, data provenance, and reproducibility first. A polished UI cannot rescue a dataset that is biased, malformed, or collected without permission.
