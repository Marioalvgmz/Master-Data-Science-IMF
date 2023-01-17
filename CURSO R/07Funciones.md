# Caso práctico 1

## Ejercicio 1

Crear una función llamada fcondición y realizar la siguiente
comprobación: si x es menor a 5 toma el valor 0 y en caso contrario el
valor 10.

``` r
fcondicion <- function(x){
  if (x < 5) {
    0
  } else {
    10
  }
}

fcondicion(3)
```

    ## [1] 0

``` r
fcondicion(7)
```

    ## [1] 10

## Ejercicio 2

-   Crear una función que pasándole un valor diga si es negativo à
    devuelve un 0.
-   Si es menor o igual a 10 à devuelve el valor dividido entre 10.
-   En cualquier otro caso devuelve un 1.

``` r
f<-function (x) {
  if (x<0) {
    0
  } else {
      if (x<=10){
        x/10
      }
      else {
        1
      }
  }
}

f(-3)
```

    ## [1] 0

``` r
f(4)
```

    ## [1] 0.4

``` r
f(12)
```

    ## [1] 1

# Caso práctico 2

## Ejercicio 1

Calcular la media entre dos números pasados a una función.

``` r
media<-function (x,y) {
  return((x+y)/2)
}

media(4,5)
```

    ## [1] 4.5

``` r
# Valores indefinidos
media2<-function(...) {
  contador<-0
  valores<-c(...)
  for (i in valores){
    contador<-contador+i
  }
 contador/length(valores) 
}

media2(1:6)
```

    ## [1] 3.5

## Ejercicio 2

Crear una función que calcule el valor absoluto de un parámetro pasado
por argumento.

``` r
absoluto<-function(x){
  if (x<0) {
    x*-1
  } else{
    x
  }
}

absoluto(-2)
```

    ## [1] 2

``` r
absoluto(5)
```

    ## [1] 5

``` r
absoluto2<-function(x) {
  abs(x)
}

absoluto2(-3)
```

    ## [1] 3

``` r
absoluto2(6)
```

    ## [1] 6
