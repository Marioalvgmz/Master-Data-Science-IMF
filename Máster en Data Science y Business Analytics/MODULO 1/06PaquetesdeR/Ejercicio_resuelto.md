En el siguiente ejercicio se trabajará con el dataset `relig_income` que
es perteneciente de la librería **tidyr**, por lo que como punto de
partida tendremos cargada dicha librería. Sobre el dataset mencionado
anteriormente, el alumno deberá realizar las siguientes
transformaciones:

-   Agrupar todas las variables que tengan que ver con la cuantía
    monetaria desde *\<$10k* hasta *Don’t know/refused* en dos
    variables: “Income”, “N_People”.
-   Convierte a factor las variables: religion e Income.
-   Agrupa el dataset resultante por religion, sobre esta agrupación,
    muestra la estadística “media_creyentes” que contenga la media de la
    variable “N_People”, finalmente, ordena de forma descendente dicha
    media.
-   Crea una nueva variable en el dataset con nombre “media_creyentes”
    cuyo valor sea: el valor de “N_People” entre la longitud del vector
    (redondea la columna a dos decimales).
-   Obtén un nuevo dataset, que sea el resultado de filtrar la variable
    “N_People” por todos los valores de la media de sí misma y que
    además la variable “Income” no contenga el valor “Don’t
    know/refused”. Tras filtrar el dataset, obtén una muestra del 30%.
-   Finalmente, sobre el dataset anterior, selecciona las columnas
    “Income” y “religion”, agrupa estas variables por la variable
    “Income”, sobre esta agrupación, muestra el número de todas las
    religiones diferentes para cada valor de “Income”, en último lugar,
    ordena el valor de la estadística realizada de menor a mayor.

``` r
library(tidyr)
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
head(relig_income)
```

    ## # A tibble: 6 × 11
    ##   religion       `<$10k` $10-2…¹ $20-3…² $30-4…³ $40-5…⁴ $50-7…⁵ $75-1…⁶ $100-…⁷
    ##   <chr>            <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>
    ## 1 Agnostic            27      34      60      81      76     137     122     109
    ## 2 Atheist             12      27      37      52      35      70      73      59
    ## 3 Buddhist            27      21      30      34      33      58      62      39
    ## 4 Catholic           418     617     732     670     638    1116     949     792
    ## 5 Don’t know/re…      15      14      15      11      10      35      21      17
    ## 6 Evangelical P…     575     869    1064     982     881    1486     949     723
    ## # … with 2 more variables: `>150k` <dbl>, `Don't know/refused` <dbl>, and
    ## #   abbreviated variable names ¹​`$10-20k`, ²​`$20-30k`, ³​`$30-40k`, ⁴​`$40-50k`,
    ## #   ⁵​`$50-75k`, ⁶​`$75-100k`, ⁷​`$100-150k`

-   Agrupar todas las variables que tengan que ver con la cuantía
    monetaria desde *\<$10k* hasta *Don’t know/refused* en dos
    variables: “Income”, “N_People”.

``` r
tidy.df <- gather(relig_income, "Income", "N_People", 2:ncol(relig_income))
head(tidy.df)
```

    ## # A tibble: 6 × 3
    ##   religion           Income N_People
    ##   <chr>              <chr>     <dbl>
    ## 1 Agnostic           <$10k        27
    ## 2 Atheist            <$10k        12
    ## 3 Buddhist           <$10k        27
    ## 4 Catholic           <$10k       418
    ## 5 Don’t know/refused <$10k        15
    ## 6 Evangelical Prot   <$10k       575

-   Convierte a factor las variables: religion e Income.

``` r
tidy.df$religion <- as.factor(tidy.df$religion)
tidy.df$Income <- as.factor(tidy.df$Income)
```

-   Agrupa el dataset resultante por religion, sobre esta agrupación,
    muestra la estadística “media_creyentes” que contenga la media de la
    variable “N_People”, finalmente, ordena de forma descendente dicha
    media.

