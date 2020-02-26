<h1 align="center">Tabular</h1>

# Gradient Boosting

# Factorization Machines

# Neural Nets
- [DeepFM](https://arxiv.org/abs/1703.04247)
- [xDeepFM](https://arxiv.org/abs/1803.05170)
- [TabNet](https://arxiv.org/abs/1908.07442)
- [NODE](https://arxiv.org/abs/1909.06312): Neural Oblivious Decision Ensembles for Deep Learning on Tabular Data
- [GrowNet](https://arxiv.org/abs/2002.07971): Gradient Boosting Neural Networks
   - Shallow NNs as “weak learners” in gradient boosting framework
   - Incorporates 2nd order stats, corrective step & dynamic boost rate to remedy pitfalls of gradient boosting tree
   - Outperforms XGBoost


<h1 align="center">Temporal Series</h1>

# ➕ Feature engineering

#### Get information about the current date (date variable)

|     Date     | | Day | Month | Year | Weekday | Weeknum | IsHoliday |
|:------------:|-|:---:|:-----:|:----:|:-------:|:-------:|:---------:|
| **1/1/2018** | |  1  |   1   | 2018 |    2    |    1    |     1     |
| **2/1/2018** | |  2  |   1   | 2018 |    3    |    1    |     0     |
| **3/1/2018** | |  3  |   1   | 2018 |    4    |    1    |     0     |
| **4/1/2018** | |  4  |   1   | 2018 |    5    |    1    |     0     |
| **5/1/2018** | |  5  |   1   | 2018 |    6    |    1    |     0     |
| **6/1/2018** | |  6  |   1   | 2018 |    7    |    1    |     0     |
| **7/1/2018** | |  7  |   1   | 2018 |    1    |    2    |     0     |
| **8/1/2018** | |  8  |   1   | 2018 |    2    |    2    |     0     |
| **9/1/2018** | |  9  |   1   | 2018 |    3    |    2    |     0     |


#### Get information about the past (continuous variable)

|     Date     |  Sales  | | Lag1 | Lag2 | Moving average (2) |
|:------------:|:-------:|-|:----:|:----:|:--------------:|
| **1/1/2018** | **100** | |   -  |   -  |        -       |
| **2/1/2018** | **150** | |  100 |   -  |       100      |
| **3/1/2018** | **160** | |  150 |  100 |       125      |
| **4/1/2018** | **200** | |  160 |  150 |       155      |
| **5/1/2018** | **210** | |  200 |  160 |       180      |
| **6/1/2018** | **150** | |  210 |  200 |       205      |
| **7/1/2018** | **160** | |  150 |  210 |       180      |
| **8/1/2018** | **120** | |  160 |  150 |       155      |
| **9/1/2018** |  **80** | |  120 |  160 |       140      |


- Lag variables (autoregressive elements)
- Aggregated features on lagged variables:
  - Moving Average (MA): Average of Lags.
  - Exponential Weighting Moving Average (EWMA): More recent values have higher weight.
  - Others like mean, std, sum, substraction
  - Regression on lags (slope, intercep)

---

# Reference
- Time Series in Driverless AI
  - [documentation](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/time-series.html)
  - [video](https://youtu.be/eF4Oa0ZzXdQ)
- MLcourse.ai  Time series analysis (Topic 9)
  - [Part 1](https://mlcourse.ai/articles/topic9-part1-time-series)
  - [Part 2: Facebook Prophet](https://mlcourse.ai/articles/topic9-part2-prophet)
