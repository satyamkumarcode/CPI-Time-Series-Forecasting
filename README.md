# Time Series Forecasting: All India Consumer Price Index Analysis

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> A comprehensive time series analysis and forecasting project on India's Consumer Price Index (CPI) using ARIMA modeling techniques.

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Methodology](#methodology)
- [Results](#results)
- [Visualizations](#visualizations)
- [Technologies Used](#technologies-used)
- [Key Findings](#key-findings)
- [Future Enhancements](#future-enhancements)
- [Contributing](#contributing)
- [Author](#author)
- [License](#license)

## 🎯 Overview

This project implements a robust time series forecasting model to predict India's Consumer Price Index (CPI) using historical data from January 2013 to June 2020. The analysis employs ARIMA (AutoRegressive Integrated Moving Average) modeling to capture inflation trends and generate accurate forecasts.

**Key Highlights:**
- ✅ Achieved **95.39%** model accuracy
- ✅ MAPE of only **4.61%**
- ✅ 12-month ahead forecasting capability
- ✅ Comprehensive exploratory data analysis
- ✅ Systematic model selection using AIC

## 📊 Dataset

**Source:** All India Consumer Price Index (Rural + Urban Combined)

**Dataset Link:** [All India CPI Data](https://raw.githubusercontent.com/satyamkumarcode/delhi_aqi/refs/heads/main/All_India_Index_july2019_20Aug2020.csv)

**Details:**
- **Time Period:** January 2013 - June 2020
- **Observations:** 87 monthly data points
- **Sector:** Rural + Urban Combined
- **Data Quality:** Clean, no missing values
- **CPI Range:** 104.6 (Jan 2013) to 151.8 (Jun 2020)

## 📁 Project Structure
```
CPI-Time-Series-Forecasting/
│
├── CPI_TimeSeries_Analysis__1_.ipynb    # Main Jupyter notebook
├── TSF_Assignment_Report.docx            # Detailed project report
├── data/                                  # Dataset directory
│   └── All_India_Index_july2019_20Aug2020.csv
├── images/                                # Visualization outputs
│   ├── original_timeseries.png
│   ├── rolling_statistics.png
│   ├── seasonal_decomposition.png
│   ├── acf_pacf_plots.png
│   ├── forecast_plot.png
│   └── residual_analysis.png
├── requirements.txt                       # Python dependencies
├── README.md                              # Project documentation
└── LICENSE                                # License file
```

## 🛠️ Installation

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook
- Git

### Setup Instructions

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/CPI-Time-Series-Forecasting.git
cd CPI-Time-Series-Forecasting
```

2. **Create a virtual environment** (recommended)
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install required packages**
```bash
pip install -r requirements.txt
```

4. **Launch Jupyter Notebook**
```bash
jupyter notebook CPI_TimeSeries_Analysis__1_.ipynb
```

## 🚀 Usage

### Running the Analysis

1. Open the Jupyter notebook:
```bash
jupyter notebook CPI_TimeSeries_Analysis__1_.ipynb
```

2. Run all cells sequentially to:
   - Load and explore the dataset
   - Perform stationarity tests
   - Conduct seasonal decomposition
   - Select optimal ARIMA parameters
   - Train the model
   - Generate forecasts
   - Evaluate model performance

### Quick Start Example
```python
import pandas as pd
from statsmodels.tsa.arima.model import ARIMA

# Load data
url = 'https://raw.githubusercontent.com/satyamkumarcode/delhi_aqi/refs/heads/main/All_India_Index_july2019_20Aug2020.csv'
df = pd.read_csv(url)

# Filter Rural+Urban sector
ts = df[df['Sector'] == 'Rural+Urban']['General index']

# Fit ARIMA model
model = ARIMA(ts, order=(1, 1, 0))
fitted_model = model.fit()

# Generate forecast
forecast = fitted_model.forecast(steps=12)
print(forecast)
```

## 🔬 Methodology

### 1. Data Preparation
- Data loading and cleaning
- Date parsing and indexing
- Sector filtering (Rural + Urban Combined)

### 2. Exploratory Data Analysis (EDA)
- Time series visualization
- Rolling statistics analysis
- Seasonal decomposition
- Trend identification

### 3. Stationarity Testing
- Augmented Dickey-Fuller (ADF) test
- First-order differencing
- Validation of stationarity

### 4. Model Selection
- ACF and PACF analysis
- Grid search over ARIMA parameters (p, d, q)
- AIC-based optimization
- **Selected Model:** ARIMA(1, 1, 0)

### 5. Model Training & Validation
- Train-test split (80-20)
- Model fitting on training data
- Performance evaluation on test set

### 6. Forecasting
- Test set predictions
- 12-month ahead forecasts
- Confidence interval estimation

### 7. Model Evaluation
- Residual analysis
- Error metrics calculation (MAE, MSE, RMSE, MAPE)
- Model validation

## 📈 Results

### Performance Metrics

| Metric | Value |
|--------|-------|
| Mean Absolute Error (MAE) | 7.23 |
| Root Mean Square Error (RMSE) | 8.18 |
| Mean Absolute Percentage Error (MAPE) | 4.61% |
| **Model Accuracy** | **95.39%** |

### Historical Analysis

| Metric | Value |
|--------|-------|
| Total Inflation (2013-2020) | 45.12% |
| Annual Average Inflation | 6.09% |
| Training Set | 70 months (80%) |
| Testing Set | 17 months (20%) |

### Future Forecast

- **Forecast Period:** July 2020 - June 2021 (12 months)
- **Predicted CPI Range:** 153.73 - 156.66
- **Expected Inflation:** ~1.9% over forecast period

## 📊 Visualizations

The project includes comprehensive visualizations:

1. **Original Time Series Plot**
   - Displays CPI trend from 2013-2020

2. **Rolling Statistics**
   - Rolling mean and standard deviation

3. **Seasonal Decomposition**
   - Trend, seasonal, and residual components

4. **ACF & PACF Plots**
   - Autocorrelation analysis for parameter selection

5. **Training & Testing Forecasts**
   - Model predictions vs actual values

6. **Residual Analysis**
   - Error distribution and randomness check

7. **Future Forecast Plot**
   - 12-month ahead predictions with confidence intervals

## 💻 Technologies Used

- **Python 3.8+**
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **matplotlib** - Data visualization
- **seaborn** - Statistical data visualization
- **statsmodels** - Statistical modeling and time series analysis
- **scikit-learn** - Machine learning metrics
- **jupyter** - Interactive computing environment

## 🔑 Key Findings

1. **Strong Model Performance:** Achieved 95.39% accuracy with minimal error metrics
2. **Consistent Inflation Trend:** CPI increased by 45.12% over 7.5 years
3. **Reliable Forecasts:** Future predictions maintain observed patterns
4. **Model Validation:** Residuals show random distribution with no systematic bias
5. **Economic Insights:** Annual average inflation of 6.09% indicates sustained inflationary pressure

## 🚀 Future Enhancements

- [ ] Implement SARIMA for seasonal pattern detection
- [ ] Incorporate exogenous variables (GDP, oil prices) using SARIMAX
- [ ] Compare with machine learning models (LSTM, Prophet)
- [ ] Develop ensemble forecasting methods
- [ ] Create interactive dashboard for real-time forecasting
- [ ] Extend analysis to sector-specific CPI (Rural vs Urban)
- [ ] Implement automated model retraining pipeline

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 👨‍💻 Author

**Satyam Kumar**
- Roll Number: 22051615
- Program: B.Tech in Computer Science Engineering
- Institution: KIIT Deemed to be University
- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/yourprofile)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Prof. N Sangita Achary - Project Supervisor
- KIIT Deemed to be University
- Government of India - Dataset source
- Statsmodels development team

## 📞 Contact

For any queries or suggestions, please reach out:
- Email: your.email@example.com
- Project Link: [https://github.com/yourusername/CPI-Time-Series-Forecasting](https://github.com/yourusername/CPI-Time-Series-Forecasting)

---

⭐ **If you found this project helpful, please consider giving it a star!** ⭐

---

*Last Updated: October 30, 2025*
