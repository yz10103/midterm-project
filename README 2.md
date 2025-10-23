# **ESG Scores and Financial Performance Across Industries**

### **Team Members**
- **Menghan Liu**  
- **Yicheng Song**  
- **Jenny Zhu**

---

## **1. Project Overview / Objective**

This midterm project explores the relationship between companies’ **Environmental, Social, and Governance (ESG)** scores and their financial performance across multiple industries.  
Our primary objective is to determine whether firms with stronger ESG performance exhibit different financial characteristics—such as market stability or profitability—compared with those scoring lower.

The analysis is designed as an **exploratory data analysis (EDA)** project.  We first examine ESG score distributions and differences across industries to identify general patterns.  Based on those results, we focus on the **Consumer Goods industry**, which emerges as the most distinctive sector in both magnitude and consistency of ESG performance.  
The second stage then investigates this sector in greater depth to reveal internal variation and provide further interpretation.

---

## **2. Data Source & Preprocessing**

Data were collected from two primary APIs:

1. **Financial Modeling Prep (FMP)** — provides company-level ESG ratings, including *environmentalScore*, *socialScore*, *governanceScore*, and *totalEsg* metrics.  
2. **Yahoo Finance (yfinance)** — supplies fundamental financial indicators such as *market capitalization*, *profit margins*, *return on equity (ROE)*, *beta*, and *price-to-book ratio*.

**Data Cleaning and Integration**

- Merged the two sources using stock tickers as unique identifiers.  
- Removed firms lacking valid ESG or financial data.  
- Converted relevant fields to numeric format and standardized column names.  
- Verified that each observation corresponds to a single firm-year record.

After cleaning, the final dataset includes **approximately 500 firms** from **11 major sectors**, containing **12 mixed-type features** (categorical and numeric).  
This structure satisfies the course requirement for dataset complexity and scale (≥ 12 features, ≥ 300 rows).

---

## **3. Methodology / Analysis Steps**

The project follows a structured, sequential analysis pipeline consistent with our course workflow.

### **Step 1 – Cross-Industry Comparison**
Firms are grouped by *industry*.  
For each group, we compute the **mean**, **median**, and **count** of *environmentalScore*, *governanceScore*, and *totalEsg*.  
Industries with fewer than three firms are filtered out to ensure statistical reliability.  
Results are visualized using:

- **Bar charts** of mean Total ESG scores by industry.  
- **Box plots** to illustrate score dispersion within each industry.  
- An **ANOVA test** to assess whether mean ESG scores differ significantly across industries.

### **Step 2 – Sector-Level Aggregation**
Industries are merged into broader **sectors** (e.g., Consumer, Technology, Industrials, Financial Services).  
Boxplots show how ESG scores vary by sector, helping us observe where Consumer Goods stands relative to others.

### **Step 3 – Correlation Analysis**
We analyze linear relationships among ESG scores and financial indicators using **Pearson correlation coefficients**.  
A **correlation matrix** and **heatmap** visualize the strength and direction of associations.  
This step provides statistical context for how ESG performance may relate to market characteristics such as firm size (log Market Cap), profitability, and risk (Beta).

---

## **4. Key Findings and Interpretation**

### **Cross-Industry ESG Comparison**

The industry-level summary reveals clear heterogeneity in ESG performance across sectors.  
Industries such as **Farm Products** and **Packaged Foods** display the **highest average Total ESG scores**, while **Gambling**, **Discount Stores**, and **Recreational Vehicles** rank substantially lower.  
The bar chart of mean scores confirms that ESG practices vary not only in magnitude but also in consistency among industries.  

The **ANOVA test** result (*F = 7.1524, p < 0.001*) indicates that these cross-industry differences are statistically significant.  
This confirms that ESG performance is not uniformly distributed—certain industries integrate sustainability principles more extensively than others.

Interpreting this pattern, sectors with **consumer-facing products** and strong public visibility generally show higher ESG scores.  
These industries are subject to greater external scrutiny and consumer expectations for ethical sourcing, environmental responsibility, and transparent governance.  
Conversely, industries with less direct consumer contact or fewer regulatory pressures tend to have weaker ESG engagement.

---

### **Why the Consumer Goods Industry Stands Out**

From the cross-industry comparison, the **Consumer Goods sector** emerges as a consistent leader.  
When visualizing total ESG scores by sector, the Consumer Goods category demonstrates both a **high average score** and **lower dispersion**, meaning firms within this sector perform similarly well.

In the data, Consumer Goods-related industries—including **Packaged Foods**, **Beverages**, **Restaurants**, and **Household Products**—maintain relatively balanced environmental and governance scores.  
Few extreme outliers exist, and median values remain above those of most other sectors.

Several structural factors contribute to this result:

