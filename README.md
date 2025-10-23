# **ESG Scores and Financial Performance Across Industries: A Focus on the Consumer Goods Sector**

### **Team Members**
- **Menghan Liu**  
- **Yicheng Song**  
- **Jenny Zhu**

---

## **1. Project Overview**

This project conducts an **exploratory data analysis** on the relationship between **Environmental, Social, and Governance (ESG)** scores and financial performance across industries, with a specific emphasis on the **Consumer Goods sector**.  
Our central question is whether industries with stronger ESG practices exhibit different financial and risk characteristics and, within the consumer sector, how ESG patterns differ among subsectors.

The analysis proceeds in two stages:

1. **Cross-industry comparison** – examining ESG distributions across all S&P 500 sectors.  
2. **Consumer Goods deep dive** – analyzing ESG behavior, disclosure, and financial linkages inside the consumer sector.

The study is descriptive rather than predictive: we rely on visualizations and statistical relationships to interpret patterns rather than forecast outcomes.

---

## **2. Data Sources**

All data are gathered **directly from public Yahoo Finance endpoints** and **Wikipedia**, without the use of paid APIs.  

1. **S&P 500 Tickers**  
- Scraped from the official Wikipedia *List of S&P 500 companies* page.  
- Provides company symbols for broad-market coverage, representing major U.S. firms that compose the S&P 500 stock market index.  

2. **Yahoo Finance**  
   - Retrieved company-level information through the `yfinance` package, including:  
     - *Fundamentals:* `marketCap`, `beta`, `forwardPE`, `priceToBook`, `profitMargins`, `returnOnEquity`.  
     - *Classification:* `sector`, `industry`, and `shortName`.  
     - *Sustainability:* `environmentScore`, `governanceScore`, and `totalEsg` via each ticker’s sustainability table.

3. **Yahoo Finance Screeners for Consumer Sectors**  
   - Queried two built-in screener endpoints:  
     - `ms_consumer_defensive` and `ms_consumer_cyclical`.  
   - Supplies an extended list of consumer-sector firms beyond the S&P 500.  

All scraping operations include polite pauses and error handling to respect rate limits.  
Final dataset size: approximately **500 firms** across **11 industries**, exceeding the required 300 observations and 12 features.

---

## **3. Data Preparation**

The workflow was implemented in Python using `pandas`, `numpy`, and `tqdm`.  
Major steps include:

- Fetching S&P 500 tickers and metadata from Wikipedia.  
- Looping through tickers with `yfinance.Ticker()` to retrieve financial and ESG data.  
- Collecting separate datasets for **all S&P 500 companies** (`df_all`) and **Consumer sector companies** (`df_consumer_all`).  
- Converting market capitalization to billions and log scale.  
- Standardizing sector names so *Consumer Defensive* and *Consumer Cyclical* both map to a unified **Consumer** category.  
- Filtering valid ESG observations and merging key variables.  

The cleaned dataset provides complete numerical and categorical information for subsequent EDA and hypothesis testing.

---

## **4. Methodology**

### **4.1 Industry-Level Analysis**
We examine **Total ESG** variation across sectors using boxplots and histograms.  
A **Kruskal–Wallis test** evaluates whether ESG levels differ significantly among sectors.  
The notebook output shows a test statistic **H ≈ 175.6, p ≈ 4.2×10⁻³³**, confirming strong sectoral differences.
<img width="989" height="590" alt="ESG Scores by Sector" src="https://github.com/user-attachments/assets/2233ed73-4e92-46f0-b9b9-4ec39df310d7" />


<img width="971" height="613" alt="Screenshot 2025-10-23 at 19 21 19" src="https://github.com/user-attachments/assets/bfd68557-38e5-47cc-90b4-306b8de7b888" />

### **4.2 Cross-Industry Interpretation**
Plots and summary statistics relate sector-level **Environment**, **Governance**, **ROE**, and **Beta** measures.  
These reveal contrasting ESG-risk-profitability patterns across industries.
<img width="1074" height="712" alt="Screenshot 2025-10-23 at 19 21 37" src="https://github.com/user-attachments/assets/8b62ab39-612b-4f4b-9f88-c614edbe7844" />


<img width="1074" height="725" alt="Screenshot 2025-10-23 at 19 21 49" src="https://github.com/user-attachments/assets/010eba15-0126-4517-a4b9-436b565a42de" />



