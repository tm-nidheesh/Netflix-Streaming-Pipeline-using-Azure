# Netflix-Azure-Data-Engineering-Pipeline

## Architecture
Designed a Netflix streaming data pipeline which implements a medallion architecture (Bronze → Silver → Gold) using Azure Data Lake and Databricks Delta Live Tables (DLT) to process, transform, and serve data for analytics and reporting. It follows modern data engineering best practices with a Lakehouse approach.

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
<br>

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



