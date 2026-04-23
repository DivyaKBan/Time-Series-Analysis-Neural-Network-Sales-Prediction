# Time Series Analysis Neural Network Sales Prediction

<div align="center">
<img src="imgs/poster.png" alt="Deep Temporal Demand Forecasting Banner" width="100%" style="max-width: 800px;">
</div>

📌 Executive Summary
Optimizing inventory is the backbone of modern retail operations. Accurate demand forecasting prevents costly stockouts and minimizes overstock depreciation. This project architectures an end-to-end predictive pipeline that ingests historical transactional data and utilizes advanced deep-sequence neural networks to forecast granular, item-level store demand.

By benchmarking traditional Machine Learning regressors against custom Hybrid Deep Learning architectures, this project establishes a robust framework for data-driven supply chain optimization.

🧰 Tech Stack
Languages: Python

Deep Learning: TensorFlow, Keras (LSTM, CNN architectures)

Machine Learning: Scikit-learn, XGBoost

Data Processing: Pandas, NumPy

Visualization: Matplotlib, Seaborn

🎯 Strategic Objectives
Algorithm Benchmarking: Compare the efficacy of baseline models (ARIMA, XGBoost, Random Forest) against complex sequential models (Bi-LSTM, CNN).

Hybrid Architecture Design: Develop a custom spatio-temporal neural network that extracts local patterns via convolutions and tracks sequential dependencies via recurrent layers.

Operational Scalability: Deliver a model pipeline capable of scaling across multiple store locations and diverse SKUs.

📂 Data Architecture & Ingestion
Source: Store Item Demand Forecasting Challenge (Kaggle).

Scale & Scope: 5 years of daily transactional data (Jan 2013 - Dec 2017) encompassing 10 distinct retail locations and 50 unique items.

Core Features: Date (Temporal anchor), Store_ID (Spatial anchor), Item_ID (Product anchor), Sales (Target variable).

⚙️ Data Engineering & Pipeline
To ensure model robustness and prevent data leakage, the following preprocessing steps were implemented:

Temporal Feature Extraction: Converted raw date strings into discrete ordinal features to capture seasonality and trend mechanics.

Categorical Encoding: Applied label encoding for non-ordinal identifiers (Store_ID, Item_ID).

Quality Assurance: Validated dataset integrity (zero nulls, zero duplicate records).

Sequential Splitting: Executed a strict chronological train/test split (75/25) to simulate real-world forecasting conditions and prevent look-ahead bias.

🧠 Model Architecture & Methodology
The project explores a spectrum of algorithms, graduating from foundational ML to deep sequence models:

1. Baseline Estimators:

Random Forest Regressor & XGBoost

Artificial Neural Networks (ANN) & standard Convolutional Neural Networks (CNN)

ARIMA (Statistical baseline)

2. Advanced Temporal Networks:

Long Short-Term Memory (LSTM)

Bidirectional LSTM (Bi-LSTM)

3. Custom Hybrid Architectures (Proprietary Models):

LSTM + CNN Pipeline: Convolutions extract spatial/local features from the data vector, which are then passed into LSTM layers to learn temporal dependencies over the forecast horizon.

BiLSTM + CNN Pipeline: Encapsulates the LSTM layers in a Bidirectional wrapper, allowing the network to learn context from both past and future data states during training, heavily refining the final dense layer output.

Hyperparameters: Hand-tuned with an optimized batch size of 256.

<div align="center">
<img src="imgs/model.png" alt="Hybrid Model Architecture Diagram" width="50%" style="max-width: 1000px;">
</div>


📊 Performance & Key Findings
Models were strictly evaluated using Mean Squared Error (MSE) to heavily penalize large forecasting deviations, which represent severe supply chain failures (massive overstock or total stockouts).

Baseline Evaluation
<div align="center">
<img src="imgs/baseline pic.png" alt="Baseline Model MSE Chart" width="80%" style="max-width: 800px;">
</div>
Among the baseline estimators, the standalone CNN achieved the lowest MSE, successfully capturing local data patterns, outperforming both XGBoost and the multi-layer perceptron (ANN).

Deep Sequence Evaluation
<div align="center">
<img src="imgs/time series model res.png" alt="Time Series Model Results" width="80%" style="max-width: 800px;">
</div>
The integration of sequential memory yielded significant improvements. The custom BiLSTM-CNN hybrid achieved the state-of-the-art performance for this dataset, closely followed by the standalone Bi-LSTM. The bidirectional context proved critical for minimizing error margins across volatile sales periods.

🔭 Limitations & Future Scope
While the hybrid model achieved high accuracy, the current dataset relies purely on historical sales. Future iterations of this pipeline will incorporate:

Exogenous Regressors: Integrating macroeconomic indicators, local weather data, and holiday calendars to explain sudden demand spikes.

Granular Clustering: Applying K-Means to cluster stores by geographical behavior before feeding data into the neural network to reduce global noise.
