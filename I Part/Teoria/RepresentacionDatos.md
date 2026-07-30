# Presentación de la información
## Formas más comunes de presentación de información
- Presentación textual: Consiste en introducir cifras o datos dentro de una redacción de un informe
- Presentación tabular: Consiste en formatear la información a través de cuadros o tablas utilizando solamente cifras.
- Presentación gráfica: Consiste en utilizar recursos como figuras o dibujos para mostrar los datos.
## Cuadros o tablas
Arreglo en forma de filas y columnas con los datos ordenados y clasificados según algún criterio destacado para que la información sea interpretada correctamente.
### Componentes
- Título
- Encabezados
- Columna matriz
- Cuerpo o contenido
- Nota preliminar
- Nota al pie
- Fuente
### Titulo
Parte superior del cuadro, máximo entre 15 a 25 palabras, para dar forma clara de una idea del tipo de información presentada.
#### Debe incluir:
- Dónde se recogieron los datos, a qué lugar corresponden.
- Qué son los datos, a que se refieren.
- Cómo se clasifican los datos.
- Cuándo ocurrieron los hechos que representan los datos.
### Nota Preliminar
Colocado debajo del título, indica acerca a lo que se refiere algo del cuadro.
#### Ejemplo:
- En vez de colocar 10.000.000, se coloca 10 y se específica con una nota preliminar que esto se refiere a millones.
### Columna matriz
Se coloca la clasificación principal de la información
### Encabezados
Colocado en la parte superior del cuadro y en ella se indican otras clasificaciones de datos.
### Cuerpo
Contiene las cifras, datos obtenidos.
### Nota al pie
Es una nota específica colocada al final del cuadro, antes de la fuente, con el fin de aclarar sobre alguna cifra particular.
#### Ejemplo:
- Cifras tengan tiempo y alguna sea en un año no terminado, se agrega (1) con una nota al pie para especificar hasta qué fecha son válidos los datos.
### Fuente
Indica el origen de los datos, al final del cuadro.


## Ejemplo de tabla


| Encabezado | Encabezado | Encabezado | Encabezado |
|:------------:|:------------:|:------------:|:------------:|
|     .      |            |            |            |
| Col. Matriz| Texto      | Dato       |            |
| Total      |            |            |            |


## Formas de calcular porcentajes
- Porcentaje por columna
- Porcentaje por fila
- Porcentaje con respecto al total (Se toma en cuenta múltiples variables)


#### Tabla 1: Universidad Nacional. Distribución de estudiantes según cantidad de materias matriculadas. I Ciclo 2021
| Materias  | Estudiantes | Porcentaje |
|:---------:|:-----------:|:----------:|
|  2  | 7 | 17,5
|  3  | 10| 25,0
|  4  | 8 |20,0
|  6  | 7 |18,5
|  7  | 8 |20,0
|Total| 40|100,0|
##### Fuente: Departamento de Registro


#### Tabla 2: Universidad Nacional. Distribución de estudiantes por cantidad de materias matriculadas según zona de residencia. I Ciclo 2021
| Materias  | Urbano |  | Rural |   |
|:---------:|:-----------:|:---:|:---:|:---:|
| | Total |Porcentaje | Total|Porcentaje|
|  2  | 4 | 21,1 | 3 | 14,3
|  3  | 5 | 26,3 | 5 | 23,8
|  4  | 2 | 10,5 | 6 | 28,6
|  6  | 3 | 15,8 | 4 | 19,0
|  7  | 5 | 26,3 | 3 | 14,3
|Total| 19| 100,0| 21| 100,0
##### Fuente: Departamento de Registro


## Gráfica estadísticas


Una gráfica es un instrumento que tiene por objeto presentar datos numéricos por medio de magnitudes geométricas.
#### Se debe tomar en cuenta


- La gráfica debe tener proporciones adecuadas.
- Debe explicarse por sí mismo, por eso debe contar con título, leyendas, símbolos, escalas y fuentes.
- No se deben incluir muchas series de datos.
- Las escalas no deben desfigurar hechos o relaciones que se quieren mostrar.
- Debe ser sencillo, cómodo de interpretar y adecuado al tipo de información que se tiene.


### Series estadísticas


- Series cuantitativas
- Series cualitativas
- Series geográficas
- Series de tiempo


#### Series cuantitativas


Son aquellas en la que los datos estadísticos observados se han clasificado de acuerdo con una variable cuantitativa


#### Series Cualitativas


Se refieren a aquellas clasificaciones en que la característica de interés es una cualidad o atributo.


#### Series geográficas
Se presentan cuando la clasificación está basada en espacios geográficos.


#### Series cronológicas o de tiempo
Son aquellas en las cuales las características observadas han sido
clasificadas siguiendo un orden de tiempo.


### Ejemplos de gráficas


- Gráficas de barras
- Gráficas circulares
- Gráficas lineales
- Diagramas de dispersión
- Pictogramas
- Histograma
- Polígono de frecuencia
- Diagrama de Gantt


#### Gráfica de barras


- Horizontal: Son cualitativas o geográficas.
- Vertical: Son cronológicas o cuantitativa discreta.
#### Pueden ser:
- Simple: Comportamiento variable.
- Comparativas: Comparan los componentes de algún evento.
- Compuestas: Barra dividida en secciones que muestra componentes del fenómeno.
#### Debe tener:
- Título.
- Ejes.
- Escala.
- Fuente.
- Etiquetas.
- Geometría.
- Fondo blanco.


### Gráfica lineal
Gráficas de dos dimensiones usadas especialmente para representar series de tiempo o cronológicas.
#### Pueden ser:
- Aritmética
- Logarítmica
### Gráfica circular
La gráfica circular es un círculo, el cual se divide en tantos sectores como categorías se tienen en la variable. El área de cada uno de los sectores circulares refleja la importancia de la categoría que representa.

# R

- Ctrl + Enter para ejecutar

``` R
# Definición de variables

# Asignación y valor Int
a = 2
a <-2
2 -> a
# Valor string
b <-"Clase"
# Booleano T/F
logico <- T
# Imprimir en consola
a
(c <- T) # Asignación e imprimir
# Valor no disponible
nd <- NA
nd # Para mostrarlo
# Funciones
# Formato f(arg1,arg2,...)

# getwd() permite identificar directorio de trabajo
getwd()

# help() Solicitar ayuda en R
help(getwd)

# Cambiar directorio de trabajo
setwd("Route") # "/Users/eduardo/Documents/CursoR"

# Instalar paquetes externos
install.packages("faraway")

# Cargar Paquete
library(faraway)

# Observar paquetes instalados
library()

# Observar contenido de un paquete
library(help = faraway)

# Función class(): Determina tipo de objeto creado. class(x)
class(a) #Numeric
class(b) #Character
class(c) #Logical
class(plot) #Function
class(mtcars) #Data.frame

# Escribir varios códigos en una linea
class(a); class(b); class(c)

# Definir como numérico

d <- as.numeric(c) #Transforma bool a numeric

# Funciones ls() y rm()

# Ls() Observar objetos guardados
ls()
# Pattern busca similitud
ls(pattern = "7")
ls(pattern = "a")
ls(pattern = "^b") #Inicia con b

# Diferencia asignación = y <-
class(w = 3)
class(y <- 7)
# Igualdad es limitado, contrario a <-

# Funcion c(): Crea vectores con más de 1 elemento
residencia <- c("urbana","rural","urbana","urbana","rural")




 h <- 60369857



```








