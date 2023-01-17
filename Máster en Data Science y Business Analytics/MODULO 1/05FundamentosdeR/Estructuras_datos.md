Dentro de R, existen diferentes tipos de estructuras de datos con las
que podemos trabajar, dentro de esta sección, explicaremos en qué
consisten y mostraremos algunas de sus principales funciones:

-   **Vectores**
-   **Arrays**
-   **Listas**
-   **Factores**
-   **Matrices**
-   **Dataframes**

## Vectores

En R, un **vector** es una sucesión de elementos de una dimensión. Un
vector puede soportar diferentes tipos de variables. Para su
construcción, se utiliza la función **`c`**.

``` r
a <- c(1, 3.0, 7, 'hola')

a
```

    ## [1] "1"    "3"    "7"    "hola"

Podemos indexar un vector accediendo a sus posiciones.

``` r
# Primera posición
a[1]
```

    ## [1] "1"

``` r
# Posición n
a[4]
```

    ## [1] "hola"

``` r
# Rango de posiciones
a[2:4]
```

    ## [1] "3"    "7"    "hola"

``` r
# Excluir elementos
a[-2] # Sin la posición 2
```

    ## [1] "1"    "7"    "hola"

``` r
# A través de máscara booleana o vector lógico
a[c(T, F, F, T)]
```

    ## [1] "1"    "hola"

Es **muy** importante resaltar que en los vectores cuando aplicamos una
operación, la aplicamos a todos los elementos del vector, a no ser que
especifiquemos lo contrario.

Para que podamos aplicar operaciones sobre un vector, todos sus
elementos deben ser del mismo tipo, es decir, sobre nuestro vector
actual no podríamos operar.

``` r
# a+4
# Error in a + 4 : non-numeric argument to binary operator
```

``` r
# Asignación de un nuevo vector
b <- c(1, 30, 4, 56, 9)

# Suma a todos los elementos de 4
b + 4
```

    ## [1]  5 34  8 60 13

``` r
# Resta a todos los elementos de 3
b - 3
```

    ## [1] -2 27  1 53  6

``` r
# Todos los elementos al cuadrado
b ^ 2
```

    ## [1]    1  900   16 3136   81

Si tenemos más de un vector del mismo tipo y longitud, podemos aplicar
operaciones sobre ellos.

``` r
# Resta de vectores
c <- c(3, 50, 4, 3, 0)

b - c
```

    ## [1]  -2 -20   0  53   9

``` r
# Producto de vectores, elemento a elemento
c * b
```

    ## [1]    3 1500   16  168    0

Existen algunas funciones que son propias de los vectores, este caso,
nos permiten realizar aritmética vectorial:

-   **length**. Longitud de un vector

``` r
length(b)
```

    ## [1] 5

``` r
length(a)
```

    ## [1] 4

``` r
length(c)
```

    ## [1] 5

-   **sum**. Realiza la suma de todos los elementos del vector

``` r
sum(b)
```

    ## [1] 100

-   **prod**. Realiza el producto de todos los elementos del vector.

``` r
prod(b)
```

    ## [1] 60480

-   **min**. Devuelve el elemento mínimo de un vector.

``` r
min(b)
```

    ## [1] 1

-   **max**. Devuelve el elemento máximo de un vector.

``` r
max(b)
```

    ## [1] 56

-   **range**. Devuelve el rango del vector, es decir, de su elemento
    mínimo a máximo

``` r
range(b)
```

    ## [1]  1 56

-   **mean**. Devuelve la media del vector.

``` r
mean(b)
```

    ## [1] 20

-   **var**. Devuelve la varianza del vector.

``` r
var(b)
```

    ## [1] 533.5

-   **sd**. Devuelve la desviación estándar del vector.

``` r
sd(b)
```

    ## [1] 23.09762

-   **cumsum**. Devuelve la suma acumulada elemento a elemento del
    vector

``` r
cumsum(b)
```

    ## [1]   1  31  35  91 100

-   **cumprod**. Devuelve el producto acumulado del vector elemento a
    elemento.

``` r
cumprod(b)
```

    ## [1]     1    30   120  6720 60480

-   **sqrt**. Raíz de todos los elementos del vector

``` r
sqrt(b)
```

    ## [1] 1.000000 5.477226 2.000000 7.483315 3.000000

A través de vectores, podemos crear sucesiones, en algunas ocasiones
partiendo de un vector de entrada o, creándolo de cero:

-   Generar un vector a partir de un rango definido de n a m. A través
    del operador **:**

``` r
1:20
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20

``` r
4:8
```

    ## [1] 4 5 6 7 8

-   Generar secuencias a través de la función **seq**, esta función toma
    como parámetros, origen de la secuencia, máximo de la secuencia,
    elemento de división.

``` r
seq(-10, 20, 2)  # -10 a 20 de dos en dos
```

    ##  [1] -10  -8  -6  -4  -2   0   2   4   6   8  10  12  14  16  18  20

``` r
seq(0, 1, 0.1)
```

    ##  [1] 0.0 0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9 1.0

-   A través de la función **rep**. Podemos generar vectores de números
    repetidos, esta función toma como parámetros el número a repetir (o
    elemento) y el número de veces.

``` r
# Un número 
rep(2, 200)
```

    ##   [1] 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
    ##  [38] 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
    ##  [75] 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
    ## [112] 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
    ## [149] 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
    ## [186] 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2

``` r
rep(0.5, 10)
```

    ##  [1] 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5

``` r
# Secuencias de números
rep(1:10, 3)
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10  1  2  3  4  5  6  7  8  9 10  1  2  3  4  5
    ## [26]  6  7  8  9 10

-   Mediante la función **sample**, que toma como parámetros el rango de
    valores, el número de elementos y si los valores se generaran con
    reemplazamiento o no.

``` r
no.rep <- sample(1:10, 10, replace = F)
si.rep <- sample(30:45, 10, replace = T)

no.rep
```

    ##  [1] 10  7  1  2  5  9  4  3  8  6

``` r
si.rep
```

    ##  [1] 45 41 41 40 31 33 40 36 36 38

Otra forma de seleccionar sub-vectores dentro de un vector ya existente
es a través de operaciones de comparación (expresiones booleanas), vemos
algunos ejemplos.

``` r
# Creamos un vector nuevo
z <- rep(1:20, 3)

# Vamos a asignar a todos los elementos del vector que sean menores de 7 el valor 1

z[z < 7] <- 1
z
```

    ##  [1]  1  1  1  1  1  1  7  8  9 10 11 12 13 14 15 16 17 18 19 20  1  1  1  1  1
    ## [26]  1  7  8  9 10 11 12 13 14 15 16 17 18 19 20  1  1  1  1  1  1  7  8  9 10
    ## [51] 11 12 13 14 15 16 17 18 19 20

``` r
# Seleccionar todos los elementos del array que son diferentes de 19
z[z != 19]
```

    ##  [1]  1  1  1  1  1  1  7  8  9 10 11 12 13 14 15 16 17 18 20  1  1  1  1  1  1
    ## [26]  7  8  9 10 11 12 13 14 15 16 17 18 20  1  1  1  1  1  1  7  8  9 10 11 12
    ## [51] 13 14 15 16 17 18 20

Finalmente, mostraremos cómo ordenar un vector a través de la función
**sort**.

``` r
# Generamos vector
no.rep.dos <- sample(30:60, 10, replace = F)

# Mostramos el vector ordenado
sort(no.rep.dos, decreasing = T)
```

    ##  [1] 59 58 54 53 50 48 47 44 42 40

## Arrays

A diferencia de los vectores, en un **array**, todos sus elementos deben
ser del mismo tipo, también son indexables. Para crear un array, haremos
uso de la función **`array`**.

