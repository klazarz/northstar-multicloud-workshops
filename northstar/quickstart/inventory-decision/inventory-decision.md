# Give Maya an answer

## Introduction

The inventory snapshot is ready. Help Maya identify the largest gap and decide what the inventory team should investigate.

Estimated lab time: 15 minutes

### Objectives

* Find products whose forecast demand exceeds available stock.
* Explain the result and its limitations.

### Prerequisites

* Complete the inventory snapshot lab in the same workshop schema.

## Task 1: Find the products at risk


Run this query:

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

The `WHERE` clause keeps only products with fewer available units than expected demand. The calculation shows the estimated shortfall, and the largest shortfall appears first.

**Expected result:**

| PRODUCT_NAME | AVAILABLE_UNITS | PROMOTION_DEMAND | UNITS_SHORT |
|---|---:|---:|---:|
| Trail Backpack | 12 | 30 | 18 |
| Rain Jacket | 8 | 20 | 12 |
| Camping Lantern | 5 | 15 | 10 |

Hiking Socks do not appear because the available quantity equals the forecast; this query identifies a shortage, not a safety-stock threshold.

Now calculate the total shortfall:

```sql
<copy>
SELECT COUNT(*) AS products_at_risk,
       SUM(promotion_demand - available_units) AS total_units_short
FROM ns_inventory
WHERE available_units < promotion_demand;
</copy>
```

**Expected result:** `PRODUCTS_AT_RISK = 3` and `TOTAL_UNITS_SHORT = 40`.

## Task 2: Give Maya the answer

Before reading the example, use your results to answer Maya: Which product has the largest shortfall? How many products are affected, and what is their combined shortfall? What should the team confirm before ordering?

Compare your answer with this example:

> Three products have less stock than the promotion forecast. Trail Backpack has the largest estimated shortfall: 18 units. Rain Jacket is short by 12 and Camping Lantern by 10, for a total of 40 units. Ask the inventory team to review replenishment, starting with Trail Backpack, and confirm the forecast and stock figures before placing an order.

Maya can now ask the inventory team to check the forecast and available deliveries before choosing what to order. Alex has a repeatable query to share with the team.

You have connected to Oracle Autonomous AI Database Serverless on Azure, created and loaded a table, and used SQL to turn a snapshot into a business decision. The result is based on the supplied snapshot; it does not predict actual demand or include incoming deliveries.

## Troubleshooting

* **The URL does not open or sign-in fails:** Use the approved network or remote desktop and ask your facilitator or administrator to check access.
* **The table name is already in use:** Stop and request a clean workshop schema.
* **The row count or result is different:** Confirm your workshop username and ask for help checking the data; do not delete or reload existing data blindly.

## What comes next?

Keep your workshop database and table if you are continuing into **Launch the inventory service** or another learning path. The next workshop explores the Azure resources and provisioning choices behind the service. If you are finished, follow the cleanup instructions from your facilitator or database administrator. Do not delete a shared database or network resources.

## Learn more

* [Connect to Autonomous AI Database Serverless on Azure](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucn-connect-c-autonomous-ai-database-serverless.html)
* [Connect with built-in Oracle Database Actions](https://docs.oracle.com/en-us/iaas/autonomous-database-serverless/doc/connect-database-actions.html)
* [Create Autonomous AI Database Serverless on Azure](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-autonomous-ai-database-serverless.html)


## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
