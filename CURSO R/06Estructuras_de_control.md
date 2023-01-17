# Caso práctico 1

## Ejercicio 1

Indicar si es un número par o impar.

``` r
x <- 5
if (x %% 2 == 0) {
  print("x es par")
} else {
  print("x es impar")
}
```

    ## [1] "x es impar"

## Ejercicio 2

Dados los vectores: v= (12, -3, 5 ,18.7) y w= (12, 0.25, 77, exp(2))

-   Obtener la suma de los dos vectores mediante bucles y comprobarlo
    empleando v+w.
-   Obtener la suma de las componentes del vector v y almacenarlos en C.

``` r
v <- c(12, -3, 5, 18.7)
w <- c(12, 0.25, 77, exp(2))

s = 0
n <- length(v)
for (i in 1:n) {
  s[i] <- v[i]+w[i]
}

s
```

    ## [1] 24.00000 -2.75000 82.00000 26.08906

``` r
v+w
```

    ## [1] 24.00000 -2.75000 82.00000 26.08906

``` r
c <- 0
n <- length(v)
for(i in 1:n){
  c <- c+v[i]
  }

c
```

    ## [1] 32.7

# Caso práctico 2

## Ejercicio 1

Determinar el signo de un número: positivo, negativo o nulo

``` r
x<-5 
if (x>0) {
  "es positivo"
} else if (x<0) {
  "es negativo"
} else {
  "es cero"
}
```

    ## [1] "es positivo"

## Ejercicio 2

Generar una secuencia de números del 1 al 10. Cuando llegue al 4, se
debe romper la secuencia con un break. Mientras no sea así, pintar los
valores por pantalla.

``` r
for (y in 1:10) {
  if(y==4){
    break
  } else {
    print(y)
  }
}
```

    ## [1] 1
    ## [1] 2
    ## [1] 3
