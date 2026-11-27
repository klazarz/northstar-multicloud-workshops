# Give Maya a recovery handoff

## Introduction

Maya needs a clear answer before deciding whether the promotion can proceed. Alex asks you to summarize the evidence and leave the environment owner a useful follow-up.

Estimated lab time: 10 minutes.

### Objectives

* Explain the business result and its limitations.
* Document resource status and ownership for the next action.

### Prerequisites

* Your timeline, clone provenance, and source and recovery-copy results from the previous labs.

## Task 1: Present the evidence

In your own notes or discussion, complete this handoff:

* **Incident:** source database and workshop user; the practice update changed Trail Backpack from 12 to 0; record the UTC times bracketing its commit.
* **Recovery point:** seed commit and backup timestamps in UTC, source identity, and how the chosen clone is linked to that backup.
* **Copy used:** name and whether you created it now or used the prepared copy. If a new clone was submitted but not used, record its latest status and follow-up owner.
* **Validation:** source showed 0; copy showed 12; copy contained six rows and the three shortfalls totaled 40 units. Note any mismatch or missing evidence instead of claiming success.
* **Recommendation to Maya:** ask the inventory owner to verify actual stock and approve any reconciliation. The recovered copy is evidence, not an automatic correction of the source or a live inventory feed.
* **Operations:** identify the owner and next step for each clone, including any in-flight request and costs. Keep the earlier workshop environment intact. Follow the owner's cleanup plan after the learning path; do not delete shared resources.

## Task 2: Close the incident exercise

Tell Maya: “We found a pre-mistake copy in which Trail Backpack shows 12. The practice source still shows 0. We can use the copy to investigate, but the inventory owner must confirm stock and approve a correction.” Adapt that statement if your observed evidence differs.

You have completed the workshop when your recovery copy and evidence are validated and you have a clear handoff. If an access or provenance problem prevented validation, record the blocker and owner rather than treating the exercise as complete.

## Learn more

* [Restore an Autonomous AI Database](https://docs.oracle.com/en-us/iaas/Content/database-at-azure/azurs-restore-autonomous-ai-database-serverless-restore.html)

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
