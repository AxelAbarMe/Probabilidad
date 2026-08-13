# Rstudio


## Markdown


Editor de R para generar documentos.
- New file
- Rmd
- Cambiar información


Chunk:


- Chunk donde se introduce el código de R


```
// Para imprimir todos los chunks


knitr::opts_chunk$set(echo = TRUE)
```
Se carga los paquetes para lograr leer la base
```{r}
if(!require("readxl")){
install.packages("readxl")
library("readxl")
}
```
Importar base:
1. File
2. Import dataset
3. From excel
4. Import
5. Copiar datos_estudiantes <- read_excel("C:/Users/Mate/Downloads/datos_estudiantes.xlsx") u URL dada


## Tabla de cantidades y porcentajes para una variable.




```{r}


# conteo de los datos (función table())


tabla_1 <- table(datos_estudiantes$creditos)


# cálculo de porcentajes (función prop.table(x))


prop_tabla_1 <- prop.table(x = tabla_1)*100


# redondeo a 2 decimales (función round(x, digits))


prop_tabla_1 <- round(x = prop_tabla_1, digits = 2)


# generando el vector de porcentaje


porcentaje <- as.vector(prop_tabla_1)




# creando la hoja de datos (función data.frame())


distribucion <- data.frame(tabla_1, porcentaje)


# Nombrar columnas


colnames(distribucion) <- c("Créditos", "Cantidad", "Porcentaje")
 


# escribiendo el título


titulo <- c("UNA. Distribución de estudiantes según cantidad de créditos aprobados. I ciclo 2025")




# generando la función que crea la tabla


hacer.flextable <- function(data) {


# cargando flextable


if(!require("flextable")){
install.packages("flextable")
library("flextable")
}
 
# generando la tabla y modificando el ancho de la columna
# argumento cwidth


distribucion <- flextable(data = distribucion,
                          cwidth = 1)




# alineando las columnas
# función align(x, align, part)


distribucion <- align(x = distribucion,
                      align = "center",
                      part = "all")




# agregando el título
# función set_caption(x, caption)


distribucion <- set_caption(x = distribucion,
                            caption = titulo)




# cambiando punto por coma
# función colformat_double(x, j, decimal.mark, digits, big,mark)


distribucion <- colformat_double(distribucion,
                                 j=c(3),
                                 decimal.mark=",",
                                 digits = 2,
                                 big.mark = "")




# dando formato a los encabezados
# función separate_header(x)


distribucion <- separate_header(x = distribucion)




# Se imprime el resultado final


distribucion


return(autofit(distribucion))
}


# imprimiendo la tabla


hacer.flextable(distribucion)


```


# Tablas con dos variables (tablas n x m)+0x067


```{r}


# conteo de los datos
tabla1 <- table(datos_estudiantes$materias,
                datos_estudiantes$sexo)


tabla1


# cálculo de porcentajes por columna (prop.table(x, margin))


porc_tabla1 <- prop.table(x = tabla1, margin = 2)
porc_tabla1


# datos de la categoría 1 de la segunda variable (este ejemplo: hombre)
cantidad_1 <- as.vector(tabla1[,1])
porcentaje_1 <- round(as.vector(porc_tabla1[,1])*100, 2)


# datos de la categoría 2 de la segunda variable (este ejemplo: mujer)
cantidad_2 <- as.vector(tabla1[,2])
porcentaje_2 <- round(as.vector(porc_tabla1[,2])*100, 2)


# obteniendo las categorías de la variable principal (función table())


categoria <- data.frame(table(datos_estudiantes$materias))


# dando formato de número a las categorías de la variable principal


categoria <- as.numeric(as.character(categoria$Var1))


# creando el data frame


distribucion <- data.frame(categoria,
                           cantidad_1,
                           porcentaje_1,
                           cantidad_2,
                           porcentaje_2)


colnames(distribucion) <- c("Materias",
                            "Hombre_Cantidad",
                            "Hombre_Porcentaje ",
                            "Mujer_Cantidad",
                            "Mujer_Porcentaje")




# escribiendo el título


titulo <- c("UNA. Distribución de estudiantes según cantidad de créditos aprobados. I ciclo 2025")




# generando la función que crea la tabla


hacer.flextable <- function(data) {


# cargando flextable


if(!require("flextable")){
install.packages("flextable")
library("flextable")
}
 
# generando la tabla y modificando el ancho de la columna
# argumento cwidth


distribucion <- flextable(data = distribucion,
                          cwidth = 1)




# alineando las columnas
# función align(x, align, part)


distribucion <- align(x = distribucion,
                      align = "center",
                      part = "all")




# agregando el título
# función set_caption(x, caption)


distribucion <- set_caption(x = distribucion,
                            caption = titulo)




# cambiando punto por coma
# función colformat_double(x, j, decimal.mark, digits, big,mark)


distribucion <- colformat_double(distribucion,
                                 j=c(3, 5),
                                 decimal.mark=",",
                                 digits = 2,
                                 big.mark = "")




# dando formato a los encabezados
# función separate_header(x)


distribucion <- separate_header(x = distribucion)




# Se imprime el resultado final


distribucion


return(autofit(distribucion))
}


hacer.flextable(distribucion)


```




