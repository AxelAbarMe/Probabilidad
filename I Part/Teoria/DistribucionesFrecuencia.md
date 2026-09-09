# Distribuciones de frecuencia

## Clases
Grupos en los que se distribuye la información.
- **Exhaustivas:** todas las observaciones deben ser incluidas en alguna de las clases.
- **Mutuamente excluyentes:** una observación no puede ser incluida en más de una clase.

### Frecuencia absoluta
Número de observaciones presentes en cada clase. Llamada frecuencia.

### Frecuencia relativa
Es el valor que se obtiene de dividir la frecuencia absoluta entre el número total de datos u observaciones. Se expresan en términos porcentuales.

### Frecuencias acumuladas
Se utilizan para conocer el número de observaciones mayores o menores que cierto valor de clase.

#### Ejemplo:
> Enunciado: A continuación se brinda información acerca del número de hijos de un grupo de 20 personas colaboradoras de la empresa Vista Verde Internacional en el año 2008.

> hijos <- c(2,3,3,2,5,3,4,3,4,3,2,2,4,3,5,3,3,4,3,4)

<img src="../../img/1.3_ExampleTable.png" alt="Vector" width="600">

#### Interpretaciones:
- 45 % de las personas tienen 3 hijos.
- 65 % de las personas tienen menos de 4 hijos.
- 80 % de las personas tienen más de 2 hijos.

### Representación gráfica
Las distribuciones de este tipo de variables se pueden representar por medio de un gráfico de bastones o un gráfico de barras verticales.

### Tipos de redondeo
- Redondeo usual (a la unidad más próxima)
- Redondeo hacia arriba
- Redondeo hacia abajo

> **Concepto general:** el redondeo es el proceso de aproximar un número a una cantidad de dígitos o cifras significativas determinada, con el fin de simplificar su lectura o su uso en cálculos posteriores, siguiendo una regla que define hacia qué dirección se ajusta el valor.

#### Redondeo usual
Mayor a 5 exacto, se aumenta una unidad.

|Original|Redondeo
|:--:|:--:|
|137,502 -> |138
|42,650 -> |43

#### Redondeo hacia arriba
Se conserva el último dígito y el resto se elimina.

|Original|Redondeo
|:--:|:--:|
|137,502 -> |137
|42,650 -> |42
|42,000 -> |42

#### Redondeo hacia abajo
Último dígito se aumenta una unidad, excepto cuando va seguido de ceros.

|Original|Redondeo
|:--:|:--:|
|137,502 -> |138
|42,650 -> |43
|42,020 -> |43
|42,000 -> |42

### Límites de clase
Son los valores que definen una clase, separándola de la anterior y de la posterior.

### Intervalo de clase
Indica la amplitud de la clase y se obtiene de la diferencia del límite real superior y el límite real inferior.

### Punto medio
Se refiere al valor central de cada clase, el cual se obtiene al promediar los límites reales.

### Clases abiertas
Se ubican al principio o al final de la distribución con el fin de incorporar todos aquellos datos que se apartan mucho.

## Ejemplo Límites de los pesos

1. **Fórmula de Sturges:** es un método utilizado para determinar el **número de clases (o intervalos)** recomendable al construir una distribución de frecuencias para variables continuas, en función del tamaño de la muestra. Se calcula como $k = 1 + 3,322 \cdot \log(n)$, donde $k$ es el número de clases sugerido y $n$ el total de observaciones. Al aplicarla se tiene el número de clases adecuado: $1 + 3,332 \cdot \log(40) = 6,33 \approx 6$.
2. El rango del conjunto de datos está dado por $78 - 52 = 26$.
3. El ancho de cada clase puede obtenerse como: $a = 26 \div 6 \approx 5$.

> **Fórmula Punto Medio:** $X_i = \frac{L_i + L_s}{2}$. Con $X_i$ siendo punto medio, $L_i$ siendo Límite inferior y $L_s$ siendo Límite superior.

|Rangos|Punto Medio
|:---:|:---:|
|50-55|52,5
|55-60|57,5
|60-65|62,5
|65-70|67,5
|70-75|72,5
|75-80|77,5

