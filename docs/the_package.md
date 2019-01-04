# The package {#package}

The **R** package **iRegression** contains the following functions: </br></br>


- `bivar` is a function that fits a regression model for interval-valued variables based on the bivariate symbolic regression method (BSRM);</br></br>
- `crm` is a function that fits a linear regression model based on the center and range method (CRM);</br></br>
- `ccrm` is function that fits a linear regression with inequality constraints over the range's parameters (CCRM);</br></br>
- `MinMax` is a function that fits a linear regression model for interval variables based on the MinMax method;</br></br>
- `cm` is a function that fits a linear regression model based on the center method;

All five functions require an object of class `formula` giving the symbolic description of the regression model to be estimated. Methods for analyzing the models above are also provided. The functions `coef()`, `fitted()` and `residuals()` extract the estimated coefficients, fitted values and residuals from the adjusted models. An object from any of the five classes can be summarized through the function `summary()`.

## Function bivar

The function `bivar()` can be used to estimate the parameter of a gaussian bivariate regression model for interval variables. It is possible to consider any pair of interval features for the bivariate random vector $\pmb Y$. For example, the lower and upper interval bounds or the midpoint and the range of intervals, respectively. The function is used as </br></br>


`bivar(formula1, lig1, formula2, lig2, data, ...)` </br></br>


and considers the following arguments: </br></br>

- `formula1`: an object of class `formula` that represents the symbolic description of the first marginal model;</br></br>
- `lig1`: represents the link function to be considered for the first model;</br></br>
- `formula2`: an object of class `formula` that represents the symbolic description of the second marginal model;</br></br>
- `lig2`: represents the link function to be considered for the second model;</br></br>
- `data`: an optional data frame containing the variables of the models.

Notice that it is possible to choose from different link functions (`identity`, `inverse` or `log`) to connect the random variables $Y_1$ and $Y_2$ with the respective linear predictors $\eta_1$ and $\eta_2$. The function `summary.bivar()` returns the following elements, given an object of the class `bivar`: </br></br>

- `Coefficients1` and `Coefficients2`: the vectors of coefficients for the explanatory variables of the models 1 and 2, respectively;</br></br>
- `RMSE1` and `RMSE2`: the root mean square error for the models 1 and 2, respectively;</br></br>
- `Rho`: the estimate for the correlation coefficient between $Y_1$ and $Y_2$;</br></br>
- `Phi`: the estimate of the dispersion parameter;</br></br>
- `D`: the goodness-of-fit measure deviance for the current model.

The function `bivar()` considers the expression \@ref(eq:leastsquares) to estimate the vectors of coefficients $\hat{\pmb \beta_1}$ and $\hat{\pmb \beta_2}$, the expression \@ref(eq:deviance) to compute the Deviance for the current model, and the expressions \@ref(eq:phiestimate) and \@ref(eq:profile) provide, respectively, the estimates of the dispersion parameter $\hat{\phi}$ and the correlation coefficient $\hat{\rho}$. Moreover, the function `coef.bivar()` returns just the estimated coefficients while the functions `fitted.bivar()` and `residuals.bivar()` provide, respectively, the matrices of the fitted values and the residuals for an object of the class `bivar`. The expression \@ref(eq:devianceresidual) is used to obtain the residual deviance. The function `bivar` considers the bivariate gaussian distribution as probabilistic support for the error of the model BSRM and the following elements belongs from an object of class `bivar`: </br></br>

- `coefficients1`: a named vector of coefficients for the explanatory variables of the model "1";</br></br>
- `coefficients2`:	a named vector of coefficients for the explanatory variables of the model "2";</br></br>
- `fitted.values1`: the fitted values for the response variable $\pmb Y_1$;</br></br>
- `fitted.values2`: the fitted values for the response variable $\pmb Y_2$;</br></br>
- `residuals1`: the ordinary residual for the response variable $\pmb Y_1$;</br></br>
- `residuals2`: the ordinary residual for the response variable $\pmb Y_2$;</br></br>
- `residual.deviance`:	the global residual for the bivariate vector $\pmb Y = [\pmb Y_1, \pmb Y_2]$;</br></br>
- `Rho`: the estimative for the correlation coefficient between $\pmb Y_1$ and $\pmb Y_2$;</br></br>
- `Phi`:the estimative of the dispersion parameter;</br></br>
- `D`:	the goodness-of-fit measure deviance for the current model.

# References {-}