``` r
# Definimos un nuevo array
my.arr <- array(data = c(1,2,3,4), dim = c(2,2))

my.arr
```

    ##      [,1] [,2]
    ## [1,]    1    3
    ## [2,]    2    4

Podemos ver la dimensión de un array a través de la función **`dim`**

``` r
dim(my.arr) # Dos dimensiones de dos elementos
```

    ## [1] 2 2

También es posible crear un array a través de un vector ya existente:

``` r
no.rep.dos
```

    ##  [1] 47 40 44 59 54 50 42 58 53 48

``` r
length(no.rep.dos) # Divisible entre 2 y 5
```

    ## [1] 10

``` r
dim(no.rep.dos) <- c(5,2)
```

``` r
no.rep.dos # Vector transformado en array
```

    ##      [,1] [,2]
    ## [1,]   47   50
    ## [2,]   40   42
    ## [3,]   44   58
    ## [4,]   59   53
    ## [5,]   54   48

A continuación, mostraremos diferentes maneras de seleccionar elementos
de un array.

``` r
new.arr <- array(1:40, c(5, 4, 2))

new.arr
```

    ## , , 1
    ## 
    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    6   11   16
    ## [2,]    2    7   12   17
    ## [3,]    3    8   13   18
    ## [4,]    4    9   14   19
    ## [5,]    5   10   15   20
    ## 
    ## , , 2
    ## 
    ##      [,1] [,2] [,3] [,4]
    ## [1,]   21   26   31   36
    ## [2,]   22   27   32   37
    ## [3,]   23   28   33   38
    ## [4,]   24   29   34   39
    ## [5,]   25   30   35   40

``` r
print(dim(new.arr))
```

    ## [1] 5 4 2

``` r
# Sólo primera dimensión.
new.arr[,,1]
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    6   11   16
    ## [2,]    2    7   12   17
    ## [3,]    3    8   13   18
    ## [4,]    4    9   14   19
    ## [5,]    5   10   15   20

``` r
# Columna 2 de las dos dimensiones
new.arr[,2,1:2]
```

    ##      [,1] [,2]
    ## [1,]    6   26
    ## [2,]    7   27
    ## [3,]    8   28
    ## [4,]    9   29
    ## [5,]   10   30

``` r
# Fila 4 de la segunda dimensión.
new.arr[4, ,2]
```

    ## [1] 24 29 34 39

``` r
# Elementos en tercera y cuarta posición de la quinta fila, de ambas dimensiones
new.arr[5,c(3,4) , ]
```

    ##      [,1] [,2]
    ## [1,]   15   35
    ## [2,]   20   40

``` r
# Todas las filas de la segunda columna en adelante de la primera dimensión
new.arr[ , 2:length(new.arr[1,,1]), 1]
```

    ##      [,1] [,2] [,3]
    ## [1,]    6   11   16
    ## [2,]    7   12   17
    ## [3,]    8   13   18
    ## [4,]    9   14   19
    ## [5,]   10   15   20

Análogamente, también es posible indexar un array a través de otro
array.

``` r
index <- array(c(2, 1:3, 1:2), c(2,3))

index
```

    ##      [,1] [,2] [,3]
    ## [1,]    2    2    1
    ## [2,]    1    3    2

``` r
new.arr[index]
```

    ## [1]  7 31

Del mismo modo que los vectores, sobre los arrays también podemos
aplicar operaciones aritméticas, como las descritas anteriormente,
mostramos algunos ejemplos:

``` r
# Suma
sum(new.arr)
```

    ## [1] 820

``` r
# Media
mean(new.arr)
```

    ## [1] 20.5

``` r
# Rango
range(new.arr)
```

    ## [1]  1 40

``` r
# Máximo
max(new.arr)
```

    ## [1] 40

``` r
# ...
```

Evidentemente, estas operaciones también funcionan a nivel de dimensión,
fila, columna de los arrays

``` r
sum(new.arr[2, , 1]) #Suma de los elementos de la segunda fila de la primera dimensión.
```

    ## [1] 38

No obstante, existen operaciones especiales para los arrays que
funcionan a nivel de eje (fila x columna), que son las que se muestran a
continuación:

``` r
# Suma de columnas 
colSums(new.arr, dims = 1) # Suma de todas las columnas por fila
```

    ##      [,1] [,2]
    ## [1,]   15  115
    ## [2,]   40  140
    ## [3,]   65  165
    ## [4,]   90  190

``` r
colSums(new.arr, dims = 2) # Suma de todas las columnas por columna
```

    ## [1] 210 610

``` r
# Suma de filas
rowSums(new.arr, dims = 1) # Suma de todas las filas por fila
```

    ## [1] 148 156 164 172 180

``` r
rowSums(new.arr, dims = 2) # Suma de todas las filas por columna
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]   22   32   42   52
    ## [2,]   24   34   44   54
    ## [3,]   26   36   46   56
    ## [4,]   28   38   48   58
    ## [5,]   30   40   50   60

``` r
# Media de columnas
colMeans(new.arr, dims = 1) # Media de columnas por columna
```

    ##      [,1] [,2]
    ## [1,]    3   23
    ## [2,]    8   28
    ## [3,]   13   33
    ## [4,]   18   38

``` r
colMeans(new.arr, dims = 2) # Media de columnas por dimensión
```

    ## [1] 10.5 30.5

``` r
rowMeans(new.arr, dims = 1) # Media de filas por fila
```

    ## [1] 18.5 19.5 20.5 21.5 22.5

``` r
rowMeans(new.arr, dims = 2) # Media de filas por dimensión
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]   11   16   21   26
    ## [2,]   12   17   22   27
    ## [3,]   13   18   23   28
    ## [4,]   14   19   24   29
    ## [5,]   15   20   25   30

Si se quieren permutar las dimensiones de un array, se puede hacer uso
de la función **`aperm`**

``` r
aperm(new.arr)
```

    ## , , 1
    ## 
    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    6   11   16
    ## [2,]   21   26   31   36
    ## 
    ## , , 2
    ## 
    ##      [,1] [,2] [,3] [,4]
    ## [1,]    2    7   12   17
    ## [2,]   22   27   32   37
    ## 
    ## , , 3
    ## 
    ##      [,1] [,2] [,3] [,4]
    ## [1,]    3    8   13   18
    ## [2,]   23   28   33   38
    ## 
    ## , , 4
    ## 
    ##      [,1] [,2] [,3] [,4]
    ## [1,]    4    9   14   19
    ## [2,]   24   29   34   39
    ## 
    ## , , 5
    ## 
    ##      [,1] [,2] [,3] [,4]
    ## [1,]    5   10   15   20
    ## [2,]   25   30   35   40

Los arrays, también tienen una clase única.

``` r
class(new.arr)
```

    ## [1] "array"

## Listas

Con cierta similaridad a un vector, una **lista**, es una colección de
objectos, indexable a través del operador **`[[ ]]`** (doble corchete).
Soporta desde el mismo tipo de dato a, diferentes tipos de datos, la
declaración de una lista se realiza desde la función **`list`**.

``` r
my.list <- list(c(1:40))
my.list
```

    ## [[1]]
    ##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
    ## [26] 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40

``` r
my.list[1] # Solamente tiene un elemento la lista, que es un vector
```

    ## [[1]]
    ##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
    ## [26] 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40

``` r
my.list[[1]][5] # Accedemos al primer elemento de la lista, posición 5 del vector.
```

    ## [1] 5

Algo que es siempre aconsejable para poder identificar los diferentes
campos o elementos de una lista, es utilizar nombres.

``` r
new.list <- list(alumnos=c("Juan", "María", "Alfredo"),
                calificaciones=c(7, 4,5, 9))
