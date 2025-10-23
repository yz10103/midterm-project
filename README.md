# ESG Scores and Financial Performance Across Industries  
### NYU Data Bootcamp – Midterm Project  

**Team Members:** Menghan Liu · Yicheng Song · Jenny Zhu  

---

## **Abstract**  
This project investigates the relationship between **Environmental, Social, and Governance (ESG)** performance and **financial indicators** across publicly listed firms. Using data collected through APIs from Yahoo Finance and Finnhub, we conduct an exploratory data analysis (EDA) to evaluate ESG score distributions, inter-industry differences, and their relationship with key financial metrics.  

Through comparative analysis, the **Consumer Goods sector**—particularly its **Consumer Defensive** and **Consumer Cyclical** segments—emerged as notably distinctive in both data representation and ESG consistency. Consequently, the study performs a deeper dive into this sector to interpret its internal ESG variations and the insights they provide about sustainability and firm performance.

---

## **1. Introduction**  
The purpose of this project is to analyze how ESG performance differs across industries and whether higher ESG engagement corresponds to better financial characteristics such as profitability, market capitalization, and risk.  

Initial comparisons revealed large disparities among industries. Certain sectors demonstrate strong ESG integration due to environmental exposure and stakeholder visibility, while others lag behind. Among them, the **Consumer Goods industry** stood out for its **high number of firms**, **relatively strong average ESG scores**, and **stable within-sector variation**.  

This finding guided our focus toward the **Consumer Goods industry**, a sector where consumer visibility and brand accountability often translate into consistent sustainability initiatives.

---

## **2. Data and Methodology**

### **2.1 Data Sources**  
- **Yahoo Finance API:** Provided firm-level financial indicators such as *Market Capitalization*, *Profit Margins*, *Return on Equity (ROE)*, *Beta*, and *Price-to-Book Ratio*.  
- **Finnhub ESG Dataset:** Supplied ESG component scores — *environmentScore*, *governanceScore*, and *totalEsg*.  

The merged dataset contained approximately **500 firms** and **12 key features**, encompassing both numerical and categorical data.

### **2.2 Data Cleaning and Transformation**  
Data were imported using Python’s `pandas` and merged based on firm identifiers. Firms missing all ESG components were excluded. Skewed variables such as market capitalization were log-transformed for normalization.  

### **2.3 Analytical Framework**  
The analysis follows a descriptive and comparative EDA structure:  
1. **Cross-Industry Comparison** – visualize ESG score distribution and identify industry differences.  
2. **Consumer Goods Deep Dive** – analyze Consumer Defensive and Consumer Cyclical sectors.  
3. **Correlation & Regression** – examine relationships between ESG and financial variables.  
4. **Statistical Validation** – apply ANOVA to test whether ESG differences across industries are significant.  

All computations were performed in **Google Colab (Python 3.10)** using `pandas`, `numpy`, `matplotlib`, `seaborn`, and `statsmodels`.

---

## **3. Results and Findings**

### **3.1 Cross-Industry ESG Comparison**  
Across industries, **environmental scores** display a right-skewed distribution—most firms score moderately low, with a few high performers. **Governance scores** are more centered, suggesting greater standardization across firms.  

The **boxplot of total ESG by sector** shows that *Energy* and *Basic Materials* sectors have the highest median ESG but also the widest range, indicating uneven adoption. *Communication Services* and *Real Estate* tend to have lower and more dispersed scores.  

The **Consumer sectors** show moderately high median ESG scores with less dispersion, implying a strong and consistent ESG presence across firms.  

The **bar chart of industry mean ESG** reinforces these observations: industries tied to essential daily consumption—such as *Packaged Foods*, *Household Products*, and *Grocery Stores*—rank among the top in ESG performance, while more discretionary industries—like *Gambling* or *Apparel Retail*—rank lower.  
The **ANOVA test** confirms that ESG differences across industries are statistically significant (*p* < 0.001).

---

### **3.2 Why the Consumer Goods Sector Stands Out**  
From cross-industry comparison, the Consumer Goods sector stands out for three reasons:  
- It includes **the largest number of firms**, producing stable and representative averages.  
- Its **mean ESG scores** are among the highest across industries.  
- It shows **balanced score dispersion**, suggesting mature and standardized ESG implementation.  

