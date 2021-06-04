---
description: pr0
---

# Cassandra : Scylla

### Setup : Docker

```bash
sudo docker run --name scyllaTest -d scylladb/scylla
sudo docker exec -it scyllaTest nodetool status
sudo docker exec -it scyllaTest cqlsh
```

Scylla runs nodes in a hash ring. All nodes are equal: 
- there are no master
- slave
- replica sets.

## Replication Factor
The Replication Factor (RF) is equivalent to the number of nodes where data (rows and partitions) are replicated. Data is replicated to multiple (RF=N) nodes.
An RF of one means there is only one copy of a row in a cluster, and there is no way to recover the data if the node is compromised or goes down. RF=2 means that there are two copies of a row in a cluster. An RF of at least three is used in most systems

## Consistency Level
The Consistency Level (CL) determines how many replicas in a cluster must acknowledge a read or write operation before it is considered successful.

Some of the most common Consistency Levels used are:

- `ANY` – A write must be written to at least one replica in the cluster. A read waits for a response from at least one replica. It provides the highest availability with the lowest consistency.
- `QUORUM` – When a majority of the replicas respond, the request is honored. If RF=3, then 2 replicas respond. QUORUM can be calculated using the formula (n/2 +1) where n is the Replication Factor.
- `ONE` – If one replica responds; the request is honored.
- `LOCAL_ONE` – At least one replica in the local data center responds.
- `LOCAL_QUORUM` – A quorum of replicas in the local datacenter responds.
- `EACH_QUORUM` – (unsupported for reads) – A quorum of replicas in ALL datacenters must be written to.
- `ALL` – A write must be written to all replicas in the cluster, a read waits for a response from all replicas. Provides the lowest availability with the highest consistency.

## Other Important Concepts

### Node
A Node is a unit of storage in Scylla. It is comprised of the Scylla database server software running on a computer server — a physical machine — and all its subsystems (CPUs, memory, storage, network interfaces and so on), or, in a virtualized environment, a subset of a server’s resources assigned to a container.

### Cluster
A minimum Cluster typically consists of at least 3 nodes. Data is replicated across the cluster, depending on the Replication Factor

### Table
A Table is how Scylla stores data and can be thought of as a set of rows and columns.

### Keyspace
A Keyspace is a collection of tables with attributes that define how data is replicated on nodes.  It defines several options that apply to all the tables it contains, most prominently of which is the replication strategy used by the Keyspace. It is generally encouraged to use one Keyspace per application, and thus a Cluster may define only one Keyspace.

### CQL
A query language for interacting with the Scylla (or Cassandra) database.

### CQL Shell
A command-line interface for interacting with Scylla through the Cassandra Query Language (CQL)

### Replication
The process of replicating data across Nodes in a Cluster.

### Consistency Level
A configurable setting which dictates how many replicas in a Cluster must acknowledge read or write operations.

### Tunable Consistency
The possibility for unique, per-query, Consistency Level settings. These are incremental and override fixed database settings intended to enforce data consistency. Such settings may be set directly from a CQL statement when response speed for a given query or operation is more important.

###  Replication Factor
The total number of replica Nodes across a given Cluster. A Replication Factor of 1 means that the data will only exist on a single Node in the Cluster and this setup will not have any fault tolerance. The Replication Factor is set for each Keyspace. All replicas share equal priority; there are no primary or master replicas.

### CAP Theorem
The CAP Theorem is a concept that states that a distributed database system can only have 2 of the 3: Consistency, Availability, and Partition Tolerance.