```

Podemos acceder a sus elementos además de con doble corchetes con un
operador especial de R y, que veremos muy comúnmente en dataframes, el
operador **`$`**

``` r
new.list$alumnos
```

    ## [1] "Juan"    "María"   "Alfredo"

``` r
new.list[["alumnos"]]
```

    ## [1] "Juan"    "María"   "Alfredo"

Si un elemento no existe en un componente de la lista, simplemente se
agrega.

``` r
new.list$alumnos <- c(new.list$alumnos, "Nuevo alumno")
new.list$alumnos
```

    ## [1] "Juan"         "María"        "Alfredo"      "Nuevo alumno"

``` r
new.list$edad <- c(15, 16, 17, 15)

new.list
```

    ## $alumnos
    ## [1] "Juan"         "María"        "Alfredo"      "Nuevo alumno"
    ## 
    ## $calificaciones
    ## [1] 7 4 5 9
    ## 
    ## $edad
    ## [1] 15 16 17 15

Las listas tienen su clase propia

``` r
class(new.list)
```

    ## [1] "list"

## Factores

Los factores son vectores especiales, que se utilizan únicamente, para
la representación de variables **categóricas**, los variables
categóricas son las que indican una cualidad o característica, como por
ejemplo: Alto, Bajo, Medio, etc.

Para crear una una variable categórica, tenemos que pasar un vector de
caracteres a la función **`factor`**

``` r
var.cat <- factor(c("ENERO", "FEBRERO", "MARZO", "ABRIL"))
var.cat
```

    ## [1] ENERO   FEBRERO MARZO   ABRIL  
    ## Levels: ABRIL ENERO FEBRERO MARZO

Una variable categórica, se caracteriza porque cada categoría en R, se
denomina como nivel *level*, podemos acceder a sus niveles a través de
la función **`levels`**

``` r
levels(var.cat)
```

    ## [1] "ABRIL"   "ENERO"   "FEBRERO" "MARZO"

Este tipo de vectores especiales, tienen su propia clase.

``` r
class(var.cat)
```

    ## [1] "factor"

Para eliminar un nivel de una variable categórica, se hará uso de la
función **`droplevels`** que recibirá como parámetro la variable
categórica y la categoría a eliminar

``` r
var.cat = droplevels(x = var.cat, "MARZO")

var.cat
```

    ## [1] ENERO   FEBRERO <NA>    ABRIL  
    ## Levels: ABRIL ENERO FEBRERO

## Matrices

Previamente, hemos tratado con arrays multi-dimensionales, una matriz no
es ni más ni menos que un array de dos dimensiones. No obstante, las
matrices tienen algunos tipos de funciones especiales con las que
podemos trabajar, se describirán posteriormente.

Para crear una matriz se utiliza la función **`matrix`**, que recibe los
datos de la propia matriz y, los parámetros **nrow** y **ncol**,
adicionalmente, podremos especificar cómo queremos que se rellene la
matriz a partir de los datos, por filas sí o no con el parámetro
**byrow**

``` r
# Creamos una matriz.
my.mat <- matrix(1:30, ncol = 6, nrow = 5, byrow = F) # Probar byrow TRUE
my.mat
```

    ##      [,1] [,2] [,3] [,4] [,5] [,6]
    ## [1,]    1    6   11   16   21   26
    ## [2,]    2    7   12   17   22   27
    ## [3,]    3    8   13   18   23   28
    ## [4,]    4    9   14   19   24   29
    ## [5,]    5   10   15   20   25   30

Además de todas las funciones ya vistas que pueden realizarse en arrays
y las formas disponibles de indexación, en matrices nos encontramos con
las siguientes funciones propias:

-   **`ncol`**: Devuelve el número de columnas.

``` r
# Número de columnas
ncol(my.mat)
```

    ## [1] 6

-   **`nrow`**: Devuelve el número de filas.

``` r
# Número de filas
nrow(my.mat)
```

    ## [1] 5

-   **`diag`**: Devuelve la diagonal de la matriz.

``` r
# Diagonal
diag(my.mat)
```

    ## [1]  1  7 13 19 25

-   **`crossprod`**: Realiza el producto entre dos matrices.

``` r
crossprod(x = my.mat, y = my.mat)
```

    ##      [,1] [,2] [,3] [,4] [,5] [,6]
    ## [1,]   55  130  205  280  355  430
    ## [2,]  130  330  530  730  930 1130
    ## [3,]  205  530  855 1180 1505 1830
    ## [4,]  280  730 1180 1630 2080 2530
    ## [5,]  355  930 1505 2080 2655 3230
    ## [6,]  430 1130 1830 2530 3230 3930

-   **`t`**: Devuelve la traspuesta de una matriz.

``` r
# Traspuesta
t(my.mat)
```

    ##      [,1] [,2] [,3] [,4] [,5]
    ## [1,]    1    2    3    4    5
    ## [2,]    6    7    8    9   10
    ## [3,]   11   12   13   14   15
    ## [4,]   16   17   18   19   20
    ## [5,]   21   22   23   24   25
    ## [6,]   26   27   28   29   30

-   **`svd`**: Valores singulares de una matriz.

``` r
# Valores singulares
svd(my.mat)
```

    ## $d
    ## [1] 9.716531e+01 3.728537e+00 2.538160e-15 1.947191e-15 6.089851e-16
    ## 
    ## $u
    ##            [,1]        [,2]        [,3]       [,4]       [,5]
    ## [1,] -0.4018926 -0.66217998  0.48765261  0.2233859 -0.3351025
    ## [2,] -0.4240057 -0.34672632 -0.80457360 -0.2008214 -0.1110499
    ## [3,] -0.4461188 -0.03127266  0.07019089  0.2397858  0.8588224
    ## [4,] -0.4682320  0.28418100  0.32272856 -0.7706509 -0.0440853
    ## [5,] -0.4903451  0.59963465 -0.07599847  0.5083006 -0.3685848
    ## 
    ## $v
    ##            [,1]       [,2]        [,3]        [,4]       [,5]
    ## [1,] -0.0711459  0.7202415 -0.55959544 -0.09385682  0.1469272
    ## [2,] -0.1859294  0.5105569  0.24248261  0.08217043  0.2585642
    ## [3,] -0.3007128  0.3008724  0.22067008  0.22952872 -0.8429267
    ## [4,] -0.4154963  0.0911878  0.54034856 -0.61659563  0.1878316
    ## [5,] -0.5302798 -0.1184968  0.08533938  0.68520749  0.3842241
    ## [6,] -0.6450632 -0.3281813 -0.52924519 -0.28645419 -0.1346204

-   **`eigen`**: Realiza el cálculo de autovalores y autovectores (La
    matriz tiene que ser regular).

``` r
# IMPORTANTE: Necesita una matriz regular
regular.mat <- matrix(1:9, ncol = 3, nrow = 3, byrow = F)

eigen(regular.mat)
```

    ## eigen() decomposition
    ## $values
    ## [1]  1.611684e+01 -1.116844e+00 -5.700691e-16
    ## 
    ## $vectors
    ##            [,1]       [,2]       [,3]
    ## [1,] -0.4645473 -0.8829060  0.4082483
    ## [2,] -0.5707955 -0.2395204 -0.8164966
    ## [3,] -0.6770438  0.4038651  0.4082483

Puede transformarse un vector como matriz a través de la función
**`as.matrix`**.

``` r
new.mat <- new.arr[, , 1]

as.matrix(new.mat)
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    6   11   16
    ## [2,]    2    7   12   17
    ## [3,]    3    8   13   18
    ## [4,]    4    9   14   19
    ## [5,]    5   10   15   20

``` r
class(new.mat)
```

    ## [1] "matrix" "array"

Las matrices, al igual que el resto de estructuras de datos que se
trabajan en esta lección tienen una clase propia

``` r
class(my.mat)
```

    ## [1] "matrix" "array"

## Dataframes

