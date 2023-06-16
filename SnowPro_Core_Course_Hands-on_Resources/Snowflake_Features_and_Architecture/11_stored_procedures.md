Snowflake Stored Procedures
=============================

* Javascript
* Snowflake Scripting 
	- using SQL 
* Snowpark 
	- using Python
	- using JAVA
	- using Scala
	
---------------------------------------------------------------------
|		Features					|	UDF		|  Stored Procedure	|
---------------------------------------------------------------------
| Called as part of SQL Statement	|	True	|	`False`			|
| Ability to overload				|	True	|	True			|
| 0 or more input parameters		|	True	|	True			|
| Use of Javascript API				|	`False`	|	True			|
| Return of value optional			|	`False`	|	True			|
| Values returned usable in SQL		|	True	|	`False`			|
| Call itself recursively			|	`False`	|	True			|
---------------------------------------------------------------------

Stored Procedures : It perform actions rather than return values(CRUD operations mainly).
UDFs : Functions to calculate something and return value to the user.
