# Facilitator guide: Recover from a Mistake

The SQL in this workshop targets Oracle AI Database 26ai. Confirm the source, fallback and any recovery copy run 26ai before the session; do not assume the Azure service selects this version by default.

## Status and timing

This is a draft for live validation. The 90-minute learner session assumes all preparation is complete: Get Started 10 minutes, investigation 15, backup inspection 15, clone 20, validation 20, and handoff 10. The prepared-copy route supports a complete outcome if clone creation or access is unavailable during the session. It is not evidence that the learner created a new clone.

## Prepare the practice source

1. Assign each learner an isolated, nonproduction Oracle Autonomous AI Database Serverless on Azure and a dedicated practice account and schema. Do not use the earlier workshops' shared or working database as the source. Obtain the Azure subscription, resource group, source resource name, owner, approved client path and user-specific SQL URL. Capture the result of `SELECT SYS_CONTEXT('USERENV','DB_NAME'), USER` as the expected source identity and map it to the Azure resource and URL; do not assume the database identifier equals the Azure name.
2. In a clean schema with quota and CREATE TABLE privilege, create the table and seed the snapshot below. Do not drop or replace existing data. Record the UTC time immediately after the seed commit. Verify the six rows and Trail Backpack value 12. Ensure the learner's practice account can select and update the table.

    ```sql
    CREATE TABLE ns_inventory (
      product_id NUMBER PRIMARY KEY,
      product_name VARCHAR2(60) NOT NULL,
      available_units NUMBER NOT NULL,
      promotion_demand NUMBER NOT NULL
    );
    INSERT INTO ns_inventory (product_id, product_name, available_units, promotion_demand)
    VALUES
        (101, 'Trail Backpack', 12, 30),
        (102, 'Insulated Bottle', 50, 40),
        (103, 'Rain Jacket', 8, 20),
        (104, 'Hiking Socks', 100, 100),
        (105, 'Camping Lantern', 5, 15),
        (106, 'Daypack', 35, 25);
    COMMIT;
    SELECT TO_CHAR(SYSTIMESTAMP AT TIME ZONE 'UTC',
                   'YYYY-MM-DD HH24:MI:SS TZH:TZM') AS seed_committed_by_utc;
    ```

    Execute the statements individually as appropriate for the client. If continuing from a previous workshop, copy or seed its fictional snapshot into this separate practice source; do not assume a fallback from the earlier workshop populated a newly created database.
3. Wait for and verify an eligible automatic backup **after** the seed commit. A suitable backup may not exist immediately; complete this outside the timed session. Confirm the backup is offered for cloning and record the exact source and selected backup timestamp, its displayed time zone and UTC equivalent. Automatic backups have a configurable retention period; confirm the chosen backup remains available throughout the session. Ordinary manual backups are not currently supported for this service; do not substitute an assumption of an instant manual backup. Ad hoc long-term backup is a distinct feature, not an assumed shortcut.
4. Before the learner's practice mistake, create a separate prepared clone from that exact backup using the documented Azure backup-clone flow. Record clone resource identity, source, selected backup timestamp and time zone, creation time and status. Verify it contains all six rows and Trail Backpack 12, and record a successful access check. Keep the prepared copy isolated per learner. Protect it from modification during the exercise; use a read-only account where feasible. For a separate read-only schema, grant SELECT on the practice owner’s table and configure a private NS_INVENTORY synonym pointing to that table, then verify all unqualified learner queries as that account. Alternatively use the table-owning account under an agreed no-write procedure. Supply a usable connection, account and expected identifier mapped to the clone. Cloned database users, network paths and Database Actions access must be verified rather than assumed.
5. Provide each learner a private handoff: source and prepared copy resource names and resource groups; mapped database identifiers and SQL users; approved SQL URLs/client; seed commit and eligible backup times in UTC; exact copy provenance and validation; credentials through approved secure channels; support contact; and ownership, lifetime and cleanup instructions. Recheck that source and copy are distinct and the source is still in the initial state before the session. Do not distribute passwords in the guide.

## Decide whether learners can create another clone

Confirm the Azure identity can inspect backups and, if the exercise allows it, create clones with adequate quota, access to the approved network and resource group, and an authorized budget. Supply a unique clone name, required settings, a practical waiting cutoff and a contact who can establish SQL access, configure the same table visibility and verify the new clone's resource-to-URL, database identifier and user mapping. Ensure the selected backup and settings match the handoff. Track all submissions, including those still provisioning at the cutoff; name an owner to monitor and clean them up. Do not resubmit an uncertain operation. If creation, SQL readiness, time or permission is insufficient, learners use the verified prepared clone. This route has provisioning and storage costs too; establish resource lifetime and cost ownership in advance.

## Delivery options

**Bring your own:** Verify service entitlement, permissions, region, quota, network and pricing with the owner's organization. Provision and validate the source, backup and prepared clone before class. Keep source, clone and learner identities isolated; coordinate any cleanup with the owners.

**Run on Multicloud:** Confirm with the provider that this specific reservation supplies the Azure service, backup visibility, isolated source and prepared clone, SQL connections and identities, sufficient lifetime and cost coverage. Verify whether a learner may create an additional clone, who provisions access, and how in-flight resources are tracked. Replace generic reservation instructions with the actual supported flow after verification. The existence of a generic OCI sandbox does not demonstrate this Azure scenario is available.

## Cleanup and handoff

The exercise intentionally leaves the source's practice row at zero. Preserve the earlier working service and any resource needed for the remaining learning path. The environment owner handles the source and every prepared or learner-created clone according to the approved retention and cleanup plan, including pending operations and costs. Do not silently reset or delete resources.

## Publication and quality

Pilot both entry routes end to end with representative learners, including a new clone and the prepared-copy route, real backup availability and age, timestamp conversion, SQL access, database identity mapping, clone readiness and the pending-operation handoff. Capture actual elapsed times, verify UI labels and accessible LiveLabs rendering, and add current redacted screenshots where they improve navigation. Confirm the support address and author credits. Obtain an independent rubric review, achieving at least 4.5/5 overall with no criterion below 4.0 and no critical unresolved defect. Neither a live pilot nor a verified final score has yet been completed.

## References

* [Automatic backups](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azubu-backup-autonomous-ai-database-serverless-automatic.html)
* [Manual backups](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azubu-backup-autonomous-ai-database-serverless-manual.html)
* [Long-term backups](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azubu-backup-autonomous-ai-database-serverless-ltr.html)
* [Clone from a backup](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azurs-restore-autonomous-ai-database-serverless-clone.html)
