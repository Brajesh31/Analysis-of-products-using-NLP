# Architecture

The project has two independent surfaces:

1. **Collection notebooks** use browser/HTTP parsing to extract review content from retailer product pages.
2. **Static frontend** presents a product-analysis concept through `Frontend/index.html` and `Frontend/listing.html`, with CSS and local assets.

There is currently no committed API, database, or model-serving layer connecting the notebooks to the frontend. Any future integration should preserve provenance and distinguish collected evidence from derived sentiment or price claims.
