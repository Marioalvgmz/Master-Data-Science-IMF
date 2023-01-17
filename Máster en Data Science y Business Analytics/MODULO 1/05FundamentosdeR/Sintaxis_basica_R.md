En el presente notebook se introducirá al alumno a la sintáxis de R,
antes de comenzar su andadura a través de las principales estructuras de
datos, el contenido del siguiente notebook se estructurará a través de
los siguientes apartados:

-   **Objetos**
-   **Comentarios**
-   **Operadores**
-   **Tipos de variables**

## Objetos

Cualquier variable, función, parámetro, etc. que se declare en R se
denomina **objeto**

Para crear un objeto en R a diferencia de otros lenguajes de
programación, no se utiliza el operador de asignación **=**, si no que
utilizamos la asignación de forma direccional, es decir, con los
siguientes elementos:

-   `<-`
-   `->`

Los objetos son mutables, es decir, podemos cambiar su valor en
cualquier momento, realizando una nueva asignación. Todos los objetos de
R, se almacenan en memoria RAM, hasta que cerramos el programa o,
limpiamos el entorno de variables. Mediante el comando **`ls`** podemos
ver todos los objetos que tenemos almacenados en memoria.

``` r
ls()
```

    ## character(0)

En algunas ocasiones, nos encontraremos con que hemos almacenado objetos
demasiado grandes en memoria, que una vez realizada uan operación,
deseamos elimnar, para ello, disponemos de la función **`rm`**, a la
cuál, pasaremos como parámetro el nombre de la variable a eliminar.

``` r
rm(a)
```

    ## Warning in rm(a): objeto 'a' no encontrado

``` r
print(ls())
```

    ## character(0)

No obstante, para ahorranos ciertos pasos como carga y creación de
archivos y objetos, si lo deseamos, podremos guardar además del notebook
o script, todo el entorno de variables y objetos, simplemente al
guardarlo, le asignaremos un nombre y, se guardará con extensión .Rdata,
cuando abramos la sesión, se restaurarán todos los objetos que teníamos
almacenados.

## Comentarios

En R podemos utilizar dos tipos de comentario:

-   De una línea, simplemente utilizaremos el operador **`#`** y
    agregaremos el comentario
-   Multi-línea, para ello abriremos el comentario con comillas dobles
    **`"`**y, hasta que no volvamos a incluir comillas dobles, no se
    cerrará el comentario.

``` r
# Comentario de una línea

# Otra línea
```

``` r
"
Comentario
de
varias
líneas
"
```

    ## [1] "\nComentario\nde\nvarias\nlíneas\n"

Para facilitarnos el trabajo, en R, se pueden comentar varias líneas a
la vez, para ello realizaremos:

-   Selección de las líneas
-   Sobre las línesa seleccionadas: CNTRL + SHIFT + C

## Operadores

En R existen operadores de diferentes tipos:

-   **Aritméticos**
-   **Comparaicón**
-   **Lógicos**

Definimos algunas variables para mostrar los operadores

``` r
a <- 7
b <- 2
```

Operadores aritméticos

``` r
# Suma
a + b
```

    ## [1] 9

``` r
# Resta
a - b
```

    ## [1] 5

``` r
# Multiplicación
a * b
```

    ## [1] 14

``` r
# División
a / b
```

    ## [1] 3.5

``` r
# Exponencial
a ^ b
```

    ## [1] 49

``` r
# Módulo o resto de una división
a %% b
```

    ## [1] 1

``` r
# División entera
a %/% b
```

    ## [1] 3

Operadores de comparación

``` r
# Menor que 
a < b
```

    ## [1] FALSE

``` r
# Mayor que
a > b
```

    ## [1] TRUE

``` r
# Menos o igual que
a <= b
```

    ## [1] FALSE

``` r
# Mayor o igual que
a >=b
```

    ## [1] TRUE

``` r
# Igualdad
a == b
```

    ## [1] FALSE

``` r
# No es igual que
a != b
```

    ## [1] TRUE

Operadores lógicos

``` r
# Negación
!(TRUE) # Equivalente con T
```

    ## [1] FALSE

``` r
# AND Lógico
TRUE & TRUE
```

    ## [1] TRUE

``` r
TRUE & FALSE
```

    ## [1] FALSE

``` r
# OR Lógico
TRUE | FALSE
```

    ## [1] TRUE

``` r
FALSE | FALSE
```

    ## [1] FALSE

## Tipos de variables

En R, vamos a poder distinguir tres tipos de variables, esto es
independiente del tipo de estructura que utilicemos para su
almacenamiento y procesamiento:

-   Numéricas
-   Carácter
-   Booleanas
-   Factor

Para determinar el tipo de una variable, utilizaremos la función
**`class`**

``` r
class(5)
```

    ## [1] "numeric"

``` r
class(3.9)
```

    ## [1] "numeric"

``` r
class("Hola")
```

    ## [1] "character"

``` r
class(TRUE)
```

    ## [1] "logical"

``` r
class(T)
```

    ## [1] "logical"

``` r
# Por el momento, no prestaremos mucha atención sobre la construcción
#  de tipos factor, esto se explicará en detalle en próximas unidades
class(as.factor('A'))
```

    ## [1] "factor"
