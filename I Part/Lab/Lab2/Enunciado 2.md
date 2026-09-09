# MAT006 Probabilidad y Estadística
## Práctica Laboratorio 1, II Ciclo 2026

**Facultad de Ciencias Exactas y Naturales**
**Escuela de Matemática**
**Universidad Nacional**
26 de agosto de 2026

---

## Indicaciones específicas

1. Descargue la base de datos **salud mental**.
2. Abra un archivo R Markdown cuyo título sea **Laboratorio 1** y como autor incluya su **nombre completo**.
3. Cargue la base de datos suministrada para proceder a contestar cada una de las preguntas que se plantean a continuación.
4. Compile el documento para asegurarse que es posible generar el archivo en formato HTML, WORD o PDF.

---

## Información de la base de datos

Suponga que el Departamento de Bienestar Estudiantil de la Universidad Nacional realizó un estudio durante el primer semestre del año 2026 con el objetivo de evaluar algunos indicadores relacionados con la salud mental y el bienestar psicológico de la comunidad universitaria. El estudio buscó identificar diferencias entre estudiantes y profesores en variables relacionadas con el estrés, hábitos de sueño, carga académica y bienestar.

La investigación fue desarrollada entre los meses de marzo y mayo de 2026, mediante la aplicación de un cuestionario en línea. Se seleccionó una muestra aleatoria estratificada de 100 personas, respetando la proporción de estudiantes y profesores de la población. Algunas de las variables sobre las que se obtuvieron mediciones durante dicho periodo se observan en la Tabla 1. Los datos fueron proporcionados por el Departamento de Bienestar Estudiantil.

### Tabla 1: UNA. Descripción de algunas de las variables incluidas en el estudio

| Variable | Descripción |
|:---|:---|
| **Rol** | Tipo de participante: ( ) Docente ( ) Estudiante |
| **Facultad** | Tipo de facultad de procedencia |
| **Cursos** | Número de cursos matriculados o impartidos |
| **Sesiones** | Número de sesiones de apoyo sicológico recibidas |
| **Promedio** | Promedio académico del estudiante o calificación promedio del docente |
| **Puntaje** | Puntaje obtenido en un cuestionario de bienestar psicológico |

---

## Preguntas

### 1. Con base en el contexto anterior, conteste lo que se le solicita.

* **a)** Construya una distribución de frecuencias para la variable **Cursos**. Debe incluir las frecuencias simples absoluta y relativa, las frecuencias acumuladas (menos de) absolutas y relativas, así como los elementos de presentación vistos en clase.

* **b)** Construya una distribución de frecuencias para la variable **Puntaje**. Debe incluir las frecuencias simples absoluta y relativa, las frecuencias acumuladas (menos de) absolutas y relativas, así como los elementos de presentación vistos en clase.

* **c)** Construya una gráfica adecuada para representar la distribución de la variable **Promedio**. Utilice intervalos de tamaño 5 e incluya los elementos de presentación vistos en clase.

* **d)** Construya una representación gráfica que permita apreciar la distribución de la variable **Facultad**. Debe incluir los elementos de presentación vistos en clase.

* **e)** Construya una representación gráfica que permita comparar la distribución de la variable **Cursos** entre estudiantes y docentes. Debe incluir los elementos de presentación vistos en clase.

* **f)** Construya una representación gráfica que permita apreciar la distribución de la variable **Puntaje** obtenido por los docentes. Debe incluir los elementos de presentación vistos en clase.

* **g)** Calcule la media, la mediana, la moda, los percentiles 25 y 75 y la desviación estándar de la variable **Puntaje** obtenido por los docentes.

---

# Respuestas

# Laboratorio 1 — Solución
### MAT006 Probabilidad y Estadística — II Ciclo 2026
### Base de datos: *salud mental* (n = 100: 50 estudiantes, 50 profesores)

---

## Preparación de los datos

```r
library(readxl)
library(dplyr)
library(ggplot2)

datos <- read_excel("salud_mental.xlsx")
str(datos)
```

Variables usadas en este laboratorio: `Rol`, `Facultad`, `Cursos`, `Sesiones_Apoyo`,
`Promedio`, `Puntaje_Bienestar`.

---

## a) Distribución de frecuencias de la variable *Cursos*

`Cursos` es una variable cuantitativa **discreta** (toma los valores 1 a 7), por lo que
la distribución se construye por valores individuales, sin necesidad de intervalos.

