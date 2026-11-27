# Explore and adjust capacity

## Introduction

Maya asks whether Northstar should increase capacity before the promotion. Alex explains that the team can inspect the resource allocation and evaluate changes, but a small query alone is not enough evidence for production sizing.

Estimated lab time: 20 minutes.

### Objectives

* Compare base compute, compute auto scaling and storage settings.
* Apply and verify an approved temporary compute change, or document a proposed change when mutation is unavailable.

### Prerequisites

* The baseline recorded in Lab 1 and an available, nonproduction workshop database.
* To apply a change: the resource owner's prior approval, an approved target ECPU count, a restoration plan, budget and write permission. Otherwise complete the decision-only path below.

## Task 1: Inspect allocation choices

1. Open the assigned database in Azure. Under **Settings**, select **Resource allocation**, then select **Manage**.
2. Compare the current ECPU count, **Compute auto scaling**, storage allocation and **Storage auto scaling** with your baseline. Compute and storage are separate settings. Oracle's [Azure creation guide](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azucr-create-autonomous-ai-database-serverless.html) describes compute auto scaling as allowing expansion up to three times the configured ECPU count as demand increases; actual behavior and limits depend on the service configuration.
3. Note which setting you would change to alter the base compute allocation and which enables automatic compute expansion. Review the potential cost with the resource owner using current pricing and the organization's billing arrangements. The metric and this short query do not establish the right production setting.

## Task 2: Choose the permitted path

**If a temporary change was explicitly approved for this workshop resource:**

1. Record the original ECPU count and both auto scaling settings. Enter the approved temporary ECPU count only. Leave other settings as instructed by the resource owner. Check the resource name and target before selecting **Apply**.
2. Observe the portal operation and wait for a stable state within the session. Reopen **Resource allocation** and record the displayed ECPU count. If the operation is still pending or fails, record that state and notify the owner; do not claim the change succeeded or submit it again.
3. When the change is complete, restore the original ECPU count using **Manage** and **Apply**, unless the resource owner has explicitly instructed that the temporary value be retained for the remaining workshop. Confirm the restored value after the operation completes. If restoration is pending or fails, notify the owner and record the unresolved state and cost implications.

**If a change is not approved or supported:**

1. Record the original setting and a hypothetical target supplied by the facilitator. Explain what additional workload evidence and cost approval you would need before applying it.
2. Select **Cancel**. Record that you inspected and proposed a change; the database configuration was not changed.

**Checkpoint:** You can explain the setting you selected and have either verified the approved change and restoration, recorded an outstanding operation, or completed a decision-only exercise. None of these observations alone proves that auto scaling was triggered.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
