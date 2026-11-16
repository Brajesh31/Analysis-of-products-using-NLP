# 🖥️ Static frontend guide

This directory contains the original static HTML/CSS prototype for the product-feedback project. It is intentionally kept separate from the exploratory collection notebooks.

## Current pages

| File | Responsibility |
|---|---|
| `index.html` | Main landing page and project concept presentation |
| `index.css` | Landing-page styles |
| `listing.html` | Product listing and product-detail presentation prototype |
| `listing.css` | Listing-page styles |
| `assets/` | Existing product, team, logo, illustration, and interface assets |

The frontend is a static prototype. The repository does not currently include a frontend package manifest, JavaScript application bundle, API client, authentication service, or verified backend integration. Search, sign-in, sign-up, pricing, product comparison, and sentiment-analysis elements should therefore be treated as presentation concepts unless their behaviour is implemented and tested.

## Run locally

From the repository root:

```bash
python -m http.server 8000 --directory Frontend
```

Then open `http://localhost:8000/` and `http://localhost:8000/listing.html`. Stop the server with `Ctrl+C`.

## Asset path rules

- Keep asset references relative to the HTML files, for example `assets/Mainimg.png`.
- Preserve exact filename case. A path that works on a case-insensitive local filesystem can fail on Linux hosting.
- Do not rename or delete existing assets without updating every reference and checking both pages.
- Use descriptive alternative text for informative images. Use empty alternative text only for purely decorative images.
- Compress newly added raster images and prefer SVG for simple interface icons where practical.
- Do not commit copyrighted product photography unless the project has permission to redistribute it.

## Frontend change checklist

- [ ] Both pages load from the local static server.
- [ ] No missing CSS, image, or font requests in the browser network panel.
- [ ] No new browser-console errors.
- [ ] Navigation and controls have meaningful destinations or are clearly marked as non-functional prototypes.
- [ ] Page works at narrow mobile, tablet, and desktop widths.
- [ ] Text remains readable when zoomed to 200%.
- [ ] Keyboard focus is visible and interactive controls can be reached without a mouse.
- [ ] Images have appropriate alternative text.
- [ ] Colour contrast and form labels have been reviewed.
- [ ] Screenshots in documentation represent the actual current UI, not a proposed redesign.

## Screenshots and demonstrations

Use screenshots captured from the running pages when documenting the interface. Store approved screenshots in a clearly named directory such as `docs/images/`, include the capture date and viewport in the pull request, and avoid placing reviewer or customer personal information in screenshots. Do not label mockups as a working product integration.

## Known limitations

The current HTML includes prototype copy and controls that do not establish working product search, accounts, checkout, price comparison, review ingestion, or sentiment predictions. Do not connect these controls to invented endpoints. A future integration should define a documented API contract, loading and error states, data provenance, and accessibility behaviour before it is described as functional.
