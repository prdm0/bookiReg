# Bivariate symbolic regression model (BSRM)

## Preliminaries

Let $Y = \{y_1,\ldots,y_n\}$ be a set of observations that represents a random sample of the interval-valued variable $Y$.  Each observation $y_{i} = [y_{Li},y_{Ui}] \in Y$ is defined as an interval $y \in \Im = \{[y_{L},y_{U}] : y_{L}, y_{U} \in \Re, y_{L} \leq y_{U}\}$ and represents the observed value of the interval variable $Y$. Despite the loss of information, we consider an interval-valued variable $Y$ as a two-dimensional or a bivariate  quantitative feature vector $\mathbf y_{i}=(y_{1i},y_{2i})$, where the variables $Y_1$ and $Y_2$ are one-dimensional random variables representing, for example, the lower and upper boundaries $(Y^{L},Y^{U})$ or the midpoint and half-range $(Y^{m},Y^{r})$ of the intervals or any other pair of interval features possible to be represented.

Consider that the joint density probability function of the bivariate quantitative
feature vector $\mathbf y_{i}=(y_{1i},y_{2i})$ belongs to the bivariate exponential family of 
distributions \citep{IT2005} defined by

\begin{equation}
    f(\mathbf y; \pmb \theta)=
    \mathrm{exp}\left[\phi^{-1}\{y_{1}\theta_{1} + y_{2}\theta_{2} -
    b(\theta_{1},\theta_{2},\rho)\}+ c(y_{1},y_{2},\rho,\phi)\right],
    (\#eq:random)
\end{equation}

\noindent where \boldmath$\theta$\unboldmath=
$(\theta_{1},\theta_{2})$ is the vector of canonical parameters, $\phi$ is a common dispersion parameter
and $\rho$ is a constant correlation parameter between these two
random variables. We assume that the functions
$b(\cdot,\cdot,\cdot)$ and $c(\cdot,\cdot, \cdot, \cdot)$ are known.
The function $b(\cdot,\cdot,\cdot)$ is the cumulant generating
function of (\ref{eq:random}) and the mean and variance of the bivariate 
random vector $\mathbf Y=(Y_1, Y_2)$ can be obtained from well-known 
equations of natural exponential families and presents a direct relation with the GLM framework. The log-likelihood function for the $i$th observation can be written as

\begin{equation}
  l_{i} = l_{i}(\pmb \theta,\phi,\rho) =
        \phi^{-1} \{y_{1i}\theta_{1} +                                                                           y_{2i}\theta_{2}-b(\theta_{1},\theta_{2},\rho)\}+c(y_{1i},y_{2i},\rho,\phi).
(\#eq:loglikelihood)
\end{equation}

The use of the bivariate exponential family of distributions allows to extend the GLM framework for the case of interval-valued variables.

## The model {#subsec:model}

Let $E=\{e_1,\ldots,e_n\}$ be a set of examples that are described by
$p+1$ interval-valued variables $Y$, $T_{1},\ldots,T_{p}$. The interval-valued 
variable $Y$ is a dependent variable and it is related to a set of interval-valued 
variables $T_j$ ($j=1,2,\ldots,p$), known as independent variables. Each example
$e_{i}\in E$ ($i=1,\ldots,n$) is denoted by an interval quantitative feature
vector $(\mathbf t_{i},y_{i})$, with $\mathbf t_{i} = (t_{i1},\ldots,t_{ip})$, 
where $t_{ij}=[a_{ij},b_{ij}] \in \Im = \{[a,b]: a, b \in \Re, a \leq b\}$ $(j=1,\ldots,p)$ 
  and $y_{i} = [y_{Li},y_{Ui}] \in \Im$ are the observed values of $T_{j}$ and $Y$, 
respectively. 


Now, let $Y_1$, $X_{1j}$ and $Y_2$, $X_{2j}$ ($j=1,2,\ldots,p$) be quantitative variables 
that represent any pair of interval features from the interval-valued variables $Y$ and $T_{j}$, respectively. In case where those variables represent, respectively, the lower and upper boundaries of the interval variables $Y$ and $T_{j}$,
each example $e_{i} \in E$ ($i=1,\ldots,n$) will be denoted by two vectors: $(\mathbf x^{L}_{i},y^{L}_{i})$ 
and $(\mathbf x^{U}_{i}, y^{U}_{i})$, with $\mathbf x^{L}_{i} =
(x^{L}_{i1}, \ldots, x^{L}_{ip})$ and $\mathbf x^{U}_{i} = (x^{U}_{i1},\ldots,
x^{U}_{ip})$, where $x^{L}_{ij} = a_{ij}$, $x^{U}_{ij} = b_{ij}$, $y^{L}_{i} = y_{Li}$ and $y^{U}_{i} = y_{Ui}$
are the observed values of the quantitative variables $X^{L}_{j}$, $X^{U}_{j}$, $Y^{L}$ and $Y^{U}$, respectively. Likewise, for the case where those variables
represent, respectively, the midpoint and half-range of the interval variables $Y$ and $T_{j}$,
each example $e_{i} \in E$ ($i=1,\ldots,n$) will be denoted by the vectors
$(\mathbf x^{m}_{i}, y^{m}_{i})$ and $(\mathbf x^{r}_{i}, y^{r}_{i})$,
with $\mathbf x^{m}_{i} = (x^{m}_{i1}, \ldots, x^{m}_{ip})$ and $\mathbf x^{r}_{i} = (x^{r}_{i1},\ldots,
x^{r}_{ip})$, where $x^{m}_{ij} = (a_{ij} + b_{ij})/2$, $x^{r}_{ij}=(b_{ij}-a_{ij})/2$, 
$y^{m}_{i}=(y_{Li}+y_{Ui})/2$ and $y^{r}_{i} = (y_{Ui} - y_{Li})/2$ are the observed values of 
the variables $X^{m}_{j}$, $X^{r}_{j}$, $Y^{m}$ and $Y^{r}$, respectively.

Following the GLM framework, \cite{LimaNetoetal2011} consider a \textbf{BSRM} with probabilistic support 
defined by two components (a random and a syste\-ma\-tic component) to model interval-valued data. 
The random component considers the bivariate random vector \[\textbf{Y} = \left[\begin{array}{c}
Y_{1}\\
Y_{2}\end{array}\right],\] having the bivariate exponential family (\ref{eq:random}). 
In the systematic component, the explanatory variables $X_{1j}$ and $X_{2j}$ ($j=1,2,\ldots,p$) 
are responsible for the variability of $Y_{1}$ and $Y_{2}$, respectively, and they are defined by

\begin{equation}
\pmb \eta_{1} = g_{1}(\pmb \mu_{1})= \pmb X_{1} \pmb \beta_{1}\,\, \mbox{and}\,\, \pmb \eta_{2} = g_{2}(\pmb \mu_{2})= \pmb X_{2} \pmb \beta_{2},
(\#eq:systematic)
\end{equation}
where $\pmb X_{1}$ and $\pmb X_{2}$ are known model matrices
formed by the observed values of the variables $X_{1j}$ and $X_{2j}$, 
respectively, $\pmb \beta_{1}$ and $\pmb \beta_{2}$
are vectors of parameters to be estimated,
$\pmb \eta_{1}$ and $\pmb \eta_{2}$ are
the linear predictors, $\pmb \mu_{1}$ and $\pmb \mu_{2}$ 
are the mean of the res\-pon\-se variables $Y_{1}$ and $Y_{2}$, respectively, with
$\pmb \eta_{l}$=$(\eta_{l_{1}},\ldots,
\eta_{l_{n}})^\top,$ $\pmb \mu_{l}$ = $(\mu_{l_{1}},\ldots,
\mu_{l_{n}})^\top$ and $\pmb \beta_{l}$ $=(\beta_{l_{0}},\ldots,\beta_{l_{p}})^\top$, $l = 1,2$. Here, $g_{1}(\pmb \mu_{1}$) and $g_{2}(\pmb \mu_{2}$) 
are well-known link functions that connect the mean of the res\-pon\-se variables $Y_{1}$ and $Y_{2}$ with the explanatory variables $X_{1j}$ and $X_{2j}$ ($j=1,\ldots,p$), respectively, being possible to choose different link functions. 
A few functions available for the \textbf{BSRM} are:
\textit{identity, logarithmic, inverse, power}, among others.
However, some link functions have particular properties and can be preferred
in some situations. For example, if one considers the half-range of intervals in the
random component, the logarithmic link function will guarantee positiveness
for the predicted values of $\hat{y}_{i}^{r}$ ($\hat{y}_{i}^{r} >0$)
and this result implies that $\hat{y}_{i}^{L} \leq \hat{y}_{i}^{U}$, $i = 1, \ldots, n$.

## Parameter estimation {#subsec:parest}

The maximum likelihood method will be used as a theoretical basis for parameter estimation  in the **BSRM**. In order to maximize the log-likelihood, [@LimaNetoetal2011] first assumed that $\rho$ is
fixed and then obtained the likelihood equations for estimating $\pmb \beta_{1}$ and $\pmb \beta_{2}$. Both vectors can be estimated without knowledge of $\phi$. In principle, $\phi$ could also be estimated by maximum likelihood although there may be practical difficulties associated with this method for some bivariate distributions in \@ref(eq:random). Next, a simple approach will be given to estimate $\phi$ based on the model deviance.

An algorithm for estimating these vectors of linear parameters can be 
developed from the scoring method. Differentiating the total log-likelihood 
\@ref(eq:loglikelihood) yields the score functions for $\pmb \beta_{1}$ 
and $\pmb \beta_{2}$ 

$$U(\beta_{1j}) = \frac{\partial{l(\pmb\beta_{1}},\pmb \beta_{2})}{\partial{\beta_{1j}}} = \frac{1}{\phi} \sum_{i=1}^{n} (y_{1i} - b^{(1)}_{i})\frac{\partial{\theta_{1}}}{\partial{\beta_{1j}}} = 
\frac{1}{\phi} \sum_{i=1}^{n} (y_{1i} - \mu_{1i})\frac{1}{V^{(1)}_{i}g'_{1}(\mu_{1i})}x_{1_{ij}}$$


and


$$ U(\beta_{2j}) = \frac{\partial{l(\pmb\beta_{1}, \pmb \beta_{2}})}{\partial{\beta_{2j}}} = \frac{1}{\phi} \sum_{i=1}^{n} (y_{2i} - b^{(2)}_{i})\frac{\partial{\theta_{2}}}{\partial{\beta_{2j}}} = \frac{1}{\phi} \sum_{i=1}^{n} (y_{2r} - \mu_{2i})\frac{1}{V^{(2)}_{i}g'_{2}(\mu_{2i})}x_{2_{ij}}.$$

In matrix notation, the score functions are 

\begin{equation}
\pmb U(\beta_{1}) = (\pmb X_{1})^\top \pmb W_{1} \pmb z_{1}\,\,\,
\mathrm{and}\,\,\,\pmb U(\pmb \beta_{2})= (\pmb X_{2})^\top \pmb W_{2} \pmb z_{2},
(\#eq:score)
\end{equation}
where $\pmb W_{1}$ and $\pmb W_{2}$ are diagonal weighted matrices with corresponding elements

$$w_{1i}=[V^{(1)}_{i}\mbox{}g'_{1}(\mu_{1i})^{2}]^{-1}\,\,\,\mbox{  and  }\,\,\,
w_{2i}=[V^{(2)}_{i}\mbox{}g'_{2}(\mu_{2i})^{2}]^{-1},$$

and $\pmb z_{1}$ and $\pmb z_{2}$ are modified dependent variables related to $\pmb y_{1}$ and
$\pmb y_{2}$ given by

$$\pmb z_{1} = \pmb G_{1}(\pmb y_{1} - \pmb \mu_{1})\,\,\,\mbox{  and  }\,\,\,
\pmb z_{2} = \mathbf G_{2}(\mathbf y_{2} - \pmb \mu_{2}),$$

where $\pmb G_{1} = \mathrm{diag}\{g'_{1}(\mu_{1_{1}}),\ldots,g'_{1}(\mu_{1_{n}})\}$ and $\pmb G_{2} = \mathrm{diag}\{g'_{2}(\mu_{2_{1}}),\ldots,g'_{2}(\mu_{2_{n}})\}$ are $n \times n$ diagonal matrices.

The expected value of the *sv*-th component of the information matrix for the vector of 
parameters $\pmb \beta_{1}$ is


$$\kappa_{1(s,v)} = -E\left[\frac{\partial^{2}\beta_{1}}{\partial{\beta_{1s}}\partial{\beta_{1v}}}\right] = E\left[\frac{\partial{l(\pmb \beta_{1})}}{\partial{\beta_{1s}}}\frac{\partial{l(\pmb \beta_{1}})}{\partial{\beta_{1v}}}\right] = E[U(\beta_{1s})U(\beta_{1v})].$$
In matrix notation, the information matrices for $\beta_{1}$ and
$\beta_{2}$ can be written as


$$\pmb K_{1}=\phi^{-1}\, (\pmb X_{1})^\top \pmb W_{1} \pmb X_{1}\,\,\,\mbox{and}\,\,\,
\pmb K_{2}=\phi^{-1}\, (\pmb X_{2})^\top \pmb W_{2} \pmb X_{2}.$$

From the information matrices and equations \@ref(eq:score), we can use the scoring method to obtain the conditional maximum likelihood estimates (MLEs) of $\pmb \beta_{1}$ and
$\pmb \beta_{2}$ for a given $\rho$. We have

\begin{eqnarray}
\pmb \beta^{(k+1)} = \pmb \beta^{(k)} +  (\pmb X^\top \pmb W^{(k)} \pmb X)^{-1}\pmb X^\top \pmb W^{(k)} \pmb z^{(k)},
(\#eq:leastsquares)
\end{eqnarray}

where

\[\pmb \beta^{(k+1)} = \left[\begin{array}{c} \pmb \beta_{1}^{(k+1)}\\ \pmb \beta_{2}^{(k+1)}\end{array} \right],
\mbox{  } \mathbf X = \left[\begin{array}{cc} \pmb X_{1} & \pmb 0\\ \pmb 0 & \pmb X_{2} \end{array}\right],\]

\[\mathbf W^{(k)} = \left[\begin{array}{cc}
\pmb W_{1}^{(k)} & \textbf{0}\\
\textbf{0} & \pmb W_{2}^{(k)}\end{array}\right]\,\,\mbox{and}\,\,\,
\pmb z^{(k)} = \left[\begin{array}{c}
\pmb z_{1}^{(k)}\\
\pmb z_{2}^{(k)}\end{array} \right].\]


Expression \@ref(eq:leastsquares) has the same form of the estimating equations for the GLMs. In general terms, we regress the modified dependent  variable $\mathbf z^{(k)}$ on the local model matrix $\pmb X$ by taking $\pmb W^{(k)}$ as a modified weighted matrix. At $k = 1$, an initial appro\-xi\-ma\-tion
$\pmb \beta^{(1)}$ could be used to evaluate $\pmb W^{(1)}$ and $\pmb z^{(1)}$ from which equations (\ref{leastsquares}) yield the next estimate $\pmb \beta^{(2)}$. Hence, we update $\pmb W^{(2)}$ and $\pmb z^{(2)}$, and so the iterations continue until the convergence is achieved and then the conditional MLE $\hat{\pmb \beta}$, is obtained. In general, the convergence speed is fast, but it strongly depends on the choice of the initial value $\pmb \beta^{(1)}$.

## Goodness-of-fit measure {#goodness-of-fit}


Conditioned on the parameter $\rho$, the discrepancy of a **BSRM** is defined by [@LimaNetoetal2011] as twice the difference between the maximum log-likelihood achievable and that achieved for the model under investigation. The discrepancy is known as the deviance of the current model and has the form of a genuine GLM deviance, since it is a function of the data only and of the MLEs $\hat{\mu}_{1i}$
and $\hat{\mu}_{2i}$, for $i=1,\ldots,n$, which are calculated from the data. Hence, the deviance conditioned on $\rho$, say $D(\rho)$, can be written as

\begin{eqnarray}
D(\rho) &=& 2 \sum_{i=1}^{n}\{y_{1i}[q_{1}(y_{1i},\rho) - q_{1}(\hat{\mu}_{1i},\rho)] + y_{2i}[q_{2}(y_{2i},\rho) - q_{2}(\hat{\mu}_{2i},\rho)]\nonumber\\
&+& [b(q_{1}(\hat{\mu}_{1i},\rho),q_{2}(\hat{\mu}_{2i},\rho),\rho) -
b(q_{1}(y_{1i},\rho),q_{2}(y_{2i},\rho),\rho)]\}.
(\#eq:deviance)
\end{eqnarray}


The direct maximum likelihood estimation of the dispersion parameter $\phi$ is a more difficult problem than the estimation of \boldmath$\beta$\unboldmath\, and that complexity depends entirely on the functional form of the function $c(y_1,y_2,\rho,\phi)$. For some \textbf{BSRMs}, the MLE of the
dispersion parameter could be very complicated, the deviance can be used to obtain a consistent estimate
of the dispersion parameter $\phi$ from the estimates \boldmath$\hat\beta$\unboldmath$_{1}$ and \boldmath$\hat\beta$\unboldmath$_{2}$  obtained from (\ref{leastsquares}), with dimensions $p_1 \times 1$ and $p_2 \times 1$, respectively. The deviance can be  approximated by a $\chi_{\nu}^2$ distribution with $\nu=2n-(p_1+p_2)$ degrees of freedom, which leads to a simple estimate of $\phi$ 

\begin{eqnarray}
\tilde{\phi} = \frac{D(\rho)}{2n - (p_{1} + p_{2})},
(\#eq:phiestimate)
\end{eqnarray}
based on the fact that the deviance can be approximated by a chi-squared distribution.

Substituting the estimates $\hat{\pmb \beta}_{1}$, $\hat{\pmb \beta}_{2}$ and $\tilde\phi$ in
\@ref(eq:loglikelihood) yields the profile log-likelihood for the parameter $\rho$

\begin{equation}
l_p(\rho)= \phi^{-1}\sum_{i=1}^{n} \{y_{1i}\hat\theta_{1} +
y_{2i}\hat\theta_{2}-b(\hat\theta_{1},\hat\theta_{2},\rho)\} + \sum_{i=1}^{n}
c(y_{1i},y_{2i},\rho,\tilde\phi).
(\#eq:profile)
\end{equation}

In the next step, the procedure calculates the profile log-likelihood $l_p(\rho)$ in \@ref(eq:profile) for a trial series of va\-lues of $\rho \in$ $[-1,1]$ and determines numerically the value of the estimate $\hat\rho$ that maximizes $l_p(\rho)$. Once the estimate $\hat\rho$ is obtained, it can be  substituted into the algorithm \@ref(eq:leastsquares) to produce the new conditional estimate $\hat{\pmb \beta}$, and then substituting in equation \@ref(eq:phiestimate) to obtain a new estimate $\tilde\phi$. The new values of $\hat{\pmb \beta}$, and $\tilde\phi$ can update $\hat\rho$, and so the iterations continue until convergence is observed. The joint iterative process for the parameter estimates of the **BSRM** is included in the **iRegression** package through the function `bivar`.

## Residuals {#measures}

[@LimaNetoetal2011] present some residuals expressions that are useful to make inference about the response distribution, identify outliers, verify the link function adequacy, among others aspects. The **BSRM** allows an unique residual definition for an interval-valued data. Usually, the residuals are defined separately for each boundary of the interval.

The projection matrix **H** takes the form

\begin{eqnarray}
\pmb H = \pmb W^{1/2} \pmb X (\pmb X^\top \pmb W \pmb X)^{-1} \pmb X^\top \pmb W^{1/2},
(\#eq:21h)
\end{eqnarray}

that is equivalent to replace $\pmb X$ by $\pmb W^{1/2} \pmb X$ which effectively allows for the change in variance with the mean. Here,

\[\pmb H = \left[ \begin{array}{cc}
\pmb H_{1} & \pmb 0 \\
\pmb 0 & \pmb H_{2} \end{array} \right], \mbox{ } \pmb X =
\left[ \begin{array}{cc}
\pmb X_{1} & \pmb 0 \\
\pmb 0 & \pmb X_{2} \end{array} \right]\,\, \mbox{and} \,\,\pmb
W = \left[ \begin{array}{cc}
\pmb W_{1} & \pmb 0 \\
\pmb 0 & \pmb W_{2} \end{array}\right].\]

The well-known measure of leverage is given by the diagonal elements of the projection matrix, with
$\sum_{i} h_{1_{ii}} = p_{1}$ and $\sum_{i} h_{2_{ii}} = p_{2}$. Hence, the interval-valued observations for the response variable $Y$ with high leverage are indicated by $h_{i}$ = ($h_{1_{ii}}$ + $h_{2_{ii}}$)
greater than $2(p_1+p_2)/n$. An index plot of each $h_{i}$ versus $i$ with this lower limit could be an useful informal tool for looking at leverage.

Some residual measures commonly used in the GLM theory can be easily extended to the **BSRM**. The residual related to the $i$th vector of observations $(y_{1i}, y_{2i})$ can be composed by two parts: the residual for the observation $y_{1i}$ and the residual for the observation $y_{2i}$. The Pearson residual is given by

\begin{eqnarray}
r^{P}_{1i} = \frac{y_{1i} -\hat{\mu}_{1i}}{\sqrt{\widehat{V}_{1i}}}\,\,\,\mbox{and}\,\,\,r^{P}_{2i}
=\frac{y_{2i}-\hat{\mu}_{2i}}{\sqrt{\widehat{V}_{2i}}}.
(\#eq:pearson)
\end{eqnarray}

The Studentized Pearson residual which has a constant variance when $\phi \rightarrow 0$ can be expressed as

\begin{eqnarray}
r^{SP}_{1i}= \frac{y_{1i}-\hat{\mu}_{1i}}{\sqrt{V(\hat{\mu}_{1i})(1-\hat{h}_{1_{ii}})}}\,\,\,
\mbox{and}\,\,\,r^{SP}_{2i}=\frac{y_{2i}-\hat{\mu}_{2i}}{\sqrt{V(\hat{\mu}_{2i})(1-\hat{h}_{2_{ii}})}}.
(\#eq:studentized)
\end{eqnarray}

The deviance residual can be interpreted as a joint residual measure or a global residual  measure for the vector of observations $(y_{1i}, y_{2i})$. The *i*th deviance residual is defined in terms of the  square root of the contribution of the *i*th observation to the deviance \@ref(eq:deviance).  Conditioned on $\rho$, the deviance residual can be expressed as

\begin{eqnarray} 
r_{i}^{D} &=& \mbox{sign}[(y_{1i}-\hat{\mu}_{1i})+(y_{2i}-\hat{\mu}_{2i})] \sqrt{d_{i}},
(\#eq:devianceresidual)
\end{eqnarray}

where

\begin{eqnarray} 
d_{i} &=& 2\{y_{1i}[q_{1}(y_{1i},\rho)-q_{1}(\hat{\mu}_{1i},\rho)]+ y_{2i}[q_{2}(y_{2i},\rho) - q_{2}(\hat{\mu}_{2i},\rho)] \nonumber \\
&+& b(q_{1}(\hat{\mu}_{1i},\rho),q_{2}(\hat{\mu}_{2i},\rho),\rho)-b(q_{1}(y_{1i},\rho),q_{2}(y_{2i},\rho),\rho)\}. \nonumber
(\#eq:deviance1)
\end{eqnarray}

Based on these residuals measures, the classical model checking techniques considered in the GLM theory can be straightforwardly extended for the **BSRM**.

---
