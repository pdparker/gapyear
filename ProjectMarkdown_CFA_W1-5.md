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
##       chisq df    cfi    tli   rmsea
## [1,] 46.608 10 0.9873 0.9873 0.03563
## [2,]  1.615  6 1.0000 1.0025 0.00000
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ  6 15879 15963  1.61                                  
## fitL 10 15916 15976 46.61         45       4      4e-09 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-15) converged normally after  87 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        14
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic                1.615
##   Degrees of freedom                                 6
##   P-value (Chi-square)                           0.952
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W1LIFE.SAT        1.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        1.000
##     W4LIFE.SAT        1.000
##     W5LIFE.SAT        1.000
##   s =~
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        2.000
##     W4LIFE.SAT        3.000
##     W5LIFE.SAT        4.000
##   q =~
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        4.000
##     W4LIFE.SAT        9.000
##     W5LIFE.SAT       16.000
## 
## Covariances:
##   i ~~
##     s                -0.002    0.009   -0.192    0.848
##     q                 0.000    0.002    0.001    0.999
##   s ~~
##     q                -0.004    0.002   -1.833    0.067
## 
## Intercepts:
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        0.000
##     W3LIFE.SAT        0.000
##     W4LIFE.SAT        0.000
##     W5LIFE.SAT        0.000
##     i                 3.538    0.009  387.455    0.000
##     s                 0.033    0.009    3.845    0.000
##     q                -0.013    0.002   -5.965    0.000
## 
## Variances:
##     W1LIFE.SAT        0.146    0.010
##     W2LIFE.SAT        0.146    0.005
##     W3LIFE.SAT        0.140    0.005
##     W4LIFE.SAT        0.137    0.005
##     W5LIFE.SAT        0.134    0.011
##     i                 0.109    0.010
##     s                 0.015    0.009
##     q                 0.001    0.000
```

```
## lavaan (0.5-15) converged normally after  82 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        14
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic                5.165
##   Degrees of freedom                                 8
##   P-value (Chi-square)                           0.740
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W1LIFE.SAT        1.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        1.000
##     W4LIFE.SAT        1.000
##     W5LIFE.SAT        1.000
##   s =~
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        2.000
##     W4LIFE.SAT        3.000
##     W5LIFE.SAT        4.000
##   q =~
##     W1LIFE.SAT        0.000
##     W2LIFE.SAT        1.000
##     W3LIFE.SAT        4.000
##     W4LIFE.SAT        9.000
##     W5LIFE.SAT       16.000
## 
## Regressions:
##   i ~
##     group             0.037    0.011    3.383    0.001
##   s ~
##     group    (g1)    -0.017    0.011   -1.606    0.108
##   q ~
##     group    (g2)     0.002    0.003    0.680    0.496
## 
## Covariances:
##   i ~~
##     s                -0.002    0.009   -0.234    0.815
##     q                 0.000    0.002    0.060    0.952
##   s ~~
##     q                -0.004    0.002   -1.884    0.060
## 
## Intercepts:
##     s         (b)     0.024    0.011    2.270    0.023
##     q         (c)    -0.012    0.003   -4.516    0.000
##     W1LIFE.SA         0.000
##     W2LIFE.SA         0.000
##     W3LIFE.SA         0.000
##     W4LIFE.SA         0.000
##     W5LIFE.SA         0.000
##     i                 3.559    0.011  323.532    0.000
## 
## Variances:
##     W1LIFE.SAT        0.145    0.010
##     W2LIFE.SAT        0.146    0.005
##     W3LIFE.SAT        0.140    0.005
##     W4LIFE.SAT        0.137    0.005
##     W5LIFE.SAT        0.134    0.011
##     i                 0.109    0.010
##     s                 0.016    0.009
##     q                 0.001    0.000
## 
## Defined parameters:
##     tpG1              1.508    0.135   11.190    0.000
##     tpG2              0.350    0.782    0.447    0.655
```

```
## Percentage Missing:
```

```
## W1LIFE.SAT W2LIFE.SAT W3LIFE.SAT W4LIFE.SAT W5LIFE.SAT 
##   0.001779   0.076957   0.126335   0.190836   0.250445
```

```
## W1LIFE.SAT W2LIFE.SAT W3LIFE.SAT W4LIFE.SAT W5LIFE.SAT 
##    0.00000    0.08819    0.16063    0.20630    0.31496
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

