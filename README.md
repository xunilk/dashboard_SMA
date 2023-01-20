Creación de un dashboard con Shiny app
================

# Introducción

Este proyecto prueba algunas de las funciones que se van a emplear en la
creacción de un dashboard con R; principalmente con la lectura y
operaciones relacionadas con la base de datos
**PC\_emergencias\_2022.csv**.

## Carga la base de datos PC\_emergencias\_2022.csv.

La base de datos contiene información sobre emergencias ocurridas en San
Martín de los Andes entre los años 2015 y 2022; ambos inclusive. Como es
un CVS se va a ocupar la librería tidyverse (válido también para los
filtros). La base de datos se va a nombrar como test.

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.4.0      ✔ purrr   1.0.1 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.1      ✔ stringr 1.5.0 
    ## ✔ readr   2.1.3      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
test<- read_csv("data/PC_emergencias_2022.csv")
```

    ## Rows: 313 Columns: 11
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (8): Fecha, year, evento, detalles, causa, perjuicio, zona, links_images
    ## dbl (3): id, x, y
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
test
```

    ## # A tibble: 313 × 11
    ##       id     x     y Fecha      year  evento detal…¹ causa perju…² zona  links…³
    ##    <dbl> <dbl> <dbl> <chr>      <chr> <chr>  <chr>   <chr> <chr>   <chr> <chr>  
    ##  1     0 -71.3 -40.1 27/05/2021 2021  caida… arbol … vien… materi… regi… https:…
    ##  2     1 -71.3 -40.1 24/05/2021 2021  caida… arbol … vien… lineas… ruta… https:…
    ##  3     2 -71.4 -40.2 27/05/2021 2021  accid… caida … vien… corte … Riva… <NA>   
    ##  4     3 -71.3 -40.1 27/05/2021 2021  caida… caida … vien… ninguno alto… https:…
    ##  5     4 -71.4 -40.2 24/05/2021 2021  caida… caida … vien… predio… cost… https:…
    ##  6     5 -71.4 -40.2 24/05/2021 2021  caida… caida … vien… linea … cent… https:…
    ##  7     6 -71.3 -40.1 24/05/2021 2021  caida… caida … vien… ninguno escu… https:…
    ##  8     7 -71.3 -40.1 27/05/2021 2021  caida… caida … vien… materi… alto… https:…
    ##  9     8 -71.2 -40.1 27/06/2021 2021  caida… caida … vien… ninguno el p… https:…
    ## 10     9 -71.3 -40.1 27/05/2021 2021  event… inunda… aceq… ninguno chac… https:…
    ## # … with 303 more rows, and abbreviated variable names ¹​detalles, ²​perjuicio,
    ## #   ³​links_images

``` r
library(leaflet)

emerg_Map <- leaflet() %>% 
  addTiles() %>% addCircleMarkers(data = test,
                                  lat = ~y,
                                  lng = ~x,
                                  radius = 10,
                                  opacity = 1)

emerg_Map
```

    ## TypeError: Attempting to change the setter of an unconfigurable property.
    ## TypeError: Attempting to change the setter of an unconfigurable property.

![](README_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->
