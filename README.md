# Telecom-Churn-Project
- Credit & Source: Telecom Customer Churn Dataset from Maven Data Playground (https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=telecom)
## Aims & Objectives
- Help reducing the number of churned customer by providing customized offers
- Analyze the main reasons of customers turn over
- Develop machine learning models for prediction
## EDA
### i. Revenue gained from each customer status

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/a3a14d5a-67ea-436b-b18a-e6a7b33a96b9" />

### ii. Churned reasons overview

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/0c31ab0d-4f6c-41fa-93e0-2da9038034c7" />

### iii. Number of churned customers in each contract type

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/960fec38-becf-4bc3-9354-d521ad80caaa" />

### iv. Average number of referral from the different contract type customers

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/a6943cd4-dad2-4d48-9dbe-440bec0bfbc7" />

### v. Proportion of churned customers that have subscribed to premium tech support

<img width="700" height="400" alt="image" src="https://github.com/user-attachments/assets/fe439271-f18a-40d2-b565-4f82a73e1e09" />

### vi. Distribution of data usage

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/073780b9-b322-4337-b092-6e9d0508fcaf" />

### vii. Revenue per city and distinguish whether the city with high revenue also has high churn number

<img width="1100" height="1000" alt="image" src="https://github.com/user-attachments/assets/261e64a2-0519-4b1f-a724-26124406681a" />
<img width="1100" height="1000" alt="image" src="https://github.com/user-attachments/assets/adcaae04-3b75-45e0-9efc-7a245e27e640" />

### viii. Correlation of number of user and the population size
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/a27955b4-4bf6-483a-92bc-1d3f2bc6732e" />

### ix. Correlation of total number of user and the churned number
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/e688f2cc-d674-4218-b46a-65f4a896dfba" />

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

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/558bbf44-3c13-403d-bd3a-f9150da2faaf" />

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

<img width="300" height="100" alt="image" src="https://github.com/user-attachments/assets/cb63c922-f0b4-4321-aee4-01a28fac7aa2" />

Total 83.952% of variance is captured by the PCs

**PCs Explanation:**
- PC1: higher = more likely to have more entertainment and subscribe to additional services (high-value, multi-service subscribers)
- PC2: higher = higher tenure in months and more service charges on customers and more company revenue but less add-ons (long-tenured, higher total revenue, but fewer add-ons)
- PC3: higher = customers is more likely to have one year contract

### 4. T-SNE Plots for PCs

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/911a5bce-c340-449b-ac7b-23466150d643" />
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/6bc00583-b42e-43af-a7a3-bf61844ad7a3" />
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/53a33ff5-7b26-43c2-bfaf-b8405ecb7edb" />

- There is no perfect class separation for the T-SNE plots, this may indicate there may be non-linear relationship between PCs

### 5. Supervised Learning
#### i.) Correlation Matrix
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/b243b1a6-189c-4a07-bc05-bc0fa1ab706e" />

- Weak to moderate correlation between PC2 and Customer Status

#### ii.) K-Nearest Neighbor
<p align="left">
  <img width="150" alt="image" src="https://github.com/user-attachments/assets/b4fabb9f-f349-4098-89c7-5b1bb28e835b" />
</p>
<p align="left">
  <img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/1736bb84-330b-4a68-ae05-2275e9c1bfd5" />
</p>

- Model accuracy, precision, recall and f1 score are 81.3%, 66.7%, 59.4% and 62.8% respectively

<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/8407de48-9d01-4a43-bc27-d6f23b0d631c" />
</p>

- The KNN model could get around 0.8 true positive rate while introducing around 0.2 false positive prediction

<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/7c6808de-48d3-4cc1-90f9-c8659935d11d" />
</p>
<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/a19f78e1-e482-4625-bb24-4a4ed965125c" />
</p>

- The F1-Score is maximized at the threshold of about 0.38

#### iii.) Logistic Regression

$$
\text{Logit}(p) = \log\Bigl(\frac{p}{1 - p}\Bigr) = -1.32868 + 0.221613 \cdot \mathrm{PC1} - 0.549782 \cdot \mathrm{PC2} -  0.108749 \cdot \mathrm{PC3}
$$

