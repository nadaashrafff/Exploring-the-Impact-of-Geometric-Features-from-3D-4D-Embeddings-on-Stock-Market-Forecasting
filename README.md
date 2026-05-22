# Exploring the Impact of Geometric Features from 3D/4D Embeddings on Stock Market Forecasting

## Project Overview

This project explores how geometric and topological features extracted from 3D and 4D embeddings can improve stock market forecasting.

The study focuses on the Egyptian stock market index **EGX70** and investigates whether transforming traditional 2D price-time data into higher-dimensional representations can reveal hidden market patterns that are not captured by standard technical indicators alone.

The main idea is that financial markets are nonlinear, chaotic, and dynamic. Therefore, higher-dimensional embeddings may expose useful structures such as recurrence, curvature, entropy, attractor behavior, spectral properties, and volatility regimes.

---

## Research Title

**Exploring the Impact of Geometric Features from 3D/4D Embeddings on Stock Market Forecasting**

---

## Authors

- Ahmed Waleed
- Nada Ashraf
- Aly Zaki
- Omar Bayoumi

**Affiliation:** Egypt University of Informatics

---

## Research Problem

Stock market forecasting is difficult because financial data is highly nonlinear, volatile, and often chaotic.

Traditional forecasting methods usually rely on basic 2D price-time representations, such as closing price, returns, and technical indicators. However, these methods may overlook hidden geometric and topological structures in market behavior.

This project investigates whether higher-dimensional embeddings can extract richer features and improve forecasting performance.

---

## Main Objective

The main objective of this project is to evaluate the predictive value of geometric and topological features extracted from 3D and 4D embeddings of EGX70 stock market data.

The project aims to:

- Transform raw time-series stock data into higher-dimensional embeddings.
- Extract geometric, topological, entropy-based, and recurrence-based features.
- Train machine learning models using these extracted features.
- Compare the predictive usefulness of different embedding methods.
- Analyze feature importance to understand which features contribute most to forecasting.
- Evaluate whether these features improve stock market directional prediction.

---

## Dataset

The project uses historical data from the Egyptian stock market index:

```text
EGX70 Index
```

The data includes financial time-series information such as:

- Closing prices
- OHLCV data
- Price movement
- Returns
- Volatility-related values

---

## Methodology

The project follows a modular experimental methodology.

Each embedding method is treated as a separate feature extraction pipeline. The extracted features are then used in machine learning models for forecasting.

The main steps are:

1. Data preprocessing
2. Time-series smoothing
3. Scaling and normalization
4. Sliding window segmentation
5. Embedding construction
6. Feature extraction
7. Model training
8. Feature selection
9. Evaluation and interpretation

---

## Main Approaches

## 1. Recurrence Plot and RQA Features

This approach uses recurrence plots and Recurrence Quantification Analysis to capture nonlinear behavior in the EGX70 price series.

### Features Extracted

- Recurrence Rate
- Determinism
- Laminarity
- Longest Diagonal Line
- Entropy
- Spectral Entropy

### Additional Features

- Standard deviation
- Skewness
- Kurtosis
- RSI
- MACD
- MACD Signal
- Bollinger Bands
- Lagged prices

### Model Used

```text
XGBoost Classifier
```

### Purpose

This method aims to detect recurrence patterns, predictability, and market complexity from stock price windows.

---

## 2. 3D Sample-Entropy Surface

This approach constructs a 3D sample-entropy surface across different time windows and embedding lags.

The goal is to measure how market complexity changes across time and memory scales.

### Features Extracted

- Sample entropy at multiple lags
- Minimum entropy
- Maximum entropy
- Entropy surface features
- Statistical features
- Nonlinear descriptors

### Models Tested

- Random Forest
- XGBoost

### Best Reported Configuration

```text
Model: Random Forest Classifier
Window Size: 80
Max Tau: 5
```

### Reported Test Performance

```text
Accuracy: 50.99%
Precision: 47.88%
Recall: 62.55%
F1 Score: 54.24%
```

### Important Features

- ent_tau6
- corr_dim
- ent_tau2

---

## 3. 3D Time-Delay Attractor

This method reconstructs the hidden phase space of the EGX70 time series using time-delay embedding.

The time series is transformed into a 3D point cloud using previous delayed values.

### Embedding Form

```text
X_t = (x_t, x_t-τ, x_t-2τ)
```

### Features Extracted

- Convex Hull Volume
- Minimum Spanning Tree Length
- Recurrence Network Clustering Coefficient
- Local Lyapunov Proxy

### Model Used

```text
Random Forest Classifier
```

### Reported Performance

```text
Accuracy: 40.37%
F1 Score: 0.56 for upward movement
```

### Feature Importance Interpretation

The most important features were:

1. Minimum Spanning Tree Length
2. Lyapunov Proxy
3. Clustering Coefficient
4. Convex Hull Volume

