# Time series and Exponential smoothing

## Time series [Schumway]
A *stochastic process* is a set of random variables ${y_t, t\in I}$. 

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

### Simple exponential smoothing 
### Holt's linear trend method
### Holt's damped trend methods
### Holt-Winters' seasonal methods
### What method to use?









## References:
- [Schumway]: 
- [Hyndman]: 
- [Athanasopoulos]:


