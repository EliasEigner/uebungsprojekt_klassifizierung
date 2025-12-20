# Smart Office Occupancy Forecasting
### An End-to-End Machine Learning Pipeline for HVAC Energy Optimization

## Project Overview
Buildings account for a significant portion of global energy consumption, particularly through Heating, Ventilation, and Air Conditioning (HVAC) systems. This project implements a predictive machine learning pipeline to detect room occupancy based on IoT sensor data. 

**The Goal:** By accurately forecasting whether a room is occupied, building management systems can dynamically adjust energy usage, significantly reducing costs while maintaining user comfort.

## Key Features
* **Time-Series Data Engineering:** * Robust handling of sensor drift and time-alignment (rounding to nearest minute).
    * Outlier detection logic for unphysical sensor readings (e.g., temperature spikes > 50°C).
    * Linear interpolation and backwards filling for missing values to maintain time-series integrity.
* **Advanced Feature Engineering:**
    * **Cyclic Time Encoding:** Transforming timestamps into Sine and Cosine waves to represent the circular nature of a 24-hour day.
    * **Physical Trends ($CO_2$ Delta):** Implementing 15-minute lag features to capture the rapid $CO_2$ increase associated with room entry.
    * **Domain Integration:** Automated holiday detection using the `holidays` library and defined core office hours.
* **Modeling & Validation:**
    * Comparative benchmarking of **Logistic Regression**, **Random Forest**, and **Histogram-based Gradient Boosting**.
    * Use of `TimeSeriesSplit` to prevent data leakage and ensure the model generalizes well over chronological data.

## Economic Evaluation & KPI Validation
* **Threshold Tuning:** A custom logic that balances energy costs (€) against user comfort (minutes of "freezing" per day).
* **KPI Metrics:** Validation based on Accuracy, ROC-AUC, and specifically **Recall** to minimize False Negatives (improving user satisfaction).
* **Cost-Benefit Analysis:** Calculating the actual heating runtime and associated costs for each model to identify the most efficient solution.

## Tech Stack
* **Language:** Python 3.13
* **Libraries:** `scikit-learn`, `pandas`, `numpy`, `plotly`, `holidays`

## Project Origin & Acknowledgements
This project was developed within the **"Data Mining & Machine Learning 1"** module at **Karlsruhe University of Applied Sciences (HKA)**.
* **Authors:** Markus & Govind & Elias
* **Academic Context:** B.Sc. Data Science, Winter 2025/26
* **Data Source:** Provided by the faculty for academic use case development.
