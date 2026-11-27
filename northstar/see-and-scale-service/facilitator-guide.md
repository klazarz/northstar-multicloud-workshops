# Facilitator guide: See and Scale the Service

The SQL in this workshop targets Oracle AI Database 26ai. Confirm all workshop databases run 26ai before the session; do not assume the Azure service selects this version by default.

## Status and timing

This package is a draft requiring live pilots and an independent quality review. Budget 90 minutes after preparation: Get Started 10, baseline 15, monitoring 20, query 15, allocation 20, and handoff 10. A learner may use the database and data from Launch the Inventory Service or an equivalent prepared environment; verify the actual handoff, especially where that workshop used a fallback. Do not assume the new database contains the fallback's data.

## Prepare either environment

* Provide a nonproduction Oracle Autonomous AI Database Serverless instance on Azure, an Azure identity that can view the resource and metrics, an approved client network path, and a dedicated Database Actions user. The workshop user needs access to its own `NS_INVENTORY` snapshot or a clean schema with CREATE TABLE privilege and DATA quota. Provide the URL and credentials through approved channels.
* Prepare the six-row snapshot from Lab 1, or allow learners to create it in an isolated clean schema. Check the expected query result as the learner. Do not replace an existing table or erase data to reset an environment without its owner's approved procedure.
* Confirm Azure Monitor metrics appear for the correct resource, the metric namespace, scope, time zone and time range, and the expected data delay. If recent data is unavailable, learners should document the gap; provide a separately labeled historical example for discussion without representing it as their live result.
* Assign resource ownership, permissions and an approved cost budget. For a real allocation change, provide a safe temporary ECPU target and original value, a restoration deadline and owner, and sufficient quota. The action is conditional on prior owner approval and write permissions. If not supported, use the decision-only branch. Never change a shared or production database.
* Confirm that scaling operations and restoration finish in the session or establish an owner and handoff for pending operations. A metric movement after a query does not establish causation, and the small query is not a load test or proof of auto scaling.

## Delivery options

**Bring your own:** Confirm subscription entitlement, Azure and OCI access, region, pricing and the organization's resource management policies. The learner's identity must be able to view the resource and metrics. Grant write access only for an approved isolated allocation exercise. Establish cost and cleanup ownership before the session.

**Run on Multicloud:** Confirm with the provider that the reservation supplies the Azure service, linked identities, metrics visibility, an isolated database and user, network route, lifetime, cost coverage, and whether allocation changes and restoration are permitted. Replace generic reservation instructions with the verified flow. A generic OCI sandbox is not evidence that this Azure environment exists.

## After the lab

Verify the database's current ECPU count and auto scaling settings against the recorded baseline and resolve any outstanding operation with the owner. Keep the database and sample data until the full learning path ends. The environment owner follows the established resource deletion and cost-review procedures after the final workshop. If a temporary setting was retained for subsequent sessions, record who will restore it and when.

## Publication and quality

Run the complete workshop in both delivery options with representative learners; record actual times, UI labels, metric availability and latency, SQL results, allocation change and restoration. Confirm current billing and pricing with the resource owner. Review LiveLabs rendering, copy controls, keyboard and screen-reader access, and capture current redacted screenshots where useful with descriptive alt text. Verify the support address and acknowledgements. Obtain an independent rubric review and meet 4.5/5 overall with no criterion below 4.0 and no critical unresolved defect. No live pilot or independent score has been obtained for this draft.
