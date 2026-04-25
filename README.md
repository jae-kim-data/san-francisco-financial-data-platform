# San Francisco Financial Data Ecosystem 

## Overview

Developing a data pipeline leveraging weekly public spending data from the San Francisco Controller’s Office to support reliable and timely financial reporting.

This system will automatically structure new data, preserve historical versions, and identify updates to previously reported figures. A desktop interface enables users to easily select reporting periods, streamlining Power BI refresh and analysis.


## Why is this valuable/necessary?

Financial spending and revenue data that is released on a recurring basis often include updates or corrections to prior periods, and depending on the organization, may require custom classification rules to support analysis. Without a structured process/system design, this can lead to increasingly inconsistent reporting that accumulates, manual rework, and limited visibility into historical changes, as well as growing delays in data preparation that are hard to predict. 

This project creates a reliable way to repeatedly:
Maintain spending data in a consistent, comfortable refresh workflow, even for a daily cadence if necessary.
Track and surface changes made to previously reported figures
Reduce the manual effort and errors in preparing data for analysis
Deliver fast, trustworthy Power BI reporting 

The goal is to enable finance professionals to spend less time waiting for data preparation and more time analyzing it. This is made achievable by allowing for focus on root causes, trends, and decision-making. This is a system designed with a thoughtful and robust backend, while being mindful that its ultimate goal is to be intuitive and immediately accessible to business users without requiring technical knowledge of the backend itself.  


## Key Approaches (Initial Ideas)

#### 𖧹 Self-Managing Dim Tables
The system will perform an initial scan of the received input dataset. When there is an unseen value to add to the existing dim table, the system will ask the user for preference on whether they would like to save the value under the assignment its identified alone. Depending on the case, the system will also give the user the ability to assign their own custom value, to then store the user's input assignment into the dim table. 

#### 𖧹 Automated Cleaned / Enriched Data File Generation
The system will automatically separate the received master dataset from the City of San Francisco into smaller files, separated by Month-Year. This separation idea is included in this system design brainstorm stage because I intend to enrich this given dataset with other data that I may be able to link based on certain fields. Keeping the files separated into smaller timeframe based chunks will allow for me to enrich these datasets as smaller parquet files rather than processing one master dataframe, which will also be beneficial for the user to download the data based on the range of dates they need, rather than waiting for the full master dataframe to be ingested, transformed and filtered. 

#### 𖧹 User Interface App 
After the data pipeline stores the cleaned datasets, the user will be able to launch a separate user interface desktop application to pull the stored data together into the desired format for Power BI refresh, specifying the date range that they would like to pull information for. 

#### 𖧹 Power BI Dashboard


## Planned Architecture (Diagram to be Added)

1. Data Ingestion Stage

2. Data Transformation Stage

3. Naturally Accumulating Storage

4. Change Detection Stage

5. User Interface System

6. Reporting / Visualization Platform


## Planned Scope Timeline

Version 1 Series: A Python pipeline will be the main processing engine, storing cleaned partitioned Parquet files as well as an Excel audit/correction log made for the non-technical audience, then having a user interface app that will allow the user to prepare the Power BI backend dataset based on the target date range. 

Version 2 Series: Microsoft SQL Server Management Studio (SSMS) will be introduced as the data warehouse layer, loading cleaned data into dimension tables and a central fact table. Transformations will be implemented using CTEs. The Power BI dashboard will take the curated warehouse-style views as the data source. 
