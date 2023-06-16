Storage Layer
====================

* `Persistent and infinitely scalable cloud storage` residing in cloud providers blob storage service, such as AWS S3.
  - The storage layer is really just the blob storage service of the cloud provider you've deployed your snowflake account into.
    So, for example, our trial account, which was created in AWS under the hood, the storage layer, would use the S3 service as snowflake users.
  - We inherit the native ability of services like S3 to scale out our storage layer almost infinitely.

* Snowflake users by proxy get the `availability and durability gurantees` of the cloud providers blob storage.
  - As we mentioned earlier, we also get the native availability and durability guarantees of 
    the cloud providers.

* Data loaded into Snowflake is organized by databases, schemas and accessible primarily as tables.
  - To the user data loaded or inserted into snowflake is organized into databases, schemas and tables.
    All table data is stored in the `centralized storage layer, acting as a single source of truth`.

* Both `structured and semi-structured` data files can be loaded and stored in Snowflake
  - Snowflake also has native support for ingesting structured and semi-structured file formats such as
    the limited files like CSV or TSV, as well as semi-structured files like JSON, Avro and Parquet.

* `How is Snowflake actually storing in blob storage` when data is loaded into a table?

  - When data files are loaded or rows are inserted into a table, 
      Snowflake reorganizes the data into its proprietory formats. and It is
        
    **`compressed` and `columnar file format` and `encrypted` and `partitioned`**

    - `Types of file format`
      - columnar File format - Store the data values of the same column physically next to each other on disk.
      - row file format  - Store the rows next to each other on disk.

        Storing all table data in a `columnar file format` is great for the 
        types of overlap queries will be running on Snowflake because 
        it effectively allows you to `skip past columns which are not needed for the query result`.
        
        This is what we call `read optimization` - Reducing the amount of data needed to be fetched.

    - `Compression` : Compression technique is good for columnar file format, as columns usually contain data of the same type.
    - `Encryption` : All data files are automatically encrypted by default using `AES-256` encryption.
    - `Partitioned` : Data loaded into snowflake is also divided into micro-partitions, This is done so that SF can optimize queries by ignoring partitions that aren't needed to compute the result of the query(Partition pruning)

* Storage is billed on how much is stored based on a flat rate per TB calculated monthly.
* Table data is only `accessible via SQL only`, not directly in the blob storage.

Recap : 
--------
- All the processes we've mentioned so far encryption compression, 
    columnar data storage, micro partitioning are entirely automated and managed by snowflake.