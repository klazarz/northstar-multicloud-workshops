# Get Started

## Introduction

Connect to the prepared workshop database and open a SQL worksheet. The database must be ready before you begin; provisioning is covered in a later workshop.

Estimated lab time: 10 minutes

### Objectives

* Open the SQL worksheet using your assigned workshop user.

### Prerequisites

* Oracle Autonomous AI Database Serverless on Azure running Oracle AI Database 26ai. Confirm the version with your environment owner before running the SQL.

* A dedicated database user with Database Actions access, permission to create a table, and sufficient storage quota.
* An approved network path to the database and its Database Actions URL.

## Task 1: Connect to your environment

1. Confirm that your organization has an available, nonproduction Oracle Autonomous AI Database Serverless instance on Azure and that you are authorized to use it. Your administrator must provide a dedicated workshop user and schema that does not already contain `NS_INVENTORY`.
2. Obtain the Database Actions URL, username, and password through your organization's approved channel. Use the approved client and network path. A private endpoint requires access through the configured private network.
3. Open the URL, sign in as the workshop user, and select **SQL**. Keep this worksheet open for the next lab.

If you cannot connect, contact your administrator. If your environment uses a prepared SQL Developer client instead, follow the [Oracle Azure client connection guide](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucn-connect-c-autonomous-ai-database-serverless.html); preparing the client is outside the estimated workshop time.

Do not share passwords, wallet files, or connection details in screenshots or workshop comments.

You may now **proceed to the next lab**.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
