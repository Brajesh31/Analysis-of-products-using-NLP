# ⚡ Performance and resource management

## 1. Measure before optimizing

Performance work should begin with a repeatable workload and a baseline measurement. Record input size, machine/runtime, software versions, elapsed time, and memory use. Avoid publishing claims such as “fast” or “high performance” without a measurable comparison.

## 2. Collection performance

Collection should be governed by platform permission and request limits, not by a goal to maximize throughput. Use conservative pacing, explicit timeouts, and stop conditions. Avoid fetching the same page repeatedly. Record counts for pages attempted, successful responses, parsed reviews, rejected records, and failures where permitted.

Do not increase concurrency to work around throttling. If the source restricts requests, stop or use an authorized data access method.

## 3. Parsing and memory

For small pages, parsing a response in memory is usually sufficient. For larger permitted datasets, process records in bounded batches and avoid repeated full-dataframe copies. Keep raw and processed datasets separate. Prefer stable, typed columns over storing every field as an unstructured object.

## 4. Text processing

- Normalize text once per preprocessing version.
- Cache deterministic transformations only when the cache can be invalidated by source or method changes.
- Profile tokenization on representative language samples.
- Bound vocabulary size using validation data.
- Avoid expensive transformer inference if a simple baseline meets the analytical need.
- Batch model inference according to available memory.
- Record model, tokenizer, and library versions.

## 5. Frontend performance

The current frontend is static and includes local image assets. Review image dimensions and file sizes before publishing. Use appropriately sized images, responsive image behaviour where needed, and lazy loading for off-screen media when it improves actual performance. Preserve image quality and meaningful alternative text.

Avoid adding a large charting library or frontend framework for a static page unless the product requirement justifies it.

## 6. Monitoring future pipelines

If a scheduled or service-based pipeline is added, monitor request failures, parser drift, processing latency, memory, queue depth, dataset growth, and error rates. Monitoring should avoid storing raw review text or secrets.

## 7. Performance report template

For each benchmark, record:
- benchmark objective;
- dataset size and source;
- hardware and operating system;
- Python and package versions;
- warm-up and repetition procedure;
- median and spread, not just the best run;
- memory consumption;
- output correctness checks;
- limitations and external factors.

## 8. Optimization priorities

For this project, reproducibility and data quality should come before throughput. A fast parser that captures unrelated page content or silently misses reviews is not an improvement.
