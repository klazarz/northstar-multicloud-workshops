# Prepare the inventory snapshot

## Introduction

Maya needs reliable numbers before the promotion. Connect to your workspace and prepare Northstar’s sample inventory.

Estimated lab time: 20 minutes

### Objectives

* Verify your workshop user.
* Create a table and load six sample products.

### Prerequisites

* Complete Get Started and open the SQL worksheet as your workshop user.

## Task 1: Check your connection and understand the challenge


Maya explains: “We expect more orders this weekend. Which products should I ask the team to replenish first?”

Alex says: “Let’s check the account first, then load the snapshot into your own workspace.”

The snapshot contains the quantity currently available and the quantity Northstar expects to need for the promotion. It is a planning snapshot, not a live inventory feed. You will calculate the shortfall where expected demand exceeds available stock.

1. In the SQL worksheet, paste the following statement and run it. In Database Actions, select the statement and use **Run Statement**. Run each SQL block separately throughout this lab.

    ```sql
    <copy>
    SELECT USER AS workshop_user;
    </copy>
    ```

2. Confirm that the result shows your assigned workshop user. If it does not, stop and sign in to the correct account. The objects you create belong to the current user's schema.

## Task 2: Create the inventory table

Alex has arranged for a dedicated schema. Create one small table for the snapshot:

```sql
<copy>
CREATE TABLE ns_inventory (
    product_id          NUMBER PRIMARY KEY,
    product_name        VARCHAR2(60) NOT NULL,
    available_units     NUMBER NOT NULL,
    promotion_demand    NUMBER NOT NULL
);
</copy>
```

Run the statement and check for a successful completion message. The four columns identify each product and record its current stock and expected demand.

If you receive `ORA-00955`, the name is already in use. Stop; ask the facilitator or your administrator for a clean workshop schema. Do not drop an existing object.

## Task 3: Load the snapshot

Add the six sample products in one statement:

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

Run the statement once. It should report six rows inserted. If you are unsure whether it succeeded, run the count query below before trying again; repeating the insert causes a primary key error. If the worksheet session ends before you commit, uncommitted rows can be lost.

Save the rows by running:

```sql
<copy>
COMMIT;
</copy>
```

Check the snapshot:

```sql
<copy>
SELECT COUNT(*) AS product_count
FROM ns_inventory;
</copy>
```

**Expected result:** `PRODUCT_COUNT` is `6`. If it is not, stop and ask for help before continuing.


## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
