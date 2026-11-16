# 🚀 Installation and local setup

## 1. Prerequisites

For the static frontend:
- Git;
- a modern browser;
- Python 3 for the built-in static HTTP server, or another local static server.

For the notebooks:
- a supported Python installation;
- Jupyter Notebook, JupyterLab, or Google Colab;
- the packages imported by the specific notebook;
- internet access only where permitted and required for a source request.

The inspected tracked tree does not include a pinned dependency manifest. The package list below is therefore intentionally not presented as a complete, verified lockfile. Inspect notebook imports and test the selected versions in a clean environment before adding a requirements file.

## 2. Clone the repository

```bash
git clone https://github.com/Brajesh31/Analysis-of-products-using-NLP.git
cd Analysis-of-products-using-NLP
```

## 3. Run the frontend locally

From the repository root:

```bash
python -m http.server 8000 --directory Frontend
```

Open `http://localhost:8000/`. The listing page is available at `http://localhost:8000/listing.html`.

If a page is blank or assets are missing, check the browser console and verify that local paths use the correct case. Linux-based hosting is case-sensitive.

## 4. Prepare a notebook environment

Create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
source .venv/bin/activate
```

Install Jupyter and the dependencies actually imported by the notebook. The visible notebook code uses BeautifulSoup and Requests. Install the corresponding packages in the active environment, then launch Jupyter:

```bash
python -m pip install --upgrade pip
python -m pip install jupyter requests beautifulsoup4
jupyter lab
```

This is a starting environment for the inspected notebook imports, not a pinned reproducibility guarantee. Record exact versions after validating the notebook.

## 5. Execute responsibly

Open the notebook for the intended platform. Read its Markdown instructions and code before running any collection cell. Confirm current platform terms, access rules, and applicable law. Use a small permitted test. Do not bypass technical restrictions.

## 6. Reproducibility checklist

- [ ] Python version recorded.
- [ ] Jupyter version recorded.
- [ ] Package versions recorded.
- [ ] Notebook opened from a clean kernel.
- [ ] Source access method permitted.
- [ ] Collection timestamp and source context recorded.
- [ ] Outputs inspected for personal data and secrets.
- [ ] Raw and processed data kept separate.
