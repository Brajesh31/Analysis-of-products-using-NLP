# 🏛️ Project governance

## 1. Project stewardship

The repository is maintained by Brajesh Kumar. The maintainer is responsible for project direction, repository settings, review decisions, release coordination, and the final decision on changes merged to the default branch.

## 2. Decision principles

Project decisions should prioritize:
1. lawful and responsible data access;
2. data correctness and reproducibility;
3. maintainability and simplicity;
4. accessibility and usability;
5. transparent communication of uncertainty;
6. measured need before adding infrastructure.

A new library, database, model, or service should solve a demonstrated problem. Technology count is not a quality metric.

## 3. Contribution pathway

Small documentation fixes and reproducible defects may be submitted directly as pull requests. Changes that affect collection behaviour, schema, data retention, model methodology, or public interfaces should begin with an issue describing the problem and acceptance criteria.

## 4. Review expectations

A contribution may be asked to change when it:
- captures unrelated page content or personal information;
- bypasses source restrictions;
- lacks reproducible validation;
- introduces an undocumented dependency;
- claims functionality or model quality that is not present;
- creates unnecessary operational complexity;
- breaks existing file paths without a migration plan.

## 5. Releases

A release should identify user-visible changes, compatibility requirements, methodology or schema changes, validation performed, and known limitations. Analytical releases require data provenance and evaluation evidence.

## 6. Conflict and escalation

If a technical disagreement remains unresolved, contributors should state the alternatives, evidence, risks, and maintenance cost. The maintainer makes the final repository decision and should document consequential decisions in an architecture decision record.

## 7. Governance updates

This policy may evolve as the project gains contributors or operational responsibilities. Changes should be committed with a clear explanation and reflected in contributor documentation.
