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

```
## Error: argument "paras" is missing, with no default
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

```
## Error: argument "paras" is missing, with no default
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

```
## Error: argument "paras" is missing, with no default
```

![plot of chunk futurePros](figure/futurePros.png) 

[top](#top)

Extract Matching Variables
----------------------------

```r
#Single item key|value pairs
baseData <- dbGetQuery(LSAY, "SELECT * FROM Student2003")
WaveAdict_singleitem <- list(id = 'id', stateid = 'State territory', schoolid = 'School ID',
                             loc = 'location class', sex = 'gender',
                             sisced = 'education expectations', indig = 'indigenous status', 
                             laa005 = 'ed plans',
                             laa006 = 'parent ed plaan', escs = "ses index from pisa results",
                             laa007 = 'friend ed plan',
                             laa025 = 'social comparison english',
                             laa026 = 'social comparison english', 
                             laa027 = 'social comparison total',
                             xcsl2003 = 'grade', lad001 = 'work',
                             xath2003 = 'live parents',
                             belong = 'sense of belonging', intmat = 'interest in math',
                             instmot = 'intrinsic motivation', matheff = 'self-efficacy',
                             anxmat = 'anxiety', scmat = 'self-concept', complrn = 'competative',
                             cooplrn = 'cooperative', teachsup = 'teacher support',
                            disclim = 'discipline climate')

#Multi item scal and index item key|value pairs    
WaveAdict_multiitem<- list(pv1 = "plausible values for achievement - First",
                           HRS = "hours how spent per week - 6 item"
                           #st30q = "Attitudes toward education career - 8 item" 
                           )

##Print Scale descriptions and items flags
print("Single Item scales")
```

```
## [1] "Single Item scales"
```

```r
for (i in seq_along(WaveAdict_singleitem)){
  cat(paste(names(WaveAdict_singleitem)[i], WaveAdict_singleitem[[i]][1], sep=":\t"), sep="\n")
}
```

```
## id:	id
## stateid:	State territory
## schoolid:	School ID
## loc:	location class
## sex:	gender
## sisced:	education expectations
## indig:	indigenous status
## laa005:	ed plans
## laa006:	parent ed plaan
## escs:	ses index from pisa results
## laa007:	friend ed plan
## laa025:	social comparison english
## laa026:	social comparison english
## laa027:	social comparison total
## xcsl2003:	grade
## lad001:	work
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
for (i in seq_along(WaveAdict_multiitem)){
  cat(paste(names(WaveAdict_multiitem)[i], WaveAdict_multiitem[[i]][1], sep=":\t"), sep="\n")
}
```

```
## pv1:	plausible values for achievement - First
## HRS:	hours how spent per week - 6 item
```

```r
#extraction of multi item locations
baseLocations <- paste0(paste0("^(", paste(names(WaveAdict_multiitem),collapse="|"), ")", ".*$"))
FeatureIndex<-grep(baseLocations, names(baseData), value=TRUE)
#Analaysis database is reduction from full lsay data
matchData <- data.frame(baseData[,names(WaveAdict_singleitem)], baseData[, FeatureIndex])
#recode missing
library(car)
matchData[,-c(1)] <- data.frame(apply(matchData[,-c(1)], 2,
                                      function(x) recode(x, "999=NA; 998=NA")))
matchData[,-c(1)] <- data.frame(apply(matchData[,-c(1)], 2,
                              function(x) recode(x, "999=NA; 998=NA")))
#Amount of missing data
apply(matchData,2, function(x) sum(is.na(x))/nrow(matchData))
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
##  pv1read  pv1scie  pv1prob 
## 0.000000 0.000000 0.000000
```

```r
#na.omit small amount of missing data for matching
data <- rbind(UniversityEntrant2[,names(UniversityEntrant2)%in%names(Defer2)],
              Defer2[,names(Defer2)%in%names(UniversityEntrant2)])
data$group <- c(rep(0, nrow(UniversityEntrant2)), rep(1, nrow(Defer2)))
matchData <- merge(matchData, data[, c("id", "group")], by="id", by.all=FALSE)
matchData <- na.omit(matchData)
```

[top](#top)

Propensity score matching
-----------------------------

```r
require(ggplot2)
```

```
## Loading required package: ggplot2
```

```r
require(MatchIt)
```

```
## Loading required package: MatchIt
## Loading required package: MASS
```

```r
meandifftable <- function(x) {
    post <- data.frame(x$sum.matched[4])
    matchID <- as.vector(row.names(post))
    names(post)[1] <- c("m_mean_diff")
    post$absolute <- abs(post[1])
    total2 <- post[order(-post$absolute, na.last = NA), ]
    meandiffover1 <- subset(total2[1], total2[1] > 0.1 | total2[1] < -0.1)
    meandiffover1
}

all_meandiffplot <- function(x) {
    adiff <- data.frame(x$sum.all)
    names(adiff)[4] <- c("all_mean_diff")
    diffplot <- ggplot(adiff, aes(all_mean_diff))
    diffplot <- diffplot + geom_histogram(fill = "grey")
    diffplot <- diffplot + geom_density(colour = "red")
    diffplot <- diffplot + xlim(-0.5, 0.5)
    diffplot
}

matched_meandiffplot <- function(x) {
    mdiff <- data.frame(x$sum.matched)
    names(mdiff)[4] <- c("matched_mean_diff")
    diffplot <- ggplot(mdiff, aes(matched_mean_diff))
    diffplot <- diffplot + geom_histogram(fill = "grey")
    diffplot <- diffplot + geom_density(colour = "red")
    diffplot <- diffplot + xlim(-0.5, 0.5)
    diffplot
}

all_meandiffcount <- function(x) {
    all <- data.frame(x$sum.all[4])
    all$all_group[all[1] > 0.25] <- "Large"
    all$all_group[all[1] < -0.25] <- "Large"
    all$all_group[all[1] > 0.2 & all[1] < 0.25] <- "Medium"
    all$all_group[all[1] < -0.2 & all[1] > -0.25] <- "Medium"
    all$all_group[all[1] < 0.2 & all[1] > 0] <- "Small"
    all$all_group[all[1] > -0.2 & all[1] < 0] <- "Small"
    table(all$all_group)
}

matched_meandiffcount <- function(x) {
    matched <- data.frame(x$sum.matched[4])
    matched$matched_group[matched[1] > 0.25] <- "Large"
    matched$matched_group[matched[1] < -0.25] <- "Large"
    matched$matched_group[matched[1] > 0.2 & matched[1] < 0.25] <- "Medium"
    matched$matched_group[matched[1] < -0.2 & matched[1] > -0.25] <- "Medium"
    matched$matched_group[matched[1] < 0.2 & matched[1] >= 0] <- "Small"
    matched$matched_group[matched[1] > -0.2 & matched[1] <= 0] <- "Small"
    table(matched$matched_group)
}

matchData[, c("stateid", "schoolid", "loc")] <- apply(matchData[, c("stateid", 
    "schoolid", "loc")], 2, factor)
# drop location and school and state for now
set.seed(102)
forM <- paste("group ~ ", paste0(names(matchData)[-c(1:4, 18, 36)], collapse = " + "))
# forM1 <- paste(forM, ' + I(anxmat*disclim)')
M1 <- matchit(as.formula(forM), data = matchData, method = "nearest", discard = "both", 
    caliper = 0.2, ratio = 3, distance = "logit", distance.options = list(maxit = 100))
SM1 <- summary(M1, addlvariables = NULL, interactions = TRUE, standardize = TRUE)
head(meandifftable(SM1), 5)
```

```
##               m_mean_diff
## anxmatxanxmat     -0.1587
## anxmatxscmat       0.1105
## intmatxintmat     -0.1029
```

```r
par(mfrow = c(1, 2))
all_meandiffplot(SM1)
```

```
## stat_bin: binwidth defaulted to range/30. Use 'binwidth = x' to adjust this.
```

```
## Warning: Removed 14 rows containing non-finite values (stat_density).
```

![plot of chunk PSM](figure/PSM1.png) 

```r
matched_meandiffplot(SM1)
```

```
## stat_bin: binwidth defaulted to range/30. Use 'binwidth = x' to adjust this.
```

```
## Warning: Removed 2 rows containing non-finite values (stat_density).
```

![plot of chunk PSM](figure/PSM2.png) 

```r
par(mfrow = c(1, 1))
all_meandiffcount(SM1)
```

```
## 
##  Large Medium  Small 
##     61     26    438
```

```r
matched_meandiffcount(SM1)
```

```
## 
## Small 
##   525
```

```r
# save matched data with weights
dmatch <- match.data(M1)
nrow(dmatch)
```

```
## [1] 2182
```

```r
with(dmatch, table(group))
```

```
## group
##    0    1 
## 1567  615
```

```r

dmatch <- merge(data, dmatch, by = "id", by.all = FALSE)
```



Matched Life Satisfaction
-------------------------------
Adding Weights


```r
library(lavaan.survey)
# Linear
m_linear <- Model_Fun(name = "LIFE.SAT", params = list(i = TRUE, s = TRUE, q = F, 
    ig = F, sg = F, qg = F))
des <- svydesign(ids = ~id, weights = ~weights, data = dmatch)
fitL <- growth(m_linear, data = dmatch, missing = "fiml")
fitL <- lavaan.survey(fitL, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
# Quadratic
m_quadratic <- Model_Fun(name = "LIFE.SAT", params = list(i = T, s = T, q = T, 
    ig = F, sg = F, qg = F))
fitQ <- growth(m_quadratic, data = dmatch, missing = "fiml")
fitQ <- lavaan.survey(fitQ, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
fitQ <- growth(m_quadratic, data = dmatch, missing = "fiml")
fitQ <- lavaan.survey(fitQ, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
Fit <- rbind(fitMeasures(fitL)[c("chisq", "df", "cfi", "tli", "rmsea")], fitMeasures(fitQ)[c("chisq", 
    "df", "cfi", "tli", "rmsea")])
Fit
```

```
##      chisq df    cfi    tli   rmsea
## [1,] 79.75 16 0.9806 0.9818 0.04273
## [2,] 34.33 12 0.9932 0.9915 0.02920
```

```r
anova(fitL, fitQ)
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 16133 16219  34.3                                  
## fitL 16 16171 16233  79.8       45.4       4    3.2e-09 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```r
summary(fitQ, standardized = TRUE)
```

```
## lavaan (0.5-16) converged normally after 105 iterations
## 
##   Number of observations                          2182
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               34.327
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
##     W0LIFE.SAT        1.000                               0.321    0.637
##     W1LIFE.SAT        1.000                               0.321    0.641
##     W2LIFE.SAT        1.000                               0.321    0.641
##     W3LIFE.SAT        1.000                               0.321    0.638
##     W4LIFE.SAT        1.000                               0.321    0.632
##     W5LIFE.SAT        1.000                               0.321    0.613
##   s =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.133    0.265
##     W2LIFE.SAT        2.000                               0.266    0.531
##     W3LIFE.SAT        3.000                               0.399    0.793
##     W4LIFE.SAT        4.000                               0.532    1.046
##     W5LIFE.SAT        5.000                               0.665    1.268
##   q =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.023    0.045
##     W2LIFE.SAT        4.000                               0.091    0.181
##     W3LIFE.SAT        9.000                               0.204    0.405
##     W4LIFE.SAT       16.000                               0.362    0.712
##     W5LIFE.SAT       25.000                               0.566    1.079
## 
## Covariances:
##   i ~~
##     s                -0.008    0.006   -1.302    0.193   -0.183   -0.183
##     q                 0.001    0.001    0.739    0.460    0.101    0.101
##   s ~~
##     q                -0.003    0.001   -3.103    0.002   -0.916   -0.916
## 
## Intercepts:
##     s         (b)     0.011    0.007    1.503    0.133    0.085    0.085
##     q         (c)    -0.007    0.001   -4.713    0.000   -0.293   -0.293
##     W0LIFE.SA         0.000                               0.000    0.000
##     W1LIFE.SA         0.000                               0.000    0.000
##     W2LIFE.SA         0.000                               0.000    0.000
##     W3LIFE.SA         0.000                               0.000    0.000
##     W4LIFE.SA         0.000                               0.000    0.000
##     W5LIFE.SA         0.000                               0.000    0.000
##     i                 3.581    0.010  350.152    0.000   11.144   11.144
## 
## Variances:
##     W0LIFE.SAT        0.151    0.009                      0.151    0.595
##     W1LIFE.SAT        0.150    0.005                      0.150    0.595
##     W2LIFE.SAT        0.138    0.005                      0.138    0.551
##     W3LIFE.SAT        0.132    0.005                      0.132    0.521
##     W4LIFE.SAT        0.133    0.005                      0.133    0.515
##     W5LIFE.SAT        0.141    0.009                      0.141    0.511
##     i                 0.103    0.009                      1.000    1.000
##     s                 0.018    0.005                      1.000    1.000
##     q                 0.001    0.000                      1.000    1.000
```

```r
# By Group
mG_quadratic <- Model_Fun(name = "LIFE.SAT", params = list(i = T, s = T, q = T, 
    ig = T, sg = T, qg = T))
mG_quadratic <- gsub("group", "group.x", mG_quadratic)
fitQG <- growth(mG_quadratic, data = dmatch, missing = "fiml")
fitQG <- lavaan.survey(fitQG, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
Fit <- rbind(Fit, fitMeasures(fitQG)[c("chisq", "df", "cfi", "tli", "rmsea")])
Fit
```

```
##      chisq df    cfi    tli   rmsea
## [1,] 79.75 16 0.9806 0.9818 0.04273
## [2,] 34.33 12 0.9932 0.9915 0.02920
## [3,] 50.58 15 0.9892 0.9849 0.03297
```

```r
summary(fitQG, standardized = TRUE)
```

```
## lavaan (0.5-16) converged normally after  94 iterations
## 
##   Number of observations                          2182
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               50.578
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
##     W0LIFE.SAT        1.000                               0.322    0.638
##     W1LIFE.SAT        1.000                               0.322    0.642
##     W2LIFE.SAT        1.000                               0.322    0.642
##     W3LIFE.SAT        1.000                               0.322    0.640
##     W4LIFE.SAT        1.000                               0.322    0.633
##     W5LIFE.SAT        1.000                               0.322    0.614
##   s =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.134    0.266
##     W2LIFE.SAT        2.000                               0.267    0.532
##     W3LIFE.SAT        3.000                               0.401    0.796
##     W4LIFE.SAT        4.000                               0.534    1.050
##     W5LIFE.SAT        5.000                               0.668    1.273
##   q =~
##     W0LIFE.SAT        0.000                               0.000    0.000
##     W1LIFE.SAT        1.000                               0.023    0.045
##     W2LIFE.SAT        4.000                               0.091    0.181
##     W3LIFE.SAT        9.000                               0.204    0.406
##     W4LIFE.SAT       16.000                               0.363    0.714
##     W5LIFE.SAT       25.000                               0.567    1.081
## 
## Regressions:
##   i ~
##     group.x          -0.021    0.023   -0.896    0.370   -0.064   -0.028
##   s ~
##     group.x  (g1)     0.033    0.017    1.993    0.046    0.250    0.112
##   q ~
##     group.x  (g2)    -0.007    0.003   -2.079    0.038   -0.289   -0.129
## 
## Covariances:
##   i ~~
##     s                -0.008    0.006   -1.322    0.186   -0.185   -0.185
##     q                 0.001    0.001    0.750    0.453    0.103    0.103
##   s ~~
##     q                -0.003    0.001   -3.079    0.002   -0.916   -0.916
## 
## Intercepts:
##     s         (b)     0.002    0.009    0.241    0.810    0.016    0.016
##     q         (c)    -0.005    0.002   -2.937    0.003   -0.214   -0.214
##     W0LIFE.SA         0.000                               0.000    0.000
##     W1LIFE.SA         0.000                               0.000    0.000
##     W2LIFE.SA         0.000                               0.000    0.000
##     W3LIFE.SA         0.000                               0.000    0.000
##     W4LIFE.SA         0.000                               0.000    0.000
##     W5LIFE.SA         0.000                               0.000    0.000
##     i                 3.586    0.012  298.868    0.000   11.142   11.142
## 
## Variances:
##     W0LIFE.SAT        0.151    0.009                      0.151    0.593
##     W1LIFE.SAT        0.150    0.005                      0.150    0.595
##     W2LIFE.SAT        0.139    0.005                      0.139    0.552
##     W3LIFE.SAT        0.132    0.005                      0.132    0.521
##     W4LIFE.SAT        0.133    0.005                      0.133    0.515
##     W5LIFE.SAT        0.141    0.009                      0.141    0.511
##     i                 0.104    0.009                      0.999    0.999
##     s                 0.018    0.005                      0.988    0.988
##     q                 0.001    0.000                      0.983    0.983
## 
## Defined parameters:
##     tpG1              9.159   16.609    0.551    0.581    1.556   -0.563
##     tpG2              1.559    0.298    5.228    0.000    0.265    0.186
```

```r
## plot
paras <- parameterEstimates(fitQG)[c(44, 13, 20, 21:23), "est"]
FunPlot_Multi2(model = fitQG, data = dmatch, main = "Life Satisfaction", var = "LIFE.SAT", 
    paras)
```

![plot of chunk MlifeSat](figure/MlifeSat.png) 


Matched Career Prospects
-------------------------------
Adding Weights


```r
library(lavaan.survey)
# Linear
m_linear <- Model_Fun(name = "CAREER.PROS", params = list(i = TRUE, s = TRUE, 
    q = F, ig = F, sg = F, qg = F))
des <- svydesign(ids = ~id, weights = ~weights, data = dmatch)
fitL <- growth(m_linear, data = dmatch, missing = "fiml")
fitL <- lavaan.survey(fitL, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
# Quadratic
m_quadratic <- Model_Fun(name = "CAREER.PROS", params = list(i = T, s = T, q = T, 
    ig = F, sg = F, qg = F))
fitQ <- growth(m_quadratic, data = dmatch, missing = "fiml")
fitQ <- lavaan.survey(fitQ, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
fitQ <- growth(m_quadratic, data = dmatch, missing = "fiml")
fitQ <- lavaan.survey(fitQ, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
Fit <- rbind(fitMeasures(fitL)[c("chisq", "df", "cfi", "tli", "rmsea")], fitMeasures(fitQ)[c("chisq", 
    "df", "cfi", "tli", "rmsea")])
Fit
```

```
##       chisq df    cfi    tli   rmsea
## [1,] 223.00 16 0.9058 0.9117 0.07700
## [2,]  57.14 12 0.9795 0.9743 0.04152
```

```r
anova(fitL, fitQ)
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 20761 20847  57.1                                  
## fitL 16 20919 20982 223.0        166       4     <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```r
summary(fitQ, standardized = TRUE)
```

```
## lavaan (0.5-16) converged normally after  83 iterations
## 
##   Number of observations                          2182
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               57.145
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
##     W0CAREER.PROS     1.000                               0.312    0.544
##     W1CAREER.PROS     1.000                               0.312    0.572
##     W2CAREER.PROS     1.000                               0.312    0.560
##     W3CAREER.PROS     1.000                               0.312    0.537
##     W4CAREER.PROS     1.000                               0.312    0.497
##     W5CAREER.PROS     1.000                               0.312    0.516
##   s =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.202    0.371
##     W2CAREER.PROS     2.000                               0.405    0.727
##     W3CAREER.PROS     3.000                               0.607    1.045
##     W4CAREER.PROS     4.000                               0.810    1.291
##     W5CAREER.PROS     5.000                               1.012    1.675
##   q =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.041    0.075
##     W2CAREER.PROS     4.000                               0.164    0.295
##     W3CAREER.PROS     9.000                               0.370    0.637
##     W4CAREER.PROS    16.000                               0.658    1.049
##     W5CAREER.PROS    25.000                               1.028    1.701
## 
## Covariances:
##   i ~~
##     s                -0.009    0.008   -1.120    0.263   -0.147   -0.147
##     q                 0.000    0.001    0.293    0.769    0.031    0.031
##   s ~~
##     q                -0.008    0.001   -5.672    0.000   -0.912   -0.912
## 
## Intercepts:
##     s         (b)     0.072    0.009    7.691    0.000    0.356    0.356
##     q         (c)    -0.014    0.002   -7.908    0.000   -0.340   -0.340
##     W0CAREER.         0.000                               0.000    0.000
##     W1CAREER.         0.000                               0.000    0.000
##     W2CAREER.         0.000                               0.000    0.000
##     W3CAREER.         0.000                               0.000    0.000
##     W4CAREER.         0.000                               0.000    0.000
##     W5CAREER.         0.000                               0.000    0.000
##     i                 3.337    0.011  294.034    0.000   10.700   10.700
## 
## Variances:
##     W0CAREER.PROS     0.231    0.013                      0.231    0.704
##     W1CAREER.PROS     0.190    0.007                      0.190    0.640
##     W2CAREER.PROS     0.177    0.007                      0.177    0.571
##     W3CAREER.PROS     0.193    0.008                      0.193    0.572
##     W4CAREER.PROS     0.240    0.009                      0.240    0.611
##     W5CAREER.PROS     0.157    0.013                      0.157    0.429
##     i                 0.097    0.012                      1.000    1.000
##     s                 0.041    0.008                      1.000    1.000
##     q                 0.002    0.000                      1.000    1.000
```

```r
# By Group
mG_quadratic <- Model_Fun(name = "CAREER.PROS", params = list(i = T, s = T, 
    q = T, ig = T, sg = T, qg = T))
mG_quadratic <- gsub("group", "group.x", mG_quadratic)
fitQG <- growth(mG_quadratic, data = dmatch, missing = "fiml")
fitQG <- lavaan.survey(fitQG, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
Fit <- rbind(Fit, fitMeasures(fitQG)[c("chisq", "df", "cfi", "tli", "rmsea")])
Fit
```

```
##       chisq df    cfi    tli   rmsea
## [1,] 223.00 16 0.9058 0.9117 0.07700
## [2,]  57.14 12 0.9795 0.9743 0.04152
## [3,]  61.24 15 0.9790 0.9706 0.03759
```

```r
summary(fitQG, standardized = TRUE)
```

```
## lavaan (0.5-16) converged normally after 104 iterations
## 
##   Number of observations                          2182
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               61.244
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
##     W0CAREER.PROS     1.000                               0.312    0.544
##     W1CAREER.PROS     1.000                               0.312    0.572
##     W2CAREER.PROS     1.000                               0.312    0.560
##     W3CAREER.PROS     1.000                               0.312    0.536
##     W4CAREER.PROS     1.000                               0.312    0.497
##     W5CAREER.PROS     1.000                               0.312    0.516
##   s =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.202    0.371
##     W2CAREER.PROS     2.000                               0.405    0.727
##     W3CAREER.PROS     3.000                               0.607    1.044
##     W4CAREER.PROS     4.000                               0.809    1.290
##     W5CAREER.PROS     5.000                               1.011    1.674
##   q =~
##     W0CAREER.PROS     0.000                               0.000    0.000
##     W1CAREER.PROS     1.000                               0.041    0.075
##     W2CAREER.PROS     4.000                               0.165    0.296
##     W3CAREER.PROS     9.000                               0.370    0.637
##     W4CAREER.PROS    16.000                               0.658    1.049
##     W5CAREER.PROS    25.000                               1.028    1.702
## 
## Regressions:
##   i ~
##     group.x          -0.041    0.025   -1.603    0.109   -0.131   -0.058
##   s ~
##     group.x  (g1)     0.031    0.021    1.495    0.135    0.155    0.069
##   q ~
##     group.x  (g2)    -0.006    0.004   -1.485    0.138   -0.143   -0.064
## 
## Covariances:
##   i ~~
##     s                -0.009    0.008   -1.075    0.282   -0.142   -0.142
##     q                 0.000    0.001    0.247    0.805    0.026    0.026
##   s ~~
##     q                -0.008    0.001   -5.647    0.000   -0.911   -0.911
## 
## Intercepts:
##     s         (b)     0.063    0.011    5.791    0.000    0.314    0.314
##     q         (c)    -0.012    0.002   -5.980    0.000   -0.301   -0.301
##     W0CAREER.         0.000                               0.000    0.000
##     W1CAREER.         0.000                               0.000    0.000
##     W2CAREER.         0.000                               0.000    0.000
##     W3CAREER.         0.000                               0.000    0.000
##     W4CAREER.         0.000                               0.000    0.000
##     W5CAREER.         0.000                               0.000    0.000
##     i                 3.348    0.013  252.060    0.000   10.745   10.745
## 
## Variances:
##     W0CAREER.PROS     0.232    0.013                      0.232    0.705
##     W1CAREER.PROS     0.190    0.007                      0.190    0.640
##     W2CAREER.PROS     0.177    0.007                      0.177    0.571
##     W3CAREER.PROS     0.193    0.008                      0.193    0.572
##     W4CAREER.PROS     0.240    0.009                      0.240    0.611
##     W5CAREER.PROS     0.156    0.013                      0.156    0.428
##     i                 0.097    0.012                      0.997    0.997
##     s                 0.041    0.008                      0.995    0.995
##     q                 0.002    0.000                      0.996    0.996
## 
## Defined parameters:
##     tpG1              2.471    0.683    3.616    0.000    0.503    0.516
##     tpG2              2.596    0.154   16.825    0.000    0.528    0.525
```

```r
## plot
paras <- parameterEstimates(fitQG)[c(44, 13, 20, 21:23), "est"]
FunPlot_Multi2(model = fitQG, data = dmatch, main = "Career Prospects", var = "CAREER.PROS", 
    paras)
```

![plot of chunk McareerPros](figure/McareerPros.png) 


Matched Future Prospects
-------------------------------
Adding Weights


```r
library(lavaan.survey)
# Linear
m_linear <- Model_Fun(name = "FUTURE.PROSS", params = list(i = TRUE, s = TRUE, 
    q = F, ig = F, sg = F, qg = F))
des <- svydesign(ids = ~id, weights = ~weights, data = dmatch)
fitL <- growth(m_linear, data = dmatch, missing = "fiml")
```

```
## Error: lavaan ERROR: missing observed variables in dataset: W0FUTURE.PROSS
## W1FUTURE.PROSS W2FUTURE.PROSS W3FUTURE.PROSS W4FUTURE.PROSS W5FUTURE.PROSS
```

```r
fitL <- lavaan.survey(fitL, survey.design = des, estimator = "ML")
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

```r
# Quadratic
m_quadratic <- Model_Fun(name = "FUTURE.PROS", params = list(i = T, s = T, q = T, 
    ig = F, sg = F, qg = F))
fitQ <- growth(m_quadratic, data = dmatch, missing = "fiml")
fitQ <- lavaan.survey(fitQ, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
fitQ <- growth(m_quadratic, data = dmatch, missing = "fiml")
fitQ <- lavaan.survey(fitQ, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
Fit <- rbind(fitMeasures(fitL)[c("chisq", "df", "cfi", "tli", "rmsea")], fitMeasures(fitQ)[c("chisq", 
    "df", "cfi", "tli", "rmsea")])
Fit
```

```
##       chisq df    cfi    tli   rmsea
## [1,] 223.00 16 0.9058 0.9117 0.07700
## [2,]  18.16 12 0.9971 0.9964 0.01534
```

```r
anova(fitL, fitQ)
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ 12 18236 18321  18.2                                  
## fitL 16 20919 20982 223.0        205       4     <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```r
summary(fitQ, standardized = TRUE)
```

```
## lavaan (0.5-16) converged normally after  85 iterations
## 
##   Number of observations                          2182
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               18.158
##   Degrees of freedom                                12
##   P-value (Chi-square)                           0.111
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0FUTURE.PROS     1.000                               0.318    0.587
##     W1FUTURE.PROS     1.000                               0.318    0.619
##     W2FUTURE.PROS     1.000                               0.318    0.610
##     W3FUTURE.PROS     1.000                               0.318    0.593
##     W4FUTURE.PROS     1.000                               0.318    0.611
##     W5FUTURE.PROS     1.000                               0.318    0.602
##   s =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.188    0.366
##     W2FUTURE.PROS     2.000                               0.376    0.722
##     W3FUTURE.PROS     3.000                               0.564    1.053
##     W4FUTURE.PROS     4.000                               0.752    1.447
##     W5FUTURE.PROS     5.000                               0.940    1.780
##   q =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.035    0.069
##     W2FUTURE.PROS     4.000                               0.142    0.272
##     W3FUTURE.PROS     9.000                               0.319    0.595
##     W4FUTURE.PROS    16.000                               0.567    1.091
##     W5FUTURE.PROS    25.000                               0.886    1.677
## 
## Covariances:
##   i ~~
##     s                -0.019    0.007   -2.650    0.008   -0.324   -0.324
##     q                 0.002    0.001    2.060    0.039    0.220    0.220
##   s ~~
##     q                -0.006    0.001   -5.504    0.000   -0.938   -0.938
## 
## Intercepts:
##     s         (b)     0.075    0.009    8.668    0.000    0.399    0.399
##     q         (c)    -0.013    0.002   -7.856    0.000   -0.360   -0.360
##     W0FUTURE.         0.000                               0.000    0.000
##     W1FUTURE.         0.000                               0.000    0.000
##     W2FUTURE.         0.000                               0.000    0.000
##     W3FUTURE.         0.000                               0.000    0.000
##     W4FUTURE.         0.000                               0.000    0.000
##     W5FUTURE.         0.000                               0.000    0.000
##     i                 3.357    0.011  310.423    0.000   10.563   10.563
## 
## Variances:
##     W0FUTURE.PROS     0.192    0.011                      0.192    0.655
##     W1FUTURE.PROS     0.172    0.006                      0.172    0.654
##     W2FUTURE.PROS     0.167    0.006                      0.167    0.614
##     W3FUTURE.PROS     0.175    0.007                      0.175    0.611
##     W4FUTURE.PROS     0.158    0.006                      0.158    0.583
##     W5FUTURE.PROS     0.141    0.010                      0.141    0.507
##     i                 0.101    0.011                      1.000    1.000
##     s                 0.035    0.006                      1.000    1.000
##     q                 0.001    0.000                      1.000    1.000
```

```r
# By Group
mG_quadratic <- Model_Fun(name = "FUTURE.PROS", params = list(i = T, s = T, 
    q = T, ig = T, sg = T, qg = T))
mG_quadratic <- gsub("group", "group.x", mG_quadratic)
fitQG <- growth(mG_quadratic, data = dmatch, missing = "fiml")
fitQG <- lavaan.survey(fitQG, survey.design = des, estimator = "ML")
```

```
## Warning: Estimator 'ML' will not correct standard errors and chi-square
## statistic.
```

```r
Fit <- rbind(Fit, fitMeasures(fitQG)[c("chisq", "df", "cfi", "tli", "rmsea")])
Fit
```

```
##       chisq df    cfi    tli   rmsea
## [1,] 223.00 16 0.9058 0.9117 0.07700
## [2,]  18.16 12 0.9971 0.9964 0.01534
## [3,]  19.77 15 0.9978 0.9969 0.01207
```

```r
summary(fitQG, standardized = TRUE)
```

```
## lavaan (0.5-16) converged normally after 127 iterations
## 
##   Number of observations                          2182
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               19.767
##   Degrees of freedom                                15
##   P-value (Chi-square)                           0.181
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)   Std.lv  Std.all
## Latent variables:
##   i =~
##     W0FUTURE.PROS     1.000                               0.318    0.587
##     W1FUTURE.PROS     1.000                               0.318    0.619
##     W2FUTURE.PROS     1.000                               0.318    0.610
##     W3FUTURE.PROS     1.000                               0.318    0.593
##     W4FUTURE.PROS     1.000                               0.318    0.611
##     W5FUTURE.PROS     1.000                               0.318    0.602
##   s =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.188    0.366
##     W2FUTURE.PROS     2.000                               0.376    0.722
##     W3FUTURE.PROS     3.000                               0.564    1.052
##     W4FUTURE.PROS     4.000                               0.752    1.447
##     W5FUTURE.PROS     5.000                               0.940    1.780
##   q =~
##     W0FUTURE.PROS     0.000                               0.000    0.000
##     W1FUTURE.PROS     1.000                               0.035    0.069
##     W2FUTURE.PROS     4.000                               0.142    0.272
##     W3FUTURE.PROS     9.000                               0.319    0.595
##     W4FUTURE.PROS    16.000                               0.567    1.091
##     W5FUTURE.PROS    25.000                               0.886    1.678
## 
## Regressions:
##   i ~
##     group.x           0.008    0.024    0.350    0.726    0.027    0.012
##   s ~
##     group.x  (g1)    -0.009    0.019   -0.463    0.644   -0.048   -0.021
##   q ~
##     group.x  (g2)     0.001    0.004    0.302    0.762    0.031    0.014
## 
## Covariances:
##   i ~~
##     s                -0.019    0.007   -2.646    0.008   -0.324   -0.324
##     q                 0.002    0.001    2.057    0.040    0.220    0.220
##   s ~~
##     q                -0.006    0.001   -5.501    0.000   -0.938   -0.938
## 
## Intercepts:
##     s         (b)     0.078    0.010    7.629    0.000    0.412    0.412
##     q         (c)    -0.013    0.002   -6.853    0.000   -0.368   -0.368
##     W0FUTURE.         0.000                               0.000    0.000
##     W1FUTURE.         0.000                               0.000    0.000
##     W2FUTURE.         0.000                               0.000    0.000
##     W3FUTURE.         0.000                               0.000    0.000
##     W4FUTURE.         0.000                               0.000    0.000
##     W5FUTURE.         0.000                               0.000    0.000
##     i                 3.355    0.013  264.355    0.000   10.557   10.557
## 
## Variances:
##     W0FUTURE.PROS     0.192    0.011                      0.192    0.655
##     W1FUTURE.PROS     0.172    0.006                      0.172    0.654
##     W2FUTURE.PROS     0.167    0.006                      0.167    0.614
##     W3FUTURE.PROS     0.175    0.007                      0.175    0.611
##     W4FUTURE.PROS     0.158    0.006                      0.158    0.583
##     W5FUTURE.PROS     0.141    0.010                      0.141    0.507
##     i                 0.101    0.011                      1.000    1.000
##     s                 0.035    0.006                      1.000    1.000
##     q                 0.001    0.000                      1.000    1.000
## 
## Defined parameters:
##     tpG1              3.055    0.320    9.560    0.000    0.576    0.567
##     tpG2              2.867    0.216   13.261    0.000    0.540    0.552
```

```r
## plot
paras <- parameterEstimates(fitQG)[c(44, 13, 20, 21:23), "est"]
FunPlot_Multi2(model = fitQG, data = dmatch, main = "Future Prospects", var = "FUTURE.PROS", 
    paras)
```

![plot of chunk MfuturePros](figure/MfuturePros.png) 


