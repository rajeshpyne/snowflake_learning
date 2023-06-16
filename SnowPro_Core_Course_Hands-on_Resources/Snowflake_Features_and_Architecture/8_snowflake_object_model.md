Snowflake Object Model
========================

Snoflake Object
----------------
An object in Snowflake is simply something you can interact with, 
something you can issue commands against, such as create table or drop stream.

Snowflake have also extended the use of objects beyond just enabling functionality to also make many
management aspects of the system possible.

For example, we can now manage account properties by executing commands against an account object.
It's important to point out at this stage that every object in Snowflake is securable.

This means that privileges on objects, such as the ability to read a table can be granted to `Rows`.
`Rows` are then granted to users and this determines what a user can see and do in Snowflake.

Snowflake objects fit into a hierarchy with `one to many relationships`.

`Organization`  : Responsible to managing one or more Snowflake accounts
    - `Account` : refer to both the `collection of services` snowflake provide you when you sign up the `UI`, the `compute`, the `storage`, all of that which is accessible via the
                    URL, but it also refers to an account object.
                    You can interact with this object via a SQL to change `account-level parameters` like how we handle date strings across the account.
      - `Row`   : Account level objects; they dont hold data, 
                    but are used to `configure different parts of your account`, such as which users exist and how many virtual WH you would like.
                    Row consists of  :-
                    1. Network Policy
                    2. User
                    3. Role
                    4. `Database` : `1 account :: N Database` relationship
                       1. `Schema` : One schema belongs to one database.(1:1 relationship) and 1 database can have multiple schemas
                          1. Stage
                          2. Pipe
                          3. Procedure
                          4. Function
                          5. `Table` : logical representation of data
                          6. View
                          7. Task
                          8. Stream
                    5. Warehouse
                    6. Share
                    7. Resource Monitor
        