Because consumer-facing companies operate under strong public scrutiny, they face direct pressure from consumers and regulators to maintain transparency and ethical practices. This sector therefore provides an ideal setting for a focused analysis of ESG behavior and its financial implications.

---

### **3.3 Deep Dive: The Consumer Goods Industry**  
Within the Consumer Goods industry, firms are divided into **Consumer Defensive** and **Consumer Cyclical** categories.  

Descriptive statistics reveal moderate profitability (*Profit Margins ≈ 4%*, *ROE ≈ 16%*) and wide variation in firm size (log Market Cap).  

The **histograms of ESG components** show similar shapes across this subset:  
- *environmentScore* remains the most dispersed,  
- *governanceScore* clusters tightly near the middle, and  
- *totalEsg* follows a roughly normal distribution centered near 25.  

The **industry summary table** shows that *Farm Products*, *Packaged Foods*, and *Grocery Stores* achieve the highest mean total ESG, while *Tobacco* and *Apparel Retail* fall behind.  

The **boxplot of total ESG by industry** within Consumer Goods displays substantial but interpretable differences. *Farm Products* exhibits the highest median ESG with limited variation, whereas *Apparel Retail* and *Tobacco* show both low medians and high dispersion.  

The **ANOVA test** across these industries reports *F = 7.15, p < 0.001*, confirming that ESG levels significantly differ among Consumer sub-industries.

---

### **3.4 Correlation and Regression Analysis**  
The **correlation heatmap** reveals strong internal consistency within ESG measures:  
- *totalEsg* correlates highly with *environmentScore* (*r = 0.75*) and moderately with *governanceScore* (*r = 0.43*).  
- Correlations between ESG and financial metrics (*Profit Margins*, *ROE*, *Beta*, *Price-to-Book*) are weak, indicating that ESG performance is largely independent of short-term financial outcomes.  

A regression of *log(MarketCap)* on *totalEsg* yields a small, statistically insignificant coefficient (*p ≈ 0.08*). Adding financial controls does not change the result—suggesting ESG does not directly drive profitability, though larger firms tend to perform better in both ESG and financial metrics.

---

## **4. Discussion and Interpretation**  
ESG engagement varies widely across industries, reflecting differences in environmental exposure, stakeholder expectations, and corporate governance maturity.  

The **Consumer Goods industry** distinguishes itself through **scale, stability, and accountability**. The sector’s higher average ESG scores result from stronger consumer pressure and tighter brand oversight. Its large representation within the dataset also stabilizes observed patterns, avoiding outlier effects seen in smaller industries.  

Within Consumer Goods, *Defensive* segments (Food, Household, and Staples) exhibit more consistent ESG commitment than *Cyclical* ones (Retail, Apparel, Leisure). Necessity-driven products tend to prioritize sustainability to preserve consumer trust, whereas discretionary goods experience greater score dispersion due to differing brand strategies.  

Although the statistical relationship between ESG and immediate profitability remains weak, high ESG adoption appears linked to **long-term brand value, reduced regulatory risk, and reputational resilience**—factors critical in consumer-facing industries.

---

## **5. Conclusion**  
This project demonstrates that ESG performance differs substantially across industries, with the **Consumer Goods sector** showing a combination of **strong average ESG**, **low variance**, and **broad representation**.  

Environmental factors contribute most to overall ESG variation, while governance remains consistently moderate. Financial correlations suggest ESG is not a short-term profitability driver but a **strategic stability indicator**.  

The Consumer Goods industry, due to its public visibility and stakeholder pressure, exemplifies how sustainable practices become embedded into long-term corporate strategy rather than driven by immediate financial gain.

---

## **6. Reproducibility and Tools Used**  
All analysis was conducted in **Google Colab** using **Python 3.10** with the following libraries:  
`pandas`, `numpy`, `matplotlib`, `seaborn`, `statsmodels`, `requests`, and `yfinance`.  

Repository contents include:  
- `Midterm_Project.ipynb` — main analysis notebook  
- `MIDTERM_Q(1).py` — summarized code version  
- `README.md` — this report  

All datasets were obtained via free and reproducible API access.

---

## **Data Sources**  
- ESG data retrieved from **Finnhub API** – [https://finnhub.io](https://finnhub.io)  
- Financial data retrieved from **Yahoo Finance API** – [https://finance.yahoo.com](https://finance.yahoo.com)

---

*End of Report*
