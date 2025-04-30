# 🏥 Health Batch Data Pipeline (Databricks)

This repository implements a batch ETL pipeline using **Databricks** for healthcare API and PDF metadata ingestion. The architecture includes Bronze, Silver, and Gold layers for structured processing.

---

## 📁 Project Structure

```
akrivia-health-batch-pipeline/
├── config/
│   └── pipeline_config.yml        # YAML config for data sources
├── delta/
│   ├── bronze/                    # Raw ingested data
│   ├── silver/                    # Cleaned & enriched data
│   └── gold/                      # Aggregated business summaries
├── notebooks/                     # Databricks notebooks (Python)
├── dbfs_setup/                    # Utility scripts for DBFS or init
└── README.md                      # Project documentation
```

---

## ⚙️ Components

- **Healthcare API:** Pulls FHIR data from public API.
- **Gov PDFs:** Parses metadata from raw PDF files.
- **Delta Lake:** Stores all processed layers with schema evolution.
- **Business Logic:**
  - Adds patient age
  - Categorizes PDFs by file size
  - Aggregates records per day

---

## 🧪 Execution

1. Set up Databricks cluster (DBR 11+ recommended)
2. Upload `notebooks/` to Databricks Workspace
3. Mount or simulate `/FileStore` data inputs
4. Run `init.sql` to create Delta schemas
5. Execute notebooks: ingestion → silver → gold
6. Optionally export:
   - PDFs to MongoDB
   - Patient summaries to DuckDB or MotherDuck

---

## 🔐 Credentials

- Avoid hardcoding secrets.
- Use Databricks Secrets or environment variables for external DB connections.

---

## 📬 Support

Reach out to the Data Engineering team at Akrivia for onboarding or help.
