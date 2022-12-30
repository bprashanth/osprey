# Syn Net

Synchronization primitives for networks.

## Goals

* Create a connection manager capable of enforcing access to networking hardware via Locks
* Build tools to monitor and debug these locks

## Background

The linux networking stack has evolved to support a set of features for open systems like the World Wide Web.

Lately, tech teams have been deploying linux on closed systems (eg spaceX explorers, AR/VR systems, self driving cars and cluster intranets)[1].

Closed systems require determinism, latency and throughput guarantees. For example, they may not be able to degrade frame rate as bandwidth deteriorates, or fragment packets at the cost of latency.

However, a defining characteristic of closed systems is their ability to enforce global order.

The goal of this project is to allow such closed systems to coordinate and control congestion through explicit userspace APIs.

## Introduction

A "Network Lock" (NL) is something a discerning developer can use (eg as a software object) to ask the system for guarantees.

In return, the system will require certain guarantees from the user. These guarantees will take the form of a "Critical Section Contract" (CSC).

When faced with a conflict, eg a situation when a traditional system might throttle high throughput connections, the network manager will use the NL interface to pause connections per their CSCs.

CS metadata will be communicated to the NC manager via eBPF maps.

## Refrences

[1] [Challenges](https://ntrs.nasa.gov/api/citations/20200002393/downloads/20200002393.pdf) using the linux network stack for real-time communication, Michael M. Madde, NASA Langley Research Center

