---
layout: post
title: Paper Review &#35;1
---

<a href="http://www.vldb.org/pvldb/vol10/p373-wang.pdf">Lifting the Haze off the Cloud: A Consumer-Centric Market for Database Computation in the Cloud</a> by Wang et al., VLDB 2017. 

<!--more-->

**1) Biggest contribution:** Studies the problem of cost optimization in the cloud. The paper offers a framework for choosing a cloud provider on the basis of what it charges for computing a certain task (i.e. database workload) by a certain deadline. More specifically, the framework generates a pricing contract from one or more cloud providers that computes the price for performing a given task at a given time. The framework uses an agent approach to acquire knowledge of the resources, capacity, and pricing of cloud providers, allowing the user to choose the provider that offers the lowest price. 

In my experience, the practice of saving costs in the cloud is something that confuses customers, so I think it's a valid problem to study. For example, knowing what RIs to purchase to save money on AWS and when to purchase them can be quite daunting, especially at-scale. Doing it right often requires coordination between several groups within the organization as well as some additional tooling that aggregates resource utilization and spend. 

**2) Biggest mistake:** A key benefit of moving to the cloud is the elasticity, pay-as-you-go resources. Unfortunately, this paper proposes a pricing model that assumes the workload is known ahead of time. This is not a realistic assumption since many modern apps are dynamic by nature. These apps are constantly evolving, hench their workload is also in a state of flux. Moreover, the paper evaluates the pricing model only with TPC-H and MapReduce WordCount, Sort and Join. These benchmarks are so simple, they don't even come close to capturing the workloads of real apps. In short, I would have liked to have seen a more comprehensive evaluation study using some real sample apps, with a greater volume of data, run on a wider range of data management services. 

**3) Biggest question:** If we assume that customers are open to moving between cloud providers on the basis of cost savings (all other things being equal), then the question becomes, at what point does it make sense to recommend an alternative provider to run a given database workload? This is not a trivial question because not only are database workloads dynamic, but the efforts to migrate production databases are often complex and expensive. It seems like a framework that recommends a cloud provider over another should also account for the cost of migrating the workload. 