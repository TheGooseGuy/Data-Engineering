# Data Engineering Lifecycle
## Generation: Source Systems
![de-life-cycle](5b6bd186-8aa5-4b57-bf94-6703bf5c0679.png)

Source system: the origin of the data used in the DE lifecycle.

Schema: Defines the hierarchical organization of data

Schemaless: the application defines the schema as data is written.  
Fixed schema

## Storage
### Data Access Frequency
Not all data is accessed in the same way. Retrieval patterns / data access freqeuncy determines the "temperature" of data.

Hot data: most frequently accessed  
Cold data: seldom queried and is appropriate for storing in an archival system.