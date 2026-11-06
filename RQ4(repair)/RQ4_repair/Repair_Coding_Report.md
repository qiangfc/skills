# Two-Pass Repair-Strategy Coding, Root-Cause Associations, and Data Audit

## Scope

This analysis uses the latest CSV (901 reports) and the matching XLSX for human annotation and review. No external GitHub pages were consulted and no patches were executed for validation. Original pilot/reliability assignments are retained. Root-cause IDs were not automatically mapped to repair strategies.
The outputs contain two sets of original labels, report-level action explanations, human-reviewed labels, the strategy codebook, disagreements, root-cause cross-tabulations, and all 901 source reports. Two researchers independently analyzed the original pilot reports and discussed category consolidation. A third author examined unresolved cases, and the codebook was jointly confirmed and frozen. The two researchers then independently annotated the same reliability reports with labels concealed from each other, without discussion or access to the other researcher's labels. Both original label sets were saved and locked; kappa was calculated before discussion, third-author review, and adjudication.

## Sample Reconciliation

|Level|Reports|Description|
|---|---:|---|
|Current source CSV|901|454 Pilot + 447 Reliability|
|Candidates whose first parseable change-size value is positive|398|A positive line count does not prove that a repair was applied or is related to the report|
|Working set with codable corrective actions|359|187 Pilot + 172 Reliability; human annotation and review completed|
|Positive-line-count candidates requiring further evidence|18|Application status, report association, specific action, or repository scope remains unclear|
|Positive-line-count candidates excluded|21|Unmerged, rejected, unrelated, recorded as zero, or a failure-inducing commit|
|Zero or no extractable positive change size|503|477 reports have an initial parsed value of 0; 26 have no extractable value. This does not mean all were unrepaired|

The supplied files do not include the original 508-report manifest. The 359 reports therefore cannot be described as a complete recoding of the original 508 reports, and the paper's sample size must not be silently changed.
Classifying these 359 reports does not make whole-PR line counts valid measurements of relevant change size. Records involving broad PRs, partial repairs, shared patches, or scope concerns retain corresponding notes. No unverified LOC means or totals are reported.

## Strategy Distribution (Denominator: 359 Reports)

|Strategy|Name|Count|Percentage|
|---|---|---:|---:|
|RS01|Interface and representation alignment|75|20.89%|
|RS02|Skill and context provisioning|50|13.93%|
|RS03|Execution and state consistency|75|20.89%|
|RS04|Configuration and environment adaptation|72|20.06%|
|RS05|Access and trust-boundary enforcement|38|10.58%|
|RS06|Feedback and artifact delivery|35|9.75%|
|RS07|Procedural guidance correction|14|3.90%|

## Agreement Between Original Annotation Sets

|Subset|n|Agreements|Disagreements|p_o|p_e|Cohen's κ|
|---|---:|---:|---:|---:|---:|---:|
|Codable reports in the original Reliability group|172|158|14|0.918605|0.168233|0.902142|
|All codable reports (including Pilot)|359|327|32|0.910864|0.169040|0.892731|
|Pilot (supplementary only)|187|169|18|0.903743|0.171152|0.883867|

Calculation: p_o is the proportion of matching original labels; p_e = Σ_c(n_1c × n_2c) / n²; κ = (p_o - p_e) / (1 - p_e).
The primary result uses the original reliability subset of 172 reports. Results for all 359 reports include pilot reports used to develop categories and are supplementary only. For reliability reports, the original label sets come from two researchers' independent, mutually blinded annotation. Kappa was calculated before discussion and third-author adjudication. It describes agreement between annotators, not annotation accuracy or external validity.
All 32 disagreements (including 14 reliability-group disagreements) retain their original labels. The two researchers discussed disagreements first; a third author examined the original evidence and adjudicated unresolved cases. All three authors jointly confirmed final labels. Discussion and adjudication did not overwrite either original label set. Evidence review of the 58 priority-review records is complete, with labels and statistical results unchanged.

## Observed Associations with Root Causes

