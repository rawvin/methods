---
title: "Consistency Algorithms"
date: 2020-09-13T21:10:59-05:00
tags: [Software Architecture, CAP, Consensus, Consistency, Replication]
---

When dealing with distributed database architectures in geo-replicated deployments, systems have to implement algorithms to ensure that they make the correct decision even if one or more processes have failed.

Here I've listed two of the popular approaches to achieving consistency.

## Consensus (Raft)

Raft is a leader-based consensus algorithm which guarantees strong consistency to the cluster. The consensus algorithm is divided into three parts - Leader election, Replication and Safety. Raft, compared to Paxos its predecessor, makes it easy to reason about the database in the single key context. Raft ensures that all operations are globally linearizable.

- Optimal when applied to - _Atomic transactions, Distributed messaging_
- Who is using - _Consul, Etcd, CockroachDB, InfluxDB_
- Weakness - _Network partitions_


## Convergence (CRDT)


_Conflict-free Replicated Data Types_ (CRDT) systems avoid the need for coordination by ensuring that actions taken independently can't conflict with each other and the state can be composed at a later point in time. The consistency model is _Strong Eventual Consistency_.

The operations must be commutative and idempotent in nature and can be handled either by replicating themselves or by execution at the primary with the resulting state replicated.

- Optimal when applied to - _Distributed counter, Collaborative Editing, Locality @Edge_
- Who is using - _Redis Enterprise, CloudFlare_
- Weakness - _Complexity_