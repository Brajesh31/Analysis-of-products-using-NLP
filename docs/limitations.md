# ⚠️ Known limitations, assumptions, and interpretation risks

## 1. Repository implementation limits

The inspected default-branch tree establishes the presence of two review-collection notebooks and a static frontend. It does not establish a production backend, live API, database, trained sentiment model, model weights, or benchmark report. The frontend should not be represented as a live product-intelligence service without the missing integration.

The notebooks are exploratory and contain platform-specific selectors. The Flipkart notebook currently uses a broad `div.row` selector, which can capture unrelated product-page text and reviewer metadata. Its saved output includes identifying reviewer details and should be cleared before public redistribution. The Myntra notebook uses a narrower review-container selector, but that selector can still become stale.

## 2. Source and coverage limitations

A single product URL or a small set of product pages cannot represent an entire platform, product category, or customer population. Review ordering, moderation, pagination, incentives, and product lifecycle can affect what is visible. A collection run is only a snapshot of the accessible page at a particular time.

## 3. Selection bias

People who choose to submit reviews may differ from customers who do not. Extremely positive or negative experiences may be overrepresented. Platform ranking and review moderation can further change the observed distribution. A review sample should not be described as a statistically representative survey unless its sampling design supports that claim.

## 4. Language and context

Reviews can contain multiple languages, transliteration, code-mixing, abbreviations, spelling variation, emojis, sarcasm, and domain-specific expressions. English-only preprocessing may exclude or distort part of the available feedback. Translation can also change tone and nuance.

## 5. Rating limitations

Star ratings are not direct sentiment annotations. A rating may reflect price, delivery, seller experience, product expectations, or a single defect. Converting ratings into sentiment classes introduces label noise and can create misleading model scores.

## 6. Model limitations

A sentiment model may misclassify negation, sarcasm, mixed opinions, short comments, or aspect-specific feedback. Aggregate scores can hide important subgroup errors. Without a labelled test set, baseline, and error analysis, model quality is unknown.

## 7. Comparison limitations

Two products should not be compared by raw positive-review percentage if their sample sizes, collection dates, rating scales, category mix, or source coverage differ. Show counts, date windows, and missingness. Avoid declaring a winner based on a small or unbalanced sample.

## 8. Operational limitations

Retail websites change markup and access behaviour. A selector that worked previously may return no records or the wrong content. Requests can fail due to network errors, redirects, access restrictions, or timeouts. Collection must stop when platform restrictions indicate that access is not allowed.

## 9. Reporting rule

Every analytical conclusion should state what was observed, what was inferred, what data was used, and what cannot be concluded. Do not present a model output as a definitive statement about product quality or an individual customer's intent.
