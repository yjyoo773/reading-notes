# Mongo and Mongoose

## SQL vs NoSQL
* SQL databases are primarily Relational Databases compared to NoSQL are non-relational or distributed databases.
* SQL databases are table based databases where as NoSQL are document based,key-value paires, graph databases or wide-column stores.
* SQL databses represent data in form of tables consisting of *n* number of rows of data.
* NoSQL databases do not have standard schema defininitions which it needs to adhered to.
* SQL databases have predefined schema whereas NoSQL databases have dynamic schema for unstructured data.
* SQL databases are scaled by increasing the horse-power of the hardware.
* NoSQL databases are scaled by increasing the databases servers in the pool of resources to reduce the load.
* SQL: MySQL, Oracle, Sqlite, PostgreSQL, MS-SQL
* NoSQL: MongoDB, BigTable, Redis, RavenDb, Cassandra
* SQL is better for complex queries since NoSQL do not have standard interfaces to perform complex queries.
* NoSQL is better for hierarchical data storage as it follows the key-value pair similar to JSON.
* For high transactional based application: SQL databases are best fit for heavy duty transactional type applications
* SQL databases emphasizes on ACID properties ( Atomicity, Consistency, Isolation and Durability)
* NoSQL database follows the Brewers CAP theorem ( Consistency, Availability and Partition tolerance)

## NoSQL Data Modeling Techniques
- NoSQL data modeling is typically driven by application-specific access patterns, i.e. the types of queries to be supported. The main design theme is “What questions do I have?”  
- NoSQL data modeling often requires a deeper understanding of data structures and algorithms
- Data duplication and denormalization are first-class citizens

### Conceptual Techniques
#### Denormalization
Copying the same data into mulitiple documents or tables in order to simplify/optimize query processing or to fit the user's data into a particular data model.  
In general, denormalization is helpful for the following trade-offs:
- Query data volume or IO per query VS total data volume
- Processing complexity VS total data volume

#### Aggregates
- Key-Value Stores and Graph Databases typically do not place constraints on values, so values can be comprised of arbitrary format
- BigTable models support soft schema via a variable set of columns within a column family and a variable number of versions for one cell
- Document databases are inherently schema-less, although some of them allow one to validate incoming data using a user-defined schema

#### Application Side Joins
Query time joins almost always mean a performance penalty, but in many cases one can avoid joins using Denormalization and Aggregates, i.e. embedding nested entities.  
Cases when joinsa are inevitable and an application is needed.
- Many to many relationships are often modeled by links and require joins.
- Aggregates are often inapplicable when entity internals are the subject of frequent modifications

### General Modeling Techniques
#### Atomic Aggregates
 NoSQL solutions have limited transaction support. In some cases one can achieve transactional behavior using distributed locks or application-managed MVCC, 
 but it is common to model data using an Aggregates technique to guarantee some of the ACID properties.  Aggregates allow one to store a single business entity as 
 one document, row or key-value pair and update it atomically
 
 #### Enumerable Keys
 Benetfits of Sorted Keys
 - Some NoSQL stores provide atomic counters that allow one to generate sequential IDs. In this case one can store messages using userID_messageID as a composite key. 
 If the latest message ID is known, it is possible to traverse previous messages.
 - Messages can be grouped into buckets, for example, daily buckets. This allows one to traverse a mail box backward or forward starting from any specified date 
 or the current date.
 
 #### Dimensionality Reduction
 Dimensionality Reduction is a technique that allows one to map multidimensional data to a Key-Value model or to other non-multidimensional models.
 
 #### Index Table
 The most important class of such stores is the BigTable-style database. The idea is to create and maintain a special table with keys that follow the access pattern.
 
 #### Composite Key Index
 Composite keys in conjunction with secondary sorting allows one to build a kind of multidimensional index which is fundamentally similar to the previously described 
 Dimensionality Reduction technique.
 
 #### Aggregation with Composite Keys
 The idea is to keep all records for one user collocated, so it is possible to fetch such a frame into memory (one user can not produce too many events) 
 and to eliminate site duplicates using hash table or whatever.
 
 #### Inverted Search 
 This technique is more a data processing pattern, rather than data modeling. Nevertheless, data models are also impacted by usage of this pattern. The main idea of this technique is to use an index to find data that meets a criteria, 
 but aggregate data using original representation or full scans.
 
 ### Hierarchy Modeling Techniques
 #### Tree Aggregation
 Trees or even arbitrary graphs (with the aid of denormalization) can be modeled as a single record or document.

- This techniques is efficient when the tree is accessed at once (for example, an entire tree of blog comments is fetched to show a page with a post).
- Search and arbitrary access to the entries may be problematic.
- Updates are inefficient in most NoSQL implementations (as compared to independent nodes).

#### Adjacency Lists
Adjacency Lists are a straightforward way of graph modeling – each node is modeled as an independent record that contains arrays of direct ancestors or descendants. 
It allows one to search for nodes by identifiers of their parents or children and, of course, to traverse a graph by doing one hop per query. This approach is usually 
inefficient for getting an entire subtree for a given node, for deep or wide traversals.

source: 
https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/?utm_source=tuicool
https://highlyscalable.wordpress.com/2012/03/01/nosql-data-modeling-techniques/
 
 
 
