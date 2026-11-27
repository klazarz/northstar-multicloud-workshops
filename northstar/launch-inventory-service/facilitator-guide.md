# Facilitator guide: Launch the inventory service

The SQL in this workshop targets Oracle AI Database 26ai. Confirm all workshop databases run 26ai before the session; do not assume the Azure service selects this version by default.

## Status

This is a draft for a 90-minute learner pilot, not a validated or published LiveLabs workshop. The Run on Multicloud environment, the reservation access flow, exact permissions, UI labels, setup timing, and an independent 4.5/5 quality review remain unverified. Do not represent the sandbox as available until the provider confirms it.

## Timing and preparation

The learner budget is Get Started 10 minutes, network inspection 15, database creation and status 35, and connection and handoff 30. Provisioning, account linking, subscription entitlement, network creation, client preparation, fallback provisioning, and cleanup are prepared outside the timed session. Measure actual durations in a beginner pilot.

Prepare an Azure subscription entitled for Oracle AI Database@Azure, linked OCI access and roles, an approved region, resource group, cost owner, quota, license, database configuration and tags. Prepare the private virtual network, delegated subnet (`Oracle.Database/networkAttachments`), adequate subnet capacity, DNS and approved client route. Verify that the client can access Database Actions using the chosen network settings. Reserve names and sufficient capacity for concurrent learners; provide each learner an isolated resource or safe permission model. Provide a trained facilitator who can perform creation when the learner cannot.

Prepare an independently available fallback database, client, and **clean per-learner schema** with web access, CREATE SESSION, CREATE TABLE and sufficient DATA quota. QuickStart may have left `NS_INVENTORY` in its schema: provide a different clean schema or have the owner prepare a fresh environment before the session. Do not silently drop learner data. Deliver the fallback database name, user URL and credentials securely, and test the path before learners arrive.

For the new database, arrange for an authorized administrator to create each workshop user as soon as the database is available. From the new database's Database Actions as ADMIN, use **Administration > Database Users > Create User**, enter the approved user name and password, enable **Web Access**, set a suitable DATA quota, and grant the minimum required CREATE SESSION and CREATE TABLE privileges through the approved administrative process. Provide the user-specific Database Actions URL and credentials through approved channels; sign in as that user and verify access. Oracle documents the user creation UI and roles in [Create and Manage Users](https://docs.oracle.com/en/cloud/paas/autonomous-database/serverless/adbsb/manage-users-create.html) and [Database Actions access](https://docs.oracle.com/en-us/iaas/autonomous-database-serverless/doc/connect-database-actions.html). The exact user setup and least-privilege grants must be piloted against this Azure service and current interface. If the user or network path cannot be ready within the session, use the fallback.

A newly provisioned database is separate from the QuickStart database; it does not inherit its data. This workshop supplies its own sample data. If a later workshop requires this database, keep the resource and user until the path ends and explicitly transfer the handoff. If the fallback was used, decide which database will be used later and prepare the correct data there.

## Environment-specific delivery

**Tenancy:** The customer supplies the entitled Azure and OCI environments and approves charges. Confirm each learner's creation and viewing permissions and identify the administrator who handles user creation, networking and cleanup. If the learner cannot create, the administrator can demonstrate submission; record the actual participation.

**Run on Multicloud:** The environment provider must confirm an Azure-capable reservation, Azure and OCI identities and integration, network, resource quotas, isolation, billing, lifetime, user-creation procedure, fallback, support and cleanup. Replace the generic reservation instructions with verified specifics once available. If creation is not allowed, a facilitator may submit it in the approved scope; otherwise explicitly label the exercise as a demonstration and use the fallback for SQL. A generic OCI sandbox is not proof of Azure access.

## Failure and cleanup

If a database is still provisioning, do not resubmit. Record its name, observed state, responsible owner and any follow-up. A fallback result proves only that the fallback was accessible and queried; it does not prove the new database is usable. If creation fails, preserve the error details without secrets and route to the administrator.

Preserve the database, user and sample data through the entire learning path when needed. At the end, the resource owner decides which learner-owned resources can be deleted and follows the documented [database deletion](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azudl-delete-autonomous-ai-database-serverless.html) and [delegated subnet deletion](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azudl-delete-delegated-subnet.html) processes. Never delete shared networks or another learner's resources. Confirm costs and resource state after cleanup.

## Publication and quality gates

Pilot both environment branches with representative beginners, capture actual elapsed time and validate every Azure/OCI interaction, SQL statement and expected result. Verify provisioning states, private DNS, web access, grants, fallback, and end-of-path cleanup. Preview both manifests and copy controls in the LiveLabs renderer, review accessibility and add current redacted screenshots with descriptive alt text where they improve navigation. Confirm the stakeholder help address and author acknowledgements. Obtain independent rubric scores of at least 4.5 overall and at least 4.0 per criterion with no unresolved critical defect. No such review or live pilot has yet been performed.
