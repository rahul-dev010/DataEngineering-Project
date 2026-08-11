# Data Engineering Project - Sales Analytics Pipeline

A production-ready data engineering pipeline built with Databricks Declarative Automation Bundles (DABs), implementing the medallion architecture for sales analytics.

## Architecture

**Medallion Layers:**
- **Bronze**: Raw data ingestion (customers, products, sales, suppliers)
- **Silver**: Cleaned and validated data
- **Gold**: Business-ready analytics aggregations

## Project Structure

```
de_project/
├── databricks.yml              # DABs configuration
├── resources/
│   └── sales_etl_job.job.yml  # ETL pipeline definition
├── src/
│   ├── bronze/                # Raw data ingestion notebooks
│   ├── silver/                # Data cleaning notebooks
│   ├── Gold/                  # Analytics aggregation notebooks
│   ├── table_creation         # Schema setup
│   └── cat_schema             # Catalog configuration
├── tests/                     # Unit tests
└── fixtures/                  # Test data
```

## Pipeline Flow

1. **Bronze Layer**: Parallel ingestion of customers, products, sales, suppliers
2. **Silver Layer**: Data cleaning and transformation with dependencies
3. **Gold Layer**: Business analytics
   - Customer Analytics
   - Sales Performance Metrics
   - Trend Analysis
   - Product Performance
4. **Dashboard Refresh**: Auto-refreshes analytics dashboard

## Environments

| Environment | Catalog | Mode |
|------------|---------|------|
| dev | `de_dev` | Development (default) |
| uat | `de_uat` | Development |
| prod | `de_prod` | Production |

## Deployment

```bash
# Validate bundle
databricks bundle validate -t <env>

# Deploy to environment
databricks bundle deploy -t dev
databricks bundle deploy -t uat
databricks bundle deploy -t prod

# Run the pipeline
databricks bundle run Sales_ETL_Pipeline_DE_Pro -t <env>
```

## Features

✓ Multi-environment support (dev/uat/prod)  
✓ Medallion architecture  
✓ Task dependency management  
✓ Dashboard integration with email notifications  
✓ Performance optimized execution  
✓ Queue-enabled job execution  

## Requirements

- Databricks workspace
- Unity Catalog enabled
- SQL Warehouse (for dashboard refresh)
- Databricks CLI configured

## Configuration

The pipeline uses parameterized catalogs via `${var.catalog}` for environment-specific deployments.