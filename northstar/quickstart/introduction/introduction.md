# Introduction

## About this workshop

Northstar Outfitters is preparing for a weekend promotion. Maya, the operations lead, needs to know which products might run out. The inventory team has supplied a snapshot, but the promotion starts tomorrow. Maya can request more stock today; she needs to know where to begin and how much is missing.

Alex, Northstar's cloud database specialist, has prepared an Oracle Autonomous AI Database Serverless instance on Azure. Alex asks you to connect, put the snapshot into a table, and find products whose stock is below the planned promotion quantity. You do not need to be a database expert: the SQL is provided and each step explains what it does.

Your role is to help Alex prepare the data and give Maya a recommendation supported by the numbers. At the end, you will identify the most urgent product and the total estimated shortfall. The data and company in this workshop are fictional.

**Estimated time:** 45 minutes, with the environment ready before you start.

### Objectives

In this workshop, you will:

* Identify your database and connect to its SQL worksheet.
* Create a table in your own workshop schema and add a small inventory snapshot.
* Query the snapshot to find products at risk of running short.
* Check the results and explain a practical action to Maya.

### Prerequisites

* An existing Oracle Autonomous AI Database Serverless instance in Oracle AI Database@Azure, available and reachable from your approved client. Provisioning is covered in the next workshop.
* A dedicated workshop database user and schema, authorized to sign in to Database Actions and create a table, with sufficient storage quota. The schema must not already contain an object called `NS_INVENTORY`.
* A Database Actions URL and the database username and password, provided through your organization's approved channel. Your browser must have network access to that URL. Private endpoints require an approved network path.
* Permission to use the environment and incur any associated charges. No production data is needed.

The Get Started lab for your selected environment explains how to connect. Then complete the two numbered labs.


## Learn more

* [Oracle AI Database@Azure connection guide](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucn-connect-c-autonomous-ai-database-serverless.html)
* [Oracle Database Actions](https://docs.oracle.com/en-us/iaas/autonomous-database-serverless/doc/connect-database-actions.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
