# Analysis of Products Using NLP

An exploratory product-research project combining customer-review scraping notebooks with a static product-discovery interface. The notebooks collect review text from Flipkart and Myntra pages for later natural-language analysis, while [`Frontend/`](./Frontend/) contains a visual prototype for product search, review sentiment, and price comparison.

## Repository contents

- `Web Scraping – Flipkart Customer Reviews.ipynb` - exploratory Selenium/browser scraping of a Flipkart product page and review text.
- `Web Scraping – Myntra Customer Reviews.ipynb` - requests/BeautifulSoup extraction of Myntra review blocks.
- `Frontend/index.html` - landing page describing sentiment analysis and price comparison.
- `Frontend/listing.html` - static product-listing mockup.
- `Frontend/*.css` and `Frontend/assets/` - prototype styling and image/icon assets.

The frontend is currently a static prototype: its search, authentication, notifications, and product controls are presentation elements unless explicitly connected to a service. The notebooks are experiments rather than a production ingestion pipeline.

## Getting started

### Frontend

From `Frontend/`, serve the files with any static HTTP server:

```bash
python -m http.server 8000
```

Open `http://localhost:8000/index.html`. Serving over HTTP avoids browser restrictions that can affect local asset loading.

### Notebooks

Use a Python environment with Jupyter, `requests`, `beautifulsoup4`, and the browser automation dependencies required by the Flipkart notebook. Open either notebook and run cells deliberately; live retailer markup, consent pages, anti-bot controls, rate limits, and terms can change without notice.

Do not scrape private pages, bypass access controls, collect unnecessary personal data, or use the output to make high-impact decisions. Check the target site's terms and robots guidance before running requests.

## Analysis workflow

1. Record the source URL, access date, product identifier, and collection method.
2. Store only the minimum review fields needed for analysis.
3. Normalize whitespace, ratings, languages, duplicates, and missing values.
4. Separate raw evidence from cleaned data and derived sentiment labels.
5. Validate sentiment results against a manually reviewed sample.
6. Report source limitations and avoid presenting prototype UI results as verified marketplace data.

## License

Code and original documentation are released under the MIT License. Third-party images, logos, retailer content, and dependencies remain subject to their respective terms.

Last updated: 2026-10-20 21:00 UTC
