# dbt-project

A “complete E2E dbt Cloud” demo integrating Snowflake, GitHub, and Power BI. This repo illustrates how to build and deploy a data transformation pipeline using dbt in a production-style workflow.



**Architecture & Components**

Here’s a high-level view of how pieces fit together:
- GitHub — hosts the repository, version control, PR workflows, and triggers to dbt Cloud
- dbt Cloud — runs transformations, snapshots, tests, and deploys the models
- Snowflake — serves as the underlying data warehouse (raw, staging, final tables)
- Power BI — connects to the final models to build dashboards and visualizations

The pipeline flows roughly like this:
- Raw data is loaded (e.g. via seeds or via external ingestion into Snowflake)
- dbt models transform raw into staging and then to final models
- Snapshots capture slowly changing dimensions
- Tests enforce data quality
- Power BI visualizes the final model outputs

**Repository Layout**

Here’s how this repo is organized:
```sql
/
├─ analyses/        # dbt “analysis” queries or ad hoc SQL  
├─ macros/           # dbt macro definitions  
├─ models/
│   └─ customer_rev/  # models, staging, marts related to customer revenue  
├─ seeds/             # CSV files to load via dbt seed  
├─ snapshots/         # snapshot definitions for slowly changing dimensions  
├─ tests/             # custom tests (if any)  
├─ dbt_project.yml    # core dbt project configuration  
├─ README.md          # (this file)  
└─ .gitignore  

```

Key points:
- models/ is the heart of the transformations
- snapshots/ shows how to version dimension changes over time
- seeds/ is useful for static reference data
- macros/ contains reusable logic, SQL snippets, or utility functions


<img width="932" height="832" alt="Screenshot 2025-09-24 at 3 55 33 PM" src="https://github.com/user-attachments/assets/3b1906a8-7a80-4f00-b1e7-284885a2818f" />

