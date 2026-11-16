# 🧭 Project roadmap

This roadmap is an ordered plan, not a statement that the listed features already exist. Work should be completed in dependency order. Reproducible data collection and evaluation are more important than adding fashionable infrastructure.

## Status legend

- **Planned:** not yet implemented.
- **In progress:** actively being worked on and tracked by an issue or pull request.
- **Completed:** code and validation evidence are present in the repository.

Items should move to Completed only when the implementation, documentation, and tests are committed.

## Phase 1: Notebook reliability

- [ ] Add clear notebook introductions and collection assumptions.
- [ ] Use explicit timeouts and HTTP response validation.
- [ ] Replace broad selectors with verified review-body selectors.
- [ ] Avoid reviewer identity and location fields.
- [ ] Clear saved outputs that expose personal details.
- [ ] Add parser diagnostics and safe stop conditions.
- [ ] Record a tested Python and package environment.

**Acceptance:** notebooks open from a clean kernel, do not contain secrets or sensitive outputs, and fail visibly when a source page changes.

## Phase 2: Shared data contract

- [ ] Define a versioned review record schema.
- [ ] Keep raw and normalized text separate.
- [ ] Standardize source, product, retrieval time, and rating metadata.
- [ ] Add missingness, duplicate, and malformed-record reporting.
- [ ] Add a collection-run manifest.

**Acceptance:** each platform adapter produces records that pass common validation without erasing source provenance.

## Phase 3: Exploratory analysis

- [ ] Add review volume and rating summaries.
- [ ] Report language and missingness coverage.
- [ ] Explore terms and n-grams with documented preprocessing.
- [ ] Compare product samples only when coverage is comparable.
- [ ] Generate accessible visualizations with denominators and dates.

**Acceptance:** reports are reproducible from a documented dataset snapshot and do not expose reviewer identity.

## Phase 4: NLP evaluation

- [ ] Define sentiment or aspect-analysis task.
- [ ] Document label provenance and annotation policy.
- [ ] Implement a transparent baseline.
- [ ] Choose a leakage-resistant split strategy.
- [ ] Report per-class metrics, confusion matrix, and error analysis.
- [ ] Document model limitations and supported languages.

**Acceptance:** all model claims are supported by held-out evaluation evidence and a reproducible configuration.

## Phase 5: Frontend improvement

- [ ] Audit current static pages for semantic HTML and accessibility.
- [ ] Improve responsive behaviour and keyboard interaction.
- [ ] Decide whether a backend is actually required.
- [ ] Define API contracts only after analysis outputs are stable.
- [ ] Display source, sample size, collection window, and method with insights.

**Acceptance:** the interface displays only real validated data and communicates uncertainty.

## Phase 6: Operational maturity

- [ ] Add deterministic CI checks for notebooks and documentation.
- [ ] Add versioned release notes.
- [ ] Define data retention and deletion procedures.
- [ ] Add monitoring only if an authorized scheduled pipeline exists.
- [ ] Document rollback and incident response.

## Prioritization

Do not begin with a large transformer, database, or dashboard simply to increase the technology list. First make the source data valid, the collection permitted, and the analysis reproducible. A sophisticated interface cannot compensate for a weak dataset.
