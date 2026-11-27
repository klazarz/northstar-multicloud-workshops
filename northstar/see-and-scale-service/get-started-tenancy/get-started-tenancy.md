# Get Started

## Introduction

Use your organization's prepared Azure and OCI environment and the database handed off from the previous workshop, or an equivalent standalone environment.

Estimated lab time: 10 minutes after preparation.

### Objectives

* Identify the database, SQL user, permissions and operating boundaries for the workshop.

### Prerequisites

* Oracle Autonomous AI Database Serverless on Azure running Oracle AI Database 26ai. Confirm the version with your environment owner before running the SQL.

* An available nonproduction Autonomous AI Database Serverless instance on Azure, with permission to view its resource allocation and Azure Monitor metrics.
* A dedicated workshop user, Database Actions access through the approved network path, and the inventory dataset. If the dataset needs to be created, the user needs CREATE TABLE privilege and DATA quota.
* An owner-approved resource and budget for any configuration changes; modification permission is needed only for the optional change.

## Task 1: Confirm your environment

1. Sign in to the Azure portal using your approved account. Find the database selected in the previous workshop's handoff. If that workshop used a fallback, identify whether the data and access are on that fallback or a different database. Use the database and schema prepared for this session.
2. Obtain the user-specific Database Actions URL and workshop credentials through your approved channel. Open it from the approved client or remote desktop and confirm you can reach the SQL worksheet.
3. Record the owner, resource name, current budget and permission to inspect metrics. Ask whether a temporary ECPU change is permitted and, if so, the approved target and restoration plan. If not, you can still complete the decision exercise without applying a change.
4. If you are starting independently, obtain a ready database and isolated schema from your administrator. Lab 1 provides the sample data setup for an empty schema. Do not use a production database or alter a shared resource for this exercise.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
