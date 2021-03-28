REDES NEURONALES SIMPLES
================

# Entrenamiento de una red que calcula el cuadrado de un número.

``` r
x = c(0:10)
y = x^2
z = c(x,y)
entrenador = matrix(z, ncol = 2, byrow = FALSE)
colnames(entrenador)=c("nro", "cuadrado")
entrenador
```

    ##       nro cuadrado
    ##  [1,]   0        0
    ##  [2,]   1        1
    ##  [3,]   2        4
    ##  [4,]   3        9
    ##  [5,]   4       16
    ##  [6,]   5       25
    ##  [7,]   6       36
    ##  [8,]   7       49
    ##  [9,]   8       64
    ## [10,]   9       81
    ## [11,]  10      100

``` r
library(neuralnet)
```

# Entrenamiento de la red

``` r
library(neuralnet)
modelo=neuralnet(formula = cuadrado~nro, 
                data = entrenador, 
                hidden=30,threshold=0.01 )
```

# Visualizacion de modelo

``` r
print(modelo)
```

    ## $call
    ## neuralnet(formula = cuadrado ~ nro, data = entrenador, hidden = 30, 
    ##     threshold = 0.01)
    ## 
    ## $response
    ##    cuadrado
    ## 1         0
    ## 2         1
    ## 3         4
    ## 4         9
    ## 5        16
    ## 6        25
    ## 7        36
    ## 8        49
    ## 9        64
    ## 10       81
    ## 11      100
    ## 
    ## $covariate
    ##         
    ##  [1,]  0
    ##  [2,]  1
    ##  [3,]  2
    ##  [4,]  3
    ##  [5,]  4
    ##  [6,]  5
    ##  [7,]  6
    ##  [8,]  7
    ##  [9,]  8
    ## [10,]  9
    ## [11,] 10
    ## 
    ## $model.list
    ## $model.list$response
    ## [1] "cuadrado"
    ## 
    ## $model.list$variables
    ## [1] "nro"
    ## 
    ## 
    ## $err.fct
    ## function (x, y) 
    ## {
    ##     1/2 * (y - x)^2
    ## }
    ## <bytecode: 0x0000000015387410>
    ## <environment: 0x00000000153899c0>
    ## attr(,"type")
    ## [1] "sse"
    ## 
    ## $act.fct
    ## function (x) 
    ## {
    ##     1/(1 + exp(-x))
    ## }
    ## <bytecode: 0x0000000015382788>
    ## <environment: 0x0000000015385c88>
    ## attr(,"type")
    ## [1] "logistic"
    ## 
    ## $linear.output
    ## [1] TRUE
    ## 
    ## $data
    ##    nro cuadrado
    ## 1    0        0
    ## 2    1        1
    ## 3    2        4
    ## 4    3        9
    ## 5    4       16
    ## 6    5       25
    ## 7    6       36
    ## 8    7       49
    ## 9    8       64
    ## 10   9       81
    ## 11  10      100
    ## 
    ## $exclude
    ## NULL
    ## 
    ## $net.result
    ## $net.result[[1]]
    ##               [,1]
    ##  [1,] -0.002632644
    ##  [2,]  1.009600506
    ##  [3,]  3.975748161
    ##  [4,]  9.030061307
    ##  [5,] 15.992012094
    ##  [6,] 24.977872935
    ##  [7,] 36.026341786
    ##  [8,] 49.006495090
    ##  [9,] 63.958361958
    ## [10,] 81.038392806
    ## [11,] 99.987386195
    ## 
    ## 
    ## $weights
    ## $weights[[1]]
    ## $weights[[1]][[1]]
    ##            [,1]       [,2]       [,3]      [,4]       [,5]      [,6]       [,7]
    ## [1,] -1.8238706 -3.9920416  4.3163239 -3.812667 -2.0182168  3.855222 -8.4685361
    ## [2,]  0.6877292  0.5392215 -0.5580568  0.526594  0.5424963 -0.530058  0.7832334
    ##            [,8]      [,9]      [,10]      [,11]      [,12]      [,13]
    ## [1,] -3.0908270 -2.979024 -4.7365396 -5.1085140  0.4918372  6.6387271
    ## [2,]  0.4720622  0.463051  0.5405421  0.5062792 -1.5031574 -0.6307874
    ##           [,14]      [,15]      [,16]      [,17]      [,18]      [,19]
    ## [1,] -3.0455740  3.4442692 -5.0466310 -3.2355612 -7.8584977  6.3791031
    ## [2,]  0.4651943 -0.5003868  0.4776315  0.4794221  0.7323873 -0.6167648
    ##           [,20]     [,21]      [,22]      [,23]     [,24]     [,25]     [,26]
    ## [1,]  4.3050291 0.4838288 -4.4973825  6.1050395 -3.955738 3.4702069 -6.192165
    ## [2,] -0.5500448 0.2143695  0.5744403 -0.6014613  0.533422 0.1286164  0.600386
    ##           [,27]     [,28]      [,29]      [,30]
    ## [1,] -7.0867730  5.800908 -3.2240374 -1.2169645
    ## [2,]  0.6664275 -1.094593  0.4864019  0.4027676
    ## 
    ## $weights[[1]][[2]]
    ##            [,1]
    ##  [1,]  3.714427
    ##  [2,]  5.273689
    ##  [3,]  6.645664
    ##  [4,] -1.852487
    ##  [5,]  6.534513
    ##  [6,]  5.407133
    ##  [7,] -1.691826
    ##  [8,] 31.718538
    ##  [9,]  6.129416
    ## [10,]  6.314207
    ## [11,]  6.679457
    ## [12,]  7.290559
    ## [13,]  4.729684
    ## [14,] -1.937303
    ## [15,]  6.320986
    ## [16,] -1.977269
    ## [17,]  5.575980
    ## [18,]  6.435803
    ## [19,] 14.912989
    ## [20,] -2.845732
    ## [21,] -1.644905
    ## [22,]  2.033483
    ## [23,]  6.611136
    ## [24,] -3.300530
    ## [25,]  7.132661
    ## [26,]  5.464813
    ## [27,]  7.894400
    ## [28,]  8.436989
    ## [29,] -2.445567
    ## [30,]  4.597492
    ## [31,]  4.524243
    ## 
    ## 
    ## 
    ## $generalized.weights
    ## $generalized.weights[[1]]
    ##                [,1]
    ##  [1,] -1.960448e+02
    ##  [2,] -1.899224e+02
    ##  [3,] -3.437669e-01
    ##  [4,] -8.283634e-02
    ##  [5,] -3.313988e-02
    ##  [6,] -1.675659e-02
    ##  [7,] -9.532999e-03
    ##  [8,] -5.925272e-03
    ##  [9,] -3.972793e-03
    ## [10,] -2.796639e-03
    ## [11,] -1.969376e-03
    ## 
    ## 
    ## $startweights
    ## $startweights[[1]]
    ## $startweights[[1]][[1]]
    ##          [,1]       [,2]        [,3]      [,4]       [,5]      [,6]       [,7]
    ## [1,] 1.559765 -0.5302840  0.09564013 0.5940818  0.3403863 0.4554515 -1.6613628
    ## [2,] 1.154667 -0.2277299 -0.23753334 0.6676451 -0.3382431 0.1730033  0.9567427
    ##             [,8]     [,9]      [,10]       [,11]     [,12]      [,13]     [,14]
    ## [1,]  0.48326723 1.398890 -0.4866838 -0.09202297 -1.602973  0.9369088 1.2723251
    ## [2,] -0.01965298 1.669551 -0.1515416  0.86980086 -1.960158 -0.1859987 0.7598649
    ##           [,15]      [,16]      [,17]      [,18]      [,19]       [,20]
    ## [1,] -0.8418026 -0.9027434 -0.5293755 -2.0369301  0.2243345 -0.03343425
    ## [2,] -0.9456627  0.8759141 -0.6179521  0.9031351 -0.8281218 -0.19865607
    ##           [,21]       [,22]       [,23]     [,24]      [,25]     [,26]
    ## [1,] -0.1357282 -0.48397475 -0.04613923 0.5366193  1.5566990 0.3521309
    ## [2,] -1.7336946  0.09642054 -1.15798299 0.5532634 -0.9183488 1.2260834
    ##           [,27]     [,28]      [,29]     [,30]
    ## [1,] -0.7527765 -1.075941 -0.3508314 1.1348270
    ## [2,]  1.1850097 -1.548522  1.8336418 0.6126427
    ## 
    ## $startweights[[1]][[2]]
    ##             [,1]
    ##  [1,] -1.3672796
    ##  [2,]  0.1604533
    ##  [3,]  0.6576890
    ##  [4,] -1.2476055
    ##  [5,]  0.5462319
    ##  [6,]  0.3138412
    ##  [7,] -1.4957000
    ##  [8,]  0.8622681
    ##  [9,]  0.5564014
    ## [10,]  0.7376222
    ## [11,]  0.3260979
    ## [12,]  0.7178033
    ## [13,]  0.9258298
    ## [14,] -0.4104463
    ## [15,]  1.2421980
    ## [16,] -1.0636334
    ## [17,] -0.9967754
    ## [18,]  0.8637541
    ## [19,] -0.7783250
    ## [20,] -0.9188750
    ## [21,] -1.0319075
    ## [22,]  0.8135295
    ## [23,]  0.6168600
    ## [24,] -1.6213445
    ## [25,]  1.1443802
    ## [26,]  0.3831061
    ## [27,] -0.1659360
    ## [28,]  0.3766462
    ## [29,]  0.1624769
    ## [30,] -0.9745566
    ## [31,] -0.5675563
    ## 
    ## 
    ## 
    ## $result.matrix
    ##                                 [,1]
    ## error                   3.123633e-03
    ## reached.threshold       7.904220e-03
    ## steps                   3.781000e+03
    ## Intercept.to.1layhid1  -1.823871e+00
    ## nro.to.1layhid1         6.877292e-01
    ## Intercept.to.1layhid2  -3.992042e+00
    ## nro.to.1layhid2         5.392215e-01
    ## Intercept.to.1layhid3   4.316324e+00
    ## nro.to.1layhid3        -5.580568e-01
    ## Intercept.to.1layhid4  -3.812667e+00
    ## nro.to.1layhid4         5.265940e-01
    ## Intercept.to.1layhid5  -2.018217e+00
    ## nro.to.1layhid5         5.424963e-01
    ## Intercept.to.1layhid6   3.855222e+00
    ## nro.to.1layhid6        -5.300580e-01
    ## Intercept.to.1layhid7  -8.468536e+00
    ## nro.to.1layhid7         7.832334e-01
    ## Intercept.to.1layhid8  -3.090827e+00
    ## nro.to.1layhid8         4.720622e-01
    ## Intercept.to.1layhid9  -2.979024e+00
    ## nro.to.1layhid9         4.630510e-01
    ## Intercept.to.1layhid10 -4.736540e+00
    ## nro.to.1layhid10        5.405421e-01
    ## Intercept.to.1layhid11 -5.108514e+00
    ## nro.to.1layhid11        5.062792e-01
    ## Intercept.to.1layhid12  4.918372e-01
    ## nro.to.1layhid12       -1.503157e+00
    ## Intercept.to.1layhid13  6.638727e+00
    ## nro.to.1layhid13       -6.307874e-01
    ## Intercept.to.1layhid14 -3.045574e+00
    ## nro.to.1layhid14        4.651943e-01
    ## Intercept.to.1layhid15  3.444269e+00
    ## nro.to.1layhid15       -5.003868e-01
    ## Intercept.to.1layhid16 -5.046631e+00
    ## nro.to.1layhid16        4.776315e-01
    ## Intercept.to.1layhid17 -3.235561e+00
    ## nro.to.1layhid17        4.794221e-01
    ## Intercept.to.1layhid18 -7.858498e+00
    ## nro.to.1layhid18        7.323873e-01
    ## Intercept.to.1layhid19  6.379103e+00
    ## nro.to.1layhid19       -6.167648e-01
    ## Intercept.to.1layhid20  4.305029e+00
    ## nro.to.1layhid20       -5.500448e-01
    ## Intercept.to.1layhid21  4.838288e-01
    ## nro.to.1layhid21        2.143695e-01
    ## Intercept.to.1layhid22 -4.497383e+00
    ## nro.to.1layhid22        5.744403e-01
    ## Intercept.to.1layhid23  6.105040e+00
    ## nro.to.1layhid23       -6.014613e-01
    ## Intercept.to.1layhid24 -3.955738e+00
    ## nro.to.1layhid24        5.334220e-01
    ## Intercept.to.1layhid25  3.470207e+00
    ## nro.to.1layhid25        1.286164e-01
    ## Intercept.to.1layhid26 -6.192165e+00
    ## nro.to.1layhid26        6.003860e-01
    ## Intercept.to.1layhid27 -7.086773e+00
    ## nro.to.1layhid27        6.664275e-01
    ## Intercept.to.1layhid28  5.800908e+00
    ## nro.to.1layhid28       -1.094593e+00
    ## Intercept.to.1layhid29 -3.224037e+00
    ## nro.to.1layhid29        4.864019e-01
    ## Intercept.to.1layhid30 -1.216964e+00
    ## nro.to.1layhid30        4.027676e-01
    ## Intercept.to.cuadrado   3.714427e+00
    ## 1layhid1.to.cuadrado    5.273689e+00
    ## 1layhid2.to.cuadrado    6.645664e+00
    ## 1layhid3.to.cuadrado   -1.852487e+00
    ## 1layhid4.to.cuadrado    6.534513e+00
    ## 1layhid5.to.cuadrado    5.407133e+00
    ## 1layhid6.to.cuadrado   -1.691826e+00
    ## 1layhid7.to.cuadrado    3.171854e+01
    ## 1layhid8.to.cuadrado    6.129416e+00
    ## 1layhid9.to.cuadrado    6.314207e+00
    ## 1layhid10.to.cuadrado   6.679457e+00
    ## 1layhid11.to.cuadrado   7.290559e+00
    ## 1layhid12.to.cuadrado   4.729684e+00
    ## 1layhid13.to.cuadrado  -1.937303e+00
    ## 1layhid14.to.cuadrado   6.320986e+00
    ## 1layhid15.to.cuadrado  -1.977269e+00
    ## 1layhid16.to.cuadrado   5.575980e+00
    ## 1layhid17.to.cuadrado   6.435803e+00
    ## 1layhid18.to.cuadrado   1.491299e+01
    ## 1layhid19.to.cuadrado  -2.845732e+00
    ## 1layhid20.to.cuadrado  -1.644905e+00
    ## 1layhid21.to.cuadrado   2.033483e+00
    ## 1layhid22.to.cuadrado   6.611136e+00
    ## 1layhid23.to.cuadrado  -3.300530e+00
    ## 1layhid24.to.cuadrado   7.132661e+00
    ## 1layhid25.to.cuadrado   5.464813e+00
    ## 1layhid26.to.cuadrado   7.894400e+00
    ## 1layhid27.to.cuadrado   8.436989e+00
    ## 1layhid28.to.cuadrado  -2.445567e+00
    ## 1layhid29.to.cuadrado   4.597492e+00
    ## 1layhid30.to.cuadrado   4.524243e+00
    ## 
    ## attr(,"class")
    ## [1] "nn"

