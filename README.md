# TfNSW Seasonal Patronage Analysis

## Project Overview

This project analyses seasonal public transport patronage in New South Wales using Transport for NSW (TfNSW) Opal trips data.

The analysis examines patronage patterns from **2019 to 2023** across four major transport modes — Bus, Rail Network, Ferry and Light Rail — and investigates how travel demand varies across different passenger groups.

The project was completed as part of a **Graduate Certificate in Data Analytics** and was designed as a client-style data analytics project for Transport for NSW.

## Client

**Transport for NSW (TfNSW)** is the NSW Government agency responsible for the strategic planning and management of the state's transport network.

The analysis was designed to provide insights that could support operational planning by identifying recurring seasonal patterns in public transport demand.

## Objective

The primary objective was to identify **seasonal patronage patterns** across public transport modes and passenger groups.

The analysis aimed to answer:

* Which months experience the highest levels of patronage?
* How does seasonal demand differ between transport modes?
* Which passenger groups contribute most to seasonal demand?
* Are observed peaks recurring patterns rather than isolated events?
* How could these patterns potentially inform operational planning?

## Dataset

The analysis uses the **Opal Trips - All Modes** dataset published through the TfNSW Open Data Hub.

The original dataset covers **2016–2023**. The analysis was restricted to **2019–2023** to provide a consistent timeframe incorporating the modern public transport network, including Sydney Metro and Light Rail services.

The final analytical dataset contains **960 rows and five variables**:

| Variable    | Description                 |
| ----------- | --------------------------- |
| Year        | Year of travel              |
| Month       | Month of travel             |
| Travel Type | Public transport mode       |
| Opal Card   | Passenger demographic group |
| Total Trips | Number of recorded trips    |

## Data Preparation

Several data cleaning and transformation steps were performed using R.

### 1. Date transformation

The original `Year_Month` field was separated into individual `Year` and `Month` variables.

This allowed monthly patronage to be compared across multiple years and made it possible to identify recurring seasonal patterns.

### 2. Transport mode categorisation

The original transport categories were consolidated into four broader groups:

* Bus
* Rail Network
* Ferry
* Light Rail

Sydney Trains and Sydney Metro were combined into the **Rail Network** category.

### 3. Passenger group categorisation

The original Opal card categories were consolidated into four demographic groups:

* Adult
* Student
* Senior
* Other

This reduced categorical complexity and allowed patronage patterns to be compared between major passenger groups.

### 4. Aggregation

After categorisation, trip counts were grouped by:

`Year + Month + Travel Type + Opal Card`

The resulting dataset was then used to calculate average monthly patronage across the five-year period.

## Analysis

The analysis calculated the average number of trips for each combination of:

* Month
* Transport mode
* Passenger group

A percentage-of-year measure was also calculated to normalise patronage across transport modes with substantially different overall passenger volumes.

This enabled seasonal patterns to be compared between modes without relying solely on raw trip counts.

## Key Findings

The analysis identified several notable seasonal patterns.

### Ferry

Ferry services displayed particularly strong seasonal variation around **December and January**.

The analysis identified:

* January Student patronage representing approximately **15%** of annual average monthly Student trips
* December Other patronage representing approximately **13%**
* January Adult patronage representing approximately **12%**

These results suggest that Ferry demand has a stronger summer seasonal pattern than the other transport modes analysed.

### Bus and Rail

Bus and Rail Network patronage showed comparatively consistent demand throughout the year, although several monthly peaks were identified.

Examples include:

* March Student Bus patronage: approximately **12%**
* February Student Bus patronage: approximately **11%**
* March Student Rail Network patronage: approximately **11%**

### Passenger Groups

The analysis found that the **Student** category accounted for substantial patronage across the transport network.

This is particularly visible in the Bus, Rail Network and Light Rail results.

## Visualisation

A faceted heatmap was created using `ggplot2` to compare seasonal patronage across transport modes and passenger groups.

The visualisation uses:

* **Month** on the x-axis
* **Transport mode** on the y-axis
* **Percentage of annual demand** represented through colour intensity
* Separate panels for each passenger group

A second output identified the **Top 10 operational peaks** based on the percentage of annual demand.

Together, these outputs provide both a visual overview of seasonal patterns and a numerical summary of the largest monthly concentrations.

## Recommendations

Based on the observed seasonal patterns, the analysis suggests that TfNSW could consider seasonal demand when planning transport capacity and service frequency.

In particular:

* Ferry services could be assessed for additional capacity during the December–January period.
* Seasonal demand patterns could be incorporated into timetable and resource planning.
* Bus and Rail services could be monitored for recurring Student and holiday-related peaks.
* Further analysis incorporating major events, weather and time-of-day data could help distinguish normal seasonal demand from event-driven demand.

These recommendations would require further operational and contextual data before implementation.

## Limitations

Several limitations should be considered when interpreting the results.

* The dataset provides **monthly totals**, so it cannot identify specific times of day when demand peaks.
* External factors such as weather, major events and holidays were not included.
* The **2020–2021 COVID-19 lockdown period** created significant disruption to normal patronage patterns.
* The analysis uses five years of data, meaning individual years may contain unusual events that influence averages.
* Percentage-of-year calculations allow comparison between modes, but they do not measure absolute passenger demand.

Further analysis using daily or hourly data, event information and weather data could provide a more detailed understanding of the causes behind the observed patterns.

## Tools & Technologies

* **R**
* **RStudio** 
* **dplyr** — data manipulation
* **tidyr** — data transformation
* **stringr** — text-based categorisation
* **ggplot2** — data visualisation
* **knitr / kableExtra** — table generation

## Project Deliverables

The project consisted of:

* Data cleaning and transformation
* Exploratory data analysis
* Seasonal trend analysis
* Data visualisation
* Client report
* Class presentation

## What This Project Demonstrates

This project demonstrates practical skills in:

* Data cleaning and transformation
* Data aggregation
* Categorical data manipulation
* Exploratory data analysis
* Statistical summarisation
* Data visualisation
* Interpreting business patterns from data
* Translating analytical findings into client-focused recommendations

## Data Source

Transport for NSW. *Opal Trips - All Modes*. NSW Government Open Data Hub.

https://opendata.transport.nsw.gov.au/dataset/opal-trips-all-modes