Para finalizar esta sección, se hablará sobre **dataframes**, de forma
resumida, un dataframe puede tratarse como una matriz o una lista, ya
que cada columna, por lo general, tendrá un nombre, en dataframes
hablaremos de variables en lugar de columnas, es importante añadir que
todos los registros que aparezcan en el dataframe compartirán el mismo
índice a nivel de fila. Un dataframe acepta diferentes tipos de datos.

Para aprender las características y diferentes funcionalidades que
ofrece un dataframe, trabajaremos directamente con un archivo csv, la
función encargada de leer, cargar y transformar un archivo csv como
dataframe es **`read.csv`**, es importante revisar otros parámetros como
**sep**, **header** o, **na.strings** en el caso de que ya conozcamos de
antemano que el dataset tiene valores nulos que son representados por
otros valores o caracteres

``` r
df <- read.csv("FB.csv")
```

De un modo similar a las listas, puede llamarse a las columnas a través
de dobles corchetes, con el operador $ o, a través de indexación.

``` r
df$Open
```

    ##   [1] 42.05 36.53 32.61 31.37 32.95 32.90 31.48 28.70 28.55 28.89 27.20 26.70
    ##  [13] 26.07 27.00 26.55 27.18 27.48 27.66 27.65 28.51 29.96 31.54 31.92 31.67
    ##  [25] 32.41 32.86 32.69 32.46 31.96 31.92 31.25 30.91 31.32 31.44 32.10 32.43
    ##  [37] 31.48 30.70 31.04 30.50 28.48 28.31 29.41 29.00 28.12 28.82 28.39 27.75
    ##  [49] 23.19 24.00 23.37 21.50 20.77 20.36 21.39 22.20 20.71 20.75 21.41 22.15
    ##  [61] 21.41 20.64 20.44 20.01 19.05 19.58 19.36 19.50 19.52 19.49 19.10 19.32
    ##  [73] 19.27 18.68 18.08 18.27 18.74 19.10 19.06 18.92 20.76 20.96 21.13 22.67
    ##  [85] 21.60 21.99 23.02 22.97 21.78 21.20 20.15 20.99 20.57 22.08 22.08 22.30
    ##  [97] 22.32 21.49 20.40 20.39 19.93 19.88 19.75 19.68 19.68 19.50 19.70 19.00
    ## [109] 19.20 19.25 24.13 23.29 22.40 20.82 21.08 21.26 21.10 21.24 20.85 20.52
    ## [121] 19.96 19.15 19.61 20.10 22.34 22.25 23.96 22.73 23.22 24.58 24.94 26.04
    ## [133] 25.94 26.50 27.26 28.00 27.06 27.75 27.68 27.07 27.17 28.07 28.00 27.59
    ## [145] 28.18 26.77 26.96 27.83 27.49 26.66 26.50 27.03 26.55 25.48 26.20 27.44
    ## [157] 27.88 28.01 28.69 29.51 29.67 30.60 31.28 32.08 30.64 30.21 30.08 30.31
    ## [169] 29.75 31.10 31.27 31.41 31.88 32.00 30.98 29.15 31.01 29.06 28.26 28.74
    ## [181] 29.11 28.89 28.61 27.67 27.36 28.02 28.52 28.23 28.92 28.28 27.62 27.16
    ## [193] 27.36 27.34 26.84 27.05

``` r
df[[2]]
```

    ##   [1] 42.05 36.53 32.61 31.37 32.95 32.90 31.48 28.70 28.55 28.89 27.20 26.70
    ##  [13] 26.07 27.00 26.55 27.18 27.48 27.66 27.65 28.51 29.96 31.54 31.92 31.67
    ##  [25] 32.41 32.86 32.69 32.46 31.96 31.92 31.25 30.91 31.32 31.44 32.10 32.43
    ##  [37] 31.48 30.70 31.04 30.50 28.48 28.31 29.41 29.00 28.12 28.82 28.39 27.75
    ##  [49] 23.19 24.00 23.37 21.50 20.77 20.36 21.39 22.20 20.71 20.75 21.41 22.15
    ##  [61] 21.41 20.64 20.44 20.01 19.05 19.58 19.36 19.50 19.52 19.49 19.10 19.32
    ##  [73] 19.27 18.68 18.08 18.27 18.74 19.10 19.06 18.92 20.76 20.96 21.13 22.67
    ##  [85] 21.60 21.99 23.02 22.97 21.78 21.20 20.15 20.99 20.57 22.08 22.08 22.30
    ##  [97] 22.32 21.49 20.40 20.39 19.93 19.88 19.75 19.68 19.68 19.50 19.70 19.00
    ## [109] 19.20 19.25 24.13 23.29 22.40 20.82 21.08 21.26 21.10 21.24 20.85 20.52
    ## [121] 19.96 19.15 19.61 20.10 22.34 22.25 23.96 22.73 23.22 24.58 24.94 26.04
    ## [133] 25.94 26.50 27.26 28.00 27.06 27.75 27.68 27.07 27.17 28.07 28.00 27.59
    ## [145] 28.18 26.77 26.96 27.83 27.49 26.66 26.50 27.03 26.55 25.48 26.20 27.44
    ## [157] 27.88 28.01 28.69 29.51 29.67 30.60 31.28 32.08 30.64 30.21 30.08 30.31
    ## [169] 29.75 31.10 31.27 31.41 31.88 32.00 30.98 29.15 31.01 29.06 28.26 28.74
    ## [181] 29.11 28.89 28.61 27.67 27.36 28.02 28.52 28.23 28.92 28.28 27.62 27.16
    ## [193] 27.36 27.34 26.84 27.05

``` r
df[["Open"]]
```

    ##   [1] 42.05 36.53 32.61 31.37 32.95 32.90 31.48 28.70 28.55 28.89 27.20 26.70
    ##  [13] 26.07 27.00 26.55 27.18 27.48 27.66 27.65 28.51 29.96 31.54 31.92 31.67
    ##  [25] 32.41 32.86 32.69 32.46 31.96 31.92 31.25 30.91 31.32 31.44 32.10 32.43
    ##  [37] 31.48 30.70 31.04 30.50 28.48 28.31 29.41 29.00 28.12 28.82 28.39 27.75
    ##  [49] 23.19 24.00 23.37 21.50 20.77 20.36 21.39 22.20 20.71 20.75 21.41 22.15
    ##  [61] 21.41 20.64 20.44 20.01 19.05 19.58 19.36 19.50 19.52 19.49 19.10 19.32
    ##  [73] 19.27 18.68 18.08 18.27 18.74 19.10 19.06 18.92 20.76 20.96 21.13 22.67
    ##  [85] 21.60 21.99 23.02 22.97 21.78 21.20 20.15 20.99 20.57 22.08 22.08 22.30
    ##  [97] 22.32 21.49 20.40 20.39 19.93 19.88 19.75 19.68 19.68 19.50 19.70 19.00
    ## [109] 19.20 19.25 24.13 23.29 22.40 20.82 21.08 21.26 21.10 21.24 20.85 20.52
    ## [121] 19.96 19.15 19.61 20.10 22.34 22.25 23.96 22.73 23.22 24.58 24.94 26.04
    ## [133] 25.94 26.50 27.26 28.00 27.06 27.75 27.68 27.07 27.17 28.07 28.00 27.59
    ## [145] 28.18 26.77 26.96 27.83 27.49 26.66 26.50 27.03 26.55 25.48 26.20 27.44
    ## [157] 27.88 28.01 28.69 29.51 29.67 30.60 31.28 32.08 30.64 30.21 30.08 30.31
    ## [169] 29.75 31.10 31.27 31.41 31.88 32.00 30.98 29.15 31.01 29.06 28.26 28.74
    ## [181] 29.11 28.89 28.61 27.67 27.36 28.02 28.52 28.23 28.92 28.28 27.62 27.16
    ## [193] 27.36 27.34 26.84 27.05

