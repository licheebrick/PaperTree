# classbench

## Basic
* ClassBench: a packet classification benchmark
* 2005, ToN, 400+ citations;
* J.S. Turner
* First Read: 16.12.7

## Best for reference:
* Detailed technical report for the implementation of classbench;
* Some working groups:
  - The IP Performance Metrics (IPPM): developing standard metrics for Internet data delivery;
  - The Benchmarking Methodology Working Group (BMWG): make measurement recommendations for various internetworking technologies.
* Stanford's Packet Lookup and Classification Simulator(PALAC) tools: A framework for comparative performance evaluation of vaious IP lookup and packet classification algorithms.

## Focus:
* Filter Set Analyzer
* Filter Set Generator
* Trace Generator

## Aspects of Contribution:
* Meet the needs for benchmarks in packet classification. Solved: Confidentiality issues, size and structure restrictions.
* Able to adjust some parameters in filter sets generation.

## Contents
### Base:
* 12 real filter sets;
  - Provided by Internet Service Providers, a network equipment vendor, and other research;
  - Size from 68 to 4557;
  - ACL, FW, IPC;
  - No supporting information regarding the types of systems and environments in which
they are used.

### Filter Composition
Two major components:
* An address prefix pair;
* An application specification(protocol, source port number, dst port number)

A detailed analysis:
* Application specification:
  - Protocol: Simply count the frequency of occurrance;
  - Port Ranges: 5 classes of port ranges: WC, HI, LO, AR, EM; Port Pair Class(PPC): port pair matrix. (A single PPC for each protocol;)
* Address Prefix Pairs:
  - Prefix length
  - Prefix contents -> branching probability on each level, and 'skew distribution', that is, the average weight difference of two branching on each level.
  - Source and Dst interdependence: measure the 'correlation' of source and dst prefixes: the probability that the source and destination address prefixes continue to be the same for a given prefix length.
* Scope
  - The scope this filter covers;
* Addicational Fields:
  - Beyond the standard 5-tuple.

### Parameter files entries:
--- Protocol specifications (For each protocol):

---|--- The distribution of filters of this protocol;

---|--- Port Pair Class Matrix for this protocol;

---|---|--- Each entry in PPC Matrix:

---|---|---|--- Source and Dst port distribution(For each entry);

---|---|--- Prefix pair length distribution;

---|---|---|--- Total prefix length distribution;

---|---|---|---|--- Source prefix length distributions; (for each specified total length)

---|--- Flags specifications for this protocol(For each Flag:)

---|---|---The distribution of filters over those values.

### Filter Set Generator
* Four high-level tune parameters: size, smoothing, port scope and address scope;
