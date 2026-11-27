# Introduction

## About this workshop

Northstar Outfitters is preparing for its promotion. In the QuickStart, you helped Maya, the operations lead, identify products that might run short. Maya now wants the team to repeat that analysis in a service they can manage through Azure.

Alex, Northstar's cloud database specialist, asks you to inspect the network, launch an Oracle Autonomous AI Database Serverless instance, and show that the inventory snapshot can be queried. You will record the database you actually used and give Maya a clear handoff.

**Estimated workshop time:** 90 minutes after the environment is prepared. Provisioning time varies; a prepared fallback keeps the final exercise possible if the new database is still provisioning. Creating resources may incur charges.

### Objectives

* Explain the role of the Azure virtual network and delegated subnet in the selected private access design.
* Select and submit an Autonomous AI Database Serverless configuration in Azure, and inspect its lifecycle status.
* Connect to an available workshop database, load a sample snapshot, and verify an inventory result.
* Identify whether the result came from the new database or a prepared fallback.

### Prerequisites

* Basic familiarity with a browser and SQL, such as the preceding QuickStart.
* The prepared Azure and OCI access, network, permissions, budget, and client connection described in the Get Started lab for your selected environment.
* A dedicated, nonproduction database or authorized creation of one, plus an available fallback database and isolated workshop schema if provisioning exceeds the session.

The QuickStart's sample data does not automatically appear in a newly created database. This workshop includes the data setup needed to run independently.

## Learn more

* [Create an Autonomous AI Database Serverless instance on Azure](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-autonomous-ai-database-serverless.html)
* [Create a delegated subnet](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-delegated-subnet.html)
* [Connect to Autonomous AI Database Serverless on Azure](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucn-connect-c-autonomous-ai-database-serverless.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