<img src="../../img/1.4_FrecuenciasTable.png" alt="RangosTabla" width="600">

## Representación gráfica
Para representar gráficamente una distribución de frecuencias de una variable continua se utilizan:
- El histograma
- El polígono de frecuencias
- Las ojivas

### Histograma
Es un gráfico de barras verticales en el que las barras no guardan espacios entre sí. Para construirlo se define una escala horizontal y en ella se definen los límites reales de todas las clases de la distribución.

#### Ejemplo gráfico
<img src="https://estadistica-dma.ulpgc.es/cursoR4ULPGC/9c-grafHistograma_files/figure-html/unnamed-chunk-3-1.png" Alt="Histograma" width="500">

#### Interpretaciones Generales
- **Forma de la distribución:** Muestra visualmente la simetría, sesgo o uniformidad de todos los datos recopilados.
- **Concentración de datos:** Identifica rápidamente cuál intervalo de clase agrupa la mayor cantidad de elementos acumulados.
- **Límites reales:** Define con precisión dónde empieza y termina cada grupo de datos sin dejar vacíos intermedios.

### Polígono de frecuencia
Es un gráfico de línea en el cual se toman los puntos medios de cada clase para establecer la escala horizontal. La escala vertical está representada por la frecuencia.

#### Ejemplo gráfico
<img src="https://cdn.kastatic.org/ka-perseus-images/9ee45b78c736ce8fb194a2f9bde1e1494a0be8e3.png" Alt="PoligonoFrecuencias" width="500">

#### Interpretaciones Generales
- **Tendencia del comportamiento:** Permite ver las subidas y bajadas del fenómeno estudiado mediante líneas continuas.
- **Punto central:** Utiliza la marca de clase para representar el valor medio de cada intervalo evaluado.
- **Comparación de series:** Facilita superponer dos o más distribuciones distintas en un mismo plano cartesiano.

### Ojivas
Es un gráfico de línea en el cual se toman los límites de clase para representar las frecuencias acumuladas "menos de" o "más de".

#### Ejemplo gráfico
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR2VasEROk4SelZXpYNHuXM9N7eRagnqiWjaDn0GVxJRQE4jY54lcReR4UB&s=10" Alt="Ojivas" width="500">
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjju57buTlsMEuomVWS7KHaV6Q9IN1wMS1j8E36PhzlBgXRL3-pMNGCHS4kS1zPfHPu6d8XEGLAp7ZanDSgBfBqL7J56NBnVNMTHl4IhIs1Pib4YrPo6d80o7ypKtOOZlJ4ShVS2mPdz4I/s1600/ojivas.jpg" Alt="Ojivas2" width="500">

#### Interpretaciones Generales
- **Análisis acumulativo:** Indica cuántos datos se encuentran por encima o por debajo de un valor específico.
- **Cálculo de percentiles:** Ayuda a localizar la mediana, cuartiles y porcentajes de posición de forma visual.
- **Trayectoria visual:** La curva "menos de" siempre asciende, mientras que la curva "más de" siempre desciende.

---

## R — Histograma (variables continuas)

Utilice la variable talla de la base datos_estudiantes.

```r
# determinando los valores mínimo y máximo
min(datos_estudiantes$talla)
max(datos_estudiantes$talla)

# definiendo la base de datos y la variable a graficar
ggplot(data = datos_estudiantes,
       aes(x = talla)) +
  geom_histogram(breaks = seq(150, 190, 5),
                 col = 'black',
                 fill = 'green',
                 alpha = 0.4,
                 closed = "left") +
  labs(x = "Estatura",
       y = "Cantidad",
       title = "Figura 3. UNA. Distribución de estudiantes según estatura. I ciclo 2025") +
  theme_bw() +
  theme(plot.background = element_blank(),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        panel.border = element_blank()) +
  theme(axis.line = element_line(color = "black")) +
  theme(axis.text.x = element_text(face = "plain", size = 11, family = "Times", angle = 0, color = "black"),
        axis.text.y = element_text(face = "plain", size = 11, family = "Times", angle = 0, color = "black", hjust = 1),
        axis.title = element_text(face = "bold", size = 11, family = "Times")) +
  theme(plot.title = element_text(face = "plain", size = 11, family = "Times")) +
  scale_x_continuous(breaks = seq(150, 190, 5)) +
  scale_y_continuous(breaks = seq(0, 10, 2))
```

