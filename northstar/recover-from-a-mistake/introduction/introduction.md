# Introduction

## About this workshop

Northstar Outfitters is preparing for a promotion. Maya, the inventory operations lead, notices that the Trail Backpack suddenly appears to have no stock. The previous inventory report showed 12 units. Was the inventory really depleted, or did someone change the record by mistake?

Alex, the cloud database specialist, asks you to investigate on an isolated practice database, find a trustworthy backup, and recover a copy of the earlier data. Maya needs evidence she can use to decide what to do next. Northstar, the characters and the inventory data are fictional.

**Estimated time:** 90 minutes after environment preparation. You can continue from the earlier workshops or start with an equivalent prepared environment. The exercise uses a separate practice database; it does not restore or alter the earlier inventory service.

### Objectives

* Reproduce and investigate an inventory mistake safely in an assigned practice database.
* Identify a backup taken after the sample data was saved and before the mistake.
* Create a database clone from that backup, or use a verified recovery copy prepared from it.
* Compare the affected record and inventory report on the source and recovery copy.
* Explain the evidence, limitations and next action to Maya.

### Prerequisites

* Completion of the QuickStart and **Launch the Inventory Service**, or equivalent experience navigating Azure and running SQL. **See and Scale the Service** is useful but not required.
* An isolated, nonproduction Oracle Autonomous AI Database Serverless on Azure, with a dedicated practice schema, a verified eligible backup, and access to a separately prepared backup clone. See your Get Started lab for the full handoff.
* Azure access to inspect backups and SQL access to both databases. Creating a new clone also requires the permissions, quota, network, budget and configuration supplied by the environment owner.

## Learn more

* [Automatic backups](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azubu-backup-autonomous-ai-database-serverless-automatic.html)
* [Clone from a backup](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azurs-restore-autonomous-ai-database-serverless-clone.html)
* [Restore an Autonomous AI Database](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azurs-restore-autonomous-ai-database-serverless-restore.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
