# Time series and Exponential smoothing

## Time series [Schumway]
A *stochastic process* is a set of random variables {yₜ, t ∈ I}. 

The result of an observation of these variables is a *realization* of the stochastic process, also called *time series*.
It is customary to also refer to the process giving rise to a time series as a time series.

If the indexing set I is countable (uncountable), then the time series is said to be *discrete* (*continuous*).

## Forecasting methods and models [Hyndman]
*Forecasting method*: algorithm that gives a prediction of the value of the series at a certain future time.

*Forecasting model*: stochastic data generating algorithm, producing a prediction of the probability distribution at a future time period.
A point forecast can be obtained by taking the mean of this probability distribution.


## Exponential smoothing forecasting methods [Hyndman, Athanasopoulos]

It is common to try to split a time series into three components: the *trend* (T), *seasonal* (S) and *error* (E) components. 
These components can be combined in different ways.
For example by simply adding them, so that y = T + S + E, or by assuming multiplicative seasonality but additive error, so that y = T x S + E.

The exponential smoothing methods ignore the error component, and have corresponding models (more specifically state space models). We will only discuss the methods, not the models.

Exponential smoothing was introduced in the late 1950's by Brown, Holt and Winters.
Roughly speaking, an exponential smoothing method forecasts using a weighted average whose weights decrease exponentially as the corresponding observation gets older.   
There are different exponential smoothing methods, which we will briefly discuss.


### Simple exponential smoothing 

**Use:** forecasting with data with no trend or seasonality.

To understand simple exponential smoothing it helps to first describe the *average forecasting method*, which is one of the simplest forecasting methods.
In this case, the forecast is simply the average of the observations: 
<p align="center">
  <img src="images/average_forecast.png" alt="hi" class="inline"/>
</p>
where |T in the subscript means we are using the T first datapoints for the forecast.
This is clearly too simple for most cases. 

*Simple exponential smoothing (SES)* is similar to the average method, but the average is weighted, with the weights decreasing exponentially "with age".
More precisely:

To fit the time series + forecast the next point:
<p align="center">
  <img src="images/SES.png" alt="hi" class="inline"/>
</p>
where 0 < α < 1 is the so-called *smoothing parameter*.  
To forecast further in the future one just uses the last predicted value: <img src="images/SESforecast.png" alt="hi" class="inline"/>  

**Remarks:**
- Notice that the sum of all the weights is 
<p align="center">
  <img src="images/weighted.png" alt="hi" class="inline"/>
</p>
as it should be in a weighted average.  

- SES simply forecasts a horizontal straight line, thus not accounting for seasonality or (changes in the) trend.

- A good value for α is usually found using least squares (minimizing the sum of squared errors (SSE)).

### Holt's linear trend method
### Holt's damped trend methods
### Holt-Winters' seasonal methods
### What method to use?









## References:
- [Schumway]: 
- [Hyndman]: 
- [Athanasopoulos]:


