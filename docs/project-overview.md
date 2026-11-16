# 🔎 Project overview and product context

## 1. Why this project exists

Product reviews are a large source of unstructured customer feedback. Ratings provide a quick signal, but a single number rarely explains *why* a customer is satisfied or disappointed. A review may praise battery life while criticizing the camera, describe good product quality but poor delivery, or use sarcasm that a simple keyword counter will misread.

This repository explores the product-feedback problem through two platform-specific review collection notebooks, one for Flipkart and one for Myntra, alongside a static HTML/CSS frontend prototype. The long-term direction is to help users explore product feedback and understand consumer acceptance. The current repository should be treated as an exploratory prototype, not a production decision engine.

## 2. Problem statement

A person evaluating a product idea or competitor often needs to answer questions such as:
- What do customers repeatedly appreciate?
- Which product aspects attract complaints?
- Do written reviews broadly agree with the rating distribution?
- Are there meaningful differences between products or platforms?
- Is the available sample large and representative enough to support a conclusion?

Manually reading every review becomes difficult as volume grows. NLP can help organize text, but it cannot make weak, biased, or unauthorized data reliable.

## 3. Current implementation boundary

The tracked default-branch tree contains:
- a Flipkart customer-review scraping notebook;
- a Myntra customer-review scraping notebook;
- static home and listing pages under `Frontend/`;
- local image, icon, and SVG assets;
- GitHub repository metadata and documentation.

The inspected tree does not establish:
- a trained sentiment classifier or model weights;
- a production NLP preprocessing package;
- a backend API or authentication service;
- a database or persistent review store;
- an automated collection scheduler;
- a live product search or price-comparison integration;
- benchmark metrics or a validated production dataset.

This boundary is deliberate. Documentation distinguishes implemented artefacts from future proposals so that visitors are not misled.

## 4. Project objectives

1. Keep platform-specific collection experiments understandable and inspectable.
2. Define a common review record so future analysis can compare sources responsibly.
3. Preserve raw text, source context, and retrieval timestamps where collection is permitted.
4. Add data-quality checks before analysis.
5. Establish a transparent path to exploratory NLP, sentiment, and aspect-level analysis.
6. Make results explainable through sample sizes, provenance, and limitations.
7. Maintain a static interface that can later display validated aggregated insights.

## 5. Intended users and use cases

| User | Question | Useful output |
|---|---|---|
| Product researcher | What do customers mention most? | Topic and keyword summaries |
| Startup founder | Does a similar product already exist? | Carefully sourced competitor/product context |
| Product manager | What aspects create dissatisfaction? | Aspect-level feedback summaries |
| Analyst | Are review ratings and text consistent? | Rating/text comparison with caveats |
| Developer | Can this workflow be reproduced? | Documented notebooks, schema, and tests |

These are intended use cases. They should not be presented as currently available product features unless the corresponding implementation is committed and verified.

## 6. Analytical principles

- Separate observed data from model interpretation.
- Treat ratings as metadata or weak proxy labels, not perfect sentiment truth.
- Keep original text separate from normalized text.
- Preserve language and context where possible.
- Avoid reviewer identity collection.
- Compare products only when source coverage, collection windows, and sample sizes are comparable.
- Publish denominators and uncertainty alongside percentages.

## 7. Definition of a credible release

A release that makes analytical claims must include the dataset scope, source and collection dates, field definitions, preprocessing version, label provenance, split strategy, baseline, class-wise metrics, error analysis, and limitations. A screenshot or attractive chart is not evidence of model quality by itself.

## 8. Out of scope

Bypassing platform restrictions, identifying reviewers, inferring sensitive personal attributes, scraping private content, publishing unapproved raw reviews, and presenting unvalidated predictions as facts are outside the project scope.
