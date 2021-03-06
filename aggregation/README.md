# Aggregating Savings Over Groups of Homes and Quantifying Uncertainty in Aggregate Savings Statistics

The goal of CalTrack is to develop replicable, consistent, and methodologically defensible estimators of savings over portfolios of homes. 

For CalTrack, portfolio-level savings will use inverse variance weighted means. This requires an estimate of variance. 
     
## Monthly Savings Estimate Aggregation Procedure

#### Estimating uncertainty on monthly savings estimates

For simplicity, and keeping with convention in the industry, site-level variance estimates based on ordinary least squares regressions will use OLS prediction error for savings variance. Prediction error is calculated as follows:

Take the stage one regression model with N observations and k regressors:

`y=Xβ+u`

Given a vector `x_0` of reporting period, the predicted value for that observation would be

`E[y|x_0] = ŷ_0 = x_0⋅β.`

A consistent estimator of the variance of this prediction is

`V̂_p=s^22⋅x_0⋅(X′X)^−1⋅x_0′,`

where

`s^2=Σû_i^2/(N−k).`

The forecast error for a particular `y_0` is

`ê =y_0 − ŷ_0= x_0*β + u_0 − ŷ_0.`

The zero covariance between `u_0` and `β̂` implies that

`Var[ê]=Var[ŷ_0]+Var[u_0],`

and a consistent estimator of that is

`V̂_f=s^2⋅x_0⋅(X′X)^−1⋅x_0′+s^2.`

The `1−α` confidence interval will be:

`y_0 ± t_(1−α/2)⋅(V̂_p)^.5.`

The 1−α prediction interval will be wider:

`y_0 ± t_(1−α/2)⋅(V̂_f)^.5.`


## Inverse-variance Weighted Portfolio Savings Means for Monthly Savings Analysis

Using `V̂`, CalTrack will calculate the inverse-variance weighted mean for each portfolio according to the following equation:

![Equation for inverse variance weighting](https://www.dropbox.com/s/353ssd5u7725a7c/Screenshot%202016-10-20%2010.49.07.png?raw=true)

#### Estimating uncertainty on daily savings estimates

While sampling methods would actually be preferable for characterizing the posterior distribution of savings estimates using higher-frequency AMI data, due to lack of adoption of Bayesian methods in industry and increased computational complexity, we propose CalTrack use closed-form methods with a few caveats.

The two primary considerations for higher-frequency savings models are the need to take into account stronger autocorrelation and increased model specification error. 

M & V standards for industrial savings estimation, which has been dealing with AMI data longer, provides useful guidance for dealing with these two considerations. Following ASHRAE Guideline 14-2002, and augmenting work done by the NW SEM Collaborative, we propose the following method:

##### Fractional Savings uncertainty

CalTrack will compute the Fractional Savings Uncertainty at the site level based on the following equation:

![Equation](https://www.dropbox.com/s/lca8colvkqgrtyd/Screenshot%202016-10-20%2010.28.22.png?raw=true)

##### Calculating 95% confidence intervals using frational savings uncertainty
  
To calculate confidence intervals using the following equation:

`CI(95) = +/- (FSU * 1.96) * 100`

