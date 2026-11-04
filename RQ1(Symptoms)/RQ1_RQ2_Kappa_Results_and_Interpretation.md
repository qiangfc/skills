# Kappa Results and Interpretation

## Calculation Scope and Inputs

The current full sample contains 901 reports: 454 pilot reports and 447 reliability reports. Pilot reports support category development and do not enter this Kappa calculation. This recalculation uses the currently stored two rounds of pre-discussion labels to assess RQ1 failure symptoms, RQ2 root causes, observation stages, root-cause stages, and primary components.

Input files (paths relative to the repository root):

- RQ1: `RQ1(Symptoms)/Coding_Process/Reliability_Original_Labels_Round_1.xlsx` and `RQ1(Symptoms)/Coding_Process/Reliability_Original_Labels_Round_2.xlsx`.
- RQ2: `RQ2(Root Causes)/Coding_Process/Reliability_Original_Labels_Round_1.xlsx` and `RQ2(Root Causes)/Coding_Process/Reliability_Original_Labels_Round_2.xlsx`.

Records are aligned by record ID and checked against Issue URLs. All four files contain 447 records, with matching record sets across rounds. RQ1 uses the current symptom IDs S01–S19; RQ2 uses root-cause IDs C01–C24. Existing labels are read without modification. Post-discussion consensus or final classifications do not replace the original inputs.

## Method

Unweighted Cohen’s Kappa (κ) is used. Observed agreement p_o is the number of matching labels divided by the number of valid pairs. Chance agreement p_e is the sum of the products of the two rounds’ marginal proportions for each category or status.

$$
\kappa=\frac{p_o-p_e}{1-p_e},\qquad p_e=\sum_j p_{1j}p_{2j}.
$$

“Undetermined: insufficient evidence” and “Undetermined: codebook not covered” enter the calculation as distinct values. Only absent annotation input counts as missing; missing inputs are not filled with Undetermined labels. Each field uses only records with input in both rounds. Recorded values outside the four-stage framework remain distinct values rather than being forced into one of the four stages. Kappa is not computable when there are no valid pairs or p_e=1.

## Recalculated Results

- **Failure symptom:** valid n=447; 421 agreements; 26 disagreements; observed agreement p_o=0.94183445 (94.18%); chance agreement p_e=0.071323; **κ=0.937367**.
- **Root cause:** valid n=447; 427 agreements; 20 disagreements; observed agreement p_o=0.95525727 (95.53%); chance agreement p_e=0.310166; **κ=0.935140**.
- **Observation stage:** valid n=447; 440 agreements; 7 disagreements; observed agreement p_o=0.98434004 (98.43%); chance agreement p_e=0.208604; **κ=0.980212**.
- **Root-cause stage:** valid n=447; 430 agreements; 17 disagreements; observed agreement p_o=0.96196868 (96.20%); chance agreement p_e=0.344179; **κ=0.942010**.
- **Primary component:** valid n=447; 438 agreements; 9 disagreements; observed agreement p_o=0.97986577 (97.99%); chance agreement p_e=0.059222; **κ=0.978598**.

The per-record primary-component inputs are identical in the RQ1 and RQ2 files, so only one primary-component coefficient is reported. Every field has 447 valid pairs and a computable coefficient.

## Interpretation

Kappa measures agreement remaining after accounting for chance agreement expected from the two rounds’ label distributions. κ=1 indicates complete agreement, κ=0 indicates agreement equal to that chance baseline, and negative values indicate agreement below the baseline.

All five coefficients are close to 1, indicating high agreement between the current two rounds under the annotation rules used. Symptom κ is approximately 0.9374 and root-cause κ approximately 0.9351. They assess different fields and cannot substitute for each other.

Kappa is not classification accuracy and does not establish experimental verification of a root cause. For example, symptom κ=0.937367 does not mean that “93.74% of judgments are correct.” No categorical interpretation thresholds are applied here.

## Undetermined and Missing-Input Proportions

The denominator for each round’s proportions below is 447:

- **Failure symptom:** insufficient evidence in 15 annotations in Round 1 (3.36%) and 16 in Round 2 (3.58%); codebook-uncovered counts are 1 and 1; missing-input counts are 0 and 0, respectively.
- **Root cause:** insufficient evidence in 251 annotations in Round 1 (56.15%) and 238 in Round 2 (53.24%); codebook-uncovered counts are 0 and 0; missing-input counts are 0 and 0, respectively.
- **Observation stage:** insufficient evidence in 15 annotations in Round 1 (3.36%) and 16 in Round 2 (3.58%); codebook-uncovered counts are 0 and 0; missing-input counts are 0 and 0, respectively.
- **Root-cause stage:** insufficient evidence in 251 annotations in Round 1 (56.15%) and 238 in Round 2 (53.24%); codebook-uncovered counts are 0 and 0; missing-input counts are 0 and 0, respectively.
- **Primary component:** insufficient evidence in 5 annotations in Round 1 (1.12%) and 6 in Round 2 (1.34%); codebook-uncovered counts are 0 and 0; missing-input counts are 0 and 0, respectively.

The current symptom field contains one codebook-uncovered annotation in each round (0.22% per round). This status is included as a distinct value in Kappa and is not missing input. The codebook-uncovered count is 0 for all other fields. No field has missing input in either round.

Root-cause annotations have insufficient evidence in 251 reports (56.15%) and 238 reports (53.24%) in the two rounds, respectively. Both rounds assigning “insufficient evidence” to a report counts as agreement. High Kappa therefore does not establish that those unresolved root causes have been located. Undetermined proportions for observation and root-cause stages should likewise be interpreted alongside their respective coefficients.

## Post-Calculation Review and Final Classification

The coefficients above use current pre-discussion labels. Labels from disagreement discussion, adjudication, or final review do not replace those inputs. Subsequent evidence review and final classification are separate steps; consensus agreement from those steps cannot serve as the independent agreement result reported here.

Full-sample classification combines 454 pilot reports and 447 reliability reports, totaling 901 reports. See `Full_Sample_Classification_Labels.xlsx` in each RQ directory. Final full-sample classifications are not inputs to this Kappa calculation. Human review and adjudication confirmation fields should reflect actual completion; blank fields must not be described as confirmed.

## Software and Cross-Check

The recalculation uses Python 3.12.14 and the standard-library `Fraction` class for exact rational arithmetic. An independent counting implementation in Node.js v24.22.1 cross-checks the results. Valid sample sizes, agreement counts, p_o, p_e, and κ agree, with floating-point coefficient differences below 1×10⁻¹². The statsmodels library was not invoked.

Method reference: [statsmodels documentation for Cohen’s Kappa](https://www.statsmodels.org/stable/generated/statsmodels.stats.inter_rater.cohens_kappa.html).

The statistics in this document are synchronized with the `Overall Reliability`, `Statuses and Missing Input`, and `Reliability by Repository` worksheets in the following workbooks:

- RQ1: `RQ1(Symptoms)/Coding_Process/Reliability_and_Final_Review.xlsx`.
- RQ2: `RQ2(Root Causes)/Coding_Process/Reliability_and_Final_Review.xlsx`.

The methodology notes in both workbooks use the same 447-report calculation base. The original annotation workbooks remain unchanged as the calculation inputs.
