# Repair Strategy Codebook

Two researchers independently analyzed corrective actions in the original Pilot group, compared their codes, consolidated categories, and refined boundaries. Categories were not mapped from root-cause IDs. A third author reviewed unresolved cases and assisted adjudication; all three authors jointly confirmed and froze the codebook. The 7 categories describe report-level primary corrective actions. Final labels underwent discussion, third-author adjudication, and joint review by all three authors.

## Coding Unit and Selection Rules

1. The unit is the principal applied corrective action in a report, not every commit or modified line. Assign one strategy per report.
2. Read the repair approach, associated changes, and application status before identifying what was changed. Do not simply rename a root-cause category as a strategy.
3. For patches containing multiple actions, select the action most directly addressing the principal reported failure. Supporting tests, comments, and logs do not replace the primary strategy.
4. Do not choose the primary strategy by the file with the most changed lines. If application, report association, or the specific action cannot be determined, retain a pending status rather than force a category.
5. Documentary confirmation of merging/application is not equivalent to execution validation in this analysis. Retain evidence boundaries for partial repairs and mitigations.
6. Cross-tabulate root causes and strategies after coding is complete. A root cause may correspond to multiple strategies.

## Seven Strategies

### RS01 Interface and representation alignment

**Definition:** Normalize or convert an invoked interface's formats, types, arguments, message protocols, or identifiers so that the producer and consumer follow the same contract.

**Include:** Encoding/decoding, schemas, argument mapping, response structures, provider-message adaptation, interface signatures, call IDs, and input validity.

**Boundary:** Use RS02 for changes limited to available capabilities or context selection; RS06 for final user delivery rather than interface structure; RS05 for authorization boundaries.

**Source example:** NousResearch/hermes-agent #34806, Record ID `R0199`, CSV logical row 65.

**Action summary:** Normalize email-header lookup to lowercase while preserving standard MIME output.

**Issue URL (supplied reference only; not verified online):** https://github.com/NousResearch/hermes-agent/issues/34806

### RS02 Skill and context provisioning

**Definition:** Repair Skill/tool discovery, indexing, loading, source precedence, snapshot refresh, or context selection so that the Agent receives the correct available information.

**Include:** Capability registration and visibility, resource lookup, Skill-cache refresh, history trimming or summary-material selection, context inheritance, and isolated reads.

**Boundary:** Use RS04 for runtime-path/environment-variable configuration adaptation; RS07 for instruction wording alone; RS03 for runtime-state writes and queues.

**Source example:** NousResearch/hermes-agent #76938, Record ID `R0242`, CSV logical row 5.

**Action summary:** Make the background-review fork inherit the model-specific temporary system prompt and prefill to avoid losing necessary context.

**Issue URL (supplied reference only; not verified online):** https://github.com/NousResearch/hermes-agent/issues/76938

### RS03 Execution and state consistency

**Definition:** Repair branching, queues, concurrency, retries, termination, lifecycles, transactions, or state isolation to ensure correct execution progress and state changes.

**Include:** Exception handling, boundary guards, waiting/cancellation, rollback/commit, idempotency and scheduling, session scope, and resource release or budgets.

**Boundary:** Use RS02 for capability-set snapshots alone; RS04 for passing or interpreting existing configuration; RS06 for feedback or delivery alone.

**Source example:** NousResearch/hermes-agent #75228, Record ID `R0241`, CSV logical row 7.

**Action summary:** During rollback, remove partially extracted remnants before restoring the actual Skill tree; retain recovery materials on failure.

**Issue URL (supplied reference only; not verified online):** https://github.com/NousResearch/hermes-agent/issues/75228

### RS04 Configuration and environment adaptation

**Definition:** Correct runtime-parameter loading, precedence, or propagation; supply dependencies or adapt paths, platforms, model configuration, and other runtime prerequisites.

**Include:** Environment-variable or credential propagation, cwd/path compatibility, model capability flags, dependency upgrades, containers or launchers, and configuration migration.

**Boundary:** Use RS05 for permission decisions or secret protection; RS01 for API request/response contracts; RS07 for usage instructions alone.

**Source example:** NousResearch/hermes-agent #63938, Record ID `P0233`, CSV logical row 19.

**Action summary:** Convert Windows drive-manifest paths into paths usable by WSL subprocesses.

