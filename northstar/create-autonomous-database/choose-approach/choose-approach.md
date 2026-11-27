# Choose a creation method

## Introduction

Alex wants Maya to understand which team owns each part of the launch. The service spans clouds, but not every tool can create every resource.

Estimated lab time: 10 minutes.

### Objectives

* Compare the creation methods in the documentation.
* Choose one supported method for the practical labs.

### Prerequisites

* Your readiness card from Lab 1 and permission to view the official documentation.

## Task 1: Read the creation matrix

1. Open [Create](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create.html). Compare the **Delegated Subnet** and **Autonomous AI Database (Serverless)** rows. For the Azure resources in this workshop, the matrix lists Azure Portal, Azure CLI and the AzureRM and AzAPI Terraform providers as creation methods. It lists OCI Console, OCI CLI and OCI Terraform as **Not Supported (By Design)** for these creation operations.
2. Check the specific settings you plan to use. Some workload, license, network and maintenance combinations are marked **Pending Validation** in the matrix for some tools. Treat those as a validation task with the owner, not as a verified capability. The creation page and matrix may differ or change; check the current documentation and actual environment.
3. Choose **Azure Portal** or **Azure CLI** for the hands-on labs. The tabs in Labs 3 and 4 let you inspect each route. OCI tabs explain the boundary and direct you back to an Azure option; they do not create a Serverless database in Azure. Select your method again when moving between labs if needed. Do not submit the same resource using both routes.

## Task 2: Consider infrastructure as code

The detailed [database creation page](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-autonomous-ai-database-serverless.html) and [delegated subnet page](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-delegated-subnet.html) also include AzureRM and AzAPI Terraform examples. Compare their resource fields with the settings in your readiness card. Discuss which method your team could review and repeat, and who would manage its state and secrets. Do not apply the documentation examples to your environment during this workshop without an owner-reviewed plan and configuration.

**Checkpoint:** Tell Maya which cloud owns network and database creation, which method you selected, and one configuration item requiring owner verification.

You may now **proceed to the next lab**.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
