# Caso practico 1

## Ejercicio 1

Crear una matriz como la siguiente:

     [, 1] [, 2] [, 3]

\[1,\] 1 8 3

\[2,\] 5 1 2

-   Primer elemento de la primera columna.
-   Segunda fila, tercera columna.
-   Primera fila.
-   Segunda columna.
-   Primera y segunda columna, primera fila.
-   Primera y tercera columna, segunda fila.
-   Todas las columnas excepto la segunda.

``` r
matriz <- matrix(c(1,8,3,5,1,2), ncol=3, byrow=TRUE)
matriz
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    8    3
    ## [2,]    5    1    2

``` r
matriz[1,1]
```

    ## [1] 1

``` r
matriz[2,3]
```

    ## [1] 2

``` r
matriz[1,]
```

    ## [1] 1 8 3

``` r
matriz[,2]
```

    ## [1] 8 1

``` r
matriz[1,c(1,2)]
```

    ## [1] 1 8

``` r
matriz[2,c(1,3)]
```

    ## [1] 5 2

``` r
matriz[,-2]
```

    ##      [,1] [,2]
    ## [1,]    1    3
    ## [2,]    5    2

## Ejercicio 2

Crear vectores para las columnas de la matriz:

warner \<- c(20, 20, 16, 17, 17, 22, 17, 18, 19)

disney \<- c(11, 13, 11, 8, 12, 11, 12, 8, 10)

fox \<- c(18, 15, 15, 15, 16, 17, 15, 13, 11)

-   Crear una matriz llamada compañiascine a partir de vectores antes
    anteriores.
-   Imprimir el contenido de la matriz.

``` r
warner <- c(20, 20, 16, 17, 17, 22, 17, 18, 19)
disney <- c(11, 13, 11, 8, 12, 11, 12, 8, 10)
fox <- c(18, 15, 15, 15, 16, 17, 15, 13, 11)

compañiascine <- matrix(c(warner,disney,fox), ncol=3, dimnames = list(c(),c("Warner","Disney","Fox")))
compañiascine
```

    ##       Warner Disney Fox
    ##  [1,]     20     11  18
    ##  [2,]     20     13  15
    ##  [3,]     16     11  15
    ##  [4,]     17      8  15
    ##  [5,]     17     12  16
    ##  [6,]     22     11  17
    ##  [7,]     17     12  15
    ##  [8,]     18      8  13
    ##  [9,]     19     10  11

# Caso Practico 2

## Ejercicio 1

Crear una matriz 3 x 2, como la siguiente:

     [, 1] [, 2] 

\[1,\] 1 4

\[2,\] 2 5

\[3,\] 3 6

De ella, se quiere ver:

1.  Número de elementos de x
2.  Tipo de datos de la matriz x
3.  Dimensiones de la matriz x
4.  Nombre de las filas de la matriz
5.  Nombre de las columnas de la matriz

``` r
x <- matrix(c(1,2,3,4,5,6), ncol=2)
x
```

    ##      [,1] [,2]
    ## [1,]    1    4
    ## [2,]    2    5
    ## [3,]    3    6

``` r
typeof(x)
```

    ## [1] "double"

``` r
dim(x)
```

    ## [1] 3 2

``` r
rownames(x)
```

    ## NULL

``` r
colnames(x)
```

    ## NULL

## Ejercicio 2

Se debe crear la siguiente matriz:

     Edad  Peso  Altura  

Paco 20 65 174

Pepe 22 70 180

Kiko 19 68 170

1.  Edades de todas las personas
2.  Datos de “Pepe”
3.  Edad y altura de todas las personas
4.  Mostrar los nombres de filas y cols.

``` r
e <- c(20,22,19)
p <- c(65,70,68)
a <- c(174,180,170)

m<-matrix(c(e,p,a), ncol=3,
          dimnames = list(
            c("Paco","Pepe","Kiko"),c("Edad","Peso","Altura")
          ))
m
```

    ##      Edad Peso Altura
    ## Paco   20   65    174
    ## Pepe   22   70    180
    ## Kiko   19   68    170

``` r
m[,"Edad"]
```

    ## Paco Pepe Kiko 
    ##   20   22   19

``` r
m["Pepe",]
```

    ##   Edad   Peso Altura 
    ##     22     70    180

``` r
m[,c("Edad","Altura")]
```

    ##      Edad Altura
    ## Paco   20    174
    ## Pepe   22    180
    ## Kiko   19    170

``` r
colnames(m)
```

    ## [1] "Edad"   "Peso"   "Altura"

``` r
rownames(m)
```

    ## [1] "Paco" "Pepe" "Kiko"
