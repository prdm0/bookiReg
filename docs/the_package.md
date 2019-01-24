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

## Function crm {#sec:crm}

The function `crm()` fits two independent linear regression models to the center and range
of the interval variables, respectively, and minimizes the sum of squared center's error plus the sum of squared range's error [@LimaNetoDeCarvalho2008]. The function is used as </br></br>


`crm(formula1, formula2, data, ...)` </br></br>


and considers the following arguments: </br></br>

- `formula1`: an object of class `formula` that represents the symbolic description of the center's model;</br></br>
- `formula2`: an object of class `formula` that represents the symbolic description of the range's model;</br></br>
- `data`: an optional data frame containing the variables of the models.

This function returns an object of class `crm` including the following elements: </br></br>


- `coefficients.C`: the vector of coefficients for the center's explanatory variables;</br></br>
- `coefficients.R`: the vector of coefficients for the range's explantory variables;</br></br>
- `sigma.C`:  an estimate of standard deviation for the center's regression model;</br></br>
- `sigma.R`: an estimate of standard deviation for the range's regression model;</br></br>
- `df.C`: the degrees of freedom for the center's residuals;</br></br>
- `df.R`: the degrees of freedom for the range's residuals;</br></br>
- `fitted.values.l`: the fitted values of the lower interval bounds;</br></br>
- `fitted.values.u`: the fitted values of the upper interval bounds;</br></br>
- `residuals.l`: the residuals of the lower interval bounds;</br></br>
- `residuals.u`: the residuals of the upper interval bounds.

The function `summary.crm()` returns the elements `RMSE.l` (the root mean squared error of the lower bound) and `RMSE.u` (the root mean squared error of the upper bound), given an object of the class `crm`. The function `coef.crm()` returns just the estimated coefficients while the functions `fitted.crm()` and `residuals.crm()` provide, respectively, the matrices of the fitted values and the residuals for an object of the class `crm`. Notice that the fitted values, residuals and root mean square errors are denoted in terms of lower and upper interval bounds to a better comparison with the original values of the response variable $\pmb Y$.

## Function ccrm {#sec:ccrm}

The function `ccrm()` fits two independent linear regression models to the center and range
of the interval variables. However, the parameter estimation of the range's coefficients takes into account inequality constraints and is estimated using the function `pcls()` (see package **mgcv**, available in [mgcv](http://CRAN.r-project.org/package=mgcv)). This function solves least squares problems with quadratic penalties subject to linear equality and inequality constraints using quadratic programming. The aim is to guarantee mathematical coherence between the predicted values of the lower and upper bounds of the response interval variable Y, i.e., $\hat{y}_L < \hat{y}_U$. There are no constraints over the parameter estimates for the center coefficients. For further details about the constrained center and range method, see \cite{LimaNetoDeCarvalho2010}. The function \code{ccrm()} is used as


`ccrm(formula1, formula2, data, ...)`</br></br>

and considers the following arguments: </br></br>

- `formula1`: an object of class `formula` that represents the symbolic description of the center's model;</br></br>
- `formula2`: an object of class `formula` that represents the symbolic description of the range's model;</br></br>
- `data`: an optional data frame containing the variables of the models.

This function returns an object of class `ccrm` with the following elements: `coefficients.C`, `coefficients.R`, `sigma.C`, `sigma.R`, `df.C`, `df.R`, `fitted.values.l`, `fitted.values.u`,  `residuals.l` and `residuals.u`. All these elements present the same description of the function `crm()`. The function `summary.ccrm()` returns the elements `RMSE.l` (the root mean squared error of the lower bound) and `RMSE.u` (the root mean squared error of the upper bound), given an object of the class `ccrm`. The function `coef.ccrm()` returns just the estimated coefficients while the functions `fitted.ccrm()` and `residuals.ccrm()` provide, respectively, the matrices of the fitted values and the residuals for an object of the class `ccrm`. 


# References {-}
