# Automated Data Pipeline for NHS Digital A&E Attendances and Emergency Admissions


## The Problem
Each month, NHS Digital publishes aggregated data on Accident & Emergnecy (A&E) attendances and emergency admissions:  https://www.england.nhs.uk/statistics/statistical-work-areas/ae-waiting-times-and-activity/

Monitoring aggregated measures like A&E attendances and emergency admissions is crucial for several reasons:
- **Resource Allocation**: By tracking these metrics, healthcare providers can better allocate resources, such as staff and equipment, to areas experiencing high demand.
- **Performance Monitoring**: These measures help in assessing the performance of emergency services, identifying bottlenecks, and implementing improvements.
- **Policy Making**: Aggregated data informs policymakers about the current state of healthcare services, enabling them to make evidence-based decisions.
- **Public Health**: Monitoring these metrics helps in identifying trends and patterns in public health, such as outbreaks or seasonal variations in healthcare demand.
- **Quality of Care**: Ensuring that patients receive timely and appropriate care is essential for maintaining high standards of healthcare.

Although this data is crucial, the manual process of retrieving, processing, and analysing this data can be time-consuming and prone to errors.

The objective of this project is to design and implement an automated data pipeline that retrieves open-source data on A&E attendances and emergency admissions from the NHS Digital website. The pipeline will ensure that the data is collected, processed, and stored efficiently, enabling timely and accurate analysis.

To achieve this, the following steps will be taken:
1. Create GCP Bucket and BQ Dataset: Utilize Terraform to create a Google Cloud Platform (GCP) bucket and a BigQuery (BQ) dataset for storing the project data. This will provide a scalable and secure environment for data storage and management.  
2. Set Up Kestra Workflow: Implement a Kestra workflow to automate the process of moving NHS A&E CSV files from the web to the GCP bucket. The workflow will include steps for renaming the files appropriately before storage to maintain a consistent and organized structure.  
3. Data Processing with dbt/BQ Dataform: Use dbt or BQ Dataform to process the data. This will involve removing the "Total" row from the latest extract, extracting the month and year, and appending the newest data extract to the existing dataset. These transformations will ensure the data is clean and ready for analysis.  
4. Data Visualization with Looker Studio: Visualize the processed data using Looker Studio. This will enable stakeholders to generate reports and visualizations, providing valuable insights into trends and patterns in emergency services usage.  

Expected Outcomes:
- A fully automated data pipeline that retrieves, processes, and stores A&E attendances and emergency admissions data from NHS Digital.
- Improved efficiency and accuracy in data retrieval and analysis.
- Enhanced ability for healthcare providers and researchers to monitor and respond to trends in emergency services.

Challenges:
- Ensuring data quality and consistency during the retrieval and processing stages.
- Handling changes in data formats or structures on the NHS Digital website.
- Implementing robust error handling and recovery mechanisms.

## Evaluation Criteria

* Problem description
    * 0 points: Problem is not described
    * 2 points: Problem is described but shortly or not clearly 
    * 4 points: Problem is well described and it's clear what the problem the project solves
* Cloud
    * 0 points: Cloud is not used, things run only locally
    * 2 points: The project is developed in the cloud
    * 4 points: The project is developed in the cloud and IaC tools are used
* Data ingestion (choose either batch or stream)
    * Batch / Workflow orchestration
        * 0 points: No workflow orchestration
        * 2 points: Partial workflow orchestration: some steps are orchestrated, some run manually
        * 4 points: End-to-end pipeline: multiple steps in the DAG, uploading data to data lake
    * Stream
        * 0 points: No streaming system (like Kafka, Pulsar, etc)
        * 2 points: A simple pipeline with one consumer and one producer
        * 4 points: Using consumer/producers and streaming technologies (like Kafka streaming, Spark streaming, Flink, etc)
* Data warehouse
    * 0 points: No DWH is used
    * 2 points: Tables are created in DWH, but not optimized
    * 4 points: Tables are partitioned and clustered in a way that makes sense for the upstream queries (with explanation)
* Transformations (dbt, spark, etc)
    * 0 points: No tranformations
    * 2 points: Simple SQL transformation (no dbt or similar tools)
    * 4 points: Tranformations are defined with dbt, Spark or similar technologies
* Dashboard
    * 0 points: No dashboard
    * 2 points: A dashboard with 1 tile
    * 4 points: A dashboard with 2 tiles
* Reproducibility
    * 0 points: No instructions how to run the code at all
    * 2 points: Some instructions are there, but they are not complete
    * 4 points: Instructions are clear, it's easy to run the code, and the code works
