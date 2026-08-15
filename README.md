# SBDL — Smart Banking Data Lake

![CI](https://github.com/Kenantkurt/sbdl/actions/workflows/ci.yml/badge.svg)

Guided capstone project from *Apache Spark Programming in Python* (Prashant Pandey).
Reads account, party and address data from Hive, joins them into a single
self-contained message per account, and prepares it for a Kafka sink.

## Project structure

| Path | What it is |
|---|---|
| `sbdl_main.py` | Entry point — takes environment and load date as arguments |
| `lib/` | Shared code: Spark session, config loader, logger |
| `conf/` | Per-environment settings (LOCAL / QA / PROD) |
| `test_data/` | Small CSV samples so tests can run without a cluster |
| `test_pytest_sbdl.py` | Unit tests |
| `sbdl_submit.sh` | spark-submit command for deployment |

## Setup

Requires Python 3.11 and Java 17.

```bash
pipenv install
```

## Run

```bash
pipenv run python sbdl_main.py LOCAL 2022-08-02
```

## Tests

```bash
pipenv run pytest -v
```

## CI

Every push runs the tests on a clean runner via GitHub Actions:
checkout → set up Python 3.11 and Java 17 → install locked dependencies → `pytest`.

The check is required on `main`, so a pull request cannot be merged while it is red.