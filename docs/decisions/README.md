# 🧠 Architecture decision records

Architecture decision records (ADRs) capture consequential technical choices so future contributors understand not only what was selected, but why.

## When to write an ADR

Create an ADR for decisions that materially affect:
- collection method or platform access;
- shared review schema and identifiers;
- storage format or database selection;
- preprocessing and language support;
- sentiment label provenance;
- model family and evaluation strategy;
- frontend/backend integration;
- data retention and deletion;
- CI or deployment architecture.

Routine typo fixes and isolated documentation edits do not need an ADR.

## Required sections

Each record should include:
1. Title and status.
2. Date and decision owner.
3. Context and problem.
4. Constraints and requirements.
5. Options considered.
6. Decision and rationale.
7. Consequences and trade-offs.
8. Validation or evidence.
9. Follow-up actions.

## Status values

Use Proposed, Accepted, Rejected, Superseded, or Deprecated. When a decision changes, create a new ADR and link the previous record rather than silently rewriting history.

## Template

Use [the ADR template](../templates/architecture-decision-record.md).
