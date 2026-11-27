# Introduction

## About this workshop

Northstar Outfitters' inventory service is running, and the promotion is approaching. Maya, the operations lead, asks: “Will our team be able to see what happens when orders increase, and how will we decide whether to add capacity?”

Alex, the cloud database specialist, invites you to look at the service through Azure Monitor, run a small inventory query, examine its resource allocation, and recommend a measured response. Your job is to explain what the evidence supports and what still needs investigation. The story and data are fictional.

**Estimated workshop time:** 90 minutes with the environment prepared. A small query is unlikely to cause an obvious metric change or trigger auto scaling; a visible spike is not required for success.

### Objectives

* Record the database's current compute, storage and auto scaling settings.
* Explore Azure Monitor metrics for the selected database and describe their scope and time range.
* Run a bounded inventory query and compare observations without assuming it caused a metric change.
* Inspect resource allocation and, where permitted and preapproved, make and verify a small reversible compute change.
* Give Maya a capacity recommendation that includes evidence, uncertainty and cost considerations.

### Prerequisites

* Familiarity with the QuickStart and **Launch the Inventory Service**, or equivalent ability to navigate Azure and run a SQL statement.
* A ready, nonproduction Oracle Autonomous AI Database Serverless instance on Azure and the environment access described in Get Started. A standalone learner can use an equivalent prepared database.
* An isolated workshop schema containing the sample `NS_INVENTORY` table from the previous workshop, or a clean schema in which to create it. A Database Actions connection and Azure Monitor access are ready before the session.

## Learn more

* [Monitor Oracle AI Database@Azure with Azure Monitor](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azumn-monitor-azure-monitor.html)
* [Manage resource allocation in Azure](https://learn.microsoft.com/en-us/azure/oracle/oracle-db/oracle-database-manage-autonomous-database-resources)
* [Metrics for Oracle Autonomous Database in Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/oracle-database-autonomousdatabases-metrics)
* [Billing and resource metering](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azumn-monitor-billing.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
