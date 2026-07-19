# Why Do Some Customers Browse But Never Buy?
### A Customer Segmentation Study Using K-Means Clustering

## Overview
Most companies assume a customer who visits their website often is close to buying. 
This project tested that assumption on real customer data and found the opposite for 
a majority of customers: the segments that browse the most spend the least, and the 
segment that spends the most barely browses at all. Four behavioural segments were 
identified using K-Means clustering, and the underlying browsing-buying gap is explored 
as a psychological rather than purely economic phenomenon — with a closing discussion 
on whether AI-driven personalisation could help close it.

## Data
2,211 customers, cleaned from the "Customer Personality Analysis" dataset, publicly 
available on Kaggle (original source attribution: Dr. Omar Romero-Hernandez). 
Rows with missing income were dropped, along with implausible values (incomes above 
$200,000, birth years before 1940). See `/data`.

## Methodology
- Feature engineering: age, total spend, total purchases, and number of children 
  derived from raw fields; combined with income, web visits, and recency into 7 features.
- All features standardised before clustering.
- K-Means tested for k=2 through k=8, evaluated via silhouette score.
- Silhouette scores peaked at k=2 (0.314) and declined steadily thereafter (k=4: 0.202).
- k=2 was not used, as it collapsed the sample into a low-vs-high spending split with 
  limited managerial value. k=4 was selected instead as the smallest cluster count that 
  separated customers on browsing behaviour as well as spend — a deliberate tradeoff 
  between statistical fit and interpretability, not the statistically "optimal" choice.

Full code: Python (pandas, scikit-learn). Dashboard: Power BI.

## Key Findings
- **High Spenders** buy the most while browsing the least (2.3 visits/month, $1,390 avg. spend).
- **Window Shoppers** and **Budget Browsers** browse 3x more than High Spenders 
  (6.0–6.9 visits/month) yet spend a fraction of the amount ($112–130).
- Age, income, and family size explain part of this pattern, but not all of it — 
  the size of the gap suggests something beyond demographics is driving it.
- The paper closes by asking whether AI-driven personalisation could close this gap, 
  and under what conditions (trust, perceived autonomy) it might backfire instead.

## Files
```
├── notebooks/
│   └── segmentation_analysis.ipynb    # Full analysis code
├── data/
│   └── marketing_campaign.csv         # Cleaned dataset
├── dashboard/
│   ├── segmentation_dashboard.pbix    # Power BI dashboard file
│   └── dashboard_screenshots/         # Static screenshots (no Power BI needed to view)
└── report/
    └── Whitepaper_Final.pdf           # Full write-up with methodology, findings, and discussion
```

## Tools
Python (pandas, scikit-learn), Power BI

## Full Report
See [Whitepaper_Final.pdf](report/Whitepaper_Final.pdf) for the complete write-up... 
justification, segment profiles, and discussion of implications for AI-driven personalisation.

## Author
Siddhant Vashishta
[LinkedIn](www.linkedin.com/in/siddhant-vashishta) · [SSRN](12256128)
