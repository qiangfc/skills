# Analysis Materials for Failures in Agent–Skill Interactions

This repository organizes reports of failures encountered when agents use Skills and tools. It contains analyses of failure symptoms, root-cause mechanisms, task impact, user observability, repair strategies, and repair cost.

The materials cover five open-source projects: OpenClaw, Hermes Agent, Dify, Open WebUI, and pi. Organized around four research questions, the repository contains 32 research artifacts, including coding definitions, annotation records, category labels, supporting evidence, consolidation and review records, and agreement calculations. These materials support checking the results and tracing the coding process.

## Research Questions

- **RQ1 — Symptoms:** What user- or system-observable anomalies characterize the reported failures?
- **RQ2 — Root Causes:** What implementation, configuration, or runtime mechanisms cause these failures?
- **RQ3 — Impact and Observability:** How do failures affect users' tasks, and are they directly apparent from normal user-facing feedback?
- **RQ4 — Repair:** What repair strategies are used, and how do handling duration and code change size vary across root-cause categories?

## Repository Structure

```text
.
├── RQ1(Symptoms)/
├── RQ2(Root Causes)/
├── RQ3(Impact and Observability)/
└── RQ4(repair)/
```

## RQ1: Failure Symptoms

`RQ1(Symptoms)` contains the classification and coding-process materials for failure symptoms. The codebook defines **21 failure-symptom categories**, identified by `S01`–`S21`, with definitions, inclusion and exclusion criteria, category boundaries, single-label decision rules, and evidence examples.

Key files:

- `RQ1_Codebook.xlsx`: Failure-symptom codebook and associated frequency information.
- `Full_Sample_Classification_Labels.xlsx`: Per-report category labels, stages, components, rationales, and confirmation records.
- `Pilot_Initial_Coding_Round_1.xlsx` and `Pilot_Initial_Coding_Round_2.xlsx`: Initial coding and evidence excerpts from the two pilot rounds.
- `Pilot_Code_Comparison_and_Consolidation.xlsx`: Pilot-code comparison, consolidation of similar codes, category revisions, stage coverage, and unresolved items.
- `Reliability_Original_Labels_Round_1.xlsx` and `Reliability_Original_Labels_Round_2.xlsx`: Original labels and rationales from the two rounds of reliability-sample annotation.
- `Reliability_and_Final_Review.xlsx`: Agreement calculations, original-label comparisons, disagreement handling, and final review results.

## RQ2: Root-Cause Mechanisms

`RQ2(Root Causes)` contains the classification and coding-process materials for root-cause mechanisms. The codebook defines **24 root-cause categories**, identified by `C01`–`C24`. Root-cause classification focuses on the implementation or configuration mechanism that directly causes the failure; stages and components describe where the mechanism resides.

`RQ2_Codebook.xlsx` is the root-cause codebook. The remaining files follow the same naming convention as RQ1 and contain per-report root-cause labels, two rounds of pilot coding, consolidation records, two rounds of original reliability labels, and final review results, together with relevant stages, components, and evidence.

## RQ3: Task Impact and User Observability

`RQ3(Impact and Observability)` contains annotations and analyses of two outcome attributes. Each report receives one primary label for each attribute.

**Task impact** captures the principal consequence of the failure for the user's task:

- `Noncompletion`: The task is not completed.
- `Partial completion`: The task is partially completed.
- `Incorrect result`: The execution produces an incorrect result.

**User observability** captures how the failure can be detected:

- `Directly apparent`: The failure is directly apparent from normal user-facing responses, interfaces, or operational feedback.
- `Requires additional verification`: Detecting the failure requires additional checking of outputs, logs, actual execution, or persistent state.

Insufficient evidence is retained as `Undetermined` in the original annotations. Subsequent assignments and review results separately retain their rationales and assignment types.

Key files:

- `RQ3_Attribute_Analysis.xlsx`: Attribute analyses, representative labels, and typical cases organized by failure-symptom and root-cause category.
- `Full_Sample_Labels.csv`: Per-report attribute labels for 901 reports, together with related classifications, rationales, and assignment types. This file supports full-sample attribute distributions and the joint distribution of the two attributes.
- `Pilot_Attribute_Labels.csv`: Supplementary attribute annotations and rationales for 454 pilot reports.
- `Reliability_Original_Labels_Round_1.csv` and `Reliability_Original_Labels_Round_2.csv`: Original annotations from two rounds covering 447 reliability reports.
- `Original_Label_Comparison.csv`: Field-level comparisons of the two rounds of original labels.
- `Disagreements_and_Undetermined_Review.csv`: Subsequent review records for disagreements and undetermined items.
- `Pilot_Supplement_Impact_Review.md`: Review of how supplementary pilot annotations affect attribute distributions and category-level primary labels.

## RQ4: Repair Strategies and Repair Cost

`RQ4(repair)` contains repair-strategy coding and review materials, along with handling-duration and code-change-size summaries by root-cause category.

The four repair strategies are:

- `F01 Representation and usage-contract alignment`
- `F02 Execution-flow and state correction`
- `F03 Validation and failure-path hardening`
- `F04 Environment and distribution adaptation`

Key files:

- `Repair_Strategy_Codebook.xlsx`: Descriptions, examples, and distribution information for the four strategies.
- `Root_Cause_Repair_Cost.xlsx`: Handling-duration and code-change-size summaries and analyses by root-cause category.
- `Pilot_Initial_Coding_Round_1.xlsx` and `Pilot_Initial_Coding_Round_2.xlsx`: Repair-strategy coding from the two pilot rounds.
- `Pilot_Consolidation_and_Review.xlsx`: Strategy consolidation, version records, and pilot review records.
- `Reliability_Original_Labels_Round_1.xlsx` and `Reliability_Original_Labels_Round_2.xlsx`: Two rounds of original reliability labels.
- `Reliability_and_Final_Review.xlsx`: Agreement results, the confusion matrix, disagreement handling, final review of 481 strategy reports, and statistical results.

Handling duration and code change size serve as descriptive indicators of repair cost. Measurement rules and valid sample sizes are documented in the corresponding files. Strategy labels retain evidence statuses distinguishing assignments supported by available materials from inferred matches.

## Organization of Coding and Review Materials

The materials follow this sequence: initial pilot coding, code comparison and consolidation, codebook finalization, reliability-sample annotation, agreement calculation, and disagreement handling and final review.

Agreement is calculated from the two rounds of original labels before discussion and revision. Subsequent reviewed labels are stored separately. Refer to the corresponding files for each field's valid sample size, observed agreement, Cohen's Kappa, annotation statuses, and missing-input information.

## Suggested Reading Order and Statistical Scope

1. Read each RQ's codebook to understand category definitions, boundaries, and decision criteria.
2. Consult per-report labels or final review sheets, using report identifiers, URLs, and category IDs to locate reports and evidence.
3. Examine the two rounds of original coding, consolidation records, and disagreement records to trace how individual labels were formed.
4. Calculate distributions from the per-report labels for the relevant sample, and interpret them alongside stages, components, and evidence statuses.

The repository retains materials from code development, reliability assessment, and subsequent aggregation. When reporting frequencies, percentages, or agreement results, identify the corresponding file, version, sample scope, and denominator. Category-level representative labels support category interpretation, while per-report labels support sample-level statistics. Interpret inferred matches together with their recorded rationales and evidence scope.
