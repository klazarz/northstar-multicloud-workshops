# Provision the Autonomous AI Database

## Introduction

Maya wants the Northstar inventory service to have a dependable database before the promotion. Alex has reviewed the network and asks you to create an Autonomous AI Database Serverless resource in Azure with the agreed settings. Choose one method in the tabs. The Azure portal and Azure CLI are alternative ways to create the same kind of Azure resource; the OCI tabs explain the service boundary.

Estimated lab time: 25 minutes after preparation. A database that is still provisioning can be followed up by its owner while you continue using the prepared database.

### Objectives

* Apply the approved database, network, security and maintenance settings using a supported Azure creation method.
* Record the submission and identify which database is ready for the next lab.
* Explain why an OCI creation command is not interchangeable with an Azure creation command for this service.

### Prerequisites

* The authorized Azure subscription, resource group, region, delegated subnet, unique name, settings, cost budget, network access and cutoff from the environment handoff. The environment owner has verified Oracle AI Database **26ai** availability and the necessary Azure permissions and quota.
* A separate, ready 26ai fallback database and its user-specific connection, so you can continue if the new database is not ready or creation is not permitted.
* For Azure CLI: a configured approved client, Azure CLI and `oracle-database` extension versions required by the [creation guide](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-autonomous-ai-database-serverless.html), with the correct subscription selected. The facilitator has tested this option, including the requested parameter combinations.

## Task 1: Choose a creation method

Read the tab for your preferred interface. Select one Azure creation route only. OCI Console and OCI CLI are included to show the distinction in the documentation; they do not create an Azure Autonomous AI Database Serverless resource. If your reservation or organization does not permit a creation, review the choices and continue with the prepared database. Do not submit a duplicate request.

<if type="azure_portal">

### Azure Portal

1. In the Azure portal, open **Oracle AI Database@Azure**, select **Oracle Autonomous Database**, and select **Create**.
2. Under **Basics**, select the assigned subscription, resource group and region, and enter your approved unique database name. The documented name starts with a letter, uses letters and numbers only, and is at most 30 characters.
3. Under **Configuration**, select the approved workload and **26ai** database version. Enter the approved ECPU count, compute auto scaling, storage amount and unit, storage auto scaling and backup retention. Set the ADMIN password using your organization's approved secret procedure; do not share it in notes. Choose the approved license type and, if required by the handoff, character and national character sets. Confirm the cost implications of compute, scaling, storage, backup and licensing with the owner.
4. Under **Networking**, use the approved access type. For this workshop's private network path, select **Managed private virtual network IP only**, then the assigned virtual network and delegated subnet; set mTLS as directed by the owner. The other documented choices are secure access from anywhere and access from allowed IPs; their mTLS and access-rule requirements differ. Do not switch access modes to work around a network problem.
5. Under **Maintenance**, select the approved patch level and contact information. Under **Consent**, review the terms and privacy policy and accept only as authorized by your organization. Apply the agreed **Tags**.
6. On **Review + Create**, compare every value with the handoff, including region, version, network, license, scaling and estimated cost. Validation passing does not confirm that your choices are correct. If approval, permission or a value is missing, do not submit; use the prepared database. Otherwise select **Create** once.
7. Record the Azure resource name, submission time and displayed provisioning status. Continue to Task 2.

</if>

<if type="azure_cli">

### Azure CLI

1. On the approved shell, verify the account and tool versions. Confirm the subscription ID matches the handoff. The creation guide currently specifies Azure CLI 2.87.0 or later and `oracle-database` extension 2.0.4 or later; use the version approved and tested by the facilitator.

    ```bash
    <copy>
    az account show --output table
    az version --output json
    az extension show --name oracle-database --output json
    </copy>
    ```

2. Fill in the non-secret values below from your handoff. The VNet and subnet IDs must refer to the approved Azure network and delegated subnet, which may be in a different resource group. Ask the owner for the full IDs. Replace every placeholder before continuing; the database name must be unique and follow the Azure naming rules.

    ```bash
    <copy>
    NS_RESOURCE_GROUP='<approved-resource-group>'
    NS_DB_NAME='<unique-database-name>'
    NS_LOCATION='<azure-region-code>'
    NS_VNET_ID='<approved-vnet-resource-id>'
    NS_SUBNET_ID='<approved-delegated-subnet-resource-id>'
    NS_ECPU='<approved-ecpu-count>'
    NS_STORAGE_GB='<approved-storage-gb>'
    NS_BACKUP_DAYS='<approved-retention-days>'
    NS_LICENSE='<approved-license-model>'
    </copy>
    ```

