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

* there are no master
* slave
* replica sets.

## Replication Factor

The Replication Factor \(RF\) is equivalent to the number of nodes where data \(rows and partitions\) are replicated. Data is replicated to multiple \(RF=N\) nodes. An RF of one means there is only one copy of a row in a cluster, and there is no way to recover the data if the node is compromised or goes down. RF=2 means that there are two copies of a row in a cluster. An RF of at least three is used in most systems

## Consistency Level

The Consistency Level \(CL\) determines how many replicas in a cluster must acknowledge a read or write operation before it is considered successful.

Some of the most common Consistency Levels used are:

* `ANY` – A write must be written to at least one replica in the cluster. A read waits for a response from at least one replica. It provides the highest availability with the lowest consistency.
* `QUORUM` – When a majority of the replicas respond, the request is honored. If RF=3, then 2 replicas respond. QUORUM can be calculated using the formula \(n/2 +1\) where n is the Replication Factor.
* `ONE` – If one replica responds; the request is honored.
* `LOCAL_ONE` – At least one replica in the local data center responds.
* `LOCAL_QUORUM` – A quorum of replicas in the local datacenter responds.
* `EACH_QUORUM` – \(unsupported for reads\) – A quorum of replicas in ALL datacenters must be written to.
* `ALL` – A write must be written to all replicas in the cluster, a read waits for a response from all replicas. Provides the lowest availability with the highest consistency.

## Sharding in Scylla DB

Each Scylla [node](https://university.scylladb.com/topic/node/) consists of several independent shards, which contain their share of the node’s total data. Scylla creates a one shard per core \(technically, one shard per [hyperthread](https://en.wikipedia.org/wiki/Hyper-threading), meaning some physical cores may have two or more virtual cores\). Each shard operates on a [shared-nothing architecture](https://en.wikipedia.org/wiki/Shared-nothing_architecture) basis. This means each shard is assigned its RAM and its storage, manages its [schedulers for the CPU and ](https://www.scylladb.com/2018/04/19/scylla-i-o-scheduler-3/)I/O, performs its compactions \(more about compaction later on\), and maintains its multi-queue network connection. Each shard runs as a single thread, and communicates asynchronously with its peers, without locking.

## Other Important Concepts

### Partition Key

A **Partition Key** is one or more columns that are responsible for data distribution across the nodes. It determines in which nodes to store a given row. As we will see later on, typically, data is replicated, and copies are stored on multiple nodes. This means that even if one node goes down, the data will still be available. It ensures reliability and fault tolerance

### Node

A Node is a unit of storage in Scylla. It is comprised of the Scylla database server software running on a computer server — a physical machine — and all its subsystems \(CPUs, memory, storage, network interfaces and so on\), or, in a virtualized environment, a subset of a server’s resources assigned to a container.

### Cluster

A minimum Cluster typically consists of at least 3 nodes. Data is replicated across the cluster, depending on the Replication Factor

### Table

A Table is how Scylla stores data and can be thought of as a set of rows and columns.

### Keyspace

A Keyspace is a collection of tables with attributes that define how data is replicated on nodes. It defines several options that apply to all the tables it contains, most prominently of which is the replication strategy used by the Keyspace. It is generally encouraged to use one Keyspace per application, and thus a Cluster may define only one Keyspace.

### CQL

A query language for interacting with the Scylla \(or Cassandra\) database.

### CQL Shell

A command-line interface for interacting with Scylla through the Cassandra Query Language \(CQL\)

### Replication

The process of replicating data across Nodes in a Cluster.

### Consistency Level

A configurable setting which dictates how many replicas in a Cluster must acknowledge read or write operations.

### Tunable Consistency

The possibility for unique, per-query, Consistency Level settings. These are incremental and override fixed database settings intended to enforce data consistency. Such settings may be set directly from a CQL statement when response speed for a given query or operation is more important.

### Replication Factor

The total number of replica Nodes across a given Cluster. A Replication Factor of 1 means that the data will only exist on a single Node in the Cluster and this setup will not have any fault tolerance. The Replication Factor is set for each Keyspace. All replicas share equal priority; there are no primary or master replicas.

### CAP Theorem

The CAP Theorem is a concept that states that a distributed database system can only have 2 of the 3: Consistency, Availability, and Partition Tolerance.

### Token Ranges

Each [node](https://university.scylladb.com/topic/node/) in a ring is assigned a range. The [hash function](https://en.wikipedia.org/wiki/Hash_function) computes a token for a given partition key. The hash function determines the placement of the data in the [cluster](https://university.scylladb.com/topic/cluster-node-ring/).

Without using **Vnodes** or virtual nodes, each node could only support one token range. By using vnodes, each node can support multiple, non-contiguous token ranges. By doing this, we can think of each physical node as hosting many virtual nodes. By default, each node has 256 virtual nodes.

### Gossips

Scylla, like Apache Cassandra, uses a type of internode communication protocol called Gossip.

For [nodes](https://university.scylladb.com/topic/node/) to exchange information with each other. Gossip is decentralized, and there is no single point of failure. It’s used for peer node discovery and metadata propagation. Gossip communication occurs periodically. Each node communicates with three other nodes. Eventually \(within a few seconds\), the information is propagated throughout the [cluster](https://university.scylladb.com/topic/cluster-node-ring/). To see whether a node is communicating using Gossip, we use the _**statusgossip**_ command:  


## Cluster Level Read/Write Interaction

So what happens when data is read or written at the [cluster](https://university.scylladb.com/topic/cluster-node-ring/) level? Note that what happens at the [node](https://university.scylladb.com/topic/node/) level will be explained in another lesson.

Since each node is equal in Scylla, any node can receive a read/write request. These are the main steps in the process:

![](https://university.scylladb.com/wp-content/uploads/2019/01/Read_Write_Cluster_Path.png)

1. A client connects to a Scylla node using CQL shell and performs a CQL request
2. The node the client connected to is now designated as the Coordinator Node. The Coordinator Node, based on [hashing](https://en.wikipedia.org/wiki/Hash_function) the data, using the partition key and on the [Replication Strategy](https://university.scylladb.com/topic/replication-strategy/), sends the request to the applicable nodes. Internode messages are sent through a messaging queue in an asynchronous way.
3. The [Consistency Level](https://university.scylladb.com/topic/consistency-level-cl/) determines the number of nodes the coordinator needs to hear back from, in order for the request to be successful.
4. The client is notified if the request was successful.

