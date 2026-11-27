# Prepare the delegated subnet

## Introduction

Maya wants the Northstar inventory database to be reachable from the approved Azure network. Alex explains that the private network choice starts with an Azure virtual network (VNet) and a subnet delegated to Oracle AI Database@Azure. You will inspect an assigned subnet or create one if the environment owner has prepared an isolated network exercise.

**Estimated lab time:** 20 minutes.

### Objectives

* Identify the Azure network and delegation required for the workshop's private access configuration.
* Inspect a prepared subnet or create an authorized, isolated VNet and delegated subnet.
* Record the network details needed for the database creation lab.

### Prerequisites

* Your environment handoff identifies the Azure subscription, region, resource group, VNet and delegated subnet. The account has permission to view them.
* To create a VNet, the owner has authorized an isolated exercise and supplied unique new names, approved nonoverlapping address ranges, network security and route settings, region, permissions, cost and cleanup ownership. Never change a shared subnet.
* The network owner has evaluated advanced network features and completed any required subscription-level registrations **before** subnet creation. The Oracle documentation warns that enabling those features later does not extend them to already deployed resources.

## Task 1: Choose how to prepare the network

Use the tabs to choose a method. Azure Portal and Azure CLI provide hands-on paths. OCI Console and OCI CLI describe the service boundary and direct you to an Azure path. Use the **same assigned Azure resources** throughout the workshop; do not create a second VNet merely to compare methods.

<if type="azure_portal">
### Azure Portal

1. Sign in to the Azure portal and confirm the subscription from your handoff. Open **Virtual networks**.
2. **Prepared network:** Open the assigned VNet, select **Subnets**, and open the assigned delegated subnet. Compare its name, address range and delegation with the handoff. The delegated service must be `Oracle.Database/networkAttachments`. Continue to the checkpoint below; do not modify it.
3. **Authorized new network:** Only if your owner assigned a new, isolated network exercise, select **Create**. On **Basics**, choose the assigned subscription, resource group and region and enter the approved unique VNet name. On **Security**, apply the owner's approved settings. On **IP addresses**, enter the approved VNet address range and configure the assigned subnet name and range. Select `Oracle.Database/networkAttachments` under **Subnet delegation**. Configure the network security group, route table and other network options as specified by the owner, and save the subnet.
4. Review the **Tags** and **Review + create** pages against the handoff. Correct any validation errors and submit only the authorized configuration. Wait for the operation to complete, open the new VNet, and verify the subnet's delegation and range under **Subnets**. If deployment fails or remains pending at the session cutoff, record its status and owner and use the prepared network; do not repeatedly submit.

</if>

<if type="azure_cli">
### Azure CLI

Use an approved Azure Cloud Shell **Bash** session or a prepared Bash client. The Oracle guide specifies Azure CLI 2.87.0 or later and the `oracle-database` extension 2.0.4 or later for this workflow. Sign in through the approved method. These commands use the subscription currently selected in your CLI session.

1. Check the current account. Compare the subscription ID with the handoff; if it differs, select the approved subscription through your organization's procedure before continuing.

    ```bash
    <copy>
    az account show --output table
    </copy>
    ```

2. Enter the assigned resource group, VNet and delegated subnet names when prompted. Do not enter credentials.

    ```bash
    <copy>
    read -r -p 'Resource group: ' NS_RESOURCE_GROUP
    read -r -p 'VNet name: ' NS_VNET
    read -r -p 'Delegated subnet name: ' NS_DELEGATED_SUBNET
    </copy>
    ```

3. **Prepared network:** Inspect the VNet and subnet. Confirm the identity, address range and the delegation service `Oracle.Database/networkAttachments`. If the resource cannot be found or permission is denied, contact the facilitator; do not create a replacement without the owner's instructions. Skip to the checkpoint.

    ```bash
    <copy>
    az network vnet show --resource-group "$NS_RESOURCE_GROUP" --name "$NS_VNET" --output json
    az network vnet subnet show --resource-group "$NS_RESOURCE_GROUP" --vnet-name "$NS_VNET" --name "$NS_DELEGATED_SUBNET" --output json
    </copy>
    ```

