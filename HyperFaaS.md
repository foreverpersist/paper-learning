# [HyperFaas: A Truly Elastic Serverless Computing Framework](https://cs.gmu.edu/~yuecheng/docs/nsdi19_hyperfaas.pdf)

## Problem

State-of-art open-source platform ([Alex Ellis](https://goo.gl/c8mnD2), [Fission](https://goo.gl/VJKbGV)) heavily rely on container orchestration frameworks such as Kubernetes for container resource scheduling, which is orginally designed for managing `long-running` applications such as Memcached. Kubernetes' container scheduling and auto-scaling protocol is too `heavyweight` to realize `instant` resource provisioning

## Scene

**Bursty Workloads**:

Highly-concurrent function workload sees reduced response time after 40 seconds and stabilizes after 120 seconds

## Design

Optimization such as container caching can not fundamentally solve the problem, because bursty workloads can exhaust the container cache pool quickly, resulting in excessive container provisioning afterward

Goals:

> * Maximize the `resource utilization` and `efficiency` through **hierarchical scheduling** and **container sharing**
> * Minimize `performance loss` due highly-concurrent bursty function workloads viar **transient resource scaling-up**

Overview:

```
	            --------------------
	            | Global Scheduler |
	            --------------------
	                /          \
	               /            \
	--------------------    --------------------
	| ---------------- |    | ---------------- |
	| | In-Container | |    | | In-Container | |
	| |   Scheduler  | |    | |   Scheduler  | |
	| ---------------- |    | ---------------- |
	| ---------------- |    | ---------------- |
	| |  Function A  | |    | |  Function B  | |
	| ---------------- |    | ---------------- |
	| ---------------- |    | ---------------- |
	| |   Generic    | |    | |   Generic    | |
	| ---------------- |    | ---------------- |
	--------------------    --------------------
```
