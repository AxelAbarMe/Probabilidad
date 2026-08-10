# Distribuciones de frecuencia

## Clases

Grupos en los que se distribuye la información.

- Exhaustivas: todas las observaciones deben ser incluidas en alguna de las clases
- Mutuamente excluyentes: una observación no puede ser incluida en más de una clase.

### Frecuencia absoluta
Número de observaciones presentes en cada clase. Llamada frecuencia
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
- Redondeo hacia arriba.
- Redondeo hacia abajo.

#### Redondeo usual
Mayor a 5 exacto, se aumenta una unidad

|Original|Redondeo
|:--:|:--:|
|137,502 -> |138
|42,650 -> |43

#### Redondeo hacia arriba.
Se conserva el último dígito y el resto se elimina

|Original|Redondeo
|:--:|:--:|
|137,502 -> |137
|42,650 -> |42
|42,000 -> |42

#### Redondeo hacia abajo.
Último dígito se aumenta una unidad, excepto cuando va seguido de ceros

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
Se ubican al principio o al final de la distribución con el fin de incorporar todos aquellos datos que se apartan mucho,

## Ejemplo Límites de los pesos


1. Al utilizar la fórmula de Sturges se tiene el número de clases adecuado es: 1 + 3,332 ∗ log(40) = 6, 33 ≈ 6
2. El rango del conjunto de datos está dado por 78 − 52 = 26.
3. En ancho de cada clase puede obtenerse como: a = 26 ÷ 6 ≈ 5

> Fórmula Punto Medio: Xi = (Li+Ls)/2.  Con Xi siendo punto medio, Li siendo Límite inferior y Ls siendo Límite superior

|Rangos|Punto Medio
|:---:|:---:|
|50-55|52,5
|55-60|57,5
|60-65|62,5
|65-70|67,5
|70-75|72,5
|75-80|77,5

<img src="../../img/1.4_FrecuenciasTable.png" alt="RangosTabla" width="600">

# Representación gráfica
Para representar gráficamente una distribución de frecuencias de una variable continua se utilizan: 
- El histograma
- El polígono de frecuencias
- Las ojivas

## Histograma

Es un gráfico de barras verticales en el que las barras no guardan espacios entre sí. Para construirlo se define una escala horizontal y en ella se definen los límites reales de todas las clases de la distribución.

### Ejemplo gráfico
<img src="https://estadistica-dma.ulpgc.es/cursoR4ULPGC/9c-grafHistograma_files/figure-html/unnamed-chunk-3-1.png" Alt="Histograma" width="500">

### Interpretaciones Generales
- Forma de la distribución: Muestra visualmente la simetría, sesgo o uniformidad de todos los datos recopilados.
- Concentración de datos: Identifica rápidamente cuál intervalo de clase agrupa la mayor cantidad de elementos acumulados.
- Límites reales: Define con precisión dónde empieza y termina cada grupo de datos sin dejar vacíos intermedios.

## Polígono de frecuencia

Es un gráfico de línea en el cual se toman los puntos medios de cada clase para establecer la escala horizontal. La escala vertical está representada por la frecuencia.

### Ejemplo gráfico
<img src="https://cdn.kastatic.org/ka-perseus-images/9ee45b78c736ce8fb194a2f9bde1e1494a0be8e3.png" Alt="PoligonoFrecuencias" width="500">

### Interpretaciones Generales
- Tendencia del comportamiento: Permite ver las subidas y bajadas del fenómeno estudiado mediante líneas continuas.
- Punto central: Utiliza la marca de clase para representar el valor medio de cada intervalo evaluado.
- Comparación de series: Facilita superponer dos o más distribuciones distintas en un mismo plano cartesiano.

## Ojivas

Es un gráfico de línea en el cual se toman los límites de clase para representar las frecuencias acumuladas menos de o más de.

### Ejemplo gráfico
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR2VasEROk4SelZXpYNHuXM9N7eRagnqiWjaDn0GVxJRQE4jY54lcReR4UB&s=10" Alt="Ojivas" width="500">

<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjju57buTlsMEuomVWS7KHaV6Q9IN1wMS1j8E36PhzlBgXRL3-pMNGCHS4kS1zPfHPu6d8XEGLAp7ZanDSgBfBqL7J56NBnVNMTHl4IhIs1Pib4YrPo6d80o7ypKtOOZlJ4ShVS2mPdz4I/s1600/ojivas.jpg" Alt="Ojivas2" width="500">

### Interpretaciones Generales
- Análisis acumulativo: Indica cuántos datos se encuentran por encima o por debajo de un valor específico.
- Cálculo de percentiles: Ayuda a localizar la mediana, cuartiles y porcentajes de posición de forma visual.
- Trayectoria visual: La curva "menos de" siempre asciende, mientras que la curva "más de" siempre desciende.