# ggplot2


Crear gráficos según se va escribiendo texto, es un paquete que se construye gráficas según oraciones en líneas de comandos.


colors() en consola para ver colores de R.


---
title: "Gráficas estadísticas"
author: "Eduardo Aguilar Fernández"
date: \today
output:
  word_document: default
  pdf_document: default
  html_document:
    df_print: paged
---


```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```


## R Markdown


Este es un R Markdown para contruir gráficas estadísticas.




```{r}
# cargando la base


if(!require("readxl")){
install.packages("readxl")
library("readxl")
}
datos_estudiantes <- read_excel("/Users/eduardo/Documents/trabajo/curso_R/datos_estudiantes.xlsx") # recordar importar la base y copiar el código generado en la consola en esta línea
```






# Gráfica de barras verticales simples (variables cuantitativas discretas)


Utilice la variable materias de la base datos_estudiantes.


El código que la genera es el siguiente:


```{r}
library(ggplot2) #cargando el paquete ggplot2


# función ggplot(data, mapping, ...) + geom()


# gráfica de barras la geometría corresponde a geom_bar()


# definiendo la base de datos y la variable a graficar
library(ggplot2)


ggplot(data = datos_estudiantes,
       aes(x = materias)) +
 
  # agregando la geometría (barras)
 
  geom_bar(fill = "lightgreen",
           color = "black") +
 
  # ver lista de colores en R con la función colors()
  # rotulando los ejes y agregando título
 
  labs(x = "Materias",
       y = "Cantidad",
       title = "Figura 1. UNA. Distribución de estudiantes según cantidad
       de materias matriculadas. I ciclo 2025") +
 
  # personaliza el fondo de la gráfica
  theme_bw() +
 
  theme(plot.background = element_blank(),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        panel.border = element_blank()) +
 
  # personaliza los ejes de la gráfica
 
  # la línea de los ejes
  theme(axis.line = element_line(color = "black")) +
 
  # el texto de los ejes
  theme(axis.text.x = element_text(face="plain",
                                   size=11,
                                   family = "Times",
                                   angle = 0,
                                   color = "black"),
        axis.text.y = element_text(face = "plain",
                                   size=11,
                                   family = "Times",
                                   angle = 0,
                                   color = "black",
                                   hjust = 1),
        axis.title = element_text(face = "bold",
                                  size = 11,
                                  family = "Times")
  ) +
 
  # personaliza el título de la gráfica
 
  theme(plot.title = element_text(face = "plain",
                                  size = 11,
                                  family = "Times"
                                  )
  ) +


  # la escala de los ejes
 
  scale_x_continuous(breaks = seq(2, 8, 1)) +
  scale_y_continuous(breaks = seq(0, 10, 2))




```




## Gráfica de barras verticales comparativas


El código que la genera es el siguiente:


```{r}
library(ggplot2) #cargando el paquete ggplot2


# función ggplot(data, mapping, ...) + geom()


# gráfica de barras la geometría corresponde a geom_bar()


# definiendo la base de datos y la variable a graficar


ggplot(data = datos_estudiantes,
       aes(x = materias)) +
 
  # agregando la geometría (barras)
 
  geom_bar(aes(fill = sexo),
           position = "dodge",
           color = "black") +
 
  scale_fill_brewer(palette = "Blues",
                    name = "Sexo",
                    breaks = c("h", "m"),
                    labels = c("Hombre", "Mujer")
                    ) +
 
  #O bien,
  #scale_fill_discrete(name="Sexo",
  #                    breaks=c("h", "m"),
  #                    labels=c("Hombre", "Mujer")) +
 
 
  # rotulando los ejes y agregando título
 
  labs(x = "Materias",
       y = "Cantidad",
       title = "Figura 1. UNA. Distribución de estudiantes según cantidad
       de materias matriculadas por sexo. I ciclo 2025") +
 
  # personaliza el fondo de la gráfica
  theme_bw() +
 
  theme(plot.background = element_blank(),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        panel.border = element_blank()) +
 
  # personaliza los ejes de la gráfica
 
  # la línea de los ejes
  theme(axis.line = element_line(color = "black")) +
 
  # el texto de los ejes
  theme(axis.text.x = element_text(face = "plain",
                                   size = 11,
                                   family = "Times",
                                   angle = 0,
                                   color = "black"),
        axis.text.y = element_text(face = "plain",
                                   size=11,
                                   family = "Times",
                                   angle = 0,
                                   color = "black",
                                   hjust = 1),
        axis.title = element_text(face = "bold",
                                  size = 11,
                                  family = "Times")
  ) +
 
  # personaliza el título de la gráfica
 
  theme(plot.title = element_text(face = "plain",
                                  size = 11,
                                  family = "Times",
                                  hjust = 0.5
                                  )
  ) +


  # la escala de los ejes
 
  scale_x_continuous(breaks = seq(from = 1, to = 8, by = 1))+
  scale_y_continuous(breaks = seq(from = 0, to = 9, by = 3))


```






