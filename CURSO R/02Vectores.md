# Caso practico 1

## Ejercicio 1

Crear un vector que tenga 7 veces repetido el número 11,también
crearemos un vector que generar números del 1 al 15 saltando cifras de 2
en 2

Unir los dos vectores en un llamado result=
(1,3,5,7,9,11,13,15,11,11,11,11,11,11), se debe obtener el valor del
vector en la posición 5 y crear un vector p de la posición de 5 al 10.

``` r
v1 <- rep(11,7)
v2 <- seq(1,15,by=2)
result<- c(v2,v1)
result[5]
```

    ## [1] 9

``` r
p<-result[5:10]
```

## Ejercicio 2

-   Generar un vector de 12 elementos llamado “meses”, para que se
    asigne numéricamente del 1 al 12 los doce meses del año
-   Visualizar el vector: \[1\] 1 2 3 4 5 6 7 8 9 10 11 12
-   Relacionar los números anteriores con los meses en letras.
-   Si está bien hecho el paso anterior y se visualiza “meses”:

Ene Feb Mar Abr May Jun Jul Ago Sep Oct Nov Dic

1 2 3 4 5 6 7 8 9 10 11 12

``` r
meses <- c(1:12)
names(meses) <- month.abb
meses
```

    ## Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec 
    ##   1   2   3   4   5   6   7   8   9  10  11  12

# Caso practico 1

## Ejercicio 1

Crear un vector formado por números del 1 al 10 y comprobar que devuelve
las siguientes extracciones de datos.

-   x\[3\];
-   x\[-3\];
-   x\[c(1,5,7)\]

``` r
x<-c(1:10)
x
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

``` r
x[3]
```

    ## [1] 3

``` r
x[-3]
```

    ## [1]  1  2  4  5  6  7  8  9 10

``` r
x[c(1,5,7)]
```

    ## [1] 1 5 7

## Ejercicio 2

Evaluar las siguientes generaciones de valores.

-   seq (1,6)
-   seq (1,6, by=0.5)
-   seq (1,6, length=10)
-   rep (1,5)
-   rep (c (1,2),5)
-   rep (1:4,2)

``` r
seq(1,6)
```

    ## [1] 1 2 3 4 5 6

``` r
seq(1,6, by=0.5)
```

    ##  [1] 1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0 5.5 6.0

``` r
seq(1,6, length=10)
```

    ##  [1] 1.000000 1.555556 2.111111 2.666667 3.222222 3.777778 4.333333 4.888889
    ##  [9] 5.444444 6.000000

``` r
rep(1,5)
```

    ## [1] 1 1 1 1 1

``` r
rep(c(1,2),5)
```

    ##  [1] 1 2 1 2 1 2 1 2 1 2

``` r
rep(1:4,2)
```

    ## [1] 1 2 3 4 1 2 3 4

## Ejercicio 3

Crear un vector utilizando la función seq para que genere el vector que
se muestra a continuación.

-   vector v= (1, 3, 5, 7, 9, 11, 13, 15).

``` r
v<-seq(1,15, by=2)
v
```

    ## [1]  1  3  5  7  9 11 13 15

## Ejercicio 4

Combinar el vector del ejercicio 3 y el vector que repita 7 veces el
valor numérico 11.

-   Resultado: m= (1,3,5,7,9,11,13,15,11,11,11,11,11,11,11).

``` r
m=c(v,v1)
m
```

    ##  [1]  1  3  5  7  9 11 13 15 11 11 11 11 11 11 11
