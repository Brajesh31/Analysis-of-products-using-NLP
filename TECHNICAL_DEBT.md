# 🧱 Technical debt and improvement register

This register tracks gaps that affect reproducibility, safety, or maintainability. Items should be updated when evidence changes. It is not a list of imaginary defects or a claim that proposed modules already exist.

## Verified gaps from the tracked project

| Area | Current observation | Risk | Recommended next action |
|---|---|---|---|
| Flipkart notebook | Original broad selector captured unrelated content and reviewer metadata; request lacked timeout/status checks | Incorrect extraction and sensitive output | Use narrow selector, request validation, and clear outputs |
| Myntra notebook | Original request lacked timeout/status checks and extracted a parent container | Stale markup and unrelated text | Target review-body element and validate response |
| Python environment | No pinned dependency manifest in the inspected tree | Fresh setup may differ | Test clean environment and record versions |
| Shared schema | No enforced common record contract | Source outputs may diverge | Define and validate a versioned schema |
| Parser tests | No test suite visible in the inspected tree | Markup changes may go unnoticed | Add synthetic HTML fixtures and mocked responses |
| NLP evaluation | No model benchmark report established by the tree | Quality claims cannot be assessed | Define labels, baseline, split, and metrics before modelling |
| Frontend integration | Static pages exist without verified API integration | Mock controls may be mistaken for live features | Document current status and decide whether integration is needed |
| Data governance | Raw review retention and publication need explicit controls | Privacy and compliance risk | Document minimum fields, retention, and deletion |

## Prioritization

1. Remove personal metadata from notebook outputs.
2. Make collection requests fail safely and visibly.
3. Establish schema and provenance.
4. Add deterministic parser and documentation checks.
5. Evaluate NLP methods only after label and dataset quality are established.
6. Consider backend and database infrastructure only when a real product requirement exists.

## Completion criteria

Close an item only when the code or policy change is committed, relevant tests or review evidence exist, documentation is updated, and known limitations are stated.
