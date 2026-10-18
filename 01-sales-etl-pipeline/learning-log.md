# Sales Data ETL Pipeline — Learning Log

This log documents the challenges, decisions, and concepts I learned while building my first hands-on Data Engineering project using Databricks and PySpark.

## 1. Exploring the Source Data

**What I learned**
- How to inspect DataFrame schemas, record counts, and missing values.
- Why data profiling is important before starting transformations.
- How to identify duplicate records and inconsistent data.

## 2. Cleaning Order Data

**Challenges**
- Duplicate order IDs.
- Orders with invalid quantities.
- Missing customer or product identifiers.

**What I learned**
- How to apply filtering and deduplication in PySpark.
- Why data-quality rules must reflect the actual business requirement.
- Why missing identifiers should be handled deliberately rather than ignored.

## 3. Integrating Customers, Orders, and Products

**What I learned**
- How joins combine information from multiple datasets.
- How unmatched records can be identified and investigated.
- Why choosing the right join strategy affects which records are retained.

## 4. Handling Exceptions

Rather than silently discarding unmatched records, I separated product-related and customer-related exceptions for investigation.

**Key learning:** Exception handling helps preserve visibility into data-quality problems.

## 5. Creating Delta Tables

I saved the processed datasets as Delta tables and validated the saved record counts.

| Output table | Records |
|---|---:|
| `main_sales` | 482 |
| `product_exceptions` | 2 |
| `customer_exceptions` | 3 |

The customer exceptions overlap with the main sales dataset. Therefore, the 3 customer exceptions are not additional unique orders.

## 6. Key Takeaways

- Data Engineering involves more than writing transformations; it requires validation and reconciliation.
- Data-quality rules should be explicit and testable.
- Unmatched records can provide useful investigation data.
- Final outputs should be validated after writing them to storage.

## 7. Future Learning

I plan to explore incremental processing, idempotency, and Delta MERGE in a future project where repeated file uploads and corrections make those techniques necessary.
