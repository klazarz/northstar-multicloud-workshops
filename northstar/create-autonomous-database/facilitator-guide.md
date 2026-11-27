# Facilitator guide: Create an Autonomous AI Database on Azure

## Status and timing

This draft needs live validation and independent review before publication. Budget 90 minutes after preparation: Get Started 10, readiness 10, method choice 10, delegated subnet 20, database creation 25 and verification/handoff 15. A prepared 26ai fallback permits an honest standalone outcome when creating a new resource is unavailable or slow. This is a deeper creation-method workshop that complements **Launch the Inventory Service**; it is not a claim that the earlier database or its inventory data will be present on a newly created resource.

## Prepare both environments

* Confirm Oracle AI Database@Azure onboarding, region and 26ai availability, the linked cloud identities, appropriate Azure permissions and resource-provider registrations. Use the documented [prerequisites](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-prerequisites.html); do not require learners to grant themselves privileged roles. Confirm Azure CLI and extension versions and authentication if the CLI route is offered.
* Assign a nonproduction subscription, resource group, approved delegated subnet, network path, and unique database name to each learner. A shared prepared network may be inspected but never modified by learners. If network creation is offered, assign an isolated new VNet, distinct initial and delegated subnets, approved nonoverlapping address ranges, region, security groups, routes and permissions. Decide subscription-level advanced-network feature registration before creating the subnet. Test the resulting delegated subnet and client network route.
* Prepare a separately available Autonomous AI Database Serverless on Azure running 26ai and an isolated workshop SQL user per learner. Provide user-specific Database Actions URLs and credentials through approved channels. Verify connection and `SELECT USER AS workshop_user;` from the same client learners will use. Protect private details and credentials.
* Provide an owner-approved configuration sheet covering workload, 26ai, ECPU count, compute and storage scaling, size and units, retention, ADMIN secret handling, license and edition where applicable, character sets, access mode, VNet/subnet, mTLS, maintenance, contacts and tags. Confirm quota, regional feature availability, network isolation, license entitlement, projected costs, lifetime, permission to submit, time cutoff, support contact and cleanup owner. Confirm which route can create versus inspect; the workshop does not assume creation is allowed.
* Pilot Azure Portal and Azure CLI instructions with the exact settings. The documentation matrix marks some sub-options **Pending Validation** for Azure CLI; verify the exact combination or use the portal or prepared-resource route. Review the CLI example against the installed extension's help, its interactive empty-password prompt, Bash terminal, subscription scope, and any required edition, character-set, contact or tag parameters. The example explicitly uses OLTP, ECPU, private network, mTLS, Regular maintenance and disabled scaling; it must not be submitted if these differ from the approved design. Test `--no-wait true`, observe the actual operation and verify the status path. Confirm secret-handling policy and that no debug logging exposes credentials. Never assume example defaults match the handoff.
* Prearrange a qualified administrator to create a dedicated SQL user on a new database, establish its network path and provide/test the user-specific URL as soon as possible. If this cannot be completed by the cutoff, learners use the prepared fallback and accurately record the new request state. Track each submitted resource and in-flight network/database deployment to a named owner. No repeated submissions on uncertain outcomes.

## Delivery options

**Bring your own:** The participant's organization confirms entitlements, subscription, permissions, approved 26ai region, capacity, budget and ownership. Pre-provision and test fallback SQL access and the delegated network. Creation is optional and must use the organization's approved settings.

**Run on Multicloud:** Confirm with the provider that the actual reservation supplies Oracle AI Database@Azure, Azure identities and permissions, accessible delegated networking, 26ai database, Database Actions user, approved client and sufficient lifetime. Verify whether creation is permitted, how each resource is provisioned and charged, how CLI is accessed, and who manages pending operations. A generic OCI sandbox does not establish Azure service availability. Replace generic reservation instructions with the confirmed provider flow before publication.

## Method tabs and documentation scope

Both manifests map the same four method keys on Labs 3 and 4. The corresponding `<if type="...">` blocks present Azure Portal, Azure CLI, OCI Console and OCI CLI. The creation matrix marks the OCI methods unsupported by design for Azure VNet/delegated subnet and Autonomous AI Database Serverless creation. OCI tabs are explanatory, and learners must switch to an Azure tab to perform the task. The matrix also lists AzureRM and AzAPI Terraform, which are covered as documented alternatives for comparison rather than an apply exercise. Other Exadata, Dedicated, Base Database, Exascale and GoldenGate resources are outside this Serverless workshop.

Use separate Get Started files for tenancy and sandbox; do not overload method-tab `type` with environment selection. Test the actual published LiveLabs renderer with both manifests, all tabs, navigation between labs, heading placement, copy controls, keyboard navigation and screen readers. The local template documents this mechanism, but its behavior in the deployment has not been confirmed.

## Completion, cleanup and quality

Check that the learner's handoff identifies the submitted request separately from the database used for SQL, especially when the fallback was used. Preserve resources needed for the broader learning path. The environment owner manages pending submissions and charges, and removes only owned resources under the approved cleanup procedure; never delete shared networks.

Before publication run representative learners through all actionable method and environment combinations, including no-create, pending and failed cases, time each path, verify current UI and CLI syntax, password prompt and outputs, and capture accessible, redacted screenshots where helpful. Confirm support address and credits. Obtain an independent rubric review with at least 4.5/5 overall, no criterion below 4.0, and no unresolved critical defect. A final score cannot be established without the required pilots and review.

## References

* [Create: support matrix](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create.html)
* [Create an Autonomous AI Database Serverless](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-autonomous-ai-database-serverless.html)
* [Create a delegated subnet](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-delegated-subnet.html)
* [Azure CLI Autonomous Database commands](https://learn.microsoft.com/en-us/cli/azure/oracle-database/autonomous-database?view=azure-cli-latest)
