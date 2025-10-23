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
We begin by examining how **Total ESG** varies across sectors.  
Boxplots and histograms summarize ESG distributions, while the **Kruskal–Wallis test** assesses whether differences in ESG levels among sectors are statistically significant.  

We also compute **sector-wise means** for governance, environment, ROE, and beta, creating scatter plots to relate ESG components to profitability and risk.

### **4.2 Cross-Industry Interpretation**
- *Governance vs ROE:* reveals how governance quality aligns with average profitability.  
- *Environment vs Beta:* shows whether environmentally stronger sectors experience lower market volatility.  

These relationships guide our later Consumer sector hypotheses.

### **4.3 Consumer Sector Exploration**
We isolate all consumer-related firms obtained from the Yahoo screeners, forming a detailed dataset of **Consumer Defensive** and **Consumer Cyclical** companies.  
Within this subset we:

1. Examine missing ESG values (E and G) to gauge disclosure completeness.  
2. Visualize the **distribution of Total ESG scores** across the consumer sector.  
3. Compute descriptive statistics to identify ESG leaders and laggards.

### **4.4 Hypothesis Testing**
Derived from the cross-industry findings, we test two formal hypotheses:

- **H1:** Higher *Governance Score* → Higher *Profitability (ROE)*.  
- **H2:** Higher *Environment Score* → Lower *Market Risk (Beta)*.

Ordinary Least Squares (OLS) regressions are run using `statsmodels.formula.api` to estimate these relationships within consumer firms.

### **4.5 ESG and Firm Characteristics**
We explore whether ESG relates to **firm size** and **volatility**:

- Scatterplots: ESG vs log(Market Cap) and ESG vs Beta.  
- Spearman correlations quantify monotonic relationships.  
- A multivariate OLS regression of `totalEsg ~ log_marketCap + beta` evaluates combined effects.

### **4.6 Disclosure Behavior**
To identify transparency gaps, we calculate the percentage of missing **E** and **G** scores per **Consumer industry** and visualize them with paired bar charts.  
A complementary boxplot of **Total ESG by industry** reveals how ESG levels differ among those that report data.

---

## **5. Key Findings and Interpretation**

### **5.1 Cross-Industry ESG Patterns**
ESG performance varies considerably across sectors.  
The **Kruskal–Wallis test** confirms these differences are statistically significant (*p < 0.001*).  
Sectors such as **Utilities**, **Consumer**, and **Staples** show relatively higher median ESG scores, while **Energy**, **Financials**, and **Recreational industries** lag.  

Histogram and boxplot analyses highlight that sectors with strong consumer visibility and regulatory oversight tend to maintain tighter ESG distributions, implying standardized sustainability frameworks.

---

### **5.2 Governance vs Profitability (ROE)**
In the scatterplot of **average Governance Score vs Return on Equity**, the **Consumer sector** lies in the *upper-left quadrant*—relatively high governance but moderate ROE.  
This suggests that strong governance promotes **stability and compliance** more than short-term profit maximization.  
By contrast, **Financials** and **Energy** attain higher ROE despite weaker governance, consistent with capital-intensive or cyclical profit structures.

---

### **5.3 Environment vs Market Risk (Beta)**
A visible **downward relationship** emerges between **Environmental Score** and **Beta** across sectors.  
Industries with stronger environmental management—such as Utilities and Staples—tend to experience **lower volatility**, whereas high-beta industries show weaker environmental performance.  
This supports the interpretation that environmental stewardship corresponds to **greater market stability**.

---

### **5.4 Why the Consumer Goods Sector Stands Out**
When comparing all sectors, **Consumer Goods** demonstrates both **high ESG averages** and **low variability**, making it a statistically and substantively interesting focus.  
The Consumer sector also contains a **large sample size** drawn from both *Consumer Defensive* and *Consumer Cyclical* subsectors, ensuring robust representation.

Consumer companies operate in highly visible markets where sustainability influences brand trust and purchasing behavior.  
Consequently, the sector shows consistent ESG commitment even when profitability outcomes differ.

---

### **5.5 Consumer Sector ESG Distribution**
Within the Consumer sector, **Total ESG scores** are widely dispersed, with notable leaders and laggards.  
Histogram analysis shows a roughly normal distribution centered near mid-range values, indicating broad engagement but unequal depth of implementation.

Missing-value diagnostics reveal that:
- Some firms omit **E** or **G** scores entirely, reducing transparency.  
- Missingness rates vary by subsector, hinting that disclosure practices differ by industry culture rather than data unavailability.

---

### **5.6 Hypothesis Results**

**H1: Governance → Profitability**  
OLS regression of `ROE ~ governanceScore` finds a positive though moderate coefficient, suggesting that **better governance aligns with improved profitability**, supporting the first hypothesis within the limitations of data completeness.

**H2: Environment → Risk (Beta)**  
Regression of `Beta ~ environmentScore` yields a **negative coefficient**, consistent with the notion that environmentally proactive firms face **lower market risk**.  
This aligns with the earlier cross-industry trend that strong environmental behavior correlates with stability.

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

1. **ESG scores differ significantly by industry.**  
   Consumer-facing sectors and utilities maintain higher and more consistent scores, whereas capital-intensive or entertainment sectors trail.

2. **Consumer Goods lead in consistency.**  
   The sector’s uniform ESG behavior arises from brand pressure, public exposure, and stakeholder expectations.

3. **Governance supports profitability; environmental effort reduces risk.**  
   Regression outcomes suggest that strong governance aligns with higher ROE, and robust environmental management aligns with lower Beta.

4. **Firm size and stability matter.**  
   Larger, less volatile firms typically exhibit stronger ESG performance.

5. **Disclosure remains uneven.**  
   Variations in missing E/G data across industries imply that ESG transparency is still evolving, especially in discretionary consumer segments.

Overall, the findings highlight how **sustainability has become institutionalized in Consumer Goods**—not merely a reputational choice but an operational standard shaping long-term resilience.

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


