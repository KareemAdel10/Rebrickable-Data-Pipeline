# Rebrickable Data Ingestion Pipeline
---
The **Rebrickable Data Pipeline project** is a comprehensive data ingestion system designed to securely ingest and process data from two distinct sources: **the Rebrickable LEGO Database** and **the Rebrickable User Database**.
This project leverages Azure Data Factory (ADF) to build and manage separate pipelines for each database, ensuring secure access control, daily automation, environment synchronization, and failure alerting.
# Project Goals
---
The primary objective is to establish a robust pipeline architecture to ingest, transform, and store data from **Rebrickable’s APIs** while maintaining strict security standards and operational efficiency.
# Architecture
--
![User_Dataset_pipeline](https://dev.azure.com/1900286/CI-CD/_git/Ingestion%20Task?path=/Images/Api%20Pipeline.png&version=GBsecondarybranch)
![LEGO_Database_pipeline](https://dev.azure.com/1900286/CI-CD/_git/Ingestion%20Task?path=/Images/Database%20pipeline.png&version=GBsecondarybranch)

- **Data Source**:
    - zipped files from Reprickable
- **Data Storage**:
    - Azure Data Lake Storage Gen2 that stores raw.
- **Data Processing**:
    - Azure Data Factory:
        ADF is used to create an ingestion pipeline.
- **Data Exploration**:
    - Azure Storage Explorer is used to interact with Azure Blob Storage and ADLS Gen2.

# Steps
---
1. **Environment planning**:
    - Create two resource groups in Azure, one is for the **development** environment and the other is for the **production** environment, create an instance of **ADF** and **ADLSg2** for each environment.
2. **Security**:
    - create three groups using **Microsoft Entra ID**:
        1. **adlsg2deployment** and **RBAC** for the deployment and the development environment. both are used to give **storage blob data contributor** role on the ADLSg2 accounts to each corresponding ADF instance.

        2. **DEV+PROD** a group that gives access for both adf instances to a single key vault that has the secrets on which the pipeline depend.



## Contribution
Contributions to this project are welcome. If you have any ideas for improvement, feel free to fork the repository, make your changes, and submit a pull request. Please ensure your changes align with the overall project structure and objectives.

## Acknowledgements
I would like to thank the following:
- Azure for offering powerful tools and services that enabled the seamless data engineering and analytics processes.
- Tybul on Azure for providing great learning resources.

# Contact
For any questions, feedback, or further information, feel free to reach out:
- **Email:** kareema9001@gmail.com
- **LinkedIn:** https://www.linkedin.com/in/kareem-adel-b76ab9201/

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.