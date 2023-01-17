# Ejercicio

Se facilitan los siguientes datos para crear un data.frame “personas”.

-   3 personas, por lo tanto, hay 3 id_persona que irán del 1 al 3.
-   Los nombres de las personas son “John”, “Kirk”, “AJ”.
-   Sus edades son: 21, 27, 18.

Se pide:

-   Una vez construido, se debe mostrar el data.frame personas.
-   Mostrar su estructura.
-   Chequear las primeras filas.
-   Chequear las últimas filas.
-   Obtener datos según fila y columnas:
    -   Primera fila, segunda columna.
    -   Primera fila, columna usando nombre
    -   Obtener los datos de la primera fila.
    -   Obtener los datos de una columna.
-   Mostrar el número de filas y de columnas que hay en el data.frame
-   Ordenar el data.frame por la edad.

### Creación del fataframe

``` r
#Se crean vectores con los valores.
id_persona<- c(1:3)
nombre<- c("John", "Kirk", "AJ")
edad<- c(21,27,18)

df<-data.frame(id_persona,nombre,edad)
```

### Mostrar el dataframe

``` r
df
```

    ##   id_persona nombre edad
    ## 1          1   John   21
    ## 2          2   Kirk   27
    ## 3          3     AJ   18

### Mostrar su estructura

``` r
str(df)
```

    ## 'data.frame':    3 obs. of  3 variables:
    ##  $ id_persona: int  1 2 3
    ##  $ nombre    : chr  "John" "Kirk" "AJ"
    ##  $ edad      : num  21 27 18

### Chequear primeras filas

``` r
head(df,2)
```

    ##   id_persona nombre edad
    ## 1          1   John   21
    ## 2          2   Kirk   27

### Chequear últimas filas

``` r
tail(df,2)
```

    ##   id_persona nombre edad
    ## 2          2   Kirk   27
    ## 3          3     AJ   18

### Obtener datos

``` r
#Primera fila, segunda columna
df[1,2]
```

    ## [1] "John"

``` r
#primera fila, primera(se supone porque no viene en el enunciado, está mal redactado) usando nombre
df[1,"id_persona"]
```

    ## [1] 1

``` r
#Obtener datos de la primera fila
df[1, ]
```

    ##   id_persona nombre edad
    ## 1          1   John   21

``` r
#Obtener datos de una columna
df[ ,3]
```

    ## [1] 21 27 18

### Mostrar el número de filas y columnas que hay en el dataframe

``` r
dim(df)
```

    ## [1] 3 3

### Ordenar el dataframe por la edad

``` r
df_ordenado<-df[order(df$edad), ]
df_ordenado
```

    ##   id_persona nombre edad
    ## 3          3     AJ   18
    ## 1          1   John   21
    ## 2          2   Kirk   27
