# data-dl

**Data engineer focused on healthcare data quality.** Production ETL in Python, SQL and R with dbt and
Apache Airflow; validation, reconciliation and audit trails built into every stage; pipelines that stop
loudly instead of publishing quietly wrong numbers.

Every repository here is a self-contained build you can run: synthetic or public data, a generator or
harvester included, automated tests in CI, and a page or sample run that shows the output.

## Healthcare data quality

| Project | What it does | Proof |
|---|---|---|
| [**population-health-pipeline**](https://github.com/data-dl/population-health-pipeline) | Five weekly healthcare supplier feeds (roster, screenings, labs, appointments, pharmacy claims) governed by data contracts with 63 rules, loaded into an audited DuckDB warehouse, then nine dbt quality measures with equity reporting and a de-identified release behind a 12-check leak gate. Runs locally or on Apache Airflow. | 5,000 synthetic patients; all 269 planted defects caught; every measure matches an independent calculation at every clinic; 84 tests on Linux and Windows. [Live report](https://data-dl.github.io/population-health-pipeline/) |
| [**directory-qa-pipeline**](https://github.com/data-dl/directory-qa-pipeline) | A controlled monthly data-quality cycle for a healthcare provider directory on a legacy single-file database: a 22-rule registry with severities, duplicate classification with a human decision log, verified backups, and a READY / NOT READY gate before anything is published. | 25,000 synthetic listings with 20 kinds of planted defect; 243 duplicates removed with zero false deletions; 69 tests. [Sample run](https://github.com/data-dl/directory-qa-pipeline/blob/main/docs/sample_run/summary.md) |

## Other data projects

| Project | What it does | Data |
|---|---|---|
| [**northstar-finance**](https://github.com/data-dl/northstar-finance) | Eight raw export formats (bank CSVs and statement PDFs, card activity, order histories, payment statements, a brokerage file, alert emails) reconciled into four dashboards behind twenty integrity checks. | Generated synthetic household. [Live demo](https://data-dl.github.io/northstar-finance/) |
| [**journal-analytics-pipeline**](https://github.com/data-dl/journal-analytics-pipeline) | A year of tables of contents for 27 peer-reviewed journals, harvested from OpenAlex, Crossref and PubMed into one searchable page with citations and field-weighted impact. | Public bibliographic data. [Live page](https://data-dl.github.io/journal-analytics-pipeline/) |
| [**season-ahead**](https://github.com/data-dl/season-ahead) | Every forthcoming title from five university presses, harvested from five very different catalogue sites into one searchable page. | Public catalogue data. [Live page](https://data-dl.github.io/season-ahead/) |

## How these are built

- **Inputs are untrusted.** Every feed is checked against a contract; provable fixes are applied and logged,
  ambiguous rows are held for a person, never guessed.
- **Every run leaves evidence.** Row counts reconcile from raw file to output, and each run writes a
  manifest, a summary and a file for every finding.
- **Correctness is measured.** Synthetic data comes with planted defects and an answer key, and CI grades
  each run against it.
- **Safe by default.** Dry runs first, verified backups, and nothing published until the blocking checks pass.

**Stack:** Python · SQL · R · dbt · Apache Airflow · DuckDB · PostgreSQL · SQLite · MongoDB · pytest · GitHub Actions
