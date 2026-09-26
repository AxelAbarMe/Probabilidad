# Distribuciones muestrales

## Concepto de Distribución de Muestreo

* **Definición:** una distribución de muestreo para un estadístico es la **distribución de probabilidad** de los valores posibles que puede tomar dicho estadístico al extraer, de manera repetida, muestras de tamaño *n* de una población.
* **Distribución de muestreo de la media:** distribución de probabilidad de los valores posibles del estadístico **x̄**, resultante de extraer repetidamente muestras de tamaño *n* de la población.
* Los promedios muestrales se usan para **estimar la media poblacional desconocida (μ)**; sin embargo, el promedio puede variar de una muestra a otra, por lo que se necesita valorar qué tan buena es esa aproximación mediante la distribución de muestreo del estadístico.

---

## Ejemplo Introductorio (Muestreo con reemplazo)

> Población: **{1, 2, 3, 4, 5}**. Se construye la distribución de muestreo para la media usando **muestras de tamaño 2**.

**Pasos para construirla:**
1. Seleccionar todas las posibles muestras de tamaño 2 (con reemplazo → 5×5 = 25 muestras posibles).
2. Calcular el estadístico (la media) para cada muestra.
3. Construir la distribución de probabilidad del estadístico x̄.

### Tabla de combinaciones (todas las muestras ordenadas con repetición)

| | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| **1** | (1,1) | (1,2) | (1,3) | (1,4) | (1,5) |
| **2** | (2,1) | (2,2) | (2,3) | (2,4) | (2,5) |
| **3** | (3,1) | (3,2) | (3,3) | (3,4) | (3,5) |
| **4** | (4,1) | (4,2) | (4,3) | (4,4) | (4,5) |
| **5** | (5,1) | (5,2) | (5,3) | (5,4) | (5,5) |

### Distribución de probabilidad de x̄

| x̄ | P(x̄) | x̄·P(x̄) |
|---|---|---|
| 1 | 1/25 | 1/25 |
| 1,5 | 2/25 | 3/25 |
| 2 | 3/25 | 6/25 |
| 2,5 | 4/25 | 10/25 |
| 3 | 5/25 | 15/25 |
| 3,5 | 4/25 | 14/25 |
| 4 | 3/25 | 12/25 |
| 4,5 | 2/25 | 9/25 |
| 5 | 1/25 | 5/25 |

* **Valor esperado de x̄:** E(x̄) = Σ x̄·P(x̄) = **3**
* **Media poblacional:** μ = (1+2+3+4+5) / 5 = **3**
* Se comprueba que **E(x̄) = μ**, es decir, el valor esperado de la media muestral coincide con la media poblacional.
* La gráfica de P(x̄) contra x̄ muestra una forma **simétrica y triangular**, con el máximo en x̄ = 3 (donde P(x̄) = 5/25).

### Ejemplo con datos reales: estatura de estudiantes

> Se seleccionan 5 estudiantes de una población universitaria, y este proceso se repite en 4 muestras (n₁, n₂, n₃, n₄) para calcular la estatura promedio en cada una.

| n₁ | n₂ | n₃ | n₄ |
|---|---|---|---|
| x̄₁ = 163 | x̄₂ = 163,4 | x̄₃ = 163 (≈167,2) | x̄₄ = 162,4 |

* Al repetir el proceso varias veces, **es poco probable que el promedio sea el mismo** en cada muestra, ya que varía de muestra a muestra.

---

## Teorema del Límite Central (TLC)

### Caso 1: Muestreo con reemplazo (N desconocida o poblaciones infinitas)

> Sean X₁, X₂, …, Xₙ variables aleatorias **independientes e idénticamente distribuidas (iid)**, con media μ_X y varianza σ²_X. Entonces, la distribución de los promedios x̄ es aproximadamente **normal**, con:

* **E(x̄) = μ_x̄ = μ_X**
* **Var(x̄) = σ²_x̄ = σ²_X / n**

### Caso 2: Muestreo sin reemplazo (N conocida o poblaciones finitas)

> Sean X₁, X₂, …, Xₙ variables aleatorias idénticamente distribuidas, con media μ_X y varianza σ²_X. Entonces:

* **E(x̄) = μ_x̄ = μ_X**
* **Var(x̄) = (σ²_X / n) · [(N − n) / (N − 1)]**

### Notación general

> x̄ ~ N( μ_x̄ = μ , σ²_x̄ = σ²_X / n )

---

## Error Estándar

* La raíz cuadrada de la varianza del estimador es la **desviación estándar del estimador**, también llamada **error estándar**.

* **Poblaciones infinitas:**
  σ_x̄ = √(σ²_X / n) = σ / √n

* **Poblaciones finitas:**
  σ_x̄ = √(σ²_X / n) · √[(N − n) / (N − 1)] = (σ / √n) · √[(N − n) / (N − 1)]

---

## Aplicación: Estimación e Intervalos

* El **Teorema del Límite Central** permite describir el comportamiento de un estimador aprovechando que su distribución es aproximadamente normal, lo cual posibilita el cálculo de probabilidades.

> **Error – Aleatorio – medir:** relación entre el estadístico x̄, el error de estimación (E) y el parámetro poblacional.

* Con la media muestral x̄ y un margen de error E, se construye un intervalo:
  * **x̄ − E**
  * **x̄ + E**
* Este intervalo busca contener al parámetro poblacional **μ**, dentro de un rango:  x̄ − E < μ < x̄ + E.

---

## Ejemplos de Aplicación

### Ejemplo 1: Precio de un artículo
> μ_X = $280, σ = $50, tamaño de muestra n = 36.

* **a.** P(x̄ ≤ 260) = 0,0082
* **b.** P(270 < x̄ < 290) = 0,3249
* **c.** 50 % central de las medias muestrales: entre **274,38** y **285,62** (cuantiles 25 y 75).
* **d.** Cuantil 35 (35 % de menor monto): x̄ = **276,79**
* **e.** Con población finita de N = 5000 artículos, se solicita calcular P(x̄ ≥ 290) usando la corrección para poblaciones finitas.

### Ejemplo 2: Peso de una población estudiantil
> μ_X = 130 kg, varianza poblacional = 441 kg², tamaño de muestra n = 30.

* **a.** Probabilidad de que las medias muestrales estén entre 120 y 139 kg.
* **b.** Proporción de medias muestrales que sobrepasan los 119 kg.
* **c.** Límites del 90 % central de las medias muestrales.
* **d.** Porcentaje de personas con peso medio de a lo sumo 125 kg, en una población finita de 1000 personas (aplica corrección para población finita).

---

## Resumen general del tema

* Una **distribución de muestreo** describe la variabilidad de un estadístico (como x̄) al repetir el muestreo.
* El **valor esperado de x̄ siempre coincide con la media poblacional (μ)**.
* El **Teorema del Límite Central** garantiza que, para muestras suficientemente grandes, x̄ sigue una distribución **aproximadamente normal**, con media μ y varianza σ²/n (ajustada por el factor de población finita cuando N es conocida).
* El **error estándar** (σ_x̄) mide la dispersión de las medias muestrales alrededor de μ.
* Estas propiedades permiten calcular **probabilidades, cuantiles e intervalos** sobre la media muestral, aplicables tanto a poblaciones infinitas como finitas.
