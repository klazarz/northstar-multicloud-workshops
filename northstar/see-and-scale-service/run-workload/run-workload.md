# Run and observe an inventory query

## Introduction

Alex asks you to repeat the inventory check while keeping a record of when the request ran. The query is intentionally small, so it is safe to use as an observation exercise rather than a stress test.

Estimated lab time: 15 minutes.

### Objectives

* Run a bounded, read-only query against the inventory snapshot.
* Compare the query time with available monitoring data without assuming causation.

### Prerequisites

* The six-row `NS_INVENTORY` snapshot and the metric baseline from the previous labs.

## Task 1: Run the inventory check

1. In your assigned Database Actions worksheet, note the current time and time zone. Run the following statement once:

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

2. Confirm that the result contains Trail Backpack (18 units short), Rain Jacket (12), and Camping Lantern (10). If the output differs, check that you are using the intended database, workshop schema and sample data; ask the facilitator before changing any existing table.
3. Record the completion time and whether the query returned the expected result. This query reads the snapshot; it does not change inventory or simulate real order traffic.

## Task 2: Compare the monitoring view

1. Return to the same database's **Monitoring > Metrics** view. Select the same metric, aggregation and time granularity as before, and choose a time range that includes your query.
2. Record what you see and whether data for the query interval has arrived. The query may be too small or fast to produce a visible change; monitoring data can also be delayed or aggregated with other activity.
3. Describe the evidence carefully: a chart value near the query time is an observation, not proof the query caused it. No visible change does not prove a problem, and this exercise does not demonstrate auto scaling.

**Checkpoint:** You have a verified inventory query and a timestamped metric observation or a clearly documented data gap.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
