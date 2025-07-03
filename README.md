# Netflix Streaming Pipeline

Designed a Netflix streaming data pipeline which implements a medallion architecture (Bronze → Silver → Gold) using Azure Data Lake and Databricks Delta Live Tables (DLT) to process, transform, and serve data for analytics and reporting. It follows modern data engineering best practices with a Lakehouse approach.

## Architecture

![Project Architecture](https://github.com/user-attachments/assets/0a3a64cf-8b28-4486-9ed9-d259ff8ee57f)


## Project description
### Bronze Table
Developed a bronze table(which contains data in raw format) by ingesting data into Azure Data Lake Storage using Azure Data Factory.<br>
* Purpose: Ingest raw, unprocessed data from various sources.<br>
* Sources:<br>
  * Files from cloud storage (Azure Blob): Data is incrementally loaded using Autoloaders.<br>
  * APIs: Data from web(Github account) is ingested to the bronze table using ADF pipeline.<br>
* Processing Type: Incremental data loads.<br>
* Storage: Data is ingested into a Data Lake in its original format.<br>


<img width="959" alt="adf_pipeline" src="https://github.com/user-attachments/assets/b598a329-b885-42b0-b537-96f649aa3541" />

    ADF pipeline

<img width="953" alt="storage account overview" src="https://github.com/user-attachments/assets/e496c0e9-e0a6-4625-95e8-65dedcdb82ed" />
               
    Overview of storage account

### Silver Table(transformed data)
* Purpose: Clean and enrich data to make it query-ready.
* Transformations Include:
  * Data cleaning and deduplication
  * Type casting and formatting
  * Applying business rules
* Tool Used: Pyspark in Azure Databricks
* Storage: Transformed data is written back to the Data Lake in Delta format.<br>

<img width="959" alt="silver container after running the pipeline" src="https://github.com/user-attachments/assets/633266dc-0c9b-43a5-9175-d48bd604d3b4" /><br>
                  
    Silver container after running the pipeline
  <br>

### Gold Table(Serving data)
* Purpose: Provide aggregated and business-ready data for analytics and reporting.
* Processing Includes:
  * Data aggregation and summarization
  * Business KPIs computation
  * Dimensional modeling (facts and dimensions)
* Storage: Clean, ready-to-use data stored in Delta Tables in the Data Lake.
* Use Case: Consumed by downstream tools like:
  * Azure Synapse Analytics.
  * Power BI Dashboards.

<img width="959" alt="gold_dlt2" src="https://github.com/user-attachments/assets/035f2f4a-55ec-48de-8da8-c990ee8e12a6" /><br>

    DELTA LIVE TABLE

<img width="959" alt="workflow 2 success" src="https://github.com/user-attachments/assets/0b5a1fb2-e987-40ad-a145-7cd48b724084" />

 



