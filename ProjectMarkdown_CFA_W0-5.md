Gap Years in Australia: Effects on Multidimensional Life Satisfaction
========================================================

Contents:

1. [Data Munging](#SQL)
2. [Cohort Sequence Design](#cohort)
3. [Growth Curve: General Life Satisfaction](#lifeSat)
4. [Growth Curve: Satisfaction with Career Prospects](#careerPros)
5. [Growth Curve: Satisfaction with Future Prospects](#futPros)

<a name="SQL"></a>
SQL Data Munging
--------------
Initial data-munging was done using a series of SQL queries. For direct further education entrants we took those who indicated that they had finished year 12 the year before and indicated that they were currently undertaking some form of teriary study. Gap year students were derived by taking those who had completed year 12 the year before and indicated that they had defered further education and/or confirmed the following year that they had defered further education in the year previous.

Further education drop-outs were taking by exploring if in any of the years under investigation they indicated they had withdrawn from their teriary education course. Gap-year returners composed those who had, at any time during the period of investigation indicated that they currently undertaking teriary education. SQL queries underlying theis subsetting are in .Rmd file associated with this file.

```
## Loading required package: DBI
```

```
## [1] "META1995"    "META1998"    "META2003"    "Student1995" "Student1998"
## [6] "Student2003"
```


The number of adolescence who directly entered university after high-school was ***2259***. The number of adolescents that took a gap-year (offered further education but defered) was ***645***. Of the direct entrants, those who withdraw from further education in the direct entrant group were ***81***. For ther gap-year group, those who eventually returned to further education were ***461***.

<a name="cohort"></a>
Cohort Sequence Design
-----------------------
The PISA database consistst on individuals who are the same age but may be in a veriety of year in school grades. In the current research we wanted to compare individuals in terms of years since high-school graduation rather than age in years. As such, we needed to rearrange the data.

The Satisfaction Items are (How satisfied are you with):

* WORK The work you do, at school, at home or in a job
* LEISURE What you do in your spare time
* GET.ALONG How you get on with people in general
* WAGE The money you get each week
* SOCIAL Your social life
* INDEPENDENCE Your independence - being able to do what you want
* **CAREER.PROS** Your career prospects
* **FUTURE.PROS** Your future
* HOME.LIFE Your life at home
* LIVE.STAND Your standard of living
* RESIDENCE Where you live
* **LIFE.SAT** Your life as a whole

Items in **bold** are the ones used in the analysis.



<a name="lifeSat"></a>
CFA Growth - Life Satisfaction
-----------------------

Group Parameters significant for Life Satisfaction so this model is plotted at the end of this section.


```
##      chisq df    cfi    tli   rmsea
## [1,] 63.51 16 0.9869 0.9877 0.03209
## [2,] 31.17 12 0.9947 0.9934 0.02354
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 19403 19493  31.2                                  
## fitL 16 19428 19493  63.5       32.3       4    1.6e-06 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-15) converged normally after 103 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        16
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               31.172
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.002
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W0LIFE.SAT        1.000
##     W1LIFE.SAT        1.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        1.000
##     W4LIFE.SAT        1.000
##     W5LIFE.SAT        1.000
##   s =~
##     W0LIFE.SAT       -1.000
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        2.000
##     W4LIFE.SAT        3.000
##     W5LIFE.SAT        4.000
##   q =~
##     W0LIFE.SAT       -1.000
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        4.000
##     W4LIFE.SAT        9.000
##     W5LIFE.SAT       16.000
## 
## Covariances:
##   i ~~
##     s                 0.005    0.002    2.072    0.038
##     q                -0.002    0.001   -2.352    0.019
##   s ~~
##     q                -0.002    0.001   -2.583    0.010
## 
## Intercepts:
##     W0LIFE.SAT        0.000
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        0.000
##     W3LIFE.SAT        0.000
##     W4LIFE.SAT        0.000
##     W5LIFE.SAT        0.000
##     i                 3.563    0.007  496.734    0.000
##     s                 0.003    0.006    0.544    0.587
##     q                -0.006    0.002   -3.936    0.000
## 
## Variances:
##     W0LIFE.SAT        0.158    0.007
##     W1LIFE.SAT        0.151    0.005
##     W2LIFE.SAT        0.147    0.005
##     W3LIFE.SAT        0.140    0.005
##     W4LIFE.SAT        0.137    0.005
##     W5LIFE.SAT        0.140    0.010
##     i                 0.101    0.004
##     s                 0.009    0.003
##     q                 0.001    0.000
```

```
## lavaan (0.5-15) converged normally after  80 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        16
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               43.809
##   Degrees of freedom                                15
##   P-value (Chi-square)                           0.000
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W0LIFE.SAT        1.000
##     W1LIFE.SAT        1.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        1.000
##     W4LIFE.SAT        1.000
##     W5LIFE.SAT        1.000
##   s =~
##     W0LIFE.SAT       -1.000
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        2.000
##     W4LIFE.SAT        3.000
##     W5LIFE.SAT        4.000
##   q =~
##     W0LIFE.SAT       -1.000
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        4.000
##     W4LIFE.SAT        9.000
##     W5LIFE.SAT       16.000
## 
## Regressions:
##   i ~
##     group             0.017    0.009    2.011    0.044
##   s ~
##     group             0.006    0.007    0.942    0.346
##   q ~
##     group            -0.003    0.002   -1.554    0.120
## 
## Covariances:
##   i ~~
##     s                 0.005    0.002    2.047    0.041
##     q                -0.002    0.001   -2.307    0.021
##   s ~~
##     q                -0.002    0.001   -2.534    0.011
## 
## Intercepts:
##     W0LIFE.SAT        0.000
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        0.000
##     W3LIFE.SAT        0.000
##     W4LIFE.SAT        0.000
##     W5LIFE.SAT        0.000
##     i                 3.573    0.009  413.449    0.000
##     s                 0.007    0.007    1.002    0.317
##     q                -0.008    0.002   -4.130    0.000
## 
## Variances:
##     W0LIFE.SAT        0.158    0.007
##     W1LIFE.SAT        0.151    0.005
##     W2LIFE.SAT        0.147    0.005
##     W3LIFE.SAT        0.140    0.005
##     W4LIFE.SAT        0.137    0.005
##     W5LIFE.SAT        0.140    0.010
##     i                 0.101    0.004
##     s                 0.009    0.003
##     q                 0.001    0.000
```

```
## Percentage Missing:
```

```
## W1LIFE.SAT W2LIFE.SAT W3LIFE.SAT W4LIFE.SAT W5LIFE.SAT W0LIFE.SAT 
##   0.001779   0.076957   0.126335   0.190836   0.250445   0.007117
```

```
## W1LIFE.SAT W2LIFE.SAT W3LIFE.SAT W4LIFE.SAT W5LIFE.SAT W0LIFE.SAT 
##   0.000000   0.088189   0.160630   0.206299   0.314961   0.001575
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

<a name="careerPros"></a>
CFA Growth - Career Prospects
-----------------------
Group Parameters not significant for Life Satisfaction so pooled model is plotted at the end of this section.


```
##       chisq df    cfi    tli   rmsea
## [1,] 183.39 16 0.9275 0.9321 0.06024
## [2,]  47.04 12 0.9848 0.9810 0.03183
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 24456 24546    47                                  
## fitL 16 24584 24650   183        136       4     <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-15) converged normally after  91 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        30
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               47.040
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.000
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W0CAREER.PROS     1.000
##     W1CAREER.PROS     1.000
##     W2CAREER.PROS     1.000
##     W3CAREER.PROS     1.000
##     W4CAREER.PROS     1.000
##     W5CAREER.PROS     1.000
##   s =~
##     W0CAREER.PROS    -1.000
##     W1CAREER.PROS     0.000
##     W2CAREER.PROS     1.000
##     W3CAREER.PROS     2.000
##     W4CAREER.PROS     3.000
##     W5CAREER.PROS     4.000
##   q =~
##     W0CAREER.PROS    -1.000
##     W1CAREER.PROS     0.000
##     W2CAREER.PROS     1.000
##     W3CAREER.PROS     4.000
##     W4CAREER.PROS     9.000
##     W5CAREER.PROS    16.000
## 
## Covariances:
##   i ~~
##     s                 0.009    0.003    2.557    0.011
##     q                -0.003    0.001   -3.750    0.000
##   s ~~
##     q                -0.007    0.001   -6.083    0.000
## 
## Intercepts:
##     W0CAREER.PROS     0.000
##     W1CAREER.PROS     0.000
##     W2CAREER.PROS     0.000
##     W3CAREER.PROS     0.000
##     W4CAREER.PROS     0.000
##     W5CAREER.PROS     0.000
##     i                 3.371    0.008  440.773    0.000
##     s                 0.050    0.007    7.172    0.000
##     q                -0.016    0.002   -7.713    0.000
## 
## Variances:
##     W0CAREER.PROS     0.223    0.010
##     W1CAREER.PROS     0.206    0.007
##     W2CAREER.PROS     0.191    0.007
##     W3CAREER.PROS     0.197    0.007
##     W4CAREER.PROS     0.228    0.008
##     W5CAREER.PROS     0.167    0.016
##     i                 0.103    0.005
##     s                 0.028    0.004
##     q                 0.003    0.000
```

```
## lavaan (0.5-15) converged normally after  94 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        30
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               49.045
##   Degrees of freedom                                15
##   P-value (Chi-square)                           0.000
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W0CAREER.PROS     1.000
##     W1CAREER.PROS     1.000
##     W2CAREER.PROS     1.000
##     W3CAREER.PROS     1.000
##     W4CAREER.PROS     1.000
##     W5CAREER.PROS     1.000
##   s =~
##     W0CAREER.PROS    -1.000
##     W1CAREER.PROS     0.000
##     W2CAREER.PROS     1.000
##     W3CAREER.PROS     2.000
##     W4CAREER.PROS     3.000
##     W5CAREER.PROS     4.000
##   q =~
##     W0CAREER.PROS    -1.000
##     W1CAREER.PROS     0.000
##     W2CAREER.PROS     1.000
##     W3CAREER.PROS     4.000
##     W4CAREER.PROS     9.000
##     W5CAREER.PROS    16.000
## 
## Regressions:
##   i ~
##     group            -0.011    0.009   -1.173    0.241
##   s ~
##     group             0.022    0.008    2.599    0.009
##   q ~
##     group            -0.006    0.002   -2.382    0.017
## 
## Covariances:
##   i ~~
##     s                 0.009    0.003    2.570    0.010
##     q                -0.003    0.001   -3.768    0.000
##   s ~~
##     q                -0.007    0.001   -6.054    0.000
## 
## Intercepts:
##     W0CAREER.PROS     0.000
##     W1CAREER.PROS     0.000
##     W2CAREER.PROS     0.000
##     W3CAREER.PROS     0.000
##     W4CAREER.PROS     0.000
##     W5CAREER.PROS     0.000
##     i                 3.365    0.009  364.855    0.000
##     s                 0.063    0.008    7.386    0.000
##     q                -0.019    0.002   -7.677    0.000
## 
## Variances:
##     W0CAREER.PROS     0.223    0.010
##     W1CAREER.PROS     0.206    0.007
##     W2CAREER.PROS     0.191    0.007
##     W3CAREER.PROS     0.197    0.007
##     W4CAREER.PROS     0.228    0.008
##     W5CAREER.PROS     0.167    0.016
##     i                 0.103    0.005
##     s                 0.028    0.004
##     q                 0.003    0.000
```

```
## Percentage Missing:
```

```
## W1CAREER.PROS W2CAREER.PROS W3CAREER.PROS W4CAREER.PROS W5CAREER.PROS 
##       0.01157       0.08274       0.13390       0.19395       0.25445 
## W0CAREER.PROS 
##       0.01557
```

```
## W1CAREER.PROS W2CAREER.PROS W3CAREER.PROS W4CAREER.PROS W5CAREER.PROS 
##      0.006299      0.097638      0.170079      0.211024      0.319685 
## W0CAREER.PROS 
##      0.009449
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 


<a name="futPros"></a>
CFA Growth - Future Prospects
-----------------------
Group Parameters not significant for Life Satisfaction so pooled model is plotted at the end of this section.


```
##       chisq df    cfi    tli   rmsea
## [1,] 86.236 16 0.9716 0.9734 0.03902
## [2,]  6.743 12 1.0000 1.0027 0.00000
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 21531 21620  6.74                                  
## fitL 16 21602 21668 86.24       79.5       4    2.2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-15) converged normally after  95 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        32
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic                6.743
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.874
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W0FUTURE.PROS     1.000
##     W1FUTURE.PROS     1.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     1.000
##     W4FUTURE.PROS     1.000
##     W5FUTURE.PROS     1.000
##   s =~
##     W0FUTURE.PROS    -1.000
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     2.000
##     W4FUTURE.PROS     3.000
##     W5FUTURE.PROS     4.000
##   q =~
##     W0FUTURE.PROS    -1.000
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     4.000
##     W4FUTURE.PROS     9.000
##     W5FUTURE.PROS    16.000
## 
## Covariances:
##   i ~~
##     s                 0.006    0.003    2.019    0.043
##     q                -0.002    0.001   -2.977    0.003
##   s ~~
##     q                -0.005    0.001   -4.892    0.000
## 
## Intercepts:
##     W0FUTURE.PROS     0.000
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     0.000
##     W3FUTURE.PROS     0.000
##     W4FUTURE.PROS     0.000
##     W5FUTURE.PROS     0.000
##     i                 3.395    0.007  472.384    0.000
##     s                 0.044    0.006    6.860    0.000
##     q                -0.010    0.002   -5.715    0.000
## 
## Variances:
##     W0FUTURE.PROS     0.197    0.009
##     W1FUTURE.PROS     0.176    0.006
##     W2FUTURE.PROS     0.169    0.006
##     W3FUTURE.PROS     0.179    0.007
##     W4FUTURE.PROS     0.158    0.006
##     W5FUTURE.PROS     0.145    0.012
##     i                 0.092    0.004
##     s                 0.019    0.004
##     q                 0.002    0.000
```

```
## lavaan (0.5-15) converged normally after  95 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        32
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic                6.743
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.874
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W0FUTURE.PROS     1.000
##     W1FUTURE.PROS     1.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     1.000
##     W4FUTURE.PROS     1.000
##     W5FUTURE.PROS     1.000
##   s =~
##     W0FUTURE.PROS    -1.000
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     2.000
##     W4FUTURE.PROS     3.000
##     W5FUTURE.PROS     4.000
##   q =~
##     W0FUTURE.PROS    -1.000
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     4.000
##     W4FUTURE.PROS     9.000
##     W5FUTURE.PROS    16.000
## 
## Covariances:
##   i ~~
##     s                 0.006    0.003    2.019    0.043
##     q                -0.002    0.001   -2.977    0.003
##   s ~~
##     q                -0.005    0.001   -4.892    0.000
## 
## Intercepts:
##     W0FUTURE.PROS     0.000
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     0.000
##     W3FUTURE.PROS     0.000
##     W4FUTURE.PROS     0.000
##     W5FUTURE.PROS     0.000
##     i                 3.395    0.007  472.384    0.000
##     s                 0.044    0.006    6.860    0.000
##     q                -0.010    0.002   -5.715    0.000
## 
## Variances:
##     W0FUTURE.PROS     0.197    0.009
##     W1FUTURE.PROS     0.176    0.006
##     W2FUTURE.PROS     0.169    0.006
##     W3FUTURE.PROS     0.179    0.007
##     W4FUTURE.PROS     0.158    0.006
##     W5FUTURE.PROS     0.145    0.012
##     i                 0.092    0.004
##     s                 0.019    0.004
##     q                 0.002    0.000
```

```
## Percentage Missing:
```

```
## W1FUTURE.PROS W2FUTURE.PROS W3FUTURE.PROS W4FUTURE.PROS W5FUTURE.PROS 
##       0.01068       0.08185       0.13390       0.19573       0.25578
```

```
## W1FUTURE.PROS W2FUTURE.PROS W3FUTURE.PROS W4FUTURE.PROS W5FUTURE.PROS 
##      0.006299      0.092913      0.166929      0.207874      0.318110
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5.png) 

