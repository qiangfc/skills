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
│   ├── RQ1_Codebook.xlsx
│   ├── Full_Sample_Classification_Labels.xlsx
│   └── Coding_Process/
├── RQ2(Root Causes)/
│   ├── RQ2_Codebook.xlsx
│   ├── Full_Sample_Classification_Labels.xlsx
│   └── Coding_Process/
├── RQ3(Impact and Observability)/
│   ├── RQ3_Attribute_Analysis.xlsx
│   ├── Full_Sample_Labels.csv
│   └── Coding_Process/
└── RQ4(repair)/
    ├── Repair_Strategy_Codebook.xlsx
    ├── Root_Cause_Repair_Cost.xlsx
    ├── Full_Sample_Labels.xlsx
    └── Coding_Process/
```

Each RQ directory keeps its codebook, full-sample labels, and main analyses at the root, where applicable. Its `Coding_Process/` subfolder contains the coding, consolidation, reliability, and review records.

## RQ1: Failure Symptoms

`RQ1(Symptoms)` contains the classification and coding-process materials for failure symptoms. The codebook defines **21 failure-symptom categories**, identified by `S01`–`S21`, with definitions, inclusion and exclusion criteria, category boundaries, single-label decision rules, and evidence examples.

Key files:

- `RQ1_Codebook.xlsx`: Failure-symptom codebook and associated frequency information.
- `Full_Sample_Classification_Labels.xlsx`: Per-report category labels, stages, components, rationales, and confirmation records.
- `Coding_Process/Pilot_Initial_Coding_Round_1.xlsx` and `Coding_Process/Pilot_Initial_Coding_Round_2.xlsx`: Initial coding and evidence excerpts from the two pilot rounds.
- `Coding_Process/Pilot_Code_Comparison_and_Consolidation.xlsx`: Pilot-code comparison, consolidation of similar codes, category revisions, stage coverage, and unresolved items.
- `Coding_Process/Reliability_Original_Labels_Round_1.xlsx` and `Coding_Process/Reliability_Original_Labels_Round_2.xlsx`: Original labels and rationales from the two rounds of reliability-sample annotation.
- `Coding_Process/Reliability_and_Final_Review.xlsx`: Agreement calculations, original-label comparisons, disagreement handling, and final review results.

## RQ2: Root-Cause Mechanisms

`RQ2(Root Causes)` contains the classification and coding-process materials for root-cause mechanisms. The codebook defines **24 root-cause categories**, identified by `C01`–`C24`. Root-cause classification focuses on the implementation or configuration mechanism that directly causes the failure; stages and components describe where the mechanism resides.

`RQ2_Codebook.xlsx` is the root-cause codebook, and `Full_Sample_Classification_Labels.xlsx` contains the per-report root-cause classifications. The `Coding_Process/` files follow the same naming convention as RQ1 and contain two rounds of pilot coding, consolidation records, two rounds of original reliability labels, and final review results, together with relevant stages, components, and evidence.

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
- `Coding_Process/Pilot_Attribute_Labels.csv`: Supplementary attribute annotations and rationales for 454 pilot reports.
- `Coding_Process/Reliability_Original_Labels_Round_1.csv` and `Coding_Process/Reliability_Original_Labels_Round_2.csv`: Original annotations from two rounds covering 447 reliability reports.
- `Coding_Process/Original_Label_Comparison.csv`: Field-level comparisons of the two rounds of original labels.
- `Coding_Process/Disagreements_and_Undetermined_Review.csv`: Subsequent review records for disagreements and undetermined items.

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
- `Full_Sample_Labels.xlsx`: Final repair-strategy labels for all 481 reports included in the strategy analysis, with strategy names, repair actions, assignment rationales, review records, evidence statuses, and URLs. The worksheet is named `Full_Sample_Labels`.
- `Coding_Process/Pilot_Initial_Coding_Round_1.xlsx` and `Coding_Process/Pilot_Initial_Coding_Round_2.xlsx`: Repair-strategy coding from the two pilot rounds.
- `Coding_Process/Pilot_Consolidation_and_Review.xlsx`: Strategy consolidation, version records, and pilot review records.
- `Coding_Process/Reliability_Original_Labels_Round_1.xlsx` and `Coding_Process/Reliability_Original_Labels_Round_2.xlsx`: Two rounds of original reliability labels.
- `Coding_Process/Reliability_and_Final_Review.xlsx`: Agreement results, the confusion matrix, disagreement handling, final review of 481 strategy reports, and statistical results.

Handling duration and code change size serve as descriptive indicators of repair cost. Measurement rules and valid sample sizes are documented in the corresponding files. Strategy labels retain evidence statuses distinguishing assignments supported by available materials from inferred matches.
