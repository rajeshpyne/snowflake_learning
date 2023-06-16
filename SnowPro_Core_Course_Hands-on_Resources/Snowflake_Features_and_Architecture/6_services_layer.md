Services Layer
================

It's not really a part of the architecture that is deeply explored in the Snowflake documentation,
partly because Snowflake is a SaaS solution.


But it is important to know some details bout what is this `services layer`?
    - It's a collection of `Highly-Available` and `Scalable` services 
        that coordinate activities across all snowflake accounts in order to process user requests such as 
        `authentication` and `query optimizaion` across all Snowflake accounts.
        This is why you might hear it referred as the global services layer.

    - Having a `global multi tenancy model` like this, instead of creating an account specific version of all
        the services every time an account is requested allows Snowflake to achieve certain economies of scale
        and also makes implementation of some interesting features like secure data sharing much simpler to achieve.

    - Behind the scenes, the `services layer run on cloud based compute instances`, much like virtual warehouses.
        However, we have no control or visibility into their creation or how they work.

* Services managed by this `services layer` includes :-

  - `Authentication and Access control` : This is about proving who you are and if you have `valid login credentials` as well as determining once you're logged into an account what `level of privileges` you have to perform certain actions.

  - `Infrastructure Management` : This service handles the `creation and management of the underlying cloud resources`, 
    such as the *blob storage* and *compute instances required for the storage and query processing layers*.

  - `Transaction Management` : Data should `consistently available to all virtual warehouses`, as SF is ACID compliant data warehouse.

  - `Metadata Management` : keeps `information and statistics on objects` and the data they manage.
  
  - `Query parsing and optimization` : The service takes the `SQL query submited, turns it into an actionable plan`.
  
  - `Security` : broad category of services which handle things like `data encryption` and `key rotation`.