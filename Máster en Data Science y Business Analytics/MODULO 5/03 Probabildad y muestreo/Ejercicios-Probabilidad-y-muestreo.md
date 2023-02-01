# I. PROBLEMA MUESTREO

5 000 restaurantes han comprado fruta de temporada en el último mes a
unos grandes almacenes. Se desea tomar una muestra para estimar la
compra media. Se quiere que dicha estimación tenga un error máximo de
dos kilos y se busca un nivel de confianza del 90 %. Con una muestra
piloto de 40 restaurantes, se ha obtenido una media de 168,5 kilos con
una desviación típica de 20,5 kilos. ¿Qué tamaño de muestra se debe
escoger?

``` r
#Datos
N=5000
B=2 
NS=0.10
NC=1-NS
k=qnorm(1-NS/2)
s2=(20.5)^2
D=B^2/k^2
#formula para el tamano de muestra (cuando se estima la media)
n=(N*s2)/((N-1)*D+s2)
#El tamano de muestra es :
round(n)
```

    ## [1] 269

![](images/image-1762281286.png)

``` r
# Error máximo
Emax <- 2
# Intervalo de confianza (nivel de confianza)
IC <- 0.9
# Desviacion típica
sigma <- 20.5
# Tamaño población
N <- 5000
#Valor Z alpha medio
z.student <- 1-(1-IC)/2
z.student
```

    ## [1] 0.95

``` r
z.alfa.medios <- qnorm(z.student)
z.alfa.medios
```

    ## [1] 1.644854

``` r
#Fórmula muestreo (estimando la media)
n <- (N*z.alfa.medios^2*sigma^2)/((N-1)*Emax^2+z.alfa.medios^2*sigma^2)
round(n)
```

    ## [1] 269

# II. PROBLEMA MUESTREO

De 3 675 clientes registrados en una entidad financiera se escogen
aleatoriamente a 147 y se les consulta si fueron a la entidad por
consejo de alguien. De los 147 encuestados, 48 contestan que sí. Se
pide:

-   Hacer una estimación de la proporción de las 3 675 personas que
    fueron por consejo de alguien.

``` r
#datos
N=3675
n=147
a=48
NS=0.05;NC=1-NS # Se toma un nivel de confianza del 95%
k=qnorm(1-NS/2);round(k,3)#k=f(z)
```

    ## [1] 1.96

``` r
## [1] 1.96
#inciso a
#la proporcion de personas que vinieron por consejo de alguien.
p=a/n
p
```

    ## [1] 0.3265306

``` r
#la proporcion de personas que no vinieron por consejo de alguien.
q=1-p
q
```

    ## [1] 0.6734694

-   Determinar el error en la estimación asumiendo un nivel de confianza
    adecuado.

``` r
#varianza de la proporcion
vp=((p*q)/n)*((N-n)/N)
vp
```

    ## [1] 0.001436136

``` r
#error de la estimacion (desv estandar= K*raiz cuadrada de la varianza)
B=k*sqrt(vp)
B
```

    ## [1] 0.07427556

-   ¿Qué opinión tiene sobre el valor obtenido para dicho error?

``` r
#Error relativo=B/p
ER=(B/p)
ER
```

    ## [1] 0.2274689

``` r
if ((B/p)>0.10) ("La estimacion no es confiable, se sugiere aumentar n") else ("La estimacion es confiable")
```

    ## [1] "La estimacion no es confiable, se sugiere aumentar n"

# 3. Investiga las funciones y paquetes más relevantes utilizadas en muestreo

Propuesta solución:

<https://cran.r-project.org/web/packages/survey/survey.pdf>

Selección de muestras simples con dplyr:

Una forma mós sencilla de obtener una muestra es con el paquete
dplyr.Este paquete es sumamente útil para el tratamiento de datos,
adicionalmente contiene una función para obtener muestras simples de un
data frame:

``` r
# library(dplyr)
# # #Muestra sin reemplazo
# # 
# flightsmuestra2<- flights %>%
#    sample_n(size=n,replace=FALSE)
#  head(flightsmuestra2)
```

Muestra con peso:

``` r
#flightsmuestra3<- flights %>%
#  sample_n(size=n,weight=Freq)
#head(flightsmuestra3)
```

Muestra con una proporción de casos:

``` r
#flightsmuestra4<- flights %>%
#  sample_frac(0.05)
#head(flightsmuestra4)
#dim(flightsmuestra4)
```

Selección de muestras sistemáticas:

Para el ejemplo del muestreo sistemático utilizaremos la función
sys.sample del paquete SamplingUtil.

``` r
#flightsmuestra5<- sys.sample(N=nrow(flights),n=300)
#flightsmuestra5
```

# 4. Problema probabilidad

-   1.  Casi todas las distribuciones admiten parámetros adicionales.
        Por ejemplo, la media y la desviación estándar para la
        distribución normal. Consulta la ayuda de dnorm para ver cómo
        muestrear una variable aleatoria normal con media 100 y
        desviación estándar 20.

-   1.  Obtengamos 10 valores aleatorios que vienen de esa población (mu
        = 100, SD = 20)

-   1.  Una vez obtenida la muestra (muestra), veamos el valor de la
        media y la desviación estándar.

