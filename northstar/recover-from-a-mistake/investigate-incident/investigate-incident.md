# Investigate the incident

## Introduction

Maya sees a zero where she expected 12 backpacks. Alex has set up an isolated practice source so you can reproduce the incident and preserve evidence without touching the working service.

Estimated lab time: 15 minutes.

### Objectives

* Verify the identity and starting state of the practice source.
* Reproduce one controlled mistake and record when it occurred.

### Prerequisites

* The verified source, backup and prepared copy handoff from Get Started. The workshop account can update its own practice table.

## Task 1: Verify the practice source

1. Connect to the **practice source** using its supplied SQL connection. Run each block separately using **Run Statement**.

    ```sql
    <copy>
    SELECT SYS_CONTEXT('USERENV', 'DB_NAME') AS database_name,
           USER AS workshop_user;
    </copy>
    ```

2. Compare both values with the owner's source handoff. The database identifier need not match the Azure resource name; use the owner's verified mapping. If either differs, stop. Never perform the update on the recovery copy, a shared database or production.
3. Check the starting state:

    ```sql
    <copy>
    SELECT product_id, product_name, available_units, promotion_demand
    FROM ns_inventory
    WHERE product_id = 101;
    </copy>
    ```

    **Expected:** one row, `101`, `Trail Backpack`, `12`, `30`. If it differs, stop and ask for help; do not reset or overwrite data.

## Task 2: Reproduce the mistake

1. Record the current UTC time using the following query. Confirm the supplied backup timestamp is earlier than this time and later than the seed commit. If it is not, stop: the backup cannot establish the required sequence.

    ```sql
    <copy>
    SELECT TO_CHAR(SYSTIMESTAMP AT TIME ZONE 'UTC',
                   'YYYY-MM-DD HH24:MI:SS TZH:TZM') AS utc_time;
    </copy>
    ```

2. In the same source session, run the targeted update once:

    ```sql
    <copy>
    UPDATE ns_inventory
    SET available_units = 0
    WHERE product_id = 101
      AND product_name = 'Trail Backpack'
      AND available_units = 12;
    </copy>
    ```

3. Check the SQL client's affected-row count. If it is exactly **one**, run `COMMIT;`. If it is zero or any other count, run `ROLLBACK;`, stop and ask for help. Do not retry blindly.

    ```sql
    <copy>
    COMMIT;
    </copy>
    ```

4. Repeat the UTC time query and record the time after the commit. Query product 101 again. It should now show **0** available units. Your notes should contain the source identity, backup time and times bracketing the committed change. If the result is unexpected, stop and contact the facilitator.

Maya's concern is now reproducible: the current record says zero, but the earlier report said 12. A current value alone cannot tell you which is correct.

You may now **proceed to the next lab**.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
