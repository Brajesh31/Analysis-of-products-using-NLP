# 🤝 Contributing to Analysis of Products Using NLP

Thank you for considering a contribution. The most useful improvements make this project more reproducible, accurate, accessible, safe, and understandable. A large change is not automatically a valuable change. Prefer a focused, testable improvement over adding a new framework or model without a clear need.

## 1. Before you start

1. Read the root [README](README.md) to understand the current project boundary.
2. Read the relevant guide under [docs/](docs/README.md).
3. Search existing issues and pull requests to avoid duplicate work.
4. For substantial changes, open an issue describing the problem and proposed acceptance criteria.
5. Confirm that any proposed data collection is permitted by the source platform and applicable requirements.

The current project contains two exploratory review-collection notebooks and a static HTML/CSS frontend. A production API, database, and trained sentiment model are not established by the tracked tree. Contributions should not assume those components already exist.

## 2. Areas where contributions are useful

- **Notebook safety:** request timeouts, response validation, narrow selectors, and safe output handling.
- **Data quality:** schema validation, missingness reporting, deduplication, and provenance.
- **NLP methodology:** language handling, label provenance, baselines, evaluation, and error analysis.
- **Frontend:** semantic HTML, responsive behaviour, keyboard support, and accurate feature descriptions.
- **Documentation:** reproducible setup, diagrams, troubleshooting, and limitations.
- **Automation:** deterministic repository checks that do not scrape external retail sites.

## 3. Local setup

Clone the repository and create a focused branch:

```bash
git clone https://github.com/Brajesh31/Analysis-of-products-using-NLP.git
cd Analysis-of-products-using-NLP
git switch -c docs/describe-your-change
```

For the static frontend:

```bash
python -m http.server 8000 --directory Frontend
```

Open `http://localhost:8000/` and verify the home and listing pages.

For notebook work, install Jupyter and the packages imported by the notebook in an isolated environment. The repository does not currently provide a pinned dependency lockfile, so do not claim a fully reproducible environment until tested package versions are recorded.

## 4. Notebook contribution standards

- Add a clear Markdown explanation before each major stage.
- State the research question, source platform, collection date, and assumptions.
- Use explicit request timeouts and validate response status.
- Use narrow selectors that target review-body text only.
- Do not collect reviewer names, profile links, precise locations, or unrelated metadata.
- Never bypass CAPTCHAs, login restrictions, rate limits, or other access controls.
- Preserve raw text separately from normalized text.
- Keep cells restartable and runnable from a fresh kernel.
- Clear outputs containing personal data, cookies, tokens, raw HTML, or large datasets.
- Use synthetic fixtures for parser tests instead of live retail requests in CI.

## 5. Frontend contribution standards

Preserve existing relative asset paths unless a deliberate migration is included. Use semantic HTML, meaningful image alternative text, keyboard-accessible controls, visible focus, and responsive layouts. Do not present static mock elements as live product search, price comparison, or NLP functionality.

## 6. Documentation standards

Documentation must be detailed enough for another contributor to understand the purpose, assumptions, procedure, failure cases, and validation of a component. Avoid shallow one-paragraph files. At the same time, do not add filler or repeat the same generic guidance across every file. Keep project-specific details in the relevant guide and link related documents.

Use Mermaid source for diagrams so they remain editable. Label future architecture as proposed. Never invent benchmark scores, screenshots, endpoints, database tables, or model results.

## 7. Data and security requirements

Do not commit:
- credentials, API keys, cookies, browser storage, or session tokens;
- raw reviewer identities or contact information;
- private or restricted review data;
- large unreviewed exports;
- notebook outputs that expose sensitive page content.

If a secret is exposed, rotate it immediately. Removing it from the current file does not remove it from Git history.

## 8. Validation before opening a pull request

Run the checks relevant to your change:
- `git diff --check`;
- validate changed notebooks as JSON;
- restart and run notebook cells in order where safe and permitted;
- test the static frontend through a local server;
- inspect browser console and asset requests;
- check internal Markdown links;
- review the complete diff for accidental deletions and sensitive content.

Do not run retail scraping as part of CI. Use synthetic fixtures and mocked responses.

## 9. Pull request content

A high-quality pull request includes:
1. Problem statement and scope.
2. Summary of implementation and important decisions.
3. Files changed and user-visible effects.
4. Exact validation commands and observed results.
5. Data, privacy, and platform-policy impact.
6. Screenshots for genuine visual changes.
7. Known limitations and untested areas.

Use the repository pull request template. Keep changes focused and respond to review comments with evidence.

## 10. Review and merge

The maintainer may request revisions where behaviour is unclear, data collection is unsafe, tests are missing, or documentation overstates implementation. Approval is based on correctness and maintainability, not the size of the contribution.
