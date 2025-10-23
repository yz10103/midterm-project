# **ESG Scores and Financial Performance Across Industries: Exploratory Analysis**

### **Team Members**
- **Menghan Liu**  
- **Yicheng Song**  
- **Jenny Zhu**

---

## **1. Project Overview / Objective**

This project explores the relationship between **Environmental, Social, and Governance (ESG)** scores and firms’ **financial characteristics** across different industries.  
The analysis seeks to identify which sectors demonstrate higher ESG performance, whether ESG levels vary significantly across industries, and how these differences relate to financial indicators such as market capitalization, profitability, and valuation ratios.

The study proceeds in two stages:
1. **Cross-industry ESG comparison** — comparing average and distributional ESG scores across multiple sectors.  
2. **Focus on the Consumer Goods sector** — conducting a deeper exploration of ESG behavior within one industry that stands out in consistency and representation.

---

## **2. Data Source & Collection**

All data are collected programmatically using Python.  
The project integrates information from two main APIs:

1. **Financial Modeling Prep (FMP)** — used to retrieve company-level ESG scores, including:
   - `environmentScore`
   - `socialScore`
   - `governanceScore`
   - `totalEsg`
2. **Yahoo Finance (yfinance)** — used to extract firm-level financial indicators such as:
   - Market Capitalization (`marketCap`)
   - Price-to-Book Ratio (`priceToBook`)
   - Beta (`beta`)
   - Profit Margins (`profitMargins`)
   - Return on Equity (`returnOnEquity`)
   - Industry classification

The resulting dataset merges these two sources based on firm tickers and includes **approximately 500 companies** across **11 industries**, with **12 features** of mixed numerical and categorical types.

---

## **3. Data Cleaning and Preprocessing**

Data preprocessing and feature alignment were conducted using **pandas**.  
The major steps include:
- Filtering firms with valid ESG and financial data.  
- Dropping duplicated or missing values.  
- Standardizing data types and resetting the index for analysis.  
- Creating new columns to categorize firms by **industry** and **sector** for grouped comparisons.  

After cleaning, the dataset satisfies all midterm project requirements:  
> ≥ 12 columns (mixed numeric and categorical) and ≥ 300 observations.

---

## **4. Methodology**

All analysis was performed in **Python 3.10**, using the following libraries:  
`pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy.stats`, `yfinance`, and `requests`.

The exploratory process follows three main stages:

### **Step 1 — Industry-Level ESG Analysis**
- Firms are grouped by industry.  
- Mean and median ESG scores are computed for each group.  
- A **bar plot** visualizes average ESG performance by industry.  
- A **box plot** compares the dispersion of ESG scores within each sector.  
- An **ANOVA test** evaluates whether average ESG scores differ significantly across industries.

### **Step 2 — Sector Aggregation**
- Industries are categorized into broader **sectors** (e.g., Consumer, Technology, Financials).  
- Sector-level averages are computed to identify which sectors demonstrate the strongest ESG engagement.  
- The **Consumer sector** emerges as particularly interesting due to its large representation and relatively high ESG averages.

### **Step 3 — Consumer Goods Deep Dive**
- A subset of firms belonging to **Consumer Goods** is isolated for focused analysis.  
- Descriptive statistics and visualizations show ESG score variation within this sector.  
- The **Consumer Defensive** and **Consumer Cyclical** segments are examined to interpret differences in consistency and performance.  
- Visual comparisons are made using **box plots** and **histograms** of ESG components.

---

## **5. Key Findings and Interpretation**

### **Cross-Industry ESG Comparison**
Across all industries, ESG performance exhibits meaningful variation.  
Industries such as **Farm Products**, **Packaged Foods**, and **Beverages** achieve relatively high ESG averages, while **Gambling**, **Discount Stores**, and **Recreational Vehicles** show much lower results.  

The **ANOVA test** indicates that these differences are **statistically significant** (*p < 0.001*), confirming that ESG performance is not uniform across industries.  
Visual comparisons further highlight that sectors with strong consumer interaction and visibility tend to maintain higher ESG engagement, while those with fewer public-facing responsibilities display lower scores and wider dispersion.

