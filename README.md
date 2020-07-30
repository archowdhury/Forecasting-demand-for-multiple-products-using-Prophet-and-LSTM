# Forecasting demand for multiple products using Prophet and LSTM networks


## The problem statement

There are multiple product lines (teams). The Teams are A,B and C. Team C is further split into sub-teams CA, CB, CC, CD. We need to prepare a rolling 12 month forecast for each of the teams/subteams

The fiscal year spans from April to March, as well as the team targets to be achieved for each team each year.

## The Approach
There are many different methods available to forecast univariate time series - ARIMA, Exponential Smoothing, Prophet, Deep learning models like LSTM etc.

For this problem statement we will use Facebook's Prophet library. It's an easy to use package and gives reasonably good results. It also scales up to account for holidays and multivariate data when required.

Towards the end I have also demonstrated how to use a Deep Learning network like Bidirectional LSTMs to get even better results. It's important to have ample data when training neural networks. Since in this case we don't have too many data points so a more traditional approach like Prophet might work better

#### Being careful with the dates
Since we are dealing with data which runs in the Fiscal year Apr-Mar, hence we need to ensure that the sequence remains unchanged when we feed the data into Prophet. Otherwise the Jan-Mar data would be taken prior to April, thus ruining the forecasts

#### Evaluating the model performance

We will use the following metrics to evaluate the forecasts:

1) RMSE (Root Mean Squared Error)
2) RMSLE (Root Mean Squared Log Error)

The RMSLE has an advantage that unlike RMSE it is scale agnostic. So for example if our products have values in very different scales say 30, 300, 3000 etc. the RMSE values could vary like 1, 10, 100. However, the RMSLE will remain similar - 0.1, 0.1, 0.1 etc.
