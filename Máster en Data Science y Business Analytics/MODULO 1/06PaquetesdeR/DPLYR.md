Cuando se trabaja con un conjunto de datos, debemos saber qué queremos
hacer con los datos, encontrar funciones o, saber qué paquetes importar
para transformación y manipulación de datos. Gracias a **Dplyr**,
podemos transformar los datos de una manera muy sencilla.

Su lógica se basa en el uso de *verbos*, que no son más que funciones
que corresponden con la mayor parte de los procesos de manipulación de
datos, lo cuál, hace que sea muy intuitivo el trabajo con esta librería
y saber qué función utilizar para una transformación específica.

**Dplyr**, no es un paquete que ya venga instalado en nuestra
distribución de R, por lo tanto, es necesaria su instalación.

``` r
# Instalamos
# install.packages("dplyr")
```

``` r
# Carga de un paquete en nuestra sesión de trabajo
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

En el presente notebook se explicaran las siguientes funciones de dplyr:

-   **`filter`**
-   **`select`**
-   **`Operador Pipe %>%`**
-   **`mutate`**
-   **`transmute`**
-   **`summarise`**
-   **`group_by`**
-   **`distinct`**
-   **`rename`**
-   **`arrange`**
-   **`sample_n`**
-   **`sample_frac`**

Utilizaremos el siguiente dataset para trabajar. **`storms`**.
Importante, para poder trabajar con este dataset, previamente debe
tenerse cargado dplyr, ya que es un dataset que viene preinstalado con
la librería, si se quieren conocer otros datasets pre-cargados en R,
utilizar el comando **`data()`**

``` r
head(storms)
```

    ## # A tibble: 6 × 13
    ##   name   year month   day  hour   lat  long status categ…¹  wind press…² tropi…³
    ##   <chr> <dbl> <dbl> <int> <dbl> <dbl> <dbl> <chr>  <ord>   <int>   <int>   <int>
    ## 1 Amy    1975     6    27     0  27.5 -79   tropi… -1         25    1013      NA
    ## 2 Amy    1975     6    27     6  28.5 -79   tropi… -1         25    1013      NA
    ## 3 Amy    1975     6    27    12  29.5 -79   tropi… -1         25    1013      NA
    ## 4 Amy    1975     6    27    18  30.5 -79   tropi… -1         25    1013      NA
    ## 5 Amy    1975     6    28     0  31.5 -78.8 tropi… -1         25    1012      NA
    ## 6 Amy    1975     6    28     6  32.4 -78.7 tropi… -1         25    1012      NA
    ## # … with 1 more variable: hurricane_force_diameter <int>, and abbreviated
    ## #   variable names ¹​category, ²​pressure, ³​tropicalstorm_force_diameter

Realizamos una pequeña exploración sobre los datos.

``` r
summary(storms)
```

    ##      name                year          month             day       
    ##  Length:11859       Min.   :1975   Min.   : 1.000   Min.   : 1.00  
    ##  Class :character   1st Qu.:1992   1st Qu.: 8.000   1st Qu.: 8.00  
    ##  Mode  :character   Median :2002   Median : 9.000   Median :16.00  
    ##                     Mean   :2001   Mean   : 8.785   Mean   :15.83  
    ##                     3rd Qu.:2011   3rd Qu.: 9.000   3rd Qu.:24.00  
    ##                     Max.   :2020   Max.   :12.000   Max.   :31.00  
    ##                                                                    
    ##       hour             lat             long            status         
    ##  Min.   : 0.000   Min.   : 7.20   Min.   :-109.30   Length:11859      
    ##  1st Qu.: 6.000   1st Qu.:17.50   1st Qu.: -80.70   Class :character  
    ##  Median :12.000   Median :24.60   Median : -64.40   Mode  :character  
    ##  Mean   : 9.117   Mean   :24.76   Mean   : -64.09                     
    ##  3rd Qu.:18.000   3rd Qu.:31.30   3rd Qu.: -48.40                     
    ##  Max.   :23.000   Max.   :51.90   Max.   :  -6.00                     
    ##                                                                       
    ##  category       wind           pressure    tropicalstorm_force_diameter
    ##  -1:2898   Min.   : 10.00   Min.   : 882   Min.   :  0.0               
    ##  0 :5347   1st Qu.: 35.00   1st Qu.: 985   1st Qu.: 60.0               
    ##  1 :1934   Median : 45.00   Median : 999   Median :120.0               
    ##  2 : 749   Mean   : 53.64   Mean   : 992   Mean   :145.3               
    ##  3 : 434   3rd Qu.: 65.00   3rd Qu.:1006   3rd Qu.:210.0               
    ##  4 : 411   Max.   :160.00   Max.   :1022   Max.   :870.0               
    ##  5 :  86                                   NA's   :6509                
    ##  hurricane_force_diameter
    ##  Min.   :  0.00          
    ##  1st Qu.:  0.00          
    ##  Median :  0.00          
    ##  Mean   : 18.15          
    ##  3rd Qu.: 25.00          
    ##  Max.   :300.00          
    ##  NA's   :6509

``` r
str(storms)
```

    ## tibble [11,859 × 13] (S3: tbl_df/tbl/data.frame)
    ##  $ name                        : chr [1:11859] "Amy" "Amy" "Amy" "Amy" ...
    ##  $ year                        : num [1:11859] 1975 1975 1975 1975 1975 ...
    ##  $ month                       : num [1:11859] 6 6 6 6 6 6 6 6 6 6 ...
    ##  $ day                         : int [1:11859] 27 27 27 27 28 28 28 28 29 29 ...
    ##  $ hour                        : num [1:11859] 0 6 12 18 0 6 12 18 0 6 ...
    ##  $ lat                         : num [1:11859] 27.5 28.5 29.5 30.5 31.5 32.4 33.3 34 34.4 34 ...
    ##  $ long                        : num [1:11859] -79 -79 -79 -79 -78.8 -78.7 -78 -77 -75.8 -74.8 ...
    ##  $ status                      : chr [1:11859] "tropical depression" "tropical depression" "tropical depression" "tropical depression" ...
    ##  $ category                    : Ord.factor w/ 7 levels "-1"<"0"<"1"<"2"<..: 1 1 1 1 1 1 1 1 2 2 ...
    ##  $ wind                        : int [1:11859] 25 25 25 25 25 25 25 30 35 40 ...
    ##  $ pressure                    : int [1:11859] 1013 1013 1013 1013 1012 1012 1011 1006 1004 1002 ...
    ##  $ tropicalstorm_force_diameter: int [1:11859] NA NA NA NA NA NA NA NA NA NA ...
    ##  $ hurricane_force_diameter    : int [1:11859] NA NA NA NA NA NA NA NA NA NA ...

``` r
colnames(storms)
```

    ##  [1] "name"                         "year"                        
    ##  [3] "month"                        "day"                         
    ##  [5] "hour"                         "lat"                         
    ##  [7] "long"                         "status"                      
    ##  [9] "category"                     "wind"                        
    ## [11] "pressure"                     "tropicalstorm_force_diameter"
    ## [13] "hurricane_force_diameter"

``` r
apply(is.na(storms),2,sum)
```

    ##                         name                         year 
    ##                            0                            0 
    ##                        month                          day 
    ##                            0                            0 
    ##                         hour                          lat 
    ##                            0                            0 
    ##                         long                       status 
    ##                            0                            0 
    ##                     category                         wind 
    ##                            0                            0 
    ##                     pressure tropicalstorm_force_diameter 
    ##                            0                         6509 
    ##     hurricane_force_diameter 
    ##                         6509

``` r
apply(is.na(storms),2,sum)/(length(storms)*100)
```

    ##                         name                         year 
    ##                     0.000000                     0.000000 
    ##                        month                          day 
    ##                     0.000000                     0.000000 
    ##                         hour                          lat 
    ##                     0.000000                     0.000000 
    ##                         long                       status 
    ##                     0.000000                     0.000000 
    ##                     category                         wind 
    ##                     0.000000                     0.000000 
    ##                     pressure tropicalstorm_force_diameter 
    ##                     0.000000                     5.006923 
    ##     hurricane_force_diameter 
    ##                     5.006923

## Filter

La función **filter** selecciona columnas, en función del valor de sus
filas. Por ejemplo, seleccionaremos sólo las filas con valor -65.9 en la
columna ‘long’.

``` r
# Seleccionaremos sólo las filas con valor -65.9 en la columna 'long'.