4. **Authorized new network:** If the owner has explicitly assigned a new isolated VNet exercise, first verify the account, region, resource group, unique VNet and subnet names, and approved CIDRs. Confirm with the owner that the VNet name is unused; do not use `create` on an existing VNet because it can modify an existing resource. Enter the remaining approved values:

    ```bash
    <copy>
    read -r -p 'Azure region: ' NS_REGION
    read -r -p 'VNet address prefix: ' NS_VNET_PREFIX
    read -r -p 'Initial subnet name: ' NS_INITIAL_SUBNET
    read -r -p 'Initial subnet address prefix: ' NS_INITIAL_PREFIX
    read -r -p 'Delegated subnet address prefix: ' NS_DELEGATED_PREFIX
    </copy>
    ```

5. Review the values with the handoff. The VNet and its initial subnet are created first; run the second command only after the first succeeds. It creates the delegated subnet in that new VNet. The snippets follow Oracle's CLI example and do not configure an NSG, route table or other optional settings. If your approved design requires them, use the owner's approved configuration instead of submitting an incomplete network.

    ```bash
    <copy>
    az network vnet create \
      --resource-group "$NS_RESOURCE_GROUP" \
      --location "$NS_REGION" \
      --name "$NS_VNET" \
      --address-prefixes "$NS_VNET_PREFIX" \
      --subnet-name "$NS_INITIAL_SUBNET" \
      --subnet-prefixes "$NS_INITIAL_PREFIX"
    </copy>
    ```

    ```bash
    <copy>
    az network vnet subnet create \
      --resource-group "$NS_RESOURCE_GROUP" \
      --vnet-name "$NS_VNET" \
      --name "$NS_DELEGATED_SUBNET" \
      --address-prefixes "$NS_DELEGATED_PREFIX" \
      --delegations "Oracle.Database/networkAttachments"
    </copy>
    ```

6. Run the two inspection commands from step 3. Verify the resource group, VNet, delegated subnet, range and delegation against the handoff. If creation fails or remains pending, record the status and contact the owner; do not resubmit blindly. Use the prepared network if the new one is unavailable by the session cutoff.

</if>

<if type="oci_console">
### OCI Console

Oracle's creation matrix lists creating an Azure VNet and delegated subnet from OCI Console as **not supported by design**. Azure owns these network resources. Select the **Azure Portal** or **Azure CLI** tab to inspect the prepared network or create the authorized isolated one. The same Oracle guide also describes Azure Terraform providers for automation; they are outside this lab's four-tab exercise.

</if>

<if type="oci_cli">
### OCI CLI

Oracle's creation matrix lists creating an Azure VNet and delegated subnet from OCI CLI as **not supported by design**. An OCI CLI command for an OCI network does not create the Azure delegated subnet required here. Select the **Azure CLI** or **Azure Portal** tab to complete the network task. Azure Terraform providers are another documented automation option, outside this lab's four-tab exercise.

</if>

## Task 2: Record the network checkpoint

For the network you will actually use, record the subscription, resource group, region, VNet name, delegated subnet name and address range in an approved private location. Record whether it was prepared or newly created and confirm the delegation is `Oracle.Database/networkAttachments`. Share the result with Alex: “The Azure network is identified, and the assigned subnet is delegated for the database.”

If the delegation or resource identity cannot be verified, stop and ask the environment owner for help. A validated subnet alone does not prove that a database connection or client network path works; you will check the database separately.

You may now **proceed to the next lab**.

## Learn more

* [Create a delegated subnet](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-delegated-subnet.html)
* [Creation method support matrix](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create.html)
* [Azure advanced network features for Oracle AI Database@Azure](https://learn.microsoft.com/en-us/azure/oracle/oracle-db/oracle-database-network-plan)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
