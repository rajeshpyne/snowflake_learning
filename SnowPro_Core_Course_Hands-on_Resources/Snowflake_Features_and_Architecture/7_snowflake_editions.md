Snowflake Features and Editions
================================

Different editions of Snowflake exist to better fit how an organization would use Snowflake and 
what level of features and service they require. 
The snowflake addition affects the amount charged for compute and data storage.

* **Standard** - 
    - It is the introductory level offering and contains the core functionality of Snowflake.
    - we get the basic ANSI standard SQL features you'd expect, including `most DDL and DML statements`, 
        as well as use of advanced DML statements such as `multi table insert`, `merge` and `windowing` functions.
    - We also get access to Snowflake's `suite of security`, `governance` and `data protection` features Snowflake collectively called *continuous data protection*. This includes the likes of `time travel` and `network policies`.

* **Enterprise** - 
    - With this, we get all the features and services of the standard edition, along with features designed
        specifically for the needs of large scale enterprises and organizations.
    - Some examples include `multi cluster warehouses` and `database failover`.

* **Business Critical** - 
    - The business Critical edition offers `higher levels of data protection` and `enhanced security` 
        to support organisations with very sensitive data.
        For example, data that must comply with regulations.
    - we can enable `private connectivity` to our snowflake account or `use our own customer manage key to encrypt data in Snowflake`.

    Business critical includes all the features and services of the enterprise and standard editions.

* **Virtual Private Snowflake (VPS Edition)** -
    - This offers the `highest level of security` for organizations that have strict requirements around data protection, such as governmental bodies or financial institutions.
    - It includes all the features of the business critical edition and below, 
        but in a `completely separate environment`, walled off from all other snowflake accounts.

    E.g. - As we know, the services layer is shared between accounts.
    If you were to create a VBS edition account, this wouldn't be the case.
    Services like the metadata store wouldn't be shared.