# Ploteo de la red neuronal

``` r
library(NeuralNetTools)
library(nnet)
plot(modelo)
plotnet(modelo)
```

# Uso de la red para predecir

``` r
test <- data.frame(entrenador = 12)
 prediccion <- compute(x=modelo, covariate=test)
 prediccion
```

    ## $neurons
    ## $neurons[[1]]
    ##        entrenador
    ## [1,] 1         12
    ## 
    ## $neurons[[2]]
    ##      [,1]      [,2]      [,3]       [,4]      [,5]      [,6]       [,7]
    ## [1,]    1 0.9983883 0.9226291 0.08468283 0.9245935 0.9889229 0.07547534
    ##           [,8]      [,9]     [,10]     [,11]     [,12]        [,13]     [,14]
    ## [1,] 0.7171289 0.9291641 0.9294052 0.8519484 0.7244884 2.397985e-08 0.2827783
    ##          [,15]      [,16]    [,17]     [,18]     [,19]     [,20]     [,21]
    ## [1,] 0.9266788 0.07173275 0.664842 0.9253598 0.7171056 0.2646236 0.0914956
    ##          [,22]     [,23]     [,24]    [,25]    [,26]     [,27]     [,28]
    ## [1,] 0.9550521 0.9165142 0.2474057 0.920219 0.993397 0.7335029 0.7130731
    ##            [,29]     [,30]     [,31]
    ## [1,] 0.000652394 0.9316799 0.9738204
    ## 
    ## 
    ## $net.result
    ##          [,1]
    ## [1,] 135.7905