filter(storms, long == -65.9 )
```

    ## # A tibble: 18 × 13
    ##    name       year month   day  hour   lat  long status    categ…¹  wind press…²
    ##    <chr>     <dbl> <dbl> <int> <dbl> <dbl> <dbl> <chr>     <ord>   <int>   <int>
    ##  1 Amy        1975     7     2     6  37.3 -65.9 tropical… 0          60     984
    ##  2 Charley    1980     8    23     0  39.6 -65.9 hurricane 1          65     992
    ##  3 Georges    1980     9     7     6  35.9 -65.9 tropical… 0          45    1002
    ##  4 Emily      1981     9     2     0  31.9 -65.9 tropical… 0          50     992
    ##  5 Ana        1985     7    18     6  39.1 -65.9 tropical… 0          45    1004
    ##  6 Andrew     1992     8    22     0  25.3 -65.9 tropical… 0          55    1000
    ##  7 Edouard    1996     8    29     0  22.9 -65.9 hurricane 3         110     957
    ##  8 Bonnie     1998     8    21    18  20.3 -65.9 tropical… 0          55     999
    ##  9 Dean       2001     8    22    18  19.1 -65.9 tropical… 0          50    1009
    ## 10 Erin       2001     9    11     6  36.9 -65.9 hurricane 1          80     976
    ## 11 Humberto   2001     9    22     6  27.2 -65.9 tropical… -1         30    1010
    ## 12 Colin      2010     8     7    18  29.3 -65.9 tropical… 0          35    1012
    ## 13 Fiona      2010     9     2    12  23.6 -65.9 tropical… 0          45    1002
    ## 14 Igor       2010     9    19    18  30.8 -65.9 hurricane 1          70     952
    ## 15 Shary      2010    10    29    12  29.3 -65.9 tropical… 0          50     998
    ## 16 Gabrielle  2013     9     4    18  16.2 -65.9 tropical… -1         30    1010
    ## 17 Bonnie     2016     6     4    18  35.1 -65.9 tropical… -1         30    1008
    ## 18 Maria      2017     9    20    10  18   -65.9 hurricane 4         135     920
    ## # … with 2 more variables: tropicalstorm_force_diameter <int>,
    ## #   hurricane_force_diameter <int>, and abbreviated variable names ¹​category,
    ## #   ²​pressure

Vemos que es mucho más sencillo este tipo de selección que realizar
`storms[storms$long == -65.9, ]`. Se mostrará un nuevo ejemplo, además
de seleccionar solamente las filas con valor ‘long’ -65.9, también será
requerimiento que el valor de ‘year’ sea 1981.

``` r
filter(storms, long == -65.9 , year == 1981)
```

    ## # A tibble: 1 × 13
    ##   name   year month   day  hour   lat  long status categ…¹  wind press…² tropi…³
    ##   <chr> <dbl> <dbl> <int> <dbl> <dbl> <dbl> <chr>  <ord>   <int>   <int>   <int>
    ## 1 Emily  1981     9     2     0  31.9 -65.9 tropi… 0          50     992      NA
    ## # … with 1 more variable: hurricane_force_diameter <int>, and abbreviated
    ## #   variable names ¹​category, ²​pressure, ³​tropicalstorm_force_diameter

Esto, es mucho más legible que:
`storms[(storms$long == -65.9 & storms$year == 1981), ]`

## Select

De una manera similar a las bases de datos relacionales, con la función
**select**, seleccionamos las columnas que queremos utilizar, por
ejemplo, seleccionaremos del dataframe las columnas: ‘name’ y ‘status’.

``` r
select(storms, name, status) # Equivalente: storms[, c("name", "status")]
```

    ## # A tibble: 11,859 × 2
    ##    name  status             
    ##    <chr> <chr>              
    ##  1 Amy   tropical depression
    ##  2 Amy   tropical depression
    ##  3 Amy   tropical depression
    ##  4 Amy   tropical depression
    ##  5 Amy   tropical depression
    ##  6 Amy   tropical depression
    ##  7 Amy   tropical depression
    ##  8 Amy   tropical depression
    ##  9 Amy   tropical storm     
    ## 10 Amy   tropical storm     
    ## # … with 11,849 more rows

Puede apreciarse que, no es necesario utilizar el operador **$** para
seleccionar las columnas, basta con que el primer argumento sea el
dataframe y, los siguientes, los nombres de las columnas.

También podemos seleccionar rangos, por ejemplo, se tomarán las columnas
desde: ‘year’ a ‘hour’ (ambas inclusive).

``` r
select(storms, year:hour)
```

    ## # A tibble: 11,859 × 4
    ##     year month   day  hour
    ##    <dbl> <dbl> <int> <dbl>
    ##  1  1975     6    27     0
    ##  2  1975     6    27     6
    ##  3  1975     6    27    12
    ##  4  1975     6    27    18
    ##  5  1975     6    28     0
    ##  6  1975     6    28     6
    ##  7  1975     6    28    12
    ##  8  1975     6    28    18
    ##  9  1975     6    29     0
    ## 10  1975     6    29     6
    ## # … with 11,849 more rows

Del mismo modo, también podemos seguir indexando por filas, por ejemplo,
realizando una selección de las 5 primeras.

``` r
select(storms[0: 5, ], year:hour)
```

    ## # A tibble: 5 × 4
    ##    year month   day  hour
    ##   <dbl> <dbl> <int> <dbl>
    ## 1  1975     6    27     0
    ## 2  1975     6    27     6
    ## 3  1975     6    27    12
    ## 4  1975     6    27    18
    ## 5  1975     6    28     0

Existen además parámetros muy interesantes y de gran ayuda cuando no
conocemos exactamente el nombre de la columna que queramos seleccionar
en cuestión. Estos parámetros son:

-   **`starts_with`**: Selecciona columnas que comienzan con una cadena
    de texto.

``` r
head(select(storms, starts_with("y")), 2)
```

    ## # A tibble: 2 × 1
    ##    year
    ##   <dbl>
    ## 1  1975
    ## 2  1975

-   **`ends_with`**: Selecciona columnas que finalizan con una cadena de
    texto.

``` r
head(select(storms, ends_with("y")), 2)
```

    ## # A tibble: 2 × 2
    ##     day category
    ##   <int> <ord>   
    ## 1    27 -1      
    ## 2    27 -1

-   **`contains`**: Selecciona columnas que contienen una cadena de
    texto.

``` r
head(select(storms, contains("on")), 2)
```

    ## # A tibble: 2 × 2
    ##   month  long
    ##   <dbl> <dbl>
    ## 1     6   -79
    ## 2     6   -79

## Pipe %\>%

Similar al operador **\|** en Linux, gracias a dplyr, podemos utilizar
un operador que nos permite concatenar funciones **%\>%**, es decir, a
los resultados de una primera función, aplicar una nueva función, todo a
través de una sola línea de código.

Para ejemplificar este operador, se tomará el ejemplo previo: Además de
seleccionar solamente las filas con valor ‘long’ -65.9, también será
requerimiento que el valor de ‘year’ sea 1981. A este ejemplo se añadirá
la restricción de mostrar únicamente con las columnas: ‘status’ y
‘category’.

``` r
filter(storms, long == -65.9 , year == 1981) %>%
  select(status, category)
