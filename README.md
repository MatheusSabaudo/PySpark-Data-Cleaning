# PySpark Data Cleaning

A PySpark exercise in cleaning and standardizing messy customer data into a well-typed, analysis-ready table. It walks through the kind of real-world data-quality fixes you hit when ingesting raw records.

## What it does

Starting from raw customer records with inconsistent formatting, the notebook:

- Profiles the data — row counts, schema, and null/empty counts per column.
- Cleans text fields (`full_name`, `email`, `country`): trims whitespace and converts empty strings to nulls.
- Repairs obfuscated emails, rewriting patterns like `name (at) domain (dot) com` back into valid `name@domain.com` addresses.
- Parses inconsistent dates into proper timestamps using `try_to_timestamp` with multiple format fallbacks.
- Standardizes `age`: safe-casts to integer and clamps invalid/negative/null values.
- Normalizes `country` into canonical values (e.g. collapsing `usa`, `united states`, etc.).
- Cleans `lifetime_value`, stripping currency symbols and codes (`$`, `,`, `GBP`, `EUR`, `USD`) and casting to numeric.
- Enforces a final target schema and drops duplicates.

## Key concepts demonstrated

- Schema design and enforcement with `StructType` / `StructField`
- Data profiling (null/empty detection across all columns)
- String cleaning and regex repair with `regexp_replace`
- Robust date parsing with `try_to_timestamp` and `coalesce`
- Safe type casting with `try_cast`
- Value normalization and deduplication

## Tech stack

- Python 3.9+
- Apache Spark (PySpark) 3.5+

## Getting started

```bash
git clone https://github.com/MatheusSabaudo/pyspark-data-cleaning.git
cd pyspark-data-cleaning
pip install -r requirements.txt
jupyter notebook data_cleaning.ipynb
```

The notebook builds its sample data inline, so no external dataset is required.

## License

[MIT](LICENSE) © Matheus Sabaudo
