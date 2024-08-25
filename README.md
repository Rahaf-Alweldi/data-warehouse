# Data Warehouse Project

This project showcases a comprehensive Data Warehouse project, focusing on data ingestion, transformation, and analysis. The project leverages cloud-based solutions and modern tools to create a scalable and efficient data warehouse.

## Agenda

1. [Project Overview](#project-overview)
2. [Project Architecture](#project-architecture)
3. [About Data](#about-data)
4. [Business Requirements](#business-requirements)
5. [Project Infrastructure](#project-infrastructure)

---
<br></br>
## Project Overview
This project entails typical Analytical Data Engineering, involving the ingestion of data from various sources and its loading into the Snowflake data warehouse. 
Within the warehouse, after undergoing a series of data transformation processes, the data is prepared for Business Intelligence (BI) usage.
The BI tool Metabase connects to the data warehouse to generate diverse dashboards and reports.

### Project Structure
1. **Data Ingestion:** Utilizes AWS Lambda and Airbyte for automating the ingestion of raw data from various sources into the data warehouse.

2. **Data Transformation:** Implements Snowflake for transforming the ingested data. The transformation scripts clean, aggregate, and structure the data, preparing it for detailed analysis.

3. **Data Analysis:** Uses Metabase to create visualizations and dashboards for analyzing the transformed data.


### Technologies Used
- **AWS Lambda:** Enables serverless data ingestion, automating the ETL processes without the need for managing servers.
- **Airbyte:** A data integration tool used for extracting data from various sources and loading it into Snowflake.
- **Snowflake:** A cloud-based data warehousing solution used for data storage and transformation.
- **Metabase:** An open-source business intelligence tool used for creating dashboards and visualizing data.

---
<br></br>
## Project Architecture
![image](https://github.com/user-attachments/assets/d8ae5ffd-3e50-4610-8475-2a6e83bcfb62)


---
<br></br>
## About Data
The dataset utilized originates from TPCDS, a well-known dataset designed for database testing, with a specific emphasis on Retail Sales. It encompasses sales records from both websites and catalogs, 
along with detailed information on inventory levels for each item within every warehouse. Moreover, it incorporates 15 dimensional tables containing valuable information about customers, warehouses, 
items, and more. The dataset is divided into two parts:

- **RDS:** All tables, except for the inventory tables, are stored in the Postgres DB in AWS RDS. These tables are refreshed every day with the latest sales data, requiring daily ETL processes.
- **S3 Bucket:** The single Inventory table is stored in a S3 bucket. Each day, a new file containing the most recent data is deposited into the S3 bucket. Note: The inventory table typically registers data at the end of each week, leading to one entry per item per warehouse on a weekly basis.

<img src="https://github.com/user-attachments/assets/035494cb-a7a1-4ac2-b618-de5057cc80c5" style="width:400px;"/>

---
<br></br>
## Business Requirements

1. Determine the top and bottom-performing items of the week by analyzing sales amounts and quantities.
2. Show items with low inventory levels on a weekly basis.
3. Identify items with low stock levels, including their associated week and warehouse numbers, marked as "True".
4. Show the top products in every week.

---
<br></br>
## Project Infrastructure
In this project, the entire infrastructure is constructed in the cloud:

- **Servers:** Create several servers on the AWS cloud.
- **Tools:** Install various tools on these servers, including Airbyte for data ingestion, and Metabase as the BI tool for building dashboards.
- **Cloud Data Warehouse:** Create an account on Snowflake. Then, use Snowflake, the cloud data warehouse, to store data and perform data transformation.
- **AWS Lambda:** Use AWS Lambda, a serverless service, to ingest data from AWS data storage (S3).


### 1. Data Ingestion
![image](https://github.com/user-attachments/assets/b8678404-d844-44ad-9cfb-dc0434a698b4)
The first part of the project involves Data Ingestion. It entails connecting to two data sources: **the Postgres database** and **the AWS S3 bucket**. 
Utilizing Airbyte, establish a connection to the `raw_st` schema of the Postgres database on AWS RDS, and transfer all tables to the Snowflake data warehouse. 
In addition, leverage AWS Lambda to connect to the AWS S3 bucket and transfer the file named `inventory.csv` from the S3 bucket to the Snowflake data warehouse.

<br></br>
### 2. Data Transformation
![image](https://github.com/user-attachments/assets/a7d32f56-5f76-4545-bd82-d4a39f6eba86)
The next stage of the project focuses on data transformation within the Snowflake data warehouse. This involves reshaping tables from their original structure to the desired format. 
Throughout this phase, tasks include creating a data model, developing ETL scripts, and establishing a schedule for the data loading process.

<br></br>
### 3. Data Analysis
![image](https://github.com/user-attachments/assets/f1acfdfe-54bf-4ed5-98fa-ec739a5bc6cb)
In the last part of this project, establish a connection between the Snowflake data warehouse and the BI tool (Metabase). 
This connection allows for the creation and display of dashboards and reports in Metabase, utilizing the data stored in Snowflake.
