Types of Snowflake Table
---------------------------

* Permanent
  - Default Table type
  - Exists until explicitly dropped
  - Time Travel upto 90 days ( for enterprise edition only, else 1 day for standard edition )
  - Fail-Safe enabled
  
* Temporary
  - Used for transitory data
  - Persist for duration of a session
  - Time Travel upto 1 day 
  - Not fail-safe proof
  
* Transient
  - Exists until explicitly dropped
  - No fail-safe period
  - Time Travel upto 1 day, regardless of snowflake editions
  - No Fail-safe proof
  - Cost effective as time travel and failsafe contributes to storage costs

* External
  - Query Data outside of Snowflake(like Azure BLOB container)
  - Read-only data
  - No Time Travel
  - No Fail-Safe


Type of Snowflake Views
-------------------------

* Standard
  - Does not contribute to storage costs.
  - If source table is dropped, querying the view returns error.
  - Used to restrict the contents of a table.
  
* Materialized
  - Stores results of a query definitioin and periodically refreshes it.( this incurs cost)
  - Incurs cost as serverless feature.
  - Used to boost performance of external tables.
  
* Secure
  - Both standard and materialized views can be secure.
  - Underlying query definition only visible to authorized users.
  - Some query optimizations bypassed to improve security.