# Ejemplo de uso con emprendedores logisticos

``` r
library(neuralnet)  # regression

library(nnet) # classification 

library(NeuralNetTools)

library(plyr)
```

# Carga de datos de emprendimientos logisticos

``` r
library(readr)

Categoric <- read_csv("https://themys.sid.uncu.edu.ar/rpalma/R-cran/50_Startups_Categoric_LAC.csv")
```

    ## 
    ## -- Column specification --------------------------------------------------------
    ## cols(
    ##   R_D_Spend = col_double(),
    ##   POM = col_double(),
    ##   Logist_Market = col_double(),
    ##   Pais = col_character(),
    ##   Profit = col_double(),
    ##   Supervivencia = col_character()
    ## )

``` r
str(Categoric)
```

    ## spec_tbl_df [50 x 6] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ R_D_Spend    : num [1:50] 165349 162598 153442 144372 142107 ...
    ##  $ POM          : num [1:50] 136898 151378 101146 118672 91392 ...
    ##  $ Logist_Market: num [1:50] 471784 443899 407935 383200 366168 ...
    ##  $ Pais         : chr [1:50] "Colombia" "Ecuador" "Chile" "Colombia" ...
    ##  $ Profit       : num [1:50] 192262 191792 191050 182902 166188 ...
    ##  $ Supervivencia: chr [1:50] "SpinOff" "SpinOff" "SpinOff" "SpinOff" ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   R_D_Spend = col_double(),
    ##   ..   POM = col_double(),
    ##   ..   Logist_Market = col_double(),
    ##   ..   Pais = col_character(),
    ##   ..   Profit = col_double(),
    ##   ..   Supervivencia = col_character()
    ##   .. )