```

    ## # A tibble: 1 × 2
    ##   status         category
    ##   <chr>          <ord>   
    ## 1 tropical storm 0

Es posible seguir añadiendo funciones, por ejemplo, cambiaremos las
columnas a proyectar por ‘wind’ y ‘pressure’, el año a filtrar por 2001,
finalmente mostraremos el resumen estadístico de los resultados.

``` r
filter(storms, long == -65.9 , year == 2001) %>%
  select(wind, pressure) %>%
  summary
```

    ##       wind          pressure     
    ##  Min.   :30.00   Min.   : 976.0  
    ##  1st Qu.:40.00   1st Qu.: 992.5  
    ##  Median :50.00   Median :1009.0  
    ##  Mean   :53.33   Mean   : 998.3  
    ##  3rd Qu.:65.00   3rd Qu.:1009.5  
    ##  Max.   :80.00   Max.   :1010.0

## Mutate

La función **mutate**, es utilizada para crear columnas en base a otras
ya existentes. Además agrega la nueva columna al dataframe.

``` r
mutate(storms, 
       presion_ratio = round(pressure / wind),2) %>% select(pressure, wind, presion_ratio) %>% head(., 5)
```

    ## # A tibble: 5 × 3
    ##   pressure  wind presion_ratio
    ##      <int> <int>         <dbl>
    ## 1     1013    25            41
    ## 2     1013    25            41
    ## 3     1013    25            41
    ## 4     1013    25            41
    ## 5     1012    25            40

## Transmute

Es igual a **mutate**. Sin embargo, **transmute** realiza la operación,
pero solamente devuelve las nuevas columnas.

``` r
transmute(storms, 
          presion_ratio = round((pressure / wind),2) ,
          mean_ratio_wind = presion_ratio/mean(wind)) %>% head(.,10)
