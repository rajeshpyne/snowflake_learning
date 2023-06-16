Roles
======

* Roles is an entity to which privileges on securable objects can be granted or revoked.
* Roles are assigned to users to give them the authorization to perform actions
* User can have multiple roles and switch between them within Snowflake session
* Roles can be granted to other roles for creating a role hierarchy, like below
	`ROLE3 -> ROLE2 -> ROLE1`
* Privileges of child roles are inherited by parent roles.


System-defined Roles hierarchy
--------------------------------
1. ORGADMIN
2. ACCOUNTADMIN
   1. SYSADMIN
   2. SECURITYADMIN
	  1. USERADMIN
	  2. CUSTOMROLES
3. PUBLIC

ORGADMIN
---------
1. Manages operations at organization level
2. Can create account in an organization
3. Can view all accounts in an organization
4. Can view usage information across an organization


ACCOUNTADMIN
-------------
1. Top-level and most powerful role for an account
2. Encapsulates SYSADMIN & SECURITYADMIN
3. Responsible for configuring account-level parameters
4. View and operate on all objects in an account
5. View and manage Snowflake billing and credit data
6. Stop any running SQL statements

SYSADMIN
---------
1. Can create warehouses, databases, schemas and other objects in an account.

SECURITYADMIN
--------------
1. Manage grants globally via the MANAGE GRANTS privileges
2. Create, monitor and manages users and roles

USERADMIN
-------------
   1. User and ROLE management via CREATE USER and CREATE ROLE security privileges
   2. Can create users and roles in an account

CUSTOMROLE
----------
   1. Custom Roles allows you to create a role with custom and fine-grained security privileges defined.
   		They can be aligned to groups or teams within an organization, a support team, for example, a group 
		of analysts or by environment such as dev and prod.
   2. Allow administrators working with the system-defined roles to exercise the security principle of least privilege.
   3. CUSTOM Roles can be created by the SECURITYADMIN & USERADMIN roles as well as by any role to which the CREATE ROLE privilege has been granted
   4. It is recommended to create a hierarchy of custom roles with the top-most custom role assigned to the SYSADMIN role.
   5. If custom roles are not assigned to the SYSADMIN role, system admins will not be able to manage the objects owned by the custom role.

PUBLIC
--------
1. Automatically granted to every user and every role in an account
2. Can own securable objects, however objects owned by PUBLIC role are available to every other user and role in an account.

