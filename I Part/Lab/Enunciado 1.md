# Laboratorio 1: Presentación de la información, RStudio, Distribuciones de frecuencia y Medidas descriptivas

## Problema 1

Una tienda de conveniencia desea analizar el comportamiento de compra de sus clientes durante el mes de julio de 2026. Para ello cuenta con la siguiente base de datos, guardada en el archivo `datos_clientes.xlsx`:

| ID | Sexo | Zona    | Metodo_pago  | Compra |
|:--:|:----:|:-------:|:------------:|:------:|
| 1  | H    | Urbana  | Efectivo     | 12500  |
| 2  | M    | Urbana  | Tarjeta      | 8300   |
| 3  | M    | Rural   | Transferencia| 15200  |
| 4  | H    | Rural   | Efectivo     | 9600   |
| 5  | M    | Urbana  | Tarjeta      | 21000  |
| 6  | H    | Urbana  | Efectivo     | 7400   |
| 7  | M    | Rural   | Tarjeta      | 13800  |
| 8  | H    | Urbana  | Transferencia| 18700  |
| 9  | M    | Rural   | Efectivo     | 6200   |
| 10 | H    | Urbana  | Tarjeta      | 11900  |

* a) Escriba el código en RStudio necesario para importar la base de datos `datos_clientes.xlsx` como el objeto `datos_clientes`.
* b) Elabore, mediante código de R, una tabla de frecuencias absolutas y relativas para la variable `Zona`, usando las funciones `table()` y `prop.table()`, y muéstrela con `flextable`.
* c) Construya una tabla cruzada de `Sexo` según `Metodo_pago`, con los porcentajes calculados por columna.
* d) Elabore un gráfico de barras horizontal (`coord_flip()`) para la variable `Metodo_pago`, ordenando las barras de mayor a menor frecuencia con `fct_infreq()`.

## Problema 2

Una empresa de tecnología quiere estudiar la cantidad de ventas semanales que realiza cada persona vendedora. Se cuenta con la base `datos_ventas.xlsx`:

| ID | Vendedor  | Ventas_semana | Region  |
|:--:|:---------:|:--------------:|:-------:|
| 1  | Ana       | 5               | Norte   |
| 2  | Luis      | 3               | Sur     |
| 3  | Karla     | 5               | Norte   |
| 4  | Mario     | 2               | Central |
| 5  | Sofia     | 4               | Sur     |
| 6  | Diego     | 5               | Norte   |
| 7  | Paula     | 3               | Central |
| 8  | Jose      | 4               | Sur     |
| 9  | Elena     | 2               | Norte   |
| 10 | Ricardo   | 4               | Central |
| 11 | Vero      | 3               | Sur     |
| 12 | Andres    | 5               | Norte   |

* a) Escriba el código para importar la base `datos_ventas.xlsx` en RStudio.
* b) Construya, mediante código, una tabla de distribución de frecuencias para la variable `Ventas_semana` que incluya frecuencia absoluta, relativa, absoluta acumulada y relativa acumulada (use `table()`, `prop.table()` y `cumsum()`).
* c) Elabore un gráfico de bastones o barras verticales (`geom_bar()`) para representar la variable `Ventas_semana`.
* d) A partir de la tabla del punto b), interprete la frecuencia relativa acumulada correspondiente al valor 4.

## Problema 3

En un centro de salud se desea analizar el peso (en kg) de un grupo de personas pacientes. La base `datos_pacientes.xlsx` contiene:

| ID | Edad | Peso | Talla | Sexo |
|:--:|:----:|:----:|:-----:|:----:|
| 1  | 34   | 68.2 | 165   | M    |
| 2  | 45   | 82.5 | 172   | H    |
| 3  | 29   | 59.4 | 160   | M    |
| 4  | 51   | 91.0 | 178   | H    |
| 5  | 38   | 74.8 | 168   | M    |
| 6  | 60   | 88.3 | 174   | H    |
| 7  | 42   | 65.1 | 162   | M    |
| 8  | 27   | 70.6 | 170   | H    |
| 9  | 55   | 95.2 | 180   | H    |
| 10 | 33   | 61.7 | 163   | M    |
| 11 | 48   | 79.4 | 169   | H    |
| 12 | 36   | 67.9 | 166   | M    |

