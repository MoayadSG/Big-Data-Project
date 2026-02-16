📌 Project Overview
The objective of this project is to build a full data lake pipeline to ingest, clean, and analyze large-scale synthetic datasets of weather and traffic. The project uses a multi-layer architecture (Bronze, Silver, Gold) and applies advanced analytics like Monte Carlo Simulation and Factor Analysis.

🛠 Technology Stack
Language: Python (Pandas, Scikit-learn, Streamlit, Plotly).

Infrastructure: Docker & Docker Compose.

Storage (Object Store): MinIO (S3-compatible).

Distributed Storage: Hadoop HDFS.

Data Formats: CSV (Raw) and Parquet (Processed).

🏗 Data Lake Architecture
Bronze Layer: Raw data storage in MinIO (weather_raw.csv, traffic_raw.csv).

Silver Layer: Cleaned and standardized data in Parquet format.

HDFS Layer: Distributed storage for scalability and big data processing.

Gold Layer: Final analytical datasets, daily aggregations, and joined tables for reporting.

🚀 Project Phases
1. Infrastructure & Ingestion
Setting up MinIO using Docker.

Creating buckets: bronze, silver, gold.

Ingesting raw CSV files.

2. Data Cleaning & Transformation
Handling missing values (e.g., Imputing Rainfall with Median).

Outlier detection (Filtering extreme temperatures and speeds).

Standardizing formats (Dates, Categories, and IDs).

Converting datasets to Parquet for optimized storage.

3. Advanced Analytics
Monte Carlo Simulation: Predicting traffic congestion and accident risks under 7 different weather scenarios (Heavy Rain, Extreme Heat, etc.).

Factor Analysis: Identifying latent factors like "Weather Severity" and "Traffic Flow Stress" using the FactorAnalyzer library.

4. Interactive Dashboard
A Streamlit web application was developed to visualize:

Real-time statistics and scatter plots.

Risk distribution for traffic congestion.

Correlation heatmaps of weather impact.

📊 Key Insights
Low Visibility is the leading cause of traffic congestion (approx. 69% probability).

Heavy Rain significantly increases accident risk (up to 60%).

Extreme Heat surprisingly showed a lower accident risk compared to the baseline.

⚙️ How to Run
Clone the repository.

Run docker-compose up -d to start MinIO and Hadoop.

Execute the cleaning and transformation scripts in order.

Run the dashboard using:

Bash
streamlit run dashboard/app.py