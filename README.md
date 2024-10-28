# Rebrickable Data Ingestion Pipeline

The **Rebrickable Data Pipeline project** is a comprehensive data ingestion system designed to ingest and process data from two distinct sources securely: **the Rebrickable LEGO Database** and **the Rebrickable User Database**.
This project leverages Azure Data Factory (ADF) to build and manage separate pipelines for each database, ensuring secure access control, daily automation, environment synchronization, and failure alerting.
# Project Goals

The primary objective is to establish a robust pipeline architecture to ingest, transform, and store data from **Rebrickable’s APIs** while maintaining strict security standards and operational efficiency.
# Architecture

- User_Dataset_pipeline:
    ![User_Dataset_pipeline](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/Database%20pipeline.png)
- LEGO_Database_pipeline
    ![LEGO_Database_pipeline](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/User_Dataset_pipeline.png)


# Key Features:

1. **Environment Management with Resource Groups**:
    - **Development and Production Environments**: 
        Organized into two main resource groups, one for development and one for production, the project allows isolated testing and reliable production deployment.
    - **Environment Synchronization via CI/CD**: 
        Using a CI/CD pipeline, the project synchronizes the development and production environments. Committing a pull request to the main branch automatically applies changes to the production branch, ensuring continuous alignment across environments.
        ![CI/CD pipeline](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/CI-CD%20pipeline.png)

2. **Dual Configurable Pipeline Architecture with Azure Data Factory (ADF)**:
    - **Separate ADF Instances**: 
        The project utilizes two distinct ADF instances, one for each resource group (development and production). Each ADF instance manages its own pipelines, specifically tailored to handle the LEGO Database and User Database ingestion tasks.
            ![User_Dataset_pipeline](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/Database%20pipeline.png)
            ![LEGO_Database_pipeline](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/User_Dataset_pipeline.png)
    - **Daily Scheduled Triggers**: 
        Pipelines in both ADF instances are configured with daily scheduled triggers, ensuring that data ingestion runs automatically each day, keeping the data up-to-date.
    - Each pipeline is **Configurable**, meaning The ingested file differs depending on the parameter passed at the runtime.

3. **Secure Access Control**:
    - The project employs separate Microsoft Entra ID **groups** and service principals to enforce strict access control, ensuring that only designated managed identities can interact with specific resources.
        - **adlsg2deployment** and **RBAC** for the deployment and the development environment. both are used to give **storage blob data contributor** role on the ADLSg2 accounts to each corresponding ADF instance.
            ![adlsg2deployment](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/adlsg2deployment.png)
            ![RBAC](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/RBAC.png)
        - **DEV+PROD** a group that gives access for both adf instances to a single key vault that has the secrets on which the pipeline depend.
            ![DEV+PROD](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/Dev%2BPROD.png)
    - **Azure Key Vault Integration**: 
        - API keys and user tokens for accessing Rebrickable’s APIs are securely stored in Azure Key Vault, safeguarding sensitive information from unauthorized access.
            ![Azure Key Vault](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/Key%20Vault.png)

4. **Error Handling & Notification System**:
    - **Automated Failure Alerts with Logic Apps**: 
        A Logic App monitors pipeline executions and sends HTTP notifications to a designated email if any pipeline fails, allowing for quick identification and resolution of issues.
        ![Azure Logic App](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/Logic%20App.png)

5. **Data Storage & Hierarchy**:
    - **Azure Data Lake Storage Gen2 (ADLSg2)**: 
        - ADLSg2 serves as the staging layer for data storage, organized through a structured file system hierarchy.
            ![file system hierarchy](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/File%20hierarchy.png)
          
    - **Data Redundancy**:
        - LRS is used in the development environment
        - ZRS is used in the deployment environment
    - **Life Cycle Management**:
            - created a life cycle policy that states if no changes were made to files for the last 30 days change their access tier from hot to cold.
      
                ![Life Cycle Management](https://github.com/KareemAdel10/Rebrickable-Data-Pipeline/blob/main/Images/Life%20Cycle%20Management.png)


# Technologies & Tools

- Azure Data Factory (ADF) for pipeline orchestration and scheduling
- Microsoft Entra ID for access control
- Azure Key Vault for secure storage of API keys and user tokens
- Azure Data Lake Storage Gen2 (ADLSg2) for data staging
- Logic Apps for automated failure notifications
- Azure DevOps for CI/CD pipeline management

## Contribution

Contributions to this project are welcome. If you have any ideas for improvement, feel free to fork the repository, make your changes, and submit a pull request. Please ensure your changes align with the overall project structure and objectives.

## Acknowledgements

I would like to thank the following:
- Azure for offering powerful tools and services that enable seamless data engineering and analytics processes.
- Tybul on Azure for providing great learning resources.

# Contact

For any questions, feedback, or further information, feel free to reach out:
- **Email:** kareema9001@gmail.com
- **LinkedIn:** https://www.linkedin.com/in/kareem-adel-b76ab9201/

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