-   1.  Siguiendo con rnorm tomemos una muestra más y dibujemos el
        histograma y la curva de densidad.

-   e)?Qué sucede si incrementamos la muestra?

-   Solución a:

``` r
help(Distributions)
```

    ## starting httpd help server ... done

``` r
help(dnorm)
curve(dnorm(x, mean = 100, sd = 20),
      xlim = c(20, 180))
 
legend("topright",
       c(paste("mu =", 100), paste("SD =", 20)),
       bty = "n")
```

![](Ejercicios-Probabilidad-y-muestreo_files/figure-markdown_github/unnamed-chunk-10-1.png)

-   Solución b:

``` r
# n es el número de valores a obtener.
muestra <- rnorm(10, 100, 20)
muestra
```

    ##  [1] 132.00372 115.15580  80.65752  79.52331  83.96478 101.76518  89.97912
    ##  [8]  90.46034  94.89419 101.31894

-   Solución c:

``` r
# mu y SD son la media y la desviación estándar
# de la población.
mean(muestra)
```

    ## [1] 96.97229

``` r
sd(muestra)
```

    ## [1] 16.44914

-   Solución d:

``` r
muestra2 <- rnorm(10, 100, 20)
hist(muestra2, freq = F)
lines(density(muestra2), lty = 2)
```

![](Ejercicios-Probabilidad-y-muestreo_files/figure-markdown_github/unnamed-chunk-13-1.png)

-   Solución e: Si incrementamos el tamaño de la muestra nos acercaremos
    más a la realidad (la población). Sin, embargo, y como veremos más
    adelante, no siempre es necesario tener un tamaño “grande” de la
    muestra para tener una buena descripción de la población.

El punto de esta entrada es que conozcas que se pueden obtener valores
aleatorios que vienen de una población con una distribución específica,
en esta caso, una distribución normal.

``` r
muestra7 <- rnorm(100, 100, 20)
plot(density(muestra7))
```

![](Ejercicios-Probabilidad-y-muestreo_files/figure-markdown_github/unnamed-chunk-14-1.png)

# 5. Problema probabilidad

    a)  La probabilidad de venta de un producto en una tienda es 0.52. En los próximos mil clientes que entren en la tienda, vamos a calcular la probabilidad de que haya más de 540 ventas

    b)  ¿Y si queremos pensar en las 300 de la marca? ¿En qué fracción de esas tiendas se supera la cifra de 540 ventas?

-   Solución a:

Por un lado podríamos usar la distribución binomial, con n=1000,p=0.52
para calcular ese valor. Pero lo que vamos a hacer aquí es simular esas
1000 entradas a la tienda en y ver cuantas ventas obtenemos.

``` r
rbinom(1, 1000, 0.52)
```

    ## [1] 532

-   Solución b:

``` r
#Usando replicate.
numventas = 300
(ventas = replicate(n = numventas, {
  rbinom(n = 1, size = 1000, prob = 0.52)
}))
```

    ##   [1] 521 527 498 493 513 513 523 512 534 535 505 515 540 525 540 504 533 516
    ##  [19] 536 541 548 544 514 505 521 501 523 517 524 513 523 538 530 506 527 520
    ##  [37] 525 515 511 497 560 502 495 513 502 545 530 534 497 518 534 534 519 503
    ##  [55] 537 510 520 535 524 530 524 543 496 497 500 525 529 510 534 494 539 506
    ##  [73] 489 536 503 545 529 498 513 538 533 523 528 510 538 511 515 515 506 499
    ##  [91] 497 542 534 517 522 534 502 543 506 531 505 509 530 522 502 529 495 528
    ## [109] 508 502 541 511 530 505 513 547 504 547 524 538 490 519 503 542 495 535
    ## [127] 513 532 537 524 531 529 528 513 522 517 522 514 496 494 515 517 515 518
    ## [145] 522 525 492 504 486 498 550 493 537 518 526 505 521 531 537 519 515 513
    ## [163] 545 547 489 539 522 533 528 494 515 514 535 508 528 517 535 499 529 542
    ## [181] 499 527 523 502 523 557 525 526 540 525 520 498 495 521 532 535 506 514
    ## [199] 516 518 523 527 550 559 533 521 512 514 522 527 520 509 512 498 512 494
    ## [217] 495 515 498 531 530 509 518 490 528 521 509 529 557 542 531 515 537 519
    ## [235] 514 536 529 500 510 539 523 542 501 520 497 504 526 536 495 509 502 499
    ## [253] 526 506 528 521 497 518 528 544 531 506 505 537 544 525 520 518 543 522
    ## [271] 519 515 518 527 518 513 528 538 514 529 546 525 511 511 516 514 536 531
    ## [289] 536 531 547 522 523 544 515 527 507 526 515 524

``` r
# Nota: Se podría hacer una simulación mucho más "básica" usando rbinom
# ventas<-rbinom(300,1000,0.52)
#Proporción
sum(ventas > 540) / numventas
```

    ## [1] 0.09666667

``` r
#La probabilidad calculada con la binomial es:
1-pbinom(540, size = 1000, prob = 0.52)
```

    ## [1] 0.09715473

Nota: Se podría hacer una simulación mucho más “básica” usando rbinom
