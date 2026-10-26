# Impact Review of Supplementary Pilot Annotation

- Supplemented 454 pilot reports, each with one task-impact label and one user-observability label.
- Combined total: 901 reports. The added labels contain no blanks or Undetermined values.
- The pilot contains 77 best-fit inferences, with the rationale retained for each report.
- RQ3_Attribute_Analysis.xlsx retains its existing contents. Neither the labels for the 447 reliability reports nor the Kappa file were changed.

## Effect on the Results

- 43 categories and 2 attributes yield 86 category–attribute comparisons.
- The original primary label is no longer modal in 9 comparisons, affecting 7 categories.
- The original primary label remains modal but is tied in 3 comparisons.
- The original primary label remains the unique mode in 74 comparisons.
- The within-category percentage of the original primary label changes in 82 comparisons.
- Across all reports, Noncompletion remains the modal task-impact label and Directly apparent remains the modal user-observability label.

## Comparisons Where the Original Primary Label Is No Longer Modal

- S14 Performance degradation / User observability: Original label Requires additional verification, 11/20 (55.00%) in the reliability sample; after adding pilot reports, 18/39 (46.15%). Full-sample modal label(s): Directly apparent, 21/39 (53.85%).
- S19 Ineffective controls / Task impact: Original label Noncompletion, 17/36 (47.22%) in the reliability sample; after adding pilot reports, 28/79 (35.44%). Full-sample modal label(s): Incorrect result, 40/79 (50.63%).
- C07 Stale caches or snapshots / Task impact: Original label Noncompletion, 6/13 (46.15%) in the reliability sample; after adding pilot reports, 8/24 (33.33%). Full-sample modal label(s): Incorrect result, 9/24 (37.50%).
- C07 Stale caches or snapshots / User observability: Original label Directly apparent, 7/13 (53.85%) in the reliability sample; after adding pilot reports, 10/24 (41.67%). Full-sample modal label(s): Requires additional verification, 14/24 (58.33%).
- C14 Incomplete artifact-delivery conversion / Task impact: Original label Partial completion, 7/13 (53.85%) in the reliability sample; after adding pilot reports, 9/22 (40.91%). Full-sample modal label(s): Noncompletion, 13/22 (59.09%).
- C15 Flawed security or authorization boundary checks / User observability: Original label Directly apparent, 10/20 (50.00%) in the reliability sample; after adding pilot reports, 19/47 (40.43%). Full-sample modal label(s): Requires additional verification, 28/47 (59.57%).
- C22 Model interpretation or generation errors / Task impact: Original label Partial completion, 5/10 (50.00%) in the reliability sample; after adding pilot reports, 8/26 (30.77%). Full-sample modal label(s): Noncompletion / Incorrect result, 9/26 (34.62%).
- C22 Model interpretation or generation errors / User observability: Original label Requires additional verification, 6/10 (60.00%) in the reliability sample; after adding pilot reports, 12/26 (46.15%). Full-sample modal label(s): Directly apparent, 14/26 (53.85%).
- C24 Persistence inconsistencies / User observability: Original label Directly apparent, 6/9 (66.67%) in the reliability sample; after adding pilot reports, 7/19 (36.84%). Full-sample modal label(s): Requires additional verification, 12/19 (63.16%).

## Comparisons With Tied Modal Labels

- C05 Identifier and association errors / Task impact: Noncompletion / Incorrect result, each 19/43 (44.19%).
- C13 Incomplete error and result feedback / User observability: Directly apparent / Requires additional verification, each 18/36 (50.00%).
- C24 Persistence inconsistencies / Task impact: Noncompletion / Partial completion, each 7/19 (36.84%).

## Overall Label Counts

### Task impact

- Noncompletion: 290 of 447 reliability reports (64.88%); 557 of 901 full-sample reports (61.82%).
- Incorrect result: 85 of 447 reliability reports (19.02%); 207 of 901 full-sample reports (22.97%).
- Partial completion: 72 of 447 reliability reports (16.11%); 137 of 901 full-sample reports (15.21%).

### User observability

- Directly apparent: 317 of 447 reliability reports (70.92%); 608 of 901 full-sample reports (67.48%).
- Requires additional verification: 130 of 447 reliability reports (29.08%); 293 of 901 full-sample reports (32.52%).

## Kappa

- Task impact：0.833302。
- User observability：0.867083。
- This pilot annotation is supplementary; no additional paired inputs from two rounds were created. The original pre-discussion inputs for 447 reports are unchanged, so Kappa is unchanged.

## Files

- Pilot_Attribute_Labels.csv: labels, evidence, rationales, and inference flags for the 454 added reports.
- 13_Full_Sample_New_Attribute_Labels_901.csv: per-report labels for the combined 901 reports.
- Category_New_Attribute_Counts_and_Percentages_Full_Sample.csv: complete category–attribute distributions.
- Results_Before_and_After_Pilot_Supplement.csv: original values, full-sample counts, percentages, and effects on primary labels for the 86 comparisons.
