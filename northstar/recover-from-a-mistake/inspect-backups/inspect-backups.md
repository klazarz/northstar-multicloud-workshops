# Find a recovery point

## Introduction

Alex asks: “Can we show Maya a trustworthy copy from before the change?” You will match the prepared recovery point to the incident timeline before choosing it.

Estimated lab time: 15 minutes.

### Objectives

* Locate the assigned source database's backups.
* Compare the verified backup time with the seed and incident times.

### Prerequisites

* The source resource and backup provenance handoff, the seed commit time, and the incident times from Lab 1.

## Task 1: Inspect the backup evidence

1. In the Azure portal, open your assigned practice source and select **Settings > Backups**. Confirm the resource is the source from your handoff.
2. Find the owner-verified backup timestamp. Record the displayed time and its time zone, then compare its UTC equivalent with your notes. The backup list and clone selection can display different time zones: the clone documentation notes the list uses the Azure account time zone while the clone timestamp dropdown uses the database time zone, UTC by default. Ask the facilitator to resolve any ambiguity before proceeding.
3. Confirm the chosen backup is eligible for cloning, comes from this source, and falls **after** the seed commit and **before** your incident. The prepared clone's provenance must point to that same backup. If you cannot establish all of these facts, stop and ask for a verified handoff. Do not assume a newly created database already has a suitable backup.

## Task 2: Choose the recovery approach

A backup clone creates a **separate database** containing the selected backup's data. A restore changes the database being restored. This workshop uses a copy so you can compare the two states; do not select **Restore** on the source. A backup timestamp is a selected backup, not a promise that an arbitrary point in time can be used for a backup clone.

Write a short timeline: seed committed → eligible backup → practice mistake committed. Explain why this backup is a candidate, while remembering that the data in the clone still needs validation.

## Learn more

* [Automatic backups](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azubu-backup-autonomous-ai-database-serverless-automatic.html)
* [Clone from a backup](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azurs-restore-autonomous-ai-database-serverless-clone.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