Los dataframes también tienen un tipo especial de clase

``` r
class(df)
```

    ## [1] "data.frame"

Para ahorrar trabajo y, no necesariamente tener que escribir siempre el
nombre del dataframe cuando queremos trabajar con una variable, puede
utilizarse la función **`attach`** y cargará todas las columnas como
variables.

``` r
attach(df)

Date
```

    ##   [1] "2012-05-18" "2012-05-21" "2012-05-22" "2012-05-23" "2012-05-24"
    ##   [6] "2012-05-25" "2012-05-29" "2012-05-30" "2012-05-31" "2012-06-01"
    ##  [11] "2012-06-04" "2012-06-05" "2012-06-06" "2012-06-07" "2012-06-08"
    ##  [16] "2012-06-11" "2012-06-12" "2012-06-13" "2012-06-14" "2012-06-15"
    ##  [21] "2012-06-18" "2012-06-19" "2012-06-20" "2012-06-21" "2012-06-22"
    ##  [26] "2012-06-25" "2012-06-26" "2012-06-27" "2012-06-28" "2012-06-29"
    ##  [31] "2012-07-02" "2012-07-03" "2012-07-05" "2012-07-06" "2012-07-09"
    ##  [36] "2012-07-10" "2012-07-11" "2012-07-12" "2012-07-13" "2012-07-16"
    ##  [41] "2012-07-17" "2012-07-18" "2012-07-19" "2012-07-20" "2012-07-23"
    ##  [46] "2012-07-24" "2012-07-25" "2012-07-26" "2012-07-27" "2012-07-30"
    ##  [51] "2012-07-31" "2012-08-01" "2012-08-02" "2012-08-03" "2012-08-06"
    ##  [56] "2012-08-07" "2012-08-08" "2012-08-09" "2012-08-10" "2012-08-13"
    ##  [61] "2012-08-14" "2012-08-15" "2012-08-16" "2012-08-17" "2012-08-20"
    ##  [66] "2012-08-21" "2012-08-22" "2012-08-23" "2012-08-24" "2012-08-27"
    ##  [71] "2012-08-28" "2012-08-29" "2012-08-30" "2012-08-31" "2012-09-04"
    ##  [76] "2012-09-05" "2012-09-06" "2012-09-07" "2012-09-10" "2012-09-11"
    ##  [81] "2012-09-12" "2012-09-13" "2012-09-14" "2012-09-17" "2012-09-18"
    ##  [86] "2012-09-19" "2012-09-20" "2012-09-21" "2012-09-24" "2012-09-25"
    ##  [91] "2012-09-26" "2012-09-27" "2012-09-28" "2012-10-01" "2012-10-02"
    ##  [96] "2012-10-03" "2012-10-04" "2012-10-05" "2012-10-08" "2012-10-09"
    ## [101] "2012-10-10" "2012-10-11" "2012-10-12" "2012-10-15" "2012-10-16"
    ## [106] "2012-10-17" "2012-10-18" "2012-10-19" "2012-10-22" "2012-10-23"
    ## [111] "2012-10-24" "2012-10-25" "2012-10-26" "2012-10-31" "2012-11-01"
    ## [116] "2012-11-02" "2012-11-05" "2012-11-06" "2012-11-07" "2012-11-08"
    ## [121] "2012-11-09" "2012-11-12" "2012-11-13" "2012-11-14" "2012-11-15"
    ## [126] "2012-11-16" "2012-11-19" "2012-11-20" "2012-11-21" "2012-11-23"
    ## [131] "2012-11-26" "2012-11-27" "2012-11-28" "2012-11-29" "2012-11-30"
    ## [136] "2012-12-03" "2012-12-04" "2012-12-05" "2012-12-06" "2012-12-07"
    ## [141] "2012-12-10" "2012-12-11" "2012-12-12" "2012-12-13" "2012-12-14"
    ## [146] "2012-12-17" "2012-12-18" "2012-12-19" "2012-12-20" "2012-12-21"
    ## [151] "2012-12-24" "2012-12-26" "2012-12-27" "2012-12-28" "2012-12-31"
    ## [156] "2013-01-02" "2013-01-03" "2013-01-04" "2013-01-07" "2013-01-08"
    ## [161] "2013-01-09" "2013-01-10" "2013-01-11" "2013-01-14" "2013-01-15"
    ## [166] "2013-01-16" "2013-01-17" "2013-01-18" "2013-01-22" "2013-01-23"
    ## [171] "2013-01-24" "2013-01-25" "2013-01-28" "2013-01-29" "2013-01-30"
    ## [176] "2013-01-31" "2013-02-01" "2013-02-04" "2013-02-05" "2013-02-06"
    ## [181] "2013-02-07" "2013-02-08" "2013-02-11" "2013-02-12" "2013-02-13"
    ## [186] "2013-02-14" "2013-02-15" "2013-02-19" "2013-02-20" "2013-02-21"
    ## [191] "2013-02-22" "2013-02-25" "2013-02-26" "2013-02-27" "2013-02-28"
    ## [196] "2013-03-01"

El resultado en todos los casos es un vector sobre el que podemos
aplicar las mismas funciones de indexación y operaciones ya vistas en la
sección de vectores.

``` r
# Suma de la variable Open
sum(df$Open)
```

    ## [1] 5041.93

``` r
# Mostramos las posiciones 3 a 8 de la variable Open
df$Open[3:8]
```

    ## [1] 32.61 31.37 32.95 32.90 31.48 28.70

``` r
# Filtramos la variable open por todos los valores superiores o iguales que 40
df[df$Open >= 40, ]
```

    ##         Date  Open High Low Close    Volume Adj.Close
    ## 1 2012-05-18 42.05   45  38 38.23 573576400     38.23

``` r
# Seleccionamos las filas 100 a 110 de todas las columnas a excepción de la segunda y tercera
df[100:110, -c(2,3)]
```

    ##           Date   Low Close   Volume Adj.Close
    ## 100 2012-10-09 19.97 20.23 27161800     20.23
    ## 101 2012-10-10 19.45 19.64 39321800     19.64
    ## 102 2012-10-11 19.61 19.75 21817300     19.75
    ## 103 2012-10-12 19.48 19.52 18809400     19.52
    ## 104 2012-10-15 19.49 19.52 20189700     19.52
    ## 105 2012-10-16 19.30 19.48 21834700     19.48
    ## 106 2012-10-17 19.37 19.88 44074500     19.88
    ## 107 2012-10-18 18.89 18.98 52157400     18.98
    ## 108 2012-10-19 18.80 19.00 34835000     19.00
    ## 109 2012-10-22 19.05 19.32 32447300     19.32
    ## 110 2012-10-23 19.10 19.50 78381200     19.50

Cuando ha finalizado el trabajo con el dataframe, utilizaremos
**`detach`** para que sea necesario declarar el nombre del dataframe,
para trabajar con él.

``` r
detach(df)
```

Algunas funciones principales que podemos realizar en un dataframe.

-   **`summary`**: Devuelve un resumen estadístico de un dataframe.

``` r
# Resumen estadístico de un dataframe
summary(df)
```

    ##      Date                Open            High            Low       
    ##  Length:196         Min.   :18.08   Min.   :18.27   Min.   :17.55  
    ##  Class :character   1st Qu.:21.12   1st Qu.:21.59   1st Qu.:20.61  
    ##  Mode  :character   Median :27.02   Median :27.56   Median :26.44  
    ##                     Mean   :25.72   Mean   :26.23   Mean   :25.15  
    ##                     3rd Qu.:28.94   3rd Qu.:29.51   3rd Qu.:28.39  
    ##                     Max.   :42.05   Max.   :45.00   Max.   :38.00  
    ##      Close           Volume            Adj.Close    
    ##  Min.   :17.73   Min.   :  8108300   Min.   :17.73  
    ##  1st Qu.:21.11   1st Qu.: 30382925   1st Qu.:21.11  
    ##  Median :26.91   Median : 46179100   Median :26.91  
    ##  Mean   :25.63   Mean   : 56928836   Mean   :25.63  
    ##  3rd Qu.:29.01   3rd Qu.: 72741500   3rd Qu.:29.01  
    ##  Max.   :38.23   Max.   :573576400   Max.   :38.23

