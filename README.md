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
├── All_India_Index_july2019_20Aug2020.csv     # Raw dataset
├── CPI_TimeSeries_Analysis_Satyam_kumar.ipynb # Main analysis notebook
├── TSF_Assignment_2Report_Satyam_22051615.docx # Detailed project report
├── README.md                                   # Project documentation
└── requirements.txt                            # Python dependencies
```

**File Descriptions:**

- **All_India_Index_july2019_20Aug2020.csv** - Complete CPI dataset with multiple sectors and categories
- **CPI_TimeSeries_Analysis_Satyam_kumar.ipynb** - Jupyter notebook containing:
  - Data loading and preprocessing
  - Exploratory Data Analysis (EDA)
  - Stationarity testing
  - ARIMA model selection and training
  - Forecasting and evaluation
  - Visualizations and insights
- **TSF_Assignment_2Report_Satyam_22051615.docx** - Comprehensive 5-page report with:
  - Dataset overview
  - Methodology explanation
  - Model selection rationale
  - Results and error analysis
  - Conclusions and future work
- **README.md** - Project documentation (this file)

## 🛠️ Installation

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook
- Git

### Setup Instructions

1. **Clone the repository**
```bash
git clone https://github.com/satyamkumarcode/CPI-Time-Series-Forecasting.git
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
jupyter notebook CPI_TimeSeries_Analysis_Satyam_kumar.ipynb
```

## 📦 Requirements

Create a `requirements.txt` file with the following dependencies:
```txt
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
statsmodels>=0.13.0
scikit-learn>=0.24.0
jupyter>=1.0.0
notebook>=6.4.0
```

## 🚀 Usage

### Running the Analysis

1. Open the Jupyter notebook:
```bash
jupyter notebook CPI_TimeSeries_Analysis_Satyam_kumar.ipynb
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
df = pd.read_csv('All_India_Index_july2019_20Aug2020.csv')

# Filter Rural+Urban sector and extract CPI values
ts = df[df['Sector'] == 'Rural+Urban']['General index']
ts.index = pd.to_datetime(df[df['Sector'] == 'Rural+Urban']['Year'].astype(str) + '-' + 
                          df[df['Sector'] == 'Rural+Urban']['Month'], format='%Y-%B')

# Fit ARIMA model
model = ARIMA(ts, order=(1, 1, 0))
fitted_model = model.fit()

