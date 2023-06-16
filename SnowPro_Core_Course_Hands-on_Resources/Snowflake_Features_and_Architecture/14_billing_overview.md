Compute Billing Overview
==========================

`Credits` : Snowflake billing unit of measure for compute resource consumption

Virtual Warehouse Services
------------------------------ 
    - Credit calculated based on size of virtual warehouse.
    - Credit calculated on per second basis while a virtual warehouse is in 'started' state.
    - Credit calculated with a minimum of 60 second.


Cloud Services
-----------------
    - Credits calculated at a rate of 4.4 credits per compute hour.
    - Only cloud services that exceeds 10% of the daily usage of the compute resources are billed.
    - This is called the Cloud Services Adjustment

Serverless Services
----------------------
    - Each serverless feature has its own credit rate per compute hour.
    - Serverless feature are composed of both compute services and cloud services.
    - Cloud services adjustment does not apply to cloud services usage when used by serverless features.


Data Storage and Transfer Billing 
==================================

`$ Dollar Value` : Storage and Data Transfer are billed in currency

Data Storage
-------------
    - Data Storage is calculated monthly based on the average number of on-disk bytes per day in the following locations:-
      - Database Tables
      - Internal Stages

    - Costs calculated based on a flat dollar value rate per terabyte(TB) based on :
      - Capacity or On-Demand
      - Cloud provider
      - Region

Data Transfer
--------------
    - Data transfer charges apply when moving data from one region to another or from one cloud platform to another
    - Unloading data from Snowflake using `COPY INTO <location>` command
    - Replicating data to a Snowflake account in a different region or cloud platform
    - External functions transferring data out of and into Snowflake.