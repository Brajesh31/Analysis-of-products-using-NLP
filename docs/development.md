# 🛠️ Development and maintenance guide

## 1. Repository areas

The project currently has three practical development surfaces:
- the Flipkart review collection notebook;
- the Myntra review collection notebook;
- the static HTML/CSS frontend and its existing assets.

The documentation describes a future shared data and NLP pipeline, but contributors should not assume those modules already exist. Before adding a new framework, service, or dependency, explain the concrete problem it solves.

## 2. Start with a clean working tree

```bash
git clone https://github.com/Brajesh31/Analysis-of-products-using-NLP.git
cd Analysis-of-products-using-NLP
git status --short
git switch -c feature/describe-your-change
```

Keep each branch focused. Do not combine unrelated notebook rewrites, large visual redesigns, and documentation-only changes into one difficult-to-review patch.

## 3. Notebook engineering standards

- Add a Markdown introduction that states the question, source, date, and assumptions.
- Separate setup, collection, parsing, validation, cleaning, and exploration into understandable sections.
- Keep cells restartable and avoid relying on variables created by hidden earlier execution.
- Set request timeouts and handle non-success HTTP responses explicitly.
- Do not bypass access controls, CAPTCHAs, or rate limits.
- Preserve raw review text separately from normalized text.
- Avoid extracting reviewer names, locations, profile URLs, or unrelated page content.
- Clear outputs that expose personal data, credentials, or large raw extracts.
- Record package versions after testing a clean environment.
- Use synthetic fixtures for parser regression tests.

## 4. Frontend engineering standards

Preserve the existing static HTML/CSS structure unless a deliberate refactor is part of the issue. Keep local image and stylesheet paths correct, use semantic elements, maintain a logical heading order, provide meaningful alt text, and test keyboard navigation. Do not label mock interactions as connected live functionality.

## 5. Change proposal and implementation

For a substantial change, describe:
1. The user or developer problem.
2. Existing behaviour and why it is insufficient.
3. The proposed approach and alternatives.
4. Files and interfaces affected.
5. Data protection and platform-policy implications.
6. Validation and rollback strategy.

Avoid adding a dependency for a task that can be handled by the standard library or existing project setup. If a dependency is needed, justify it, pin a tested version in the appropriate manifest, and explain installation.

## 6. Before committing

```bash
git diff --check
git status --short
git diff --stat
git diff
```

Review the staged diff for secrets, cookies, notebook outputs, raw data, accidental file deletions, and unrelated formatting changes. Confirm documentation links point to files that exist.

## 7. Pull request quality

A useful pull request includes a concise summary, implementation details, screenshots for genuine visual changes, exact validation commands, limitations, and data/privacy impact. Do not claim tests passed if they were not run. See [CONTRIBUTING.md](../CONTRIBUTING.md) and the repository pull request template.
