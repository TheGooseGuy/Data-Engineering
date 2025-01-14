# Data Engineering Lifecycle
## Generation: Source Systems
![de-life-cycle](5b6bd186-8aa5-4b57-bf94-6703bf5c0679.png)

Source system: the origin of the data used in the DE lifecycle.

To evaluate a source system (things to consider):  
1. What are the essential characteristics of the data source? Is it an application? A swarm of IoT devices?
2. How is data persisted in the source system? Is data persisted long term, or is it temporary and quickly deleted?
3. At what rate is data generated? How many events per second? How many gigabytes per hour?
4. What level of consistency can data engineers expect from the output data? If you’re running data-quality checks against the output data, how often do data inconsistencies occur—nulls where they aren’t expected, lousy formatting, etc.?
5. How often do errors occur?
6. Will the data contain duplicates?
7. Will some data values arrive late, possibly much later than other messages produced simultaneously?
8. What is the schema of the ingested data? Will data engineers need to join across several tables or even several systems to get a complete picture of the data?
9. If schema changes (say, a new column is added), how is this dealt with and communicated to downstream stakeholders?
10. How frequently should data be pulled from the source system?
11. For stateful systems (e.g., a database tracking customer account information), is data provided as periodic snapshots or update events from change data capture (CDC)? What’s the logic for how changes are performed, and how are these tracked in the source database?
12. Who/what is the data provider that will transmit the data for downstream consumption?
13. Will reading from a data source impact its performance?
14. Does the source system have upstream data dependencies? What are the characteristics of these upstream systems?
15. Are data-quality checks in place to check for late or missing data?


Schema: Defines the hierarchical organization of data

Schemaless: the application defines the schema as data is written.  
Fixed schema

## Storage
### Evaluating Storage System
To choose a storage system (things to consider):
1. Is this storage solution compatible with the architecture’s required write and read speeds?
2. Will storage create a bottleneck for downstream processes?
3. Do you understand how this storage technology works? Are you utilizing the storage system optimally or committing unnatural acts? For instance, are you applying a high rate of random access updates in an object storage system? (This is an antipattern with significant performance overhead.)
4. Will this storage system handle anticipated future scale? You should consider all capacity limits on the storage system: total available storage, read operation rate, write volume, etc.
5. Will downstream users and processes be able to retrieve data in the required service-level agreement (SLA)?
6. Are you capturing metadata about schema evolution, data flows, data lineage, and so forth? Metadata has a significant impact on the utility of data. Metadata represents an investment in the future, dramatically enhancing discoverability and institutional knowledge to streamline future projects and architecture changes.
7. Is this a pure storage solution (object storage), or does it support complex query patterns (i.e., a cloud data warehouse)?
8. Is the storage system schema-agnostic (object storage)? Flexible schema (Cassandra)? Enforced schema (a cloud data warehouse)?
9. How are you tracking master data, golden records data quality, and data lineage for data governance? (We have more to say on these in “Data Management”.)
10. How are you handling regulatory compliance and data sovereignty? For example, can you store your data in certain geographical locations but not others?

### Data Access Frequency
Not all data is accessed in the same way. Retrieval patterns / data access freqeuncy determines the "temperature" of data.

Hot data: most frequently accessed  
Cold data: seldom queried and is appropriate for storing in an archival system.

## Ingestion