-   **`str`**: Devuelve el tipo de variable del dataframe.

``` r
# Estructura columnar de un dataframe
str(df)
```

    ## 'data.frame':    196 obs. of  7 variables:
    ##  $ Date     : chr  "2012-05-18" "2012-05-21" "2012-05-22" "2012-05-23" ...
    ##  $ Open     : num  42 36.5 32.6 31.4 33 ...
    ##  $ High     : num  45 36.7 33.6 32.5 33.2 ...
    ##  $ Low      : num  38 33 30.9 31.4 31.8 ...
    ##  $ Close    : num  38.2 34 31 32 33 ...
    ##  $ Volume   : int  573576400 168192700 101786600 73600000 50237200 37149800 78063400 57267900 111639200 41855500 ...
    ##  $ Adj.Close: num  38.2 34 31 32 33 ...

-   **`attributes`**: Devuelve el nombre de las filas y columnas.

``` r
# Nombre de filas y columnas
attributes(df)
```

    ## $names
    ## [1] "Date"      "Open"      "High"      "Low"       "Close"     "Volume"   
    ## [7] "Adj.Close"
    ## 
    ## $class
    ## [1] "data.frame"
    ## 
    ## $row.names
    ##   [1]   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17  18
    ##  [19]  19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35  36
    ##  [37]  37  38  39  40  41  42  43  44  45  46  47  48  49  50  51  52  53  54
    ##  [55]  55  56  57  58  59  60  61  62  63  64  65  66  67  68  69  70  71  72
    ##  [73]  73  74  75  76  77  78  79  80  81  82  83  84  85  86  87  88  89  90
    ##  [91]  91  92  93  94  95  96  97  98  99 100 101 102 103 104 105 106 107 108
    ## [109] 109 110 111 112 113 114 115 116 117 118 119 120 121 122 123 124 125 126
    ## [127] 127 128 129 130 131 132 133 134 135 136 137 138 139 140 141 142 143 144
    ## [145] 145 146 147 148 149 150 151 152 153 154 155 156 157 158 159 160 161 162
    ## [163] 163 164 165 166 167 168 169 170 171 172 173 174 175 176 177 178 179 180
    ## [181] 181 182 183 184 185 186 187 188 189 190 191 192 193 194 195 196

-   **`dim`**: Dimensiones del dataframe filas x columnas

``` r
# Dimensiones de un dataframe
dim(df)
```

    ## [1] 196   7

-   **`colnames`**: Nombre de las columnas del dataframe.

``` r
# Nombre de las columnas de un dataframe
colnames(df)
```

    ## [1] "Date"      "Open"      "High"      "Low"       "Close"     "Volume"   
    ## [7] "Adj.Close"

-   **`rownames`**: Nombre de las filas del dataframe.

``` r
# Nombre de las filas
rownames(df)
```

    ##   [1] "1"   "2"   "3"   "4"   "5"   "6"   "7"   "8"   "9"   "10"  "11"  "12" 
    ##  [13] "13"  "14"  "15"  "16"  "17"  "18"  "19"  "20"  "21"  "22"  "23"  "24" 
    ##  [25] "25"  "26"  "27"  "28"  "29"  "30"  "31"  "32"  "33"  "34"  "35"  "36" 
    ##  [37] "37"  "38"  "39"  "40"  "41"  "42"  "43"  "44"  "45"  "46"  "47"  "48" 
    ##  [49] "49"  "50"  "51"  "52"  "53"  "54"  "55"  "56"  "57"  "58"  "59"  "60" 
    ##  [61] "61"  "62"  "63"  "64"  "65"  "66"  "67"  "68"  "69"  "70"  "71"  "72" 
    ##  [73] "73"  "74"  "75"  "76"  "77"  "78"  "79"  "80"  "81"  "82"  "83"  "84" 
    ##  [85] "85"  "86"  "87"  "88"  "89"  "90"  "91"  "92"  "93"  "94"  "95"  "96" 
    ##  [97] "97"  "98"  "99"  "100" "101" "102" "103" "104" "105" "106" "107" "108"
    ## [109] "109" "110" "111" "112" "113" "114" "115" "116" "117" "118" "119" "120"
    ## [121] "121" "122" "123" "124" "125" "126" "127" "128" "129" "130" "131" "132"
    ## [133] "133" "134" "135" "136" "137" "138" "139" "140" "141" "142" "143" "144"
    ## [145] "145" "146" "147" "148" "149" "150" "151" "152" "153" "154" "155" "156"
    ## [157] "157" "158" "159" "160" "161" "162" "163" "164" "165" "166" "167" "168"
    ## [169] "169" "170" "171" "172" "173" "174" "175" "176" "177" "178" "179" "180"
    ## [181] "181" "182" "183" "184" "185" "186" "187" "188" "189" "190" "191" "192"
    ## [193] "193" "194" "195" "196"

-   **`nrow`**: Número de filas.

``` r
# Número de filas
nrow(df)
```

    ## [1] 196

-   **`ncol`**: Número de columnas.

``` r
# Número de columnas
ncol(df)
```

    ## [1] 7

-   **`head`**: Primeras n posiciones del dataframe.

``` r
# Primeras posiciones de un dataframe, por defecto
head(df)
```

    ##         Date  Open  High   Low Close    Volume Adj.Close
    ## 1 2012-05-18 42.05 45.00 38.00 38.23 573576400     38.23
    ## 2 2012-05-21 36.53 36.66 33.00 34.03 168192700     34.03
    ## 3 2012-05-22 32.61 33.59 30.94 31.00 101786600     31.00
    ## 4 2012-05-23 31.37 32.50 31.36 32.00  73600000     32.00
    ## 5 2012-05-24 32.95 33.21 31.77 33.03  50237200     33.03
    ## 6 2012-05-25 32.90 32.95 31.11 31.91  37149800     31.91

``` r
# Primeras 10 posiciones
head(df, 10)
```

    ##          Date  Open  High   Low Close    Volume Adj.Close
    ## 1  2012-05-18 42.05 45.00 38.00 38.23 573576400     38.23
    ## 2  2012-05-21 36.53 36.66 33.00 34.03 168192700     34.03
    ## 3  2012-05-22 32.61 33.59 30.94 31.00 101786600     31.00
    ## 4  2012-05-23 31.37 32.50 31.36 32.00  73600000     32.00
    ## 5  2012-05-24 32.95 33.21 31.77 33.03  50237200     33.03
    ## 6  2012-05-25 32.90 32.95 31.11 31.91  37149800     31.91
    ## 7  2012-05-29 31.48 31.69 28.65 28.84  78063400     28.84
    ## 8  2012-05-30 28.70 29.55 27.86 28.19  57267900     28.19
    ## 9  2012-05-31 28.55 29.67 26.83 29.60 111639200     29.60
    ## 10 2012-06-01 28.89 29.15 27.39 27.72  41855500     27.72

-   **`tail`**: Últimas n posiciones del dataframe.

``` r
# Últimas posiciones de un dataframe, por defecto.
tail(df)
```

    ##           Date  Open  High   Low Close   Volume Adj.Close
    ## 191 2013-02-22 27.62 27.63 26.82 27.13 36350200     27.13
    ## 192 2013-02-25 27.16 27.64 27.15 27.27 34652000     27.27
    ## 193 2013-02-26 27.36 27.46 26.70 27.39 31611700     27.39
    ## 194 2013-02-27 27.34 27.34 26.63 26.87 44319700     26.87
    ## 195 2013-02-28 26.84 27.30 26.34 27.25 83027800     27.25
    ## 196 2013-03-01 27.05 28.12 26.81 27.78 54064800     27.78

