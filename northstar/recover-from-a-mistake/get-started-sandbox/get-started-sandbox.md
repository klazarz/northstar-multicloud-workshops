# Get Started

## Introduction

Use the resources and access instructions supplied with your Run on Multicloud reservation. The provider must prepare and verify the recovery resources before the session.

Estimated lab time: 10 minutes.

### Objectives

* Identify the assigned practice source, backup and prepared recovery copy.
* Confirm access and permitted actions before changing practice data.

### Prerequisites

* Oracle Autonomous AI Database Serverless on Azure running Oracle AI Database 26ai. Confirm the version with your environment owner before running the SQL.

* A reservation that provides an isolated Oracle Autonomous AI Database Serverless on Azure with the six-row practice snapshot, an eligible backup and a separate prepared clone from that backup, created and validated before the practice mistake.
* Azure backup visibility, SQL access to both databases, approved network paths and a named support contact. The provider must also identify whether creating a new clone is permitted and feasible.

## Task 1: Open your assigned environment

1. Follow the reservation instructions to sign in. Find your assigned practice source and prepared recovery copy in the named Azure subscription and resource group. They must be distinct and isolated for you. Do not alter the shared or working database from an earlier workshop.
2. Locate the approved SQL connection or Database Actions URL, user credentials and expected database identifier and user for each database. Confirm you can connect from the supplied client. Keep credentials and private connection details out of your notes.
3. Record the snapshot commit time and eligible backup timestamp in UTC, and the prepared copy's source and backup timestamp. Verify the snapshot was committed before that backup and the copy comes from that source and backup. Find the provider's clone settings, permission and budget guidance, waiting cutoff and cleanup contact.
4. In Azure, confirm you can view the source's **Settings > Backups**. If an item is missing, contact the facilitator or reservation support before proceeding; do not choose a substitute database or backup.

The provider must confirm this particular Run on Multicloud reservation supplies these Azure resources and capabilities; a generic OCI sandbox does not establish that support.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
