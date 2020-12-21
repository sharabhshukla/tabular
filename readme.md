<h1 align="center">Tabular</h1>

# Gradient Boosting

|         | sklearn<br>Random Forest | XGBoost<br>Gradient Boosting | LightGBM<br>Gradient Boosting | Try |
|--------------------------------------|:--------------------:|:----------------:|:----------------:|-------------|
| 🔷 Number of trees                   | N_estimators         | num_round 💡     | num_iterations 💡| 100         |
| 🔷 Max depth of the tree             | max_depth            | max_depth        | max_depth        | 7           |
| 🔶 Min cases per final tree leaf     | min_samples_leaf     | min_child_weight | min_data_in_leaf |             |
| 🔷 % of rows used to build the tree  | max_samples          | subsample        | bagging_fraction | 0.8         |
| 🔷 % of feats used to build the tree | max_features         | colsample_bytree | feature_fraction |             |
| 🔷 Speed of training                 | NOT IN FOREST        | eta              | learning_rate    |             |
| 🔶 L1 regularization                 | NOT IN FOREST        | lambda           | lambda_l1        |             |
| 🔶 L2 regularization                 | NOT IN FOREST        | alpha            | lambda_l2        |             |
| Random seed                          | random_state         | seed             | _seed            |             |


> - 🔷: Increase parameter for overfit,  decrease for underfit.
> - 🔶: Increase parameter for underfit, decrease for overfit. (regularization)
> - 💡: For Gradient Boosting maybe is better to do early stopping rather than set a fixed number of trees.

# Factorization Machines

- Read [notes on matrix factorization machines](https://www.kaggle.com/residentmario/notes-on-matrix-factorization-machines)
- Code: [FM in Keras](https://github.com/jfpuget/LibFM_in_Keras)

# Neural Nets
- [DeepFM](https://arxiv.org/abs/1703.04247) (Mar 2017)
- [xDeepFM](https://arxiv.org/abs/1803.05170) (Mar 2018)
- [Neural nets for Airbnb search](https://arxiv.org/abs/1810.09591) (Oct 2018)
- [TabNet](https://arxiv.org/abs/1908.07442): Attentive Interpretable Tabular Learning (Aug 2019)
- [NODE](https://arxiv.org/abs/1909.06312): Neural Oblivious Decision Ensembles for Deep Learning on Tabular Data (Sep 2019)
- [Graph NNs](https://arxiv.org/abs/2002.02046): DL on Relational DBs with Graph NNs (Feb 2020)
- [GrowNet](https://arxiv.org/abs/2002.07971): Gradient Boosting Neural Networks (Feb 2020)
   - Shallow NNs as “weak learners” in gradient boosting framework
   - Incorporates 2nd order stats, corrective step & dynamic boost rate to remedy pitfalls of gradient boosting tree
   - Outperforms XGBoost
- [TabTransformer](https://arxiv.org/abs/2012.06678): Tabular Data Modeling Using Contextual Embeddings (Dec 2020)


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
