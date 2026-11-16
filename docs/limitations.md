# ⚠️ Known limitations, assumptions, and interpretation risks

## 1. Repository implementation limits

The inspected default-branch tree establishes two review-collection notebooks and a static frontend. It does not establish a production backend, live API, database, trained sentiment model, model weights, or benchmark report. The frontend should not be represented as a live product-intelligence service without the missing integration.

The revised notebooks now use explicit request timeouts, response status checks, candidate review-body selectors, minimal record fields, and optional local exports disabled by default. These changes improve safety and clarity but do not establish that the selectors match the current live platform pages. No live request was executed as part of the documentation update.

## 2. Selector and source coverage limitations

The Flipkart notebook uses candidate selector `div.ZmyHeo`; the Myntra notebook uses candidate selector `#user-review-reviewTextWrapper`. Retail page markup changes frequently. Either selector may return no matches or incomplete content. Each notebook inspects one page response only and does not implement pagination or dynamic browser interaction.

A collection run is a snapshot of what was returned at a particular time. Review ordering, moderation, pagination, and platform behaviour can affect the observed sample.

## 3. Data quality limitations

The notebooks currently store a minimal record containing source platform, product reference, retrieval timestamp, and review-body text. They do not yet extract stable source review IDs, ratings, language metadata, or a full collection-run manifest. Common schema validation and robust deduplication are not yet implemented.

The old Flipkart notebook output contained reviewer names and location strings because its selector was broad. That output was removed from the revised notebook. Contributors must continue checking notebook outputs and local exports for personal information before publication.

## 4. Selection bias

People who submit reviews may differ from customers who do not. Very positive or negative experiences may be overrepresented. Platform ranking and moderation can change the visible distribution. A small page sample should not be described as a representative survey.

## 5. Language and context

Reviews may contain multiple languages, transliteration, code-mixing, abbreviations, spelling variation, emojis, sarcasm, and domain-specific expressions. English-only preprocessing may exclude or distort feedback. Translation can also change tone and nuance.

## 6. Rating limitations

Star ratings are not direct sentiment annotations. A rating may reflect price, delivery, seller experience, expectations, or one specific defect. Converting ratings into sentiment classes introduces label noise.

## 7. Model limitations

No trained sentiment model or held-out evaluation report is established by the inspected tree. Model quality is therefore unknown. Any future model may misclassify negation, sarcasm, mixed opinions, short reviews, and code-mixed text. Aggregate scores can hide subgroup errors.

## 8. Product comparison limitations

Two products should not be compared by raw positive-review percentage if sample sizes, collection dates, rating scales, product categories, or source coverage differ. Show counts, date windows, missingness, and uncertainty. Avoid declaring a winner from a small or unbalanced sample.

## 9. Operational limitations

Requests can fail due to network errors, redirects, access restrictions, timeouts, or unexpected content types. The notebooks intentionally stop on access denial and throttling. Do not attempt to evade platform restrictions.

## 10. Reporting rule

Every conclusion should state what was observed, what was inferred, what data was used, and what cannot be concluded. Never present a model output as a definitive statement about product quality or an individual reviewer's intent.
