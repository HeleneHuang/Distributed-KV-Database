# System Overview

This system is designed and implemented as a high-performance, highly available, and strongly consistent distributed key-value (K-V) storage system. It supports massive data storage and fast access, while ensuring data consistency and system stability. The system is built with the following key objectives:

- High Availability: Ensure that the system can continue providing services even in the presence of partial node failures.
- Strong Consistency: Guarantee data consistency and synchronization across all nodes.
- Horizontal Scalability: Support seamless scaling to accommodate data growth and evolving business requirements.
- Performance Optimization: Improve read/write performance and reduce latency through various optimization techniques.

# System Architecture Overview

The system adopts a Multi-Raft architecture based on the Raft consensus algorithm, where data is partitioned into multiple shards, each managed by an independent Raft Group. This design enables data migration between different Raft Groups, supporting load balancing and fault recovery.
<img width="676" height="640" alt="image" src="https://github.com/user-attachments/assets/70c95fc4-3b68-43fa-9592-e5025efc2bc8" />

## Core Components:

- Raft Group: Ensures consistency and availability for each data shard.
- Leader Node: The primary node within a Raft Group, responsible for handling write requests and log replication.
- Follower Node: Replica nodes that receive log replication from the leader and participate in leader elections.
- Log Replication: Ensures that follower nodes remain consistent with the leader.
- Snapshot Updates: Periodically create data snapshots to reduce log storage requirements and accelerate recovery.

# Key Features

- Shard Partitioning with Multi-Raft Architecture: Data is divided into multiple shards, each managed by a Raft Group, improving scalability and load balancing.
- Data Migration: Supports migration of data across Raft Groups for dynamic load balancing and fault recovery.
- Linearizable Read/Write Operations: Provides a linearizable K-V interface to guarantee strong consistency for client operations.
- Performance Optimizations: Enhancements such as asynchronous apply, ReadIndex, follower reads, and PreVote improve Raft’s performance and response time.
- Pluggable Storage Engines: Supports multiple underlying storage engines including RocksDB, B+ Trees, and hash tables, to meet diverse storage requirements and performance needs.
