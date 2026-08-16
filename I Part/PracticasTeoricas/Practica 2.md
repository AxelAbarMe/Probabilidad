# Práctica 2
> Presentación de la información y RStudio

## Tema: Presentación de la información

## Ejemplo 1
La empresa TechSol desea documentar la distribución de su personal. Para ello construye la siguiente tabla: "Tabla 3: Empresa TechSol. Distribución de empleados según departamento y nivel de estudio. II Semestre 2025", con fuente "Departamento de Recursos Humanos".
* a) Con base en el título de la tabla, indique qué cuatro aspectos debe reflejar (dónde, qué, cómo y cuándo se recolectaron los datos).
* b) ¿Qué elemento del cuadro contendría la clasificación principal de los datos (en este caso, los departamentos)?
* c) Si las cifras del cuerpo de la tabla estuvieran expresadas en miles de colones, ¿qué elemento del cuadro debe utilizarse para aclararlo y dónde se coloca?
* d) ¿Dónde se debe indicar el origen de los datos utilizados en la tabla?

## Ejemplo 2
Retome la Tabla 2 vista en el curso (Distribución de estudiantes por cantidad de materias matriculadas según zona de residencia), donde la zona urbana tiene 19 estudiantes y la zona rural 21, para un total de 40.

|Materias|	Urbano (Total)	|Rural (Total)|
|:--:|:--:|:--:|  
|2|	4|	3
|3|	5|	5
|4|	2|	6
|6|	3|	4
|7|	5|	3
|Total|	19|	21

* a) Identifique qué tipo de porcentaje se calculó originalmente en esta tabla (por columna, por fila o respecto al total). Justifique.
* b) Calcule el porcentaje, respecto al total de 40 estudiantes, que matricularon 2 materias (sumando zona urbana y rural).
* c) Calcule qué porcentaje de los estudiantes urbanos (19) matricularon 4 materias.
* d) Explique la diferencia entre calcular un porcentaje por fila y calcular un porcentaje por columna.

## Ejemplo 3
Una investigadora desea representar dos situaciones: (1) la cantidad de personas por provincia de residencia, y (2) la evolución de la matrícula universitaria durante los últimos 10 años.
* a) Complete: para representar una serie ___________ se recomienda usar barras horizontales, mientras que para series cronológicas se recomienda usar barras ___________.
* b) Mencione tres elementos que debe llevar toda gráfica de barras para que se explique por sí misma.
* c) Indique qué tipo de gráfica sería más adecuada para cada una de las dos situaciones descritas arriba y justifique.
* d) ¿Qué diferencia existe entre una gráfica de barras comparativa y una compuesta?

## Tema: RStudio

## Ejemplo 4
Un estudiante empieza a trabajar en RStudio usando un documento R Markdown para analizar la base datos_estudiantes.
* a) Explique brevemente para qué sirve un "chunk" dentro de un documento de R Markdown.
* b) ¿Cuál es la función de la instrucción library() dentro de un script de R?
* c) Explique la diferencia entre usar install.packages() y library().
* d) Si desea saber qué tipo de objeto es una variable creada en R (numérica, texto, lógica, etc.), ¿qué función utilizaría?

## Ejemplo 5
Complete los espacios en blanco con el nombre de la función correcta: getwd(), setwd(), class(), c(), NA.
* a) La función que permite conocer el directorio de trabajo actual se llama ___________.
* b) La función que permite cambiar el directorio de trabajo se llama ___________.
* c) Para crear un vector con varios elementos en R se utiliza la función ___________.
* d) El valor que en R representa un dato no disponible se denota como ___________.
* e) La función que permite determinar el tipo de un objeto (numeric, character, logical) es ___________.

## Ejemplo 6
Un estudiante necesita importar una base de datos en Excel a RStudio y luego construir una tabla de frecuencias con flextable.
* a) Describa, en orden, los pasos generales para importar una base de datos en formato Excel a RStudio usando la interfaz gráfica.
* b) Explique qué información proporciona la función table() cuando se aplica a una variable cualitativa o discreta.
* c) ¿Qué realiza la función prop.table() sobre el resultado de una tabla de frecuencias?
* d) ¿Cuál es la utilidad del paquete flextable mencionado en el curso?

# RESPUESTAS

## Ejemplo 1
* a) Debe indicar dónde se recogieron los datos (lugar), qué son los datos (a qué se refieren), cómo se clasifican y cuándo ocurrieron los hechos.
* b) La columna matriz.
* c) La nota preliminar, colocada debajo del título, indicando por ejemplo "cifras en miles de colones".
* d) Al final del cuadro, en la fuente.

## Ejemplo 2
* a) Porcentaje por columna, ya que cada porcentaje se calculó dividiendo entre el total de cada zona (19 y 21) y no entre el gran total (40).
* b) (4+3)/40 = 7/40 = 17,5 %
* c) 2/19 = 10,5 %
* d) El porcentaje por columna divide cada dato entre el total de esa columna (compara dentro de cada zona), mientras que el porcentaje por fila divide cada dato entre el total de esa fila (compara dentro de cada cantidad de materias, entre zonas).

## Ejemplo 3
* a) geográfica o cualitativa / verticales
* b) Título, ejes con escala y etiquetas, y fuente (también podría mencionarse la geometría o el fondo blanco).
* c) Para la distribución por provincia, una gráfica de barras horizontales (serie geográfica); para la evolución en 10 años, una gráfica lineal (serie cronológica).
* d) La comparativa coloca barras separadas una junto a otra para comparar categorías entre sí; la compuesta divide una sola barra en secciones que muestran los componentes de un mismo fenómeno.

## Ejemplo 4
* a) Un chunk es el espacio dentro del documento donde se escribe y ejecuta el código de R, integrándolo con el texto del informe.
* b) Cargar en la sesión de trabajo un paquete previamente instalado, para poder usar sus funciones.
* c) install.packages() descarga e instala el paquete en el computador (se hace una sola vez); library() únicamente carga el paquete ya instalado para poder usarlo en la sesión actual.
* d) class()

## Ejemplo 5
* a) getwd()
* b) setwd()
* c) c()
* d) NA
* e) class()

## Ejemplo 6
* a) File > Import dataset > From Excel > seleccionar el archivo > Import; luego copiar el código generado en la consola al chunk correspondiente.
* b) Proporciona el conteo (frecuencia absoluta) de cada categoría o valor presente en la variable.
* c) Convierte las frecuencias absolutas en proporciones (o porcentajes, si se multiplican por 100).
* d) Permite dar formato profesional a las tablas generadas en R (alinear columnas, agregar título, ajustar ancho, cambiar el separador decimal, entre otros), para presentarlas en el informe final.