* a) Escriba el código para importar la base `datos_pacientes.xlsx` en RStudio.
* b) Utilizando la fórmula de Sturges de forma manual, determine el número de clases recomendado para agrupar la variable `Peso` (n = 12).
* c) Escriba el código en R que construye la tabla de distribución de frecuencias de la variable `Peso` utilizando la función `fdt()` del paquete `fdth`, y muéstrela con `flextable`.
* d) Escriba el código en R que construye el histograma de la variable `Peso` con `ggplot2`, utilizando los límites de clase obtenidos en el punto anterior.

## Problema 4

Una persona docente desea analizar el rendimiento académico de su grupo en el curso de Estadística. Cuenta con la base `datos_notas.xlsx`:

| ID | Estudiante | Nota_parcial1 | Nota_parcial2 | Nota_final |
|:--:|:----------:|:--------------:|:--------------:|:----------:|
| 1  | E1         | 72              | 68              | 70         |
| 2  | E2         | 85              | 90              | 88         |
| 3  | E3         | 60              | 55              | 58         |
| 4  | E4         | 95              | 92              | 93         |
| 5  | E5         | 78              | 80              | 79         |
| 6  | E6         | 65              | 70              | 68         |
| 7  | E7         | 88              | 84              | 86         |
| 8  | E8         | 50              | 60              | 55         |
| 9  | E9         | 73              | 75              | 74         |
| 10 | E10        | 91              | 89              | 90         |

* a) Escriba el código para importar la base `datos_notas.xlsx` en RStudio.
* b) Escriba el código en R que calcule el promedio, la mediana y los cuartiles de la variable `Nota_final`, utilizando las funciones `mean()`, `median()` y `quantile()`.
* c) Escriba el código en R que calcule el percentil 90 de `Nota_final` e interprete el resultado obtenido.
* d) Escriba el código en R que construya un diagrama de caja (boxplot) para la variable `Nota_final` utilizando `ggplot2`.

## Problema 5

Una fábrica desea comparar la producción de dos turnos en dos plantas distintas. Se cuenta con la base `datos_produccion.xlsx`:

| ID | Planta | Turno | Unidades_producidas | Defectos |
|:--:|:------:|:-----:|:---------------------:|:--------:|
| 1  | A      | Dia   | 420                    | 5        |
| 2  | A      | Noche | 380                    | 8        |
| 3  | B      | Dia   | 450                    | 3        |
| 4  | B      | Noche | 400                    | 6        |
| 5  | A      | Dia   | 410                    | 4        |
| 6  | A      | Noche | 375                    | 9        |
| 7  | B      | Dia   | 460                    | 2        |
| 8  | B      | Noche | 395                    | 7        |
| 9  | A      | Dia   | 430                    | 5        |
| 10 | B      | Noche | 405                    | 6        |

* a) Escriba el código para importar la base `datos_produccion.xlsx` en RStudio.
* b) Escriba el código en R que calcule el rango, la varianza y la desviación estándar de la variable `Unidades_producidas`, utilizando `range()`, `var()` y `sd()`.
* c) Escriba el código en R que elabore un gráfico de barras comparativo de `Unidades_producidas` según `Turno` y `Planta`, utilizando `ggplot2` con `position = "dodge"`.
* d) Calcule manualmente el coeficiente de variación (CV = desviación estándar / promedio × 100) de `Unidades_producidas` e interprete su resultado.

---

# RESPUESTAS

## Problema 1

* a)
```
library(readxl)
datos_clientes <- read_excel("C:/Users/usuario/Documents/datos_clientes.xlsx")
```

* b)
```
tabla_zona <- table(datos_clientes$Zona)
prop_zona <- round(prop.table(tabla_zona) * 100, 2)
distribucion <- data.frame(tabla_zona, as.vector(prop_zona))
colnames(distribucion) <- c("Zona", "Frecuencia", "Porcentaje")

library(flextable)
flextable(distribucion)
```

* c)
```
tabla_cruzada <- table(datos_clientes$Sexo, datos_clientes$Metodo_pago)
porc_columna <- round(prop.table(tabla_cruzada, margin = 2) * 100, 2)
porc_columna
```

