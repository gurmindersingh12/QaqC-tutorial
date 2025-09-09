
* * * 
* * * 
### Welcome to the **QaqC Dashboard** - your one-stop tool for validating, cleaning, and exploring phenotypic datasets before statistical analysis. This tutorial will walk you through each step of the app with detailed instructions and visual guides.
* * * 
* * * 


## ----------------------------------- Step 1: Upload the Dataset ---------------------------------
---

This is where everything starts. You’ll load your phenotypic CSV file into the app, preview the data, and check for basic issues like missing values or duplicates.


**📥 Purpose:**
   * This is where everything starts. You’ll load your phenotypic CSV file into the app, preview the data, and check for basic issues like missing values or duplicates.

**🎯 What You Can Do:**

 * Upload your `.csv` file.
 * View a Raw Data Preview table.
 * Detect and remove missing values.
 * Detect and remove duplicate rows based on selected columns.

**🖱️ How to Use:** 

---

   **1.** Click “Browse…” to upload your `.csv` file. Make sure the file has column headers in the first row.
            
---
   **2.** After loading, the dataset preview appears on the right side under Raw Data Preview.

  ![upload the csv file](assets/Step-01.gif)
 ---
      
   **3.** Click “Find Missing Values” to highlight any missing entries (NA or blank).

  ![find missing in csv file](assets/Step-02.gif)
---
      
   **4.** To check for duplicates: Select which column(s) to check, Click “Find Duplicates”, and You can then choose to Remove Duplicates if needed.

  ![duplicates](assets/Step-03.gif)
---

   **5.** Reset Data will clear your current session and allow re-upload.

  ![reset the file upload](assets/Step-04.gif)
---

**🧠 Tip:**

   * All downstream analyses (summary stats, visualizations, model residuals) use the cleaned dataset, so this step is critical for ensuring high-quality input.



* * * 
* * *
* * * 
* * *


## ----------------------------------- Step 2: Column Summary Tab -----------------------------------
---
---

**🔍 Purpose:** 
Get descriptive statistics for any numeric column — a fast way to assess data spread, potential outliers, and normality.

**🎯 What You Can Do:** 
  * Select any numeric trait from the dropdown.
  * View detailed statistics:
      * Missing count
      * Zero count
      * Min, Max
      * Quartiles (Q1, Median, Q3)
      * Mean, SD, CV%
      * Skewness & Kurtosis

**🖱️ How to Use:**

  1. Choose a trait/column from the “Select Column to Summarize” dropdown.
  2. The Summary Statistics table will update instantly.
  3. Click “Show Definitions” to view explanations of each metric.

**📘 Metric Definitions (examples):**

  * CV (%): Coefficient of Variation. Helps compare variation across traits with different units.
  * Skewness: Indicates asymmetry of the distribution.
  * Kurtosis: Measures tail heaviness. >0 = heavier tails.



   ![column summary](assets/Step-05.gif)
      


* * * 
* * *
* * * 
* * *


## -------------------------------- 🚦 Step 3: Visualize & Detect Outliers --------------------------------

This step includes three tabs — Histogram, Boxplot, and Studentized Residual Plot — that help detect and visualize unusual patterns or outlier values.
* * *

## 📉 Tab 1: Histogram

**🎯 What You Can Do:**

  * Visualize frequency distribution of a numeric trait.
  * Adjust bin size and color.
  * Flag outliers using Standard Deviation thresholds.
  * Download plots or filtered data.

**🖱️ How to Use:**

  1. Select a trait.
  2. Optionally enable "Flag SD-based Outliers" and set bin size (if needed).
  3. Compare Raw vs Filtered histograms.
      * Filtered histogram excludes flagged outliers.
  4. Below the plots, see a summary table of outlier rows.
  5. Use the download buttons to save:
      * Raw Plot, Filtered Plot, or Filtered CSV.

   ![histogram](assets/Step-06.gif)

---

## 📦 Tab 2: Boxplot

**🎯 What You Can Do:**

  * Identify outliers using IQR-based method.
  * Customize box fill and point color.
  * Adjust jitter for dot spacing.

**🖱️ How to Use:**

  1. Select a trait.
  2. Optionally enable "Flag IQR-based Outliers".
  3. Compare Raw vs Filtered boxplots.
  4. Below the plots, see a summary table of outlier rows.
  5. Customize plot aesthetics if desired.
  6. Download plots and cleaned data.

   ![boxplot](assets/Step-07.gif)

---

## 📈 Tab 3: Studentized Residual Plot

**🎯 What You Can Do:**

  * Detect outliers using a linear model.
  * Plot studentized residuals against fitted values.
  * Flag residuals exceeding ±4 threshold.
  * View and export a table of detected outliers.

**🖱️ How to Use:**

  1. Choose a Response Variable (e.g., yield).
  2. Select Predictors (e.g., plot, block, entry).
  3. Set a threshold (default = 4).
  4. View the Raw vs Filtered studentized residual plots.
       * Red dots = outliers
  5. Below the plots, see a summary table of outlier rows.
  6. Export plot or cleaned dataset.

   ![st residual plot](assets/Step-08.gif)

* * * 
* * *
* * *
* * *


## -------------------------------- Step 4: Pairwise & Overall Relationships --------------------------------



