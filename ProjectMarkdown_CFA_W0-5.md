Gap Years in Australia: Effects on Multidimensional Life Satisfaction
========================================================
<a name="top"></a>

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

```r
# Single item key|value pairs
baseData <- dbGetQuery(LSAY, "SELECT * FROM Student2003")
WaveAdict_singleitem <- list(id = "id", stateid = "State territory", loc = "location class", 
    sex = "gender", sisced = "education expectations", indig = "indigenous status", 
    laa005 = "ed plans", laa006 = "parent ed plaan", escs = "ses index from pisa results", 
    laa007 = "friend ed plan", laa010 = "work experience", laa025 = "social comparison english", 
    laa026 = "social comparison english", laa027 = "social comparison total", 
    xcsl2003 = "grade", lad001 = "work", xhrs2003 = "average hrs worked", xwkp2003 = "weekly wage", 
    xath2003 = "live parents", belong = "sense of belonging", intmat = "interest in math", 
    instmot = "intrinsic motivation", matheff = "self-efficacy", anxmat = "anxiety", 
    scmat = "self-concept", complrn = "competative", cooplrn = "cooperative", 
    teachsup = "teacher support", disclim = "discipline climate")

# Multi item scal and index item key|value pairs
WaveAdict_multiitem <- list(pv1 = "plausible values for achievement - First", 
    HRS = "hours how spent per week - 6 item", st30q = "Attitudes toward education career - 8 item")

## Print Scale descriptions and items flags
print("Single Item scales")
```

```
## [1] "Single Item scales"
```

```r
for (i in seq_along(WaveAdict_singleitem)) {
    cat(paste(names(WaveAdict_singleitem)[i], WaveAdict_singleitem[[i]][1], 
        sep = ":\t"), sep = "\n")
}
```

```
## id:	id
## stateid:	State territory
## loc:	location class
## sex:	gender
## sisced:	education expectations
## indig:	indigenous status
## laa005:	ed plans
## laa006:	parent ed plaan
## escs:	ses index from pisa results
## laa007:	friend ed plan
## laa010:	work experience
## laa025:	social comparison english
## laa026:	social comparison english
## laa027:	social comparison total
## xcsl2003:	grade
## lad001:	work
## xhrs2003:	average hrs worked
## xwkp2003:	weekly wage
## xath2003:	live parents
## belong:	sense of belonging
## intmat:	interest in math
## instmot:	intrinsic motivation
## matheff:	self-efficacy
## anxmat:	anxiety
## scmat:	self-concept
## complrn:	competative
## cooplrn:	cooperative
## teachsup:	teacher support
## disclim:	discipline climate
```

```r
print("Multi Item scales")
```

```
## [1] "Multi Item scales"
```

```r
for (i in seq_along(WaveAdict_multiitem)) {
    cat(paste(names(WaveAdict_multiitem)[i], WaveAdict_multiitem[[i]][1], sep = ":\t"), 
        sep = "\n")
}
```

```
## pv1:	plausible values for achievement - First
## HRS:	hours how spent per week - 6 item
## st30q:	Attitudes toward education career - 8 item
```

```r
# extraction of multi item locations
baseLocations <- paste0(paste0("^(", paste(names(WaveAdict_multiitem), collapse = "|"), 
    ")", ".*$"))
FeatureIndex <- grep(baseLocations, names(baseData), value = TRUE)
# Analaysis database is reduction from full lsay data
matchData <- data.frame(baseData[, names(WaveAdict_singleitem)], baseData[, 
    FeatureIndex])
```

[top](#top)
