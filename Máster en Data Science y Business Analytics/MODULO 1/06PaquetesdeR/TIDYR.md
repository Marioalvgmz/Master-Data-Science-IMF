El Data Science se basa en gran medida en almacenar, transformar y
visualizar datos y modelos estadísticos. Todos los proyectos tienen un
punto común de inicio, preparar los datos para estudiarlos a través de
un software destinado a ello.

Los datasets tienen diferentes formatos y en muchas ocasiones, están
desorganizados y, una de las tareas que más tiempo consume (más del 80%
del tiempo en proyectos de ciencia de datos es consumido en tareas de
limpieza de datos) es la organización, transformación y limpieza de
datos. Basándose en la idea del artículo *Tidy Data* de Hadley Wickham
<http://www.jstatsoft.org/v59/i10/paper> surge el paquete **Tidyr**, un
paquete que, como veremos a continuación nos proveerá de elegantes
funciones para organizar nuestros datos y aportar un mayor sentido a
nuestros datasets.

Los datos organizados (*tidy*), deberían seguir la siguiente estructura:

-   Cada variable formar una columna.
-   Cada observación forma una fila.
-   Cada valor tiene su posición en una tabla.

En **Tidyr**, nos encontramos con las siguientes funciones para
organizar nuestros datos:

-   **`spread`**
-   **`gather`**
-   **`separate`**
-   **`unite`**

Utilizaremos datasets que proporciona la librería Tidyr, por lo tanto,
comenzaremos cargando la librería.

``` r
# install.packages("tidyr")

library(tidyr)
```

## Spread

Toma columnas en modo clave:valor y las pivota para crear columnas en
función de los valores únicos del campo clave. Para este ejemplo
utilizaremos el siguiente dataset disponible en tidyr **table2**

``` r
table2
```

    ## # A tibble: 12 × 4
    ##    country      year type            count
    ##    <chr>       <int> <chr>           <int>
    ##  1 Afghanistan  1999 cases             745
    ##  2 Afghanistan  1999 population   19987071
    ##  3 Afghanistan  2000 cases            2666
    ##  4 Afghanistan  2000 population   20595360
    ##  5 Brazil       1999 cases           37737
    ##  6 Brazil       1999 population  172006362
    ##  7 Brazil       2000 cases           80488
    ##  8 Brazil       2000 population  174504898
    ##  9 China        1999 cases          212258
    ## 10 China        1999 population 1272915272
    ## 11 China        2000 cases          213766
    ## 12 China        2000 population 1280428583

``` r
spread(table2, type, count)
```

    ## # A tibble: 6 × 4
    ##   country      year  cases population
    ##   <chr>       <int>  <int>      <int>
    ## 1 Afghanistan  1999    745   19987071
    ## 2 Afghanistan  2000   2666   20595360
    ## 3 Brazil       1999  37737  172006362
    ## 4 Brazil       2000  80488  174504898
    ## 5 China        1999 212258 1272915272
    ## 6 China        2000 213766 1280428583

``` r
dim(table2)
```

    ## [1] 12  4

``` r
dim(spread(table2, type, count))
```

    ## [1] 6 4

Se puede comprobar que, el número de filas queda dividido entre el
número de valores únicos del campo clave.

## Gather

**Gather** es el caso contrario de **spread**, ya que en lugar de
pivotar filas para crear columnas, aumenta la dimensionalidad en cuanto
a filas. Para ejemplificar esta función, se utilizará el siguiente
dataset.

``` r
head(billboard)
```

    ## # A tibble: 6 × 79
    ##   artist  track date.ent…¹   wk1   wk2   wk3   wk4   wk5   wk6   wk7   wk8   wk9
    ##   <chr>   <chr> <date>     <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
    ## 1 2 Pac   Baby… 2000-02-26    87    82    72    77    87    94    99    NA    NA
    ## 2 2Ge+her The … 2000-09-02    91    87    92    NA    NA    NA    NA    NA    NA
    ## 3 3 Door… Kryp… 2000-04-08    81    70    68    67    66    57    54    53    51
    ## 4 3 Door… Loser 2000-10-21    76    76    72    69    67    65    55    59    62
    ## 5 504 Bo… Wobb… 2000-04-15    57    34    25    17    17    31    36    49    53
    ## 6 98^0    Give… 2000-08-19    51    39    34    26    26    19     2     2     3
    ## # … with 67 more variables: wk10 <dbl>, wk11 <dbl>, wk12 <dbl>, wk13 <dbl>,
    ## #   wk14 <dbl>, wk15 <dbl>, wk16 <dbl>, wk17 <dbl>, wk18 <dbl>, wk19 <dbl>,
    ## #   wk20 <dbl>, wk21 <dbl>, wk22 <dbl>, wk23 <dbl>, wk24 <dbl>, wk25 <dbl>,
    ## #   wk26 <dbl>, wk27 <dbl>, wk28 <dbl>, wk29 <dbl>, wk30 <dbl>, wk31 <dbl>,
    ## #   wk32 <dbl>, wk33 <dbl>, wk34 <dbl>, wk35 <dbl>, wk36 <dbl>, wk37 <dbl>,
    ## #   wk38 <dbl>, wk39 <dbl>, wk40 <dbl>, wk41 <dbl>, wk42 <dbl>, wk43 <dbl>,
    ## #   wk44 <dbl>, wk45 <dbl>, wk46 <dbl>, wk47 <dbl>, wk48 <dbl>, wk49 <dbl>, …

