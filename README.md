# dbt Learning Lab

A hands-on project built while completing the **dbt Fundamentals** certification, using dbt Cloud connected to a Snowflake data platform via GitHub. This repo documents my journey learning the core concepts of analytics engineering with dbt — from building models to testing data quality and understanding deployment workflows.

## About This Project

This project uses the classic `jaffle_shop` sample dataset to demonstrate a typical dbt workflow: transforming raw data into clean, tested, and documented models ready for analytics.

**Tech stack:**
- **dbt Cloud** — development, orchestration, and job scheduling
- **Snowflake** — data platform
- **GitHub** — version control, connected via GitHub App integration
- **YAML** — source and test configuration

## Project Structure

```
dbt-learning-lab/
├── models/            # staging models for customers and orders, with source configs and docs
├── analyses/
├── macros/
├── seeds/
├── snapshots/
├── tests/             # data tests on sources
├── dbt_project.yml    # project-level materialization config
├── dbt fundamentals.pdf  # personal learning notes from the certification course
└── README.md
```

## Key Concepts Practiced

- **Sources** — declaring pre-existing raw tables with `source()`, including `database`/`schema`/`identifier` mapping
- **Staging models** — light transformations (renaming, type casting) mapped 1:1 to source tables
- **Materializations** — configuring models as `view` vs `table` via `config()` blocks or `dbt_project.yml`
- **Data tests** — `unique`, `not_null`, and `accepted_values` tests applied to both sources and models
- **Source freshness** — monitoring how up-to-date raw data is using `warn_after` / `error_after` thresholds
- **DAG (Directed Acyclic Graph)** — understanding model lineage and dependency order (`ref()` vs `source()`)
- **dbt build** — running models and tests together in DAG order, with automatic downstream skipping on failure
- **Environments & Jobs** — separating development and production environments, and scheduling automated jobs in dbt Cloud

## Common Commands

```bash
dbt run                              # build all models
dbt run --select my_first_dbt_model  # build a specific model
dbt test                             # run all data tests
dbt test --select source:*           # run tests on sources only
dbt build                            # run + test models in DAG order
dbt source freshness                 # check freshness of source data
```

## Progress Log

This repo was built incrementally while working through the course, commit by commit:

- Initial project scaffold (`analyses`, `macros`, `models`, `seeds`, `snapshots`, `tests`)
- Added two staging models for `customers` and `orders`, and refactored materialization config in `dbt_project.yml`
- Added data tests on sources
- Added documentation and doc blocks on YAML files
- Added personal notes (`dbt fundamentals.pdf`) capturing key takeaways from each course section

## What I Learned

Working through this project helped me understand not just *how* to write dbt models, but *why* dbt structures projects the way it does — separating staging, intermediate, and mart layers; using `ref()` and `source()` to build a reliable dependency graph; and using tests and freshness checks to catch data quality issues before they reach stakeholders.

## Certification

<img width="400" height="400" alt="dbt" src="https://github.com/user-attachments/assets/efb57df0-ad32-49c6-abc8-aa4e3020cbf2" />

----

https://credentials.getdbt.com/69d0b05d-5ae1-46b3-b78b-794ef9821dd8#acc.SUD9AXZw

