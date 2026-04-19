# ST-554-HW10

This repo contains Homework#10 for ST554. The assignment demonstrates two core components of Spark Structured Streaming:\
(1) creating and transforming a simple rate‑based stream, and\
(2) applying a batch‑trained machine learning pipeline to streaming CSV input.\
Together, these tasks show how `Spark` maintains a consistent transformation workflow across both static and streaming data sources.

## Methods
### Part 1 — Streaming Data Using the Rate Source
- Created a streaming DataFrame using Spark’s built‑in `rate` source (1 row/second).
- Applied transformations to compute the square root of the value column and the modulo‑4 remainder.
- Wrote the streaming output to an in‑memory table using `writeStream` with `format("memory")` and append mode.
- Allowed the stream to run for ~30 seconds, then stopped the query and displayed the full in‑memory table using Spark SQL.

### Part 2 — Applying a Pipeline to Streaming CSV Data
- Read the training dataset (`bikeDetails_for_fit.csv`) and prepared features using:
  - an SQLTransformer for log transforms and dummy variable creation
  - a `VectorAssembler` to combine features into a single vector
- Built and fit a two‑stage Pipeline on the batch DataFrame.
- Created a streaming DataFrame that monitors a folder for new CSV files using the same schema as the training data.
- Applied the fitted pipeline to the streaming DataFrame and wrote the transformed output to the console using append mode.
- Added five new CSV files (`bikeDetails_add*.csv`) to the input folder one at a time, allowing Spark to process each file as a separate micro‑batch.
- Stopped the streaming query after all files were processed.
## Summary
In this assignment, I implemented two complete streaming workflows in Spark. Part 1 focused on generating a simple rate‑based stream, applying transformations, and writing the results to an in‑memory table to observe continuous data processing. Part 2 extended these concepts by building a batch‑trained machine learning pipeline using SQL‑based feature engineering and a `VectorAssembler`, then applying that pipeline to streaming CSV input. By defining a consistent schema, applying the fitted pipeline to incoming data, and writing the output to the console, I demonstrated how Spark Structured Streaming supports unified preprocessing across both static and streaming data. These steps highlight key concepts such as defining a logical plan, applying transformations, starting a streaming query, and managing micro‑batch processing.
