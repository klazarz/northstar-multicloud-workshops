# Validate the recovery copy

## Introduction

Maya asks whether the backup actually contains the missing inventory. Alex reminds you that a successful clone operation alone does not establish that the right data was recovered.

Estimated lab time: 20 minutes.

### Objectives

* Check the source and recovery copy independently.
* Show the recovered inventory report and describe what it proves.

### Prerequisites

* A usable new clone or verified prepared copy from Lab 3, with its connection, expected database identifier and workshop user; the source remains accessible.

## Task 1: Check the source

1. Connect to the assigned practice source, run the identity query below and compare both values with the source handoff. Stop if they do not match.

    ```sql
    <copy>
    SELECT SYS_CONTEXT('USERENV', 'DB_NAME') AS database_name,
           USER AS workshop_user;
    </copy>
    ```

2. Run this query and record the result:

    ```sql
    <copy>
    SELECT product_id, product_name, available_units, promotion_demand
    FROM ns_inventory
    WHERE product_id = 101;
    </copy>
    ```

    **Expected on source:** Trail Backpack has `0` available units and demand `30`. If it does not, stop and investigate with the facilitator.

## Task 2: Check the recovery copy

1. Open a **separate connection** to the selected recovery copy using its supplied URL and account. Run the identity query again and compare it with the owner's verified copy identity and user. Database identifiers can be similar; confirm the URL/resource mapping as well. Stop if the copy cannot be distinguished from the source.
2. Run the product query again. **Expected on the copy:** Trail Backpack has `12` available units and demand `30`.
3. Check the row count and the report:

    ```sql
    <copy>
    SELECT COUNT(*) AS product_count FROM ns_inventory;
    </copy>
    ```

    ```sql
    <copy>
    SELECT product_name, available_units, promotion_demand,
           promotion_demand - available_units AS units_short
    FROM ns_inventory
    WHERE available_units < promotion_demand
    ORDER BY units_short DESC, product_name;
    </copy>
    ```

    **Expected:** six products total; Trail Backpack 12 available, demand 30, shortfall 18; Rain Jacket 8, 20, 12; Camping Lantern 5, 15, 10. The three shortfalls total 40 units.
4. If any result differs, check your connection and provenance with the facilitator. Do not edit either database to make the result match.

The source still shows the mistaken value; the separate copy contains the earlier value. Together with the verified backup provenance and timeline, the comparison supports the recovery of the earlier snapshot. It does not itself repair the source or prove that 12 units are physically in stock today.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
