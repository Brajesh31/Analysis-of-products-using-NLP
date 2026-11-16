# 🎨 Frontend implementation and review guide

## 1. Scope

The current frontend is a static HTML/CSS prototype in `Frontend/`. It communicates the intended product experience through a landing page and a listing page. It is not a verified full-stack application.

The page copy references capabilities such as sentiment analysis, price comparison, product search, and key-feature discovery. Those labels describe the concept. They must not be presented as operational features until the repository contains working application logic and verified data integration.

## 2. Page map

| Page | File | Main purpose |
|---|---|---|
| Landing | `Frontend/index.html` | Introduces the product concept and proposed capabilities |
| Listing | `Frontend/listing.html` | Presents a product browsing and listing concept |

Styles are maintained in the matching CSS files. Existing images and icons are stored under `Frontend/assets/`.

## 3. Local review

Run the static server from the repository root:

```bash
python -m http.server 8000 --directory Frontend
```

Review both pages at desktop and mobile viewport sizes. Use browser developer tools to inspect failed asset requests, layout overflow, console errors, and accessibility warnings.

## 4. Design and content standards

- Keep typography, spacing, button treatments, and navigation behaviour consistent across pages.
- Use semantic landmarks and a logical heading hierarchy.
- Associate form controls with visible labels.
- Use buttons for actions and links for navigation.
- Provide visible keyboard focus and ensure controls are keyboard operable.
- Avoid colour as the only way to communicate state.
- Add useful alternative text to informative images.
- Avoid arbitrary placeholder links such as `#` for controls represented as functional navigation.
- Keep copy accurate about what is implemented and what remains conceptual.

## 5. Integration boundary

Before connecting the frontend to a future backend, document the API endpoint and method, request and response schemas, authentication requirements, loading and error states, rate limits, data provenance, privacy rules, and accessibility behaviour for asynchronous updates. Do not place secrets in browser-side HTML or JavaScript. Browser-delivered code is public.

## 6. Screenshot policy

Capture screenshots from the actual running pages. Include viewport dimensions and capture date in the pull request. Use optimized image files, descriptive filenames, and alt text in documentation. Do not fabricate product analytics, ratings, sentiment charts, or backend results for demonstration purposes. Synthetic examples must be labelled as synthetic.

## 7. Review checklist

- [ ] Landing and listing pages render.
- [ ] Relative asset paths resolve on a case-sensitive filesystem.
- [ ] No console errors or broken network requests remain.
- [ ] Layout works at mobile, tablet, and desktop widths.
- [ ] Keyboard navigation and focus visibility are supported.
- [ ] Images have suitable alternative text.
- [ ] Controls are functional or explicitly identified as prototypes.
- [ ] Content does not claim unimplemented functionality.
- [ ] Screenshots match the committed interface.