# Gráfica de barras horizontales simples


Utilice la variable provincia de la base datos_estudiantes




```{r}
library(ggplot2) #cargando el paquete ggplot2


# función ggplot(data, mapping, ...) + geom()


# gráfica de barras la geometría corresponde a geom_bar()


# definiendo la base de datos y la variable a graficar


library(forcats) # para ordenar las barras


ggplot(data = datos_estudiantes,
       aes(x = fct_infreq(provincia))) +
 
  # agregando la geometría (barras)
 
  geom_bar(fill = "lightgreen",
           color = "black") +
 
  # colocando las barras en posición horizontal
  coord_flip() +
 
  # ver lista de colores en R con la función colors()
  # rotulando los ejes y agregando título
 
  labs(x = "Materias",
       y = "Cantidad",
       title = "Figura 2. UNA. Distribución de estudiantes según provincia
       de residencia. I ciclo 2025"
       ) +
 
  # personaliza el fondo de la gráfica
  theme_bw() +
 
  theme(plot.background = element_blank(),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        panel.border = element_blank()) +
 
  # personaliza los ejes de la gráfica
 
  # la línea de los ejes
  theme(axis.line = element_line(color = "black")) +
 
  # el texto de los ejes
  theme(axis.text.x = element_text(face = "plain",
                                   size = 11,
                                   family = "Times",
                                   angle = 0,
                                   color = "black"),
        axis.text.y = element_text(face = "plain",
                                   size=11,
                                   family = "Times",
                                   angle = 0,
                                   color = "black",
                                   hjust = 1),
        axis.title = element_text(face = "bold",
                                  size = 11,
                                  family = "Times")
  ) +
 
  # personaliza el título de la gráfica
 
  theme(plot.title = element_text(face = "plain",
                                  size = 11,
                                  family = "Times"
                                  )
  )


 
 
  # modificando la escala del eje y
 
  # scale_y_continuous(breaks = seq())
```




# Gráfica de barras horizontales comparativas


En este caso se muestra la composición de la distribución de estudiantes según provincia de residencia por sexo




```{r}
library(ggplot2)
library(forcats)


ggplot(data = datos_estudiantes,
       aes(x = fct_infreq(provincia))) +
 
  # agregando la geometría (barras)
 
  geom_bar(aes(fill = sexo),
           position = "dodge",
           color = "black")  +
 
  scale_fill_brewer(palette = "Blues",
                    name = "Sexo",
                    breaks = c("h", "m"),
                    labels = c("Hombre", "Mujer")
                    )  +
 
  # colocando las barras en posición horizontal
  coord_flip() +
 
  # ver lista de colores en R con la función colors()
  # rotulando los ejes y agregando título
 
  labs(x = "Provincia",
       y = "Cantidad",
       title = "Figura 2. UNA. Distribución de estudiantes según provincia
       de residencia por sexo. I ciclo 2025"
       ) +
 
  # personaliza el fondo de la gráfica
  theme_bw() +
 
  theme(plot.background = element_blank(),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        panel.border = element_blank()) +
 
  # personaliza los ejes de la gráfica
 
  # la línea de los ejes
  theme(axis.line = element_line(color = "black")) +
 
  # el texto de los ejes
  theme(axis.text.x = element_text(face = "plain",
                                   size = 11,
                                   family = "Times",
                                   angle = 0,
                                   color = "black"),
        axis.text.y = element_text(face = "plain",
                                   size=11,
                                   family = "Times",
                                   angle = 0,
                                   color = "black",
                                   hjust = 1),
        axis.title = element_text(face = "bold",
                                  size = 11,
                                  family = "Times")
  ) +
 
  # personaliza el título de la gráfica
 
  theme(plot.title = element_text(face = "plain",
                                  size = 11,
                                  family = "Times"
                                  )
  )


  # modificando la escala del eje y
 
  # scale_y_continuous(breaks = seq())
```

## Datos iniciales Rmd

---
title: "Distribuciones de frecuencias"
author: "Eduardo Aguilar Fernández"
date: "2026-03-02"
output:
  word_document: default
  pdf_document: default
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## Cargando la base

```{r cargando_base}
# cargando la base

library(readxl)
datos_estudiantes <- read_excel("/Users/eduardo/Documents/trabajo/curso_R/datos_estudiantes.xlsx") # recordar importar la base y copiar el código generado en la consola en esta línea
```
















