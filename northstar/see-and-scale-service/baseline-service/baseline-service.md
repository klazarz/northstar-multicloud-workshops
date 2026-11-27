# Establish a baseline

## Introduction

Before Maya's promotion, Alex wants a starting point. Record the resource configuration and verify that the inventory snapshot is available.

Estimated lab time: 15 minutes.

### Objectives

* Identify the current resource allocation and the database used in this session.
* Verify or prepare the small fictional inventory dataset.

### Prerequisites

* Complete Get Started and open the assigned Azure database and SQL worksheet.

## Task 1: Record current allocation

1. In the Azure portal, open **Oracle AI Database@Azure**, select **Oracle Autonomous AI Database**, and open your assigned database. Check the resource name and state. If it is not available, ask the facilitator for the prepared database.
2. Under **Settings**, select **Resource allocation**, then select **Manage**. Record the displayed ECPU count, compute auto scaling setting, storage allocation, storage unit and storage auto scaling setting in your own notes. Select **Cancel** after inspecting the settings.
3. Record the time and time zone, resource owner and whether the database is the newly created resource or the fallback from the previous workshop. Do not include credentials in your notes.

## Task 2: Verify the inventory snapshot

1. In Database Actions, run each block separately with **Run Statement**:

    ```sql
    <copy>
    SELECT USER AS workshop_user;
    </copy>
    ```

    Confirm the result matches your assigned workshop user. Then run:

    ```sql
    <copy>
    SELECT COUNT(*) AS product_count FROM ns_inventory;
    </copy>
    ```

2. If the result is **6** and you know this is the workshop table from the previous lab, proceed. If the table already exists but its ownership or contents are uncertain, stop and ask the administrator; do not overwrite it.
3. If the table is absent and the administrator has confirmed this is a clean dedicated workshop schema, create and load it using the following statements, one at a time:

    ```sql
    <copy>
    CREATE TABLE ns_inventory (
        product_id NUMBER PRIMARY KEY,
        product_name VARCHAR2(60) NOT NULL,
        available_units NUMBER NOT NULL,
        promotion_demand NUMBER NOT NULL
    );
    </copy>
    ```

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

    ```sql
    <copy>
    COMMIT;
    </copy>
    ```

    Run the count query again and confirm six rows. If creation fails because the name exists, or if the insert outcome is uncertain, stop and ask for help; do not repeat blindly.

**Checkpoint:** You have an allocation baseline and a six-row inventory snapshot in the assigned schema. The result is sample data, not production inventory.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
