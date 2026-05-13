# Lifestyle Factors and Academic Productivity: A Self-Tracking Longitudinal Analysis

## Motivation

As an international student, managing academic performance alongside lifestyle demands such as sleep, stress, and study habits presents a unique challenge. Social and behavioral factors do not affect all students equally — adaptation to a new environment, language barriers, and shifting motivation levels may all play a role in shaping academic outcomes over the course of a semester.

While self-tracking studies of this nature are not uncommon in the broader literature, this project holds particular personal significance. The research question was chosen not for its novelty but for its direct relevance to the author's own experience — the data reflect a real semester, real exam pressures, and real behavioral patterns. It is this personal grounding that motivates the careful application of data science methods to a problem that is, above all, meaningful to the researcher.

This project investigates whether and how lifestyle and adaptation factors influence weekly academic productivity throughout a semester. Rather than relying on an external dataset, data were collected personally through weekly self-tracking, making this a longitudinal single-subject study grounded in lived experience. The analysis applies the full data science pipeline — exploratory analysis, hypothesis testing, and machine learning — to understand which behavioral variables matter most and whether they can be used to predict academic outcomes.

## Datasets and Data Enrichment

The primary dataset consists of weekly self-tracked observations recorded over ten weeks of the Spring 2026 semester, from late February through early May. Each observation captures behavioral and academic variables for a single week, including total study hours, average hours of sleep per night, self-rated stress level, self-rated motivation, perceived difficulty with English-language coursework, and a composite productivity score derived from exam performance and assignment completion.

Data enrichment is achieved by incorporating the official academic calendar to classify each week as either a regular week or a midterm week. Weeks 7 and 8, which contained examinations on April 5, 6, and 19, are classified as midterm weeks. This classification introduces a structured contextual variable that enables direct comparison of behavioral patterns under different levels of academic pressure and constitutes the external data source required by the project guidelines.

## Final Dataset

After data collection and cleaning, the dataset comprises ten weekly observations with no missing values. Eight weeks are classified as regular and two as midterm. Key descriptive statistics reveal that the average productivity score across the semester was 52.40 percent, with a standard deviation of 4.84 points. Study hours averaged 12.70 per week, driven upward by exam weeks in which study time reached approximately 25 hours. Average sleep was 6.88 hours per night, stress averaged 6.00 on a ten-point scale, and motivation averaged 3.10, reflecting a consistently low motivational state throughout the semester.

## Hypothesis Testing

The hypothesis testing component evaluates whether lifestyle and adaptation factors are statistically associated with weekly academic productivity.

Five hypotheses are defined. The first posits that increased study hours improve productivity. The second posits that more sleep improves productivity. The third posits that higher stress lowers productivity. The fourth posits that productivity differs significantly between midterm and regular weeks. The fifth posits that higher motivation is associated with higher productivity.

Pearson correlation tests are applied for continuous relationships, an independent samples t-test is used to compare productivity across week types, and a Spearman correlation is used for motivation given its ordinal nature.

All five hypotheses are statistically significant at the five percent level. Stress level shows the strongest negative correlation with productivity (r = −0.96, p < 0.001), followed by language difficulty (r = −0.86, p = 0.001) and sleep as a positive predictor (r = +0.88, p = 0.001). The comparison between week types yields a t-statistic of 4.79 (p = 0.001), with regular weeks averaging 54.38 percent compared to 44.50 percent during midterm weeks. Motivation shows a significant positive association (ρ = 0.74, p = 0.015).

An unexpected finding concerns study hours, which are significantly negatively correlated with productivity (r = −0.85, p = 0.002). This result is explained by the exam-week confounding effect: study hours spike to approximately 25 hours during midterm weeks precisely when productivity is at its lowest, driven by concurrent stress elevation and sleep reduction. This finding illustrates the diminishing returns of additional study effort under conditions of high stress and poor sleep, and constitutes a substantive insight in its own right.

## Machine Learning Models

To complement the hypothesis testing, machine learning models are applied to assess whether behavioral variables can predict weekly productivity scores and the direction of weekly change.

In the regression stage, five models are evaluated using Leave-One-Out Cross-Validation, which is appropriate given the small sample size of ten observations. Linear Regression achieves the best performance with an RMSE of 1.231 and an R-squared of 0.928, indicating that behavioral variables collectively explain approximately 93 percent of the variance in weekly productivity. Ridge and Lasso regression perform similarly, while ensemble methods — Gradient Boosting and Random Forest — perform substantially worse, confirming that simpler models generalize better with limited data.

Feature importance analysis using the Random Forest regressor identifies stress level as the dominant predictor with an importance score of 0.329, followed by language difficulty (0.167), study hours (0.147), sleep average (0.139), motivation level (0.110), and the midterm indicator (0.108). This ordering is consistent with the correlation and hypothesis testing results.

In the classification stage, three models are used to predict whether productivity increases week-over-week. Logistic Regression achieves an accuracy of 60 percent, above the 50 percent random baseline, while Random Forest and Gradient Boosting achieve 40 and 30 percent respectively. The confusion matrix for Logistic Regression reveals that the model correctly identifies six out of seven decreasing weeks but fails to correctly predict any of the three increasing weeks, reflecting the class imbalance in the dataset.

## Results

Across all methods, the results consistently indicate that behavioral and contextual factors are meaningfully associated with weekly academic productivity. Stress is the single most influential variable, both statistically and in terms of predictive importance. Midterm weeks produce a significant and substantial drop in productivity despite higher study effort, a pattern that persists across both statistical tests and machine learning predictions. Sleep and motivation are meaningful secondary predictors, while language difficulty — reflecting the additional cognitive burden of studying in a second language — emerges as a stronger predictor than expected.

The regression models achieve strong predictive performance for a self-tracking single-subject study, though the small sample size limits the generalizability of these findings.

## Summary

This project demonstrates that weekly academic productivity is not determined by study effort alone but is shaped by a combination of behavioral, psychological, and contextual factors. Stress level stands out as the primary driver of productivity variation, with sleep and motivation playing supporting roles. The integration of the academic calendar as an enrichment variable enables a structured comparison that reveals how exam periods disrupt the behavioral patterns established during regular weeks.

The combination of exploratory analysis, hypothesis testing, and machine learning provides a complementary and internally consistent account of the factors influencing individual academic performance over a semester.

An interactive project webpage summarising the key findings and results is available at: https://mzeingabul.github.io/DSA210-MirasZeingabul36112/

## Limitations and Future Work

Several limitations should be acknowledged. The dataset comprises only ten observations from a single subject, which substantially limits statistical power and prevents generalization beyond this individual case. All behavioral variables are self-reported and subject to recall and rating biases. The productivity score is an approximation based on estimated exam grades and subjective assessment of assignment completion rather than verified institutional records. Furthermore, with only two midterm weeks, the group comparison carries limited statistical power despite achieving significance.

Future research could extend data collection to a full semester of fourteen or more weeks, incorporate comparison data from other students to enable cross-group analysis, and use verified grade records for a more precise productivity measure. Applying time-series methods that account for the sequential structure of weekly data, and including additional variables such as physical activity or social engagement, would further enrich the analysis.

## Usage of AI Tools

AI tools, including Claude (Anthropic), were used to assist with code generation, notebook structure, and language refinement throughout the project. All analytical decisions, modeling choices, data collection, and interpretations remain the responsibility of the author. AI usage is disclosed in accordance with DSA 210 academic integrity policy.
