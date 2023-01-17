# Caso práctico 2

Mediante los siguientes datos, sobre los que se simulará información
aleatoria para los años comprendidos entre 2016 y 2020:

vec.1 \<- sample(1:100, 100, replace = T) vec.2 \<- sample(50:150, 100,
replace = T) vec.3 \<- rep(c(“2020”, “2019”, “2018”, “2017”, “2016”),
20)

1.  Crea una matriz de dos columnas con los vectores “vec.1” y “vec.2”.
2.  Crea un nuevo vector que sea la suma de las filas de la matriz al
    cuadrado.
3.  Crea un dataframe con todos los vectores con las siguientes
    columnas:
    -   vec.1: Low.
    -   vec.2: High.
    -   Vector del apartado 2: Volume.
    -   vec.3: Year (tiene que ser una variable factor).
4.  Muestra el resumen estadístico del dataframe.
5.  Muestra la estructura de variables del dataframe.
6.  Asigna valor nulo (NA) a todos los valores de la columna “Low” por
    debajo de 20.
7.  Muestra el número de valores nulos de cada columna.
8.  Muestra la media de la columna “Volume” en función de cada factor de
    “Year”.
9.  Asigna a cada valor “NaN” la media de la columna “Low” (pista:
    investigar en la función “mean” cómo trabajar con nulos).
10. Obtén un subconjunto de los datos que sean todos los valores de 2020
    y que tengan valor superior a 90 en la columna “High”.
11. Investiga sobre la función “write.csv” y crea un archivo CSV con
    nombre “2020_Values.csv”.

``` r
#Cargar los vectores
vec.1 <- sample(1:100, 100, replace = T)
vec.2 <- sample(50:150, 100, replace = T)
vec.3 <- rep(c("2020", "2019", "2018", "2017", "2016"), 20)
```

1.  Crea una matriz de dos columnas con los vectores “vec.1” y “vec.2”.

``` r
mat <- matrix(c(vec.1,vec.2), nrow=length(vec.1) ,ncol=2, byrow = T)
mat[1:10,]
```

    ##       [,1] [,2]
    ##  [1,]   89   36
    ##  [2,]    8  100
    ##  [3,]   72   83
    ##  [4,]   11   76
    ##  [5,]    2   54
    ##  [6,]   40   52
    ##  [7,]   92    3
    ##  [8,]    5   58
    ##  [9,]   26  100
    ## [10,]   64   48

1.  Crea un nuevo vector que sea la suma de las filas de la matriz al
    cuadrado.

``` r
volume <-apply(mat, 1, sum)^2
volume[0:10]
```

    ##  [1] 15625 11664 24025  7569  3136  8464  9025  3969 15876 12544

1.  Crea un dataframe con todos los vectores con las siguientes
    columnas:
    -   vec.1: Low.
    -   vec.2: High.
    -   Vector del apartado 2: Volume.
    -   vec.3: Year (tiene que ser una variable factor).

``` r
df <- data.frame("Low" = vec.1, "High" = vec.2, "Volume" = volume, "Year" = as.factor(vec.3))
head(df)
```

    ##   Low High Volume Year
    ## 1  89   67  15625 2020
    ## 2  36   66  11664 2019
    ## 3   8  138  24025 2018
    ## 4 100   96   7569 2017
    ## 5  72  122   3136 2016
    ## 6  83  118   8464 2020

1.  Muestra el resumen estadístico del dataframe.

``` r
summary(df)
```

    ##       Low              High           Volume        Year   
    ##  Min.   :  1.00   Min.   : 51.0   Min.   :  841   2016:20  
    ##  1st Qu.: 22.75   1st Qu.: 82.5   1st Qu.:11504   2017:20  
    ##  Median : 55.00   Median :104.0   Median :22501   2018:20  
    ##  Mean   : 51.23   Mean   :102.0   Mean   :27630   2019:20  
    ##  3rd Qu.: 77.00   3rd Qu.:123.2   3rd Qu.:43162   2020:20  
    ##  Max.   :100.00   Max.   :150.0   Max.   :86436

1.  Muestra la estructura de variables del dataframe.

``` r
str(df)
```

    ## 'data.frame':    100 obs. of  4 variables:
    ##  $ Low   : int  89 36 8 100 72 83 11 76 2 54 ...
    ##  $ High  : int  67 66 138 96 122 118 55 115 137 144 ...
    ##  $ Volume: num  15625 11664 24025 7569 3136 ...
    ##  $ Year  : Factor w/ 5 levels "2016","2017",..: 5 4 3 2 1 5 4 3 2 1 ...

1.  Asigna valor nulo (NA) a todos los valores de la columna “Low” por
    debajo de 20.

``` r
df[df$Low < 20, "Low"] <- NA

summary(df)
```

    ##       Low              High           Volume        Year   
    ##  Min.   : 21.00   Min.   : 51.0   Min.   :  841   2016:20  
    ##  1st Qu.: 42.00   1st Qu.: 82.5   1st Qu.:11504   2017:20  
    ##  Median : 65.00   Median :104.0   Median :22501   2018:20  
    ##  Mean   : 63.33   Mean   :102.0   Mean   :27630   2019:20  
    ##  3rd Qu.: 82.75   3rd Qu.:123.2   3rd Qu.:43162   2020:20  
    ##  Max.   :100.00   Max.   :150.0   Max.   :86436            
    ##  NA's   :22

1.  Muestra el número de valores nulos de cada columna.

``` r
apply(is.na(df), 2, sum)
```

    ##    Low   High Volume   Year 
    ##     22      0      0      0

1.  Muestra la media de la columna “Volume” en función de cada factor de
    “Year”.

``` r
tapply(df$Volume, df$Year, mean)
```

    ##     2016     2017     2018     2019     2020 
    ## 28760.55 30600.40 19505.65 31018.10 28264.45

1.  Asigna a cada valor “NaN” la media de la columna “Low” (pista:
    investigar en la función “mean” cómo trabajar con nulos).

``` r
df$Low[which(is.na(df$Low))] <- mean(df$Low, na.rm=T)
summary(df)
```

    ##       Low              High           Volume        Year   
    ##  Min.   : 21.00   Min.   : 51.0   Min.   :  841   2016:20  
    ##  1st Qu.: 51.00   1st Qu.: 82.5   1st Qu.:11504   2017:20  
    ##  Median : 63.33   Median :104.0   Median :22501   2018:20  
    ##  Mean   : 63.33   Mean   :102.0   Mean   :27630   2019:20  
    ##  3rd Qu.: 77.00   3rd Qu.:123.2   3rd Qu.:43162   2020:20  
    ##  Max.   :100.00   Max.   :150.0   Max.   :86436

1.  Obtén un subconjunto de los datos que sean todos los valores de 2020
    y que tengan valor superior a 90 en la columna “High”.

``` r
year.values <- df[df$High > 90 & df$Year == "2020",]
year.values
```

    ##         Low High Volume Year
    ## 6  83.00000  118   8464 2020
    ## 11 40.00000  129  11664 2020
    ## 21 70.00000  127  17689 2020
    ## 31 90.00000  140    841 2020
    ## 41 35.00000   91  10201 2020
    ## 46 64.00000  103  13225 2020
    ## 51 96.00000  110  17689 2020
    ## 66 63.33333   97  47089 2020
    ## 71 55.00000   93  39204 2020
    ## 81 26.00000  112  48841 2020

-   1.  Investiga sobre la función **`write.csv`**, crea un archivo csv
        con nombre “2020_Values.csv”

``` r
write.csv2(year.values, file = "2020_Values.csv", row.names = F)
```
