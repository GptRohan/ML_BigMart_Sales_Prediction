# 🛒 BigMart Sales Forecasting Pipeline  

This project showcases a complete **Data Engineering + Machine Learning pipeline** using BigMart retail sales data.  
It includes **automated data ingestion, MySQL database setup, feature engineering, model training, and deployment** via a **Streamlit web app**.  

👉 **Live Demo**: https://mlprojectbigmartsalesprediction-codewithrohan.streamlit.app/
---

## 🧱 Architecture Overview  

```mermaid
flowchart LR
    %% ========= Ingestion =========
    subgraph A[📥 Data Ingestion]
        A1[📄 df_item.xml] --> A4[(🗄️ MySQL: item_info)]
        A2[📄 df_outlet.xml] --> A5[(🗄️ MySQL: outlet_info)]
        A3[📄 df_sales.xml] --> A6[(🗄️ MySQL: sales_info)]
    end

    %% ========= Processing =========
    subgraph B[⚙️ Data Processing]
        A4 --> B1[🔗 Merge Tables]
        A5 --> B1
        A6 --> B1
        B1 --> B2[🧹 Cleaning & Feature Engineering]
        B2 --> B3[✂️ Train/Test Split]
    end

    %% ========= Modeling =========
    subgraph C[🤖 Model Training]
        B3 --> C1[📈 GradientBoostingRegressor]
        C1 --> C2[💾 Save: bigmart_best_model.pkl]
    end

    %% ========= Deployment =========
    subgraph D[🚀 Deployment]
        C2 --> D1[🌐 Streamlit App]
        D1 --> D2[📊 Predict Sales & Show Results]
    end

    %% ========= Styling =========
    classDef data fill:#E3F2FD,stroke:#1565C0,stroke-width:2px,color:#0D47A1;
    classDef process fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px,color:#1B5E20;
    classDef model fill:#FFF3E0,stroke:#EF6C00,stroke-width:2px,color:#E65100;
    classDef deploy fill:#FCE4EC,stroke:#AD1457,stroke-width:2px,color:#880E4F;

    class A1,A2,A3,A4,A5,A6 data;
    class B1,B2,B3 process;
    class C1,C2 model;
    class D1,D2 deploy;

