# Get Started

## Introduction

Use the Azure resources and instructions supplied with your Run on Multicloud reservation. The provider must prepare the environment before the timed session.

Estimated lab time: 10 minutes.

### Objectives

* Identify the assigned scope, allowed actions and ready database.

### Prerequisites

* A reservation providing Oracle AI Database@Azure access, an approved nonproduction Azure scope and delegated subnet, and an available, reachable Autonomous AI Database Serverless on Azure running 26ai with a dedicated SQL user.
* Provider-supplied resource names, SQL URL and credentials, configuration, allowed actions, budget, cutoff and cleanup ownership. An approved authenticated shell and Azure CLI are needed for the CLI route.

## Task 1: Open your assigned environment

1. Follow the reservation instructions to sign in. Locate the Azure subscription, resource group, region, assigned VNet and subnet, and prepared database. Confirm whether the provider permits creation of a new database or network; otherwise follow the prepared-resource route.
2. Connect to the prepared database through its user-specific Database Actions URL and approved client. The provider supplies credentials securely. Do not publish passwords, tokens, wallet files or private URLs.
3. Find the approved database settings, unique name if creation is allowed, budget, quota, cutoff and support/cleanup contact. Confirm 26ai, workload, compute, storage, scaling, backup retention, networking, mTLS, license, maintenance and tags with the provider.
4. For Azure CLI, check that the approved shell is authenticated for the assigned subscription and has the supported CLI and extension. Oracle's procedure specifies Azure CLI 2.87.0 or later and `oracle-database` extension 2.0.4 or later.
5. If any prerequisite is missing, contact reservation support or the facilitator. Never change shared resources to compensate for missing access.

The provider must validate that this particular Run on Multicloud reservation supplies the Azure service and these capabilities; a generic OCI sandbox does not establish that support.

You may now **proceed to the next lab**.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
