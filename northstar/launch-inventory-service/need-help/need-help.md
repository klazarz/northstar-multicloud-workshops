# Need Help?

## Introduction

Use these checks if you encounter a problem during the workshop. Contact your facilitator or environment administrator if a prerequisite or permission is missing.

### Prerequisites

* Your assigned resource names and approved support contact.

## Task 1: Resolve access and provisioning problems

1. If the network or subnet is missing, ask the administrator to check the approved region, virtual network, delegation, capacity and permissions. Do not modify a shared network.
2. If creation fails validation, review the portal's specific error with the administrator. If a creation operation is still running, inspect its status instead of submitting a duplicate.
3. If the new database or its user is not ready in time, use the prepared fallback and record the reason. Arrange follow-up for any in-flight or failed resource.
4. If Database Actions does not open, verify the URL, client network path and user web access with the administrator. Never share passwords or wallet files in workshop comments.

## Task 2: Resolve data problems

1. Confirm the current user and the selected database. If `NS_INVENTORY` already exists, request a clean dedicated schema rather than dropping or changing an existing object.
2. If the data does not match, ask the administrator or facilitator to inspect the rows and transaction state. Do not blindly repeat the insert.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