# Generate forecast
forecast = fitted_model.forecast(steps=12)
print(forecast)
```

## 🔬 Methodology

### 1. Data Preparation
- Data loading from CSV file
- Filtering Rural+Urban Combined sector
- Date parsing and time series indexing
- Data quality checks

### 2. Exploratory Data Analysis (EDA)
- Time series visualization
- Rolling statistics analysis (mean and standard deviation)
- Seasonal decomposition (trend, seasonal, residual)
- Trend identification

### 3. Stationarity Testing
- Augmented Dickey-Fuller (ADF) test
- Visual inspection with rolling statistics
- First-order differencing for stationarity
- Validation of transformed series

### 4. Model Selection
- ACF (Autocorrelation Function) analysis
- PACF (Partial Autocorrelation Function) analysis
- Grid search over ARIMA parameters (p, d, q) from 0 to 5
- AIC-based optimization
- **Selected Model:** ARIMA(1, 1, 0)

### 5. Model Training & Validation
- Train-test split (80-20 ratio)
  - Training: 70 months
  - Testing: 17 months
- Model fitting on training data
- Performance evaluation on test set

### 6. Forecasting
- Test set predictions
- 12-month ahead future forecasts (July 2020 - June 2021)
- Confidence interval estimation

### 7. Model Evaluation
- Residual analysis
- Error metrics calculation:
  - Mean Absolute Error (MAE)
  - Mean Squared Error (MSE)
  - Root Mean Square Error (RMSE)
  - Mean Absolute Percentage Error (MAPE)
- Model validation and diagnostics

## 📈 Results

### Performance Metrics

| Metric | Value | Description |
|--------|-------|-------------|
| Mean Absolute Error (MAE) | 7.23 | Average absolute forecast error |
| Root Mean Square Error (RMSE) | 8.18 | Square root of average squared errors |
| Mean Absolute Percentage Error (MAPE) | 4.61% | Average percentage error |
| **Model Accuracy** | **95.39%** | Overall prediction accuracy |

### Historical Analysis

| Metric | Value |
|--------|-------|
| Total Inflation (2013-2020) | 45.12% |
| Annual Average Inflation | 6.09% |
| Starting CPI (Jan 2013) | 104.6 |
| Ending CPI (Jun 2020) | 151.8 |
| Training Set | 70 months (80%) |
| Testing Set | 17 months (20%) |

### Future Forecast

- **Forecast Period:** July 2020 - June 2021 (12 months)
- **Predicted CPI Range:** 153.73 - 156.66
- **Expected Inflation:** ~1.9% over forecast period
- **Trend:** Continued upward trajectory consistent with historical patterns

## 📊 Visualizations

The notebook includes comprehensive visualizations:

1. **Original Time Series Plot**
   - Monthly CPI values from 2013-2020
   - Clear upward trend visualization

2. **Rolling Statistics**
   - 12-month rolling mean
   - 12-month rolling standard deviation
   - Trend characterization

3. **Seasonal Decomposition**
   - Trend component
   - Seasonal component
   - Residual component

4. **Stationarity Analysis**
   - Before and after differencing
   - ADF test results

5. **ACF & PACF Plots**
   - Autocorrelation patterns
   - Parameter selection guidance

6. **Training & Testing Forecasts**
   - Actual vs predicted comparison
   - Visual model validation

7. **Residual Analysis**
   - Residual plot
   - Histogram of residuals
   - QQ plot for normality check

8. **Future Forecast Plot**
   - 12-month predictions
   - Historical data overlay

## 💻 Technologies Used

- **Python 3.8+** - Core programming language
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **matplotlib** - Data visualization
- **seaborn** - Statistical data visualization
- **statsmodels** - Time series analysis and ARIMA modeling
- **scikit-learn** - Machine learning metrics
- **jupyter** - Interactive computing environment

## 🔑 Key Findings

1. **Strong Model Performance:** Achieved 95.39% accuracy with MAPE of only 4.61%
2. **Consistent Inflation Trend:** CPI increased by 45.12% over 7.5 years
3. **Reliable Forecasts:** Future predictions maintain observed upward patterns
4. **Model Validation:** Residuals show random distribution with zero mean
5. **Economic Insights:** Annual average inflation of 6.09% indicates sustained inflationary pressure in India
6. **Optimal Parameters:** ARIMA(1,1,0) provides best balance of accuracy and simplicity
7. **Forecast Reliability:** Low error metrics confirm model's predictive capability

## 🚀 Future Enhancements

- [ ] Implement SARIMA for enhanced seasonal pattern detection
- [ ] Incorporate exogenous variables (GDP growth, oil prices, exchange rates) using SARIMAX
- [ ] Compare with machine learning models:
  - LSTM (Long Short-Term Memory) networks
  - Facebook Prophet
  - XGBoost for time series
- [ ] Develop ensemble forecasting methods combining multiple models
- [ ] Create interactive dashboard using Plotly/Dash for real-time forecasting
- [ ] Extend analysis to sector-specific CPI (separate Rural and Urban analysis)
- [ ] Implement automated model retraining pipeline
- [ ] Add category-wise CPI analysis (Food, Housing, Transportation, etc.)
- [ ] Perform comparative state-wise CPI analysis
- [ ] Deploy model as REST API for real-time predictions

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### How to Contribute:

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Contribution Guidelines:

- Ensure code follows PEP 8 style guidelines
- Add appropriate comments and documentation
- Update README if adding new features
- Test your changes thoroughly

## 👨‍💻 Author

**Satyam Kumar**
- **Roll Number:** 22051615
- **Program:** B.Tech in Computer Science Engineering
- **Institution:** KIIT Deemed to be University
- **GitHub:** [@satyamkumarcode](https://github.com/satyamkumarcode)
- **Project Supervisor:** Prof. N Sangita Achary

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Prof. N Sangita Achary** - Project Supervisor and Guidance
- **KIIT Deemed to be University** - Academic Support
- **Government of India** - CPI Dataset Provider
- **Statsmodels Development Team** - ARIMA Implementation
- **Python Community** - Open-source tools and libraries

## 📚 References

- Box, G. E. P., & Jenkins, G. M. (1976). Time Series Analysis: Forecasting and Control
- Hyndman, R. J., & Athanasopoulos, G. (2021). Forecasting: Principles and Practice
- Government of India Ministry of Statistics - Official CPI Documentation
- Statsmodels Documentation: https://www.statsmodels.org/

## 📞 Contact

For any queries, suggestions, or collaboration opportunities:

- **GitHub Issues:** [Create an issue](https://github.com/satyamkumarcode/CPI-Time-Series-Forecasting/issues)
- **Email:** satyam.kumar@example.com
- **Project Link:** [https://github.com/satyamkumarcode/CPI-Time-Series-Forecasting](https://github.com/satyamkumarcode/CPI-Time-Series-Forecasting)

## 📊 Project Status

✅ **Completed** - October 30, 2025

- [x] Data collection and preprocessing
- [x] Exploratory Data Analysis
- [x] Model selection and training
- [x] Performance evaluation
- [x] Documentation and reporting
- [ ] Model deployment (Future work)
- [ ] Real-time forecasting dashboard (Future work)

---

⭐ **If you found this project helpful, please consider giving it a star!** ⭐

---

**Assignment Submission Details:**
- **Course:** Time Series Forecasting
- **Assignment:** Assignment 2
- **Submission Date:** October 30, 2025
- **Status:** Submitted ✓

---

*Last Updated: October 30, 2025*
