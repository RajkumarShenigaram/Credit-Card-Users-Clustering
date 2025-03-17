# Credit Card Clustering (Unsupervised Learning)

## Overview  
This project involves **clustering credit card customers** to identify distinct **customer segments** based on their **spending behavior** and **interaction patterns** with the bank. The results will help the **Marketing Team** to **personalize campaigns** and the **Operations Team** to **enhance customer support services**.

## Objective  
- Segment existing customers based on their **spending behavior** and **interaction frequency** with the bank.
- Provide actionable insights for **targeted marketing campaigns** and **improved service delivery**.

## Dataset Description  
The dataset consists of **credit card customer data** with the following features:

### Features  
- **Sl_No**: Serial number (not used in analysis).  
- **Customer Key**: Unique customer identifier.  
- **Avg_Credit_Limit**: The average credit limit per customer.  
- **Total_Credit_Cards**: The total number of credit cards a customer owns.  
- **Total_visits_bank**: Number of in-person visits to the bank.  
- **Total_visits_online**: Number of online banking visits.  
- **Total_calls_made**: Number of calls made to customer service.  

## Project Workflow  

### 1. Data Preprocessing  
- Identified **duplicate customer keys** and removed them.  
- Dropped unnecessary columns (**Sl_No**, **Customer Key**).  
- Removed **exact duplicate rows** to avoid redundant data.  
- **Converted categorical data** where necessary.  

### 2. Exploratory Data Analysis (EDA)  
- **Summary Statistics**:
  - **Avg_Credit_Limit** is **right-skewed**, indicating a few high-limit customers.  
  - Customers typically own **3 to 6 credit cards**.  
  - **Most customers use one primary contact method** (bank visits, online banking, or phone calls).  

- **Correlation Analysis**:
  - **Avg_Credit_Limit is positively correlated with Total_Credit_Cards**.  
  - **Avg_Credit_Limit is negatively correlated with Total_calls_made and Total_visits_bank**.  
  - Customers **prefer a single contact method** rather than using multiple channels.  

### 3. Data Scaling  
- Applied **Z-score normalization** using `StandardScaler()` to scale all features for clustering.

## Clustering Techniques  

### 1. K-Means Clustering  
- Used the **Elbow Method** to determine **optimal clusters (k=3)**.  
- **Reason for choosing k=3**:
  - The **Sum of Squared Errors (SSE) dropped significantly** at k=3, indicating a strong clustering structure.  
- **Why scaling is needed?**  
  - K-Means uses **Euclidean distance**, and unscaled features would lead to bias toward larger magnitude values.  

#### **K-Means Cluster Profiles**  
- **Cluster 0**: Moderate credit limits, balanced banking habits, and an **average level of engagement**.  
- **Cluster 1**: **Low-value customers** with low credit limits, minimal online activity, and **higher reliance on in-person banking**.  
- **Cluster 2**: **High-value customers** with **high credit limits**, more credit cards, and a preference for **online banking**.  

### 2. Gaussian Mixture Model (GMM) Clustering  
- Applied **Gaussian Mixture Model (GMM)** clustering with **k=3**.  
- The **GMM clusters were similar to K-Means**.  

#### **GMM Cluster Profiles**  
- **Cluster 0**: Low-credit limit customers, relying mainly on phone banking.  
- **Cluster 1**: Moderate-credit limit customers with a balance between **bank visits and online banking**.  
- **Cluster 2**: High-credit limit customers, highly engaged with **online banking services**.  

### 3. K-Medoids Clustering  
- Applied **K-Medoids clustering with k=3**.  
- **K-Medoids was more robust to outliers compared to K-Means**.  

#### **K-Medoids Cluster Profiles**  
- **Cluster 0**: Low average credit limits, minimal credit cards, and preference for **phone support**.  
- **Cluster 1**: High credit limits, multiple credit cards, and heavy **online banking usage**.  
- **Cluster 2**: Moderate credit limits, average credit card ownership, and **preference for in-person banking**.  

## Comparison of Clustering Results  

| Cluster Model  | Low-Value Customers | Mid-Value Customers | High-Value Customers |
|---------------|--------------------|--------------------|--------------------|
| **K-Means**   | Prefers in-person banking, low credit cards | Moderate habits, balanced engagement | High credit limit, digital-first customers |
| **GMM**       | Prefers phone banking, low engagement | Balanced between online and in-person banking | High online banking usage |
| **K-Medoids** | Prefers phone banking, low credit limit | Moderate credit usage, in-person banking | High credit limits, prefers online services |

## Key Findings & Business Recommendations  
- **High-value customers (Cluster 2) prefer online banking** → The bank should focus on **enhancing digital experience and security**.  
- **Low-value customers (Cluster 1) rely on traditional banking methods** → Improve **in-person customer service** and streamline **phone support**.  
- **Cart abandonment in high-value customers is a concern** → The bank can offer **incentives for completing online transactions**.  
- **Personalized marketing campaigns** can be targeted at each customer segment to improve **engagement and retention**.  

## Author  
Rajkumar Shenigaram  

