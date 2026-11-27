# Verify and hand off

## Introduction

Maya wants to know whether Northstar can use the database. Alex distinguishes an accepted creation request from an available resource and a successful user connection.

Estimated lab time: 15 minutes.

### Objectives

* Verify the resource status and the connection actually used.
* Give Maya an evidence-based handoff with ownership and next steps.

### Prerequisites

* The resource and request details from Labs 3 and 4, and the prepared fallback SQL connection from Get Started.

## Task 1: Check the result

1. Find the assigned new database in Azure if you submitted a request. Record its name, configuration, latest provisioning state and time. If it is not available, has failed, or you did not submit, use the prepared fallback. Do not repeat a request whose outcome is uncertain; record an owner for follow-up.
2. If the new database is available, use it only if its authorized administrator has created a dedicated workshop user, provided an approved network path and user-specific Database Actions URL, and verified SQL access. Otherwise use the fallback. An available Azure resource alone does not prove a SQL user or connection is ready.
3. Connect to the database actually selected, open **SQL** and run:

    ```sql
    <copy>
    SELECT USER AS workshop_user;
    </copy>
    ```

    Compare the result and connection with the owner's handoff. If they do not match, stop and ask for help. Record whether this was the new or the prepared database. No inventory table is assumed to exist in a newly created database.
4. Give Maya a small, table-free calculation using fictional figures. Run:

    ```sql
    <copy>
    SELECT 'Trail Backpack' AS product, 12 AS available_units,
           30 AS promotion_demand, 30 - 12 AS units_short;
    </copy>
    ```

    **Expected:** one row showing `Trail Backpack`, 12 available, demand 30 and a shortfall of 18. This confirms the chosen 26ai database can evaluate a simple business calculation; it does not load an inventory table or reflect live stock.

## Task 2: Give Maya the handoff

Summarize:

* **Creation method and network:** the selected Azure route, VNet/subnet and delegation verified; whether the subnet was prepared or created.
* **Database:** the approved configuration, resource name, and last observed state. Say whether a request was submitted, not submitted, pending, failed or available.
* **SQL evidence:** the database actually used, the verified workshop user and the sample calculation result. A fallback connection proves the fallback works; it does not prove that the new database is usable.
* **Next step and owner:** access setup, outstanding provisioning, review of costs and any cleanup. Keep resources needed for the rest of the learning path; follow the owner's cleanup plan and do not delete shared networks.

Tell Maya what is ready and what still needs work. You have completed the workshop when you have a validated SQL connection to the new or prepared 26ai database and an honest handoff. If the fallback is not accessible, record the blocker and ask the facilitator for help.

## Learn more

* [Connect to Autonomous AI Database Serverless on Azure](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucn-connect-c-autonomous-ai-database-serverless.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