This suggests that trajectory connectivity and divergence may be more informative than simple density or volume measures.

---

## 4. Parametric Embedding Methodology

This approach combines classical financial features with deep-learned parametric embeddings.

A feedforward autoencoder is used to compress the input feature space into a lower-dimensional latent representation.

### Feature Engineering

The engineered features include:

- Daily returns
- Log returns
- High-low range
- Close-open range
- Momentum
- SMA
- ATR14
- Relative volume
- Price regime indicator

### Autoencoder Embedding

The autoencoder maps the input features into a 2D latent space.

The learned embeddings are then concatenated with the original financial features to enrich the feature space.

### Classifier Used

```text
XGBoost Classifier
```

### Target

The model predicts next-day volatility spikes.

A volatility spike is defined based on whether the absolute return exceeds a threshold derived from rolling median volatility.

---

## Machine Learning Models Used

The project uses several machine learning methods, including:

- XGBoost
- Random Forest
- Autoencoder-based embedding
- Gradient-boosted decision trees
- Classification models for directional forecasting

---

## Feature Selection

Feature selection was performed using model-based feature importance.

For XGBoost, gain-based feature importance was used. Features with importance greater than a selected threshold were retained.

This helped:

- Reduce noise
- Avoid overfitting
- Improve interpretability
- Focus on the most predictive features
- Simplify the feature space

---

## Important Features Identified

Across the experiments, several important features were identified:

- Spectral Entropy
- RSI
- Bollinger Bands
- Minimum Spanning Tree Length
- Lyapunov Proxy
- Sample Entropy
- Correlation Dimension
- Momentum
- Velocity
- ATR14

---

## Evaluation Strategy

The project uses chronological splitting to avoid data leakage.

The data is split based on time order rather than random sampling.

Common split strategies include:

```text
70% Training
15% Validation
15% Testing
```

or

```text
80% Training
20% Testing
```

depending on the experiment.

---

## Evaluation Metrics

The models are evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC AUC
- PR AUC
- Confusion Matrix
- Feature Importance

For trading-related experiments, the project also discusses:

- Cumulative returns
- Win rate
- Average trade return
- Alpha
- Beta
- Transaction costs
- Slippage

---

## Key Findings

The project shows that higher-dimensional embeddings can provide useful information for stock market forecasting.

Main findings include:

- Recurrence-based features capture nonlinear complexity and market structure.
- Sample entropy surfaces provide moderate predictive ability for EGX70 direction prediction.
- Time-delay attractor features reveal geometric properties of market dynamics.
- Minimum Spanning Tree Length and Lyapunov Proxy were important in the 3D attractor experiment.
- Autoencoder-based parametric embeddings can enrich traditional financial features.
- Feature selection improves interpretability and can reduce overfitting.



---

## File Description

### `FinalReport.pdf`

The final research report containing:

- Abstract
- Introduction
- Related work
- Methodology
- Recurrence plot methodology
- Sample entropy surface methodology
- Time-delay attractor methodology
- Parametric embedding methodology
- Feature importance analysis
- Results
- References

---

## Research Contributions

This project contributes to financial forecasting research by:

- Applying 3D and 4D geometric embeddings to the EGX70 index.
- Extracting nonlinear and topological features from stock market data.
- Comparing multiple embedding-based feature extraction strategies.
- Combining classical financial indicators with advanced geometric descriptors.
- Testing machine learning models on emerging market data.
- Providing feature importance interpretation for stock market prediction.

---

## Technologies and Libraries

The project can be implemented using the following tools and libraries:

- Python
- NumPy
- Pandas
- Scikit-learn
- XGBoost
- Matplotlib
- Seaborn
- SciPy
- TensorFlow / Keras
- Financial time-series preprocessing tools

---

## Possible Future Work

Future improvements may include:

- Testing the approach on other Egyptian indices.
- Applying the framework to international markets.
- Combining multiple embedding methods into one hybrid model.
- Improving trading strategy backtesting.
- Adding transaction cost sensitivity analysis.
- Testing deep learning models on recurrence plot images.
- Exploring graph neural networks for attractor-based features.
- Using more robust financial validation methods.

---

## Conclusion

This project investigates the impact of geometric and topological features extracted from 3D and 4D embeddings on stock market forecasting.

By transforming EGX70 stock market data into higher-dimensional representations, the study explores hidden structures that traditional 2D price-time methods may miss.

The results suggest that embedding-based features, especially recurrence, entropy, and attractor-based descriptors, can provide meaningful insights into market behavior and may support better forecasting models when combined with machine learning techniques.

---

## Academic Context

This research was conducted as part of a university research project at:

```text
Egypt University of Informatics
```

The project focuses on the intersection of:

- Financial forecasting
- Machine learning
- Nonlinear time-series analysis
- Geometric feature extraction
- Topological data analysis
- Emerging market prediction
