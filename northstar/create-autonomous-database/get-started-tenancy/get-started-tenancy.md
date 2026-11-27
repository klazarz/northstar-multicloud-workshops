# Get Started

## Introduction

Bring your own Azure and Oracle AI Database@Azure environment. An environment owner must prepare the handoff before the timed session; onboarding and provisioning a fallback are not included in the 90 minutes.

Estimated lab time: 10 minutes.

### Objectives

* Identify the approved scope, tools and fallback database.

### Prerequisites

* An onboarded Oracle AI Database@Azure subscription, approved nonproduction resource group, region and networking, and the identities and permissions to perform your selected tasks.
* A reachable, available Autonomous AI Database Serverless on Azure running 26ai, a dedicated SQL user and its Database Actions URL. This fallback must be separate from a resource you create during the workshop.
* The owner's approved settings, budget, unique names, network access, CLI setup if applicable, cutoff time and cleanup owner.

## Task 1: Collect the environment handoff

1. Sign in using your organization's approved Azure identity. Record the subscription, resource group, region, approved VNet and delegated subnet, and the assigned new database name. Ask the owner whether you may create the database and whether a new network is allowed. If not, use the prepared resources described in the labs.
2. Locate the fallback database and its user-specific Database Actions URL. Connect using the dedicated account from the approved client. Never put passwords, tokens, wallet files or private URLs in shared notes.
3. Confirm your owner-provided configuration: database version 26ai; workload, compute, storage, auto scaling, backup retention, networking and mTLS; license entitlement, maintenance and tags. Confirm budget, quota, cleanup owner and session cutoff. Do not invent values.
4. If using Azure CLI, confirm the approved shell, signed-in account, subscription, installed CLI and `oracle-database` extension. For the Azure resource creation procedure, Oracle documents Azure CLI 2.87.0 or later and extension 2.0.4 or later. Follow your organization's authentication policy; do not paste credentials into commands or public notes.
5. If any required access or handoff is missing, contact the owner or facilitator before continuing. Do not alter shared networking to make the workshop work.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
