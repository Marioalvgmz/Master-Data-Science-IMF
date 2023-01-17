# Caso practico 1

## Ejercicio 1

Crear una lista formada por los vectores.

-   Edad: generar un vector con las edades aleatorias empezando por 10
    hasta 40. Usar la función rnorm.
-   Seguridad social: crear un vector que genere T o F por si tiene
    número o no. Para ello, repetir la secuencia de F, T 5 veces.

Mostrar la lista resultante.

``` r
edad <- round(rnorm(10,40,10))
edad
```

    ##  [1] 33 38 48 44 53 28 27 33 39 21

``` r
SS <- rep(c(F,T),5)
SS
```

    ##  [1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE

``` r
Lista <- list(Edad=edad, SeguroSocial=SS)
Lista
```

    ## $Edad
    ##  [1] 33 38 48 44 53 28 27 33 39 21
    ## 
    ## $SeguroSocial
    ##  [1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE

## Ejercicio 2

Indicar qué devuelve cada lista de las que tienes a continuación:

``` r
Otra<-list(Numeros=1:20,Letras=letters[1:15])
Otra
```

    ## $Numeros
    ##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
    ## 
    ## $Letras
    ##  [1] "a" "b" "c" "d" "e" "f" "g" "h" "i" "j" "k" "l" "m" "n" "o"

# Caso practico 2

## Ejercicio 1

Crear una lista llamada familia con los siguientes campos:

-   Padre=“juan”,

-   Madre=“maría”,

-   NumerodeHijos=3,

-   Nombrehijos=“Luis”,“Carlos”,“Eva”

-   Edades=7, 5,3

-   Ciudad=“Madrid”

1.  Mostrar la lista que se ha creado.

2.  Mostrar el nombre del padre usando $.

3.  Mostrar el nombre de la madre \[\[\]\].

4.  Mostrar la cantidad de hijos que hay en la lista.

``` r
familia = list(Padre="juan", Madre="maría", NumerodeHijos=3, Nombrehijos=c("Luis","Carlos","Eva"), Edades=c(7,5,3), Ciudad ="Madrid")
familia
```

    ## $Padre
    ## [1] "juan"
    ## 
    ## $Madre
    ## [1] "maría"
    ## 
    ## $NumerodeHijos
    ## [1] 3
    ## 
    ## $Nombrehijos
    ## [1] "Luis"   "Carlos" "Eva"   
    ## 
    ## $Edades
    ## [1] 7 5 3
    ## 
    ## $Ciudad
    ## [1] "Madrid"

``` r
familia$Padre
```

    ## [1] "juan"

``` r
familia[[2]]
```

    ## [1] "maría"

``` r
familia[[3]]
```

    ## [1] 3

``` r
familia[[4]][1] # Acceder dentro del vector
```

    ## [1] "Luis"

## Ejercicio 2

Crear una lista llamada familia2 con los siguientes campos:

-   Hombre = “Pedro”,

-   Mujer = “María”,

-   Casados = TRUE,

-   Numero. Hijos = 4,

-   Edad. Hijos = 4, 7, 9, 2

-   Nombre. Hijos=‘Hugo’, ‘Paco’, ‘Luis’, ‘Mary’

1.  Mostrar la lista que se ha creado.

2.  Mostrar el nombre del hombre y la mujer.

3.  Mostrar la edad de los hijos.

4.  Mostrar el nombre de los hijos.

``` r
familia2 <- list(Hombre="Pedro", Mujer="María", Casados=T, numh=4, edadh=c(4,7,9,2), nomh=c("Hugo","Paco","Luis","Mary"))
familia2
```

    ## $Hombre
    ## [1] "Pedro"
    ## 
    ## $Mujer
    ## [1] "María"
    ## 
    ## $Casados
    ## [1] TRUE
    ## 
    ## $numh
    ## [1] 4
    ## 
    ## $edadh
    ## [1] 4 7 9 2
    ## 
    ## $nomh
    ## [1] "Hugo" "Paco" "Luis" "Mary"

``` r
familia2[1:2]
```

    ## $Hombre
    ## [1] "Pedro"
    ## 
    ## $Mujer
    ## [1] "María"

``` r
familia2$edadh
```

    ## [1] 4 7 9 2

``` r
familia2[[6]]
```

    ## [1] "Hugo" "Paco" "Luis" "Mary"
