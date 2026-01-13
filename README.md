# US Flight Delay & Cancellation Analysis (2019-2023)

![Project Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Course](https://img.shields.io/badge/Course-Big%20Data%20Analytics-blue)
![Tools](https://img.shields.io/badge/Tools-Databricks%20%7C%20Power%20BI-green)

## Overview

This project is a comprehensive Big Data analysis of US domestic flight trends, delays, and cancellations over a 5-year period (2019-2023). Developed for the **Big Data Analytics** course, the solution utilizes **Databricks** for ETL (Extract, Transform, Load) processes and **Power BI** for interactive data visualization and risk assessment.

The goal was to provide actionable insights into airport performance, airline reliability, and to calculate flight risks for travelers based on historical data.

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
We utilized Databricks (PySpark/SQL) implementing a **Medallion Architecture** (Bronze, Silver, Gold layers) for structured data processing:

* **Bronze Layer (Raw):** * Automated ingestion of data directly from Kaggle via the **Kaggle API**.
    * Secure authentication using `kaggle.json` tokens.
    * Storage of raw CSV archives in the file system.
* **Silver Layer (Cleaned):**
    * Handling missing values and filtering anomalies.
    * Standardizing timestamp formats (e.g., converting '945' to '09:45').
    * Enrichment: Performing `JOIN` operations to merge flight data with dictionary datasets (Airline Codes and Airport Geolocation).
* **Gold Layer (Aggregated):**
    * Computing Business KPIs: Delay ratios, cancellation percentages, and problem rates.
    * Route Risk Calculation: Utilizing Haversine formula for distance and historical delay probability.

### 2. Visualization & Intelligence (Power BI)
The processed Gold data is consumed by Power BI to create an interactive dashboard featuring the following insights:

#### Dashboard Features
* **Airport Performance Ranking:**
    * **Top 5 Worst Airports:** Ranking based on the highest percentage of problematic flights (delays > 15m + cancellations).
    * **Top 5 Best Airports:** Ranking of the most reliable hubs.
* **Geospatial Reliability Map:**
    * Interactive map of the USA visualizing airport reliability (color-coded indicators based on geolocation data).
* **Route Analysis:**
    * Ranking of the Top 5 most frequently delayed specific connections (Origin -> Destination).
* **Airline Leaderboard:**
    * Comparative analysis of airline reliability (Best vs. Worst performing carriers based on arrival delays).
* **Flight Risk Assessment Model:**
    * A logic-based model that categorizes a specific flight choice into **Low**, **Medium**, or **High Risk**.
    * *Logic:* Based on historical delay probability (e.g., >30% delay rate = High Risk).

#### Interactive Filters
The dashboard allows users to drill down using:
* **Airline Carrier**
* **Origin & Destination**
* **Flight Distance** (Calculated via Haversine formula)
* **Date Range**
