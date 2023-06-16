Architecture
================

- `Shared Disk`
  
    Data Storage
        |
        |
    |---|---|
    P1  P2  P2     (Processor)  

    * This was the first move away from single node architectures and worked by scaling out nodes in a compute
    cluster, but keeping storage in a single location.
    * In other words, all data is accessible from all cluster nodes.
    Any machine can read or write any portion of the data.

    Advantages : -
    - Relatively simple to manage
    - Single source of truth

    Disadvantages : -
    - Single point of failure
    - Bandwidth and network latency
    - Limited scalability(small number of queries can overwhelm)
    - leads to Resource contention ideally something we would like to avoid.

- `Shared Nothing`
    
    P1  P2  P3  ... Pn (Processor)
    D1  D2  D3  ... Dn (Data Storage)

    * As the name indicates, the nodes in this architecture do not share any hardware, storage and compute
    are located on separate machines that network together.
    * The nodes in the cluster contain a subset of data locally instead of the node sharing one central data
    repository.

    Advantages :-
    - Co-locating compute and storage avoids networking latency issues
    - Generally cheaper to build and maintain
    - Improved scaling over shared-disk architecture

    Disadvantages :-
    - Scaling still limited (Shuffling the data between nodes becomes expensive)
    - Storage and compute tightly coupled(redistributing the data becomes a challenge)
    - Tendency to overprovision 
    - no flexiblity to easily decrease compute resources when they weren't needed, so resource contention is still existing here
    
Snowflake `reimagined the storage, compute and networking in the cloud`

`Multi-Cluster Shared Data Architecture`
------------------------------------------

It's a `service-oriented architecture` consisting of three physically separated but logically integrated layers

**Data Storage Layer**
----------------------
The `centralized cloud-storage layer`, which stores all our table data organized
    into databases conceptually similar to the **`shared-disk architecture`**.

**Query Processing Layer**
---------------------------
Moving up a level, we have the `query processing layer` 
    made up of separate compute clusters that snowflake called `virtual warehouses`.
    They're responsible for `executing the computation required to process a query`, usually uses SQL command
    to create virtual warehouses, which then snowflake provision and manage it.
    All virtual warehouses created have `consistent access to the centralized storage` and 
    have the ability to `cache locally the table data` used during query processing, 
    each cluster working in a similar fashion to the **`shared-nothing architecture`**.

**Cloud Services Layer**
-------------------------
At the top, we have the `cloud services layer`, which coordinates the whole show handling 
    `authentication to Snowflake`, 
    `managing the cloud infrastructure`, 
    `passing and optimising queries` and a lot more.

Why this architecture is called as `service-oriented architecture` ?
    The reason is that each layer under the hood is a 
    separate `physical service or collection of services` that 
    snowflake manage `communicating over a network via restful interfaces`.
    They communicate over a network.

    For example, the actual physical machines which compute the query results which make up virtual warehouses, 
    are entirely separate from where we keep the long term table data.

    This novel architecture is one of, if not the main differentiators of Snowflake 
    and is a direct result of having been purpose built for the cloud.


Other unique capabilities :-
  1. Key Storage compute and management services can now be scaled independently 
      - They are de-coupled.
  2. No hard limit on how much each layer can be scaled 
      - We can throw as musch as data into the cloud storage layer and scale out compute near infinitely. 
      - The multi-cluster aspect of the multi-cluster shared data architecutre is the 
          ability to create as many separate compute clusters as desired, 
          and they'd be isolated from each other as different virtual warehouses.

    This allows for workload isolations, for example, allowing analytics and pipeline jobs to not contend for resources

**Cloud Agnostic Layer**
------------------------------

This layer will `ensure the 3 main layers will perform identically on any of the cloud providers` an account is deployed to

