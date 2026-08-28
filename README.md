# Global Banking Data ETL Pipeline
### IBM Data Engineering Specialization - Portfolio Project

![ETL](https://img.shields.io/badge/ETL%20Pipeline-purple)
![Python](https://img.shields.io/badge/Python-blue)
![SQLite](https://img.shields.io/badge/SQLite-lightgrey)
![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-red)

---

## Table of Contents

- [Overview](#overview)
- [Project Objectives](#project-objectives)
- [Dataset](#dataset)
- [Tools & Technologies](#tools--technologies)
- [Methodology](#methodology)
- [Results](#results)
- [Key Performance Indicators](#key-performance-indicators)
- [Key Findings](#key-findings)
- [How to Run the Project](#how-to-run-the-project)
- [About This Project](#about-this-project)

---

## Overview

This project implements a complete Extract, Transform, Load (ETL) workflow in Python. It extracts the top 10 largest banks by market capitalization (USD) from an archived web source, transforms the values into GBP, EUR, and INR using a supplied exchange rate file, and loads the processed data into both CSV and SQLite database formats, with a full timestamped process log maintained throughout execution. The project was completed as part of the IBM Data Engineering Specialization.

---

## Project Objectives

- Extract market capitalization data from an archived web source
- Clean and structure the raw data into a pandas DataFrame
- Convert USD market capitalization into GBP, EUR, and INR
- Save transformed data into a CSV file and SQLite database
- Log all major steps using a structured log file (`code_log.txt`)
- Deliver a clean, reproducible ETL workflow

---

## Dataset

| Attribute | Detail |
|---|---|
| Source | Archived Wikipedia "By market capitalization" table |
| Scope | Top 10 largest banks by USD market cap |
| Supporting File | `exchange_rate.csv` (GBP, EUR, INR conversion rates) |
| Output Formats | CSV (`Largest_banks_data.csv`) and SQLite (`Banks.db`) |

---

## Tools & Technologies

| Category | Tools |
|---|---|
| Language | Python |
| Environment | Google Colab |
| Database | SQLite |
| Libraries | requests, BeautifulSoup (bs4), pandas, numpy, sqlite3, datetime |

---

## Methodology

**1. Extract**
Scraped the "By market capitalization" table from the archived Wikipedia page, cleaned the values, and extracted the top 10 largest banks by USD market cap.

**2. Transform**
Loaded exchange rates from `exchange_rate.csv`, calculated market capitalization in GBP, EUR, and INR, rounded transformed values to two decimal places, and reordered DataFrame columns to match project requirements.

**3. Load**
Saved the final DataFrame to `Largest_banks_data.csv` and loaded the processed data into `Banks.db` under the table name `Largest_banks`.

**4. Logging**
Wrote timestamped entries for every major step into `code_log.txt`, in the format `YYYY-MM-DD HH:MM:SS : <message>`, to maintain a complete audit trail of the pipeline run.

---

## Results

All screenshots in [`Results/`](./Results).

| # | Result | Screenshot |
|---|--------|------------|
| 1 | Extract phase - successful extraction of the market cap table and top 10 bank selection | ![Extract](Results/Extract.png) |
| 2 | Transform phase - DataFrame with GBP, EUR, and INR conversions applied | ![Transform](Results/Transform.png) |
| 3 | Save to CSV - confirms final DataFrame saved to `Largest_banks_data.csv` | ![Save CSV](Results/save_csv.png) |
| 4 | SQL query results - full table retrieval, average GBP market cap, top 5 bank names | ![Query Results](Results/queries_results.png) |
| 5 | Files generated - all output files, including CSV, SQLite database, and artifacts | ![Files Log](Results/files_log.png) |
| 6 | ETL process log - timestamped log contents from `code_log.txt` for each pipeline stage | ![ETL Log](Results/etl_process_log.png) |

---

## Key Performance Indicators

| KPI | Result |
|---|---|
| Banks Processed | Top 10 by market cap |
| Currencies Converted To | GBP, EUR, INR |
| Output Formats | 2 (CSV, SQLite) |
| Pipeline Stages Logged | 4 (Extract, Transform, Load, Logging) |

---

## Key Findings

- The pipeline reliably extracts and ranks the top 10 banks by USD market capitalization from a static archived source, making the output reproducible across runs.
- Currency conversion into GBP, EUR, and INR is applied consistently across all 10 banks, enabling multi-currency comparison from a single USD-based source table.
- Dual-format loading (CSV and SQLite) supports both lightweight file-based use and structured SQL querying of the same processed dataset.
- End-to-end timestamped logging gives full visibility into each pipeline stage, supporting debugging and auditability without needing to re-run the notebook.

---

## How to Run the Project

1. Open the notebook at `Notebook/world_top_banks.ipynb`.
2. Run all cells in Google Colab or Jupyter Notebook.
3. Ensure `exchange_rate.csv` is present in the Data directory.
4. The output CSV, database, and logs will be recreated automatically upon execution.

---

## About This Project

This ETL pipeline project was completed as part of the IBM Data Engineering Specialization. It has been structured, documented, and uploaded to GitHub as a portfolio project showcasing practical data engineering skills.

---