- When holding other variables constant, one unit increase in PC1 will cause the odds of being churned increase by 1.249
- When holding other variables constant, one unit increase in PC2 will cause the odds of being churned decrease by 1.733
- When holding other variables constant, one unit increase in PC3 will cause the odds of being churned decrease by 1.115

<p align="left">
<img width="150" alt="image" src="https://github.com/user-attachments/assets/2fa31d3b-302a-461a-a1fa-ca57b575f30d" />
</p>
<p align="left">
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/f34dbf65-daeb-4cc0-b135-e82ed28e02a8" />
</p>

- Model accuracy, precision, recall and f1 score are 76.1%, 58.1%, 36.4% and 44.7% respectively

<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/f021a742-d05c-4e4d-9cdb-30d81b87ec28" />
</p>

- The LR model could get around 0.7 true positive rate while introducing around 0.3 false positive rate

<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/669f9db8-4688-4bb3-a224-bb138c49340e" />
</p>
<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/3f9ee077-83d6-468b-b271-b6479cc24d63" />
</p>

- The F1-Score is maximized at the threshold of about 0.37

<p align="left">
<img width="260" alt="image" src="https://github.com/user-attachments/assets/7672a3d7-7ed7-4a09-b87a-3748a341358e" />
</p>

- The precision, recall and F1-Socre are 0.518, 0.650 and 0.577 when the threshold is set to 0.37, which is a massive increment

#### iv.) Random Forest

<p align="left">
<img width="150" alt="image" src="https://github.com/user-attachments/assets/ffa79126-20f7-4507-bd96-d49b5e14010f" />
</p>
<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/c3f6e104-c84e-4137-8ce6-351e9337fa8c" />
</p>

- Model accuracy, precision, recall and f1 score are 80.5%, 68.0%, 50.5% and 58.0% respectively

<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/ec75c853-375b-49bf-882a-a5d95676b950" />
</p>

- The RF model could get around 0.8 true positive rate while introducing around 0.25 false positive rate

<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/ea94bdd5-03a3-43db-a9e7-90bd9d19eec0" />
</p>
<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/f0f2728c-c1e1-4bfe-8ee2-d0dc398d51cf" />
</p>

- The F1-Score is maximized at the threshold of about 0.35

<p align="left">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/863585cd-7ca2-4db4-a675-3cf38b6bb561" />
</p>

- The PC3 is the most important feature which indicates the length of contract period being one year, but it does not show a significant relationship with the label (Customer Status)

v. Support Vector Machine

<p align="left">
<img width="150" alt="image" src="https://github.com/user-attachments/assets/2c6469d7-60aa-4bbc-a83d-8b5a1a18e728" />
</p>
<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/2bcb2763-bb4a-4d85-8cd5-c9e393b22ed4" />
</p>

- Model accuracy, precision, recall and f1 score are 81.4%, 71.2%, 50.3% and 58.9% respectively

<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/4c2e982a-acba-4995-91a2-e30ea43a0a37" />
</p>

- The SVM model could get around 0.8 true positive rate while introducing around 0.25 false positive rate

<p align="left">
<img width="600" height="500" alt="image" src="https://github.com/user-attachments/assets/a998d797-465c-45a6-b2a1-cf3147e5e5df" />
</p>
<p align="left">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/8ac3850f-8ee7-409f-a390-361e35c2077a" />
</p>

- The F1-Score is maximized at the threshold of about 0.16

### 6. Model Evaluation
- Customer retention can be costly when implementing customized offers. In this case, the precision score is the primary concern, and an SVM model could provide the best precision
- For general performance, when striving for a balance between precision and recall, KNN works as the best solution since it provides decent accuracy while achieving moderately high precision and recall scores
- Since the prediction variables are principal components (PCs), which do not capture all the variance in the true sample data, the performance metrics may not be as good as when using the original data. However, PCs are still used because they significantly reduce the dimensionality, mitigating the curse of dimensionality that could affect the models