**Issue URL (supplied reference only; not verified online):** https://github.com/NousResearch/hermes-agent/issues/63938

### RS05 Access and trust-boundary enforcement

**Definition:** Implement or correct authorization, trust, resource ownership, and confidentiality policies to prevent inappropriate access or remove erroneous rejection.

**Include:** Server-side permission checks, approval policies, path-containment checks, key redaction, prompt-injection isolation, and safeguards before destructive actions.

**Boundary:** Ordinary null/type checks are not security checks; use RS01/RS03. Use RS04 for changes limited to configuration-value propagation.

**Source example:** openclaw/openclaw #66769, Record ID `P0066`, CSV logical row 226.

**Action summary:** Redact API keys and environment secrets from outgoing skills.update responses while retaining internal originals.

**Issue URL (supplied reference only; not verified online):** https://github.com/openclaw/openclaw/issues/66769

### RS06 Feedback and artifact delivery

**Definition:** Repair the propagation, diagnosis, delivery, or verification of execution results, status, errors, and artifacts to the Agent or user so that results are interpretable and accessible.

**Include:** Explicit error receipts, success determination, file/media delivery, displayed result status, progress feedback, and user-response chunking or deduplication.

**Boundary:** Use RS01 for machine-message conversion required by a provider protocol; RS03 for events needed to complete the execution lifecycle.

**Source example:** NousResearch/hermes-agent #67052, Record ID `R0236`, CSV logical row 17.

**Action summary:** Complete action-verification feedback and connect it to upgrade and approval feedback so the Agent can continue based on execution results.

**Issue URL (supplied reference only; not verified online):** https://github.com/NousResearch/hermes-agent/issues/67052

### RS07 Procedural guidance correction

**Definition:** Revise instructions and constraints in Skill descriptions, prompt templates, or operating documentation so they match supported operations and applicable conditions.

**Include:** Command-usage clarification, removal of incorrect mandatory steps, task-role or approval wording, success/failure handling guidance, and Skill-authoring standards.

**Boundary:** Do not select this category when wording changes merely accompany the main code repair. Use RS02 for prompt selection/injection rather than changes in instruction meaning.

**Source example:** openclaw/openclaw #52540, Record ID `P0048`, CSV logical row 161.

**Action summary:** Remove the incorrect requirement to use tmux for desktop authentication.

**Issue URL (supplied reference only; not verified online):** https://github.com/openclaw/openclaw/issues/52540

## Frequently Confused Boundaries and Final-Review Examples

- RS01 vs RS03: type/field/message contracts use RS01; control flow, mutable state, transactions, and runtime lifecycles use RS03. Pi #1115 ultimately uses RS01 because undefined arguments violate the object schema, not merely because deep copying was also added.
- RS02 vs RS04: selecting or injecting Skills/context uses RS02; resolving the same resource to the correct platform path or passing the correct model/environment configuration uses RS04.
- RS04 vs RS05: adapting a usable credential backend or correcting paths does not automatically constitute access hardening. Explicit authorization/trust checks, approval changes, or secret disclosure controls use RS05.
- RS02 vs RS07: changing which content is supplied and where uses RS02; changing instruction meaning, operational constraints, or applicability uses RS07.
- RS01 vs RS06: low-level protocol response conversion uses RS01; turning actual execution results into status, diagnostics, or artifacts useful to the user or subsequent decisions uses RS06.
- RS03 vs RS06: changing when execution starts/ends or how rollback occurs uses RS03; correcting user-facing status, error explanations, or file delivery without changing the core action uses RS06.

## Agreement Interpretation

Two researchers independently annotated the same reliability reports using the frozen codebook, with labels concealed from each other and without discussion or access to the other researcher's labels. Both original label sets were saved and locked. Kappa was calculated before discussion, third-author review, or adjudication; the third author was not included in kappa. The two researchers first discussed the 32 disagreements, after which a third author examined original evidence and adjudicated unresolved cases. All three authors jointly confirmed final labels. Original labels, kappa, and existing classification results remain unchanged.
Missing or zero change size does not mean no repair. The current 359 reports form a working set of codable corrective actions, including partial-repair and change-attribution risk flags; they are not a verified 508-report research gold standard.
CSV logical row numbers refer to parsed record positions, including the header, rather than physical text-line numbers in files containing multiline fields.
