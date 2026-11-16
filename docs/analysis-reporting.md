# 📊 Analysis, visualization, and reporting standard

## 1. Reporting objective

An analysis report should answer a specific product-feedback question and show how the evidence supports the conclusion. It should not merely display a word cloud or a sentiment percentage. Every reported statistic must be traceable to a dataset version, collection window, source, and processing method.

## 2. Minimum report metadata

Every report should state:
- report generation date;
- source platform and product coverage;
- collection start/end timestamps;
- number of pages or records inspected;
- accepted, rejected, and duplicate record counts;
- language scope and unsupported-language handling;
- missing text and missing rating rates;
- preprocessing version;
- label provenance, if sentiment is included;
- model or lexicon version;
- known limitations.

## 3. Exploratory summaries

Useful first-pass outputs include review volume by product/source, rating distributions, review-length distribution, missingness, duplicate rates, language distribution, and frequent unigrams/bigrams. These summaries describe the observed sample; they do not prove population-wide customer opinion.

## 4. Sentiment reporting

For every sentiment chart:
- show counts as well as percentages;
- include the denominator;
- identify whether labels are human-annotated, rating-derived, lexicon-based, or model-predicted;
- report model evaluation separately from predictions on the analysis sample;
- avoid hiding neutral or uncertain examples;
- explain how mixed sentiment is handled.

Never describe rating-derived proxy labels as ground truth.

## 5. Aspect reporting

Aspect summaries should distinguish mention frequency from sentiment. A product aspect mentioned often is not necessarily a problem. Report the number of reviews that mention the aspect, the number with a sentiment label, the method used to extract the aspect, and representative examples only when publication is permitted.

## 6. Product comparisons

Do not rank products using unadjusted percentages when sample size, source, collection dates, rating scales, or category differ. Use minimum sample thresholds and clearly show the data coverage. If uncertainty intervals are calculated, describe the method and assumptions.

## 7. Visualization quality

- Use clear chart titles and labelled axes.
- Show units and denominators.
- Avoid 3D charts and misleading truncated scales.
- Use a colour-blind-aware palette and redundant labels.
- Provide a text explanation and accessible data table.
- Include collection dates and source labels.
- Do not use a decorative word cloud as the sole evidence for a conclusion.

## 8. Recommended report structure

1. Executive summary.
2. Research question and scope.
3. Data sources and collection method.
4. Dataset quality and coverage.
5. Methodology and preprocessing.
6. Results and visualizations.
7. Error analysis and uncertainty.
8. Interpretation and practical implications.
9. Limitations and ethical considerations.
10. Reproducibility appendix.

## 9. Review checklist

Before publishing, verify that all figures can be regenerated, all percentages have denominators, all model metrics come from a held-out set, no reviewer identities are exposed, and every claim is supported by the described sample.
