# PortDataPipeline

A Python pipeline for ingesting, cleaning, and monitoring global port trade volume data from the IMF Portwatch dataset. Built for an economics research lab at UC San Diego.

---

## Overview

The original workflow involved manually downloading CSV files from IMF Portwatch and processing them by hand. This pipeline automates the full process — from data ingestion through anomaly detection — and surfaces results through an interactive Streamlit dashboard that became the team's primary monitoring tool.

---

## Repository Structure

```
PortDataPipeline/
│
└── PortData.ipynb     # Core pipeline: ingestion, cleaning, anomaly detection, visualization
```

---

## What It Does

### Data Ingestion
- Pulls trade volume data from IMF Portwatch CSV exports covering global port activity
- Handles ingestion from multiple files across ports and time periods
- Implements a daily refresh cycle to keep the dataset current without manual intervention

### Cleaning & Processing
- Standardizes column formats, date parsing, and port identifiers across inconsistent source files
- Forward-fills missing observations and handles gaps in port reporting
- Outputs a clean, analysis-ready DataFrame for downstream use

### Anomaly Detection
- Flags statistically unusual trade volume observations using rolling window statistics
- Detects both volume spikes and sudden drops relative to each port's historical baseline
- Anomalies are labeled and surfaced in the dashboard for researcher review

### Streamlit Dashboard
- Interactive monitoring tool built for the research team
- Visualizes trade volume time series by port and region
- Highlights flagged anomalies inline with the underlying data
- Replaced the team's previous manual CSV review process

---

## Data Source

**IMF Portwatch** — a real-time global port activity dataset maintained by the International Monetary Fund, tracking vessel calls and cargo throughput across hundreds of ports worldwide.

- Source: [https://portwatch.imf.org](https://portwatch.imf.org)
- Input format: CSV exports (one file per port / time slice)
- No API key required for CSV access

---

## Dependencies

```bash
pip install pandas numpy matplotlib streamlit
```

---

## About

Port data research pipeline built for an economics research lab at UC San Diego. The Streamlit dashboard is designed to be the team's live monitoring interface — run `streamlit run` against the output to launch it.
