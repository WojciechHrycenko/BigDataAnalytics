# US Flight Delay & Cancellation Analysis (2019-2023)

![Project Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Course](https://img.shields.io/badge/Course-Big%20Data%20Analytics-blue)
![Tools](https://img.shields.io/badge/Tools-Databricks%20%7C%20Power%20BI-green)

## Overview

This project is a comprehensive Big Data analysis of US domestic flight trends, delays, and cancellations over a 5-year period (2019-2023). Developed for the **Big Data Analytics** course, the solution utilizes **Databricks** for ETL (Extract, Transform, Load) processes and **Power BI** for interactive data visualization and risk assessment.

The goal is to provide actionable insights into airport performance, airline reliability, and to calculate flight risks for travelers.

## Team Members

* **Aleksandra Szpakowska**
* **Cezary Kuźmowicz**
* **Wojciech Hrycenko**

---

## Data Source

The dataset used for this analysis is sourced from Kaggle:
* **Dataset:** [Flight Delay and Cancellation Dataset (2019-2023)](https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023?select=dictionary.html)
* **Content:** Millions of flight records including timestamps, carriers, origin/destination airports, and delay/cancellation reasons.

---

## Tech Stack & Workflow

### 1. Big Data Processing (Databricks)
We utilize Databricks (PySpark/SQL) for high-volume data processing and preparation.
* **Data Cleaning:** Handling missing values, filtering anomalies, and standardizing timestamp formats for accurate time-series analysis.
* **Data Enrichment:** Performing `JOIN` operations to merge the main flight ledger with dictionary datasets (Airline Codes and Airport Codes).
* **Aggregation:** Computing key performance metrics (KPIs) such as delay ratios, cancellation percentages, and average delay times per carrier/route.

### 2. Visualization & Intelligence (Power BI)
The processed data is consumed by Power BI to create an interactive dashboard featuring the following insights:

#### Dashboard Features
* **Airport Performance Ranking:**
    * **Top 5 Worst Airports:** Ranking based on the highest percentage of problematic flights.
    * **Top 5 Best Airports:** Ranking of the most reliable hubs.
* **Geospatial Reliability Map:**
    * Interactive map of the USA visualizing airport reliability (color-coded indicators for delay frequency).
* **Route Analysis:**
    * Ranking of the Top 5 most frequently delayed specific connections (Origin -> Destination).
* **Airline Leaderboard:**
    * Comparative analysis of airline reliability (Best vs. Worst performing carriers).
* **Flight Risk Assessment Model:**
    * A logic-based model that categorizes a specific flight choice into **Low**, **Mid**, or **High Risk**.
    * *Inputs:* Origin, Destination, Time of year, Airline history.

#### Interactive Filters
The dashboard allows users to drill down using:
* **Airline Carrier**
* **Origin & Destination**
* **Flight Distance Categories** (Short / Medium / Long / Ultra-Long)
* **Date Range**