### **4.3 Consumer Sector Exploration**
We isolate consumer firms (both *Consumer Defensive* and *Consumer Cyclical*) and explore:
1. Missingness of Environmental and Governance scores,  
2. The distribution of Total ESG, and  
3. Descriptive statistics highlighting leading and lagging firms.
<img width="952" height="591" alt="Screenshot 2025-10-23 at 19 22 02" src="https://github.com/user-attachments/assets/c430db19-aabf-4205-a519-9da4d7e7507c" />


<img width="709" height="472" alt="Screenshot 2025-10-23 at 19 22 16" src="https://github.com/user-attachments/assets/509887af-6ec0-4cee-8f61-145217412ae1" />




### **4.4 Hypothesis Testing** 

Two simple **Ordinary Least Squares (OLS)** models are estimated for Consumer firms:


- **H1:** `returnOnEquity ~ governanceScore`  
- **H2:** `beta ~ environmentScore`

These are **bivariate exploratory regressions** meant to identify directional relationships, not causal effects.
There are also scatter plots visualizing this effect.

<img width="837" height="597" alt="Screenshot 2025-10-23 at 19 23 01" src="https://github.com/user-attachments/assets/d191331e-c9de-4a4d-bb2c-821f69c54e7a" />


<img width="837" height="597" alt="Screenshot 2025-10-23 at 19 23 12" src="https://github.com/user-attachments/assets/39e07364-950b-48b2-821a-e8f617031285" />



### **4.5 ESG and Firm Characteristics**
We assess whether **Total ESG** relates to firm size and market risk using:
- Spearman correlations between ESG and key variables, and  
- A multivariate regression:  
  \[
  \text{totalEsg} \sim \log(\text{marketCap}) + \text{beta}
  \]

### **4.6 Disclosure Behavior**
We calculate per-industry missingness for **Environmental** and **Governance** scores within the consumer sector.  
The results are visualized via **bar plots** and **boxplots** to show transparency patterns and ESG distribution differences.
<img width="1345" height="575" alt="Screenshot 2025-10-23 at 19 23 28" src="https://github.com/user-attachments/assets/e842ad3a-9aa1-4d71-bb86-40be9a3d59b7" />


<img width="1176" height="709" alt="Screenshot 2025-10-23 at 19 23 44" src="https://github.com/user-attachments/assets/51fb2ad6-46ee-43ee-884d-7dcaf56c8f81" />




---

## **5. Key Findings and Interpretation**

### **5.1 Cross-Industry ESG Patterns** 
ESG levels vary widely by sector.  
The Kruskal–Wallis test confirms these differences are statistically significant (*p < 0.001*).  
Sectors such as **Utilities** and **Consumer** exhibit higher median ESG scores, while **Energy** and **Financials** lag.

---

### **5.2 Governance vs Profitability (ROE)** 
The bivariate regression  
`returnOnEquity ~ governanceScore`  
is **not statistically significant** (R² ≈ 0.002, *p ≈ 0.504*).  

This means **H1 is not supported** — there is **no clear evidence** that stronger governance directly corresponds to higher profitability (ROE) in this dataset.

---

### **5.3 Environment vs Market Risk (Beta)** 
The regression  
`beta ~ environmentScore`  
produces a **negative and significant coefficient** (*β ≈ −0.0333, p < 0.01*).  
This supports **H2**, suggesting that firms with higher environmental scores tend to exhibit **lower market risk (Beta)**, aligning with stability-oriented ESG interpretations.

---

### **5.4 Consumer Sector ESG Distribution** 
Consumer-sector Total ESG scores are broadly distributed but center around moderate values.  
Subsector differences remain visible — some (e.g., Household, Food & Beverage) cluster higher, while others (e.g., Apparel, Leisure) show greater variation or missingness.

---

### **5.5 ESG and Firm Characteristics** 
Correlation and regression analysis yield:

- **Spearman correlation:** ESG–Beta shows a small negative association (ρ ≈ −0.1465, *p ≈ 0.0027*).  
- **Multivariate OLS (`totalEsg ~ log_marketCap + beta`):**
  - log_marketCap coefficient = **−1.01** (*p < 0.001*)  
  - beta coefficient = **−1.81** (*p ≈ 0.002*)

Thus, in this sample:
> **Larger firms and those with higher volatility tend to have lower Total ESG scores.**

