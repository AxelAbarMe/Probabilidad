# Medidas estadísticas

## Promedio

El promedio se define como $$\bar{x} = \frac{\sum_{i=1}^{n} x_i}{n}$$

> Es la medida de tendencia central más usada y conocida

En el caso de una población finita se denota como $$\mu = \frac{\sum_{i=1}^{N} x_i}{N}$$

### Ejemplo:

> Suponga que las notas de un grupo de estudiantes del curso de matemática general son las siguientes: 70; 77; 65; 64,2; 58,7; 69,5 y 74,6. Determine e interprete la nota promedio del grupo.

El cálculo resulta en $\bar{x} = \frac{70 + 77 + 65 + 64.2 + 58.7 + 69.5 + 74.6}{7} = 68.4$ para este caso.

---
Dada una muestra de n observaciones x1, x2, ..., xn para las cuales existe w1, w2, ..., wn tal que wi representa la ponderación de cada xi se llama media o promedio aritmético ponderado del conjunto de datos x1, x2, ..., xn a la expresión, denotada por x_w. La media ponderada se calcula como 

$$\bar{x}_w = \frac{\sum_{i=1}^{n} (x_i \cdot w_i)}{\sum_{i=1}^{n} w_i}$$

### Ejemplo:

> Suponga que la nota del curso de Probabilidad y Estadística está distribuida de la siguiente manera I Parcial: 20 %, II Parcial: 25 %, III Parcial 30 %, Pruebas Cortas: 10 % y Tareas 15 %.
> 
> Si una persona obtiene las siguientes calificaciones I parcial: 50, II parcial: 70; III parcial: 80, Pruebas cortas: 60, tareas: 90. ¿Cuál es su nota promedio?

El cálculo final da como resultado $\bar{x}_w = \frac{50 \cdot 20 + 70 \cdot 25 + 80 \cdot 30 + 60 \cdot 10 + 90 \cdot 15}{20 + 25 + 30 + 10 + 15} = 71$ para esta muestra.

## Mediana

Se define como el valor central de una serie de datos ordenados, o como un valor tal que no más de la mitad de las observaciones son menores que él y no más de la mitad son mayores.

### N impar
> La posición de la mediana cuando los datos están ordenados se encuentra en:

$$M_e = x_{\frac{n+1}{2}}$$

#### Ejemplo:

> Supongamos que las notas de siete estudiantes son 55,60, 68, 72, 76, 80, 90. Calcule e interprete la mediana.

El cálculo resulta en $M_e = x_{\frac{n+1}{2}} = x_{\frac{7+1}{2}} = x_4 = 72$ para este caso.

---
### N par
> La mediana es igual al promedio de los datos en la posición n/2 y n/(2 + 1).

$$M_e = \frac{x_{\frac{n}{2}} + x_{\frac{n}{2} + 1}}{2}$$

#### Ejemplo:

> Suponga que se tiene información de las notas de un grupo de estudiantes: 55, 60, 68, 72, 76, 80, 90, 93. Calcule e interprete la mediana.

El cálculo resulta en $M_e = \frac{x_4 + x_5}{2} = \frac{72 + 76}{2} = 74$ para este caso.

## Moda

La moda se define como el valor al cual corresponde la mayor frecuencia, es decir el valor más común o popular dentro del conjunto de datos. La moda se puede aplicar tanto para datos cuantitativos como cualitativos.

> En el caso de dos modas, se llama bimodal, en caso de 3 o más valores, se llama multimodal y deja de ser útil como medida de tendencia central.

### Ejemplos:

#### Ejemplo 1

> Suponga que las Notas de un grupo de estudiantes están dadas por: 5, 7, 7, 8, 8, 8, 9. Calcule e interprete la moda.

La moda resulta $M_o = 8$ para este caso. La nota más común entre el estudiantado es 8.

#### Ejemplo 2

> Suponga que el estado civil de un grupo de estudiantes están dadas por: C, S, S, S, S, C, V. Calcule e interprete la moda.

La moda resulta $M_o = S$ para este caso. El estado civil más común entre el estudiantado es soltero

# Observaciones

* La media y la mediana pueden no pertenecer al conjunto de los datos.
* La moda, si existe, pertenece al conjunto de los datos.
* La media no tiene sentido en el caso de variables cualitativas.
* La mediana puede obtenerse en datos cualitativos de naturaleza ordinal.
* En el cálculo de la moda y la mediana no se incluyen todos los valores de la variable.
* La moda y la mediana no se ven afectadas por la presencia de valores extremos.

## Cuantilos

Valores que dividen al conjunto de datos en fracciones específicas. Para su cálculo los datos deben estar ordenados.

### Tipos

* Cuartiles
* Quintiles
* Deciles
* Percentiles

### Cuartiles

Los cuartiles dividen al conjunto de datos en 4 grupos de modo que cada grupo reúne el 25 % de las observaciones. 

|x1|25%|C1|25%|C2|25%|C3|25%|xn|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|

### Quintiles

Los quintiles dividen al conjunto de datos en 5 grupos de modo que cada grupo reúne el 20 % de las observaciones. 

|x1|20%|Q1|20%|Q2|20%|Q3|20%|Q4|20%|xn|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|

### Deciles

Los deciles dividen al conjunto de datos en 10 grupos de modo que cada grupo reúne el 10 % de las observaciones.

|x1|10%|D1|10%|D2|10%|D3|10%|D4|10%|D5|10%|D6|10%|D7|10%|D8|10%|D9|10%|xn|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|

### Percentiles

Si m es un valor tal que 1 ≤ m ≤ 99 entonces definimos el percentil m a la expresión denota por Pm tal que:

$$P_m = x_{\frac{m}{100}(n+1)}$$