<a name="careerPros"></a>
CFA Growth - Career Prospects
-----------------------
Group Parameters not significant for Life Satisfaction so pooled model is plotted at the end of this section.


```
##       chisq df    cfi    tli   rmsea
## [1,] 112.85 10 0.9470 0.9470 0.05973
## [2,]  26.67  6 0.9894 0.9823 0.03457
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ  6 19933 20016  26.7                                  
## fitL 10 20011 20071 112.8       86.2       4     <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-15) converged normally after  64 iterations
## 
##   Number of observations                          2883
## 
##   Number of missing patterns                        22
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic               26.671
##   Degrees of freedom                                 6
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
##     W1CAREER.PROS     1.000
##     W2CAREER.PROS     1.000
##     W3CAREER.PROS     1.000
##     W4CAREER.PROS     1.000
##     W5CAREER.PROS     1.000
##   s =~
##     W1CAREER.PROS     0.000
##     W2CAREER.PROS     1.000
##     W3CAREER.PROS     2.000
##     W4CAREER.PROS     3.000
##     W5CAREER.PROS     4.000
##   q =~
##     W1CAREER.PROS     0.000
##     W2CAREER.PROS     1.000
##     W3CAREER.PROS     4.000
##     W4CAREER.PROS     9.000
##     W5CAREER.PROS    16.000
## 
## Covariances:
##   i ~~
##     s                -0.026    0.012   -2.159    0.031
##     q                 0.003    0.002    1.328    0.184
##   s ~~
##     q                -0.012    0.003   -4.230    0.000
## 
## Intercepts:
##     s         (b)     0.064    0.010    6.082    0.000
##     q         (c)    -0.019    0.003   -7.112    0.000
##     W1CAREER.         0.000
##     W2CAREER.         0.000
##     W3CAREER.         0.000
##     W4CAREER.         0.000
##     W5CAREER.         0.000
##     i                 3.360    0.010  327.455    0.000
## 
## Variances:
##     W1CAREER.PROS     0.169    0.014
##     W2CAREER.PROS     0.194    0.007
##     W3CAREER.PROS     0.196    0.008
##     W4CAREER.PROS     0.227    0.008
##     W5CAREER.PROS     0.164    0.017
##     i                 0.147    0.014
##     s                 0.051    0.013
##     q                 0.003    0.001
## 
## Defined parameters:
##     tpG2              1.715    0.096   17.844    0.000
```

```
## Percentage Missing:
```

```
## W1CAREER.PROS W2CAREER.PROS W3CAREER.PROS W4CAREER.PROS W5CAREER.PROS 
##       0.01157       0.08274       0.13390       0.19395       0.25445
```

```
## W1CAREER.PROS W2CAREER.PROS W3CAREER.PROS W4CAREER.PROS W5CAREER.PROS 
##      0.006299      0.097638      0.170079      0.211024      0.319685
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 


<a name="futPros"></a>
CFA Growth - Future Prospects
-----------------------
Group Parameters not significant for Life Satisfaction so pooled model is plotted at the end of this section.


```
##        chisq df    cfi    tli   rmsea
## [1,] 38.4351 10 0.9861 0.9861 0.03141
## [2,]  0.8288  6 1.0000 1.0042 0.00000
```

```
## Chi Square Difference Test
## 
##      Df   AIC   BIC Chisq Chisq diff Df diff Pr(>Chisq)    
## fitQ  6 17426 17509  0.83                                  
## fitL 10 17456 17515 38.44       37.6       4    1.4e-07 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

