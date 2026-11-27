# QuickStart quality review

Review date: 27 November 2026. This is an author-side design review, not the independent review required by the curriculum quality gate. Scores are provisional judgments based on the written draft and source checks; they are not evidence that the workshop has achieved 4.5/5 in delivery.

| Criterion | Draft score / 5 | Evidence and remaining work |
|---|---:|---|
| Learner outcome and proof | 4.5 | Expected results and a business recommendation give a concrete finish. Verify results against a live database. |
| Story and motivation | 4.5 | Maya has a deadline and a decision; Alex guides the learner, who supplies the evidence. Validate engagement with representative learners. |
| Technical accuracy | 4.0 | Data arithmetic was checked locally and connection guidance references Oracle documentation. Oracle SQL, grants, UI labels and network behavior require a live run. |
| Feasibility and environment | 3.5 | Both routes define prerequisites and ownership; an Azure-capable provided sandbox and exact access experience remain unconfirmed. |
| Timing | 3.5 | Task estimates total 45 minutes with setup beforehand. A beginner pilot must measure actual time and waiting. |
| Accessibility and clarity | 4.0 | Text describes expected results and the task sequence, and does not depend on color. Screen-reader, keyboard, rendered layout and learner comprehension need review. |
| LiveLabs conformance | 3.5 | Introduction, objectives, prerequisites, numbered tasks, acknowledgements and copy markers follow a [public LiveLabs example](https://github.com/oracle-livelabs/database/blob/main/db-21c-fundamentals/setup/setup.md). Current requirements, rendering, manifest, images and publishing workflow need confirmation. |
| Standalone completion | 4.0 | The workshop ends with a complete recommendation and names its prerequisites. Clean-schema recovery and both access routes require a pilot. |

**Provisional mean: 4.0/5.** The current draft does not pass the proposed release gate of 4.5 overall and 4.0 in every criterion. Scores are not independent and may change after the pilot.

## Improvements made in this review

The story now has a clear deadline, a decision Maya can act on, and a reason for the learner to check the results. The closing task asks learners to formulate their own answer before viewing the example. Tasks have a single numbered sequence with a 45-minute budget, concise troubleshooting, clearer transaction guidance, and copy markers patterned on a public LiveLabs example. Copy markers must be verified in the target renderer; ordinary Markdown viewers may display them as text.

## Validation and release actions

1. Confirm an actual provided Azure environment, its reservation and access flow, identity isolation, lifetime, support, cost and cleanup. Run the bring-your-own route with a separate representative setup.
2. Run every statement and connection step on the target service as a minimally privileged learner, including commit behavior, partial completion and the correct worksheet controls. Confirm the expected data and outputs.
3. Observe a beginner completing each route; record task times and revise the 45-minute estimate or content based on evidence. Confirm what happens when the next workshop provisions a separate database.
4. Render in the intended LiveLabs platform; check copy controls, headings, lists, links, tables, keyboard navigation, screen reader behavior and any required screenshots or alternative text. Obtain current authoring and publishing rules and add a validated manifest and acknowledgements.
5. Have a reviewer independent of the author assess all eight criteria using pilot evidence. Resolve critical defects, score each criterion again, and meet the agreed 4.5/5 overall and 4.0 minimum per criterion before release.