- **Representation:** Consumer industries account for **over one-third of all firms** in the dataset, giving the sector greater statistical weight and a more stable distribution.  
- **Standardization:** Firms in this industry often operate under well-defined sustainability frameworks and certification standards, producing less variation in ESG scores.  
- **Public accountability:** Because these companies interact directly with end-consumers, ESG practices become integral to brand value and corporate strategy.

Collectively, these characteristics make the Consumer Goods sector both numerically dominant and analytically meaningful—warranting the deeper exploration that follows.

---

### **Insights from the Deep Dive into Consumer Goods**

In our focused analysis, we subdivide Consumer Goods into two primary categories:  
**Consumer Defensive** and **Consumer Cyclical**.  
The boxplot comparing these groups (see figure “Distribution of Total ESG by Sector”) illustrates clear differences in median scores and dispersion.

- **Consumer Defensive firms** (e.g., food producers, household goods) exhibit **higher median ESG scores** and **narrower interquartile ranges**, indicating stronger and more consistent sustainability performance.  
  Their stability aligns with business models emphasizing long-term trust, essential-product demand, and low revenue volatility.  

- **Consumer Cyclical firms** (e.g., retailers, discretionary goods) show **wider dispersion and lower medians**, reflecting greater diversity in ESG engagement.  
  This variation corresponds with differing levels of exposure to short-term market fluctuations and branding strategies.

Thus, while the Consumer Goods sector as a whole demonstrates superior ESG performance relative to other industries, internal heterogeneity persists depending on a firm’s market cycle sensitivity.  
Defensive subsectors appear more mature in embedding ESG principles into corporate governance, whereas cyclical subsectors exhibit uneven adoption.

These findings are visually supported by the sector-level boxplots and are consistent across multiple ESG dimensions, reinforcing the robustness of the observed pattern.

---

### **Correlation Analysis and Sector-Level Context**

The correlation matrix and heatmap provide additional quantitative insight.  
Among the ESG dimensions, **environmentalScore** and **totalEsg** show a strong positive correlation ( *r ≈ 0.75 *), confirming that the environment component drives most of the overall ESG variation.  
Correlations between ESG metrics and financial variables are generally modest:

- *Total ESG vs log Market Cap:* slightly negative ( r ≈ -0.20 ) → larger firms do not necessarily score higher on ESG.  
- *Total ESG vs Profit Margins / ROE:* near zero → limited direct relationship between ESG performance and profitability.  
- *Total ESG vs Beta:* weak negative association ( r ≈ -0.10 ) → firms with higher ESG scores tend to show slightly lower market volatility.

Although none of these relationships are economically large, they suggest that ESG strength may correlate with marginally greater stability rather than with short-term returns.  
The correlation heatmap (see figure “Correlation Heatmap (Pearson)”) visually confirms these patterns: warmer colors along the environment–total ESG axis and cooler tones between ESG and financial metrics.

---

### **Synthesis of Findings**

1. **Industry Differences:** ESG performance varies significantly across industries, validated by statistical testing.  
2. **Consumer Goods Leadership:** This sector consistently achieves high and stable ESG scores, partly due to public visibility and institutionalized sustainability standards.  
3. **Intra-Sector Variation:** Within Consumer Goods, Defensive firms surpass Cyclical firms in ESG consistency.  
4. **Financial Relationships:** ESG performance is weakly linked to market stability but not to profitability or firm size.

Together, these findings demonstrate that ESG engagement is shaped more by **industry structure and stakeholder pressure** than by financial returns alone.  
The Consumer Goods industry, by virtue of its consumer exposure and scale, provides the clearest example of how these forces manifest in practice.

---

## **5. Conclusion**

This project provides an exploratory, data-driven view of how ESG scores distribute across industries and how they relate to financial metrics.  
The analysis confirms substantial cross-industry variation and identifies the **Consumer Goods sector** as a notable leader in both average performance and internal consistency.  
Further decomposition of this sector shows that Consumer Defensive firms achieve particularly stable ESG profiles compared with their Cyclical counterparts.  

While correlations between ESG and financial indicators are weak, they suggest that firms with stronger ESG commitments may enjoy slightly lower risk exposure and greater market resilience.  
Overall, the results underscore the importance of industry context in interpreting ESG data and illustrate how sector-specific characteristics shape corporate sustainability outcomes.

---

## **6. Code Reproducibility Note**

All analysis was conducted in **Python (3.x)** using **Google Colab**.  
Key libraries include:  
`pandas`, `numpy`, `matplotlib`, `scipy`, `yfinance`, `tqdm`, and `requests`.

The full implementation is contained in two files:  
- `Midterm_Project.ipynb` – complete analysis notebook with code, figures, and interpretations.  
- `MIDTERM_Q(1).py` – condensed code summary for quick reference and reuse.

Running the notebook sequentially from top to bottom will reproduce all data cleaning, aggregations, statistical tests, and plots exactly as shown.  
No manual input or external editing is required.


