# Práctica 3
> Distribuciones de frecuencia y medidas descriptivas

## Tema: Distribuciones de frecuencia

## Ejemplo 1
El número de mascotas registradas en 15 hogares es: 1, 2, 2, 3, 1, 2, 4, 3, 2, 1, 2, 3, 4, 2, 1
* a) Construya la tabla de distribución de frecuencias con frecuencia absoluta, relativa (%), acumulada absoluta y acumulada relativa (%).
* b) Interprete: ¿qué porcentaje de los hogares tiene 2 mascotas o menos?
* c) Interprete: ¿qué porcentaje de los hogares tiene más de 3 mascotas?
* d) ¿Esta distribución corresponde a una variable cuantitativa discreta o continua? Justifique.

## Ejemplo 2
Aplique los tres tipos de redondeo vistos en el curso (usual, hacia arriba y hacia abajo) a los siguientes valores: 73,240 ; 26,000 ; 15,500

|Valor|Usual|Hacia Arriba|Hacia abajo|
|:---:|:---:|:---:|:---:|
|73.240||||
|26,000||||
|15,500||||

## Ejemplo 3
Se tiene un conjunto de 50 datos correspondientes al gasto mensual (en miles de colones) de un grupo de familias, cuyo valor mínimo es 30 y el máximo es 95.
* a) Utilizando la fórmula de Sturges, determine el número de clases adecuado.
* b) Calcule el rango del conjunto de datos.
* c) Calcule el ancho aproximado de cada clase (redondeando a un número entero conveniente).
* d) Indique los límites y el punto medio de la primera clase, iniciando en 30.

## Tema: Medidas descriptivas

## Ejemplo 4
Las notas de un grupo de 7 estudiantes en un examen son: 82, 75, 90, 68, 71, 85, 79
* a) Calcule e interprete el promedio del grupo.
* b) Un estudiante tiene las siguientes notas ponderadas: I Parcial (25 %): 65, II Parcial (25 %): 80, III Parcial (30 %): 70, Tareas (20 %): 90. Calcule su nota ponderada final.
* c) ¿Por qué en este segundo caso no basta con calcular un promedio simple?
* d) Mencione una limitación del promedio como medida de tendencia central.

## Ejemplo 5
* a) Las edades de 5 personas son: 23, 19, 35, 28, 41. Calcule e interprete la mediana.
* b) Las calificaciones de 8 estudiantes son: 55, 62, 70, 74, 78, 82, 88, 91. Calcule e interprete la mediana.
* c) Las tallas de zapatos vendidos en un día son: 38, 40, 40, 41, 42, 40, 39. Calcule e interprete la moda.
* d) Indique si la mediana y la moda pueden verse afectadas por valores extremos.

## Ejemplo 6
Los salarios mensuales (en miles de colones) de 10 personas colaboradoras, ya ordenados, son: 320, 350, 360, 380, 400, 410, 430, 450, 470, 500
* a) Calcule e interprete el percentil 30 (P30).
* b) Calcule e interprete el primer cuartil (Q1 = P25).
* c) ¿Qué porcentaje de los salarios se ubica por debajo del valor calculado en b)?
* d) Mencione dos tipos de cuantiles distintos a los cuartiles.

# RESPUESTAS

## Ejemplo 1
a)

|Mascotas|	Frec. Absoluta|	Frec. Relativa (%)|	Acum. Absoluta|	Acum. Relativa (%)
|1|	4|	26,7|	4|	26,7|
|2|	6|	40,0|	10|	66,7|
|3|	3|	20,0|	13|	86,7|
|4|	2|	13,3|	15|	100,0|
|Total|	15|	100,0|||

* b) 66,7 % de los hogares tiene 2 mascotas o menos.
* c) 13,3 % de los hogares tiene más de 3 mascotas.
* d) Cuantitativa discreta, porque el número de mascotas solo puede tomar valores enteros (no admite valores intermedios).

## Ejemplo 2

* 73,240: usual = 73 ; hacia arriba = 73 ; hacia abajo = 74
* 26,000: usual = 26 ; hacia arriba = 26 ; hacia abajo = 26
* 15,500: usual = 16 ; hacia arriba = 15 ; hacia abajo = 16

## Ejemplo 3
* a) 1 + 3,332 × log(50) = 1 + 3,332 × 1,699 ≈ 6,66 ≈ 7 clases
* b) Rango = 95 − 30 = 65
* c) Ancho ≈ 65 ÷ 7 ≈ 9,3, que se redondea a 10 para facilitar la construcción de las clases
* d) Primera clase: 30 – 40, con punto medio Xi = (30+40)/2 = 35

## Ejemplo 4
* a) x̄ = (82+75+90+68+71+85+79)/7 = 550/7 ≈ 78,57. En promedio, el grupo obtuvo una nota de 78,57.
* b) x̄w = (65×25 + 80×25 + 70×30 + 90×20)/100 = 7525/100 = 75,25
* c) Porque cada evaluación tiene una ponderación distinta dentro de la nota final; un promedio simple le daría el mismo peso a todas las evaluaciones, lo cual no refleja correctamente cómo se compone la nota.
* d) Es sensible a la presencia de valores extremos, ya que estos pueden distorsionar su valor.

## Ejemplo 5
* a) Datos ordenados: 19, 23, 28, 35, 41. n impar, posición (5+1)/2=3, Me = 28. La mitad de las personas tiene 28 años o menos, y la otra mitad 28 años o más.
* b) Datos ya ordenados: n par, Me = (x4+x5)/2 = (74+78)/2 = 76.
* c) Mo = 40, ya que es el valor que más se repite (3 veces). La talla más vendida ese día fue la 40.
* d) No, la mediana y la moda no se ven afectadas por la presencia de valores extremos.

## Ejemplo 6
* a) P30 = x[(30/100)(11)] = x3,3. Entre x3=360 y x4=380: P30 = 360 + 20×0,3 = 366. El 30 % de los salarios es menor o igual a 366 mil colones, y el 70 % es mayor o igual a ese valor.
* b) Q1 = P25 = x[(25/100)(11)] = x2,75. Entre x2=350 y x3=360: Q1 = 350 + 10×0,75 = 357,5. El 25 % de los salarios es menor o igual a 357,5 mil colones.
* c) 25 %.
* d) Quintiles y deciles (también podrían mencionarse los percentiles en general).
