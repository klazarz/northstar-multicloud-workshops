# Launch the inventory database

## Introduction

Maya asks Alex for a managed service the team can use throughout the promotion. Choose the approved configuration, start provisioning, and inspect the result.

Estimated lab time: 35 minutes, including time to inspect status. Actual provisioning may take longer.

### Objectives

* Configure and submit a database using the Azure portal.
* Identify whether provisioning completed or remains in progress.

### Prerequisites

* The assigned network and approved configuration from the previous lab.
* Creation permission and an available fallback database. Creating a database can incur charges; use only the approved subscription and settings.

## Task 1: Choose and submit the configuration

1. In the Azure portal, open **Oracle AI Database@Azure**, select **Oracle Autonomous Database**, and select **Create**. Interface labels can vary slightly. Choose database version **26ai** in the database configuration; if it is unavailable, stop and contact the environment owner.
2. On **Basics**, choose the approved subscription, resource group and region. Enter your assigned unique database name: letters and numbers only, starting with a letter, with no spaces and at most 30 characters.
3. On **Configuration**, choose **Transaction Processing** for the inventory workload and the approved available database version, ECPU count, storage, auto scaling, backup retention and license type. Use the approved settings and budget; do not assume Bring Your Own License applies. Create a strong ADMIN password following the form's requirements and store it through your approved method.
4. On **Networking**, select **Managed private virtual network IP only**, then select the assigned virtual network and delegated subnet. Use the approved mTLS setting and verify the prepared client supports it.
5. On **Maintenance**, use the approved patch and contact settings. Review the terms in **Consent** and follow your organization's authorization before accepting. Add any required tags.
6. On **Review + Create**, check the region, name, network, configuration, license and estimated cost according to your organization's process. Correct validation errors. Select **Create** once the settings are approved.

If the environment does not permit creation, ask the facilitator to perform it. Record that you observed the submission; do not claim to have created the resource yourself.

## Task 2: Check provisioning and choose your path

1. Return to the Autonomous Database list and open the new resource. Record its name and current lifecycle or provisioning state. Refresh the view as directed by the portal; do not submit a second database while the first is still in progress.
2. If it is available and the administrator has prepared its workshop user and connection, use the new database in the next lab. Record **new database** in your handoff notes.
3. If it is still provisioning, has failed, or its user or client path is not ready, use the prepared fallback for the next lab. Record **fallback database**, the reason, and the new resource's last observed state. Ask the facilitator or administrator to follow up on the original operation; a submitted request is not proof of an available database.

**Checkpoint:** You have either submitted and inspected a database creation or observed the facilitator do so, and you know which database you will use next.

You may now **proceed to the next lab**.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