``` r
# Últimas 4 posiciones
tail(df, 4)
```

    ##           Date  Open  High   Low Close   Volume Adj.Close
    ## 193 2013-02-26 27.36 27.46 26.70 27.39 31611700     27.39
    ## 194 2013-02-27 27.34 27.34 26.63 26.87 44319700     26.87
    ## 195 2013-02-28 26.84 27.30 26.34 27.25 83027800     27.25
    ## 196 2013-03-01 27.05 28.12 26.81 27.78 54064800     27.78

Finalmente, se muestran algunas de las principales transformaciones que
pueden aplicarse a un dataframe.

Mediante **`rbind`** se añade una nueva fila, por su parte, **`cbind`**
añade una nueva columna.

``` r
df <- rbind(df, c("2013-03-01", 35.12, 39.32, 32.75, 34.65, 57052800, 34.65), stringsAsFactors=T)

tail(df)
```

    ##           Date  Open  High   Low Close   Volume Adj.Close
    ## 192 2013-02-25 27.16 27.64 27.15 27.27 34652000     27.27
    ## 193 2013-02-26 27.36 27.46  26.7 27.39 31611700     27.39
    ## 194 2013-02-27 27.34 27.34 26.63 26.87 44319700     26.87
    ## 195 2013-02-28 26.84  27.3 26.34 27.25 83027800     27.25
    ## 196 2013-03-01 27.05 28.12 26.81 27.78 54064800     27.78
    ## 197 2013-03-01 35.12 39.32 32.75 34.65 57052800     34.65

``` r
index.list <- list(index=1:nrow(df))

df <- cbind(df, index.list)

head(df)
```

    ##         Date  Open  High   Low Close    Volume Adj.Close index
    ## 1 2012-05-18 42.05    45    38 38.23 573576400     38.23     1
    ## 2 2012-05-21 36.53 36.66    33 34.03 168192700     34.03     2
    ## 3 2012-05-22 32.61 33.59 30.94    31 101786600        31     3
    ## 4 2012-05-23 31.37  32.5 31.36    32  73600000        32     4
    ## 5 2012-05-24 32.95 33.21 31.77 33.03  50237200     33.03     5
    ## 6 2012-05-25  32.9 32.95 31.11 31.91  37149800     31.91     6

Otra forma de añadir una columna al dataframe simplemente es asignar el
nombre a través del operador $ y un vector de la misma longitud.

``` r
df$Nueva_Columna <- '^'(as.numeric(df$High),2)

head(df)
```

    ##         Date  Open  High   Low Close    Volume Adj.Close index Nueva_Columna
    ## 1 2012-05-18 42.05    45    38 38.23 573576400     38.23     1      2025.000
    ## 2 2012-05-21 36.53 36.66    33 34.03 168192700     34.03     2      1343.956
    ## 3 2012-05-22 32.61 33.59 30.94    31 101786600        31     3      1128.288
    ## 4 2012-05-23 31.37  32.5 31.36    32  73600000        32     4      1056.250
    ## 5 2012-05-24 32.95 33.21 31.77 33.03  50237200     33.03     5      1102.904
    ## 6 2012-05-25  32.9 32.95 31.11 31.91  37149800     31.91     6      1085.703

Si se desea eliminar una variable, aplicaremos **NULL** a la variable

``` r
# Borramos la columna
df$index <- NULL
```

Para obtener un sub-conjunto del dataframe, empleamos **`subset`**, para
seleccionar las columnas a tener en cuenta, aplicaremos el parámetro
**select**

``` r
muestra <- subset(df, select = c("High", "Low"))

muestra
```

    ##      High   Low
    ## 1      45    38
    ## 2   36.66    33
    ## 3   33.59 30.94
    ## 4    32.5 31.36
    ## 5   33.21 31.77
    ## 6   32.95 31.11
    ## 7   31.69 28.65
    ## 8   29.55 27.86
    ## 9   29.67 26.83
    ## 10  29.15 27.39
    ## 11  27.65 26.44
    ## 12  27.76 25.75
    ## 13  27.17 25.52
    ## 14  27.35 26.15
    ## 15  27.76 26.44
    ## 16  28.07 26.84
    ## 17  27.77 26.96
    ## 18   28.1  27.1
    ## 19  28.32 27.38
    ## 20   30.1 28.35
    ## 21  32.08 29.41
    ## 22  32.18  30.7
    ## 23  31.93 31.15
    ## 24   32.5 31.51
    ## 25  33.45 32.06
    ## 26  33.02 31.55
    ## 27  33.44  32.5
    ## 28   32.9  31.9
    ## 29  32.19  30.9
    ## 30  31.99 30.76
    ## 31  31.73 30.55
    ## 32  31.44  30.8
    ## 33  31.63 31.02
    ## 34   31.9 31.26
    ## 35  32.88 31.99
    ## 36  32.48 31.16
    ## 37  31.56 30.55
    ## 38   31.4  30.6
    ## 39  31.07 30.56
    ## 40   30.5 28.21
    ## 41  28.59 27.15
    ## 42  29.29 28.15
    ## 43   29.5 28.63
    ## 44  29.47 28.72
    ## 45     29 28.01
    ## 46  29.45  28.1
    ## 47  29.49 28.08
    ## 48  28.23 26.73
    ## 49  24.54 22.28
    ## 50  24.04 23.03
    ## 51  23.37 21.61
    ## 52  21.58 20.84
    ## 53  20.84 19.82
    ## 54  22.16  19.9
    ## 55  22.15  21.3
    ## 56  22.45  20.5
    ## 57  21.15 20.22
    ## 58  21.17 20.61
    ## 59  21.82 21.13
    ## 60  22.45  21.4
    ## 61   21.6 20.25
    ## 62  21.41  20.4
    ## 63  20.48 19.69
    ## 64  20.08    19
    ## 65  20.13 18.75
    ## 66  19.98 19.09
    ## 67  19.53 18.96
    ## 68  19.73 19.36
    ## 69  19.68 19.25
    ## 70  19.53  19.1
    ## 71  19.38 18.95
    ## 72  19.38 19.07
    ## 73  19.45 19.06
    ## 74   18.7 18.03
    ## 75  18.27 17.55
    ## 76  18.75 18.18
    ## 77  19.26 18.72
    ## 78  19.42 18.78
    ## 79   19.2 18.55
    ## 80  19.58 18.85
    ## 81  21.16 20.28
    ## 82  21.48 20.61
    ## 83  22.08  20.9
    ## 84  22.75  21.5
    ## 85  21.98 21.37
    ## 86  23.37 21.77
    ## 87  23.24 22.54
    ## 88  23.24  22.6
    ## 89  21.98 20.36
    ## 90  21.21 20.22
    ## 91  20.78  19.8
    ## 92     21 20.16
    ## 93  21.95  20.5
    ## 94  22.59 21.73
    ## 95  22.49 21.82
    ## 96  22.49  21.8
    ## 97   22.4 21.41
    ## 98  21.63 20.88
    ## 99  20.75 20.16
    ## 100 20.55 19.97
    ## 101 19.94 19.45
    ## 102 19.96 19.61
    ## 103  19.8 19.48
    ## 104 19.88 19.49
    ## 105 19.69  19.3
    ## 106 20.48 19.37
    ## 107 19.79 18.89
    ## 108 19.06  18.8
    ## 109 19.43 19.05
    ## 110  19.8  19.1
    ## 111 24.25 22.85
    ## 112 23.31 22.47
    ## 113 22.88 21.88
    ## 114  21.5 20.73
    ## 115 21.44 21.01
    ## 116 21.69 21.07
    ## 117 21.48 20.92
    ## 118 21.37 20.99
    ## 119 20.95 20.37
    ## 120 20.73 19.98
    ## 121    20 19.13
    ## 122 20.17 18.87
    ## 123 20.11 19.56
    ## 124  22.5 19.93
    ## 125  22.5 21.65
    ## 126 23.93 22.18
    ## 127 24.12 22.82
    ## 128  23.9  22.7
    ## 129 24.53 23.05
    ## 130 24.68 23.88
    ## 131 26.09 24.81
    ## 132  26.5 25.46
    ## 133 26.49 25.75
    ## 134 27.52 26.16
    ## 135    28 26.76
    ## 136 28.88 26.98
    ## 137 27.76 26.68
    ## 138  27.9 27.26
    ## 139 27.75 26.82
    ## 140 27.78 26.84
    ## 141 28.17  27.1
    ## 142 28.24 27.66
    ## 143 28.14 27.37
    ## 144 28.75 27.43
    ## 145 28.33 26.76
    ## 146    27 26.32
    ## 147 27.91  26.9
    ## 148 28.22 26.95
    ## 149  27.6 27.13
    ## 150 27.01 26.12
    ## 151 26.96  26.2
    ## 152 27.18 26.38
    ## 153  26.8 25.52
    ## 154 26.11 25.15
    ## 155 26.99 26.11
    ## 156 28.18 27.42
    ## 157 28.47 27.59
    ## 158 28.93 27.83
    ## 159 29.79 28.65
    ## 160  29.6 28.86
    ## 161  30.6 29.49
    ## 162 31.45 30.28
    ## 163 31.96  31.1
    ## 164 32.21 30.62
    ## 165 31.71 29.88
    ## 166 30.35 29.53
    ## 167 30.42 30.03
    ## 168 30.44 29.27
    ## 169 30.89 29.74
    ## 170  31.5  30.8
    ## 171 31.49 30.81
    ## 172 31.93 31.13
    ## 173 32.51 31.81
    ## 174 32.07 30.71
    ## 175 31.49 30.88
    ## 176 31.47 28.74
    ## 177 31.02 29.63
    ## 178  29.2 28.01
    ## 179 28.96 28.04
    ## 180 29.29 28.66
    ## 181 29.15 28.27
    ## 182 29.17 28.51
    ## 183 28.68 28.04
    ## 184 28.16  27.1
    ## 185 28.32 27.31
    ## 186 28.63 28.01
    ## 187 28.75 28.09
    ## 188 29.08 28.12
    ## 189 29.05 28.33
    ## 190 28.55 27.15
    ## 191 27.63 26.82
    ## 192 27.64 27.15
    ## 193 27.46  26.7
    ## 194 27.34 26.63
    ## 195  27.3 26.34
    ## 196 28.12 26.81
    ## 197 39.32 32.75

