Gap Years in Australia: Effects on Multidimensional Life Satisfaction
========================================================
<a name="top"></a>

Contents:

1. [Data Munging](#SQL)
2. [Cohort Sequence Design](#cohort)
3. [Growth Curve: General Life Satisfaction](#lifeSat)
4. [Growth Curve: Satisfaction with Career Prospects](#careerPros)
5. [Growth Curve: Satisfaction with Future Prospects](#futPros)
6. [Propensity Score Matching](#PSM)
7. [Matched Growth: Life Satisfaction](#Mls)
8. [Matched Growth: Career Prospects](#Mcp)
9. [Matched Growth: Future Prospects](#Mfp)

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

[top](#top)

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




```
## Loading required package: ggplot2
## Loading required package: MatchIt
## Loading required package: MASS
```

[top](#top)

<a name="lifeSat"></a>
CFA Growth - Life Satisfaction
-----------------------

Group Parameters significant for Life Satisfaction so this model is plotted at the end of this section.


```
##      chisq df    cfi    tli   rmsea
## [1,] 63.51 16 0.9869 0.9877 0.03209
## [2,] 37.86 12 0.9928 0.9911 0.02734
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 19410 19499  37.9                                  
## fitL 16 19428 19493  63.5       25.7       4    3.7e-05 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-16) converged normally after  97 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        16
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               37.857
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.000
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0LIFE.SAT        1.000                               0.317    0.627
##     W1LIFE.SAT        1.000                               0.317    0.630
##     W2LIFE.SAT        1.000                               0.317    0.621
##     W3LIFE.SAT        1.000                               0.317    0.619
##     W4LIFE.SAT        1.000                               0.317    0.619
##     W5LIFE.SAT        1.000                               0.317    0.601
##   s =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.113    0.225
##     W2LIFE.SAT        2.000                               0.227    0.444
##     W3LIFE.SAT        3.000                               0.340    0.663
##     W4LIFE.SAT        4.000                               0.454    0.884
##     W5LIFE.SAT        5.000                               0.567    1.074
##   q =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.019    0.038
##     W2LIFE.SAT        4.000                               0.076    0.149
##     W3LIFE.SAT        9.000                               0.172    0.334
##     W4LIFE.SAT       16.000                               0.305    0.594
##     W5LIFE.SAT       25.000                               0.477    0.903
## 
## Covariances:
##   i ~~
##     s                -0.003    0.006   -0.607    0.544   -0.094   -0.094
##     q                 0.000    0.001    0.057    0.955    0.009    0.009
##   s ~~
##     q                -0.002    0.001   -2.239    0.025   -0.897   -0.897
## 
## Intercepts:
##     s         (b)     0.003    0.007    0.401    0.689    0.024    0.024
##     q         (c)    -0.004    0.001   -3.063    0.002   -0.213   -0.213
##     W0LIFE.SA         0.000                               0.000    0.000
##     W1LIFE.SA         0.000                               0.000    0.000
##     W2LIFE.SA         0.000                               0.000    0.000
##     W3LIFE.SA         0.000                               0.000    0.000
##     W4LIFE.SA         0.000                               0.000    0.000
##     W5LIFE.SA         0.000                               0.000    0.000
##     i                 3.568    0.009  398.023    0.000   11.238   11.238
## 
## Variances:
##     W0LIFE.SAT        0.156    0.008                      0.156    0.607
##     W1LIFE.SAT        0.151    0.005                      0.151    0.593
##     W2LIFE.SAT        0.148    0.005                      0.148    0.564
##     W3LIFE.SAT        0.141    0.005                      0.141    0.537
##     W4LIFE.SAT        0.137    0.005                      0.137    0.522
##     W5LIFE.SAT        0.145    0.009                      0.145    0.522
##     i                 0.101    0.008                      1.000    1.000
##     s                 0.013    0.005                      1.000    1.000
##     q                 0.000    0.000                      1.000    1.000
```

```
##      chisq df    cfi    tli   rmsea
## [1,] 63.51 16 0.9869 0.9877 0.03209
## [2,] 37.86 12 0.9928 0.9911 0.02734
## [3,] 48.89 15 0.9907 0.9869 0.02799
```

```
## lavaan (0.5-16) converged normally after 103 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        16
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               48.890
##   Degrees of freedom                                15
##   P-value (Chi-square)                           0.000
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0LIFE.SAT        1.000                               0.317    0.627
##     W1LIFE.SAT        1.000                               0.317    0.630
##     W2LIFE.SAT        1.000                               0.317    0.620
##     W3LIFE.SAT        1.000                               0.317    0.619
##     W4LIFE.SAT        1.000                               0.317    0.619
##     W5LIFE.SAT        1.000                               0.317    0.601
##   s =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.113    0.224
##     W2LIFE.SAT        2.000                               0.226    0.441
##     W3LIFE.SAT        3.000                               0.338    0.660
##     W4LIFE.SAT        4.000                               0.451    0.880
##     W5LIFE.SAT        5.000                               0.564    1.069
##   q =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.019    0.038
##     W2LIFE.SAT        4.000                               0.076    0.148
##     W3LIFE.SAT        9.000                               0.170    0.332
##     W4LIFE.SAT       16.000                               0.302    0.589
##     W5LIFE.SAT       25.000                               0.472    0.895
## 
## Regressions:
##   i ~
##     group             0.010    0.011    0.964    0.335    0.033    0.027
##   s ~
##     group    (g1)     0.013    0.008    1.530    0.126    0.113    0.093
##   q ~
##     group    (g2)    -0.003    0.002   -2.033    0.042   -0.174   -0.144
## 
## Covariances:
##   i ~~
##     s                -0.003    0.006   -0.611    0.541   -0.095   -0.095
##     q                 0.000    0.001    0.062    0.951    0.010    0.010
##   s ~~
##     q                -0.002    0.001   -2.174    0.030   -0.896   -0.896
## 
## Intercepts:
##     s         (b)     0.010    0.008    1.213    0.225    0.089    0.089
##     q         (c)    -0.006    0.002   -3.691    0.000   -0.315   -0.315
##     W0LIFE.SA         0.000                               0.000    0.000
##     W1LIFE.SA         0.000                               0.000    0.000
##     W2LIFE.SA         0.000                               0.000    0.000
##     W3LIFE.SA         0.000                               0.000    0.000
##     W4LIFE.SA         0.000                               0.000    0.000
##     W5LIFE.SA         0.000                               0.000    0.000
##     i                 3.574    0.011  331.468    0.000   11.258   11.258
## 
## Variances:
##     W0LIFE.SAT        0.156    0.008                      0.156    0.607
##     W1LIFE.SAT        0.150    0.005                      0.150    0.592
##     W2LIFE.SAT        0.148    0.005                      0.148    0.565
##     W3LIFE.SAT        0.141    0.005                      0.141    0.537
##     W4LIFE.SAT        0.137    0.005                      0.137    0.522
##     W5LIFE.SAT        0.146    0.009                      0.146    0.522
##     i                 0.101    0.008                      0.999    0.999
##     s                 0.013    0.005                      0.991    0.991
##     q                 0.000    0.000                      0.979    0.979
## 
## Defined parameters:
##     tpG1             -0.489    1.708   -0.286    0.775   -0.082   -0.012
##     tpG2              1.233    0.449    2.743    0.006    0.206    0.199
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

![plot of chunk lifeSat](figure/lifeSat.png) 

[top](#top)

<a name="careerPros"></a>
CFA Growth - Career Prospects
-----------------------
Group Parameters not significant for Life Satisfaction so pooled model is plotted at the end of this section.


```
##       chisq df    cfi    tli   rmsea
## [1,] 183.39 16 0.9275 0.9321 0.06024
## [2,]  52.91 12 0.9823 0.9779 0.03439
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 24462 24551  52.9                                  
## fitL 16 24584 24650 183.4        130       4     <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-16) converged normally after  81 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        30
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               52.906
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.000
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0CAREER.PROS     1.000                               0.336    0.587
##     W1CAREER.PROS     1.000                               0.336    0.602
##     W2CAREER.PROS     1.000                               0.336    0.594
##     W3CAREER.PROS     1.000                               0.336    0.577
##     W4CAREER.PROS     1.000                               0.336    0.551
##     W5CAREER.PROS     1.000                               0.336    0.546
##   s =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.208    0.372
##     W2CAREER.PROS     2.000                               0.416    0.734
##     W3CAREER.PROS     3.000                               0.624    1.070
##     W4CAREER.PROS     4.000                               0.832    1.362
##     W5CAREER.PROS     5.000                               1.040    1.688
##   q =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.041    0.073
##     W2CAREER.PROS     4.000                               0.164    0.290
##     W3CAREER.PROS     9.000                               0.370    0.634
##     W4CAREER.PROS    16.000                               0.657    1.077
##     W5CAREER.PROS    25.000                               1.027    1.668
## 
## Covariances:
##   i ~~
##     s                -0.019    0.008   -2.292    0.022   -0.266   -0.266
##     q                 0.002    0.001    1.552    0.121    0.154    0.154
##   s ~~
##     q                -0.008    0.001   -5.894    0.000   -0.924   -0.924
## 
## Intercepts:
##     s         (b)     0.060    0.009    6.966    0.000    0.289    0.289
##     q         (c)    -0.012    0.002   -7.310    0.000   -0.300   -0.300
##     W0CAREER.         0.000                               0.000    0.000
##     W1CAREER.         0.000                               0.000    0.000
##     W2CAREER.         0.000                               0.000    0.000
##     W3CAREER.         0.000                               0.000    0.000
##     W4CAREER.         0.000                               0.000    0.000
##     W5CAREER.         0.000                               0.000    0.000
##     i                 3.333    0.010  329.474    0.000    9.905    9.905
## 
## Variances:
##     W0CAREER.PROS     0.216    0.012                      0.216    0.656
##     W1CAREER.PROS     0.203    0.007                      0.203    0.650
##     W2CAREER.PROS     0.192    0.007                      0.192    0.597
##     W3CAREER.PROS     0.201    0.007                      0.201    0.590
##     W4CAREER.PROS     0.227    0.008                      0.227    0.610
##     W5CAREER.PROS     0.184    0.014                      0.184    0.486
##     i                 0.113    0.011                      1.000    1.000
##     s                 0.043    0.007                      1.000    1.000
##     q                 0.002    0.000                      1.000    1.000
```

```
## lavaan (0.5-16) converged normally after  84 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        30
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               54.005
##   Degrees of freedom                                15
##   P-value (Chi-square)                           0.000
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0CAREER.PROS     1.000                               0.337    0.588
##     W1CAREER.PROS     1.000                               0.337    0.603
##     W2CAREER.PROS     1.000                               0.337    0.595
##     W3CAREER.PROS     1.000                               0.337    0.578
##     W4CAREER.PROS     1.000                               0.337    0.552
##     W5CAREER.PROS     1.000                               0.337    0.547
##   s =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.209    0.373
##     W2CAREER.PROS     2.000                               0.417    0.737
##     W3CAREER.PROS     3.000                               0.626    1.073
##     W4CAREER.PROS     4.000                               0.834    1.367
##     W5CAREER.PROS     5.000                               1.043    1.693
##   q =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.041    0.074
##     W2CAREER.PROS     4.000                               0.165    0.291
##     W3CAREER.PROS     9.000                               0.371    0.636
##     W4CAREER.PROS    16.000                               0.659    1.080
##     W5CAREER.PROS    25.000                               1.030    1.672
## 
## Regressions:
##   i ~
##     group            -0.030    0.012   -2.501    0.012   -0.090   -0.075
##   s ~
##     group    (g1)     0.029    0.010    2.749    0.006    0.138    0.114
##   q ~
##     group    (g2)    -0.005    0.002   -2.547    0.011   -0.127   -0.105
## 
## Covariances:
##   i ~~
##     s                -0.018    0.008   -2.267    0.023   -0.264   -0.264
##     q                 0.002    0.001    1.520    0.128    0.151    0.151
##   s ~~
##     q                -0.008    0.001   -5.866    0.000   -0.924   -0.924
## 
## Intercepts:
##     s         (b)     0.076    0.010    7.303    0.000    0.366    0.366
##     q         (c)    -0.015    0.002   -7.450    0.000   -0.372   -0.372
##     W0CAREER.         0.000                               0.000    0.000
##     W1CAREER.         0.000                               0.000    0.000
##     W2CAREER.         0.000                               0.000    0.000
##     W3CAREER.         0.000                               0.000    0.000
##     W4CAREER.         0.000                               0.000    0.000
##     W5CAREER.         0.000                               0.000    0.000
##     i                 3.316    0.012  272.383    0.000    9.837    9.837
## 
## Variances:
##     W0CAREER.PROS     0.215    0.012                      0.215    0.654
##     W1CAREER.PROS     0.203    0.007                      0.203    0.650
##     W2CAREER.PROS     0.191    0.007                      0.191    0.597
##     W3CAREER.PROS     0.201    0.007                      0.201    0.591
##     W4CAREER.PROS     0.227    0.008                      0.227    0.610
##     W5CAREER.PROS     0.184    0.014                      0.184    0.485
##     i                 0.113    0.011                      0.994    0.994
##     s                 0.043    0.007                      0.987    0.987
##     q                 0.002    0.000                      0.989    0.989
## 
## Defined parameters:
##     tpG1              2.362    0.154   15.330    0.000    0.466    0.473
##     tpG2              2.556    0.147   17.399    0.000    0.505    0.503
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

![plot of chunk careerPros](figure/careerPros.png) 

[top](#top)

<a name="futPros"></a>
CFA Growth - Future Prospects
-----------------------
Group Parameters not significant for Life Satisfaction so pooled model is plotted at the end of this section.


```
##       chisq df    cfi    tli   rmsea
## [1,] 86.236 16 0.9716 0.9734 0.03902
## [2,]  6.061 12 1.0000 1.0030 0.00000
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 21530 21619  6.06                                  
## fitL 16 21602 21668 86.24       80.2       4     <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-16) converged normally after  88 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        32
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic                6.061
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.913
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
##     W0FUTURE.PROS     0.000
##     W1FUTURE.PROS     1.000
##     W2FUTURE.PROS     2.000
##     W3FUTURE.PROS     3.000
##     W4FUTURE.PROS     4.000
##     W5FUTURE.PROS     5.000
##   q =~
##     W0FUTURE.PROS     0.000
##     W1FUTURE.PROS     1.000
##     W2FUTURE.PROS     4.000
##     W3FUTURE.PROS     9.000
##     W4FUTURE.PROS    16.000
##     W5FUTURE.PROS    25.000
## 
## Covariances:
##   i ~~
##     s                -0.014    0.007   -2.078    0.038
##     q                 0.002    0.001    1.437    0.151
##   s ~~
##     q                -0.005    0.001   -4.793    0.000
## 
## Intercepts:
##     s         (b)     0.052    0.008    6.655    0.000
##     q         (c)    -0.009    0.002   -5.663    0.000
##     W0FUTURE.         0.000
##     W1FUTURE.         0.000
##     W2FUTURE.         0.000
##     W3FUTURE.         0.000
##     W4FUTURE.         0.000
##     W5FUTURE.         0.000
##     i                 3.358    0.009  353.857    0.000
## 
## Variances:
##     W0FUTURE.PROS     0.191    0.010
##     W1FUTURE.PROS     0.174    0.006
##     W2FUTURE.PROS     0.169    0.006
##     W3FUTURE.PROS     0.181    0.006
##     W4FUTURE.PROS     0.158    0.006
##     W5FUTURE.PROS     0.152    0.010
##     i                 0.100    0.010
##     s                 0.030    0.006
##     q                 0.001    0.000
```

```
## lavaan (0.5-16) converged normally after  88 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        32
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic                6.061
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.913
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0FUTURE.PROS     1.000                               0.317    0.587
##     W1FUTURE.PROS     1.000                               0.317    0.609
##     W2FUTURE.PROS     1.000                               0.317    0.599
##     W3FUTURE.PROS     1.000                               0.317    0.579
##     W4FUTURE.PROS     1.000                               0.317    0.603
##     W5FUTURE.PROS     1.000                               0.317    0.590
##   s =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.174    0.335
##     W2FUTURE.PROS     2.000                               0.349    0.659
##     W3FUTURE.PROS     3.000                               0.523    0.957
##     W4FUTURE.PROS     4.000                               0.697    1.328
##     W5FUTURE.PROS     5.000                               0.871    1.625
##   q =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.032    0.062
##     W2FUTURE.PROS     4.000                               0.130    0.246
##     W3FUTURE.PROS     9.000                               0.292    0.534
##     W4FUTURE.PROS    16.000                               0.519    0.989
##     W5FUTURE.PROS    25.000                               0.811    1.513
## 
## Covariances:
##   i ~~
##     s                -0.014    0.007   -2.078    0.038   -0.258   -0.258
##     q                 0.002    0.001    1.437    0.151    0.161    0.161
##   s ~~
##     q                -0.005    0.001   -4.793    0.000   -0.935   -0.935
## 
## Intercepts:
##     s         (b)     0.052    0.008    6.655    0.000    0.301    0.301
##     q         (c)    -0.009    0.002   -5.663    0.000   -0.264   -0.264
##     W0FUTURE.         0.000                               0.000    0.000
##     W1FUTURE.         0.000                               0.000    0.000
##     W2FUTURE.         0.000                               0.000    0.000
##     W3FUTURE.         0.000                               0.000    0.000
##     W4FUTURE.         0.000                               0.000    0.000
##     W5FUTURE.         0.000                               0.000    0.000
##     i                 3.358    0.009  353.857    0.000   10.607   10.607
## 
## Variances:
##     W0FUTURE.PROS     0.191    0.010                      0.191    0.656
##     W1FUTURE.PROS     0.174    0.006                      0.174    0.645
##     W2FUTURE.PROS     0.169    0.006                      0.169    0.606
##     W3FUTURE.PROS     0.181    0.006                      0.181    0.607
##     W4FUTURE.PROS     0.158    0.006                      0.158    0.574
##     W5FUTURE.PROS     0.152    0.010                      0.152    0.530
##     i                 0.100    0.010                      1.000    1.000
##     s                 0.030    0.006                      1.000    1.000
##     q                 0.001    0.000                      1.000    1.000
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

![plot of chunk futurePros](figure/futurePros.png) 

[top](#top)

Extract Matching Variables
----------------------------

```
## [1] "matching Features"
```

```
##      Variable                                             Label
## 2     stateid                                   State/Territory
## 4    schoolid                                         School ID
## 7         loc                                 MCEETYA Loc Class
## 8         sex                                 Sex of respondent
## 9       indig                                Final Indig Status
## 385    sisced     Expected educational level of student (ISCED)
## 395      escs                   Economic social cultural status
## 398    belong                Sense of belonging to school (WLE)
## 399    intmat                     Interest in mathematics (WLE)
## 400   instmot      Instrumental motivation in mathematics (WLE)
## 401   matheff                   Mathematics self-efficacy (WLE)
## 402    anxmat                         Mathematics anxiety (WLE)
## 403     scmat                    Mathematics self-concept (WLE)
## 407   complrn                        Competitive learning (WLE)
## 408   cooplrn                       Co-operative learning (WLE)
## 409  teachsup            Teacher support in maths lessons (WLE)
## 410   disclim       Disciplinary climate in maths lessons (WLE)
## 432    laa005                   A5 Respondent post-school plans
## 433    laa006                 A6 Parent post-school aspirations
## 434    laa007                  A7 Peer post-school expectations
## 670    laa025         A25 Self-assessment of literacy (English)
## 671    laa026     A26 Self-assessment of numeracy (Mathematics)
## 672    laa027                       A27 Overall self-assessment
## 729    lad001                              D1 Currently working
## 5196 xcsl2003            Derived: XCSL2003 Current school level
## 5364 xath2003           Derived: XATH2003 Living with parent(s)
## 10    pv1math                           Plausible value in math
## 15   pv1math1         Plausible value in math - Space and Shape
## 20   pv1math2 Plausible value in math- Change and Relationships
## 25   pv1math3             Plausible value in math - Uncertainty
## 30   pv1math4                Plausible value in math - Quantity
## 35    pv1read                        Plausible value in reading
## 40    pv1scie                        Plausible value in science
## 45    pv1prob                Plausible value in problem solving
## 238   st30q01                       Attitude enjoy reading Q30a
## 239   st30q02                              Attitude effort Q30b
## 240   st30q03                        Attitude look forward Q30c
## 241   st30q04                        Attitude enjoy Maths  Q30d
## 242   st30q05                             Attitude career  Q30e
## 243   st30q06                          Attitude interested Q30f
## 244   st30q07                       Attitude further study Q30g
## 245   st30q08                                Attitude job  Q30h
```

```
##       id  stateid schoolid      loc      sex   sisced    indig   laa005 
## 0.000000 0.000000 0.000000 0.000000 0.000000 0.001350 0.000000 0.000000 
##   laa006     escs   laa007   laa025   laa026   laa027 xcsl2003   lad001 
## 0.000000 0.006075 0.000000 0.000000 0.000000 0.000000 0.000000 0.000000 
## xath2003   belong   intmat  instmot  matheff   anxmat    scmat  complrn 
## 0.000000 0.002218 0.004339 0.003568 0.004147 0.004918 0.004532 0.009740 
##  cooplrn teachsup  disclim  pv1math pv1math1 pv1math2 pv1math3 pv1math4 
## 0.011668 0.012825 0.013693 0.000000 0.000000 0.000000 0.000000 0.000000 
##  pv1read  pv1scie  pv1prob  st30q01  st30q02  st30q03  st30q04  st30q05 
## 0.000000 0.000000 0.000000 0.006943 0.006365 0.014272 0.012150 0.006750 
##  st30q06  st30q07  st30q08 
## 0.014272 0.010029 0.008968
```

```
## Loading required package: foreign
## Loading required package: Rcpp
## Loading required package: RcppArmadillo
## ## 
## ## Amelia II: Multiple Imputation
## ## (Version 1.7.2, built: 2013-04-03)
## ## Copyright (C) 2005-2014 James Honaker, Gary King and Matthew Blackwell
## ## Refer to http://gking.harvard.edu/amelia/ for more information
## ##
```

```
## -- Imputation 1 --
## 
##   1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
##  21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37
```

[top](#top)

<a name="PSM"></a>
Propensity score matching
-----------------------------

```
## Formula:
##  group ~  sex + sisced + indig + laa005 + laa006 + escs + laa007 + laa025 + laa026 + laa027 + xcsl2003 + lad001 + belong + intmat + instmot + matheff + anxmat + scmat + complrn + cooplrn + teachsup + disclim + pv1math + pv1math1 + pv1math2 + pv1math3 + pv1math4 + pv1read + pv1scie + pv1prob + st30q01 + st30q02 + st30q03 + st30q04 + st30q05 + st30q06 + st30q07 + st30q08 + preLIFE.SAT + preCAREER.PROS + preFUTURE.PROS + Sses + Smath + Sread + Sscie + Sprob
```

```
## [1] m_mean_diff
## <0 rows> (or 0-length row.names)
```

![plot of chunk PSM](figure/PSM1.png) ![plot of chunk PSM](figure/PSM2.png) 

```
## 
##  Large Medium  Small 
##     99     47   1029
```

```
## 
## Small 
##  1175
```

```
## [1] 2152
```

```
## group
##    0    1 
## 1538  614
```

[top](#top)
<a name="Mls"></a>


Matched Life Satisfaction
-------------------------------


```
## Warning: Estimator 'ML' will not correct standard errors and chi-square statistic.
## Warning: Estimator 'ML' will not correct standard errors and chi-square statistic.
## Warning: Estimator 'ML' will not correct standard errors and chi-square statistic.
```

```
##      chisq df    cfi    tli   rmsea
## [1,] 66.28 16 0.9837 0.9847 0.03865
## [2,] 33.94 12 0.9929 0.9911 0.02948
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 15715 15800  33.9                                  
## fitL 16 15740 15802  66.3       32.3       4    1.6e-06 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-16) converged normally after  79 iterations
## 
##   Number of observations                          2104
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               33.937
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.001
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0LIFE.SAT        1.000                               0.326    0.652
##     W1LIFE.SAT        1.000                               0.326    0.654
##     W2LIFE.SAT        1.000                               0.326    0.641
##     W3LIFE.SAT        1.000                               0.326    0.637
##     W4LIFE.SAT        1.000                               0.326    0.638
##     W5LIFE.SAT        1.000                               0.326    0.622
##   s =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.125    0.250
##     W2LIFE.SAT        2.000                               0.249    0.491
##     W3LIFE.SAT        3.000                               0.374    0.731
##     W4LIFE.SAT        4.000                               0.499    0.976
##     W5LIFE.SAT        5.000                               0.624    1.190
##   q =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.019    0.037
##     W2LIFE.SAT        4.000                               0.075    0.147
##     W3LIFE.SAT        9.000                               0.168    0.328
##     W4LIFE.SAT       16.000                               0.299    0.584
##     W5LIFE.SAT       25.000                               0.467    0.890
## 
## Covariances:
##   i ~~
##     s                -0.009    0.006   -1.427    0.154   -0.214   -0.214
##     q                 0.001    0.001    0.623    0.533    0.103    0.103
##   s ~~
##     q                -0.002    0.001   -2.330    0.020   -0.907   -0.907
## 
## Intercepts:
##     s         (b)     0.007    0.008    0.925    0.355    0.056    0.056
##     q         (c)    -0.006    0.001   -3.886    0.000   -0.296   -0.296
##     W0LIFE.SA         0.000                               0.000    0.000
##     W1LIFE.SA         0.000                               0.000    0.000
##     W2LIFE.SA         0.000                               0.000    0.000
##     W3LIFE.SA         0.000                               0.000    0.000
##     W4LIFE.SA         0.000                               0.000    0.000
##     W5LIFE.SA         0.000                               0.000    0.000
##     i                 3.588    0.010  346.222    0.000   11.015   11.015
## 
## Variances:
##     W0LIFE.SAT        0.144    0.009                      0.144    0.575
##     W1LIFE.SAT        0.146    0.005                      0.146    0.590
##     W2LIFE.SAT        0.148    0.006                      0.148    0.573
##     W3LIFE.SAT        0.142    0.005                      0.142    0.543
##     W4LIFE.SAT        0.136    0.005                      0.136    0.523
##     W5LIFE.SAT        0.145    0.009                      0.145    0.528
##     i                 0.106    0.009                      1.000    1.000
##     s                 0.016    0.005                      1.000    1.000
##     q                 0.000    0.000                      1.000    1.000
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```
##      chisq df    cfi    tli   rmsea
## [1,] 66.28 16 0.9837 0.9847 0.03865
## [2,] 33.94 12 0.9929 0.9911 0.02948
## [3,] 49.79 15 0.9888 0.9843 0.03320
```

```
## lavaan (0.5-16) converged normally after  97 iterations
## 
##   Number of observations                          2104
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               49.791
##   Degrees of freedom                                15
##   P-value (Chi-square)                           0.000
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0LIFE.SAT        1.000                               0.327    0.654
##     W1LIFE.SAT        1.000                               0.327    0.656
##     W2LIFE.SAT        1.000                               0.327    0.642
##     W3LIFE.SAT        1.000                               0.327    0.639
##     W4LIFE.SAT        1.000                               0.327    0.639
##     W5LIFE.SAT        1.000                               0.327    0.623
##   s =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.126    0.252
##     W2LIFE.SAT        2.000                               0.251    0.494
##     W3LIFE.SAT        3.000                               0.377    0.737
##     W4LIFE.SAT        4.000                               0.502    0.983
##     W5LIFE.SAT        5.000                               0.628    1.198
##   q =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.019    0.038
##     W2LIFE.SAT        4.000                               0.075    0.147
##     W3LIFE.SAT        9.000                               0.169    0.330
##     W4LIFE.SAT       16.000                               0.300    0.587
##     W5LIFE.SAT       25.000                               0.468    0.894
## 
## Regressions:
##   i ~
##     group.x          -0.029    0.023   -1.243    0.214   -0.088   -0.039
##   s ~
##     group.x  (g1)     0.038    0.017    2.265    0.024    0.304    0.136
##   q ~
##     group.x  (g2)    -0.008    0.003   -2.453    0.014   -0.414   -0.185
## 
## Covariances:
##   i ~~
##     s                -0.009    0.006   -1.454    0.146   -0.218   -0.218
##     q                 0.001    0.001    0.635    0.526    0.106    0.106
##   s ~~
##     q                -0.002    0.001   -2.299    0.022   -0.907   -0.907
## 
## Intercepts:
##     s         (b)    -0.004    0.009   -0.409    0.682   -0.029   -0.029
##     q         (c)    -0.003    0.002   -2.011    0.044   -0.179   -0.179
##     W0LIFE.SA         0.000                               0.000    0.000
##     W1LIFE.SA         0.000                               0.000    0.000
##     W2LIFE.SA         0.000                               0.000    0.000
##     W3LIFE.SA         0.000                               0.000    0.000
##     W4LIFE.SA         0.000                               0.000    0.000
##     W5LIFE.SA         0.000                               0.000    0.000
##     i                 3.596    0.012  294.584    0.000   11.012   11.012
## 
## Variances:
##     W0LIFE.SAT        0.143    0.009                      0.143    0.572
##     W1LIFE.SAT        0.146    0.005                      0.146    0.590
##     W2LIFE.SAT        0.148    0.006                      0.148    0.574
##     W3LIFE.SAT        0.142    0.005                      0.142    0.543
##     W4LIFE.SAT        0.136    0.005                      0.136    0.523
##     W5LIFE.SAT        0.145    0.009                      0.145    0.529
##     i                 0.106    0.009                      0.998    0.998
##     s                 0.015    0.005                      0.981    0.981
##     q                 0.000    0.000                      0.966    0.966
## 
## Defined parameters:
##     tpG1              4.762    2.310    2.061    0.039    0.710   13.563
##     tpG2              1.554    0.309    5.024    0.000    0.232    0.147
```

![plot of chunk MlifeSat](figure/MlifeSat.png) 

[top](#top)
<a name="Mcp"></a>


Matched Career Prospects
-------------------------------


```
## Warning: Estimator 'ML' will not correct standard errors and chi-square statistic.
## Warning: Estimator 'ML' will not correct standard errors and chi-square statistic.
## Warning: Estimator 'ML' will not correct standard errors and chi-square statistic.
```

```
##      chisq df    cfi    tli   rmsea
## [1,] 188.8 16 0.9149 0.9202 0.07164
## [2,]  34.9 12 0.9887 0.9859 0.03011
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 20082 20167  34.9                                  
## fitL 16 20228 20290 188.8        154       4     <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-16) converged normally after  94 iterations
## 
##   Number of observations                          2104
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               34.896
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.000
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0CAREER.PROS     1.000                               0.297    0.514
##     W1CAREER.PROS     1.000                               0.297    0.548
##     W2CAREER.PROS     1.000                               0.297    0.535
##     W3CAREER.PROS     1.000                               0.297    0.512
##     W4CAREER.PROS     1.000                               0.297    0.476
##     W5CAREER.PROS     1.000                               0.297    0.492
##   s =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.187    0.344
##     W2CAREER.PROS     2.000                               0.373    0.672
##     W3CAREER.PROS     3.000                               0.560    0.964
##     W4CAREER.PROS     4.000                               0.747    1.196
##     W5CAREER.PROS     5.000                               0.933    1.544
##   q =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.039    0.072
##     W2CAREER.PROS     4.000                               0.157    0.283
##     W3CAREER.PROS     9.000                               0.353    0.608
##     W4CAREER.PROS    16.000                               0.628    1.006
##     W5CAREER.PROS    25.000                               0.981    1.624
## 
## Covariances:
##   i ~~
##     s                -0.005    0.008   -0.535    0.593   -0.082   -0.082
##     q                -0.000    0.001   -0.070    0.944   -0.008   -0.008
##   s ~~
##     q                -0.007    0.001   -4.863    0.000   -0.907   -0.907
## 
## Intercepts:
##     s         (b)     0.076    0.010    8.008    0.000    0.408    0.408
##     q         (c)    -0.015    0.002   -8.269    0.000   -0.379   -0.379
##     W0CAREER.         0.000                               0.000    0.000
##     W1CAREER.         0.000                               0.000    0.000
##     W2CAREER.         0.000                               0.000    0.000
##     W3CAREER.         0.000                               0.000    0.000
##     W4CAREER.         0.000                               0.000    0.000
##     W5CAREER.         0.000                               0.000    0.000
##     i                 3.338    0.012  288.587    0.000   11.230   11.230
## 
## Variances:
##     W0CAREER.PROS     0.246    0.014                      0.246    0.736
##     W1CAREER.PROS     0.192    0.007                      0.192    0.653
##     W2CAREER.PROS     0.182    0.007                      0.182    0.588
##     W3CAREER.PROS     0.199    0.008                      0.199    0.589
##     W4CAREER.PROS     0.240    0.009                      0.240    0.615
##     W5CAREER.PROS     0.155    0.014                      0.155    0.425
##     i                 0.088    0.012                      1.000    1.000
##     s                 0.035    0.008                      1.000    1.000
##     q                 0.002    0.000                      1.000    1.000
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```
##       chisq df    cfi    tli   rmsea
## [1,] 188.78 16 0.9149 0.9202 0.07164
## [2,]  34.90 12 0.9887 0.9859 0.03011
## [3,]  36.15 15 0.9896 0.9854 0.02588
```

```
## lavaan (0.5-16) converged normally after  96 iterations
## 
##   Number of observations                          2104
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               36.145
##   Degrees of freedom                                15
##   P-value (Chi-square)                           0.002
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0CAREER.PROS     1.000                               0.297    0.514
##     W1CAREER.PROS     1.000                               0.297    0.548
##     W2CAREER.PROS     1.000                               0.297    0.535
##     W3CAREER.PROS     1.000                               0.297    0.511
##     W4CAREER.PROS     1.000                               0.297    0.476
##     W5CAREER.PROS     1.000                               0.297    0.492
##   s =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.187    0.344
##     W2CAREER.PROS     2.000                               0.373    0.671
##     W3CAREER.PROS     3.000                               0.560    0.963
##     W4CAREER.PROS     4.000                               0.746    1.196
##     W5CAREER.PROS     5.000                               0.933    1.543
##   q =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.039    0.072
##     W2CAREER.PROS     4.000                               0.157    0.283
##     W3CAREER.PROS     9.000                               0.353    0.608
##     W4CAREER.PROS    16.000                               0.628    1.006
##     W5CAREER.PROS    25.000                               0.981    1.624
## 
## Regressions:
##   i ~
##     group.x          -0.035    0.026   -1.370    0.171   -0.119   -0.053
##   s ~
##     group.x  (g1)     0.023    0.021    1.089    0.276    0.124    0.055
##   q ~
##     group.x  (g2)    -0.004    0.004   -1.089    0.276   -0.111   -0.050
## 
## Covariances:
##   i ~~
##     s                -0.004    0.008   -0.506    0.613   -0.078   -0.078
##     q                -0.000    0.001   -0.100    0.920   -0.012   -0.012
##   s ~~
##     q                -0.007    0.001   -4.847    0.000   -0.907   -0.907
## 
## Intercepts:
##     s         (b)     0.070    0.011    6.244    0.000    0.374    0.374
##     q         (c)    -0.014    0.002   -6.464    0.000   -0.348   -0.348
##     W0CAREER.         0.000                               0.000    0.000
##     W1CAREER.         0.000                               0.000    0.000
##     W2CAREER.         0.000                               0.000    0.000
##     W3CAREER.         0.000                               0.000    0.000
##     W4CAREER.         0.000                               0.000    0.000
##     W5CAREER.         0.000                               0.000    0.000
##     i                 3.347    0.014  246.398    0.000   11.271   11.271
## 
## Variances:
##     W0CAREER.PROS     0.246    0.014                      0.246    0.736
##     W1CAREER.PROS     0.192    0.007                      0.192    0.653
##     W2CAREER.PROS     0.182    0.007                      0.182    0.588
##     W3CAREER.PROS     0.199    0.008                      0.199    0.589
##     W4CAREER.PROS     0.240    0.009                      0.240    0.615
##     W5CAREER.PROS     0.155    0.014                      0.155    0.424
##     i                 0.088    0.012                      0.997    0.997
##     s                 0.035    0.008                      0.997    0.997
##     q                 0.002    0.000                      0.998    0.998
## 
## Defined parameters:
##     tpG1              2.514    0.482    5.214    0.000    0.529    0.535
##     tpG2              2.579    0.157   16.466    0.000    0.543    0.540
```

![plot of chunk McareerPros](figure/McareerPros.png) 

[top](#top)
<a name="Mfp"></a>


Matched Future Prospects
-------------------------------


```
## Error: lavaan ERROR: missing observed variables in dataset: W0FUTURE.PROSS
## W1FUTURE.PROSS W2FUTURE.PROSS W3FUTURE.PROSS W4FUTURE.PROSS W5FUTURE.PROSS
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```
## found:  W0CAREER.PROS W1CAREER.PROS W2CAREER.PROS W3CAREER.PROS W4CAREER.PROS W5CAREER.PROS 
## expected:  W0FUTURE.PROSS W1FUTURE.PROSS W2FUTURE.PROSS W3FUTURE.PROSS W4FUTURE.PROSS W5FUTURE.PROSS
```

```
## Error: lavaan ERROR: rownames of covariance matrix do not match the model!
##   found: W0CAREER.PROS W1CAREER.PROS W2CAREER.PROS W3CAREER.PROS W4CAREER.PROS W5CAREER.PROS
##   expected: W0FUTURE.PROSS W1FUTURE.PROSS W2FUTURE.PROSS W3FUTURE.PROSS W4FUTURE.PROSS W5FUTURE.PROSS
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square statistic.
## Warning: Estimator 'ML' will not correct standard errors and chi-square statistic.
```

```
##       chisq df    cfi    tli    rmsea
## [1,] 188.78 16 0.9149 0.9202 0.071642
## [2,]  12.16 12 0.9999 0.9999 0.002544
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 17674 17759  12.2                                  
## fitL 16 20228 20290 188.8        177       4     <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-16) converged normally after  82 iterations
## 
##   Number of observations                          2104
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               12.163
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.433
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0FUTURE.PROS     1.000                               0.303    0.561
##     W1FUTURE.PROS     1.000                               0.303    0.589
##     W2FUTURE.PROS     1.000                               0.303    0.584
##     W3FUTURE.PROS     1.000                               0.303    0.558
##     W4FUTURE.PROS     1.000                               0.303    0.586
##     W5FUTURE.PROS     1.000                               0.303    0.573
##   s =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.168    0.325
##     W2FUTURE.PROS     2.000                               0.336    0.646
##     W3FUTURE.PROS     3.000                               0.503    0.926
##     W4FUTURE.PROS     4.000                               0.671    1.297
##     W5FUTURE.PROS     5.000                               0.839    1.584
##   q =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.032    0.061
##     W2FUTURE.PROS     4.000                               0.127    0.244
##     W3FUTURE.PROS     9.000                               0.285    0.524
##     W4FUTURE.PROS    16.000                               0.506    0.978
##     W5FUTURE.PROS    25.000                               0.791    1.493
## 
## Covariances:
##   i ~~
##     s                -0.012    0.007   -1.663    0.096   -0.244   -0.244
##     q                 0.001    0.001    1.047    0.295    0.134    0.134
##   s ~~
##     q                -0.005    0.001   -4.242    0.000   -0.924   -0.924
## 
## Intercepts:
##     s         (b)     0.070    0.009    7.992    0.000    0.416    0.416
##     q         (c)    -0.011    0.002   -6.900    0.000   -0.357   -0.357
##     W0FUTURE.         0.000                               0.000    0.000
##     W1FUTURE.         0.000                               0.000    0.000
##     W2FUTURE.         0.000                               0.000    0.000
##     W3FUTURE.         0.000                               0.000    0.000
##     W4FUTURE.         0.000                               0.000    0.000
##     W5FUTURE.         0.000                               0.000    0.000
##     i                 3.360    0.011  306.817    0.000   11.072   11.072
## 
## Variances:
##     W0FUTURE.PROS     0.200    0.012                      0.200    0.685
##     W1FUTURE.PROS     0.177    0.007                      0.177    0.665
##     W2FUTURE.PROS     0.167    0.007                      0.167    0.619
##     W3FUTURE.PROS     0.185    0.007                      0.185    0.627
##     W4FUTURE.PROS     0.155    0.006                      0.155    0.580
##     W5FUTURE.PROS     0.146    0.010                      0.146    0.520
##     i                 0.092    0.011                      1.000    1.000
##     s                 0.028    0.007                      1.000    1.000
##     q                 0.001    0.000                      1.000    1.000
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```
##       chisq df    cfi    tli    rmsea
## [1,] 188.78 16 0.9149 0.9202 0.071642
## [2,]  12.16 12 0.9999 0.9999 0.002544
## [3,]  13.76 15 1.0000 1.0009 0.000000
```

```
## lavaan (0.5-16) converged normally after  81 iterations
## 
##   Number of observations                          2104
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               13.764
##   Degrees of freedom                                15
##   P-value (Chi-square)                           0.543
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0FUTURE.PROS     1.000                               0.303    0.561
##     W1FUTURE.PROS     1.000                               0.303    0.589
##     W2FUTURE.PROS     1.000                               0.303    0.584
##     W3FUTURE.PROS     1.000                               0.303    0.558
##     W4FUTURE.PROS     1.000                               0.303    0.586
##     W5FUTURE.PROS     1.000                               0.303    0.573
##   s =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.168    0.325
##     W2FUTURE.PROS     2.000                               0.335    0.646
##     W3FUTURE.PROS     3.000                               0.503    0.926
##     W4FUTURE.PROS     4.000                               0.671    1.296
##     W5FUTURE.PROS     5.000                               0.839    1.583
##   q =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.032    0.061
##     W2FUTURE.PROS     4.000                               0.127    0.244
##     W3FUTURE.PROS     9.000                               0.285    0.524
##     W4FUTURE.PROS    16.000                               0.506    0.978
##     W5FUTURE.PROS    25.000                               0.791    1.493
## 
## Regressions:
##   i ~
##     group.x           0.010    0.024    0.392    0.695    0.032    0.014
##   s ~
##     group.x  (g1)    -0.005    0.019   -0.245    0.807   -0.028   -0.013
##   q ~
##     group.x  (g2)    -0.000    0.004   -0.076    0.939   -0.009   -0.004
## 
## Covariances:
##   i ~~
##     s                -0.012    0.007   -1.658    0.097   -0.243   -0.243
##     q                 0.001    0.001    1.044    0.297    0.133    0.133
##   s ~~
##     q                -0.005    0.001   -4.241    0.000   -0.924   -0.924
## 
## Intercepts:
##     s         (b)     0.071    0.010    6.918    0.000    0.425    0.425
##     q         (c)    -0.011    0.002   -5.821    0.000   -0.355   -0.355
##     W0FUTURE.         0.000                               0.000    0.000
##     W1FUTURE.         0.000                               0.000    0.000
##     W2FUTURE.         0.000                               0.000    0.000
##     W3FUTURE.         0.000                               0.000    0.000
##     W4FUTURE.         0.000                               0.000    0.000
##     W5FUTURE.         0.000                               0.000    0.000
##     i                 3.357    0.013  260.402    0.000   11.065   11.065
## 
## Variances:
##     W0FUTURE.PROS     0.200    0.012                      0.200    0.685
##     W1FUTURE.PROS     0.177    0.007                      0.177    0.665
##     W2FUTURE.PROS     0.167    0.007                      0.167    0.619
##     W3FUTURE.PROS     0.185    0.007                      0.185    0.627
##     W4FUTURE.PROS     0.156    0.006                      0.156    0.581
##     W5FUTURE.PROS     0.146    0.010                      0.146    0.520
##     i                 0.092    0.011                      1.000    1.000
##     s                 0.028    0.007                      1.000    1.000
##     q                 0.001    0.000                      1.000    1.000
## 
## Defined parameters:
##     tpG1              3.471    0.546    6.360    0.000    0.655    0.623
##     tpG2              2.889    0.230   12.566    0.000    0.545    0.574
```

![plot of chunk MfuturePros](figure/MfuturePros.png) 

[top](#top)