3. Review the [creation guide's Azure CLI example](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-autonomous-ai-database-serverless.html) and your installed `az oracle-database autonomous-database create --help`. This example uses `OLTP`, 26ai, ECPU, private VNet and subnet, mTLS, and disabled compute and storage auto scaling. Confirm these choices, including license and maintenance settings, are approved for your environment. The command does not set edition, character sets, contacts or tags: verify the resulting defaults with the owner, and do not submit if explicit values or other settings are required. The [creation matrix](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create.html) lists some workload and license sub-options as **Pending Validation** for Azure CLI; the facilitator must verify your exact combination before submission. If it has not been verified, use the Azure Portal tab or the prepared database.
4. If creation is permitted, use an approved private interactive terminal. The command below passes an empty value for `--admin-password`; the Azure CLI reference says this prompts for the password on the terminal. Enter the password only at that prompt. The facilitator must verify this behavior with the installed extension and the organization's secret-handling policy. Do not enable shell tracing or share terminal output containing secrets. If the prompt is unavailable, stop and use the prepared database.
5. Submit once, after confirming all settings and costs. This command follows the documentation's Azure CLI create example; the facilitator must verify the extension's help and the approved flags for the environment. The `--regular` option follows that example. If any value or support status is unclear, do not submit; use the prepared database.

    ```bash
    <copy>
    az oracle-database autonomous-database create \
      --resource-group "$NS_RESOURCE_GROUP" \
      --name "$NS_DB_NAME" \
      --display-name "$NS_DB_NAME" \
      --location "$NS_LOCATION" \
      --db-workload OLTP \
      --db-version 26ai \
      --compute-model ECPU \
      --compute-count "$NS_ECPU" \
      --cpu-auto-scaling false \
      --data-storage-size-in-gbs "$NS_STORAGE_GB" \
      --is-auto-scaling-for-storage-enabled false \
      --backup-retention-period-in-days "$NS_BACKUP_DAYS" \
      --admin-password "" \
      --license-model "$NS_LICENSE" \
      --vnet-id "$NS_VNET_ID" \
      --subnet-id "$NS_SUBNET_ID" \
      --is-mtls-connection-required true \
      --autonomous-maintenance-schedule-type Regular \
      --regular \
      --no-wait true
    </copy>
    ```

    If the command fails or its outcome is uncertain, do not repeat it. Check the Azure resource and deployment status with the owner first. Record the outcome without exposing the password.
6. Record the Azure resource name, submission time and displayed provisioning status. Inspect the same resource in the Azure portal or run the command below. The response is a snapshot; record the reported lifecycle and provisioning fields. If it is not found, the state is unclear, or the operation failed, ask the owner to investigate and track the existing request before any retry. Continue to Task 2.

    ```bash
    <copy>
    az oracle-database autonomous-database show \
      --resource-group "$NS_RESOURCE_GROUP" \
      --name "$NS_DB_NAME" --output json
    </copy>
    ```

</if>

<if type="oci_console">

### OCI Console

The creation matrix marks OCI Console **Not Supported (By Design)** for creating this Autonomous AI Database Serverless resource in Azure. Creating an OCI-native Autonomous AI Database would be a different resource and does not fulfill this Azure exercise. Switch to **Azure Portal** or **Azure CLI** for the actual creation, or continue using the prepared Azure database. Terraform through AzureRM or AzAPI is also documented, but is outside this hands-on lab.

</if>

<if type="oci_cli">

### OCI CLI

The creation matrix marks OCI CLI **Not Supported (By Design)** for creating this Autonomous AI Database Serverless resource in Azure. Do not substitute an OCI-native Autonomous Database create command: it targets a different resource. Switch to **Azure Portal** or **Azure CLI** for the actual creation, or continue using the prepared Azure database. AzureRM and AzAPI Terraform creation methods are documented separately.

</if>

## Task 2: Choose the usable database

1. If you submitted a creation request, inspect its latest status without submitting again. Record **available**, **still provisioning**, or **failed**, the resource name, and the owner responsible for follow-up and any charges. If you did not submit, record **not submitted** and why.
2. Use the new resource in the next lab only when it is available **and** the facilitator has supplied and tested the dedicated workshop SQL user, connection and approved network path. Resource availability alone does not establish SQL access.
3. If the new resource is not ready by the agreed cutoff, use the prepared database and record its name. The new resource still needs monitoring and cleanup; it is not automatically populated with data from the prepared one. If neither resource is usable, ask the facilitator for help rather than claiming success.

**Checkpoint:** You have documented either a creation request or an explicit reason for using the prepared resource, and selected an accessible database for Maya's inventory check.

## Learn more

* [Create an Autonomous AI Database Serverless in Azure](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-autonomous-ai-database-serverless.html)
* [Creation support matrix](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