* d)
```
library(ggplot2)
library(forcats)

ggplot(data = datos_clientes, aes(x = fct_infreq(Metodo_pago))) +
  geom_bar(fill = "lightblue", color = "black") +
  coord_flip() +
  labs(x = "Metodo de pago", y = "Cantidad",
       title = "Distribucion de clientes segun metodo de pago")
```

## Problema 2

* a)
```
library(readxl)
datos_ventas <- read_excel("C:/Users/usuario/Documents/datos_ventas.xlsx")
```

* b)
```
tabla_1 <- table(datos_ventas$Ventas_semana)
porcentaje <- round(prop.table(tabla_1) * 100, 2)
acum_cantidad <- cumsum(tabla_1)
acum_porcentaje <- cumsum(porcentaje)

distribucion <- data.frame(tabla_1, as.vector(porcentaje),
                            acum_cantidad, acum_porcentaje)
colnames(distribucion) <- c("Ventas_semana", "Frecuencia",
                             "Porcentaje", "Acum_Frecuencia", "Acum_Porcentaje")
distribucion
```

* c)
```
library(ggplot2)

ggplot(data = datos_ventas, aes(x = Ventas_semana)) +
  geom_bar(fill = "orange", color = "black") +
  labs(x = "Ventas por semana", y = "Cantidad de vendedores",
       title = "Distribucion de vendedores segun ventas semanales")
```

* d) La frecuencia relativa acumulada para el valor 4 indica el porcentaje de personas vendedoras cuyas ventas semanales fueron de 4 unidades o menos; representa la proporción del total de vendedores que se ubica en ese nivel de ventas o por debajo de él.

## Problema 3

* a)
```
library(readxl)
datos_pacientes <- read_excel("C:/Users/usuario/Documents/datos_pacientes.xlsx")
```

* b) Con n = 12: numero de clases = 1 + 3.332 * log(12) ≈ 1 + 3.332(1.079) ≈ 4.60 ≈ 5 clases.

* c)
```
if(!require("fdth")){
  install.packages("fdth")
  library("fdth")
}

dist_peso <- fdt(x = datos_pacientes$Peso, start = 55, end = 100, h = 9)
dist_peso <- data.frame(dist_peso)

library(flextable)
flextable(dist_peso)
```

* d)
```
library(ggplot2)

ggplot(data = datos_pacientes, aes(x = Peso)) +
  geom_histogram(breaks = seq(55, 100, 9), col = "black",
                 fill = "lightgreen", alpha = 0.5, closed = "left") +
  labs(x = "Peso (kg)", y = "Cantidad de pacientes",
       title = "Distribucion de pacientes segun peso")
```

## Problema 4

* a)
```
library(readxl)
datos_notas <- read_excel("C:/Users/usuario/Documents/datos_notas.xlsx")
```

* b)
```
mean(datos_notas$Nota_final)
median(datos_notas$Nota_final)
quantile(datos_notas$Nota_final)
```

* c)
```
quantile(datos_notas$Nota_final, probs = 0.90)
```
Interpretación: el 90 % del estudiantado obtuvo una nota final menor o igual al valor calculado, y solo el 10 % restante obtuvo una nota superior a ese valor.

* d)
```
library(ggplot2)

ggplot(data = datos_notas, aes(y = Nota_final)) +
  geom_boxplot(fill = "lightyellow", color = "black") +
  labs(y = "Nota final", title = "Diagrama de caja de la nota final")
```

## Problema 5

* a)
```
library(readxl)
datos_produccion <- read_excel("C:/Users/usuario/Documents/datos_produccion.xlsx")
```

* b)
```
range(datos_produccion$Unidades_producidas)
var(datos_produccion$Unidades_producidas)
sd(datos_produccion$Unidades_producidas)
```

* c)
```
library(ggplot2)

ggplot(data = datos_produccion, aes(x = Planta, y = Unidades_producidas, fill = Turno)) +
  geom_bar(stat = "identity", position = "dodge", color = "black") +
  labs(x = "Planta", y = "Unidades producidas",
       title = "Produccion segun planta y turno")
```

* d) CV = (sd / promedio) × 100. Un CV bajo (por ejemplo, menor al 15-20 %) indica que la producción es relativamente homogénea entre las observaciones; un CV alto indicaría mayor variabilidad relativa en la cantidad de unidades producidas.
