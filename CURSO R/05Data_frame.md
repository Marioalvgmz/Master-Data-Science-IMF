# Caso práctico 1

Crear un data.frame con los siguientes datos:

-   Producto=“Zumo”, “Queso”, “Yogurt”
-   Seccion = “Bebidas”, “Productos lácteos”, “Productos lácteos”
-   Unidades =2, 1, 10

1.  Mostar el data.frame que se ha creado con el nombre super.
2.  Mostrar la primera fila del data.frame, usando la función específica
    para ello head.
3.  Mostrar las unidades que hay en el super.
4.  Mostrar los productos que hay en el super

``` r
Producto <- c("Zumo", "Queso", "Yogurt")
Seccion <- c("Bebidas", "Productos lácteos", "Productos lácteos")
Unidades <- c(2,1,10)

super <- data.frame(producto=Producto, seccion=Seccion, unidades=Unidades)
super
```

    ##   producto           seccion unidades
    ## 1     Zumo           Bebidas        2
    ## 2    Queso Productos lácteos        1
    ## 3   Yogurt Productos lácteos       10

``` r
head(super,1)
```

    ##   producto seccion unidades
    ## 1     Zumo Bebidas        2

``` r
super[,3]
```

    ## [1]  2  1 10

``` r
super$producto
```

    ## [1] "Zumo"   "Queso"  "Yogurt"

# Caso practico 2

## Ejercicio 1

Se facilitan los siguientes datos para crear un data.frame llamado
“empleados”:

-   Generar el id_empleado que sean números del 1 al 5.
-   Los nombres de los empleados son
    “Rick”,“Dan”,“Michelle”,“Ryan”,“Gary”.
-   El salario de los empleados: 623.3,515.2,611.0,729.0,843.25

Una vez construido, se debe mostrar el data.frame “empleados”.

``` r
id_empleado <- seq(1:5)
nombre_empleado <- c("Rick","Dan","Michelle","Ryan","Gary")
salario <- c(623.3,515.2,611.0,729.0,843.25)

empleados <- data.frame(id=id_empleado, nombre=nombre_empleado, salario=salario)
empleados
```

    ##   id   nombre salario
    ## 1  1     Rick  623.30
    ## 2  2      Dan  515.20
    ## 3  3 Michelle  611.00
    ## 4  4     Ryan  729.00
    ## 5  5     Gary  843.25

## Ejercicio 2

A partir del data.frame creado en el ejercicio anterior, se deben
realizar las distintas operaciones:

1.  Extraer las dos primeras filas.
2.  Visualizar la 3ª, 5ª fila con la 1ª y 3ª columna
3.  Añadir al data.frame del ejercicio 1 un nuevo vector llamado
    “departamento”: “IT”,“Operations”,“IT”,“HR”,“Finance”.

``` r
empleados[c(1,2),]
```

    ##   id nombre salario
    ## 1  1   Rick   623.3
    ## 2  2    Dan   515.2

``` r
empleados[c(3,5),c(1,3)]
```

    ##   id salario
    ## 3  3  611.00
    ## 5  5  843.25

``` r
empleados_copia<-empleados
empleados_copia$departamento <- c("IT","Operations","IT","HR","Finance")
empleados_copia
```

    ##   id   nombre salario departamento
    ## 1  1     Rick  623.30           IT
    ## 2  2      Dan  515.20   Operations
    ## 3  3 Michelle  611.00           IT
    ## 4  4     Ryan  729.00           HR
    ## 5  5     Gary  843.25      Finance

``` r
str(empleados_copia)
```

    ## 'data.frame':    5 obs. of  4 variables:
    ##  $ id          : int  1 2 3 4 5
    ##  $ nombre      : chr  "Rick" "Dan" "Michelle" "Ryan" ...
    ##  $ salario     : num  623 515 611 729 843
    ##  $ departamento: chr  "IT" "Operations" "IT" "HR" ...
