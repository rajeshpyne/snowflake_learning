Privileges
=============

- A security privilege defines a level of access to an object.

- For each object, there is a set of security privileges that can be granted on it.

- There are 4 categories of security privileges:-
  - Global Privileges
  - Privileges for account objects
  - Privileges for schemas
  - Privileges for schema objects

- Privileges are managed using the `GRANT` and `REVOKE` commands.
    `GRANT USAGE ON DATABASE <MY_DB> TO ROLE <MY_ROLE>`
    `REVOKE USAGE ON DATABASE <MY_DB> TO ROLE <MY_ROLE>`

- Future grants allow privileges to be defined for objects not yet created.
    `GRANT SELECT ON FUTURE TABLES IN SCHEMA <my_schema> TO ROLE <my_role>`
