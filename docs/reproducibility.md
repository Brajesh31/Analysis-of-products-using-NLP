# 🔁 Reproducibility and environment management

## Purpose

A review-analysis result is useful only when another contributor can understand how it was produced. This guide defines the minimum environment and execution record for the repository's exploratory notebooks. It does not claim that the current notebooks produce a deterministic NLP model or a benchmarked analytical result.

## Dependency files

- `requirements.txt` lists the direct runtime packages used by the current collection notebooks.
- `requirements-dev.txt` includes the runtime file plus JupyterLab and notebook-format tooling for development.
- The files use bounded version ranges. They are not a hash-locked dependency solution and do not guarantee identical transitive dependencies on every machine.

Create an isolated environment from the repository root:

```bash
python -m venv .venv
```

Activate it, then install development dependencies:

```powershell
# Windows PowerShell
.venv\\Scripts\\Activate.ps1
```

```bash
# macOS or Linux
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements-dev.txt
jupyter lab
```

Record the interpreter and installed package versions when sharing a result:

```bash
python --version
python -m pip freeze
jupyter --version
```

Do not paste environment output containing private package indexes, access tokens, or credentials into a public issue.

## Notebook execution protocol

1. Start from a clean kernel.
2. Read all Markdown instructions and inspect the cells before execution.
3. Confirm that the source and collection method are currently permitted.
4. Record the product URL or a non-sensitive product identifier, platform, retrieval timestamp, and selector assumptions.
5. Run only a small permitted test first.
6. Record the Python version and package versions.
7. Keep raw collected text separate from normalized text and derived features.
8. Do not publish raw review data unless redistribution is permitted.
9. Clear outputs before committing if they contain personal data, secrets, large payloads, or irrelevant execution noise.
10. Re-run from a fresh kernel before describing the notebook as validated.

## Reproducibility record template

| Field | Value to record |
|---|---|
| Date and time | UTC timestamp or clearly stated timezone |
| Notebook | Exact tracked notebook filename |
| Python | Full interpreter version |
| Jupyter | JupyterLab or Notebook version |
| Dependencies | Relevant package versions |
| Platform | Source platform and permitted access method |
| Product reference | Public URL or non-sensitive identifier |
| Selector | Exact selector and date it was checked |
| Sample size | Number of records collected, if collection was permitted |
| Data changes | Cleaning, filtering, deduplication, and exclusions |
| Random seed | Value, if any stochastic analysis is later introduced |
| Output location | Local path, never a private dataset committed by default |
| Limitations | Access restrictions, missing fields, sample bias, and uncertainty |

## Determinism and limits

HTTP responses can change over time. Product pages, review ordering, markup, access rules, and availability are outside this repository's control. Therefore, rerunning a collection notebook later may not return the same records. A timestamp and provenance record improve traceability but do not make a live source immutable.

If a future NLP pipeline introduces random train/test splitting, stochastic optimization, or randomized sampling, set and record the relevant seeds. Also record the dataset version and preprocessing configuration. A seed alone does not guarantee identical results across library versions, hardware, or execution backends.

## Before claiming reproducibility

- [ ] Dependencies install in a fresh virtual environment.
- [ ] Both notebooks open without format errors.
- [ ] Each notebook runs from a clean kernel under a permitted test condition.
- [ ] The exact tested environment is recorded.
- [ ] No private data or credentials are included in committed outputs.
- [ ] Results include sample size, provenance, and limitations.
- [ ] A second contributor can follow the documented steps.
