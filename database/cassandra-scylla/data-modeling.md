---
description: and Application Development
---

# Data Modeling

In Scylla, as opposed to relational databases, the data model is based around the queries and not just around the domain entities. When creating the data model, we take into account both the conceptual data model and the application workflow: which queries will be performed by which users and how often.

Things to keep in mind when design Tables

* **Even data distribution**: data should be evenly spread across the cluster so that every **node** holds roughly the same amount of data. Scylla determines which node should store the data based on hashing the partition key. Therefore, choosing a suitable partition key is crucial. More on this later on.
* **To minimize the number of partitions accessed in a read query**: To make reads faster, we’d ideally have all the data required in a read query stored in a single [Table](https://university.scylladb.com/courses/scylla-essentials-overview/lessons/data-modeling/topic/table-and-basic-concepts/). Although it’s fine to duplicate data across tables, in terms of performance, it’s better if the data needed for a read query is in one table.