``` r
tidy.df %>% group_by(religion) %>% summarise(media_creyentes = mean(N_People)) %>% arrange(desc(media_creyentes))
```

    ## # A tibble: 18 × 2
    ##    religion                media_creyentes
    ##    <fct>                             <dbl>
    ##  1 Evangelical Prot                  947. 
    ##  2 Catholic                          805. 
    ##  3 Mainline Prot                     747  
    ##  4 Unaffiliated                      371. 
    ##  5 Historically Black Prot           200. 
    ##  6 Agnostic                           82.6
    ##  7 Jewish                             68.2
    ##  8 Mormon                             58.1
    ##  9 Atheist                            51.5
    ## 10 Other Faiths                       44.9
    ## 11 Buddhist                           41.1
    ## 12 Orthodox                           36.3
    ## 13 Don’t know/refused                 27.2
    ## 14 Hindu                              25.7
    ## 15 Jehovah's Witness                  21.5
    ## 16 Other Christian                    12.9
    ## 17 Muslim                             11.6
    ## 18 Other World Religions               4.2

-   Crea una nueva variable en el dataset con nombre “media_creyentes”
    cuyo valor sea: el valor de “N_People” entre la longitud del vector
    (redondea la columna a dos decimales).

``` r
# tidy.df$media_creyentes <- round(tidy.df$N_People/length(tidy.df$N_People), 2)
tidy.df <- mutate(tidy.df, media_creyentes = round(N_People/length(N_People),2))
head(tidy.df)
```

    ## # A tibble: 6 × 4
    ##   religion           Income N_People media_creyentes
    ##   <fct>              <fct>     <dbl>           <dbl>
    ## 1 Agnostic           <$10k        27            0.15
    ## 2 Atheist            <$10k        12            0.07
    ## 3 Buddhist           <$10k        27            0.15
    ## 4 Catholic           <$10k       418            2.32
    ## 5 Don’t know/refused <$10k        15            0.08
    ## 6 Evangelical Prot   <$10k       575            3.19

-   Obtén un nuevo dataset, que sea el resultado de filtrar la variable
    “N_People” por todos los valores de la media de sí misma y que
    además la variable “Income” no contenga el valor “Don’t
    know/refused”. Tras filtrar el dataset, obtén una muestra del 30%.

``` r
new.relig <- filter(tidy.df, N_People > mean(N_People), Income != "Don't know/refused") %>% sample_frac(size=0.3)
```

``` r
new.relig
```

    ## # A tibble: 12 × 4
    ##    religion                Income   N_People media_creyentes
    ##    <fct>                   <fct>       <dbl>           <dbl>
    ##  1 Unaffiliated            $10-20k       299            1.66
    ##  2 Unaffiliated            $75-100k      407            2.26
    ##  3 Mainline Prot           $75-100k      939            5.22
    ##  4 Mainline Prot           $30-40k       655            3.64
    ##  5 Unaffiliated            $30-40k       365            2.03
    ##  6 Mainline Prot           <$10k         289            1.61
    ##  7 Evangelical Prot        $75-100k      949            5.27
    ##  8 Evangelical Prot        $30-40k       982            5.46
    ##  9 Catholic                $10-20k       617            3.43
    ## 10 Unaffiliated            $50-75k       528            2.93
    ## 11 Mainline Prot           $50-75k      1107            6.15
    ## 12 Historically Black Prot $20-30k       236            1.31

-   Finalmente, sobre el dataset anterior, selecciona las columnas
    “Income” y “religion”, agrupa estas variables por la variable
    “Income”, sobre esta agrupación, muestra el número de todas las
    religiones diferentes para cada valor de “Income”, en último lugar,
    ordena el valor de la estadística realizada de menor a mayor.

``` r
new.relig %>% select(Income, religion) %>% group_by(Income) %>% summarise(Income_religiones=n()) %>% arrange(Income_religiones)
```

    ## # A tibble: 6 × 2
    ##   Income   Income_religiones
    ##   <fct>                <int>
    ## 1 $20-30k                  1
    ## 2 <$10k                    1
    ## 3 $10-20k                  2
    ## 4 $50-75k                  2
    ## 5 $30-40k                  3
    ## 6 $75-100k                 3
