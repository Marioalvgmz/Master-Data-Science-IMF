# Caso práctico 1

## Ejercicio 1

Ejecuta en orden las siguientes operaciones y explicar qué mostrará cada
una de ellas si se ejecutan una detrás de otra.

-   sqrt(-17)
-   sqrt(-17+0i)
-   x\<-5/0
-   exp(-x)
-   exp(x)-exp(x)

``` r
sqrt(-17) 
```

    ## Warning in sqrt(-17): Se han producido NaNs

    ## [1] NaN

``` r
sqrt(-17+0i) 
```

    ## [1] 0+4.123106i

``` r
x<-5/0 
exp(-x) 
```

    ## [1] 0

``` r
exp(x)-exp(x) 
```

    ## [1] NaN

## Ejercicio 2

Si se realizan las siguientes asignaciones, ¿cuál sería su salida?

x \<- 5

y \<- 2

-   x \> y
-   x == y
-   x != y

``` r
x <- 5
y <- 2

x > y
```

    ## [1] TRUE

``` r
x == y
```

    ## [1] FALSE

``` r
x != y
```

    ## [1] TRUE

\# Caso práctico 2 \## Ejercicio 1 Usar R como calculadora:

-   1+1+2+3+5+8
-   8-13
-   13\*21
-   34\*34
-   55/34 \* sqrt (89)

``` r
1+1+2+3+5+8
```

    ## [1] 20

``` r
8-13
```

    ## [1] -5

``` r
13*21
```

    ## [1] 273

``` r
34*34
```

    ## [1] 1156

``` r
55/34 * sqrt (89)
```

    ## [1] 15.26085

## Ejercicio 2

Explicar en qué orden se ejecutan las dos expresiones siguientes:

-   2 \* 5 + 1
-   2 \* (5 + 1)

``` r
2 * 5 + 1 #Multiplicación anres que suma
```

    ## [1] 11

``` r
2 * (5 + 1) #Paréntesis antes que multiplicación
```

    ## [1] 12
