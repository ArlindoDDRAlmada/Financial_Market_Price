# Financial_Market_Price

Financial Market Price Estimation with Kalman Filters
Introduction to Kalman Filters
Kalman Filters are named after Rudolf Kalman, who developed the technique. They are used in many applications, such as control systems, signal processing, navigation systems etc. Kalman filters were utilized during the Apollo Program, and have also found use in NASA space shuttles, navy submarines, unmanned aerospace vehicles, and rocket-based weapons like cruise missiles. However they are also used in civilian location tracking applications such as the GPS system in your car.

The unique value proposition of Kalman Filters is that they provide an efficient way to estimate the state of a process. They support the estimation of past, present, and future states even when the precise model of the system is unknown.

Kalman Filters are most commonly used when:

The variables of interest can not be measured directly
The measurements available from multiple sources are subject to noise
Kalman Filters are quite ostensibly an unsupervised machine learning algorithm for tracking a single object in continuous state space.

Given a sequence of noisy measurements, Kalman Filters are able to recover the true state of the underlying object being tracked, by combining measurements and predictions to find an optimum estimate of the target value.

Kalman Filters involve two steps:

The Prediction step, which predicts the current state estimate
The Update step, which adjusts the predicted estimate by an actual measurement
The above two steps continue to find an optimal estimate of the target value.

test_image![image](https://github.com/ArlindoDDRAlmada/Financial_Market_Price/assets/134323111/00446388-c532-4b14-bae3-0fae15771e94)


Some of the different types of Kalman Filters are:

State Estimator	Model	Assumed Distribution
Kalman Filter	Linear	Gaussian
Extended Kalman Filter	Locally Linear	Gaussian
Unscented Kalman Filter	Nonlinear	Gaussian
Particle Filter	Nonlinear	Non Gaussian
Case Study - Context
In financial market trading, Kalman Filters are also extensively used to produce estimates of prices and correlations. They use a timeframe of observed noisy prices to create a price estimate.

In this case study, we will:

Design a Kalman estimator to replace moving average signals
Use a Kalman filter to estimate regression coefficients
Kalman Filters are typically used in momentum trading strategies where the trading signal is generated by a moving average crossover. They are also used to dynamically adjust the hedge ratio in a mean reverting trading strategy.

Kalman Filter as Moving Average
As the Kalman filter updates its estimates at every time step and tends to weigh recent observations more than older ones, a particularly useful application is estimation of rolling parameters of the data. This is similar to computing exponentially weighted moving average (EWMA), but not exactly the same as when we use a Kalman filter, there's no window length that we need to specify. This is useful for computing the moving average or for smoothing out estimates of other quantities. For instance, if we have already computed the moving target (e.g any finanical metric like sharpe ratio), we can smooth it using a Kalman filter.

Below, we'll use both a Kalman filter and an n-day moving average to estimate the rolling mean of a dataset. We hope that the mean describes our observations well, so it shouldn't change too much when we add an observation; therefore, we assume that it evolves as a random walk with a small error term. The mean is the model's guess for the mean of the distribution from which measurements are drawn, so our prediction of the next value is simply equal to our estimate of the mean. We assume that the observations have variance 1 around the rolling mean, for lack of a better estimate. Our initial guess for the mean is 0, but the filter quickly realizes that that is incorrect and adjusts.
