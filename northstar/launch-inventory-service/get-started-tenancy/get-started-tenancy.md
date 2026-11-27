# Get Started

## Introduction

Prepare to use your organization's Azure and OCI environment. Complete the following checks before beginning the timed labs.

Estimated lab time: 10 minutes, after administrators have prepared the environment.

### Objectives

* Identify the resources and permissions approved for this workshop.

### Prerequisites

* Oracle Autonomous AI Database Serverless on Azure running Oracle AI Database 26ai. Confirm the version with your environment owner before running the SQL.

* An Azure subscription entitled for Oracle AI Database@Azure, linked OCI access as appropriate, and an approved supported region, resource group and budget.
* Permission to inspect the network and create and view a database, or a designated administrator to perform those actions.
* An existing Azure virtual network and delegated subnet approved for this workshop, and an approved browser or remote client with private network access to Database Actions.
* An available, nonproduction fallback Autonomous AI Database Serverless instance on Azure, with a dedicated workshop user, Database Actions access, CREATE TABLE privilege and storage quota. Its schema must not contain `NS_INVENTORY`.

## Task 1: Record your workshop details

1. Sign in to the Azure portal using your approved account. Record the subscription, resource group, region, virtual network, delegated subnet, and the database name reserved for your use. Use an approved private place for notes; do not put account identifiers in public comments.
2. Confirm your administrator has prepared the OCI console access and network path used to reach Database Actions. Obtain the fallback database name, user-specific Database Actions URL, and workshop credentials through an approved channel.
3. Confirm who will create a dedicated workshop user on the new database after provisioning. The user needs Database Actions web access, CREATE SESSION and CREATE TABLE privileges, and DATA tablespace quota. The facilitator guide describes the preparation.
4. Confirm the budget, licensed model, resource settings, and who owns cleanup. If a required permission or access path is missing, resolve it before continuing. Do not alter shared network resources.

You may now **proceed to the next lab**.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
