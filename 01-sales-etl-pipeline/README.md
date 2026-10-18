# Sales Data ETL Pipeline

## Project Overview

This project demonstrates a PySpark-based ETL pipeline built using Databricks Free Edition. The goal is to explore raw sales datasets, clean data, integrate customer, order, and product information, validate data quality, and store the resulting datasets as Delta tables.

## Technologies

- Python
- PySpark
- Databricks Free Edition
- Delta Lake

## Source Datasets

The project uses three datasets:

- Customers
- Orders
- Products

## Pipeline Workflow

1. Explore source datasets and assess data quality.
2. Remove duplicate and invalid order records.
3. Validate customer and product references.
4. Join orders with product and customer information.
5. Separate unmatched records into exception datasets.
6. Create and validate Delta tables.

## Data Quality and Exception Handling

The pipeline identifies duplicate orders, invalid quantities, missing identifiers, and unmatched customer or product references.

Instead of silently discarding unmatched records during integration, the project preserves them in dedicated exception datasets for investigation.

## Output Tables

| Table | Records |
|---|---:|
| `main_sales` | 482 |
| `product_exceptions` | 2 |
| `customer_exceptions` | 3 |

The customer exceptions overlap with the main sales dataset, so they are not added to the main sales record count.

## Key Learning Outcomes

- PySpark DataFrame transformations and joins
- Data cleaning and validation
- Handling unmatched records
- Building a basic ETL workflow
- Writing and validating Delta tables

## Project Status

Completed — foundational ETL pipeline.

## Future Improvements

Incremental processing, idempotency, and Delta MERGE operations will be explored in a future project where they solve a real business requirement.
