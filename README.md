# data-dl

Data engineer — production ETL pipelines (R, dbt, Airflow, Postgres) and healthcare data
quality. The repositories here are self-contained builds over real problems: each ingests messy exports from several sources, reconciles them, and ends in a
single-file page you can open with no server.

| Repository | What it is | Data |
|---|---|---|
| [**northstar-finance**](https://github.com/data-dl/northstar-finance) | A personal-finance pipeline: eight raw export formats in, four reconciled dashboards out, gated by twenty integrity checks. Card spending in near-real time from issuer alert emails. | Runs end to end on a **generated synthetic household**; the generator is part of the repo. [Live demo](https://data-dl.github.io/northstar-finance/) |
| [**directory-qa-pipeline**](https://github.com/data-dl/directory-qa-pipeline) | A controlled monthly data-quality cycle for a healthcare provider directory on a legacy single-file database, with a swappable SQLite/Access backend. | Synthetic, with planted defects and an answer key. |
| [**season-ahead**](https://github.com/data-dl/season-ahead) | Every forthcoming title from five university presses, harvested from five very different catalogue sites into one searchable page with credited blurbs and lead titles ranked within press and month. | Public catalogue data. [Live page](https://data-dl.github.io/season-ahead/) |
| [**journal-radar**](https://github.com/data-dl/journal-radar) | Twelve months of 27 journals' tables of contents from OpenAlex, Crossref and PubMed, with citations, field-weighted impact and lead-article detection. | Public bibliographic data. [Live page](https://data-dl.github.io/journal-radar/) |
| [**listening-machine**](https://github.com/data-dl/listening-machine) | Fifteen years of Spotify history read as behaviour, in local time, with a detector for the days the account was not mine. | My own listening data, by choice. [Live page](https://data-dl.github.io/listening-machine/) |

Common threads: exports are treated as untrusted inputs (overlaps deduped, control totals
checked, ambiguous rows quarantined rather than dropped), every invented default is written
down, and the numbers are wrong loudly rather than quietly.