---

### **Why the Consumer Goods Sector Stands Out**
Among all sectors analyzed, **Consumer Goods** demonstrates one of the **highest average ESG scores** and the **lowest score variability**.  
This indicates a strong internal consistency in sustainability performance, supported by greater regulatory pressure, supply-chain visibility, and public accountability.  

The sector also contains the **largest number of firms** in the dataset (accounting for roughly one-third of all entries), ensuring strong statistical reliability.  
These attributes make the Consumer Goods industry an ideal focus for a detailed ESG assessment.

---

### **Insights from the Deep Dive into Consumer Goods**
The **Consumer Goods industry**—encompassing both *Consumer Defensive* and *Consumer Cyclical* firms—exhibits an overall strong and cohesive ESG pattern.  

- **Consumer Defensive firms** (e.g., food, beverages, household essentials) tend to achieve **higher median ESG scores** and **narrower dispersion**, suggesting structured sustainability frameworks and consistent governance practices.  
- **Consumer Cyclical firms** (e.g., apparel, retail, leisure) show **slightly lower medians** and broader variation, reflecting differing degrees of ESG prioritization.  

Despite these differences, the Consumer Goods sector as a whole maintains a stable ESG profile compared to other industries.  
This suggests that **ESG integration has become an industry norm**, not merely a differentiating factor.

---

### **Correlation Analysis**
Pairwise correlations reveal that:
- **environmentScore** strongly correlates with **totalEsg** (*r ≈ 0.75*), showing that environmental performance drives most ESG variation.  
- ESG scores have **weak correlations** with financial metrics such as *Profit Margins*, *ROE*, and *Market Cap*.  
- A **slight negative correlation** with *Beta* suggests that higher-ESG firms may experience slightly lower volatility.

These relationships imply that ESG commitment may not immediately affect profitability, but it could contribute to long-term **market stability and reputational resilience**.

---

## **6. Conclusion**

This project provides a comprehensive exploratory analysis of ESG performance and its relationship with financial indicators across industries.  
The results demonstrate significant cross-industry differences in ESG adoption, with the **Consumer Goods sector** emerging as a leading performer in both average ESG scores and internal consistency.  

Within Consumer Goods, **Defensive firms** show particularly mature ESG integration, while **Cyclical firms** display wider variation but still maintain moderate engagement.  
Overall, the findings suggest that ESG performance is shaped more by **industry characteristics and stakeholder pressure** than by firm size or immediate profitability.

---

## **7. Code Reproducibility and Structure**

All computations are contained in the file **`MIDTERM_Q(1).py`**, organized into modular, clearly commented sections.  
Each code block is reproducible and can be executed independently in Google Colab or Jupyter Notebook.  
Key sections include:

1. **Data Import and Cleaning** – API retrieval, merging, and formatting.  
2. **Industry-Level Analysis** – groupby operations, mean/median calculations, and visualizations.  
3. **Statistical Testing** – ANOVA for ESG mean differences.  
4. **Consumer Goods Deep Dive** – subsetting and visual interpretation.  
5. **Correlation Analysis** – Pearson correlation matrix and heatmap plotting.

Running the script sequentially will recreate all tables, plots, and statistical results.

---

## **8. Tools and Libraries**
- `pandas` – data manipulation  
- `numpy` – numerical computation  
- `matplotlib` / `seaborn` – visualization  
- `scipy.stats` – statistical testing (ANOVA)  
- `yfinance` – financial data retrieval  
- `requests` – API access  

---

## **9. Data Sources**
- **ESG Data:** Financial Modeling Prep API – [https://financialmodelingprep.com](https://financialmodelingprep.com)  
- **Financial Data:** Yahoo Finance – [https://finance.yahoo.com](https://finance.yahoo.com)

---

**Word count:** ≈ 1,470  
**Format:** Markdown (`README.md`) – ready for submission on GitHub or Colab.

