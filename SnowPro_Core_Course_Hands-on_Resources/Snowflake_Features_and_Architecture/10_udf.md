UDFS
------------

```sql
CREATE FUNCTION AREA_OF_CIRCLE(radius FLOAT)
RETURNS TABLE(area number)
AS
$$
    pi() * radius * radius
$$;

```


* User Defined Functions (UDFs) are schema-level objects that enable users to write their 
    own functions in four languages as of now
  - SQL
  - JavaScript
  - Python
  - Java

* UDFs accept 0 or more parameters
* UDFs can return scalar or tabular results(UDTF)
* UDFs can be called as part of SQL statement (`SELECT AREA_OF_CIRCLE(col1) from MY_TABLE`)

JavaScript UDF
----------------
* JS is specified with language parameter.
* Enables use of high-level programming language features, 
    such as branching, looping, error handling and in-built functions.
    But it cannot include or code additional libraries within the code.
* Unlike SQL, UDFs Javascript UDFs can refer to themselves recursively.
* Snowflake data types are mapped to JavaScript data types.

SQL and JS UDFs are considered as secure,
while JAVA UDF is not.

External Functions
-------------------

Example of External Functions:-
```js
    CREATE OR REPLACE EXTERNAL FUNCTION CALC_SENTIMENT(STRING_COL VARCHAR)
    RETURNS VARIANT
    API_INTEGRATION = AWS_API_INTEGRATION
    AS 'https://<service-name>.<region-name>.amazonaws.com/';
```

Life Cycle of External Functions :-

`Client Program` -> `Snowflake` -----------------> `HTTPS Proxy Service` ---> `HTTPS Proxy`
        |            |                              |                           |
`calc_sentiment` -> `Ext.Func(API Integration)` -> `AWS API Gateway` -------> `AWS Lambda`


Limitations of External Functions :-
1. Query Optimizer can turn it slower
2. Scalar only(only a single value can be returned)
3. Not Shareable( cannot share with other accounts)
4. Less Secure (calling outside sensitive data could raise security alarms)
5. Egress Changes(snowflake can charge data moved to different cloud platform)