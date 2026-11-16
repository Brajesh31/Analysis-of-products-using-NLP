# 🧠 NLP methodology: preprocessing, modelling, and evaluation

## 1. Start with a precise question

“Use NLP on reviews” is not a sufficiently precise task definition. Choose a target:
- **Polarity classification:** positive, neutral, or negative opinion.
- **Aspect-based sentiment:** opinion about a named attribute such as battery, camera, fit, durability, price, or delivery.
- **Topic exploration:** recurring themes without assigning sentiment.
- **Rating-text agreement:** whether written language broadly aligns with the numeric rating.
- **Product comparison:** differences in themes or sentiment under comparable sampling conditions.

Each target needs its own label definition, evaluation method, and interpretation.

## 2. Preprocessing design

Preserve the raw review text and apply transformations into separate fields. A practical sequence is:
1. Validate text type and encoding.
2. Normalize Unicode consistently.
3. Remove accidental HTML markup while retaining meaningful punctuation.
4. Normalize whitespace.
5. Detect language and record confidence.
6. Route supported languages to suitable tokenizers.
7. Handle transliteration and code-mixing explicitly.
8. Create tokens or model inputs.
9. Record preprocessing version and configuration.

Do not automatically remove stop words, punctuation, emojis, or repeated characters. “Not good” is not equivalent to “good”; emojis and punctuation can carry meaning. Stemming and lemmatization can also damage domain terms and names.

## 3. Exploratory analysis before modelling

Before training, inspect:
- number of records by source and product;
- missing text and rating rates;
- duplicate and near-duplicate rates;
- review-length distribution;
- language distribution;
- rating distribution by source;
- collection date coverage;
- frequent terms and n-grams;
- unusually repetitive or templated reviews.

This step often reveals more important problems than model selection. For example, a dataset dominated by one product or one rating class cannot support a broad claim about customer opinion.

## 4. Label provenance

A model is only as trustworthy as its labels. Document whether labels come from human annotation, ratings, a lexicon, or another model.

If star ratings are converted into positive/neutral/negative classes, call them *rating-derived proxy labels*. They are not direct annotations of the review's expressed sentiment. A customer can give a high rating while criticizing one aspect, or a low rating because of shipping rather than product performance.

For human annotation, provide a written guide, ambiguous examples, annotator count, disagreement resolution, and inter-annotator agreement where appropriate.

## 5. Baselines

Begin with simple, inspectable baselines:
- majority-class prediction;
- a domain-appropriate lexicon baseline;
- TF-IDF features with logistic regression or a linear SVM, when labels exist.

A complex transformer should earn its place by improving a meaningful metric on a held-out set. Do not compare models using different data splits or preprocessing and then attribute all differences to the model.

## 6. Train/test design

Split before fitting any learned transformations. Keep duplicates and near-duplicates together. If the intended use is predicting sentiment for unseen products, use product-grouped splits. If the intended use is future reviews, consider a time-based holdout. Avoid random splitting when it creates leakage from repeated reviews or product templates.

## 7. Evaluation

For classification, report:
- confusion matrix;
- precision, recall, and F1 for each class;
- macro-F1 when class imbalance matters;
- class support counts;
- accuracy as a supplementary metric;
- baseline comparison;
- representative error analysis.

Inspect performance across languages, sources, products, rating bands, and review lengths. Report limitations for groups with too few examples.

## 8. Aspect-based analysis

Aspect extraction and sentiment classification are separate tasks. A sentence can mention several aspects with different opinions. Define an aspect taxonomy, annotation policy, and treatment of implicit aspects before building an aspect model. Validate extracted aspect-opinion pairs manually on a representative sample.

## 9. Reporting and reproducibility

Record dataset version, collection window, sources, sample counts, language scope, label provenance, preprocessing version, split strategy, random seeds, model configuration, software versions, and metrics. Do not publish a score without support counts and a description of the test set.

## 10. Responsible interpretation

Reviews are self-selected and may be affected by incentives, moderation, fake activity, product lifecycle, or platform ranking. NLP predictions can misread sarcasm, dialect, spelling variation, and code-mixed text. Treat model outputs as evidence to investigate, not as a definitive product verdict.
