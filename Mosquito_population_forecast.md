# Mosquito population forecast

## Context
On February 15 and 16 our team tackled the "Mosquitoes challenge": a problem proposed by the Red Cross with the goal of predicting the fluctuations of the mosquito population in the Philippines, which is a predictor for outbreaks of Dengue.

### The data
One way to monitor the mosquito population in a region is by installing so-called ovitraps. These are container covered with water and covered with a mesh where mosquitoes can lay eggs, which after developing into mosquitoes are trapped inside the ovitrap by the mesh.

[comment]: # (Thisimage was supposed to be centered...)
<p align="center">
  <img src="https://i.imgur.com/r9rXTaW.gif" alt="hi" class="inline"/>
</p>



We were given the number of mosquitoes captured in said ovitraps on many different schools in the Phillipines, with measurements made once a month. We were aso provided the climateric conditions on those days.

### Our approach


---

## Baseline time series model

As a first step, we ignore all predictors except time and just treat the problem as a time series. The result will be our baseline model, to which one can latter add other predictors.

It is common to try to split a time series into three components: the *trend* (or level) (T), *seasonal* (S) and *error* (E) components. 
These components can be combined in different ways.
For example by simply adding them, so that y = T + S + E, or by assuming multiplicative seasonality but additive error, so that y = T x S + E.

The forecasting methods we discuss ignore the error component. It is important to note that they can have different rules for fitting and forecasting.



### Exponential smoothing
Exponential smoothing was introduced in the late 1950's by Brown, Holt and Winters.
Roughly speaking, an exponential smoothing method forecasts using a weighted average whose weights decrease exponentially as the corresponding observation gets older.   
There are different exponential smoothing methods.

#### Simple exponential smoothing 
**Use:** forecasting using data with no trend and no seasonality.

Applied to our case:
![](https://i.imgur.com/UjrojAh.png)

#### Holt's linear trend method
**Use:** forecasting using data with an approximately constant trend but without seasonality.

*Holt's linear trend method* is an extension of SES which separates T in two components: the level l and the trend (slope) b.

Applied to our case:
![](https://i.imgur.com/oAJ7dsZ.png)

#### Holt's damped trend method
**Use:** forecasting using data with a decreasing trend but without seasonality.

It is clear that the Holt's linear trend method tends to overshoot in many cases for long forecast horizons. One can try to solve this by introducing damping of the trend such that the level does not increase indefinitely. The result is the *Holt's damped trend method*.

Applied to our case:
![](https://i.imgur.com/sW0mcqn.png)

#### Holt-Winters' additive seasonal method
**Use:** forecasting using data with an approximately constant trend and with seasonality, and the seasonal variations are approximately constant across time.

*Holt-Winters' additive seasonal method* is an extension of Holt's linear trend method which adds a seasonal component.

Applied to our case:
![](https://i.imgur.com/CoYlwwQ.png)


#### Grid search over all exponential smoothing methods
We can introduce damping in seasonal methods and assume multiplicative seasonality instead of additive seasonality.
All these options together give us a table with all the exponential smoothing methods:

|           |                      |          |  Seasonality |                    |
|-----------|----------------------|:--------:|:------------:|:------------------:|
|           |                      | N (None) | A (Additive) | M (Multiplicative) |
|           | N (None)             |  (N, N)  |    (N, A)    |       (N, M)       |
|**Trend**  | A (Additive)         |  (A, N)  |    (A, A)    |       (A, M)       |
|           | Ad (Additive damped) |  (Ad, N) |    (Ad, A)   |       (Ad, M)      |

There are also models with multiplicative trend, but those are seldom useful. We'll include them in the grid search for completeness nonetheless.

Running a grid search over all exponential smoothing methods, the result is slightly disappointing: the best exponential smoothing method is the SES, which forecasts a flat line, a sqrt deviation of 7.3 (which will turn out to be worse than the Sarimax approach). 

![](https://i.imgur.com/E43tHOu.png)

A flatline is not useful for our purposes.
So we drop this method and explore the Sarimax method instead.



### SARIMAX



