# ✅ Repository quality and completion checklist

This checklist is a practical acceptance standard for changes to this repository. It deliberately distinguishes file presence from working functionality. A repository is not complete merely because it contains many Markdown documents.

## Repository and documentation

- [ ] Root README explains the actual project, current features, setup, limitations, and contribution route.
- [ ] Repository structure matches the tracked tree.
- [ ] Documentation index links to every maintained guide.
- [ ] Relative Markdown links resolve.
- [ ] Mermaid diagrams render and distinguish current components from proposed components.
- [ ] Examples are executable or clearly labelled illustrative.
- [ ] No unsupported performance, dataset-size, model-accuracy, or production-readiness claims exist.
- [ ] Changelog entries correspond to actual changes.
- [ ] License and citation metadata are accurate.

## Notebook and data quality

- [ ] Notebook JSON parses and cell IDs are unique.
- [ ] Notebooks have clear purpose, prerequisites, and execution order.
- [ ] Network requests have timeouts and explicit response validation.
- [ ] Access-denied and rate-limited responses stop collection.
- [ ] Selectors are checked against currently permitted markup.
- [ ] No access-control bypass or anti-bot evasion is present.
- [ ] Reviewer identity and unnecessary personal data are excluded.
- [ ] Data schema and provenance are documented.
- [ ] Raw data is not overwritten by cleaned or transformed data.
- [ ] Private datasets and sensitive notebook outputs are excluded from Git.
- [ ] Any analytical conclusion reports sample size, method, uncertainty, and limitations.

## Frontend quality

- [ ] Both static pages load locally.
- [ ] All referenced assets exist with exact filename case.
- [ ] No console errors or broken network requests remain.
- [ ] Layout works at mobile, tablet, and desktop widths.
- [ ] Keyboard navigation and visible focus are supported.
- [ ] Images have appropriate alternative text.
- [ ] Controls are functional or explicitly identified as prototypes.
- [ ] Product and sentiment claims match implemented behaviour.

## Automation and security

- [ ] Quality workflow runs successfully on a representative change.
- [ ] Workflow permissions are least-privilege.
- [ ] Third-party actions and dependencies are reviewed.
- [ ] No credentials, cookies, tokens, or private data are committed.
- [ ] Issue and pull-request templates collect reproducible, sanitized information.
- [ ] Vulnerability reports use the private reporting route where available.

## Release readiness

- [ ] Changes are reviewed against the roadmap and technical-debt register.
- [ ] Setup instructions have been followed in a clean environment.
- [ ] Known limitations and breaking changes are documented.
- [ ] Screenshots, if included, show the actual current interface.
- [ ] A release is not described as production-ready without integration, security, and operational evidence.

## Current project status

The current repository contains two exploratory review-collection notebooks and a static HTML/CSS frontend prototype, with supporting documentation and GitHub templates/workflows. The presence of this checklist does not mean that a production NLP pipeline, sentiment model, API, database, or automated deployment exists.
