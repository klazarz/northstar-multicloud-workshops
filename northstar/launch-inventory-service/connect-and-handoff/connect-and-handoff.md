# Connect and deliver the inventory result

## Introduction

Maya needs proof that the team can use the inventory service. Connect to the database selected in the previous lab, load the same fictional snapshot used in the QuickStart, and report the result and database status.

Estimated lab time: 30 minutes.

### Objectives

* Connect as the dedicated workshop user and verify the account.
* Load and query the snapshot and explain the result.
* Record whether the new or fallback database produced the result.

### Prerequisites

* An available database selected in the previous lab, a user-specific Database Actions URL and credentials, and an approved client network path.
* A dedicated workshop schema with CREATE TABLE privilege and quota. `NS_INVENTORY` must not already exist in this schema.

## Task 1: Connect and confirm your user

1. From the approved client, open the selected database's user-specific Database Actions URL. Sign in using the dedicated workshop database user and select **SQL**. For a newly created database, your administrator or facilitator must first create and enable the user and provide the URL; see the facilitator guide.
2. Run each SQL block separately with **Run Statement**. Start with:

    ```sql
    <copy>
    SELECT USER AS workshop_user;
    </copy>
    ```

3. Confirm that the result matches your assigned user. If it does not, stop and connect to the correct account.

## Task 2: Create and load the snapshot

Run the following statement once in the dedicated schema:

```sql
<copy>
CREATE TABLE ns_inventory (
    product_id       NUMBER PRIMARY KEY,
    product_name     VARCHAR2(60) NOT NULL,
    available_units  NUMBER NOT NULL,
    promotion_demand NUMBER NOT NULL
);
</copy>
```

If the name is already in use (`ORA-00955`), stop and request a clean workshop schema. Do not drop an existing table.

Run this statement once:

```sql
<copy>
INSERT INTO ns_inventory (product_id, product_name, available_units, promotion_demand)
VALUES
    (101, 'Trail Backpack', 12, 30),
    (102, 'Insulated Bottle', 50, 40),
    (103, 'Rain Jacket', 8, 20),
    (104, 'Hiking Socks', 100, 100),
    (105, 'Camping Lantern', 5, 15),
    (106, 'Daypack', 35, 25);
</copy>
```

Save the data, then check the number of rows:

```sql
<copy>
COMMIT;
</copy>
```

```sql
<copy>
SELECT COUNT(*) AS product_count FROM ns_inventory;
</copy>
```

**Expected result:** `PRODUCT_COUNT` is `6`. If the insert's outcome is uncertain, check the count before retrying. Ask for help if it differs; repeating the insert can cause a primary key error.

## Task 3: Show Maya the evidence

Run the query:

```sql
<copy>
SELECT product_name,
       available_units,
       promotion_demand,
       promotion_demand - available_units AS units_short
FROM ns_inventory
WHERE available_units < promotion_demand
ORDER BY units_short DESC, product_name;
</copy>
```

**Expected result:**

| Product | Available | Forecast demand | Estimated shortfall |
|---|---:|---:|---:|
| Trail Backpack | 12 | 30 | 18 |
| Rain Jacket | 8 | 20 | 12 |
| Camping Lantern | 5 | 15 | 10 |

Maya can ask the inventory team to check replenishment, beginning with Trail Backpack. The total estimated shortfall is 40 units. These figures come from a fictional snapshot, not a live inventory feed or a guaranteed forecast.

## Task 4: Hand off the service

Share your result verbally or in your own notes:

* **Database used:** new or fallback, and its name in an approved location.
* **Evidence:** SQL connected as your workshop user and returned the three expected products.
* **New database state:** available, still provisioning, or failed at the last check. Name the owner of any follow-up.
* **Business result:** three products are short by a combined 40 units; check the forecast and incoming deliveries before ordering.

Keep the database and data if you are continuing into the next workshop. If you used the fallback, the data remains there; it is not automatically copied to the newly provisioned database. At the end of the full learning path, follow the resource owner's cleanup instructions.

You have completed the workshop.

## Learn more

* [Connect with built-in Oracle Database Actions](https://docs.oracle.com/en-us/iaas/autonomous-database-serverless/doc/connect-database-actions.html)
* [Connect from an Azure VM](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucn-connect-c-autonomous-ai-database-serverless.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
