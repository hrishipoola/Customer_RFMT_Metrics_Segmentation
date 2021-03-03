# Customer RFMT Metrics & Segmentation

## 1. Introduction

Today, we'll construct recency, frequency, monetary value, and tenure (RFMT) metrics and segments using Brazilian ecommerce marketplace [Olist's sales transactions data](https://www.kaggle.com/olistbr/brazilian-ecommerce?select=olist_orders_dataset.csv) dating from October 2016 to October 2018. 

RFMT metrics can be used to segment customers in order to identify which customers are responsive to marketing, engaged, contribute to churn, high spenders vs. low-value purchasers, or have upselling or cross-selling potential. Understanding segments can help us better tailor product, sales, and marketing activities and investments. For example, at-risk customers may have high monetary value and frequency, but weak recency and could be targeted with promotions and renewals. In our case, we'll define our metrics as:

- Recency: days since last transaction (delivery)
- Frequency: number of transactions during time period
- Monetary value: total spend during time period
- Tenure: days since first purchase order 

To construct RFMT metrics, we'll need order id, purchase history, order status, delivery dates, and spend details by unique customer id. Olist's data schema shows that the orders data set contains unique customer ids, order status, and delivery dates, while the payments data set contains spend. Let's merge these two data sets together on order id to get what we need. 

We'll use RFMT metrics to segment customers, first manually by building RFMT scores along with arbitrary cutoffs and then using K-means clustering to uncover segemnts in the data (an alternative to K-means would be non-zero matrix factorization (NMF)). We'll then compare our 4 resulting segments and relative importance of segment metrics. 

Future areas to explore:

- Tailor metrics to product categories. For example, we could weight R and F higher and M lower for FMCG (e.g., cosmetics, headphones), while weighting M higher and R and F lower for durable goods (e.g., washing machines)
- Merge [marketing funnel data set](https://www.kaggle.com/olistbr/marketing-funnel-olist/home) to understand and model how customer journey shapes purchasing behavior 