Para ordenar un dataframe, disponemos de la función **`order`**

``` r
ordered <- df[order(df$Open, decreasing = T), ]

head(ordered)
```

    ##           Date  Open  High   Low Close    Volume Adj.Close Nueva_Columna
    ## 1   2012-05-18 42.05    45    38 38.23 573576400     38.23      2025.000
    ## 2   2012-05-21 36.53 36.66    33 34.03 168192700     34.03      1343.956
    ## 197 2013-03-01 35.12 39.32 32.75 34.65  57052800     34.65      1546.062
    ## 5   2012-05-24 32.95 33.21 31.77 33.03  50237200     33.03      1102.904
    ## 6   2012-05-25  32.9 32.95 31.11 31.91  37149800     31.91      1085.703
    ## 26  2012-06-25 32.86 33.02 31.55 32.06  24352900     32.06      1090.320

Si mediante la función **`names`**, accedemos a los nombres de las
variables, es posible renombrar las columnas

``` r
# Renombramos una columna
names(df)[2] <- "Precio-Apertura"

names(df)
```

    ## [1] "Date"            "Precio-Apertura" "High"            "Low"            
    ## [5] "Close"           "Volume"          "Adj.Close"       "Nueva_Columna"

Con la función **`as.data.frame`**, se pueden convertir vectores,
matrices, listas y arrays como dataframes.

``` r
# Tomamos un array anterior, importante, estudiar cómo se distribuyen las dimensiones.
new.df <- as.data.frame(new.arr)

new.df
```

    ##   V1 V2 V3 V4 V5 V6 V7 V8
    ## 1  1  6 11 16 21 26 31 36
    ## 2  2  7 12 17 22 27 32 37
    ## 3  3  8 13 18 23 28 33 38
    ## 4  4  9 14 19 24 29 34 39
    ## 5  5 10 15 20 25 30 35 40

Finalmente, es importante cómo gestionar los nulos en un dataframe.
Primero, tomaremos una observación como valor nulo.

``` r
new.df[3, 1] <- NA
```

Una forma inicial de comprobar si tenemos nulos en nuestro dataframe, es
a través del comando summary

``` r
summary(new.df) # Aparece un nulo en V1
```

    ##        V1             V2           V3           V4           V5    
    ##  Min.   :1.00   Min.   : 6   Min.   :11   Min.   :16   Min.   :21  
    ##  1st Qu.:1.75   1st Qu.: 7   1st Qu.:12   1st Qu.:17   1st Qu.:22  
    ##  Median :3.00   Median : 8   Median :13   Median :18   Median :23  
    ##  Mean   :3.00   Mean   : 8   Mean   :13   Mean   :18   Mean   :23  
    ##  3rd Qu.:4.25   3rd Qu.: 9   3rd Qu.:14   3rd Qu.:19   3rd Qu.:24  
    ##  Max.   :5.00   Max.   :10   Max.   :15   Max.   :20   Max.   :25  
    ##  NA's   :1                                                         
    ##        V6           V7           V8    
    ##  Min.   :26   Min.   :31   Min.   :36  
    ##  1st Qu.:27   1st Qu.:32   1st Qu.:37  
    ##  Median :28   Median :33   Median :38  
    ##  Mean   :28   Mean   :33   Mean   :38  
    ##  3rd Qu.:29   3rd Qu.:34   3rd Qu.:39  
    ##  Max.   :30   Max.   :35   Max.   :40  
    ## 

Otra manera es utilizar la función **`is.na`**

``` r
is.na(new.df)
```

    ##         V1    V2    V3    V4    V5    V6    V7    V8
    ## [1,] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [2,] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [3,]  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [4,] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [5,] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE

Pueden detectarse las filas en las que hay nulos a través de
**`complete.cases`**

``` r
complete.cases(new.df)
```

    ## [1]  TRUE  TRUE FALSE  TRUE  TRUE

Si se decide borrar los casos nulos haremos:

``` r
new.df <- new.df[complete.cases(new.df), ]

new.df
```

    ##   V1 V2 V3 V4 V5 V6 V7 V8
    ## 1  1  6 11 16 21 26 31 36
    ## 2  2  7 12 17 22 27 32 37
    ## 4  4  9 14 19 24 29 34 39
    ## 5  5 10 15 20 25 30 35 40

Si, por el contrario, interesa reemplazar el valor nulo por otro valor.

``` r
new.df <- as.data.frame(new.arr)
new.df[3, 2] <- NA

new.df$V2[which(is.na(new.df$V2))] <- 1000

new.df
```

    ##   V1   V2 V3 V4 V5 V6 V7 V8
    ## 1  1    6 11 16 21 26 31 36
    ## 2  2    7 12 17 22 27 32 37
    ## 3  3 1000 13 18 23 28 33 38
    ## 4  4    9 14 19 24 29 34 39
    ## 5  5   10 15 20 25 30 35 40
