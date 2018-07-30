---
layout: post
title: What's the difference between a distributed hashtable and the bitcoin blockchain?
tags: p2p english dht blockchain
---

These are two distributed data structures which serve different
purposes but both are distributed and used to save data accross a
network.  Distributed means it uses a network where all peers are
collectively responsible for maintaining the structure. There is no
central authority. That has multiple effects compared to a centralized
data structure. The data structure is resiliant to failure, censorship
or any attack that can only target one entity.  If a peer leave the
network the data is still available.

## Distributed Hash Table

A DHT is simply a key-value store distributed accross a number of
nodes in a network. The keys are distributed among nodes with a
deterministic algorithm. Each node is responsible for a portion of the
hash table.

A routing algorithm allow to perform request in the hash table without
knowing every node of the network.

For exemple in the [Chord
DHT](https://en.wikipedia.org/wiki/Chord_%28peer-to-peer%29) each node
is assigned an identifier and is responsible of keys which are closer
to its identifier.

Imagine you have 4 nodes that have identifiers : 2a6c, 7811, a20f,
e9c3 The data with the identifier 2c92 will be stored on the node
2a6c.

Imagine now that you only know the node 7811 and you are looking for
the data with the identifier eabc.

You ask the node 7811 for the data eabc. 7811 doesn't have it so it
ask the node e9c3 wich send it to node 7811 which send it back to you.

A clever algorithm allows to find data in O(log(N)) jumps. Without
storing the entire routing table of the network (the addresses of each
nodes). Basically you ask the closest node to the data identifier you
know wich itself asks the closest node it knows and so on reducing the
size of the jump at each step.

A DHT is very scalable because the data are uniformly distributed
among nodes and lookup time generally grow in O(log(N)).

## Blockchain

A blockchain is also a distributed data structure but its purpose is
completely different.

Think of it as a history, or a ledger. The purpose is to store an
continuously-growing list of record without the possibility of
tampering and revision.

It is mainly used in the bitcoin currency system for keeping track of
transaction. Its property of being tamper-proof allows to know the
exact balance of an account by knowing its history of transaction.

In a blockchain, each node of the network stores the full data.  So it
is absolutely not the same idea as the DHT in which data are divided
among nodes.  Every new entry in the blockchain must be validated by a
process called mining, but I can't tell you more about it in
details. This process insure consensus of the data.

The two structures are both distributed data structure but serve
different purposes. DHT aims to provide a efficient (in term of lookup
time and storage footprint) structure to divide data on a network and
blockchain aims to provide a tamper-proof data structure.