```

    ## # A tibble: 10 × 2
    ##    presion_ratio mean_ratio_wind
    ##            <dbl>           <dbl>
    ##  1          40.5           0.755
    ##  2          40.5           0.755
    ##  3          40.5           0.755
    ##  4          40.5           0.755
    ##  5          40.5           0.755
    ##  6          40.5           0.755
    ##  7          40.4           0.754
    ##  8          33.5           0.625
    ##  9          28.7           0.535
    ## 10          25.0           0.467

## Summarise

La función **summarise**, permite confeccionar resúmenes sobre los datos
de forma personalizada mostrando estadísticas sobre variables.

Para ayudar en la obtención de estadísticas, dplyr integra nuevas
funciones que realizan las siguientes operaciones:

-   **first**: Muestra el primer elemento de una columna del dataframe.
-   **last**: Muestra el último elemento de una columna del dataframe.
-   **n**: Elementos de la columna del dataframe.
-   **n_distinct**: Número de elementos únicos de la columna del
    dataframe.

``` r
storms %>% summarise(sum_pressure = sum(pressure),
                     min_wind = min(wind),
                     max_wind = max(wind),
                     range_wind = (max(wind) - min(wind)),
                     first_row_status = first(status),
                     last_row_status = last(status),
                     unique_categories = n_distinct(category),
                     total_rows = n())