## R — Polígono de frecuencias

```r
min(datos_estudiantes$talla)
max(datos_estudiantes$talla)

ggplot(data = datos_estudiantes,
       aes(x = talla)) +
  geom_freqpoly(breaks = seq(150, 190, 5),
                 col = 'black',
                 closed = "left") +
  labs(x = "Estatura",
       y = "Cantidad",
       title = "Figura 4. UNA. Distribución de estudiantes según estatura. I ciclo 2025") +
  theme_bw() +
  theme(plot.background = element_blank(),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        panel.border = element_blank()) +
  theme(axis.line = element_line(color = "black")) +
  theme(axis.text.x = element_text(face = "plain", size = 10, family = "Times", angle = 0, color = "black"),
        axis.text.y = element_text(face = "plain", size = 11, family = "Times", angle = 0, color = "black", hjust = 1),
        axis.title = element_text(face = "bold", size = 11, family = "Times")) +
  theme(plot.title = element_text(face = "plain", size = 11, family = "Times")) +
  scale_x_continuous(breaks = seq(147.5, 192.5, 5)) +
  scale_y_continuous(breaks = seq(0, 10, 2))
```

## R — Distribución de frecuencia de variables continuas

```r
# usando la función fdt del paquete fdth
if(!require("fdth")){
  install.packages("fdth")
  library("fdth")
}

min(datos_estudiantes$talla)
max(datos_estudiantes$talla)

dist_continua <- fdt(x = datos_estudiantes$talla, 
                     start = 150, 
                     end = 190, 
                     h = 5)

dist_continua <- data.frame(dist_continua)
dist_continua <- dist_continua[,c(1,2,4,5,6)] 
colnames(dist_continua) <- c("Estatura", "Frecuencia_Absoluta", "Frecuencia_Porcentaje", "Acumulada_Absoluta", "Acumulada_Porcentaje")

titulo <- c("UNA. Distribución de estudiantes según estatura. I ciclo 2025")

hacer.flextable <- function(data) {
  if(!require("flextable")){
    install.packages("flextable")
    library("flextable")
  }
  dist_continua <- flextable(data = dist_continua, cwidth = 1)
  dist_continua <- align(x = dist_continua, align = "center", part = "all")
  dist_continua <- set_caption(x = dist_continua, caption = titulo)
  dist_continua <- colformat_double(dist_continua, j=c(3, 5), decimal.mark=",", digits = 2, big.mark = "")
  dist_continua <- separate_header(x = dist_continua)
  return(autofit(dist_continua))
}

hacer.flextable(dist_continua)
```

## R — Distribución de frecuencia de variables discretas

```r
tabla_1 <- table(datos_estudiantes$creditos) 
prop_tabla_1 <- prop.table(tabla_1) 
prop_tabla_1 <- round(prop_tabla_1*100, 2)
porcentaje <- as.vector(prop_tabla_1)

acum_cantidad <- cumsum(tabla_1)
acum_porcentaje <- cumsum(porcentaje)

distribucion <- data.frame(tabla_1, porcentaje, acum_cantidad, acum_porcentaje) 
colnames(distribucion) <- c("Créditos", "Frecuencia_Absoluta", "Frecuencia_Porcentaje", "Acumulada_Absoluta", "Acumulada_Porcentaje")

titulo <- c("UNA. Distribución de estudiantes según cantidad de créditos aprobados. I ciclo 2025")

hacer.flextable <- function(data) {
  if(!require("flextable")){
    install.packages("flextable")
    library("flextable")
  }
  distribucion <- flextable(data = distribucion, cwidth = 1)
  distribucion <- align(x = distribucion, align = "center", part = "all")
  distribucion <- set_caption(x = distribucion, caption = titulo)
  distribucion <- colformat_double(distribucion, j=c(3, 5), decimal.mark=",", digits = 2, big.mark = "")
  distribucion <- separate_header(x = distribucion)
  return(autofit(distribucion))
}

hacer.flextable(distribucion)
```
