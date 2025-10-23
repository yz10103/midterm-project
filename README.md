ESG Scores and Financial Performance Across Industries
NYU Data Bootcamp – Midterm Project

Team Members: Menghan Liu · Yicheng Song · Jenny Zhu

Abstract

This project explores the relationship between Environmental, Social, and Governance (ESG) performance and financial indicators across publicly listed firms. Using datasets constructed from public APIs and Yahoo Finance, we conduct an exploratory data analysis (EDA) to evaluate ESG score distributions, inter-industry differences, and the connection between ESG and financial stability.

Through cross-industry comparison, the Consumer Goods industry—particularly its Consumer Defensive and Consumer Cyclical segments—emerged as distinctive in both the scale of data representation and the consistency of ESG engagement. We therefore perform a deep-dive analysis within this sector to interpret what drives its ESG variation and how ESG relates to firm performance.

1. Introduction

The study aims to examine how ESG performance differs across industries and whether strong ESG engagement translates into measurable financial characteristics such as profitability, firm size, and risk.

Initial cross-industry exploration reveals notable disparities: some sectors demonstrate high ESG adoption due to environmental regulations or stakeholder pressure, while others show weaker commitment. Among these, the Consumer Goods industry stood out not only for its large representation in the dataset (accounting for a significant proportion of roughly 500 firms) but also for its stable, relatively high ESG performance.

This pattern motivated a deeper investigation into the Consumer Goods sector, where consumer visibility and brand accountability may contribute to more uniform sustainability behavior.

2. Data and Methodology
2.1 Data Sources

Yahoo Finance API – provided firm-level financial indicators including Market Capitalization, Beta, PE ratios, Profit Margins, and Return on Equity.

Finnhub ESG Dataset – supplied ESG component scores: environmentScore, governanceScore, and totalEsg.
The merged dataset contains mixed numerical and categorical variables across approximately 500 firms, with over 12 key features.

2.2 Data Processing

Data were imported via API calls and merged using Python (pandas). Missing or incomplete ESG data were handled by filtering out firms lacking all ESG components. Log transformation of Market Capitalization was applied to normalize scale differences.

2.3 Analytical Framework

The project follows a descriptive and comparative EDA pipeline:

Cross-Industry Analysis – visualize ESG score distributions and compare sectoral averages.

Consumer Goods Deep Dive – focus on firms classified as Consumer Defensive and Consumer Cyclical.

Correlation and Regression Tests – evaluate relationships between ESG scores and financial variables (log Market Cap, Profit Margins, ROE, Beta, Price-to-Book).

Statistical Validation – use ANOVA to test significance of ESG differences across industries.

All analyses were performed in Google Colab using Python libraries: pandas, numpy, matplotlib, seaborn, and statsmodels.

3. Results and Findings
3.1 Cross-Industry ESG Comparison

The histograms of ESG components show that environmental scores are right-skewed, indicating most firms perform modestly on environmental criteria, while governance scores are more centered, reflecting greater standardization.

In the boxplot of Total ESG by Sector, Energy and Basic Materials display the highest medians but wide dispersion, implying uneven adoption. Communication Services and Real Estate score consistently lower. The Consumer sectors fall in the upper-middle range, notable for both relatively high medians and moderate variation, indicating strong but consistent ESG performance across firms.

The bar chart of industry mean ESG confirms that industries linked to everyday consumption—such as Packaged Foods, Household Products, and Grocery Stores—maintain higher average ESG scores than luxury or discretionary categories like Gambling and Apparel Retail. An ANOVA test verified these differences are statistically significant (p < 0.001).

3.2 Why Consumer Goods Stand Out

From the cross-industry overview, the Consumer Goods sector emerged as distinctive for three main reasons:

It includes a large number of firms, providing richer, more stable statistical patterns.

Its average ESG scores are among the higher groups, particularly in Consumer Defensive industries.

It shows balanced variation, with neither extreme highs nor lows, implying mature and consistent ESG adoption.

Because consumer-facing companies are directly accountable to public perception, they face stronger incentives to maintain ethical sourcing, sustainability, and transparent governance. This combination of scale, stability, and social visibility made Consumer Goods an ideal candidate for deeper examination.

3.3 Deep Dive into the Consumer Goods Industry

Within the Consumer Goods subset (Consumer Defensive + Consumer Cyclical), descriptive statistics show market capitalizations ranging from small retailers to global conglomerates. Profit Margins average around 4 percent, and ROE centers near 16 percent, reflecting moderate but stable profitability.

The histograms of ESG components in this subset reveal similar structure: environmental scores remain most dispersed, governance scores cluster mid-range, and total ESG forms a bell-like distribution centered near 25.

At the industry level, Farm Products, Packaged Foods, and Grocery Stores show the highest total ESG, while Apparel Retail and Tobacco lag behind. The boxplot of Total ESG by Industry within the consumer group demonstrates that the ESG difference across sub-industries is meaningful, supported by an ANOVA F-statistic ≈ 7.15 (p < 0.001).

3.4 Correlation and Regression Analysis

The correlation heatmap shows a strong internal link between total ESG and environmentScore (r ≈ 0.75) and moderate correlation with governanceScore (r ≈ 0.43). Relationships between ESG and financial variables (Profit Margins, ROE, Beta, Price-to-Book) are weak, suggesting ESG behavior is largely independent from short-term financial outcomes.

A simple regression of log Market Cap on total ESG yielded a small, statistically insignificant coefficient (p ≈ 0.08). A multivariate model including financial controls confirms ESG is not a significant direct predictor of profitability, though larger firms tend to exhibit both higher profitability and higher ESG scores.

4. Discussion and Interpretation

The analysis highlights that ESG engagement differs across industries due to varying environmental impacts, stakeholder expectations, and reporting maturity. The Consumer Goods industry stands out not because of extreme ESG values, but due to its consistency and representation: with more firms adopting ESG disclosure and relatively narrow variation, this sector exemplifies institutionalized sustainability practice.

Within Consumer Goods, the contrast between Defensive and Cyclical segments reveals how necessity-driven sectors (food, household, personal care) prioritize sustainability to maintain consumer trust, whereas discretionary segments face weaker ESG pressure and show broader score dispersion.

The weak statistical linkage between ESG and profitability suggests that, while ESG adoption may not yield immediate financial advantages, it contributes to long-term brand value, risk mitigation, and reputational stability—factors especially vital in consumer-facing industries.

5. Conclusion

The study demonstrates significant variation in ESG performance across industries, with the Consumer Goods sector emerging as both sizable and sustainability-conscious. Environmental criteria drive most of the total ESG variance, while governance remains the most consistent dimension.

Our findings suggest that sector context and public accountability play crucial roles in shaping ESG engagement. Although direct correlations between ESG and financial returns remain weak, the stability and uniformity of ESG adoption in Consumer Goods imply long-term integration of sustainability into business strategy.

6. Reproducibility and Tools Used

All analyses were conducted in Google Colab using Python 3.10 with the following packages:
pandas, numpy, matplotlib, seaborn, statsmodels, requests, yfinance.
The project repository includes:

Midterm_Project.ipynb – main analysis notebook

MIDTERM_Q(1).py – summarized code version

README.md – current report

All code and data sources are openly reproducible using free API access.
