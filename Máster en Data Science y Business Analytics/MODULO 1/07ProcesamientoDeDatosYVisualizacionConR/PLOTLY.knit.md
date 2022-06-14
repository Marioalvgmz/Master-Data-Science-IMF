---
title: "PLOTLY"
output:
  html_document:
    df_print: paged
  word_document: default
autor: Juan Manuel Moreno
always_allow_html: true
---

**Plotly** es un paquete destinado a la creación de gráficos interactivos, durante esta sesión, se mostrará tanto su instalación como realizar algunos gráficos simples.

Para su instalación, simplemente instalamos el paquete **`plotly`**.

```r
# install.packages("plotly")

library(plotly)
```

```
## Loading required package: ggplot2
```

```
## 
## Attaching package: 'plotly'
```

```
## The following object is masked from 'package:ggplot2':
## 
##     last_plot
```

```
## The following object is masked from 'package:stats':
## 
##     filter
```

```
## The following object is masked from 'package:graphics':
## 
##     layout
```

Las gráficas pueden mostrarse a través de RStudio o en el navegador web. Comenzaremos cargando la librería y obteniendo unos vectores para realizar la primera visualización.

Para realizar una visualización en plotly, siempre tenemos que utilizar la función **`plot_ly`** y pasar nuestros parámetros para dibujar los ejes x e y. En plotly, escogeremos el tipo de visualización a través del parámetro **type**.


```r
x <- c(1, 2, 3, 8, 7, 5, 6)
y <- c(4, 5, 6, 2, 10 ,12, 5)
```


## Diagrama de dispersión


```r
fig <- plot_ly (
  x = x,
  y = y,
  type = "scatter"
)

fig
```

```
## No scatter mode specifed:
##   Setting the mode to markers
##   Read more about this attribute -> https://plotly.com/r/reference/#scatter-mode
```

```{=html}
<div id="htmlwidget-fcd650725781575c49e3" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-fcd650725781575c49e3">{"x":{"visdat":{"32c851fb4d80":["function () ","plotlyVisDat"]},"cur_data":"32c851fb4d80","attrs":{"32c851fb4d80":{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"type":"scatter","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

Además del tipo de gráfica, en plotly (para algunos tipos de visualización), podemos elegir el modo, es decir, si existirá algún patrón de unión entre las observaciones que vayamos a pintar, por ejemplo: puntos y líneas, este parámetro es **`mode`**.


```r
fig.sizes <- plot_ly (
  x = x,
  y = y,
  type = "scatter",
  mode = "markers",
  size = 3,
  alpha = 0.9
)

fig.sizes
```

```{=html}
<div id="htmlwidget-02b6e80b34227740eb41" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-02b6e80b34227740eb41">{"x":{"visdat":{"32c89f6b5d":["function () ","plotlyVisDat"]},"cur_data":"32c89f6b5d","attrs":{"32c89f6b5d":{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"mode":"markers","size":3,"alpha":0.9,"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"mode":"markers","type":"scatter","marker":{"color":"rgba(31,119,180,0.9)","size":[55,55,55,55,55,55,55],"sizemode":"area","line":{"color":"rgba(31,119,180,1)"}},"textfont":{"size":55},"error_y":{"color":"rgba(31,119,180,0.9)","width":55},"error_x":{"color":"rgba(31,119,180,0.9)","width":55},"line":{"color":"rgba(31,119,180,0.9)","width":55},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

```r
fig.line <- plot_ly (
  x = x,
  y = y,
  type = "scatter",
  mode = "lines"
)

fig.line 
```

```{=html}
<div id="htmlwidget-e5415d41eb2541a6b765" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e5415d41eb2541a6b765">{"x":{"visdat":{"32c84e254549":["function () ","plotlyVisDat"]},"cur_data":"32c84e254549","attrs":{"32c84e254549":{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"mode":"lines","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

Podemos seleccionar ambos modos con *lines+markers*.

```r
fig.line <- plot_ly (
  x = x,
  y = y,
  type = "scatter",
  mode = "lines+markers"
)

