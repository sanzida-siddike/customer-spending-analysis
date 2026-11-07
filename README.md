# Customer Spending Analysis (Python)

An exploratory data analysis and statistics project on 2,240 customers of a retail company. The goal was to find out **what makes some customers spend much more than others**, check whether those differences are statistically significant, and build a model to predict spending.

## Data

- **Source:** based on the [Customer Personality Analysis](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis) dataset from Kaggle
- **Rows:** 2,240 customers (2,208 after cleaning)
- **Columns used:** birth year, education, marital status, income, kids and teens at home, days since last purchase, and spending on wine, fruit, meat, fish, sweets and gold

## Tools

Python, pandas, NumPy, matplotlib, seaborn, SciPy, scikit-learn, Jupyter Notebook

## Files

| File | Description |
|---|---|
| `Customer_Spending_Analysis.ipynb` | Full analysis with code, charts and explanations |
| `campaignData.csv` | The dataset |
| `README.md` | Project summary |

## What I did

1. **Cleaning:** removed impossible birth years (1893, 1899, 1900), one extreme income (666,666), 24 rows with missing income, and meaningless marital status values ("YOLO", "Absurd").
2. **Feature engineering:** created Age, TotalSpent, LivesAlone, Children, FamilySize, IsParent and EducationLevel.
3. **Exploratory analysis:** 8 charts on spending distribution, products, income, children, age, education and correlations.
4. **Statistical tests:** Pearson/Spearman correlation, Welch's t-test, Mann-Whitney U test and chi-square test.
5. **Modelling:** compared Linear Regression, SGD Regressor and Random Forest using R², MAE and RMSE.

## Key findings

**1. Income is the strongest driver of spending.** Correlation between income and total spending is 0.79 (p < 0.001), and income makes up about 90% of the Random Forest's feature importance.

**2. Customers without children spend about 2.7 times more.**

| Group | Customers | Average spending |
|---|---|---|
| No children | 630 | $1,104 |
| Parents | 1,578 | $409 |

The difference is significant (Welch's t-test and Mann-Whitney U, both p < 0.001). 79% of non-parents are above-median spenders, compared with 38% of parents (chi-square p < 0.001).

**3. Wine and meat are about 78% of all spending** (wine 50.3%, meat 27.5%). Fruits and sweets are under 5% each.

**4. Education level and living alone make no real difference.** Postgraduate customers spend $618 on average and undergraduates $597 (t-test p = 0.40).

**5. Spending is right-skewed.** The median customer spends $396, while the mean is $607, so a smaller group of big spenders brings in a large share of revenue.

**6. Random Forest predicts spending best.**

| Model | R² | MAE |
|---|---|---|
| Linear Regression | 0.66 | $262 |
| SGD Regressor | 0.66 | $262 |
| Random Forest | 0.76 | $213 |

## Recommendations

- Target **high-income customers without children** with premium wine and meat promotions.
- Offer **family bundles and everyday discounts** to parents, whose spending is much lower.
- **Don't segment by education level**, since it doesn't change spending.
- Start a **loyalty program for top spenders**, because a small group brings a large share of revenue.

## Limitations

- No purchase dates, so trends over time can't be studied.
- Age uses 2014 as the reference year, when the original data was collected.
- The results show relationships, not cause and effect. Parents may spend less partly because of lower income, not only because of children.

---

**Sanzida Siddike**