```r
n <- nrow(datos)

tabla_cursos <- datos %>%
  count(Cursos, name = "ni") %>%
  arrange(Cursos) %>%
  mutate(
    fi  = round(ni / n, 3),
    Ni  = cumsum(ni),
    Fi  = round(Ni / n, 3)
  )
tabla_cursos
```

**Tabla 1. Distribución de frecuencias — Cursos matriculados/impartidos (n = 100)**

| Cursos ($x_i$) | $n_i$ | $f_i$ | Menos de | $N_i$ | $F_i$ |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | 14 | 0.14 | Menos de 2 | 14  | 0.14 |
| 2 |  9 | 0.09 | Menos de 3 | 23  | 0.23 |
| 3 | 19 | 0.19 | Menos de 4 | 42  | 0.42 |
| 4 | 22 | 0.22 | Menos de 5 | 64  | 0.64 |
| 5 | 20 | 0.20 | Menos de 6 | 84  | 0.84 |
| 6 |  7 | 0.07 | Menos de 7 | 91  | 0.91 |
| 7 |  9 | 0.09 | Menos de 8 | 100 | 1.00 |
| **Total** | **100** | **1.00** | | | |

**Interpretación:** el 22 % de las personas encuestadas tiene matriculados o
imparte exactamente 4 cursos (la categoría más frecuente), y el 64 % tiene
5 cursos o menos (`Fi` en "menos de 6").

---

## b) Distribución de frecuencias de la variable *Puntaje* (bienestar psicológico)

`Puntaje_Bienestar` es una variable **continua**, por lo que se agrupa en
intervalos de clase. Usando la regla de Sturges:

$$k = 1 + 3.322\log_{10}(100) \approx 7.64 \Rightarrow k = 8 \text{ clases}$$

Con un rango de 21.0 a 94.3, se usa una amplitud de clase $c = 10$, iniciando en 20.

```r
tabla_puntaje <- datos %>%
  mutate(clase = cut(Puntaje_Bienestar,
                      breaks = seq(20, 100, by = 10),
                      right = FALSE, include.lowest = TRUE)) %>%
  count(clase, name = "ni") %>%
  mutate(
    fi = round(ni / n, 3),
    Ni = cumsum(ni),
    Fi = round(Ni / n, 3)
  )
tabla_puntaje
```

**Tabla 2. Distribución de frecuencias — Puntaje de bienestar psicológico (n = 100)**

| Intervalo de clase | Marca de clase | $n_i$ | $f_i$ | Menos de | $N_i$ | $F_i$ |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [20, 30) | 25 | 14 | 0.14 | Menos de 30  | 14  | 0.14 |
| [30, 40) | 35 | 12 | 0.12 | Menos de 40  | 26  | 0.26 |
| [40, 50) | 45 | 18 | 0.18 | Menos de 50  | 44  | 0.44 |
| [50, 60) | 55 | 13 | 0.13 | Menos de 60  | 57  | 0.57 |
| [60, 70) | 65 | 11 | 0.11 | Menos de 70  | 68  | 0.68 |
| [70, 80) | 75 | 11 | 0.11 | Menos de 80  | 79  | 0.79 |
| [80, 90) | 85 | 13 | 0.13 | Menos de 90  | 92  | 0.92 |
| [90, 100)| 95 |  8 | 0.08 | Menos de 100 | 100 | 1.00 |
| **Total** | | **100** | **1.00** | | | |

**Interpretación:** la clase modal es [40, 50), con el 18 % de los datos; el
44 % de la comunidad universitaria obtuvo un puntaje de bienestar inferior a 50
puntos, lo que sugiere que una proporción considerable presenta niveles bajos
de bienestar psicológico.

---

## c) Gráfico de la variable *Promedio* (intervalos de tamaño 5)

```r
ggplot(datos, aes(x = Promedio)) +
  geom_histogram(breaks = seq(55, 100, by = 5),
                 fill = "steelblue", color = "white", closed = "left") +
  labs(title = "Distribución del promedio académico/calificación",
       x = "Promedio", y = "Frecuencia absoluta") +
  theme_minimal()
```

**Tabla de apoyo (intervalos de amplitud 5):**

| Intervalo | $n_i$ |
|:---:|:---:|
| [55, 60) | 9  |
| [60, 65) | 14 |
| [65, 70) | 9  |
| [70, 75) | 13 |
| [75, 80) | 12 |
| [80, 85) | 12 |
| [85, 90) | 5  |
| [90, 95) | 16 |
| [95,100) | 10 |

