# Prepare the launch

## Introduction

Maya asks, “Can we start creating now?” Alex explains that cloud onboarding and access, networking, and budget decisions come first. Your task is to make those dependencies visible, not to change organizational security settings.

Estimated lab time: 10 minutes.

### Objectives

* Record the boundaries and prerequisites for the assigned environment.
* Decide whether to create a new resource or use the prepared database.

### Prerequisites

* The environment handoff from Get Started.

## Task 1: Build a readiness card

1. Record the Azure subscription, resource group, region and database name supplied by the owner. Confirm that Oracle AI Database@Azure onboarding is complete and the selected region supports the service and the approved 26ai configuration. OCI tenancy linkage and identity onboarding are part of the broader service setup, even though this Serverless Azure resource is created through Azure.
2. Check that your Azure identity has the owner's approved database and network permissions. Oracle's [prerequisites](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-prerequisites.html) distinguish network and Autonomous Database administration. Ask the owner to resolve a missing grant; do not assign yourself broad roles.
3. Record the approved VNet, dedicated delegated subnet, IP range and access path. Confirm whether the network is pre-existing or you may create an isolated one. Determine who owns the network and any feature-registration decisions. Do not change a shared VNet or subnet.
4. Record the selected workload, 26ai, ECPU and storage settings, scaling, retention, license, network access and mTLS, maintenance, contacts, tags, budget and cleanup owner. Get approved values from the handoff rather than guessing. Record whether a new database is permitted and the cutoff for waiting.
5. Check that the prepared 26ai database, SQL user and client path are accessible. If creation is prohibited, waiting exceeds the cutoff, or a new database has no SQL user yet, this independently prepared database provides the final SQL checkpoint. The fallback does not demonstrate that a submitted database is ready.

**Checkpoint:** You have either an approved creation plan plus a fallback, or a prepared-resource plan with the creation limitation recorded.

## Learn more

* [Onboarding](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/oaaonboard.htm)
* [Service prerequisites](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-prerequisites.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
