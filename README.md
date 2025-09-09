# 🔍 Anomaly Detection and Fraud Analysis in Metaverse Transactions

## 📌 Problem Statement  
With the rapid growth of metaverse platforms, transaction volumes have surged—making them attractive targets for fraud, scams, and suspicious activities. Traditional rule-based fraud detection systems often fail to capture **rare, contextual, or evolving anomalies** hidden in user behavior.  

This project focuses on **unsupervised anomaly detection** in metaverse transactions. By leveraging advanced machine learning algorithms, the aim is to identify anomalous activities that could indicate fraud, money laundering, or abnormal behavioral patterns, thereby strengthening trust and security in virtual economies.  

---

## 📊 Dataset  
The dataset consists of **78,600 metaverse transactions** with attributes capturing transactional, behavioral, and contextual information:  

- **Timestamp**: Date and time of the transaction  
- **Hour of Day**: Hour extracted from the timestamp  
- **Sending Address**: Blockchain address of the sender  
- **Receiving Address**: Blockchain address of the receiver  
- **Amount**: Transaction amount in simulated currency  
- **Transaction Type**: Categorization (e.g., transfer, sale, purchase, scam, phishing)  
- **Location Region**: Simulated geographical region of the transaction  
- **IP Prefix**: Simulated IP address prefix  
- **Login Frequency**: User login frequency (varies by age group)  
- **Session Duration**: Duration of activity sessions (minutes)  
- **Purchase Pattern**: Behavioral pattern of purchases (focused, random, high-value)  
- **Age Group**: User activity categorization (new, established, veteran)  
- **Risk Score**: Calculated transaction risk score *(dropped for modeling)*  
- **Anomaly**: Risk-level assessment *(dropped for modeling)*  

> ⚠️ **Note**: Features `Risk Score` and `Anomaly` were **dropped** to ensure the detection framework learns anomalies directly from raw attributes, avoiding label leakage.

---

## 🚀 Approach  

1. **Preprocessing**  
   - Extracted numerical and categorical features from raw transaction data.  
   - Standardized numerical attributes to ensure balanced influence across models.  

2. **Unsupervised Anomaly Detection Models**  
   - **Isolation Forest (IF):** Detects anomalies by isolating observations in random partitions.  
   - **Local Outlier Factor (LOF):** Captures local density deviations, effective in spotting *contextual anomalies*.  
   - **ECOD (Empirical Cumulative Distribution Outlier Detection):** Non-parametric model leveraging feature-wise tail probabilities, robust for heterogeneous data.  

3. **Consensus Anomaly Detection**
   - Generated anomaly sets from each model separately.
   - Flagged transactions as high-confidence anomalies when consistently detected across multiple methods.
   - Quantified model agreement using Jaccard similarity, highlighting overlap and consensus strength.

4. **Explainability (SHAP)**  
   - Applied SHAP values on consensus-flagged anomalies.  
   - Generated **summary plots** and **waterfall plots** to highlight key drivers of suspicious activity.  

---

## 📈 Impact  

- ✅ ECOD model (3,530 anomalies) showed the strongest statistical separation among the three models.
- ✅ Enhanced **investigation efficiency** by providing **SHAP-based feature attributions**, which reduced manual probing and accelerated decision-making. 
- ✅ Provided analysts with actionable insights on **which features contributed most to anomalous flags** (e.g., unusual transaction amount, login frequency patterns, region-specific anomalies).  

---

## 🔮 Future Improvements  

- **Model Deployment**: Wrap anomaly detection into a deployable API for real-time transaction monitoring.  
- **Deep Learning**: Introduce **Autoencoders** and **Variational Autoencoders** for advanced anomaly representation.  
- **LLM + RAG for Analysts**:  
  - Use LLMs to convert model outputs into **human-friendly explanations**.  
  - Imagine a chatbot where an analyst can query:  
    > *“Show me all high-risk transactions from yesterday in regions with unusually high amounts.”*  
  - The system retrieves anomalies with natural language interaction, bridging the gap between **data science outputs and business insights**.  

---

## 🛠️ Tech Stack  
- **Python**: Data processing & modeling  
- **Scikit-learn**: Isolation Forest, LOF  
- **PyOD**: ECOD  
- **SHAP**: Explainability  
- **Matplotlib / Seaborn**: Visualization  

---