This **contradicts** the earlier expectation that larger firms have higher ESG scores, illustrating how exploratory results can challenge assumptions.

---

### **5.6 Disclosure Behavior Across Consumer Industries** 
Bar-plot analysis reveals uneven ESG transparency:
- **Apparel** and **Leisure** firms show higher rates of missing E/G data.  
- **Food**, **Beverage**, and **Household Products** show more complete disclosures.  

   Boxplots confirm that even among reporting firms, ESG performance varies by subsector, highlighting inconsistency in sustainability reporting practices.
---

### **5.7 ESG and Firm Characteristics**
Spearman correlations and multivariate OLS results show:

- **Total ESG vs Market Cap:** weak positive correlation — larger firms tend to score higher, reflecting resource capacity and investor scrutiny.  
- **Total ESG vs Beta:** weak negative correlation — higher ESG corresponds to slightly lower volatility.  

The combined regression confirms these tendencies: **larger and more stable firms generally maintain stronger ESG profiles**.

---

### **5.8 Disclosure Behavior Across Consumer Industries**
Analysis of missing E/G scores uncovers uneven transparency:

- Certain sub-industries (e.g., Apparel and Leisure) have the **highest rates of E and G non-disclosure**, possibly reflecting reputational or strategic reluctance.  
- Industries like **Food, Beverage, and Household Products** report **more complete data**, aligning with mature ESG governance.  

The accompanying boxplot of Total ESG by industry shows that even within disclosed data, performance varies, emphasizing the need for standardized reporting.

---

## **6. Conclusions**

This project provides a comprehensive exploratory view of ESG dynamics across industries using real-time Yahoo Finance data.  
Key conclusions:

1. **ESG scores differ significantly across sectors.**  
   Kruskal–Wallis test confirms strong cross-sector variation (*p < 0.001*).

2. **Governance → Profitability:**  
   Not statistically significant. No evidence that higher governance scores predict higher ROE in this dataset.

3. **Environment → Risk:**  
   Significant negative relationship — firms with higher environmental scores show lower market beta (less risk).

4. **Firm size and volatility:**  
   Contrary to common assumptions, larger firms in this dataset exhibit **lower Total ESG scores**, and higher-beta firms also score lower.

5. **Disclosure patterns vary.**  
   Missingness in E/G reporting differs by consumer subsector, reflecting uneven transparency practices.

> Overall, the notebook’s exploratory evidence suggests that **environmental performance relates to stability**, while **governance–profitability links are weak**.  
> Firm size does not guarantee better ESG standing, underscoring the complexity of sustainability-performance dynamics in the consumer goods industry.


---

## **7. Reproducibility and Code Structure**

All analyses are contained in **`MIDTERM_Q(1)(2).py`**, which executes sequentially and reproducibly.  
Major code sections:

1. **Data Collection** – scrape S&P 500 tickers (Wikipedia) and Consumer lists (Yahoo Screeners).  
2. **Feature Extraction** – pull financial and ESG metrics via `yfinance`.  
3. **Data Cleaning & Merging** – handle missing values and normalize variables.  
4. **Exploratory Plots** – histograms, boxplots, sector comparisons.  
5. **Statistical Tests & Regressions** – Kruskal–Wallis, Spearman, OLS.  
6. **Consumer Industry Disclosure Analysis** – missing E/G patterns and visualizations.

The script can be run in **Google Colab** or **Jupyter Notebook** to reproduce every table and figure without modification.

---

## **8. Libraries**

| Library | Purpose |
|----------|----------|
| `pandas` | Data manipulation and cleaning |
| `numpy` | Numerical computation |
| `yfinance` | Financial and sustainability data retrieval |
| `requests` | Web scraping for tickers and consumer screens |
| `matplotlib` / `seaborn` | Visualization |
| `statsmodels` | OLS regression and statistical modeling |
| `scipy.stats` | Kruskal–Wallis and Spearman tests |
| `tqdm` | Progress bar for API loops |
| `time` / `os` | API pacing and configuration |

---

## **9. Data References**

- **S&P 500 Constituents:** [Wikipedia – List of S&P 500 companies](https://en.wikipedia.org/wiki/List_of_S%26P_500_companies)  
- **Financial and ESG Data:** [Yahoo Finance](https://finance.yahoo.com)  
- **Consumer Sector Screeners:** Yahoo Finance API (`ms_consumer_defensive`, `ms_consumer_cyclical`)


