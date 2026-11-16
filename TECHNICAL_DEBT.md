# 🧱 Technical debt and improvement register

This register tracks gaps that affect reproducibility, safety, or maintainability. Items are based on the inspected repository and should be updated when evidence changes. It is not a list of imaginary defects or a claim that proposed modules already exist.

## Verified gaps and follow-up work

| Area | Current observation | Risk | Recommended next action |
|---|---|---|---|
| Flipkart notebook | Now uses a narrow candidate selector and explicit request validation; selector is not live-verified | It may stop matching or capture unexpected text | Verify permitted markup and add synthetic fixtures |
| Myntra notebook | Now uses a review-text candidate selector and explicit request validation; selector is not live-verified | Page changes may break extraction | Verify permitted markup and add synthetic fixtures |
| Pagination | Both notebooks inspect a single page response | Results may be incomplete | Determine whether pagination is permitted and required before implementing |
| Shared schema | Notebook records contain only a minimal common subset | Source outputs may diverge as fields grow | Define and validate a versioned schema |
| Dependency reproducibility | No pinned dependency manifest is present in the inspected tree | Fresh setup may differ | Test a clean environment and record compatible versions |
| Parser tests | CI validates notebook structure and Markdown; no parser fixture suite is established | Markup changes may go unnoticed | Add synthetic HTML fixtures and mocked request tests |
| NLP evaluation | No model benchmark report is established by the tree | Quality claims cannot be assessed | Define task, labels, baseline, split, and metrics before modelling |
| Frontend integration | Static pages exist without verified API integration | Mock controls may be mistaken for live features | Keep status explicit and decide whether integration is needed |
| Data governance | Retention and publication controls need project-specific decisions | Privacy and compliance risk | Document retention, deletion, and approved publication policy |

## Prioritization

1. Verify both selectors using permitted current page structures.
2. Add deterministic parser tests with synthetic fixtures.
3. Establish schema, provenance, and validation.
4. Add a tested dependency manifest.
5. Build exploratory analysis only after data quality is measurable.
6. Evaluate NLP methods only after label provenance and a leakage-resistant split are established.
7. Consider backend and database infrastructure only when a real product requirement exists.

## Completion criteria

Close an item only when the code or policy change is committed, relevant tests or review evidence exist, documentation is updated, and known limitations are stated.
