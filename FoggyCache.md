# [FoggyCache: Cross-Device Approximate Computation Reuse](https://dl.acm.org/citation.cfm?doid=3241539.3241557)

## Problem

The same applications are used by multiple devices over time, often in a similar context (e.g., common locations). redundancy elimination across devices can then simultaneously achive low latency and accurate results.

## Scene

Features of target scene:

> * **Similiar Input**
>> * Temporal Correlation
>> * Spatial Correlation
>> * Common Objects

> * **Error Tolerance**
>> * High-dimensional input are mapped to lower-dimensional output - Learning based workloads and graphics rendering

> * **Repeated Invocations**
>> * Popularity of some mobile apps
>> * Significant correlation exists spatio-temporal contexts and smartphone usage
>> * Different apps can invoke the same library functions

---

Example scenarios:

> * Smart Home - audio commands
> * Congitive assistant apps - tourists's image
> * Intelligent agriculture - Image and other sensor data

## Design

### A-LSH(Adaptive Locality Sensitive Hashing)

### H-kNN(Homogenized k Nearest Neighbors)

### Two-level Cache