Each denominator below is the number of codable reports for that root cause within the 359-report working set, not its total among all 901 reports.

|Root cause|Most frequent strategy|Count / codable reports for the root cause|Percentage|
|---|---|---:|---:|
|C02 Data-type or schema mismatches|RS01 Interface and representation alignment|15/18|83.33%|
|C09 Discovery and loading rule errors|RS02 Skill and context provisioning|14/15|93.33%|
|C11 Asynchronous lifecycle races|RS03 Execution and state consistency|17/20|85.00%|
|C15 Flawed security or authorization boundary checks|RS05 Access and trust-boundary enforcement|24/28|85.71%|
|C16 Configuration handling errors|RS04 Configuration and environment adaptation|16/19|84.21%|
|C13 Incomplete error and result feedback|RS06 Feedback and artifact delivery|10/11|90.91%|
|C14 Incomplete artifact-delivery conversion|RS06 Feedback and artifact delivery|7/10|70.00%|
|C23 Incorrect operational guidance|RS07 Procedural guidance correction|7/11|63.64%|

C08 Context selection and injection errors illustrates why root causes do not directly determine strategies: of its 14 codable reports, 9 use RS02 (correcting context selection, injection, or inheritance) and 5 use RS07 (revising prompt/guidance semantics).
Root causes and repair strategies are not in one-to-one correspondence. The cross-tabulation describes associations among the working labels; it does not establish deployment failure probabilities or causal strategy effects.

## Working Findings on Agent–Skill Interaction

Repairs involve more than rewording Skill instructions. They also concern whether Skill/tool capabilities can be discovered, whether the correct context is propagated, whether instructions become arguments/protocols accepted by the runtime, and whether actual results support subsequent decisions and delivery.
RS02 and RS07 are distinct: the former changes which Skills and context reach the agent; the latter changes the meaning of the instructions themselves. RS06 corrects feedback/delivery gaps. A successful tool operation alone does not establish task completion.
Interface/representation alignment, execution/state consistency, and configuration/environment adaptation together account for 222/359 reports (61.84%). This percentage applies only to the current codable subset, not all 901 reports or the previously stated 508-report set.

## Evidence-Audit Examples

* Hermes Agent #73388: the 267 lines belong to a still-open, unmerged proposal and are not treated as an applied repair.
* Hermes Agent #73841: the 163 lines belong to an unmerged proposal. A later 215-line repair of the same type is listed separately; the source records 0 issue-specific lines, so the later change is not forced into that measurement.
* Dify #18276: the cited 6 lines correct CONTRIBUTING spelling, not the reported runtime failure.
* OpenClaw #64921: the corrective action is identifiable, but 1695 lines belong to a broad refactor and cannot directly represent report-related change size.
* OpenClaw #54013 and #55382 share PR #55202: report-level strategy frequencies may count both reports, but this does not create two independent patches or justify counting patch size twice.

These are checks of the supplied records, not new online PR verification. See each record's original text, rationale, and source logical-row locator.

## File Index

* Repair_Strategy_Coding.xlsx: main workbook containing definitions, two annotation sets, scope audit, disagreements, cross-tabulations, and formulas.
* Coded_359_Two_Passes_and_Review.csv: both original label sets and reviewed labels for all 359 reports.
* All_901_Eligibility_and_Human_Codes.csv: all 901 source reports and eligibility statuses; no report was silently removed.
* Positive_LOC_Candidates_Excluded_or_Pending.csv: 39 excluded or pending positive-line-count candidates and their reasons.
* Priority_Human_Review.csv: 58 priority human-review records.
* Human_Review_Template_Blank.csv: blank human-annotation template without existing strategy or root-cause labels.
* pass1_locked.json, pass2_locked.json, final_codes_reviewed.json: original annotation sets and reviewed results.
* agreement_statistics.json, analysis_manifest.json: statistical results, scope, input hashes, and annotation-set hashes.
* recompute_statistics.py: recalculates statistics from exported coding CSVs; it does not assign strategies automatically.

Original source files were not overwritten.
