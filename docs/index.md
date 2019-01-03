---
knit: "bookdown::render_book"
title: "iRegression: An R Package for Regression Models with Interval Variables"
author: "Eufrasio de A. Lima Neto and Pedro Rafael D. Marinho"
description: "Escrever um prefácio"
date: "2019-01-03"
output: bookdown::gitbook
bibliography: [iReg.bib]
biblio-style: apalike
link-citations: yes
always_allow_html: yes
url: 'https://prdm0.github.io/iRegression/'
github-repo: prdm0/bookiRegression
site: bookdown::bookdown_site
documentclass: book
---

# Preface {-}

-----

<p align="center">
<img src="images/logo_iRegession.png" width="300" height="300"/>
</p>

<div class=text-justify>
In real problems, it is usual to have the available data presented as intervals. Currently, it is possible to find a wide literature about statistical methods for analyzing interval data. Therefore, different approaches have been proposed to obtain a regression model for this type of data. Some of these methods study the problem itself from an optimization point of view while other regression methods take into account a probabilistic background for the dependent variable. This book presents the **R** package **iRegression** that contains functions to estimate regression models for interval-valued variables. Particularly, it is presented a generalized linear model for interval-valued variables that includes, as special cases, some regression models for interval variables. The package also provides functions to obtain the fitted values and residuals for the estimated models as well as goodness-of-fit measures and examples of real interval data sets.
</div></br></br></br></br>


<div style= "float:right;position: relative; top: -100px;">
<img src="images/note.png"  width="40" height="40"/>

<div style="background-color:rgba(255, 255, 0, 0.65)">
- More summary information and examples of using the **iRegression** package functions can be obtained from the package development website at [iRegression](https://prdm0.github.io/iRegression/) or in  the documentations packaged in The Comprehensive R Archive Network - CRAN in [iRegression (CRAN)](http://CRAN.r-project.org/package=iRegression).

- In [iRegression (CRAN)](http://CRAN.r-project.org/package=iRegression) you can find the stable version of the package.
</div>

---