```

    ## # A tibble: 1 × 8
    ##   sum_pressure min_wind max_wind range_wind first_row_…¹ last_…² uniqu…³ total…⁴
    ##          <int>    <int>    <int>      <int> <chr>        <chr>     <int>   <int>
    ## 1     11763897       10      160        150 tropical de… tropic…       7   11859
    ## # … with abbreviated variable names ¹​first_row_status, ²​last_row_status,
    ## #   ³​unique_categories, ⁴​total_rows

## Group_by

Al igual que en SQL, a través de **group_by**, podemos mostrar el
dataframe agrupado por variables o estadísticas de las mismas.

``` r
storms %>% group_by(category, status) %>%
           summarise(media_viento = mean(wind),
                     total_category = n())
```

    ## `summarise()` has grouped output by 'category'. You can override using the
    ## `.groups` argument.

    ## # A tibble: 8 × 4
    ## # Groups:   category [7]
    ##   category status              media_viento total_category
    ##   <ord>    <chr>                      <dbl>          <int>
    ## 1 -1       tropical depression         27.5           2898
    ## 2 0        tropical storm              45.7           5347
    ## 3 1        hurricane                   71.0           1933
    ## 4 1        tropical storm              70                1
    ## 5 2        hurricane                   89.4            749
    ## 6 3        hurricane                  104.             434
    ## 7 4        hurricane                  122.             411
    ## 8 5        hurricane                  146.              86

``` r
storms %>%
  select(year, name, pressure) %>% 
  group_by(name, year) %>% 
  summarise(media_presion = round(mean(pressure), 2)) %>% 
  arrange(year)
