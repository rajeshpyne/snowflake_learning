Tasks and Streams
=================

* Task is an object used to schedule the execution of a 
    `SQL statement` or
    `stored procedure` or 
    `procedural logic` 
using _Snowflake Scripting_.

Task Workflow
---------------
* Prerequisite
  - ACCOUNTADMIN role or CREATE TASK privilege.
  
```sql
    CREATE TASK MINUTE_TASK
        WAREHOUSE = MYWH
        SCHEDULE = '30 minute'
    AS
        COPY INTO MY_TABLE
        from $MY_STAGE
    ;

    ALTER TASK MINUTE_TASK RESUME;  -- START the Task
    ALTER TASK MINUTE_TASK SUSPEND;  -- PAUSE theTask
```

DAG
----

T1 -> [T2, T3] -> T4

A DAG can be composed of a `maximum of 1000 tasks`, 
and `one task can only be linked to 100 other tasks`.
So a 
`child task can only reference 100 dependent tasks or a parent task with 100 child tasks`.

It's also worth pointing out that 
`all tasks in a DAG must have the same task owner` and 
`they must be stored in the same database and schema`.


CREATE TASK T4
WAREHOUSE = MYWH
    AFTER T2, T3
AS 
    COPY INTO MY_TABLE FROM $MY_STAGE
;


STREAMS
========

Stream is an `schema-level object` created to 
`view and track DML changes to a source table` 
  - inserts, updates and deletes.

```sql
    CREATE STREAM MY_STREAM ON TABLE MY_TABLE ; -- Create Stream
    SELECT * FROM MY_STREAM ;   -- Query Stream

```

```SQL
    CREATE TASK MY_TASK1
    WAREHOUSE= MY_WH
    SCHEDULE = '5 MINUTE'
    WHEN
        SYSTEM$STREAM_HAS_DATA('MY_STREAM')
    AS
        INSERT INTO MYTABLE1(ID,NAME) SELECT ID, NAME
        FROM MYSTREAM WHERE METADATA$ACTION = 'INSERT'
    ;
```

- Tasks create processing steps in the table
- Streams record the delta changes in the table

When chained together, 
tasks and streams form quite a good way 
to create continuous transformation
pipelines.
