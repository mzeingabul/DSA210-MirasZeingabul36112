# Lifestyle Factors and Academic Productivity: A Self-Tracking Longitudinal Analysis

**Project webpage:** https://mzeingabul.github.io/DSA210-MirasZeingabul36112/

---

## 1. Motivation

As an international student, managing academic performance alongside lifestyle demands such as sleep, stress, and study habits presents a unique challenge. Social and behavioral factors do not affect all students equally — adaptation to a new environment, language barriers, and shifting motivation levels may all play a role in shaping academic outcomes over the course of a semester.

While self-tracking studies of this nature are not uncommon in the broader literature, this project holds particular personal significance. The research question was chosen not for its novelty but for its direct relevance to the author's own experience — the data reflect a real semester, real exam pressures, and real behavioral patterns. It is this personal grounding that motivates the careful application of data science methods to a problem that is, above all, meaningful to the researcher.

This project investigates whether and how lifestyle and adaptation factors — study hours, sleep duration, stress level, motivation, and language difficulty — significantly influence weekly academic productivity. Data is collected personally each week through self-tracking, making this a longitudinal single-subject study. The academic calendar is used as an external data source to enrich the dataset by classifying weeks according to academic pressure level (regular vs. midterm periods), enabling behavioral comparisons across different phases of the semester.

---

## 2. Research Questions

**Main Question**
- Do lifestyle and adaptation factors significantly influence academic productivity during the semester?

**Sub-Questions**
1. Which behavioral factors are most strongly correlated with weekly productivity?
2. Does academic productivity differ significantly between regular and midterm weeks?
3. Can lifestyle variables predict academic productivity using machine learning models?

---

## 3. Hypotheses

| # | Hypothesis | Test | Result |
|---|---|---|---|
| H1 | Increased study hours improve productivity | Pearson r | Significant (r=-0.85, p=0.002) — negative due to exam confounding |
| H2 | More sleep improves productivity | Pearson r | Significant (r=+0.88, p=0.001) ✓ |
| H3 | Higher stress lowers productivity | Pearson r | Significant (r=-0.96, p<0.001) ✓ |
| H4 | Productivity differs by week type | t-test | Significant (t=4.79, p=0.001) ✓ |
| H5 | Higher motivation improves productivity | Spearman rho | Significant (rho=0.74, p=0.015) ✓ |

**All 5 hypotheses were statistically significant.**

---

## 4. Data Description

| Dataset | Variables | Purpose |
|---|---|---|
| **Self-tracked weekly log** (`dataset.csv`) | Study hours, sleep, stress, motivation, language difficulty, productivity score | Main dataset: behavioral and academic variables recorded weekly |
| **Academic calendar** (external) | Week classification: regular / midterm | Enrichment: classifies weeks by academic pressure level |

### Variables

| Variable | Type | Description |
|---|---|---|
| `week` | int | Week number (1–10) |
| `week_type` | str | regular / midterm |
| `study_hours` | float | Total hours studied that week |
| `sleep_avg` | float | Average hours of sleep per night |
| `stress_level` | int | Self-rated stress (1=low, 10=high) |
| `motivation_level` | int | Self-rated motivation (1=low, 10=high) |
| `language_difficulty` | int | Self-rated language difficulty (1=low, 10=high) |
| `productivity_score` | float | Composite academic outcome (%) |

---

## 5. Key Results

### EDA
- Productivity drops from ~54–58% in regular weeks to ~43–46% during midterm weeks
- Stress level has the strongest correlation with productivity (r = -0.96)
- Sleep positively correlates with productivity (r = +0.88)

### Machine Learning

**Regression (predict productivity score):**

| Model | RMSE | R² |
|---|---|---|
| **Linear Regression** | **1.231** | **0.928** |
| Ridge | 1.341 | 0.915 |
| Lasso | 1.348 | 0.914 |
| Gradient Boosting | 2.032 | 0.804 |
| Random Forest | 2.048 | 0.801 |

**Classification (predict productivity direction):**

| Model | Accuracy |
|---|---|
| **Logistic Regression** | **60%** |
| Random Forest | 40% |
| Gradient Boosting | 30% |

**Top feature:** `stress_level` (importance = 0.329)

---

## 6. Repository Structure

```
DSA210/
├── data/
│   └── dataset.csv
├── notebooks/
│   ├── 02_eda.ipynb
│   └── 03_ml_models.ipynb
├── figures/
│   ├── productivity_over_time.png
│   ├── productivity_by_week_type.png
│   ├── correlation_heatmap.png
│   ├── scatter_predictors.png
│   ├── regression_model_comparison.png
│   ├── pred_vs_actual.png
│   ├── feature_importance.png
│   ├── classification_accuracy.png
│   └── confusion_matrix.png
├── report.md
├── requirements.txt
└── README.md
```

---

## 7. Project Status

| Milestone | Deadline | Status |
|---|---|---|
| GitHub repo created | 17 March | ✅ Done |
| Project proposal submitted | 31 March | ✅ Done |
| Data collection, EDA & hypothesis testing | 14 April | ✅ Done |
| ML methods | 5 May | ✅ Done |
| Final report & code submission | 18 May | ✅ Done |

---

## 8. How to Reproduce

1. Clone the repository
```bash
git clone https://github.com/mzeingabul/DSA210-MirasZeingabul36112.git
```
2. Install dependencies
```bash
pip install -r requirements.txt
```
3. Open notebooks in Google Colab
   - Go to [colab.research.google.com](https://colab.research.google.com)
   - Upload `notebooks/02_eda.ipynb` → Runtime → Run all
   - Upload `notebooks/03_ml_models.ipynb` → Runtime → Run all

---

## 9. Tools & Libraries

- Python 3.x
- pandas, numpy, matplotlib, seaborn
- scipy (hypothesis testing)
- scikit-learn (machine learning)

---

## 10. Academic Integrity

Use of Claude (Anthropic) as an AI assistant is documented as required by course policy — used to help structure the analysis pipeline and generate initial code. All data collection, interpretations, and conclusions are the student's own work.
