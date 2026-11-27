# Inspect the network for the inventory service

## Introduction

Alex wants the service reachable from Northstar's approved client without exposing it unnecessarily. In this lab, inspect the prepared network before selecting it for the database.

Estimated lab time: 15 minutes.

### Objectives

* Find the assigned virtual network and delegated subnet.
* Explain the connection path and identify the approved client.

### Prerequisites

* Complete Get Started and have permission to view the assigned Azure network.

## Task 1: Find the delegated subnet

1. In the Azure portal, search for **Virtual networks** and open the virtual network assigned in Get Started. Check its subscription, resource group, and region against your workshop details.
2. Under **Settings**, select **Subnets**. Open the assigned delegated subnet and inspect its name, address range, and delegation. Confirm the delegation is `Oracle.Database/networkAttachments`.
3. Ask the facilitator or network administrator to confirm adequate available addresses and the approved client path. Do not change an existing subnet, security group, or route in this lab.

If the assigned subnet is missing or has a different delegation, stop and ask the administrator for a suitable prepared subnet. Creating a virtual network and subnet is documented in the [delegated subnet guide](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-delegated-subnet.html); it requires an approved address plan and permissions and is outside this lab's time budget.

## Task 2: Trace the route

1. Identify the approved browser or remote desktop that will reach Database Actions. Record its location in your notes without copying credentials or network identifiers to public channels.
2. Explain in your own words: Azure hosts the selected virtual network and delegated subnet; the learner's client must have an approved route to the database's private access path. A subnet name alone does not prove the connection works.

**Checkpoint:** You can identify the correct virtual network, delegated subnet and client path. Keep these details for the next lab.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