```
## lavaan (0.5-15) converged normally after  79 iterations
## 
##                                                   Used       Total
##   Number of observations                          2882        2883
## 
##   Number of missing patterns                        23
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic                0.829
##   Degrees of freedom                                 6
##   P-value (Chi-square)                           0.991
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W1FUTURE.PROS     1.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     1.000
##     W4FUTURE.PROS     1.000
##     W5FUTURE.PROS     1.000
##   s =~
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     2.000
##     W4FUTURE.PROS     3.000
##     W5FUTURE.PROS     4.000
##   q =~
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     4.000
##     W4FUTURE.PROS     9.000
##     W5FUTURE.PROS    16.000
## 
## Covariances:
##   i ~~
##     s                -0.009    0.010   -0.838    0.402
##     q                 0.000    0.002    0.196    0.845
##   s ~~
##     q                -0.006    0.002   -2.773    0.006
## 
## Intercepts:
##     s         (b)     0.042    0.010    4.420    0.000
##     q         (c)    -0.010    0.002   -4.272    0.000
##     W1FUTURE.         0.000
##     W2FUTURE.         0.000
##     W3FUTURE.         0.000
##     W4FUTURE.         0.000
##     W5FUTURE.         0.000
##     i                 3.396    0.009  358.685    0.000
## 
## Variances:
##     W1FUTURE.PROS     0.161    0.012
##     W2FUTURE.PROS     0.168    0.006
##     W3FUTURE.PROS     0.180    0.007
##     W4FUTURE.PROS     0.158    0.006
##     W5FUTURE.PROS     0.143    0.013
##     i                 0.111    0.012
##     s                 0.028    0.011
##     q                 0.002    0.001
## 
## Defined parameters:
##     tpG2              2.099    0.153   13.711    0.000
```

```
## lavaan (0.5-15) converged normally after  79 iterations
## 
##                                                   Used       Total
##   Number of observations                          2882        2883
## 
##   Number of missing patterns                        23
## 
##   Estimator                                         ML
##   Minimum Function Test Statistic                0.829
##   Degrees of freedom                                 6
##   P-value (Chi-square)                           0.991
## 
## Parameter estimates:
## 
##   Information                                 Observed
##   Standard Errors                             Standard
## 
##                    Estimate  Std.err  Z-value  P(>|z|)
## Latent variables:
##   i =~
##     W1FUTURE.PROS     1.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     1.000
##     W4FUTURE.PROS     1.000
##     W5FUTURE.PROS     1.000
##   s =~
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     2.000
##     W4FUTURE.PROS     3.000
##     W5FUTURE.PROS     4.000
##   q =~
##     W1FUTURE.PROS     0.000
##     W2FUTURE.PROS     1.000
##     W3FUTURE.PROS     4.000
##     W4FUTURE.PROS     9.000
##     W5FUTURE.PROS    16.000
## 
## Covariances:
##   i ~~
##     s                -0.009    0.010   -0.838    0.402
##     q                 0.000    0.002    0.196    0.845
##   s ~~
##     q                -0.006    0.002   -2.773    0.006
## 
## Intercepts:
##     s         (b)     0.042    0.010    4.420    0.000
##     q         (c)    -0.010    0.002   -4.272    0.000
##     W1FUTURE.         0.000
##     W2FUTURE.         0.000
##     W3FUTURE.         0.000
##     W4FUTURE.         0.000
##     W5FUTURE.         0.000
##     i                 3.396    0.009  358.685    0.000
## 
## Variances:
##     W1FUTURE.PROS     0.161    0.012
##     W2FUTURE.PROS     0.168    0.006
##     W3FUTURE.PROS     0.180    0.007
##     W4FUTURE.PROS     0.158    0.006
##     W5FUTURE.PROS     0.143    0.013
##     i                 0.111    0.012
##     s                 0.028    0.011
##     q                 0.002    0.001
## 
## Defined parameters:
##     tpG2              2.099    0.153   13.711    0.000
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

