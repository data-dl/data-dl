# data-dl

Data engineer — production ETL pipelines (R, dbt, Airflow, Postgres) and healthcare data
quality. The repositories here are self-contained builds over real problems: each ingests messy exports from several sources, reconciles them, and ends in a
single-file page you can open with no server.

## Featured projects

| Repository | What it is | Data |
|---|---|---|
| [**population-health-pipeline**](https://github.com/data-dl/population-health-pipeline) | Five synthetic healthcare supplier feeds governed by data contracts and loaded into an audited DuckDB warehouse, with dbt quality measures, equity reporting, Airflow-compatible orchestration, and a de-identified release protected by a leak gate. | A **synthetic network of 5,000 patients** with 269 planted defects and an answer key that CI grades every run against. [Live report](https://data-dl.github.io/population-health-pipeline/) |
| [**northstar-finance**](https://github.com/data-dl/northstar-finance) | A personal-finance pipeline: eight raw export formats in (credit-union CSVs and statement PDFs, card activity, order histories, Venmo statements, a brokerage file, issuer alert emails), four reconciled dashboards out, gated by twenty integrity checks. | Runs end to end on a **generated synthetic household**; the generator is part of the repo. [Live demo](https://data-dl.github.io/northstar-finance/) |
| [**season-ahead**](https://github.com/data-dl/season-ahead) | Every forthcoming title from five university presses, harvested from five very different catalogue sites into one searchable page with credited blurbs and lead titles ranked within press and month. | Public catalogue data. [Live page](https://data-dl.github.io/season-ahead/) |

Common threads: exports are treated as untrusted inputs (overlaps deduped, control totals
checked, ambiguous rows quarantined rather than dropped), every invented default is written
down, and the numbers are wrong loudly rather than quietly.
