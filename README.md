# Olympic_ADF_Project
Using Olympic created azure data pipeline end-to-end atchitechture which provides each and every steps of data engineering life-cycle, from data ingestion from multiple sources then moving those into raw layer and finally perform transformation based on business requirement and publishing data interms of reporting.

# Project Architechture:
![image](https://github.com/vinaytekkur/Olympic_ADF_Project/assets/156997918/f82d5c13-189d-4579-a70c-ef551e3d2c25)

**Azure Services Used:**
1) Azure Data Factory
2) Azure Gen 2 Blob Storage
3) Azure Key Vault
4) Azure Synapse Dedicated SQL pool
5) Logic Apps
6) SQL Server

**Project describes following Layers:**
**Ingestion Layer : ** 
We have data coming from following sources:
1) Azure Storage Gen 2 - Contains day wise files(in csv format) which is uploaded by some external process.
2) Snowflake - We have some tables stored in snowfalke DB.
3) REST API - using Country API to map all respective contries.
![image](https://github.com/vinaytekkur/Olympic_ADF_Project/assets/156997918/5931b0ab-f429-469b-a8cc-54a8a12fdeb7)

**Raw Layer:**
         Using ADF taking respective data from sources and dump those data into Raw layer(Azure Gen 2 Blob Storage), Logic supports missed data files due to any failure etc.
Sink side as well storing data interms of day-wise which is created dynamically by ADF.

**Transformation Layer:**
                  Based on data tranformation requirement modify raw layer data into more meaningful data by creating Dataflows and store those respective data into publish Layer(Azure Gen 2 Blob Storage)
Published layer will have respective container based on data files(Example: if data coming from Athelets data then publishing will be done on Athelets container)
![image](https://github.com/vinaytekkur/Olympic_ADF_Project/assets/156997918/f4384cb9-a25a-45bb-be55-0e0dc4c88b4e)

Pipeline respective to dataflows
![image](https://github.com/vinaytekkur/Olympic_ADF_Project/assets/156997918/c02b8f1b-86f6-41b3-9f4b-353bf95c6179)


Master Pipeline which triggers email notification with information such as (Status of pipeline, Trigger time, pipeline executed by etc)
![image](https://github.com/vinaytekkur/Olympic_ADF_Project/assets/156997918/56e4b242-0967-4519-9804-d4a3df0b2837)
Azure Gen 2 Master data pipeline

![image](https://github.com/vinaytekkur/Olympic_ADF_Project/assets/156997918/dd6bc54a-a943-458d-9b71-c81c9044388e)
Snowflake Master data pipeline


**Reporting Layer:**
              Our final required dataset exists on Publish layer and we create External Tables using Azure Synapse Dedicated SQL pool, Using this we will create Power BI dashboard
![image](https://github.com/vinaytekkur/Olympic_ADF_Project/assets/156997918/118d4cb7-0bcc-46f8-8182-42cd32904cb7)
Power BI Dashboard using external table exists in Synapse Dedicated SQL pool

Project Implemented By - Vinay Tekkur (Data Engineer)
