## Persistence


-
-
### Database types

-
#### Relational Databases

- Mysql, sqlite, Postgresql
- Store data in rows in tables
- Most (but not all) use SQL or similar
- Tables have a fixed schema (set of columns)
- Changing schema is slow and costly

-
#### Schemaless databases

- eg: MongoDB
- Flexible semantics of entries in the DB
- Still have an implicit schema (code expects certain properties)
- Schema can change on the fly (requires careful management though)

-
#### Graph Databases

- eg: Neo4J
- Store data as a graph of relationships (eg Facebook's Social graph)


-
### Relational Engine implementation

-
#### Considerations

- large file store (too big for memory)
- Caching and recency
- Query optimization

-
#### Today's Focus

- Optimizing searching by indexing columns

-
-
## Indexing

-
### Context

- Searching values in a column requires reading every row  of the table
- Very large tables may be stored on disk, sometimes in multiple files
- Searching by columns other than ID is common
- Tables are often sorted by primary key

-
### Consequences

- Searches of large tables doesn't scale well ( `O(n)` )
- Reading from disk compounds this issue (IO is very slow)
- Any action that requires searching multiple tables becomes highly time consuming

-
### Solutions

- Duplicate tables sorted by different columns (different primary key)
  - Creates redundancy, overhead, and danger of inconsistencies
- Keep track of all values in a column and which rows they occur in (an index)

-
-
## Implementing indexes

-
### Requirements

- Indexes map column values to lists of row IDs
- Indexes must be accurate -- A missing key indicates that value does not exist in that column
- Searching should consult an index if one is present
- CRUD operations must update corresponding indexes.

-
### Implementation

- Store column values as keys in a map; lists of corresponding IDs as values
- Optimize storage with specialized data structures
  - Binary tree
  - B Tree or B+ Tree

-
### B Tree

- N-ary tree
- N varies by node
- Each node has N children
- Each node stores N-1 values

-
### B+ Tree

- Same structure as B Trees
- All values are stored on the leaf nodes
- Leaf nodes are linked, allowing quicker traversal

-
#### Exercise

[Persistence Challenge](https://gist.github.com/DavidGinzberg/c5ed1cc548080f3811cda81a1696231f)

-
-
### Resources

*** Coming soon ***

-
#### Topics not covered

*** Coming soon ***
