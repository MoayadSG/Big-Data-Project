# 🚦 Urban Traffic Analytics Under Weather Conditions
### Modern Data Lake & Predictive Analysis Pipeline (London Smart City Project)

## 📌 Project Overview
The goal of this project is to analyze how weather conditions (rain, temperature extremes, humidity, wind, and visibility) influence urban traffic behavior and congestion levels in **London**. We built a full predictive data lake pipeline to ingest, clean, and analyze large-scale synthetic datasets.



## 🏗 Data Lake Architecture
The system follows a three-layer data lake architecture using **MinIO**, with an additional **HDFS** integration layer:
* **Bronze Layer:** Raw synthetic data in CSV format.
* **Silver Layer:** Cleaned and structured data in Parquet format.
* **HDFS Layer:** Distributed storage for scalability.
* **Gold Layer:** Final analytical results, simulations, and reports.



## 🛠 Technology Stack
| Category | Tools |
| :--- | :--- |
| **Infrastructure** | Docker, MinIO, HDFS |
| **Programming** | Python (Pandas, Scikit-learn, FactorAnalyzer) |
| **Data Formats** | CSV (Raw), Parquet (Processed) |
| **Analysis** | Monte Carlo Simulation, Factor Analysis |
| **Visualization** | Streamlit / Plotly |

## 🚀 Project Phases

### Phase 1: Infrastructure & Ingestion (Bronze)
* Containerized environment using **Docker Compose**.
* Setup of MinIO buckets: `bronze`, `silver`, and `gold`.
* Ingestion of raw `weather_raw.csv` and `traffic_raw.csv`.

### Phase 2: Data Cleaning (Bronze → Silver)
Handled messy real-world data issues:
* **Weather:** Fixed IDs, parsed mixed date formats, and handled outliers (e.g., Temp -30°C to 60°C).
* **Traffic:** Corrected negative speeds, capped extreme vehicle counts, and standardized congestion levels.
* **Output:** All data converted to **Parquet** for high-performance reads.

### Phase 3: HDFS Integration
Replicated the Silver layer data to a **Hadoop HDFS** cluster (NameNode & DataNode) to ensure distributed processing capabilities.

### Phase 4: Dataset Merging
Unified weather and traffic datasets via an **Inner Join** on `date_time` and `city` to create a master analytical table.

### Phase 5: Monte Carlo Simulation
Simulated 10,000+ scenarios to predict:
* **Traffic Jam Probability:** Highest risk identified during "Low Visibility" (69%).
* **Accident Risk:** "Heavy Rain" increased risk by 13% over the baseline.

### Phase 6: Factor Analysis
Applied dimensionality reduction to identify 3 latent factors:
1.  **Weather Severity:** (Rain, Wind, Visibility).
2.  **Traffic Flow Stress:** (Vehicle Count, Speed).
3.  **Accident Risk Factor:** (Accident Counts).

### Phase 7: Interactive Dashboard
Developed a **Streamlit** dashboard to visualize:
* Data Quality Metrics.
* Scenario-based Risk Distributions.
* Correlation Heatmaps.

## 📊 Key Insights & Recommendations
* **Visibility** is the strongest driver of congestion; smart lighting is recommended.
* **Heavy Rain** is the primary driver of accidents; adaptive speed limits should be enforced.
* **Extreme Heat** correlates with lower traffic complexity.
