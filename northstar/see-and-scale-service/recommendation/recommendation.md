# Give Maya a capacity recommendation

## Introduction

Maya needs a decision for the promotion and an honest explanation of what the team has learned. Bring the evidence together in a short handoff.

Estimated lab time: 10 minutes.

### Objectives

* Summarize the observations, decision and next actions for a business stakeholder.

### Prerequisites

* Your baseline, metric notes, query result and resource allocation outcome from the preceding labs.

## Task 1: Prepare the handoff

Record the following in your own words:

1. **Service and baseline:** identify the database in an approved location, its availability state, base ECPU count and auto scaling setting.
2. **Evidence:** name the metric, time range, aggregation and observation, or state that data was unavailable. Confirm whether the inventory query returned the expected three products.
3. **Capacity action:** state whether an approved change was applied, verified and restored; remains pending; or was only proposed. Identify the owner of any outstanding action.
4. **Recommendation:** explain what to monitor during the promotion and what further evidence, cost review and approval would support a sizing decision. Do not claim the query caused a metric movement or that auto scaling occurred without evidence.

## Task 2: Compare your answer

A sound answer could be:

> The inventory query returned the expected three products. We recorded the current compute and auto scaling settings and examined CPU utilization for the selected period. The sample query was too small to establish the capacity needed for the promotion. Monitor the service during a representative, approved workload and review trends, response times and cost before changing the production allocation. The workshop's configuration change and restoration status are recorded separately.

Adjust the example to match what you actually observed, including missing data or an incomplete operation. Maya now has a reasoned next step, and Alex has a baseline to carry into the next workshop.

Keep the database and sample data for the rest of the learning path. Follow your environment owner's cleanup instructions after the final workshop.

You have completed the workshop.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