#### Once individual traits are cleaned, the next step is to explore relationships between traits. This is crucial for detecting hidden correlations, multicollinearity, or unexpected trends.

* * *


#### We use two tabs here: Scatter Plot (pairwise) and Correlation Heatmap (overall).

**🔹 Tab 1: Scatter Plot**

**🎯 What You Can Do:**

  * Plot a response variable against a predictor variable.
  * Add a linear regression line or correlation ellipse.
  * Flag and filter outliers if needed.
  * Display model statistics below the plot:
      * Equation of best-fit line
      * _R²_ (coefficient of determination)
      * _p_-value (significance of relationship)
      * Pearson’s correlation (strength & direction of association)

**🖱️ How to Use:**

  1. From the left panel, select a Response Variable (e.g., yield).
  2. Select a Predictor Variable (e.g., plot).
  3. (Optional) Check “Add Linear Model” to overlay a regression line.
  4. (Optional) Add a Correlation Ellipse to visualize spread.
  5. Compare Raw vs Filtered scatterplots.
  6. Review model results under each plot.

**📘 Interpretation Example:**

 * If _R²_ = 0.01 → very weak relationship.
 * If Pearson’s _r_ = 0.75 → strong positive correlation.
 * _p_-value < 0.05 → relationship is statistically significant.


![scatter plot](assets/Step-09.gif)

* * * 
* * *

**🔹 Tab 2: Correlation Heatmap**

**🎯 What You Can Do:**

  * View overall pairwise correlation between multiple traits.
  * Choose correlation method (Pearson, Spearman, Kendall).
  * Apply outlier filtering (e.g., SD-based).
  * Compare Raw vs Filtered heatmaps.
  * Export plots and datasets.

**🖱️ How to Use:**

  1. Select multiple variables in the Select Variables panel.
  2. Choose a correlation method:
       * Pearson: linear correlations
       * Spearman: rank-based correlations
       * Kendall: concordance between ranks

  3. (Optional) Enable outlier detection with SD threshold.
  4. Compare Raw vs Filtered heatmaps.
  5. Hover over heatmap cells to see exact correlation values.
  6. Download as plot or filtered dataset.

**📘 Interpretation Example:**

  * Correlation values range from -1 (perfect negative) to +1 (perfect positive).
  * Strong correlations (e.g., >0.7 or < -0.7) may indicate redundancy.
  * Negative correlations could point to trade-offs (e.g., yield vs lodging).

![heatmap](assets/Step-10.gif)

* * * 
* * *
* * * 
* * *

## ------------------------------📑 Step 5: QA/QC Report ------------------------------

This is the final step — it brings everything together into a downloadable report.

**🎯 What You Can Do:**

  * Mirror results from selected tabs (Column Summary, Histogram, Boxplot, Residuals, Scatter, Correlation).
  * Automatically generate a comprehensive report.
  * Download in HTML format for interactivity, sharing or archiving.

**🖱️ How to Use:**

  1. In the Mirror Settings panel, check which sections you want to include.
       * Example: Histogram + Boxplot + Residuals.
  2. The report preview updates live under Everything currently visible across tabs.
  3. Click `Download HTML` to export the full report.

**📘 Why It Matters:**

  * Provides a transparent record of your QA/QC workflow.
  * Ensures consistency — same steps can be shared across collaborators.
  * Saves time by documenting analyses automatically.

![qaqc report](assets/Step-11.gif)

* * * 
* * *
* * * 
* * *

## ------------------------------ 🎉 Wrapping Up ------------------------------

**Congratulations — you’ve just completed the QaqC Dashboard tutorial! 🚀**

By now, you should be able to:

  * Upload and clean phenotypic datasets.
  * Summarize traits with descriptive statistics.
  * Detect and filter outliers using multiple methods (Histogram, Boxplot, Studentized Residuals).
  * Explore pairwise and overall trait relationships (Scatter Plots and Correlation Heatmaps).
  * Generate a QA/QC Report to document your workflow and share with collaborators.

**💡 Why This Matters**

Every cleaned dataset you generate through QaqC is more:

  * **Reliable** — errors and anomalies are caught early.
  * **Reproducible** — every step is documented transparently.
  * **Decision-ready** — enabling confident downstream analysis and interpretation.

**🚀 Next Steps**

  * Use your cleaned dataset in statistical models, GWAS, or genomic prediction.
  * Share your QA/QC report with your advisor, labmates, or collaborators.
  * Explore how different outlier detection methods change your results.

## ------------------------------📬 Support & Contact ------------------------------ 

#### If you run into issues while using the QaqC Dashboard, please don’t hesitate to reach out. We’re here to help!

Gurminder Singh (Developer / Tutorial Author)
📧 g.singh@ndsu.edu

Dr. Richard Horsley (Department Head, Project Lead)
📧 richard.horsley@ndsu.edu

Dr. Ana Heilman-Morales (Director, NDSU Agricultural Data Analytics)
📧 ana.heilman.morales@ndsu.edu

NDSU Big Data Team (Technical Support)
📧 ndsu.bigdata@ndsu.edu

**💡 Tip:** When emailing, please include a brief description of the problem and, if possible, a screenshot of the error or the dataset structure you are working with. This helps us respond more effectively.

* * * 
* * *
* * * 
* * *
