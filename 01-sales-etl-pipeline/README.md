# Sales Data ETL Pipeline

## Project Overview

This project demonstrates a PySpark-based ETL pipeline built using Databricks Free Edition. The goal is to explore raw sales datasets, clean data, integrate customer, order, and product information, validate data quality, and store the resulting datasets as Delta tables.

## Technologies

- Python
- PySpark
- Databricks Free Edition
- Delta Lake

- ## Project Notebook

Explore the complete PySpark implementation, including data exploration, cleansing, joins, data-quality validation, exception handling, and Delta table creation.

**[View the Sales Data ETL Notebook](notebooks/01_sales_data_exploration.ipynb)**


## Source Datasets

The project uses three synthetic CSV datasets included in the [`data/sample/`](data/sample/) directory:

- `customers.csv` — customer master data.
- `orders.csv` — sales order records.
- `products.csv` — product master data.

These datasets are generated for learning and demonstration purposes.

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

The customer exceptions overlap with the main sales dataset, so they are not additional unique orders.

The main sales dataset and product exceptions together account for 484 unique orders.

## Key Learning Outcomes

- PySpark DataFrame transformations and joins.
- Data cleaning and validation.
- Handling unmatched records and data-quality exceptions.
- Building a basic ETL workflow.
- Writing and validating Delta tables.
- Reconciling record counts across pipeline outputs.

## Reproducibility

### Prerequisites

- Access to a Databricks workspace.
- Basic familiarity with Python and PySpark.
- The sample CSV files included in this repository.

### How to Run the Project

1. Clone or download this repository.
2. Download the CSV files from [`data/sample/`](data/sample/).
3. Upload the files to your Databricks workspace or another location accessible to your notebook.
4. Update the input paths in the notebook to match your file locations.
5. Configure the target catalog and schema for your Databricks environment.
6. Run the notebook cells in sequence, starting with setup and configuration.
7. Review the data-quality checks, integration results, exception datasets, and final record counts.

### Expected Results

When using the original sample datasets and the same transformation logic, the expected output counts are:

- **Main sales:** 482 records.
- **Product exceptions:** 2 records.
- **Customer exceptions:** 3 records.

These counts assume the original inputs and transformation rules. The customer exceptions overlap with the main sales dataset and should not be added when calculating unique orders.

### Important Notes

- The notebook may require changes to file paths, catalog names, and schema names in another Databricks workspace.
- The output Delta tables are created in the configured Databricks environment; they are not automatically included in this repository.
- The sample datasets are intended for educational use and do not represent production data.

## Project Status

**Completed — foundational ETL pipeline.**

The project covers data exploration, cleansing, integration, exception handling, and Delta table validation.

## Future Improvements

Incremental processing, idempotency, and Delta MERGE operations will be explored in a future project where repeated file uploads and corrections create a practical business requirement.