# Tratamiento de valores categoricos

``` r
tabla1 <- table(Categoric$Pais)
tabla2 <- table(Categoric$Supervivencia)
tabla3 <- table(Categoric$Pais,Categoric$Supervivencia)
plot(tabla1, col=c("red","green","blue"))
```

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

``` r
plot(tabla2, col=c("red","green","blue"))
```

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-9-2.png)<!-- -->

``` r
plot(tabla3, col=c("red","green","blue"))
```

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-9-3.png)<!-- -->

# Histogramas superpuestos

``` r
ind_1 <- which(Categoric$Pais=="Colombia")
p1 <- as.matrix(Categoric[ind_1,5])

ind_2 <- which(Categoric$Pais=="Ecuador")
p2 <- as.matrix(Categoric[ind_2,5])

ind_3 <- which(Categoric$Pais=="Chile")
p3 <- as.matrix(Categoric[ind_3,5])
hp1 <- hist(p1)
```

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

``` r
hp2 <- hist(p2)
```

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-10-2.png)<!-- -->

``` r
hp3 <- hist(p3)
```

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-10-3.png)<!-- -->

``` r
par(mfrow=c(3,1))
plot( hp1, col=rgb(0,0,1,1/4), xlim=c(30000,200000),ylim=c(0,5),main="Ecuador")
plot( hp2, col=rgb(1,0,0,1/4),xlim=c(30000,200000),ylim=c(0,10),main="Colombia") 
plot( hp3, col=rgb(1,0,0,1/4),xlim=c(30000,200000),ylim=c(0,10),main="Chile") 
par(mfrow=c(1,3))
plot( hp1, col=rgb(0,0,1,1/4), xlim=c(30000,200000),ylim=c(0,5),main="Ecuador")
plot( hp2, col=rgb(1,0,0,1/4),xlim=c(30000,200000),ylim=c(0,10),main="Colombia") 
plot( hp3, col=rgb(1,0,0,1/4),xlim=c(30000,200000),ylim=c(0,10),main="Chile") 
```

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-10-4.png)<!-- -->

