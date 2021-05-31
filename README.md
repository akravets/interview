# System design

Keep it simple. Creating distributed systems is expensive both money wise and maintenance/resource wise. If something can be made in a single system, then it's better approach initially.

# Distributed System Characteristics

  - **No shared clock:** Difference in time (clock drift), issue with ordering of events and communication between nodes
  - **No shared memory:** Request for additional memory
  - **Shared resources:** Data between nodes should be shared
  - **Concurrency and consistency**

## Issues
  - Clients can't find server
  - Server crashes mid request
  - Server response is lost
  - Client crashes

## Benefits

  - More reliable, fault tolerant (replicas)
  - Scalability (horizontal - add more machines)
  - Lower latency, increase performance (processes distributed across multiple machines)
  - Cost effective

## Scalability

  - Achieve growth without loss of performance
  - Increased volume of data or requests

## Reliability

  - Probability a system will fail during a period of time
    - **MTBF:** Mean Time Before Failure **(prediction of when system will fail)** = (Total Elapsed Time - total downtime) / number of failures
  - Harder to define than hardware reliability, since hardware failure is more apparent

## Availability

  - Amount of time system is operational during period of time
  - Minimal downtime for maintenance

## Latency

  - Avoid network calls whenever possible
  - Replicate data across data centers for recovery and performance
  - Keep frequently accessed data in memory rather than in cache ro disk
