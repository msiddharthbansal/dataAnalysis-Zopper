# Data Science Internship Assessment: Zopper

## Overview
This repository contains the solution for the hiring assessment. The goal was to analyze the provided dataset, visualize key relationships, and build a predictive model to estimate store performance trends to predict January "Attach Rates" across different regions. The solution handles high-volatility data by distinguishing between **consistent performers** and **unstable stores**, applying smoothing techniques where necessary.

## Repository Structure
```text
├── plots/                  
│   ├── correlation_btw_months_heatmap.png
│   ├── distribution_plot.png
│   └── market_prediction_after_smoothing.png
│   └── performance_report.png
│   └── plot_outliers.png
│   └── trends_by_region.png
├── submission.csv
├── analysis.ipynb 
├── requirements.txt        
└── README.md               
````

## Approach & Methodology

Instead of a simple average, I implemented a robust tiered prediction logic:

### 1\. Exploratory Data Analysis (EDA)

  - **Trend Analysis:** Visualized monthly growth trends by Branch.
  - **Volatility Check:** Plotted Mean vs Standard Deviation to identify unstable stores.
  - **Correlation Decay:** Confirmed that recent months (Dec/Nov) have a much stronger correlation with the target than older months (Aug/Sep).

### 2\. Feature Engineering & Logic

  - **Weighted Prediction:** For stable stores, I used a weighted average: Prediction = (Dec x 0.5) + (Nov x 0.3) + (Oct x 0.2). This prioritizes recent performance.
  - **Outlier Smoothing:** For "Inconsistent" stores (high volatility), I applied a smoothing function:
      1) Identified stores where standard deviation > 0.20.
      2) Capped outliers that deviated > 1.5x from the median before calculating predictions .

### 3\. Key Results

  - **Star Performers:** identified stores like "Hauz Khas" as statistical outliers (positive) to be studied.
  - **Market Correction:** The model corrected aggressive spikes in December data to provide a realistic January forecast.

## Visualizations

### Correlation Heatmap

<img width="785" height="682" alt="correlation_btw_months_heatmap" src="https://github.com/msiddharthbansal/dataAnalysis-Zopper/blob/main/plots/correlation_btw_months_heatmap.png" />

### Model Performance (Projected Change: December vs January)

<img width="1012" height="547" alt="market_prediction_after_smoothing" src="https://github.com/msiddharthbansal/dataAnalysis-Zopper/blob/main/plots/market_prediction_after_smoothing.png" />


## How to Run

1.  Clone the repository:
    ```bash
    git clone https://github.com/msiddharthbansal/dataAnalysis-Zopper
    ```
2.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3.  Open the Jupyter Notebook:
    ```bash
    jupyter notebook analysis.ipynb
    ```

## 📬 Contact

**Siddharth Bansal**

  - **Email:** (msiddharth.bansal@gmail.com)
  - **LinkedIn:** (https://www.linkedin.com/in/siddharth-bansal-6b88a225a/)
