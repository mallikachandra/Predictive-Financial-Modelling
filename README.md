# Predictive-Financial-Modelling
Crude oil prices wield immense influence over global economies and geopolitical affairs. In this paper, we focus on forecasting the prices of West Texas Intermediate (WTI) crude oil, a vital benchmark in the United States, spanning from 1990 to 2023 at weekly intervals.

## The models that were compared to conclude an optimal forecast were:
### Seasonal Naïve, STL-ETS, ARIMA, NNAR, TBATS, Combination Models, ARCH/GARCH, THIEF, MAPA

## Results of the Best Performing Model: NNAR
Intuition: It builds a neural network autoregression model that uses lagged values of the series as inputs to a neural network. It is a more advanced AR model that does away with the stationarity requirement of the data. Since this includes a hidden layer, it helps to model non-linear relationships.

### In-sample Test
<img width="452" alt="NNAR" src="https://github.com/mallikachandra/Predictive-Financial-Modelling/assets/122634492/b57f3c9a-b9fc-4ae1-afad-450b6ff69056">

Observation: The optimal model NNAR(11,1,6)[52] implies using 11 lags, 1 seasonal lag and 6 neurons in the hidden layer. This optimal model was achieved after experimenting with higher seasonal lag orders and multiple repeat parameters.

### Residuals
![NNAR Residuals pngs](https://github.com/mallikachandra/Predictive-Financial-Modelling/assets/122634492/6cc089e8-f839-4ff6-a07d-d6d9ce403b37)
Observation: 
* The optimal NNAR (11,1,6)[52] model reduces the RMSE drastically when compared to ARIMA and auto ARIMA models.
* The residuals closely resemble a white noise process with insignificant AR lags.
* The residuals still exhibit some cyclicity and the first plot on the right shows non-constant volatility, motivating ARCH/GARCH modeling.

### Out-of-Sample Forecast
<img width="452" alt="1yearahead" src="https://github.com/mallikachandra/Predictive-Financial-Modelling/assets/122634492/ca7eea7d-e36c-4d70-be23-a02919a42f6f">
This forecast is for beyond our test set, so it will be interesting to see how consistent the model is with reality moving forward. Just on simple inspection the forecast does seem to capture well past patterns and sudden spikes, especially compared to other models with is a good sign.
