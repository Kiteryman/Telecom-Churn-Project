# Telecom-Churn-Project
- Credit & Source: Telecom Customer Churn Dataset from Maven Data Playground (https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=telecom)
## Aims & Objectives
- Help reducing the number of churned customer by providing customized offers
- Analyze the main reasons of customers turn over
- Develop machine learning models for prediction
## EDA
### i. Revenue gained from each customer status

<img width="576" alt="image" src="https://github.com/user-attachments/assets/a3a14d5a-67ea-436b-b18a-e6a7b33a96b9" />

### ii. Churned reasons overview

<img width="573" alt="image" src="https://github.com/user-attachments/assets/0c31ab0d-4f6c-41fa-93e0-2da9038034c7" />

### iii. Number of churned customers in each contract type

<img width="577" alt="image" src="https://github.com/user-attachments/assets/960fec38-becf-4bc3-9354-d521ad80caaa" />

### iv. Average number of referral from the different contract type customers

<img width="572" alt="image" src="https://github.com/user-attachments/assets/a6943cd4-dad2-4d48-9dbe-440bec0bfbc7" />

### v. Proportion of churned customers that have subscribed to premium tech support

<img width="586" alt="image" src="https://github.com/user-attachments/assets/fe439271-f18a-40d2-b565-4f82a73e1e09" />

### vi. Distribution of data usage

<img width="605" alt="image" src="https://github.com/user-attachments/assets/073780b9-b322-4337-b092-6e9d0508fcaf" />

### vii. Revenue per city and distinguish whether the city with high revenue also has high churn number

<img width="1067" alt="image" src="https://github.com/user-attachments/assets/261e64a2-0519-4b1f-a724-26124406681a" />
<img width="1059" alt="image" src="https://github.com/user-attachments/assets/adcaae04-3b75-45e0-9efc-7a245e27e640" />

### viii. Correlation of number of user and the population size
<img width="591" alt="image" src="https://github.com/user-attachments/assets/a27955b4-4bf6-483a-92bc-1d3f2bc6732e" />

### ix. Correlation of total number of user and the churned number
<img width="597" alt="image" src="https://github.com/user-attachments/assets/e688f2cc-d674-4218-b46a-65f4a896dfba" />

### x. Proportion of churned customers and the churned cash flow
<img width="448" alt="image" src="https://github.com/user-attachments/assets/7ee3c583-173a-40a3-9cfc-ff598fbcd0c3" />

### xi. Distinguish whether the company loses any high value customer
<img width="646" alt="image" src="https://github.com/user-attachments/assets/47605c1f-6c33-4a30-b458-68c4661f08dd" />

#### Findings through EDA：
- Around 26.54% of the customer churned because of the competitors and poor service quality, and the churned customers contribute to 17.2% of the total revenue of the fiscal year
- Among all the churned customers, most of them are with short-term contract (Month-to-month contract)
- Long-term/loyal customers tend to refer more people (May know the service quality through time and get positive impression)
- Most of the customers consume around 20 - 30GB data per month on average
- Most of the customers subscribed to the premium technical support but they still got poor experience on the service support
- Cities with high revenue does not mean there is large number of churned customers, whcih mean that the revenue and the correlation between revenue and churned customers may not be too strong
- Number of population and the users are not necessary correlated
- The company indeed loses valuable customers with whom contribute over 10-thousand dollars each year per customers
- Recommendation：Regarding the poor expertise for support, on-job training is highly recommended for better user experience (More Advice in Unsupervised Learning Section)

## Unsupervised Learning
### 1. Clustering

<img width="521" alt="image" src="https://github.com/user-attachments/assets/558bbf44-3c13-403d-bd3a-f9150da2faaf" />

- Cluster 0: Entertainment enthuasiasts without long distance line service
- Cluster 1: Non-entertainment users with long distance line service
- Cluster 2: Entertainment enthuasiasts with long distance line service
- Cluster 3: Heavy data usage customers without long distance line service

**Original Goal:** Help reducing churned customers

**Recommendation:** Provide value-added service for each customer profile below:

- Entertainment enthuasiasts without long distance service: Provide offers with combination of more diverse free entertainment platforms access
- Non-entertainment users with long distance service: Provide offers with free long-distance service limit for each month
- Entertainment enthuasiasts with long distance service: Suggest customers upgrading to taylor-made plan for unlimited service assess without significant price boost
- Heavy data usage customers without long distance service: Provide offers with data-oriented package for customers

### 2. DBScan (For filtering out outliers)

<img width="612" alt="image" src="https://github.com/user-attachments/assets/cb51505a-c0bf-4863-ae98-a0840a0c3f80" />

Choose the final DBScan model as Eps = 1.9 and Min Samples = 7

### 3. PCA

<img width="319" alt="image" src="https://github.com/user-attachments/assets/cb63c922-f0b4-4321-aee4-01a28fac7aa2" />

Total 83.952% of variance is captured by the PCs

**PCs Explanation:**
- PC1: higher = more likely to have more entertainment and subscribe to additional services (high-value, multi-service subscribers)
- PC2: higher = higher tenure in months and more service charges on customers and more company revenue but less add-ons (long-tenured, higher total revenue, but fewer add-ons)
- PC3: higher = customers is more likely to have one year contract

### 4. T-SNE Plots for PCs

<img width="589" alt="image" src="https://github.com/user-attachments/assets/911a5bce-c340-449b-ac7b-23466150d643" />
<img width="587" alt="image" src="https://github.com/user-attachments/assets/6bc00583-b42e-43af-a7a3-bf61844ad7a3" />
<img width="588" alt="image" src="https://github.com/user-attachments/assets/53a33ff5-7b26-43c2-bfaf-b8405ecb7edb" />

- There is no perfect class separation for the T-SNE plots, this may indicate there may be non-linear relationship between PCs

### 5. Supervised Learning
#### i.) Correlation Matrix
<img width="534" alt="image" src="https://github.com/user-attachments/assets/b243b1a6-189c-4a07-bc05-bc0fa1ab706e" />

- Weak to moderate correlation between PC2 and Customer Status

#### ii.) K-Nearest Neighbor
<img width="197" alt="image" src="https://github.com/user-attachments/assets/66a1f9ec-5171-4ad6-8857-f1d00a60bf22" />
<img width="243" alt="image" src="https://github.com/user-attachments/assets/cead36a0-97ad-41ee-8b06-381ade72cd03" />
<img width="518" alt="image" src="https://github.com/user-attachments/assets/1736bb84-330b-4a68-ae05-2275e9c1bfd5" />

- Model accuracy, precision, recall and f1 score are 81.3%, 66.7%, 59.4% and 62.8% respectively

#### iii.) Logistic Regression


