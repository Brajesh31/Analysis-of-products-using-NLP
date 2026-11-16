# Product review analysis report

> Replace all bracketed prompts. Do not publish raw review excerpts or personal information without permission.

## 1. Executive summary

State the research question, most important supported observations, and the limits of the evidence. Avoid a definitive product recommendation when the sample is small or biased.

## 2. Research question and scope

- **Question:** [What is being investigated?]
- **Products:** [Non-sensitive product identifiers]
- **Platforms:** [Approved sources]
- **Collection window:** [Start and end timestamps]
- **Language scope:** [Languages included/excluded]
- **Intended audience:** [Who will use the result?]

## 3. Data provenance

Describe the authorized collection method, source pages, retrieval dates, parser version, schema version, and any known source restrictions.

| Measure | Count |
|---|---:|
| Pages or records inspected | [n] |
| Records accepted | [n] |
| Records rejected | [n] |
| Duplicates identified | [n] |
| Missing review text | [n] |
| Missing ratings | [n] |

## 4. Data quality

Describe missingness, duplicate handling, malformed records, language detection, and sample coverage. Explain whether the data is representative. Usually, online reviews are self-selected and should not be treated as a random sample.

## 5. Methodology

Document preprocessing, tokenization, language handling, label provenance, feature extraction, baseline, model configuration, split strategy, and software versions. Clearly distinguish human labels from rating-derived proxies and model predictions.

## 6. Results

For every table and chart, include denominators, collection dates, source, and units. Report class-wise metrics and support counts when evaluating a classifier. Include a text summary and accessible data alternative for important visualizations.

## 7. Error analysis

Review false positives, false negatives, mixed sentiment, sarcasm, code-mixed text, short reviews, and domain-specific language. Explain which failure cases could materially change the conclusion.

## 8. Interpretation

Separate direct observations from inference. Explain practical implications without claiming causation or population-wide representativeness.

## 9. Limitations and responsible use

Document selection bias, source coverage, platform changes, label noise, language gaps, privacy controls, retention, and publication permissions.

## 10. Reproducibility

Provide the dataset version or safe reference, code commit, environment, random seeds, exact commands, and expected outputs. Do not attach restricted raw data.

## 11. Review checklist

- [ ] Every metric has a denominator and source.
- [ ] Dataset scope and collection window are explicit.
- [ ] Label provenance is documented.
- [ ] Evaluation uses a held-out test set.
- [ ] No personal information is exposed.
- [ ] Conclusions match the evidence.
- [ ] Limitations and untested areas are disclosed.