``` r
colnames(billboard)
```

    ##  [1] "artist"       "track"        "date.entered" "wk1"          "wk2"         
    ##  [6] "wk3"          "wk4"          "wk5"          "wk6"          "wk7"         
    ## [11] "wk8"          "wk9"          "wk10"         "wk11"         "wk12"        
    ## [16] "wk13"         "wk14"         "wk15"         "wk16"         "wk17"        
    ## [21] "wk18"         "wk19"         "wk20"         "wk21"         "wk22"        
    ## [26] "wk23"         "wk24"         "wk25"         "wk26"         "wk27"        
    ## [31] "wk28"         "wk29"         "wk30"         "wk31"         "wk32"        
    ## [36] "wk33"         "wk34"         "wk35"         "wk36"         "wk37"        
    ## [41] "wk38"         "wk39"         "wk40"         "wk41"         "wk42"        
    ## [46] "wk43"         "wk44"         "wk45"         "wk46"         "wk47"        
    ## [51] "wk48"         "wk49"         "wk50"         "wk51"         "wk52"        
    ## [56] "wk53"         "wk54"         "wk55"         "wk56"         "wk57"        
    ## [61] "wk58"         "wk59"         "wk60"         "wk61"         "wk62"        
    ## [66] "wk63"         "wk64"         "wk65"         "wk66"         "wk67"        
    ## [71] "wk68"         "wk69"         "wk70"         "wk71"         "wk72"        
    ## [76] "wk73"         "wk74"         "wk75"         "wk76"

``` r
gather(billboard, "week", "sales", 4:ncol(billboard))
```

    ## # A tibble: 24,092 × 5
    ##    artist         track                   date.entered week  sales
    ##    <chr>          <chr>                   <date>       <chr> <dbl>
    ##  1 2 Pac          Baby Don't Cry (Keep... 2000-02-26   wk1      87
    ##  2 2Ge+her        The Hardest Part Of ... 2000-09-02   wk1      91
    ##  3 3 Doors Down   Kryptonite              2000-04-08   wk1      81
    ##  4 3 Doors Down   Loser                   2000-10-21   wk1      76
    ##  5 504 Boyz       Wobble Wobble           2000-04-15   wk1      57
    ##  6 98^0           Give Me Just One Nig... 2000-08-19   wk1      51
    ##  7 A*Teens        Dancing Queen           2000-07-08   wk1      97
    ##  8 Aaliyah        I Don't Wanna           2000-01-29   wk1      84
    ##  9 Aaliyah        Try Again               2000-03-18   wk1      59
    ## 10 Adams, Yolanda Open My Heart           2000-08-26   wk1      76
    ## # … with 24,082 more rows

``` r
dim(billboard)
```

    ## [1] 317  79

``` r
dim(gather(billboard, "week", "sales", 4:ncol(billboard)))
```

    ## [1] 24092     5

## Separate

La función se **separate** es muy básica, teniendo en cuenta un
carácter, por ejemplo separadores de una fecha, de una hora, un email,
una dirección IP, etc. Devuelve tantas columnas cómo elementos sea
posible separar.

``` r
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

``` r
aux.tidy.billboard <- gather(billboard, "week", "sales", 4:ncol(billboard))

separate(aux.tidy.billboard, date.entered, into = c("year", "month", "day"), sep = "-") %>% head()
```

    ## # A tibble: 6 × 7
    ##   artist       track                   year  month day   week  sales
    ##   <chr>        <chr>                   <chr> <chr> <chr> <chr> <dbl>
    ## 1 2 Pac        Baby Don't Cry (Keep... 2000  02    26    wk1      87
    ## 2 2Ge+her      The Hardest Part Of ... 2000  09    02    wk1      91
    ## 3 3 Doors Down Kryptonite              2000  04    08    wk1      81
    ## 4 3 Doors Down Loser                   2000  10    21    wk1      76
    ## 5 504 Boyz     Wobble Wobble           2000  04    15    wk1      57
    ## 6 98^0         Give Me Just One Nig... 2000  08    19    wk1      51

## Unite

Realiza lo contrario que **separate**, mediante **unite**, juntamos n
columnas en una sola, a través un separador común (el separador puede
ser simplemente un espacio)

``` r
tidy.billboard <- separate(aux.tidy.billboard, date.entered, into = c("year", "month", "day"), sep = "-")

new.billboard <- unite(tidy.billboard, "full_song_name", artist, track, sep = ' - ')
```

``` r
head(new.billboard)
```

    ## # A tibble: 6 × 6
    ##   full_song_name                    year  month day   week  sales
    ##   <chr>                             <chr> <chr> <chr> <chr> <dbl>
    ## 1 2 Pac - Baby Don't Cry (Keep...   2000  02    26    wk1      87
    ## 2 2Ge+her - The Hardest Part Of ... 2000  09    02    wk1      91
    ## 3 3 Doors Down - Kryptonite         2000  04    08    wk1      81
    ## 4 3 Doors Down - Loser              2000  10    21    wk1      76
    ## 5 504 Boyz - Wobble Wobble          2000  04    15    wk1      57
    ## 6 98^0 - Give Me Just One Nig...    2000  08    19    wk1      51

``` r
colnames(new.billboard)
```

    ## [1] "full_song_name" "year"           "month"          "day"           
    ## [5] "week"           "sales"