**Interpretación:** el histograma muestra una distribución con varias
concentraciones (multimodal), destacando el intervalo [90, 95) como el de
mayor frecuencia (16 personas), seguido de [60, 65).

---

## d) Gráfico de la variable *Facultad*

`Facultad` es cualitativa nominal, por lo que se representa con un **gráfico de
barras**.

```r
ggplot(datos, aes(x = fct_infreq(Facultad))) +
  geom_bar(fill = "darkorange") +
  labs(title = "Distribución por Facultad de procedencia",
       x = "Facultad", y = "Frecuencia absoluta") +
  theme_minimal()
```
*(requiere `library(forcats)` para `fct_infreq`, o bien usar `table()` y ordenar manualmente)*

| Facultad | $n_i$ | $f_i$ |
|:---|:---:|:---:|
| Sociales | 25 | 0.25 |
| Educación | 23 | 0.23 |
| Salud | 18 | 0.18 |
| Ciencias | 18 | 0.18 |
| Ingeniería | 16 | 0.16 |

**Interpretación:** la Facultad de Sociales concentra la mayor proporción de
participantes (25 %), mientras que Ingeniería es la de menor representación
(16 %).

---

## e) Comparación de *Cursos* entre estudiantes y docentes

```r
ggplot(datos, aes(x = factor(Cursos), fill = Rol)) +
  geom_bar(position = "dodge") +
  labs(title = "Cursos matriculados/impartidos según Rol",
       x = "Número de cursos", y = "Frecuencia absoluta", fill = "Rol") +
  theme_minimal()
```

| Cursos | Estudiante | Profesor |
|:---:|:---:|:---:|

```r
table(datos$Cursos, datos$Rol)
```

**Interpretación:** el gráfico de barras agrupadas permite observar si la carga
de cursos se comporta de forma similar entre ambos roles o si, por ejemplo,
los docentes tienden a concentrarse en un número distinto de cursos que los
estudiantes.

---

## f) Gráfico de *Puntaje* obtenido por los docentes

```r
docentes <- datos %>% filter(Rol == "Profesor")

ggplot(docentes, aes(x = Puntaje_Bienestar)) +
  geom_histogram(breaks = seq(20, 100, by = 10),
                 fill = "seagreen", color = "white", closed = "left") +
  labs(title = "Puntaje de bienestar psicológico — Docentes",
       x = "Puntaje", y = "Frecuencia absoluta") +
  theme_minimal()
```

**Interpretación:** entre los 50 docentes, el puntaje de bienestar muestra una
dispersión amplia (de 21.0 a 94.3 puntos), sin una concentración clara en un
único intervalo, lo que indica heterogeneidad en el bienestar psicológico
percibido por el personal docente.

---

## g) Medidas descriptivas del *Puntaje* de los docentes

```r
docentes <- datos %>% filter(Rol == "Profesor")
x <- docentes$Puntaje_Bienestar

media    <- mean(x)
mediana  <- median(x)
moda_fun <- function(v) {
  t <- table(v)
  as.numeric(names(t)[t == max(t)])
}
moda     <- moda_fun(x)
p25      <- quantile(x, 0.25)
p75      <- quantile(x, 0.75)
desv_est <- sd(x)

c(media = media, mediana = mediana, p25 = p25, p75 = p75, sd = desv_est)
moda
```

**Resultados (n = 50 docentes):**

| Medida | Valor |
|:---|:---:|
| Media ($\bar{x}$) | 56.49 |
| Mediana ($Me$) | 52.30 |
| Moda ($Mo$) | 22.7, 45.0 y 52.1 (trimodal, cada valor se repite 2 veces) |
| Percentil 25 ($P_{25}$) | 39.60 |
| Percentil 75 ($P_{75}$) | 77.45 |
| Desviación estándar ($s$) | 22.48 |

**Interpretación:** el puntaje promedio de bienestar de los docentes es
56.49, ligeramente superior a la mediana (52.30), lo que sugiere una leve
asimetría positiva (algunos docentes con puntajes altos elevan la media). El
50 % central de los docentes obtuvo entre 39.60 y 77.45 puntos (rango
intercuartílico ≈ 37.85), y la desviación estándar de 22.48 indica una
dispersión considerable en el bienestar psicológico reportado por este grupo.
No existe una moda única y representativa, ya que solo tres valores se
repiten (cada uno dos veces), lo cual es habitual en variables continuas con
muchos decimales.