``` r
pairs(Categoric[ ,1:3])
```

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-10-5.png)<!-- -->

``` r
boxplot(Categoric[ ,1:3])
Categoric$Pais <- as.numeric(revalue(Categoric$Pais,
                          c("Colombia"="0", "Ecuador"="1",
                            "Chile"="2")))
```

    ## Warning: NAs introducidos por coerción

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-10-6.png)<!-- -->

# Cuadro de campos categoricos

``` r
Categoric$Supervivencia <- as.numeric(revalue(Categoric$Supervivencia,
                          c("BankR"="0", "RevEq"="1",
                            "SpinOff"="2")))
```

# Profit vs pais

``` r
plot(Categoric$Pais, Categoric$Profit)
```

![](REDNEURONAL_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

# Vislaizacion de tablas

``` r
library(kableExtra)
kable(head(Categoric), "pipe")
```

| R\_D\_Spend |       POM | Logist\_Market | Pais |   Profit | Supervivencia |
|------------:|----------:|---------------:|-----:|---------:|--------------:|
|    165349.2 | 136897.80 |       471784.1 |    0 | 192261.8 |             2 |
|    162597.7 | 151377.59 |       443898.5 |    1 | 191792.1 |             2 |
|    153441.5 | 101145.55 |       407934.5 |    2 | 191050.4 |             2 |
|    144372.4 | 118671.85 |       383199.6 |    0 | 182902.0 |             2 |
|    142107.3 |  91391.77 |       366168.4 |    2 | 166187.9 |             2 |
|    131876.9 |  99814.71 |       362861.4 |    0 | 156991.1 |             2 |

# Tabla simple

``` r
kable(head(Categoric), "simple")
```

| R\_D\_Spend |       POM | Logist\_Market | Pais |   Profit | Supervivencia |
|------------:|----------:|---------------:|-----:|---------:|--------------:|
|    165349.2 | 136897.80 |       471784.1 |    0 | 192261.8 |             2 |
|    162597.7 | 151377.59 |       443898.5 |    1 | 191792.1 |             2 |
|    153441.5 | 101145.55 |       407934.5 |    2 | 191050.4 |             2 |
|    144372.4 | 118671.85 |       383199.6 |    0 | 182902.0 |             2 |
|    142107.3 |  91391.77 |       366168.4 |    2 | 166187.9 |             2 |
|    131876.9 |  99814.71 |       362861.4 |    0 | 156991.1 |             2 |

# Normalizacion

``` r
normalize<-function(x){
  return ( (x-min(x))/(max(x)-min(x)))
}

Startups_norm<-as.data.frame(lapply(Categoric,FUN=normalize))
summary(Startups_norm$Profit)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##  0.0000  0.4249  0.5254  0.5481  0.7044  1.0000

## Including Plots

You can also embed plots, for example:

![](REDNEURONAL_files/figure-gfm/pressure-1.png)<!-- -->

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.
