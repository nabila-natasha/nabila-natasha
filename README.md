## Hi, I'm Nabila 👋

### Data Engineer | Data Analyst | Analytics Engineer

SQL · Python · PySpark · Azure · Snowflake · Power BI · Terraform · CI/CD · Machine Learning

I'm a data professional with 5+ years across energy, banking and technology. I turn fragmented, manual reporting into reliable, automated analytics, and I build the pipelines, data-quality controls and dashboards behind it.

My day-to-day work covers ETL and data integration into SQL Server and Power BI, regulatory data profiling and UAT, and Azure Databricks / PySpark / Data Factory workloads. My self-directed projects below extend that experience onto cloud platforms with infrastructure as code, automated testing, CI/CD and machine learning.

📍 Kuala Lumpur, Malaysia · Open to Data Engineer / Analytics Engineer / Data Analyst roles (remote, hybrid or on-site)

---

## 🚀 Featured Projects

### 1. Azure Transaction Risk Platform
**End-to-end Azure data-to-ML platform for transaction risk**

Batch and event-driven ingestion, a data-quality gate, ML, a SQL serving layer and BI, with Terraform and Azure DevOps CI/CD.

```text
ADF (batch, ~1.7M rows)  ──┐
                           ├─► ADLS Bronze ─► DQ gate ─► Silver (+ Quarantine / Audit)
Event Hubs replay (~140K) ─┘                                │
                                                            ▼
                         Gold ML outputs ◄─ XGBoost · Isolation Forest · SHAP
                                │
                                ▼
                    Synapse Serverless views ─► Power BI
```

- **Ingestion:** Azure Data Factory for historical batch; Azure Event Hubs for simulated near-real-time replay, with batching, retries and exponential backoff to handle throttling
- **Data quality:** schema and business validation, deterministic event-ID deduplication, quarantine; 104.7K duplicate events isolated from a 244K-row replay
- **ML:** chronological train/evaluate split, XGBoost with class weighting (ROC-AUC 0.98, PR-AUC 0.36, recall 84% at 0.50 threshold), threshold analysis, Isolation Forest anomaly signal, SHAP explainability
- **Serving:** Synapse Serverless SQL views at explicit analytical grains feeding a two-page Power BI dashboard
- **Platform engineering:** Terraform with remote state; Azure DevOps CI (16 pytest tests, Terraform validate/plan) and a separate CD with saved-plan artifact, approval gate, apply and smoke validation; workload identity federation and RBAC (no long-lived secrets)

**Stack:** Azure Data Factory · Event Hubs · ADLS Gen2 · Synapse Serverless · Python · XGBoost · SHAP · Terraform · Azure DevOps · Power BI

*Uses historical data replayed to demonstrate event-driven design; it is not a live production feed.*

👉 [View the project](https://github.com/nabila-natasha/azure-transaction-risk-platform)

---

### 2. Mercedes-Benz Vehicle Analytics & ML Platform
**Snowflake analytics platform with ML and Power BI**

- RAW → SILVER → GOLD architecture on Snowflake, deployed from development to production with **GitHub Actions CI/CD**
- Combined Mercedes used-car data with the public **NHTSA** vehicle safety/recall API, transforming semi-structured responses into analytical datasets
- Dimensional **fact constellation** (conformed vehicle dimension shared by UK resale and US recall facts) with **Dynamic Tables** for auto-refreshing Gold facts
- **Random Forest** regression on ~370 configuration features to predict manufacturing test-bench time: **48% lower MAE** than a naive baseline, using cross-validation and RandomizedSearchCV
- Three Power BI dashboards (market/resale, manufacturing quality & ML, vehicle safety); fixed a many-to-many join that inflated safety counts

**Stack:** Snowflake · Dynamic Tables · Python · scikit-learn · GitHub Actions · Power BI · DAX

👉 [View the project](https://github.com/nabila-natasha/mercedes-snowflake-analytics)

---

### 3. Healthcare Public Health Surveillance & Risk Analytics Lakehouse
**Azure lakehouse with streaming, batch, ML and Power BI (public and synthetic data only)**

- **Streaming:** archived CDC COVID-19 surveillance data replayed through **Azure Event Hubs** (Kafka protocol) to a Python consumer with validation, deduplication and a **quarantine path** for malformed events
- **Batch:** paginated **openFDA REST API** ingestion with Azure Data Factory (4,000 unique adverse-event reports validated, zero duplicate IDs)
- **Medallion lakehouse** on ADLS Gen2 with Parquet datasets across RAW, Bronze, Silver and Gold
- **Serving:** five Synapse Serverless SQL views feeding three Power BI dashboards (CDC surveillance, openFDA adverse events, ML risk and anomaly analytics)
- **ML:** XGBoost seriousness classifier with explicit leakage controls (ROC-AUC 0.88 on a 200-row holdout), Isolation Forest anomaly screening, SHAP explainability and MLflow tracking in Databricks
- **Engineering:** 26 pytest tests, GitHub Actions CI, architecture decision records, security and governance documentation, and a Terraform foundation

**Stack:** Azure Data Factory · Event Hubs (Kafka) · ADLS Gen2 · Synapse Serverless · Databricks · XGBoost · MLflow · GitHub Actions · Power BI

*No PHI is used. The repository documents its limitations, including the Databricks Free Edition handoff and that Terraform is a foundation, not a full environment definition.*

👉 [View the project](https://github.com/nabila-natasha/healthcare-public-health-lakehouse)

---

### 4. Volve Oil & Gas Data Platform
**Snowflake analytics on real production data and external market data**

```text
Volve production + EIA Brent API + FX API
        ↓ Python / JSON ingestion
Snowflake Bronze → VARIANT / FLATTEN → Silver
        ↓ Dynamic Tables
Gold analytical layer → Power BI
```

- Production decline, water-cut trends, choke / wellhead pressure relationships and downtime analysis
- Brent-benchmarked production value, well value ranking and Brent price scenario analysis

**Stack:** Snowflake · Python · REST APIs · Dynamic Tables · Power BI

👉 [View the project](https://github.com/nabila-natasha/volve-snowflake-data-platform)

---

## 🛠️ Technical Skills

| Area | Skills |
| --- | --- |
| **Languages & processing** | SQL (T-SQL, Snowflake SQL), Python, PySpark, Pandas, NumPy, Parquet, JSON, REST APIs |
| **Data engineering** | ETL/ELT, batch and streaming pipelines, Medallion architecture, data integration, data quality and validation, deduplication, data lineage |
| **Cloud & platforms** | Azure (ADLS Gen2, Data Factory, Event Hubs, Synapse Serverless, Databricks, Entra ID / RBAC), Snowflake, SQL Server, PostgreSQL, Kafka protocol |
| **BI & modelling** | Power BI, DAX, semantic models, row-level security, star schema, fact constellation |
| **DevOps & IaC** | Git, GitHub Actions, Azure DevOps Pipelines, Terraform, pytest, workload identity federation |
| **Machine learning** | scikit-learn, XGBoost, Isolation Forest, SHAP, MLflow, feature engineering, model evaluation |

---

## 📚 Currently Learning

- **Machine Learning Zoomcamp 2026** (DataTalks.Club)
- **AWS Certified Cloud Practitioner** (starting October 2026)
- Production patterns for data platforms: monitoring, model versioning and data contracts

---

## 📫 Connect with me

- LinkedIn: [linkedin.com/in/nabilanatashaothman](https://www.linkedin.com/in/nabilanatashaothman)
- Email: nabilaothman.work@gmail.com
