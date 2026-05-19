# 🌊 Seaborn Complete Guide

![Python](https://img.shields.io/badge/Python-3.7%2B-blue?style=flat-square&logo=python)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12%2B-teal?style=flat-square)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square&logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

> A comprehensive, hands-on guide to **Seaborn** — Python's elegant statistical data visualization library. Covers everything from basics to advanced multi-plot grids, all in interactive Jupyter Notebooks.

---

## 📁 Repository Structure

```
seaborn-complete-guide/
│
├── 📓 notebooks/
│   ├── 01_basics.ipynb
│   ├── 02_relational_plots.ipynb
│   ├── 03_distribution_plots.ipynb
│   ├── 04_categorical_plots.ipynb
│   ├── 05_regression_plots.ipynb
│   ├── 06_matrix_plots.ipynb
│   └── 07_multi_plots.ipynb
│
├── 📊 datasets/
│   └── (Uses built-in Seaborn datasets)
│
├── requirements.txt
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

```bash
Python >= 3.7
```

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/seaborn-complete-guide.git
cd seaborn-complete-guide

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter Notebook
jupyter notebook
```

### `requirements.txt`

```
seaborn>=0.12.0
matplotlib>=3.5.0
pandas>=1.4.0
numpy>=1.22.0
scipy>=1.8.0
jupyter>=1.0.0
notebook>=6.4.0
```

---

## 📚 Notebooks Overview

---

### 1️⃣ `01_basics.ipynb` — Seaborn Basics

> **Get started with Seaborn — setup, themes, and your first plots.**

| Topic | Description |
|-------|-------------|
| 🔧 Setup | Import seaborn, matplotlib, pandas |
| 🎨 Themes | `set_theme()`, `set_style()`, `set_palette()` |
| 📦 Datasets | Loading built-in datasets (`tips`, `iris`, `titanic`) |
| 🖼️ First Plot | Simple `sns.scatterplot()` and `sns.lineplot()` |
| 🎭 Figure Aesthetics | Contexts: `paper`, `notebook`, `talk`, `poster` |

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.set_theme(style="darkgrid", palette="muted")

tips = sns.load_dataset("tips")
sns.scatterplot(data=tips, x="total_bill", y="tip", hue="sex")
plt.title("Tips vs Total Bill")
plt.show()
```

---

### 2️⃣ `02_relational_plots.ipynb` — Relational Plots

> **Visualize relationships between two or more numeric variables.**

| Plot | Function | Use Case |
|------|----------|----------|
| Scatter Plot | `sns.scatterplot()` | Relationship between two variables |
| Line Plot | `sns.lineplot()` | Trends over time or ordered data |
| Relplot | `sns.relplot()` | Figure-level scatter/line with facets |

```python
# Scatter with hue, size, and style
sns.scatterplot(
    data=tips, x="total_bill", y="tip",
    hue="day", size="size", style="sex"
)

# Line plot with confidence interval
fmri = sns.load_dataset("fmri")
sns.lineplot(data=fmri, x="timepoint", y="signal",
             hue="region", style="event")
```

**Key Concepts Covered:**
- `hue`, `size`, `style` semantic mapping
- Aggregation with confidence intervals
- Faceting with `col` and `row` in `relplot()`

---

### 3️⃣ `03_distribution_plots.ipynb` — Distribution Plots

> **Understand the distribution of your data — univariate and bivariate.**

| Plot | Function | Use Case |
|------|----------|----------|
| Histogram | `sns.histplot()` | Frequency distribution |
| KDE Plot | `sns.kdeplot()` | Smooth density estimate |
| ECDF Plot | `sns.ecdfplot()` | Cumulative distribution |
| Rug Plot | `sns.rugplot()` | Show individual observations |
| Displot | `sns.displot()` | Figure-level distribution grid |

```python
# Histogram with KDE overlay
sns.histplot(data=tips, x="total_bill", kde=True, color="teal")

# Bivariate KDE
sns.kdeplot(data=tips, x="total_bill", y="tip",
            fill=True, cmap="Blues")

# Distribution comparison
sns.displot(data=tips, x="total_bill", hue="sex",
            kind="kde", fill=True)
```

**Key Concepts Covered:**
- Univariate vs bivariate distributions
- Bin width and bandwidth selection
- Overlaying multiple distributions

---

### 4️⃣ `04_categorical_plots.ipynb` — Categorical Plots

> **Visualize how a numeric variable varies across categories.**

| Plot | Function | Use Case |
|------|----------|----------|
| Bar Plot | `sns.barplot()` | Mean with CI per category |
| Count Plot | `sns.countplot()` | Count of observations |
| Box Plot | `sns.boxplot()` | Quartiles and outliers |
| Violin Plot | `sns.violinplot()` | Distribution shape per category |
| Strip Plot | `sns.stripplot()` | All individual data points |
| Swarm Plot | `sns.swarmplot()` | Non-overlapping points |
| Point Plot | `sns.pointplot()` | Mean estimates with CI |
| Catplot | `sns.catplot()` | Figure-level categorical grid |

```python
# Box plot with hue
sns.boxplot(data=tips, x="day", y="total_bill", hue="sex")

# Violin plot
sns.violinplot(data=tips, x="day", y="tip",
               inner="quart", palette="pastel")

# Combined strip + box
fig, ax = plt.subplots()
sns.boxplot(data=tips, x="day", y="total_bill", ax=ax)
sns.stripplot(data=tips, x="day", y="total_bill",
              color=".3", ax=ax)
```

**Key Concepts Covered:**
- Choosing the right categorical plot
- Combining multiple plot types
- Ordering categories

---

### 5️⃣ `05_regression_plots.ipynb` — Regression Plots

> **Explore linear relationships and model fits in your data.**

| Plot | Function | Use Case |
|------|----------|----------|
| Reg Plot | `sns.regplot()` | Scatter + linear regression line |
| LM Plot | `sns.lmplot()` | Figure-level regplot with facets |
| Residual Plot | `sns.residplot()` | Residuals of a regression fit |

```python
# Simple linear regression
sns.regplot(data=tips, x="total_bill", y="tip",
            scatter_kws={"alpha": 0.5})

# Regression by group with facets
sns.lmplot(data=tips, x="total_bill", y="tip",
           hue="smoker", col="time",
           height=5, aspect=0.8)

# Polynomial regression (order=2)
sns.regplot(data=tips, x="total_bill", y="tip", order=2)

# Logistic regression
titanic = sns.load_dataset("titanic")
sns.regplot(data=titanic, x="age", y="survived",
            logistic=True, y_jitter=0.03)
```

**Key Concepts Covered:**
- Confidence interval bands
- Polynomial and logistic regression
- Residual diagnostics
- Faceted regression across groups

---

### 6️⃣ `06_matrix_plots.ipynb` — Matrix Plots

> **Visualize matrix-form data — correlations, hierarchies, and grids.**

| Plot | Function | Use Case |
|------|----------|----------|
| Heatmap | `sns.heatmap()` | Correlation/confusion matrices |
| Clustermap | `sns.clustermap()` | Hierarchically clustered heatmap |

```python
# Correlation heatmap
import pandas as pd

corr = tips.select_dtypes("number").corr()
sns.heatmap(corr, annot=True, fmt=".2f",
            cmap="coolwarm", linewidths=0.5,
            vmin=-1, vmax=1)

# Clustered heatmap
flights = sns.load_dataset("flights")
flights_pivot = flights.pivot("month", "year", "passengers")
sns.clustermap(flights_pivot, cmap="YlOrRd",
               figsize=(10, 8), standard_scale=1)
```

**Key Concepts Covered:**
- Annotating cells with values
- Color map selection
- Hierarchical clustering in clustermap
- Masking the upper triangle of a matrix

---

### 7️⃣ `07_multi_plots.ipynb` — Multi-Plots (Grid Plots)

> **Combine multiple plots into powerful grid layouts for deeper exploration.**

| Plot | Function | Use Case |
|------|----------|----------|
| Pair Plot | `sns.pairplot()` | All pairwise relationships |
| Pair Grid | `sns.PairGrid()` | Custom pairwise grid |
| Facet Grid | `sns.FacetGrid()` | Conditional small multiples |
| Joint Plot | `sns.jointplot()` | Bivariate + marginal distributions |

```python
# Pair plot
iris = sns.load_dataset("iris")
sns.pairplot(iris, hue="species", diag_kind="kde",
             plot_kws={"alpha": 0.6})

# Custom PairGrid
g = sns.PairGrid(iris, hue="species")
g.map_upper(sns.scatterplot)
g.map_lower(sns.kdeplot)
g.map_diag(sns.histplot)
g.add_legend()

# FacetGrid — custom faceted plots
g = sns.FacetGrid(tips, col="time", row="sex", height=4)
g.map_dataframe(sns.scatterplot, x="total_bill", y="tip")
g.add_legend()

# Joint plot
sns.jointplot(data=tips, x="total_bill", y="tip",
              kind="reg", height=7)
```

**Key Concepts Covered:**
- `map_upper()`, `map_lower()`, `map_diag()` in PairGrid
- `map_dataframe()` in FacetGrid
- Joint plot kinds: `scatter`, `kde`, `hist`, `hex`, `reg`, `resid`
- Combining figure-level and axes-level plots

---

## 🎨 Seaborn Themes & Palettes Cheatsheet

```python
# Styles
sns.set_style("whitegrid")   # white background, grid lines
sns.set_style("darkgrid")    # dark background, grid lines
sns.set_style("white")       # white background, no grid
sns.set_style("dark")        # dark background, no grid
sns.set_style("ticks")       # white background, tick marks

# Contexts
sns.set_context("paper")     # smallest
sns.set_context("notebook")  # default
sns.set_context("talk")      # for presentations
sns.set_context("poster")    # largest

# Palettes
sns.color_palette("deep")
sns.color_palette("muted")
sns.color_palette("pastel")
sns.color_palette("bright")
sns.color_palette("dark")
sns.color_palette("colorblind")
```

---

## 🗂️ Built-in Datasets Used

| Dataset | Description |
|---------|-------------|
| `tips` | Restaurant tips data |
| `iris` | Iris flower measurements |
| `titanic` | Titanic passenger survival |
| `fmri` | Brain imaging signals |
| `flights` | Monthly airline passengers |
| `penguins` | Palmer penguins measurements |
| `diamonds` | Diamond pricing data |

Load any dataset with:
```python
df = sns.load_dataset("dataset_name")
```

---

## 🧭 Which Plot Should I Use?

```
Your Data
│
├── Numeric only?
│   ├── 1 variable  → histplot, kdeplot, ecdfplot
│   └── 2 variables → scatterplot, lineplot, jointplot
│
├── Numeric + Categorical?
│   ├── Summarize   → barplot, pointplot
│   ├── Distribution→ boxplot, violinplot
│   └── Raw data    → stripplot, swarmplot
│
├── Regression?
│   └── regplot, lmplot, residplot
│
├── Matrix data?
│   └── heatmap, clustermap
│
└── Everything at once?
    └── pairplot, PairGrid, FacetGrid
```

---

## 📖 Resources

- 📘 [Official Seaborn Documentation](https://seaborn.pydata.org/)
- 📗 [Seaborn Tutorial](https://seaborn.pydata.org/tutorial.html)
- 📙 [Seaborn API Reference](https://seaborn.pydata.org/api.html)
- 📊 [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)
- 🐍 [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/add-new-plot`
3. Commit your changes: `git commit -m 'Add advanced violin plot examples'`
4. Push to the branch: `git push origin feature/add-new-plot`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---
