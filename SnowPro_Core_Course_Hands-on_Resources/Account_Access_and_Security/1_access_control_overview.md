Access Control Overview
=======================

2 types of Access Control Frameworks

- Role-based Access Control (RBAC) : 
  	It is an access control framework in which 
	access privileges are `assigned to roles`
	and in turn `assigned to users`.

	Privileges are like `SELECT`, `MODIFY`, `REMOVE` etc.
  
  **`Privilege` -> `Role` -> `User`**

- Discretionary Access Control (DAC) :
	
	**`Role A`	---Owns--->	`Object A`**
		| grants
		| access to `Role B`
		| only `select` for example
	**`Role B`** --can only use SELECT on Object A then

	Snowflake combines RBAC with 
	Discretionary Access Control (DAC) in which each
	object has an owner, 
	who can in turn grant access to that object.

Securable Object
-----------------
Every securable object is owned by a single role which can be found by executing a `SHOW <object>` command.

the owning role will have:
- Has all privileges on the object by default
- Can grant or revoke privileges on the object to other roles
- Transfer ownership to another role
- Share control of an object if the owning role is shared

Access to objects is also defined by privileges granted to roles:
- Ability to create a Warehouse
- Ability to list tables contained in a schema
- Ability to add data to a table

Unless allowed by a grant, access to a securable object will be denied.