# econ5200-lab04-outlier-pipeline

# Outlier Detection on California Housing

## Objective
I compared three outlier detection methods on the California Housing data to decide which one a policy team should use before modeling.

## Methodology
- Found and fixed three bugs in a broken outlier-detection pipeline. The modified Z-score used the mean and standard deviation instead of the median and MAD, the Tukey fence used the wrong multiplier, and Isolation Forest was set to flag far too many rows.
- Used an OutlierDetector class that offers the modified Z-score, Tukey fences and Isolation Forest, checks its settings when it is created, and reports a summary of what it flagged.
- Ran the modified Z-score and Tukey fences on MedInc, and Isolation Forest on all 9 columns.
- Compared which rows each method flagged using a Venn diagram.
- Wrote a method-selection memo for a policy team allocating housing funds.
- Built an interactive outlier method explorer with a column dropdown and sliders for each method's setting. It shows how many rows each method flags and lets me look through the flagged rows.

## Key Findings
- The modified Z-score on MedInc flagged 400 rows, Tukey on MedInc flagged 681, and Isolation Forest on all 9 columns flagged 1032.
- All three methods agreed on 322 rows.
- Every row the modified Z-score flagged was also flagged by Tukey.
- The methods disagree because they look at different things. The Z-score and Tukey only see income, while Isolation Forest looks at all the columns together and picks up unusual combinations.
- My memo recommends Isolation Forest on all columns as the main method, with a Tukey fence on income as a check.
- A flagged row is not automatically an error. For funding decisions, extreme values can be real, so I would review flagged rows and only remove clear errors.