```

    ## `summarise()` has grouped output by 'name'. You can override using the
    ## `.groups` argument.

    ## # A tibble: 512 × 3
    ## # Groups:   name [214]
    ##    name      year media_presion
    ##    <chr>    <dbl>         <dbl>
    ##  1 Amy       1975          995.
    ##  2 Caroline  1975         1002.
    ##  3 Doris     1975          983.
    ##  4 Belle     1976          982.
    ##  5 Gloria    1976          993.
    ##  6 Anita     1977          982.
    ##  7 Clara     1977         1005.
    ##  8 Evelyn    1977         1001.
    ##  9 Amelia    1978         1008.
    ## 10 Bess      1978         1009.
    ## # … with 502 more rows

## Distinct

Elimina filas duplicadas de un dataframe.

``` r
df <- data.frame("col_uno"=c(1,2,3,4,5,6,6), "col_dos"= c(1,7,8,4,5,6,6))
df
```

    ##   col_uno col_dos
    ## 1       1       1
    ## 2       2       7
    ## 3       3       8
    ## 4       4       4
    ## 5       5       5
    ## 6       6       6
    ## 7       6       6

``` r
distinct(df)
```

    ##   col_uno col_dos
    ## 1       1       1
    ## 2       2       7
    ## 3       3       8
    ## 4       4       4
    ## 5       5       5
    ## 6       6       6

## Rename

Su uso es muy sencillo, simplemente pasamos como argumento el dataframe
y el nuevo nombre que utilizaremos para una columna determinada. Por
ejemplo, se cambiará el nombre de la variable ‘status’ por ‘tipo’.

``` r
rename(storms, tipo = status)
```

    ## # A tibble: 11,859 × 13
    ##    name   year month   day  hour   lat  long tipo  categ…¹  wind press…² tropi…³
    ##    <chr> <dbl> <dbl> <int> <dbl> <dbl> <dbl> <chr> <ord>   <int>   <int>   <int>
    ##  1 Amy    1975     6    27     0  27.5 -79   trop… -1         25    1013      NA
    ##  2 Amy    1975     6    27     6  28.5 -79   trop… -1         25    1013      NA
    ##  3 Amy    1975     6    27    12  29.5 -79   trop… -1         25    1013      NA
    ##  4 Amy    1975     6    27    18  30.5 -79   trop… -1         25    1013      NA
    ##  5 Amy    1975     6    28     0  31.5 -78.8 trop… -1         25    1012      NA
    ##  6 Amy    1975     6    28     6  32.4 -78.7 trop… -1         25    1012      NA
    ##  7 Amy    1975     6    28    12  33.3 -78   trop… -1         25    1011      NA
    ##  8 Amy    1975     6    28    18  34   -77   trop… -1         30    1006      NA
    ##  9 Amy    1975     6    29     0  34.4 -75.8 trop… 0          35    1004      NA
    ## 10 Amy    1975     6    29     6  34   -74.8 trop… 0          40    1002      NA
    ## # … with 11,849 more rows, 1 more variable: hurricane_force_diameter <int>, and
    ## #   abbreviated variable names ¹​category, ²​pressure,
    ## #   ³​tropicalstorm_force_diameter

## Arrange

La función **arrange**, se utiliza para ordenar un dataframe de dos
formas diferentes: 1. De forma descendente con **desc**, 2. Ascendente
(por defecto). En el siguiente ejemplo, se ordenará el dataframe por las
columnas lat y long.

``` r
arrange(storms, lat, long) %>% head(., 10)
```

    ## # A tibble: 10 × 13
    ##    name     year month   day  hour   lat  long status      categ…¹  wind press…²
    ##    <chr>   <dbl> <dbl> <int> <dbl> <dbl> <dbl> <chr>       <ord>   <int>   <int>
    ##  1 Isidore  1990     9     4     0   7.2 -23.4 tropical d… -1         25    1010
    ##  2 Isidore  1990     9     4     6   7.4 -25.1 tropical d… -1         25    1010
    ##  3 Kirk     2018     9    22     6   7.7 -21.8 tropical d… -1         30    1007
    ##  4 Kirk     2018     9    22    12   8.1 -22.9 tropical s… 0          35    1005
    ##  5 Pablo    1995    10     4    18   8.3 -31.4 tropical d… -1         30    1009
    ##  6 Pablo    1995    10     5     0   8.4 -32.8 tropical d… -1         30    1009
    ##  7 Isidore  1990     9     4    12   8.4 -26.7 tropical d… -1         25    1009
    ##  8 Kirk     2018     9    22    18   8.5 -24.1 tropical s… 0          35    1005
    ##  9 Isidore  1996     9    24    12   8.6 -23.3 tropical d… -1         25    1008
    ## 10 Arthur   1990     7    22     6   8.8 -41.9 tropical d… -1         25    1010
    ## # … with 2 more variables: tropicalstorm_force_diameter <int>,
    ## #   hurricane_force_diameter <int>, and abbreviated variable names ¹​category,
    ## #   ²​pressure

En este otro ejemplo, se ordenará de forma descendente todo el dataframe
por la columna ‘year’

``` r
arrange(storms, desc(year)) %>% head(., 10)
```

    ## # A tibble: 10 × 13
    ##    name    year month   day  hour   lat  long status       categ…¹  wind press…²
    ##    <chr>  <dbl> <dbl> <int> <dbl> <dbl> <dbl> <chr>        <ord>   <int>   <int>
    ##  1 Arthur  2020     5    16    18  28   -78.7 tropical de… -1         30    1008
    ##  2 Arthur  2020     5    17     0  28.9 -78   tropical st… 0          35    1006
    ##  3 Arthur  2020     5    17     6  29.6 -77.6 tropical st… 0          35    1004
    ##  4 Arthur  2020     5    17    12  30.3 -77.5 tropical st… 0          35    1003
    ##  5 Arthur  2020     5    17    18  31   -77.3 tropical st… 0          40    1003
    ##  6 Arthur  2020     5    18     0  31.9 -77   tropical st… 0          40    1003
    ##  7 Arthur  2020     5    18     6  33.1 -76.7 tropical st… 0          40    1002
    ##  8 Arthur  2020     5    18    12  34.4 -75.9 tropical st… 0          45    1000
    ##  9 Arthur  2020     5    18    18  35.5 -74.7 tropical st… 0          45     993
    ## 10 Arthur  2020     5    19     0  36.2 -73.1 tropical st… 0          50     991
    ## # … with 2 more variables: tropicalstorm_force_diameter <int>,
    ## #   hurricane_force_diameter <int>, and abbreviated variable names ¹​category,
    ## #   ²​pressure

## Sample_n

Devuelve una muestra de n filas aleatorias, podemos utilizar `replace=T`
para hacer muestreos.

``` r
sample_n(storms, 5)
```

    ## # A tibble: 5 × 13
    ##   name   year month   day  hour   lat  long status categ…¹  wind press…² tropi…³
    ##   <chr> <dbl> <dbl> <int> <dbl> <dbl> <dbl> <chr>  <ord>   <int>   <int>   <int>
    ## 1 Floyd  1999     9    14    18  26.1 -77   hurri… 3         110     930      NA
    ## 2 Keith  2000    10     5     6  21.2 -96.1 hurri… 1          65     987      NA
    ## 3 Tanya  1995    10    31    12  36.2 -45.8 hurri… 1          75     973      NA
    ## 4 Fred…  1979     9     2    12  15.5 -57.2 tropi… 0          60     996      NA
    ## 5 Pablo  2019    10    27     6  39.5 -20.7 tropi… 0          60     983      90
    ## # … with 1 more variable: hurricane_force_diameter <int>, and abbreviated
    ## #   variable names ¹​category, ²​pressure, ³​tropicalstorm_force_diameter

## Sample_frac

Devuelve una muestra aleatoria del dataframe de forma porcentual,
podemos utilizar `replace=T` para hacer muestreos.

``` r
sample_frac(storms, 0.01)
```

    ## # A tibble: 119 × 13
    ##    name     year month   day  hour   lat  long status      categ…¹  wind press…²
    ##    <chr>   <dbl> <dbl> <int> <dbl> <dbl> <dbl> <chr>       <ord>   <int>   <int>
    ##  1 Arthur   2014     7     2     6  28.2 -79.1 tropical s… 0          50     995
    ##  2 Iota     2020    11    15     6  13   -77.1 hurricane   1          65     988
    ##  3 Iris     1989     9    19     6  18.1 -57.5 tropical s… 0          55    1001
    ##  4 Charley  1998     8    22    12  27.9 -97.4 tropical s… 0          35    1001
    ##  5 Alex     2004     8     3     0  32.4 -78.2 tropical s… 0          60     987
    ##  6 Ernesto  2012     8     4     6  13.9 -66.4 tropical s… 0          45    1005
    ##  7 Isaac    2012     8    29    18  29.7 -90.8 tropical s… 0          60     973
    ##  8 Kyle     2008     9    25     0  21.5 -70   tropical d… -1         30    1005
    ##  9 Alberto  2000     8     9    12  21.9 -49.9 tropical s… 0          55     994
    ## 10 Keith    1988    11    17    18  14.9 -74.3 tropical d… -1         30    1008
    ## # … with 109 more rows, 2 more variables: tropicalstorm_force_diameter <int>,
    ## #   hurricane_force_diameter <int>, and abbreviated variable names ¹​category,
    ## #   ²​pressure
