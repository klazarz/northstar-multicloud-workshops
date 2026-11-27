# QuickStart facilitator and environment guide

The SQL in this workshop targets Oracle AI Database 26ai. Confirm all workshop databases run 26ai before the session; do not assume the Azure service selects this version by default.

## Status and scope

This is a draft for review and pilot. The workshop uses an existing Oracle Autonomous AI Database Serverless instance on Azure; it does not create an Azure database or a LiveLabs sandbox. A suitable provided Azure environment, reservation flow, and access details have not yet been confirmed. Do not publish the provided-environment option as available until those details are verified.

Learner content is organized into lab folders and selected by the [tenancy manifest](workshops/tenancy/manifest.json) or [sandbox manifest](workshops/sandbox/manifest.json). Plan 45 minutes of learner time after preparation. Pilot the timings with a beginner and record actual connection, worksheet and query experience. Provisioning, user setup, access troubleshooting and cleanup are outside that estimate.

## Prepare either environment

1. Choose an available, nonproduction Autonomous AI Database Serverless instance in Oracle AI Database@Azure and identify its owner, region, subscription, cost owner, and retention period. Confirm the environment remains available for any subsequent workshop.
2. Give each learner a separate database user and schema, or an equivalent isolation arrangement. Enable Database Actions access for that user, grant the permissions needed to connect and create a table, and provide sufficient tablespace quota. Confirm `NS_INVENTORY` is absent in each schema. Do not use ADMIN as the shared learner account.
3. Establish an approved network path from the learner's browser or remote desktop to the Database Actions URL. Test from the same client environment learners will use. Private networking and access rules depend on the deployed configuration.
4. Deliver each learner's database username, password and user-specific Database Actions URL through approved channels. Provide the database name and a named support contact. Do not put credentials or wallet files in the workshop or a public repository.
5. Sign in as a representative learner; verify the SQL worksheet is available and that table creation, insertion, commit and query work. Use a dedicated pilot schema. Confirm the six rows, three shortages, and total shortfall of 40. Check whether learner isolation and access survive the entire planned day.
6. Decide who handles cleanup and when. For a full-day path, keep the schema and sample table until the related sessions end. If the follow-on workshop uses a different database, arrange a validated data checkpoint or repeat the QuickStart data setup there; a newly provisioned database does not automatically contain this table.

For user-specific Database Actions access, Oracle describes enabling web access and providing the URL in [Connect with Built-In Oracle Database Actions](https://docs.oracle.com/en-us/iaas/autonomous-database-serverless/doc/connect-database-actions.html). Confirm the precise roles, grants and quota for the chosen deployment with its administrator; do not assume a generic sandbox has them.

## Provided environment

The environment provider must supply the database, isolated user, network path, URL, credential delivery, access instructions, support contact, reservation duration, reset process and cleanup ownership. Confirm availability of the actual Azure service and both-cloud integration with the sandbox team. Validate concurrency, quota, expiration, permissions and cost before advertising this route. If the provider cannot supply the required environment, offer the bring-your-own route or an explicitly labeled facilitator demonstration.

## Bring your own

The learner or organization provides an existing entitled Azure subscription and the Azure/OCI resources, database, user and access path. Before the session, confirm permissions, availability, budget and ownership with the administrators. An Azure VM and SQL Developer with a wallet are an alternative client path documented by Oracle, but preparing and verifying that client is separate from the 45-minute lab. See the [Azure client connection guide](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucn-connect-c-autonomous-ai-database-serverless.html).

## Troubleshooting

* **URL does not open:** confirm the exact URL, approved client, DNS and network access; use the prepared remote environment if required. Do not tell learners to change access rules on shared resources.
* **Sign-in fails or SQL is missing:** check the database user, credential, account status and Database Actions access/roles with the administrator. Do not share passwords in chat or screenshots.
* **Cannot create the table:** check the user, `CREATE TABLE` privilege, quota and schema. `ORA-00955` means a name is already in use; give the learner an isolated clean schema rather than dropping the object.
* **Insert reports a primary key conflict:** check the existing row count and data before deciding how to proceed. Do not rerun blindly or remove rows in an unfamiliar schema.
* **Result differs:** confirm the learner ran the full insert once, committed it, and is connected to the intended schema. Compare the six input rows and the query with the learner-facing instructions.

## Cleanup

At the end of the entire learning path, the environment owner determines whether to retain the data. In a verified dedicated workshop schema, the owner may remove the workshop table with `DROP TABLE ns_inventory PURGE;` only after confirming the schema and that the table is no longer needed. Dropping is irreversible. Account and cloud resource cleanup follow the provider's approved procedures, ownership and retention policy; do not delete a shared database, virtual network or delegated subnet. Charges can continue while resources remain provisioned.

## Review and publication checklist

* Independently review the story, business calculation, SQL, access instructions, accessibility and both delivery branches against the proposed 4.5/5 rubric. See [quality-review.md](quality-review.md) for provisional author-side scores; an independent score has not yet been awarded.
* Pilot both routes with representative learners in a real supported environment; record timestamps, failures, screenshots with sensitive details removed, expected output, and corrective changes.
* Verify current LiveLabs manifest, Markdown, copy controls, accessibility, copyright, acknowledgements, support and publishing requirements with the publishing team. The manifests and renderer shells follow the local sample workshop; validate in the target renderer and confirm the workshop stakeholder help address before publication.
* Confirm a viable restart strategy for a partially completed lab, per-learner isolation, and cleanup after the full day. Verify all service and UI labels at the time of publication.
