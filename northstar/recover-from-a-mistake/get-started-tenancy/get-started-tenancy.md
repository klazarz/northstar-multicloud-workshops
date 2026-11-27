# Get Started

## Introduction

Prepare your own environment for an isolated recovery exercise. Your environment owner must complete the preparation in the facilitator guide before the 90-minute session.

Estimated lab time: 10 minutes.

### Objectives

* Identify the practice source, eligible backup and prepared recovery copy.
* Confirm access and ownership before changing practice data.

### Prerequisites

* Oracle Autonomous AI Database Serverless on Azure running Oracle AI Database 26ai. Confirm the version with your environment owner before running the SQL.

* A nonproduction Oracle Autonomous AI Database Serverless on Azure dedicated to this exercise, with the six-row inventory snapshot, and an eligible backup taken after the snapshot was committed.
* A separate, accessible, prepared clone from that same backup. It must have been created and validated before the practice mistake.
* Approved Azure and SQL access, client network paths, cost coverage and resource ownership. An owner-approved clone configuration, quota and creation permissions are needed for the optional new clone.

## Task 1: Collect the handoff

1. Obtain the Azure subscription, resource group and names of your assigned **practice source** and **prepared recovery copy**. They must be different databases and isolated for you. Do not use the previous workshop's shared or working database as the practice source.
2. Obtain each database's approved SQL connection or Database Actions URL, user credentials and expected database identifier and user. Ask how to reach them from the approved client; never paste credentials into workshop notes.
3. Record the snapshot commit time and the verified eligible backup timestamp, both in UTC, and the prepared copy's source and backup timestamp. Confirm the snapshot commit precedes the backup, and the copy comes from this source and backup. Also obtain the owner's clone settings, approved budget, cleanup owner and the cutoff for waiting on a clone.
4. Sign in to Azure and confirm that you can find the source and view **Settings > Backups**. Confirm you can connect to both databases. If any handoff or access is missing, ask your facilitator or environment owner before proceeding. Do not substitute another database or backup.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
