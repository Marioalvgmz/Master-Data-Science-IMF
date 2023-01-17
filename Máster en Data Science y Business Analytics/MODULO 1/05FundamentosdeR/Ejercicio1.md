# Caso práctico 1

1.  Crea un vector con la secuencia 1, 2, 3, 4, 5 de longitud 10.

2.  Crea un array de dos dimensiones, de 10 elementos cada una, con los
    20 primeros números pares del 0 al 40.

3.  Crea una muestra de números aleatorios del 1 a 100 con repetición de
    longitud 10.

4.  Crea un nuevo vector que sea el resultado de la suma fila a fila de
    cada dimensión del array.

5.  Finalmente, crea un dataframe con todas las estructuras de datos
    creadas anteriormente y muestra el resumen estadístico del
    dataframe.

6.  Crea un vector con la secuencia 1, 2, 3, 4, 5 de longitud 10.

``` r
vec <- 1:10
vec
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

1.  Crea un array de dos dimensiones, de 10 elementos cada una, con los
    20 primeros números pares del 0 al 40.

``` r
#Vector auxiliar para rellenar
aux.vec <- c()

#Bucle pares a vector
i<- 1
for (number in 0:40) {
  if (number %% 2  == 0) {
    aux.vec[i] <- number
    i<-i+1
  }
  else{
    next
  }
}

aux.vec
```

    ##  [1]  0  2  4  6  8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40

``` r
#Crear array
arr <- array(aux.vec, dim=c(10,2))
arr
```

    ##       [,1] [,2]
    ##  [1,]    0   20
    ##  [2,]    2   22
    ##  [3,]    4   24
    ##  [4,]    6   26
    ##  [5,]    8   28
    ##  [6,]   10   30
    ##  [7,]   12   32
    ##  [8,]   14   34
    ##  [9,]   16   36
    ## [10,]   18   38

1.  Crea una muestra de números aleatorios del 1 a 100 con repetición de
    longitud 10.

``` r
muestra <- sample(1:100, 10, replace=T)
muestra
```

    ##  [1] 28 58 69 82 30 55 71 41 51 80

1.  Crea un nuevo vector que sea el resultado de la suma fila a fila de
    cada dimensión del array.

``` r
arr.sums <- rowSums(arr)
arr.sums
```

    ##  [1] 20 24 28 32 36 40 44 48 52 56

1.  Finalmente, crea un dataframe con todas las estructuras de datos
    creadas anteriormente y muestra el resumen estadístico del
    dataframe.

``` r
df <- data.frame("columna 1"=vec,"columna 2"=arr, "columna 3"=muestra, "columna 4"=arr.sums)
df
```

    ##    columna.1 columna.2.1 columna.2.2 columna.3 columna.4
    ## 1          1           0          20        28        20
    ## 2          2           2          22        58        24
    ## 3          3           4          24        69        28
    ## 4          4           6          26        82        32
    ## 5          5           8          28        30        36
    ## 6          6          10          30        55        40
    ## 7          7          12          32        71        44
    ## 8          8          14          34        41        48
    ## 9          9          16          36        51        52
    ## 10        10          18          38        80        56

``` r
summary(df)
```

    ##    columna.1      columna.2.1    columna.2.2     columna.3      columna.4 
    ##  Min.   : 1.00   Min.   : 0.0   Min.   :20.0   Min.   :28.0   Min.   :20  
    ##  1st Qu.: 3.25   1st Qu.: 4.5   1st Qu.:24.5   1st Qu.:43.5   1st Qu.:29  
    ##  Median : 5.50   Median : 9.0   Median :29.0   Median :56.5   Median :38  
    ##  Mean   : 5.50   Mean   : 9.0   Mean   :29.0   Mean   :56.5   Mean   :38  
    ##  3rd Qu.: 7.75   3rd Qu.:13.5   3rd Qu.:33.5   3rd Qu.:70.5   3rd Qu.:47  
    ##  Max.   :10.00   Max.   :18.0   Max.   :38.0   Max.   :82.0   Max.   :56
