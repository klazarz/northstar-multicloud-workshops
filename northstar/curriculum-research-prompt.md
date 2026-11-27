# Research and design an Oracle AI Database@Azure LiveLabs curriculum

Act as an experienced Oracle LiveLabs curriculum designer, workshop author, and Oracle AI Database@Azure specialist. Research and recommend a curriculum for Oracle Autonomous AI Database Serverless on Azure, using the documentation index in `01. Oracle Autonomous AI Database Serverless@Azure Workshop.txt` as the starting scope. This assignment is curriculum research and design; do not write full workshops or modify the source index.

## Confirmed design decisions

- Make the QuickStart a shorter prerequisite before each three-workshop learning path. Recommend a realistic duration and ensure it delivers a substantial, visible learner success.
- Design for two delivery options: learners bring their own Azure and OCI environments, or use a pre-provided LiveLabs sandbox environment. Verify whether a suitable sandbox is available and what it supports; identify provisioning and operational gaps rather than assuming availability.
- Propose a scoring rubric and independent review process for the 4.5/5 quality requirement.

Ask the requester only about other decisions that materially affect the design and cannot be resolved through research. Do not invent answers; mark unresolved decisions and explain viable alternatives and consequences.

## Research

- Read every link in the local documentation index and map its content to potential hands-on outcomes. Check the explicitly missing scaling and optimization topic against current authoritative documentation; identify any unsupported or unverified coverage.
- Research current Oracle LiveLabs authoring requirements, templates, manifests, formatting conventions, accessibility guidance, and relevant existing workshops using authoritative sources. Cite exact sources and distinguish confirmed rules from inferred recommendations. If internal rules are inaccessible, identify the gap and request the relevant guidance; do not invent requirements.
- Check current Oracle and Microsoft documentation for availability, prerequisites, permissions, regional constraints, costs, provisioning times, and any service limitations that materially affect the proposed activities. Do not imply that documentation alone proves a live exercise works.
- Identify existing relevant LiveLabs workshops and explain the proposed curriculum's relationship to them, including duplication and opportunities for reuse. Clearly distinguish existing workshops from new proposals.

## Design the curriculum

Recommend a prioritized list of proposed workshops spanning beginner, intermediate, and advanced levels. Aim for approximately 90 minutes per workshop, with a realistic time budget for each lab and any setup, waiting, validation, and wrap-up. Include a starter workshop or QuickStart that teaches fundamentals and gives the learner a compelling, demonstrable success. Recommend its duration based on the proposed activities and realistic setup time.

Propose two or three distinct learning paths, each with three workshops that build on one another and could be delivered in a full-day session on the same environment. Show total teaching time, breaks, setup, and any asynchronous provisioning or contingency time. Describe the state carried forward, dependencies, and a practical entry point for someone taking any workshop independently. Each workshop must have a complete ending: a specific business or technical outcome, visible evidence of success, and a wrap-up that makes sense on its own.

Use an engaging, coherent business story with one or two recurring characters who represent a technical expert and a business user where appropriate. Give each workshop a motivating challenge, learner role, meaningful decisions, and a payoff. Make the story inclusive and credible across different personas; keep dialogue purposeful and technical instructions clear.

For every workshop provide: proposed title, level, target personas, prerequisite knowledge and environment, story and challenge, measurable learning objectives, lab sequence and timed activities, concrete completion evidence, dependencies and standalone entry, documentation coverage with citations, feasibility and constraints, and any optional extensions. Map all indexed topics to workshops, including deletion and cleanup, and identify gaps or topics that are better treated as demonstrations or reference material with reasons. Do not present destructive operations or paid resources as consequence-free. Explain how shared resources are preserved between workshops and cleaned up at the appropriate point.

## Quality and evidence

Each proposed workshop must achieve at least 4.5 out of 5 under the proposed assessment method, subject to requester approval. Propose a transparent rubric covering learner outcome, story, technical accuracy, feasibility, timing, accessibility, LiveLabs conformance, and standalone completion. Define scoring, evidence, reviewer independence, and how deficiencies are resolved. A design-stage estimate is provisional; do not claim a verified 4.5 score without the agreed review and supporting evidence. Identify what requires live validation and what was assessed only from documentation.

## Deliverable

Present an executive recommendation, a workshop catalog, two or three three-workshop path diagrams or tables, a documentation-to-workshop coverage matrix, environment and full-day delivery considerations, existing-workshop comparison, quality assessment, source links, and a concise decision register. Separate verified facts, proposals, and open questions. Cite sources close to claims. Ask only questions that materially change the design, and continue independent research while awaiting answers.

## LiveLabs workshop authoring contract

For subsequent workshop development, study the LiveLabs how-to guide at `common/sample-livelabs-templates/create-labs/labs` in the LiveLabs repository and the adjacent `sample-workshop` templates. Build each workshop as lab folders containing matching lowercase Markdown filenames and `images` folders for lab-specific images. Create `workshops/tenancy` and `workshops/sandbox`, each with its own `index.html` and `manifest.json`; learners choose their environment before starting. Put environment-specific Get Started instructions in separate labs selected by the corresponding manifest, and share environment-neutral labs where appropriate. The sandbox option is named Run on Multicloud; do not invent its reservation or credentials flow. Follow the guide for manifest ordering and relative paths, copy controls, accessible image descriptions, acknowledgements, and available formatting features; omit unused manifest includes and variables. Use real, current screenshots only when available, redact sensitive information, and confirm the stakeholder support address. Preview both manifests in the LiveLabs renderer and complete its QA and accessibility checks before publication. Document any unavailable sandbox or live validation rather than claiming it works.
