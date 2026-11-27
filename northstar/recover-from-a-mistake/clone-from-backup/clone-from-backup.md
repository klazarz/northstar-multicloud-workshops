# Create a recovery copy

## Introduction

Alex proposes a separate copy so Maya can inspect earlier inventory without overwriting the current source. Depending on your environment and time available, you will create a clone or use the verified copy prepared from the same backup.

Estimated lab time: 20 minutes.

### Objectives

* Select the verified source and backup for a recovery copy.
* Track a new clone or identify the prepared copy and its provenance.

### Prerequisites

* The verified timeline and backup from Lab 2, and the prepared copy handoff. A new clone requires owner-approved settings, permissions, quota, budget, network access and a unique resource name.

## Task 1: Decide which copy to use

Check the environment owner's instructions and the session cutoff. If clone creation is permitted and there is sufficient time and capacity, follow Task 2. Otherwise, go directly to Task 3. Either route can complete the investigation. A prepared copy shows a prior backup clone; it does not mean you created one during this workshop.

## Task 2: Create a clone from the verified backup

1. In the Azure portal, open the assigned **practice source**, then **Settings > Backups**. Select **Create clone from backup**.
2. On **Basics**, choose **Clone from a backup** as the clone source. Choose the verified backup timestamp from Lab 2, checking its displayed time zone against the owner's UTC mapping. If the exact backup is unavailable or the time is unclear, cancel the form and use Task 3; do not select a guessed timestamp.
3. Enter the unique resource name and remaining settings supplied by the environment owner. Check the subscription, resource group, network, configuration and cost authorization against the handoff. Submit only if all match and clone creation is permitted.
4. Record the submitted clone's name, source, selected backup timestamp, time zone and status. Monitor the existing request; do not submit another if it is slow. If the clone is available and the owner has supplied a working SQL connection, user and verified resource-to-URL and database identifier mapping, use it in the next lab. Otherwise, record the pending or failed status and responsible follow-up owner, and use Task 3. Do not wait beyond the session cutoff.

## Task 3: Use the prepared recovery copy

Identify the supplied prepared copy. Check its resource name, source, backup timestamp and creation/validation record against the handoff and your timeline. It must be the copy made from the verified pre-incident backup of your practice source. If provenance or access cannot be verified, stop and contact the facilitator; an unverified copy is not evidence of this recovery.

Record **prepared copy** as the route used, and carry its SQL connection details securely into the next lab. If you also submitted a new clone, record its current state and its owner for follow-up and cleanup.

You may now **proceed to the next lab**.

## Learn more

* [Clone from a backup](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azurs-restore-autonomous-ai-database-serverless-clone.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