fig.line 
```

```{=html}
<div id="htmlwidget-b342356b45ddbfdf532a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-b342356b45ddbfdf532a">{"x":{"visdat":{"32c84aca6cf6":["function () ","plotlyVisDat"]},"cur_data":"32c84aca6cf6","attrs":{"32c84aca6cf6":{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"mode":"lines+markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"mode":"lines+markers","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```


```r
fig <- plot_ly(
  data = iris, x = ~Sepal.Width, y = ~Petal.Width,
  type = "scatter",
  color = ~Species, size = ~Sepal.Width
)

fig
```

```
## No scatter mode specifed:
##   Setting the mode to markers
##   Read more about this attribute -> https://plotly.com/r/reference/#scatter-mode
```

```
## Warning: `line.width` does not currently support multiple values.

## Warning: `line.width` does not currently support multiple values.

## Warning: `line.width` does not currently support multiple values.
```

```{=html}
<div id="htmlwidget-ff38b4d92a36bf0bd07b" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-ff38b4d92a36bf0bd07b">{"x":{"visdat":{"32c853093dab":["function () ","plotlyVisDat"]},"cur_data":"32c853093dab","attrs":{"32c853093dab":{"x":{},"y":{},"color":{},"size":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"Sepal.Width"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Petal.Width"},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[3.5,3,3.2,3.1,3.6,3.9,3.4,3.4,2.9,3.1,3.7,3.4,3,3,4,4.4,3.9,3.5,3.8,3.8,3.4,3.7,3.6,3.3,3.4,3,3.4,3.5,3.4,3.2,3.1,3.4,4.1,4.2,3.1,3.2,3.5,3.6,3,3.4,3.5,2.3,3.2,3.5,3.8,3,3.8,3.2,3.7,3.3],"y":[0.2,0.2,0.2,0.2,0.2,0.4,0.3,0.2,0.2,0.1,0.2,0.2,0.1,0.1,0.2,0.4,0.4,0.3,0.3,0.3,0.2,0.4,0.2,0.5,0.2,0.2,0.4,0.2,0.2,0.2,0.2,0.4,0.1,0.2,0.2,0.2,0.2,0.1,0.2,0.2,0.3,0.3,0.2,0.6,0.4,0.3,0.2,0.2,0.2,0.2],"type":"scatter","mode":"markers","name":"setosa","marker":{"color":"rgba(102,194,165,1)","size":[66.25,47.5,55,51.25,70,81.25,62.5,62.5,43.75,51.25,73.75,62.5,47.5,47.5,85,100,81.25,66.25,77.5,77.5,62.5,73.75,70,58.75,62.5,47.5,62.5,66.25,62.5,55,51.25,62.5,88.75,92.5,51.25,55,66.25,70,47.5,62.5,66.25,21.25,55,66.25,77.5,47.5,77.5,55,73.75,58.75],"sizemode":"area","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)","size":[66.25,47.5,55,51.25,70,81.25,62.5,62.5,43.75,51.25,73.75,62.5,47.5,47.5,85,100,81.25,66.25,77.5,77.5,62.5,73.75,70,58.75,62.5,47.5,62.5,66.25,62.5,55,51.25,62.5,88.75,92.5,51.25,55,66.25,70,47.5,62.5,66.25,21.25,55,66.25,77.5,47.5,77.5,55,73.75,58.75]},"error_y":{"color":"rgba(102,194,165,1)","width":[]},"error_x":{"color":"rgba(102,194,165,1)","width":[]},"line":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[3.2,3.2,3.1,2.3,2.8,2.8,3.3,2.4,2.9,2.7,2,3,2.2,2.9,2.9,3.1,3,2.7,2.2,2.5,3.2,2.8,2.5,2.8,2.9,3,2.8,3,2.9,2.6,2.4,2.4,2.7,2.7,3,3.4,3.1,2.3,3,2.5,2.6,3,2.6,2.3,2.7,3,2.9,2.9,2.5,2.8],"y":[1.4,1.5,1.5,1.3,1.5,1.3,1.6,1,1.3,1.4,1,1.5,1,1.4,1.3,1.4,1.5,1,1.5,1.1,1.8,1.3,1.5,1.2,1.3,1.4,1.4,1.7,1.5,1,1.1,1,1.2,1.6,1.5,1.6,1.5,1.3,1.3,1.3,1.2,1.4,1.2,1,1.3,1.2,1.3,1.3,1.1,1.3],"type":"scatter","mode":"markers","name":"versicolor","marker":{"color":"rgba(252,141,98,1)","size":[55,55,51.25,21.25,40,40,58.75,25,43.75,36.25,10,47.5,17.5,43.75,43.75,51.25,47.5,36.25,17.5,28.75,55,40,28.75,40,43.75,47.5,40,47.5,43.75,32.5,25,25,36.25,36.25,47.5,62.5,51.25,21.25,47.5,28.75,32.5,47.5,32.5,21.25,36.25,47.5,43.75,43.75,28.75,40],"sizemode":"area","line":{"color":"rgba(252,141,98,1)"}},"textfont":{"color":"rgba(252,141,98,1)","size":[55,55,51.25,21.25,40,40,58.75,25,43.75,36.25,10,47.5,17.5,43.75,43.75,51.25,47.5,36.25,17.5,28.75,55,40,28.75,40,43.75,47.5,40,47.5,43.75,32.5,25,25,36.25,36.25,47.5,62.5,51.25,21.25,47.5,28.75,32.5,47.5,32.5,21.25,36.25,47.5,43.75,43.75,28.75,40]},"error_y":{"color":"rgba(252,141,98,1)","width":[]},"error_x":{"color":"rgba(252,141,98,1)","width":[]},"line":{"color":"rgba(252,141,98,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[3.3,2.7,3,2.9,3,3,2.5,2.9,2.5,3.6,3.2,2.7,3,2.5,2.8,3.2,3,3.8,2.6,2.2,3.2,2.8,2.8,2.7,3.3,3.2,2.8,3,2.8,3,2.8,3.8,2.8,2.8,2.6,3,3.4,3.1,3,3.1,3.1,3.1,2.7,3.2,3.3,3,2.5,3,3.4,3],"y":[2.5,1.9,2.1,1.8,2.2,2.1,1.7,1.8,1.8,2.5,2,1.9,2.1,2,2.4,2.3,1.8,2.2,2.3,1.5,2.3,2,2,1.8,2.1,1.8,1.8,1.8,2.1,1.6,1.9,2,2.2,1.5,1.4,2.3,2.4,1.8,1.8,2.1,2.4,2.3,1.9,2.3,2.5,2.3,1.9,2,2.3,1.8],"type":"scatter","mode":"markers","name":"virginica","marker":{"color":"rgba(141,160,203,1)","size":[58.75,36.25,47.5,43.75,47.5,47.5,28.75,43.75,28.75,70,55,36.25,47.5,28.75,40,55,47.5,77.5,32.5,17.5,55,40,40,36.25,58.75,55,40,47.5,40,47.5,40,77.5,40,40,32.5,47.5,62.5,51.25,47.5,51.25,51.25,51.25,36.25,55,58.75,47.5,28.75,47.5,62.5,47.5],"sizemode":"area","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)","size":[58.75,36.25,47.5,43.75,47.5,47.5,28.75,43.75,28.75,70,55,36.25,47.5,28.75,40,55,47.5,77.5,32.5,17.5,55,40,40,36.25,58.75,55,40,47.5,40,47.5,40,77.5,40,40,32.5,47.5,62.5,51.25,47.5,51.25,51.25,51.25,36.25,55,58.75,47.5,28.75,47.5,62.5,47.5]},"error_y":{"color":"rgba(141,160,203,1)","width":[]},"error_x":{"color":"rgba(141,160,203,1)","width":[]},"line":{"color":"rgba(141,160,203,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```


```r
vec.1 <- c(1:100)
random_y <- rnorm(100, mean = 0)

data <- data.frame("norm_1" = vec.1, 
                   "norm_2" =random_y)

fig <- plot_ly(data, x = ~norm_1, y = ~norm_2, 
               type = 'scatter', 
               mode = 'lines')

fig
```

```{=html}
<div id="htmlwidget-1a4c073ef4d0ef6371c8" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1a4c073ef4d0ef6371c8">{"x":{"visdat":{"32c846bcf39":["function () ","plotlyVisDat"]},"cur_data":"32c846bcf39","attrs":{"32c846bcf39":{"x":{},"y":{},"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"norm_1"},"yaxis":{"domain":[0,1],"automargin":true,"title":"norm_2"},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,91,92,93,94,95,96,97,98,99,100],"y":[1.13463563760014,0.78291078595873,-0.0816909026315771,1.59101909481443,1.79854662013406,-0.4195704076,-1.4571576561821,-0.181524223837382,0.162796959359917,2.06197071564514,-0.409851726736578,1.29054011198904,-0.988972557715109,-1.66331546458228,1.60762359651743,-1.32543585489715,0.720511333722072,0.992805632129756,0.32803269243849,-0.042791979549526,2.65303864247166,-1.00030602176161,-0.159360386126995,0.336747004721721,0.0554361523267038,-0.53014475808229,1.04138671764629,-0.563119305592779,-0.682727745409597,1.30661489308116,-1.27482709085405,0.0526984372070243,0.299936368318085,-0.606666817481905,-0.630630020673137,0.65731042651462,1.07534208986513,0.637169063724756,-2.21194353783773,0.399975837230022,0.348845617205062,-0.471252617895452,-0.387638463317806,0.15811954347302,2.27674539287635,-0.620889699766522,0.132667959939429,-0.193477042439893,-1.09740574310075,1.43073736472227,-0.801011514021171,-1.26462540219791,0.920321177032846,0.241692116365923,-0.242947670820931,1.97124600084556,2.41283282441574,1.24848594371486,1.05094706318726,0.334256171876419,-2.52663959094569,0.0482388509671241,-0.601017419355992,1.13089778916031,-0.334402359197394,-0.771498054112139,0.993649667284302,-1.50706138665661,-0.745737256409991,0.135095631855921,0.355756494981025,-0.941271549438789,0.0852679472517819,-1.06216141705858,-0.978658903787656,0.443580766561786,0.464242729851409,1.0823276056163,-0.570735744129867,0.683328170638606,-0.762827677257073,0.640869847016047,0.959201920018942,0.87772135135534,-0.344624564578402,-0.00884941933332602,0.57158607556221,-1.01688754268375,0.925188769001977,-0.686231409642974,0.683101326682086,-0.968300429816294,-0.474266303579599,-2.21441708182239,0.00760312080846657,-0.558558245394981,-1.03826427923638,1.79573179934545,-0.38047295893557,0.103099857897511],"mode":"lines","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```


## Diagrama de barras


```r
fig.bar <- plot_ly (
  x = x,
  y = y,
  type = "bar"
)

fig.bar 
```

```{=html}
<div id="htmlwidget-fac9174ad158811baedf" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-fac9174ad158811baedf">{"x":{"visdat":{"32c83b831531":["function () ","plotlyVisDat"]},"cur_data":"32c83b831531","attrs":{"32c83b831531":{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3,8,7,5,6],"y":[4,5,6,2,10,12,5],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

Como podemos comprobar, el parámetro x es tomado como índice y por ello, el valor 4 está vacío, vemos que este hecho, no afecta a los diagramas de barras con variables categóricas.


```r
fig <- plot_ly(
  x = c("Manzanas", "Naranajas", "Sandías"),
  y = c(300, 245, 283),
  name = "Ventas",
  type = "bar"
)

fig
```

```{=html}
<div id="htmlwidget-e4e3739090dd72703af6" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e4e3739090dd72703af6">{"x":{"visdat":{"32c82e693e54":["function () ","plotlyVisDat"]},"cur_data":"32c82e693e54","attrs":{"32c82e693e54":{"x":["Manzanas","Naranajas","Sandías"],"y":[300,245,283],"name":"Ventas","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":[],"type":"category","categoryorder":"array","categoryarray":["Manzanas","Naranajas","Sandías"]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":["Manzanas","Naranajas","Sandías"],"y":[300,245,283],"name":"Ventas","type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

Para evitar el problema del primer diagrama de barras, es aconsejable utilizar dataframes

```r
fig.bar <- plot_ly (
  data = iris,
  x = ~Sepal.Length,
  y = ~Sepal.Width,
  type = "bar",
  color = ~Species
)

fig.bar 
```

```{=html}
<div id="htmlwidget-1c03cd8cd05f70144134" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1c03cd8cd05f70144134">{"x":{"visdat":{"32c878c5284b":["function () ","plotlyVisDat"]},"cur_data":"32c878c5284b","attrs":{"32c878c5284b":{"x":{},"y":{},"color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"Sepal.Length"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Sepal.Width"},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[5.1,4.9,4.7,4.6,5,5.4,4.6,5,4.4,4.9,5.4,4.8,4.8,4.3,5.8,5.7,5.4,5.1,5.7,5.1,5.4,5.1,4.6,5.1,4.8,5,5,5.2,5.2,4.7,4.8,5.4,5.2,5.5,4.9,5,5.5,4.9,4.4,5.1,5,4.5,4.4,5,5.1,4.8,5.1,4.6,5.3,5],"y":[3.5,3,3.2,3.1,3.6,3.9,3.4,3.4,2.9,3.1,3.7,3.4,3,3,4,4.4,3.9,3.5,3.8,3.8,3.4,3.7,3.6,3.3,3.4,3,3.4,3.5,3.4,3.2,3.1,3.4,4.1,4.2,3.1,3.2,3.5,3.6,3,3.4,3.5,2.3,3.2,3.5,3.8,3,3.8,3.2,3.7,3.3],"type":"bar","name":"setosa","marker":{"color":"rgba(102,194,165,1)","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[7,6.4,6.9,5.5,6.5,5.7,6.3,4.9,6.6,5.2,5,5.9,6,6.1,5.6,6.7,5.6,5.8,6.2,5.6,5.9,6.1,6.3,6.1,6.4,6.6,6.8,6.7,6,5.7,5.5,5.5,5.8,6,5.4,6,6.7,6.3,5.6,5.5,5.5,6.1,5.8,5,5.6,5.7,5.7,6.2,5.1,5.7],"y":[3.2,3.2,3.1,2.3,2.8,2.8,3.3,2.4,2.9,2.7,2,3,2.2,2.9,2.9,3.1,3,2.7,2.2,2.5,3.2,2.8,2.5,2.8,2.9,3,2.8,3,2.9,2.6,2.4,2.4,2.7,2.7,3,3.4,3.1,2.3,3,2.5,2.6,3,2.6,2.3,2.7,3,2.9,2.9,2.5,2.8],"type":"bar","name":"versicolor","marker":{"color":"rgba(252,141,98,1)","line":{"color":"rgba(252,141,98,1)"}},"textfont":{"color":"rgba(252,141,98,1)"},"error_y":{"color":"rgba(252,141,98,1)"},"error_x":{"color":"rgba(252,141,98,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[6.3,5.8,7.1,6.3,6.5,7.6,4.9,7.3,6.7,7.2,6.5,6.4,6.8,5.7,5.8,6.4,6.5,7.7,7.7,6,6.9,5.6,7.7,6.3,6.7,7.2,6.2,6.1,6.4,7.2,7.4,7.9,6.4,6.3,6.1,7.7,6.3,6.4,6,6.9,6.7,6.9,5.8,6.8,6.7,6.7,6.3,6.5,6.2,5.9],"y":[3.3,2.7,3,2.9,3,3,2.5,2.9,2.5,3.6,3.2,2.7,3,2.5,2.8,3.2,3,3.8,2.6,2.2,3.2,2.8,2.8,2.7,3.3,3.2,2.8,3,2.8,3,2.8,3.8,2.8,2.8,2.6,3,3.4,3.1,3,3.1,3.1,3.1,2.7,3.2,3.3,3,2.5,3,3.4,3],"type":"bar","name":"virginica","marker":{"color":"rgba(141,160,203,1)","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

## Añadir texto a una gráfica.

A una gráfica ya existente, le agregamos la función **`layout`** a la cuál le pasaremos los siguientes parámetros:

* **title**: Título de la gráfica.
* **xaxis**: Lista con el atributo **title**, si queremos desactivar este componente otorgaremos valor FALSE al atributo showgrid.
* **yaxis**: Lista con el atributo **title**, si queremos desactivar este componente otorgaremos valor FALSE al atributo showgrid.


```r
x <- c(1, 2, 3, 8, 7, 5, 6, 2, 4, 14, 16, 19, 23, 5, 8)
y <- c(4, 5, 6, 2, 10 ,12, 5, 9, 10, 11, 23, 4, 7, 6, 8)
f <- factor(c("VALUE1", "VALUE2", "VALUE1", "VALUE1", "VALUE2", "VALUE1", "VALUE1", 
              "VALUE1", "VALUE2", "VALUE1", "VALUE1", "VALUE2", "VALUE1", "VALUE1", "VALUE2"))
z <- sample(15:30, 15, replace = F)
d <- data.frame("x" = x, "y" = y, "f" = f, "z" = z)

fig <- plot_ly(iris, x = ~x, y = ~y, 
               text = ~f, color = ~f,
               type = 'scatter', mode = 'markers', 
        marker = list(size = ~z, opacity = 0.5))

fig <- fig %>% layout(title = 'X ~ Y',
         xaxis = list(title = "Vector X"),
         yaxis = list(title = "Vector Y"))

fig
```

```
## Warning in RColorBrewer::brewer.pal(N, "Set2"): minimal value for n is 3, returning requested palette with 3 different levels

## Warning in RColorBrewer::brewer.pal(N, "Set2"): minimal value for n is 3, returning requested palette with 3 different levels
```

```{=html}
<div id="htmlwidget-d37c4ad6206e4ba090a2" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-d37c4ad6206e4ba090a2">{"x":{"visdat":{"32c8c5f7b99":["function () ","plotlyVisDat"]},"cur_data":"32c8c5f7b99","attrs":{"32c8c5f7b99":{"x":{},"y":{},"text":{},"mode":"markers","marker":{"size":{},"opacity":0.5},"color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"X ~ Y","xaxis":{"domain":[0,1],"automargin":true,"title":"Vector X"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Vector Y"},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,3,8,5,6,2,14,16,23,5],"y":[4,6,2,12,5,9,11,23,7,6],"text":["VALUE1","VALUE1","VALUE1","VALUE1","VALUE1","VALUE1","VALUE1","VALUE1","VALUE1","VALUE1"],"mode":"markers","marker":{"color":"rgba(102,194,165,1)","size":[27,20,18,28,19,29,17,22,16,21],"opacity":0.5,"line":{"color":"rgba(102,194,165,1)"}},"type":"scatter","name":"VALUE1","textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"line":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[2,7,4,19,8],"y":[5,10,10,4,8],"text":["VALUE2","VALUE2","VALUE2","VALUE2","VALUE2"],"mode":"markers","marker":{"color":"rgba(141,160,203,1)","size":[25,15,24,23,26],"opacity":0.5,"line":{"color":"rgba(141,160,203,1)"}},"type":"scatter","name":"VALUE2","textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"line":{"color":"rgba(141,160,203,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

## Histograma


```r
fig <- plot_ly(x = ~rnorm(500),
               alpha = 0.6, 
               type = "histogram")

fig
```

```{=html}
<div id="htmlwidget-2642a7f8b7075a7514c1" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-2642a7f8b7075a7514c1">{"x":{"visdat":{"32c83ad443cd":["function () ","plotlyVisDat"]},"cur_data":"32c83ad443cd","attrs":{"32c83ad443cd":{"x":{},"alpha":0.6,"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"histogram"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"rnorm(500)"},"yaxis":{"domain":[0,1],"automargin":true},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[0.981800454653981,-0.829925909292983,-1.04480608228712,-0.848437282060164,-0.696655073124183,0.294581116627918,-0.18516022248857,0.315706863614546,0.690309387740409,-0.677086692051371,-1.45959619149337,0.76659897823089,-0.0372484741633473,1.91894900323893,-2.60595034796228,1.12141622154345,0.138127097012089,-0.955220278446769,0.269063346687304,-0.77920154216073,-1.27138189701029,0.24923073691881,-0.386765146317195,1.15958800438226,-0.0621582592556939,0.249629601746554,-0.105786739623145,-2.14689408790263,-0.0179354655159725,1.36464320315476,-0.770524951299332,0.289721498136133,-0.357525435598561,-1.12447097590986,0.299607674047228,0.156598063053281,-0.00911912534062269,-0.191733479784302,-1.28430853515883,0.777555095138243,-1.15354859937034,0.935013095916257,-0.326800118158055,-1.80706648050552,1.3272079116825,0.533603333347959,-0.756803541025743,0.995426287594799,-0.247158961611763,-0.604682142974456,0.142186993403621,0.424103604861688,0.978391973825588,1.99667055612782,-0.679725797504891,-0.704780522153102,-1.42126418776182,1.26803724712862,0.95645901426287,-0.209286559440935,0.221140187851337,0.537091152277994,-0.793473524852961,1.91279038939478,0.381637703332559,1.37907748241273,-1.34527261959861,-1.23991942372346,0.405744328700986,0.813356676452473,0.88495125981158,-0.0169851647900536,0.183173150610607,1.10745239721833,-1.15638878927154,1.07711886122316,-0.674033319415973,1.13922592977124,1.02766906138047,1.48941929803597,1.22287481695786,2.12413669791014,-1.39574731884268,-1.03321439607519,-0.373354714188096,0.803837230423222,1.504411992703,1.42399830369141,0.284614910436475,-0.287967102460529,1.30167438176841,0.854022477792377,0.781790947243277,0.333176760247272,0.453703432003669,-0.737725357396021,0.325643259072681,-1.31755300993727,1.04154926229967,-1.15675312732712,-0.444653618289255,1.68482799656771,-0.552756681839605,0.292194171529714,0.148307670241154,-0.212223072849561,-0.449081568131807,-0.0103463757235653,0.592870560459099,-0.74108104172037,-0.747195642696698,0.591029948167671,1.05687221663114,-1.77770538885762,-0.536627404335339,-0.937968374581928,0.704012316820951,0.114396429415883,1.49464080720399,0.943766953319768,0.102033721276572,1.19526768562327,-0.142494219897867,-0.27609660949889,1.29885221461124,-0.625365281791557,1.81815786925618,-0.283566276899032,-0.377032140309027,-0.553904645577154,1.25654804012348,-0.685176573554106,-0.225196560260062,-0.934102652991925,-1.49925654226633,0.609698498266475,-0.585932279764857,-0.731281677597997,-1.5043062931517,0.90704321728974,0.822399500905819,-1.61058814141655,-0.896361302797306,0.405580551222158,1.03445337371931,-0.248400388586945,0.441721476103357,-0.473132102746258,-1.22769789243899,-0.23495192669799,-1.09483433906412,-0.206393132243154,-1.52902348705618,0.518044880898755,1.53380405857648,0.104835456306734,-1.12357220719255,1.70480135228725,0.214411412784133,-0.118902983013281,-1.06174285808464,-1.6486285398876,-0.177790291507468,-0.205048386514122,0.0648821800738394,1.48179064092365,-0.896684660551291,-0.630522843711585,1.62780636397846,-0.792228801530542,-0.548638011343063,0.260399337206176,-0.373421722290896,-0.276473797675906,0.237599074392188,-0.374113893821755,-1.39594181675097,-1.31224596224789,0.5541873480406,2.86335399918476,-0.0542910959365941,-2.0916987182597,1.24754318722272,-0.956276476295267,0.169110824089235,-1.40241617805426,0.553362841593996,-0.683407278106971,-0.42069542372213,-0.458246247971417,-0.843812256846396,-0.420135481559005,-0.234093307771663,-0.133952649299636,-0.493963786077563,0.821791175938833,-0.674242909236964,-0.115123991975731,-0.348813585250722,-1.53765719286008,-0.533938895468854,-0.82981253929124,0.173730995578906,-0.509613243411215,-0.420474551279802,1.25869053405101,0.480711078731062,0.00220555506824995,-0.205098059212553,-0.0303679063364858,-0.293314021036994,0.457359993855347,-0.846300124840374,0.36510559219636,1.18107341944787,0.170837654334521,-0.280649038747647,-1.30471829221648,-0.566026986738075,1.14075027371975,0.780560472646573,0.0274895496244567,0.00106530296787231,-0.857236713410092,-2.22669354433044,0.100463726723492,0.245441232701247,-2.04022970034131,-2.57750379674964,-0.151951738735992,0.231871591553433,1.48212668726792,1.24897737611801,-1.36180554835922,0.284925302867523,0.134876932230087,-0.263091051460913,-0.234542357792168,0.71015732334615,-1.69876428136094,0.993225343836586,-0.664525654282272,1.27269266744737,1.01520890215941,-0.577820986345055,-1.08982511795568,-1.924587695429,-0.826526172875272,-0.332173700802111,0.244152745501695,1.27193011420976,-0.216978698652933,-0.924176324054035,-0.666749029864451,0.0213682127373966,0.635776074941819,-0.300337853567648,-0.27017989487572,-0.147634764090551,1.10626203386338,-0.15741667482004,-1.46453458633912,-0.180914306281348,-1.63620317843555,-0.662721278608005,-0.0260599777302256,-1.09532145900794,-1.89095104770651,0.651207298775159,-1.06546523047118,-0.659810754327918,0.9346213341806,0.051119672928183,0.258892587345216,0.538038848292031,-0.0512827057149942,-0.887975042103711,0.378586958494787,0.783828993078331,1.3820202316654,0.307970157784243,0.134407086439584,1.00519803744632,-0.296159494736189,0.0493101664908476,-0.788546850935231,-1.1264685486159,-0.713999177099731,0.429440602435088,1.22964057998557,-0.417866121992782,-0.642256106978181,-1.61631668087669,-0.667056548537375,-0.554373421378562,0.22390838768712,-0.0906706993940046,-0.158762533190917,-0.21118702363183,-0.647969596967183,-0.0172094870104479,-0.190678976094466,1.91334574372633,1.0950596006506,1.27470115174727,-1.2990960698971,-0.445791680564795,-0.191666103373337,0.935982172328747,-0.0919080870233367,1.13862609454067,0.109405529889998,0.963259734317045,-1.99179917031792,0.823171607985343,-0.94685153687287,-1.34771006598469,0.0571315579033293,-0.668751808058282,0.306019860880659,0.278713600994636,-0.467921686345707,-0.240942981802911,-0.0799907919258076,0.144657847360998,-1.22509821716739,-0.55306167161487,0.953017949701503,1.07958453552968,0.407466574908891,-0.384098675115284,0.165556721048369,-0.641092936458741,1.3602331460523,-0.757470994838299,1.49366094456403,-0.21801397152998,0.55939874804248,2.42127444077203,0.465995274326643,-1.25528468091268,-2.21747203973971,1.77714175830034,0.0576200158158762,2.49935141463705,-0.678665197390242,-0.989451432155713,-0.202357884086547,-1.01592301028038,1.25607387279138,-2.4969798732075,1.20174170587878,-0.0349575995609874,-1.18122752201586,-0.755677761431784,-1.17972308490985,-0.313486306638834,-0.830391217715289,1.28973737618184,-0.789272329544104,0.580026705974776,0.294477999511277,-0.823605954015505,-0.0996440452520963,-0.421719847784054,-0.806124111423194,0.114956621646677,1.23960291485702,2.27175668144817,-0.515138484211967,0.371611484958169,1.95891339480171,-0.402068096916475,0.329264770396976,-1.30684220457287,-0.474320422135628,-0.121391066565816,-1.00864764097799,-0.231656776031136,-0.514697729381712,0.669926523996267,0.523052678935464,-0.199287822790294,0.718999269853371,0.120909514544198,-1.38856437742948,0.969066494979778,-0.687254948903454,-0.613151631675259,-1.5189063596839,-0.58476753425288,-0.974292215920299,-1.72900813104606,1.4765391380415,1.1909206793874,0.29093039575513,-0.960789774592101,0.18337028883304,-0.414859008541124,-0.260478839241547,1.13747595466314,0.171653189935088,-0.15514289395754,0.121799825494251,0.735650627157187,-1.58034937449566,-0.572976127498608,0.562086994364387,-0.320903622261235,1.90233063204729,-0.165670698720683,-1.16539852733803,-1.21916607496969,0.169005970836098,-2.17121406693524,-0.686613653378003,0.0699194722511855,0.227731612080977,-0.824948851450866,0.0920526050858278,1.03266930577186,-1.56474697566259,0.324103539579778,-0.448992238884376,-0.321966749397481,1.42052691928147,0.789655308027942,-0.350969252049006,-0.177446225608988,-0.0119262608599708,0.840975805944552,0.144559577508478,-0.443989321583048,-0.693465796239961,-0.163560201017667,-1.18459022494895,-0.10973278011486,-0.462850872399149,0.876685102100316,1.33365679910565,-0.899677993694522,-0.481599286423996,1.67433791843386,-0.124768253019654,1.08721940189551,0.656770334336826,-2.68773672501129,-0.459823023590485,0.569536113414694,1.53360013326282,0.442451455304831,-0.0220448972146681,0.373610578142584,1.1040780560402,-0.690868021892916,0.355062922811237,-0.422419791759566,0.544723524359865,1.61922092898763,-2.00055232700114,-0.595202002918857,0.67110453470785,-0.291874400448417,0.967854311648236,-1.03176625550525,-1.71312664183755,-0.146978192327672,-0.278630243695659,-1.46905865801543,-1.08343894401213,-0.408676351560171,-0.306170235705661,-0.168897221763308,1.01746886322837,-1.03945080401393,-1.05528897120318,-0.801046351360354,-0.58240884877056,1.26617903794456,0.596280083631777,0.444149067375701,0.0821077423101922,0.214201016435926,0.498081520598327,1.6259978902583,-0.219109231490584,-1.4469186572517,0.845013404807256,0.499707924285056,1.26536249070569,-0.67510501714857,1.09899484043609,0.354781843429395,-0.312385462104041,-0.729119171646009,-1.05004715718952,0.9172060897661,-2.51933065704047,1.23371760328724,1.41727350951389],"type":"histogram","marker":{"color":"rgba(31,119,180,0.6)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,0.6)"},"error_x":{"color":"rgba(31,119,180,0.6)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```


```r
fig <- plot_ly(alpha = 0.6)
fig <- fig %>% add_histogram(x = ~rnorm(500))
fig <- fig %>% add_histogram(x = ~rnorm(500) + 1)
fig <- fig %>% layout(barmode = "overlay") # "stack" | "group" | "overlay" | "relative"

fig
```

```{=html}
<div id="htmlwidget-9d2407e790f88cf4a5fc" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-9d2407e790f88cf4a5fc">{"x":{"visdat":{"32c8c3c17fc":["function () ","plotlyVisDat"]},"cur_data":"32c8c3c17fc","attrs":{"32c8c3c17fc":{"alpha":0.6,"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"type":"histogram","inherit":true},"32c8c3c17fc.1":{"alpha":0.6,"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"type":"histogram","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"barmode":"overlay","xaxis":{"domain":[0,1],"automargin":true,"title":"rnorm(500)"},"yaxis":{"domain":[0,1],"automargin":true},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[-1.09662832275406,-0.18518950300023,0.455677550531011,1.63447153431064,-0.0736656902401923,-0.331369399090102,-0.496444382355546,0.87722218068473,0.781124658650103,0.499606528745775,1.14149993144221,-0.38794993944584,0.34857616815681,-0.315183173199197,1.06300491393612,-0.538376842895254,-0.339757095530752,0.222026430426022,0.689096594712133,1.11921057127209,1.42410146117157,0.588809024640672,0.464430188281705,0.265183052969622,0.679823249444784,-0.566381172283476,-0.336589035484668,-0.268844017835763,0.237718534896711,0.130325180744511,-0.104858645437702,0.0728680152457407,-0.157017130229932,-2.08236331786023,1.68683040168129,0.817098005098954,2.32448452353325,-1.23857493948367,1.38466602159053,-1.30238893219913,-0.36092009664895,-0.394456851320901,-0.19743889806078,2.2446712006098,0.961216915521849,-0.322605857383498,-1.10169722795921,1.67570638079478,-0.0794787448144201,-0.802866257283526,-0.275126037988279,0.417609176017731,0.857068421319514,0.506218890711714,-0.798569672066181,-0.530384918426132,0.435558356863295,-0.289567586998955,0.794721245708209,0.718302358226974,-0.0730257323775559,-0.852372266163965,1.77567128290901,1.247333289315,0.36814184233352,1.36421857035121,-0.114834671481893,1.28261119467282,1.01245028842376,0.47837170580683,0.654766789118566,0.111725479610551,-0.275507805164724,1.1733049932461,-0.613490176717434,-0.699355106518952,0.687122244148784,0.837509081442294,0.139682547735093,0.370819901720225,-0.637626304365352,0.0498541938206558,1.62481955159238,-1.58374834113338,-0.660641697833764,-0.317607087145095,-0.131943582680384,-1.06326499490282,0.92230947550608,-0.404983515342,0.384181362367425,-0.314472710769515,0.503922789713701,0.0186820440425653,-0.502669600601128,-0.763856236550402,-0.742246481817446,-0.256499193176418,-0.556043245060104,-1.20820607912056,1.60494343862938,-0.926931893456137,-0.472466015050057,0.400614957920072,-1.35066564282834,0.810045234344532,1.68196563611072,-0.946034254280753,0.500928785027189,0.331927334753021,-0.359292900133611,-1.57217259595692,0.429011084046633,-0.171852582692789,1.86224028874081,0.968479621027315,-0.36532796563572,0.826162938216377,-0.391064748508194,0.700464701127633,-0.291137462004446,0.518467252592845,0.837061385448793,0.1431715432821,-0.401009418912632,-0.0457923395415797,-0.282439267048586,1.16883483205769,-1.1563089011462,-1.07456745396236,0.199150148511749,1.09582079383567,-0.0375759382080119,-1.26400578967047,0.184765052819851,-0.123593471580105,-0.311027711150659,1.38886647481955,-2.20191492164766,0.668562404570512,-0.432079328473237,0.362541079058805,-2.35096185809826,-1.8311577793728,-0.0917193945355639,-0.3814136081584,-0.464797363455879,-0.379598307120748,-0.955923204873474,-0.25639410193136,-0.302919316500143,-1.14504579574679,-0.585609757780568,1.44244158314628,0.707018432538302,-1.85770709620203,0.306735374193679,0.103311108827418,0.170114910404663,0.507477381552416,0.509064041716943,-0.79102791875697,-1.59319326369609,-1.36706592283674,-0.48101682326617,-0.166731349406842,-0.506279182565202,-2.64652838321399,1.44593702182028,2.58174606318647,-0.607629567043331,-0.657287480808871,0.860754814783157,0.297645834513134,-1.3833697061484,-0.499842717639886,1.03924511271168,0.177250048093857,-1.04149129713942,0.982559670324398,-0.659328759635329,-0.123118737432571,0.913959700014754,-0.0427513325441912,0.26604553731825,-1.31130514916684,1.24359128701958,0.147159320931625,0.133002825883981,0.838304475642065,-0.216751295634068,-0.8918107235316,-0.71046803863654,-0.567949940432009,-0.229335925185966,-0.52980663171377,-1.19236036266734,0.412710591044636,-0.030278188063563,-1.32943145082024,-1.16988024385545,-0.902955640485266,-1.17089581254345,1.78952019885381,1.29305655227277,0.720580358279088,-0.332243612297073,1.38255155621184,-0.412189302075362,0.93353357684489,-0.112500265071173,0.897998750931111,0.816163819943092,0.869973607180829,-1.3369106723352,1.39499551733374,-0.815490064197979,-1.98979739132175,1.17185443971089,-0.407311341252056,-0.582262603238506,0.092300748053637,1.4746083499111,-0.649520370030934,-1.98048158469992,-1.02167322622784,1.03585359603721,0.484395583550987,2.27158772183784,0.952801687009806,-1.24825228440535,-0.46058046434155,0.109129203066994,-0.908112435197192,0.583704967647883,1.67262674695979,-0.793827539661811,0.39897068179109,-1.11788791604772,1.053675514081,0.522123870220313,0.672503990101645,-0.0399515343091343,-1.00878032639412,-0.149447589257782,-0.215340675114052,2.7735555590208,-0.00559453969600218,-0.163980476572303,-0.359199258375126,0.426080299442262,-1.21438286049133,0.864911327889275,-0.74086544333853,0.219622922001353,-1.24335681397989,0.441846015061269,-1.38721719665593,1.19115015145034,-0.090494952910125,1.20144794464609,0.0627078664384373,-0.392792109848429,-1.49191583286987,2.33431713612933,1.11326321413481,-0.527775350776785,0.255214501888973,0.51169240258579,0.822165399109793,0.322914059256102,-1.71336767202125,-0.42548146238608,2.10018492606634,-0.0123725556898919,0.128486259616777,-0.525912236942035,-1.51182731601331,0.526911217131852,0.146803050238221,-0.924055480421052,-1.60896657722002,-0.0772397423921296,0.289600662325467,0.832863316748835,0.362435119631428,-1.11117157121738,-0.0782309602548396,0.345758179168848,0.0608753461995511,0.375831689068159,1.24187065708208,0.96274106317096,1.0472248959996,-2.84613802979745,1.84029145035973,0.438047628899125,-0.569930487067085,-0.476447459995533,-0.271637768248451,0.670562050452109,0.439417979299569,-1.14657725916223,0.385753960217593,-0.168108649572563,0.0141447566287801,1.37068431036141,-0.789180575444243,-1.06087251561192,-0.49952956586088,0.686767119884077,0.277636067866719,1.37677217890082,0.718739558154937,0.276596594832883,0.711650483320888,-0.857945179177745,-0.306751690992552,-0.385561482868162,-0.00357843565992014,1.85430434073846,-1.5895552596741,-1.08346006148617,-0.3064721070521,-0.222527541870073,-0.210639318727058,-0.837533667934776,0.0920188164223422,-1.53995970427761,-0.251868903413851,0.549826394782017,2.01549678690597,-0.542330823232928,-0.662608035625519,-0.615669671927748,0.279783841631571,1.07417228725757,-0.335309660767836,-1.28218451648851,-1.2282267342194,-0.57744068565778,-0.284419230718644,-0.856194477018261,-1.25513771071858,0.153729672549665,0.481098948502823,0.536657537694121,-0.668120360816955,0.329332536753626,0.770383714099425,-0.823494760524981,-1.08598563170811,-0.910274539357288,0.958506734732725,0.610591104259027,-1.40032788410721,-1.86851401402447,0.426670316391335,0.694350997778936,0.636346158854526,-0.624607087385782,-0.354236577632981,0.405982899571324,-1.77090317285369,-0.83980638864773,0.298128307952739,0.391602017361749,-1.67390869387741,0.211159324448044,0.854528760482201,0.814098045099809,-0.718609268410034,-0.0819440417013393,0.276632781591199,0.44749800707227,1.14215246999197,-0.832837968090553,1.18033162739904,0.683673853620221,-0.439071231272124,0.965077561510429,-1.08361773243928,-0.264595402094669,-0.465973342176626,-0.362389332777766,-1.19849684980386,-1.36918261260131,1.35734123817866,1.58614562496574,-0.412151728660589,-0.942375446910549,1.75265502757488,-0.301834544553393,-0.317676084134335,0.847486877612673,-0.822671762649464,-0.0806035356728479,1.19840184789395,-0.0438963216939493,-1.93356092174043,0.0511200824521246,-1.10741060411225,-0.367352227851705,-0.0107312909029751,-0.039421701281582,0.813502107733185,-0.764205328972232,0.0472175529921582,0.0527665549617578,-1.52575662863964,1.46180505683416,0.919391959636134,-1.81903413943381,1.06579623816751,0.178961889027199,0.580714922868319,0.358540890035037,0.165560763862736,-0.430369130404287,0.76103535581386,0.13803541241919,-0.326447844568736,-2.07170499687496,-0.710061512918895,0.772408156318242,0.0164751142810484,-0.617158481205805,-0.0438408282625101,0.28957262817556,1.07784412884709,-1.22474447679557,-0.78290912526777,-2.2911466958884,0.749502013299556,0.440005477488232,-0.580747503015386,-0.0478507505540365,0.526555210996443,-0.267052384659423,1.60659001441086,0.455135411373485,-1.31406090629334,-0.839508280525153,-0.214180143699141,-0.50340819518712,-0.949221356253382,-0.437129503436099,-0.541255925229947,0.363515007726259,0.778603521827119,0.250968091115733,-0.472830887959483,1.01414728066291,0.266228770096971,0.504347973957311,-1.27177499895688,1.39497856576921,0.196230506256521,-0.0469290414542992,-1.46354084119575,-0.110826846822226,-0.300489952136037,-0.664096953383611,-0.438442213018506,0.0671665448422706,-0.534874346908762,-1.14697192829271,-1.08115180451495,1.21404955112953,-1.32847477494128,2.09912130574364,-1.16122507391701,-0.395914140084389,0.092493549413359,1.00641295137879,-0.48103154819688,0.322810239795835,-0.103063154146749,-1.24137476992342,-0.669921386741322,0.221721216905963,-0.550352712286712,1.1986222731892,1.51985937676593,-0.699453922129044,-1.19723462248042,-0.320964696606282,1.86465987262009,0.714824401188718,0.0824701083448703,0.988300264406487,0.71118788106399,1.48525631231681,0.288207493280992,-0.0123921321309278,-0.209093841112317,-1.68615797673478,-0.988373402754978,1.69637020337183,-0.393314636837821],"type":"histogram","marker":{"color":"rgba(31,119,180,0.6)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,0.6)"},"error_x":{"color":"rgba(31,119,180,0.6)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[1.58146400981237,0.875934157958384,0.97410250398013,0.735479233591033,1.52981861911288,0.973513004907223,-0.121878860739941,-0.634540289495892,2.0315540767568,0.936955062138747,-0.323488909780063,-0.827505017931915,1.57177267865036,3.0286827544657,1.49193343890309,1.81915642125233,-0.00811833995162381,0.278353829116396,1.37415809129871,0.920015099719031,0.231309873127012,-0.102515954888938,0.939686730370436,2.49414777148802,-0.382276309879462,0.889881754205124,1.96712180738766,1.26902765526041,1.82294056975926,-0.269706173333202,-0.551660193903379,1.85680701569481,-0.424259129378033,2.81066281089933,1.0939410318495,0.34681594740236,1.22169958101601,-0.104461720854243,1.05506170659333,0.269637991566654,0.278254731083626,1.04451237280694,-0.425468111218956,2.44744434810418,2.19035826332962,1.40636434818248,0.447268321981882,-1.05558661773836,0.513664112846485,0.572608404677906,1.09016634235516,-0.184154561919359,2.44094771459902,1.05986569749481,2.16196254984349,0.354610771032797,-0.209255224582834,1.5605757203169,0.144988600670501,0.880462659951154,0.434360523222428,1.20213479676198,3.0182239570315,1.19212598234056,0.738796579459531,0.245391321453565,1.00433696310482,1.33618826302524,-0.927918803629605,-0.117231822547724,2.64043359789529,-1.85891550164102,1.04781654886203,0.55757235224023,0.76580908644735,2.39953224983549,-0.273644277206136,1.12075042007406,-0.744145548954397,-1.19608081848887,1.25020891196674,-0.661107396081816,0.0721782053912803,1.26609504154278,2.1821467547785,-0.473057976802766,1.73801975690746,1.27657960467645,0.987220486559892,0.923112592161894,0.666630263630411,-0.991825427420637,0.443627910658042,1.35986347635907,0.822266970264318,1.65339646375649,2.29247222744236,0.818865962911699,1.93285918431332,0.246886974472939,1.43885702489363,1.14288816839714,0.813322538516519,0.580461114199763,1.41915649763341,0.417662970971684,0.730987175166487,1.13557661784839,-0.2725060870627,0.571431448046531,1.4874936299491,1.6698248804667,1.06381002131588,0.597841247478167,0.868550405565872,2.72908454785081,1.42450282020202,0.903725821870498,0.851084862417782,0.588949269264572,-0.357940833121288,-0.500112175698795,0.94949252994191,1.59685533488078,1.16412322605906,2.12820381259409,3.23658740528594,0.91916868660059,2.61269936385339,-0.808656036349437,1.0797497769692,0.295379660414108,0.981544284733729,1.23050998254223,0.507320542771479,2.64506623843849,2.5995396714016,0.254494867819016,2.19901499137655,2.17208310067781,0.7924372772841,2.53315586260849,2.03909627033096,0.310944646823006,2.85040014684171,1.12884064899579,0.432909716281863,2.15733856826408,0.497019211605896,1.45031383279709,-1.4385096647009,0.678842722292814,0.550101219126231,0.386828939972357,-0.314609390990276,0.977552990815148,-0.590239046836179,-1.42529591159748,-0.662598754476176,2.45233921911021,0.0984259306873193,0.194154408757022,2.02922104984878,1.43671865235802,-0.338151961204642,0.407783506779699,0.342081922093782,-0.886385589706839,1.58403569627844,2.21953742595154,0.444997281473446,0.719054431485398,2.23200165711684,1.41504592300986,1.26581888159588,-0.0909665686897672,0.528314949270824,-0.853650571569314,0.358838710508805,1.51970577013952,0.531231557969553,2.65326786669393,0.225987228460912,0.919217627125726,0.744639624428467,3.03547875425499,-0.108529783894159,1.37762170893854,2.10447702847884,0.556493012210921,1.10735114870289,1.20172947314116,1.30370919415419,-0.0438433636408668,2.96896051752739,0.416919145138255,-0.226308617518339,2.54134876503646,1.52382733169579,0.141876502586175,1.53325955992187,0.821014553382233,0.966789625749954,2.11208394173667,0.380900776752747,3.23970535675529,-0.537997981481207,-0.923950647026672,3.01187234163992,1.09132737144956,0.592569683016541,1.52947830617002,5.25137014641543,2.85060107305547,1.08763403062124,1.18858399566939,-0.481721258456826,2.69709674334513,0.829754384358317,2.51312273212747,0.481356772057464,2.37810244331192,0.953840844183293,0.68211469910922,1.13639639980769,0.450446584598002,0.0595300899943922,2.14289830149897,-0.504086085814311,1.89179616275159,1.82931202241727,0.620348333985795,0.344307349283733,1.30942658949802,0.562251132160277,0.406861869012005,1.95026164364239,-0.353926244480342,-0.730998866084325,2.55323278188814,1.82576516352012,1.42704724197226,0.873068451872842,1.77232098924255,0.845122224542007,0.640493891848359,0.418741523738657,1.03114766506077,0.166363656320937,0.0417907148228451,1.16791709849369,2.53078400950163,2.41503208326696,0.356714909444207,1.93103393032745,1.54739429499308,1.34154859897808,-0.267888588270567,0.00406300432855677,-0.223897004288756,0.40442784992974,-0.315307691949298,0.382009623507423,0.172744882999804,0.825053459847807,0.126957226636181,0.206637573530931,1.69752984045667,2.19245192641789,2.64023938949317,2.15612589471644,1.366045749685,1.89702491936356,-0.032643596352149,2.10164675797841,-1.25613068684055,0.556943612432588,4.08524532387813,1.89363765329455,2.71336106664713,0.739450961481824,1.63065030245762,3.20750610994427,1.51284030547243,1.3386741509602,2.34924113217714,2.22124673871405,-0.997313598143684,1.87677647373107,0.434502094621234,1.84748853434982,0.798570950389629,-0.910441004492507,0.213238921115315,1.60710026080993,0.785059730539681,1.97213634100127,0.694169352712668,0.761987474744527,0.948446663858934,1.14504813444972,2.34968157714362,0.570612674731865,-0.313569129630632,1.18505471125372,1.37039836791339,2.52222808052009,0.0554779292208709,1.9561125829961,0.468636237140151,3.40667196295623,1.07941741680367,1.43392711945934,3.15411105088065,0.36413886126131,-0.435403910828891,1.00464651936231,2.10276364522663,-0.100669009515741,0.793562679127636,1.74710606529378,-0.669959774532375,0.844821959922402,2.99286692016608,0.660892641047565,-0.305822807122366,0.481666633142002,0.968135485739577,-0.878923884946557,1.36505322801526,0.535722316613634,1.27363383978058,0.841726743497488,1.64338752782976,-0.317688154193126,1.57930098481449,-0.374595068011395,1.4413723940754,0.307081638910433,-0.776682095775058,1.55875342702367,1.24047035382158,2.11935496617834,0.943072376953064,0.839624894782814,2.45768648006843,-1.64495523768051,0.817093768262745,-0.192157605026983,2.21745064405511,-1.26576497974667,0.738403570500215,0.77518312974719,1.16047556293525,0.833534843505038,1.51363361805221,0.0155662442454132,0.86873215190829,0.906780960175045,1.7663935962866,0.0904372185071975,0.157701664752791,-0.500718294660625,2.29560551088427,1.70376130077339,1.73464023814827,2.31708639593675,1.32091546321139,0.46111543736922,2.89807304590562,1.82580336165827,1.35723541016374,1.50180160707378,0.521235900823284,0.0964144233086269,0.556261156386918,1.60259809261399,0.66320030195198,2.88472285967427,-0.92157506157552,0.611592258566729,3.11667119578958,0.632196867705093,1.56056061664024,-0.324376858046664,-0.200069814307012,1.63385647231434,-0.547674138670555,2.37176067126138,2.03986905351793,0.584856532391779,-0.688679955281259,1.51188329479755,-0.23818888872793,0.192719164255254,0.66212507525628,-0.30523912952568,1.70996756452608,2.35626561748401,0.898198094750976,-0.835889746119179,2.02452613927025,1.7384280464667,2.1617606375644,2.05469014521312,2.06583875034593,0.824955989022021,0.38980864344505,0.917512908661249,2.10109191950018,0.0419500795722011,0.520064889782504,0.479606932885335,-0.211478299307005,2.70118442884105,2.31750294665076,-0.426837727455845,1.03345526699727,-0.476701160347758,0.584622645389458,2.21061870054617,2.29530851496032,2.12778483614124,1.36467871933739,-1.43365023639286,1.8975899236877,-0.109265701237955,0.425113313325131,2.58426026173607,0.287256383456425,0.111856103179548,1.42301177001881,1.13902438684892,1.45624374864897,0.691300340884671,1.8376167454911,-0.112507208674897,0.869998633136055,0.596739943326124,1.78815449483063,1.86233956241483,2.24409387157357,0.782943497529496,0.990206205638199,-0.433062154807464,0.96968551639249,-0.31219095107225,2.20064481667076,1.20054441188595,0.699782566244858,0.40419277652743,0.520199911005375,1.98338323440028,-0.550798453626723,0.650516971363052,3.30642061770933,2.40794650607625,2.63074180660434,1.39023639630787,0.717390212914567,0.015292413883462,0.576884990529119,0.328595480166074,0.762637694722367,0.766520704391015,-0.121739142752758,0.561580235459054,1.75156715284222,1.31402875481705,1.24579093729912,-1.0186799854964,0.161636122915849,1.30351591062114,1.63599384003556,1.68493734233575,2.29691508312687,1.08341673651135,1.24459043263333,0.834198433592373,1.738391241058,-0.560413844742572,-0.484963078410472,0.0193520173067376,1.70553409517758,0.783564800580587,0.487694512827785,-0.548741146882635,1.59151816843314,1.10743181938354,3.55670343846498,1.22460964269048,2.62068821205849,0.19261389904675,2.6459102010521,1.76878574820289,0.760261986300028,-0.195525160430534,-0.560631817318143,0.719669743714493,2.26655453127797],"type":"histogram","marker":{"color":"rgba(255,127,14,0.6)","line":{"color":"rgba(255,127,14,1)"}},"error_y":{"color":"rgba(255,127,14,0.6)"},"error_x":{"color":"rgba(255,127,14,0.6)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

## Boxplot


```r
fig <- plot_ly(y = ~rnorm(50), type = "box") %>% 
  layout(title = "Boxplot",
             xaxis = list(showgrid = FALSE),
             yaxis = list(showgrid = FALSE))

fig
```

```{=html}
<div id="htmlwidget-66ca9dd1447dc4d7b7d9" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-66ca9dd1447dc4d7b7d9">{"x":{"visdat":{"32c86909276e":["function () ","plotlyVisDat"]},"cur_data":"32c86909276e","attrs":{"32c86909276e":{"y":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"box"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Boxplot","xaxis":{"domain":[0,1],"automargin":true,"showgrid":false},"yaxis":{"domain":[0,1],"automargin":true,"showgrid":false,"title":"rnorm(50)"},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"fillcolor":"rgba(31,119,180,0.5)","y":[1.0188459245555,-0.442028899701819,-2.68017796903874,0.225799698569074,0.362549206192251,-0.0150295371038309,0.24079987817215,2.00024674683412,0.379458443575521,0.313622102998554,0.629121271337925,-0.473219034688603,0.805640024245109,-2.03346417944164,0.488754185533386,2.24578532530152,0.930103247406312,-1.74625071346889,0.632440202242524,0.0722189783805234,-0.172485245035876,0.126387199022156,1.68262497879838,0.734390985843562,-1.03827262427176,0.96652349761211,0.484740878326223,0.395659781782271,-2.97218950344082,1.53529690172767,1.84949916695471,-0.728158102397606,0.0277259949490923,-1.01657814572759,-0.776193375912626,-0.0896884713146789,-1.23984820504539,0.515619780366576,-0.537063627456006,0.525775655937576,-0.971913119487551,0.0272875675625717,-0.874913013682775,1.30866235245334,-0.451170225422305,0.996842637610609,-1.89927354328802,1.12149929432648,-0.255378198195867,-0.91049127900831],"type":"box","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

## Diagrama de sectores


```r
fig <- plot_ly(
  data = iris,
  labels = ~Species,
  values = ~Sepal.Length,
  type = 'pie'
) %>% layout(title = "Diagrama de sectores por Species",
             xaxis = list(showgrid = FALSE),
             yaxis = list(showgrid = FALSE))
fig
```

```{=html}
<div id="htmlwidget-12ea2b44e93a5fdc64c7" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-12ea2b44e93a5fdc64c7">{"x":{"visdat":{"32c81b327e98":["function () ","plotlyVisDat"]},"cur_data":"32c81b327e98","attrs":{"32c81b327e98":{"labels":{},"values":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Diagrama de sectores por Species","xaxis":{"showgrid":false},"yaxis":{"showgrid":false},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"labels":["setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","setosa","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","versicolor","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica","virginica"],"values":[5.1,4.9,4.7,4.6,5,5.4,4.6,5,4.4,4.9,5.4,4.8,4.8,4.3,5.8,5.7,5.4,5.1,5.7,5.1,5.4,5.1,4.6,5.1,4.8,5,5,5.2,5.2,4.7,4.8,5.4,5.2,5.5,4.9,5,5.5,4.9,4.4,5.1,5,4.5,4.4,5,5.1,4.8,5.1,4.6,5.3,5,7,6.4,6.9,5.5,6.5,5.7,6.3,4.9,6.6,5.2,5,5.9,6,6.1,5.6,6.7,5.6,5.8,6.2,5.6,5.9,6.1,6.3,6.1,6.4,6.6,6.8,6.7,6,5.7,5.5,5.5,5.8,6,5.4,6,6.7,6.3,5.6,5.5,5.5,6.1,5.8,5,5.6,5.7,5.7,6.2,5.1,5.7,6.3,5.8,7.1,6.3,6.5,7.6,4.9,7.3,6.7,7.2,6.5,6.4,6.8,5.7,5.8,6.4,6.5,7.7,7.7,6,6.9,5.6,7.7,6.3,6.7,7.2,6.2,6.1,6.4,7.2,7.4,7.9,6.4,6.3,6.1,7.7,6.3,6.4,6,6.9,6.7,6.9,5.8,6.8,6.7,6.7,6.3,6.5,6.2,5.9],"type":"pie","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```




