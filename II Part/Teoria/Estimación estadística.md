# Estimación estadística

## 1. Conceptos básicos de la estimación

* **Parámetro poblacional:** valor que describe a toda la población (ej. el promedio `µ` o la proporción `P`).
* **Estimador:** estadístico calculado a partir de una muestra para estimar un parámetro.
* **Estimación puntual:** un valor específico del estimador (ej. un valor concreto de `x̄` es una estimación puntual de `µ`).

| Concepto | Población (parámetro) | Muestra (estimador) |
|---|---|---|
| **Promedio** | `µ = (1/N) · ΣXi` (i = 1..N) | `x̄ = (1/n) · ΣXi` (i = 1..n) |
| **Proporción** | `P = X / N` | `p̂ = X / n` |

* En `P` y `p̂`, `X` es la cantidad de elementos que cumplen con la **característica de interés** (en la población y en la muestra, respectivamente).
* La estimación puntual **no informa** sobre el posible tamaño del error de la estimación; para eso se usa la **estimación por intervalo**.

---

## 2. Estimación por intervalos

* Una **estimación por intervalo** de `θ` es un intervalo `θ̂1 < θ < θ̂2` tal que:

```
P(θ̂1 < θ < θ̂2) = 1 − α
```

* Ese intervalo es un **intervalo de confianza del (1 − α)·100 %** para `θ`.

| Término | Significado |
|---|---|
| **1 − α** | Grado (nivel) de **confianza** del intervalo |
| **θ̂1** | Límite **inferior** (`Li`) |
| **θ̂2** | Límite **superior** (`Ls`) |
| **Amplitud** | **Precisión** del intervalo |
| **Confianza** | **Confiabilidad** de que el valor real del parámetro esté contenido en el intervalo |

* Se puede controlar tanto la **precisión** (amplitud) como la **confiabilidad** (confianza).
* **Interpretación típica:** "con una confianza del `(1 − α)·100 %`, `θ` está contenido en el intervalo `[Li, Ls]`".
* El intervalo simétrico tiene la forma: **estimador ± margen de error**.
* El **margen de error** `E` es la distancia desde el estimador hasta el final (o el principio) del intervalo.
* El **error estándar de estimación** es la parte de la fórmula de `E` que acompaña al valor crítico (`z` o `t`).

---

## 3. Notación de los valores críticos

### Valor `z`

* `zα` = percentil `100(1 − α)` de la distribución **normal estándar**.
* `z(α/2)` = percentil `100(1 − α/2)` de la distribución normal estándar.

| α | α/2 | Valor | Percentil | Valor de z |
|---|---|---|---|---|
| 0,05 | 0,025 | `z0,05` | 95 | 1,645 |
| 0,05 | 0,025 | `z0,025` | 97,5 | 1,96 |

```r
alpha <- 0.05
qnorm(1 - alpha)       # z0.05  -> 1.644854
qnorm(1 - alpha/2)     # z0.025 -> 1.959964
```

### Valores `z(α/2)` más usados en los ejemplos

| Confianza | α | z(α/2) |
|---|---|---|
| 90 % | 0,10 | 1,645 |
| 95 % | 0,05 | 1,96 |
| 98 % | 0,02 | 2,33 |
| 99 % | 0,01 | 2,58 |

### Valor `t` (distribución t-Student)

* Se usa con `n − 1` **grados de libertad**.
* La función `qt()` de R obtiene el cuantil de la distribución t.

```r
alpha <- 0.05; n <- 25
qt(1 - alpha, n - 1)   # t0.05 con 24 g.l. -> 1.710882
```

---

## 4. Media poblacional con σ² conocida

* **Condición:** población normal con variancia `σ²` **conocida**.
* Hay una probabilidad `1 − α` de que el error sea menor que `E`.

### Población infinita

```
E = z(α/2) · σ / √n
```

```
Intervalo:  [ x̄ − z(α/2) · σ/√n ,  x̄ + z(α/2) · σ/√n ]
```

### Población finita (tamaño N)

```
E = z(α/2) · σ / √n · √((N − n) / (N − 1))
```

* El factor `√((N − n)/(N − 1))` es el **factor de corrección para población finita**; el error estándar pasa a ser `σ/√n · √((N − n)/(N − 1))`.

### Ejemplo 1: error máximo (índice de masa corporal)

* Muestra de 150 personas, `σ = 6,2 kg/m²`, confianza del 99 %. Se pide el **error máximo**.

```
n = 150; σ = 6,2; α = 0,01
E = 2,58 · 6,2/√150 = 1,30
```

* **Interpretación:** con un 99 % de confianza, el error máximo en la estimación del índice de masa corporal promedio real es de **1,30 kg/m²**.

### Ejemplo 2: intervalo de confianza (vida útil de componentes)

* Muestra de 40 componentes, `x̄ = 5,6` años, `σ = 2,1` años, confianza del 98 %.

```
n = 40; σ = 2,1; x̄ = 5,6; α = 0,02
E = 2,33 · 2,1/√40 = 0,77
Li = 5,6 − 0,77 = 4,83
Ls = 5,6 + 0,77 = 6,37
```

* **Interpretación:** con un 98 % de confianza, la vida útil promedio real de los componentes está entre **4,83 y 6,37 años**.

### Ejemplo 3: tiempo de traslado (población infinita)

* Muestra de 36 estudiantes, tiempo de traslado normal, `σ = 5,2` min, confianza del 98 %.

```
n = 36; σ = 5,2; x̄ = 20,19; α = 0,02
E = 2,33 · 5,2/√36 = 2,02
Li = 18,18   y   Ls = 22,21
```

* **Interpretación:** con un 98 % de confianza, el tiempo promedio real de traslado está entre **18,18 y 22,21 minutos**.

### Ejemplo 4: tiempo de traslado (población finita N = 5000)

* Mismos datos del ejemplo anterior, pero con `N = 5000` estudiantes.

```
E = 2,33 · 5,2/√36 · √((5000 − 36)/(5000 − 1)) = 2,01
Intervalo = [18,185 ; 22,204]
```

* Al usar el factor de corrección, el margen de error baja de 2,02 a **2,01** y el intervalo se vuelve ligeramente más estrecho.

---

## 5. Media poblacional con σ² desconocida y muestra grande (n > 30)

* **Condición:** población normal, `σ²` **desconocida** y `n > 30`.
* Se **sustituye `σ` por la desviación estándar muestral `s`** y se sigue usando el valor `z`.

### Población infinita

```
E = z(α/2) · s / √n
```

```
Intervalo:  [ x̄ − z(α/2) · s/√n ,  x̄ + z(α/2) · s/√n ]
```

### Población finita (tamaño N)

```
E = z(α/2) · s / √n · √((N − n) / (N − 1))
```

```
Intervalo:  [ x̄ − z(α/2) · s/√n · √((N−n)/(N−1)) ,  x̄ + z(α/2) · s/√n · √((N−n)/(N−1)) ]
```

### Ejemplo 1: tiempo de secado de pintura

* 49 áreas pintadas, `x̄ = 66,3` min, `s = 8,4` min, confianza del 95 %.

```
n = 49; s = 8,4; x̄ = 66,3; α = 0,05
E = 1,96 · 8,4/√49 = 2,35
Li = 63,95   y   Ls = 68,65
```

* **Interpretación:** con un 95 % de confianza, el tiempo promedio real de secado de la nueva pintura está entre **63,95 y 68,65 minutos**.

### Ejemplo 2: años de educación universitaria

* Muestra de 40 personas, `x̄ = 5,6` años, `s = 2,1` años, distribución normal.

**a) Intervalo de confianza del 98 %**

```
n = 40; s = 2,1; x̄ = 5,6; α = 0,02
E = 2,33 · 2,1/√40 = 0,77
Li = 4,83   y   Ls = 6,37
```

* **Interpretación:** con un 98 % de confianza, la cantidad promedio real de años de educación universitaria está entre **4,83 y 6,37 años**.

**b) Nivel de confianza si la longitud del intervalo es 1,2 años**

* Longitud = `2E`, así que `E = 1,2 / 2 = 0,6`.
* Se despeja `z(α/2)` de la fórmula del error:

```
E = z(α/2) · s/√n   ⇒   z(α/2) = E · √n / s = 0,6 · √40 / 2,1 ≈ 1,81
```

* Con `z = 1,81` se obtiene el área en la tabla normal y de ahí el nivel de confianza.
* **Interpretación:** la confianza empleada en la construcción del intervalo es del **92,92 %**.

---

## 6. Media poblacional con σ² desconocida y muestra pequeña (n ≤ 30)

* **Condición:** `Xi ~ N(µ, σ²)`, `σ` **desconocida** y `n ≤ 30`.
* Se usa la distribución **t-Student** con **`n − 1` grados de libertad** en lugar de `z`.

### Población infinita

```
E = t(α/2, n−1) · s / √n
```

```
Intervalo:  [ x̄ − t(α/2, n−1) · s/√n ,  x̄ + t(α/2, n−1) · s/√n ]
```

### Población finita (tamaño N)

```
E = t(α/2, n−1) · s / √n · √((N − n) / (N − 1))
```

```
Intervalo:  [ x̄ − t(α/2, n−1) · s/√n · √((N−n)/(N−1)) ,  x̄ + t(α/2, n−1) · s/√n · √((N−n)/(N−1)) ]
```

* `t` es el valor de una variable aleatoria `T` con distribución t-Student y `n − 1` grados de libertad.

### Ejemplo 1: estatura de estudiantes de noveno año

* Muestra de 25 estudiantes, `x̄ = 1,63 m`, `s = 5,84 cm = 0,0584 m`, confianza del 90 %.

```
n = 25; s = 0,0584; x̄ = 1,63; α = 0,10
E = t(0,05; 24) · 0,0584/√25 = 1,71 · 0,0584/5 = 0,02
Li = 1,61   y   Ls = 1,65
```

* **Interpretación:** con un 90 % de confianza, la estatura media del estudiantado de noveno año está entre **1,61 y 1,65 metros**.
* Se debe trabajar todo en las mismas unidades (aquí, metros).

### Ejemplo 2: consumo semanal de combustible

* Muestra de 20 vehículos, `x̄ = 225` litros, `s = 56,9` litros, confianza del 98 %.

```
n = 20; s = 56,9; x̄ = 225; α = 0,02
E = t(0,01; 19) · 56,9/√20 = 2,54 · 56,9/√20 = 32,31
Li = 192,69   y   Ls = 257,31
```

* **Interpretación:** con un 98 % de confianza, el consumo semanal promedio real por vehículo está entre **192,69 y 257,31 litros**.

---

## 7. Proporción poblacional

* El **error estándar de `p̂`** depende de si la población es infinita o finita.

### Población infinita

```
σ(p̂) = √( p̂(1 − p̂) / n )
```

```
E = z(α/2) · √( p̂(1 − p̂) / n )
```

```
Intervalo:  [ p̂ − z(α/2) · √(p̂(1−p̂)/n) ,  p̂ + z(α/2) · √(p̂(1−p̂)/n) ]
```

### Población finita (tamaño N)

```
σ(p̂) = √( p̂(1 − p̂) / n ) · √((N − n) / (N − 1))
```

```
E = z(α/2) · √( p̂(1 − p̂) / n ) · √((N − n) / (N − 1))
```

### Ejemplo 1: estudiantes satisfechos con su carrera (población infinita)

* Muestra de 210 personas; 130 están satisfechas con su carrera. Confianza del 95 %.

```
n = 210; x = 130; p̂ = 130/210 = 0,619; α = 0,05
E = 1,96 · √(0,619 · 0,381 / 210) = 1,96 · 0,0335 = 0,0657
Li = 0,5533   y   Ls = 0,6847
```

* **Interpretación:** con un 95 % de confianza, la proporción real de estudiantes satisfechos con su carrera está entre **55,34 % y 68,47 %**.

### Ejemplo 2: mismos datos, población finita (N = 5000)

```
E = 1,96 · 0,0335 · √((5000 − 210)/(5000 − 1)) ≈ 0,0643
```

* **Interpretación:** con un 95 % de confianza, la proporción real de estudiantes satisfechos con su carrera está entre **55,47 % y 68,33 %**.

### Ejemplo 3: encuesta sobre medidas económicas del gobierno

* Encuesta a 846 personas; alrededor del 45 % está de acuerdo con las medidas del gobierno.

**a) Intervalo de confianza del 98 %**

```
n = 846; p̂ = 0,45; α = 0,02
E = 2,33 · √(0,45 · 0,55 / 846) = 2,33 · 0,0171 = 0,0398
Li = 0,4102   y   Ls = 0,4898
```

* **Interpretación:** con una confianza del 98 %, la proporción real de personas que están de acuerdo con las medidas económicas del gobierno está entre **41,02 % y 48,98 %**.

**b) Nivel de confianza si la longitud del intervalo es 6 %**

* Longitud = `2E = 0,06`, entonces `E = 0,03`.

```
z(α/2) = E / √(p̂(1−p̂)/n) = 0,03 / 0,0171 ≈ 1,75
```

* Con `z ≈ 1,75` se obtiene el nivel de confianza en la tabla normal: aproximadamente **92 %**.

---

## 8. Comparación de los casos para la media

| Caso | Condición | Valor crítico | Error estándar |
|---|---|---|---|
| **σ conocida** | Población normal | `z(α/2)` | `σ/√n` |
| **σ desconocida, n > 30** | Población normal | `z(α/2)` | `s/√n` |
| **σ desconocida, n ≤ 30** | Población normal | `t(α/2, n−1)` | `s/√n` |
| **Proporción** | Muestra suficientemente grande | `z(α/2)` | `√(p̂(1−p̂)/n)` |

* En **población finita** se multiplica el error estándar por `√((N − n)/(N − 1))` en todos los casos.

### Pasos para construir un intervalo de confianza

1. Identificar el **parámetro** (media o proporción) y los datos: `n`, `x̄` o `p̂`, `σ` o `s`, `N` (si aplica).
2. Calcular `α = 1 − confianza` y `α/2`.
3. Obtener el valor crítico (`z` o `t`) según el caso.
4. Calcular el **margen de error** `E`.
5. Calcular los límites: `Li = estimador − E` y `Ls = estimador + E`.
6. **Interpretar** el resultado indicando el nivel de confianza, el parámetro y las unidades.

### Cálculo del nivel de confianza a partir de la longitud del intervalo

* Longitud del intervalo = `2E`, así que `E = longitud / 2`.
* Se despeja el valor crítico: `z(α/2) = E · √n / s` (para la media) o `z(α/2) = E / √(p̂(1−p̂)/n)` (para la proporción).
* Con ese `z` se obtiene el nivel de confianza `1 − α`.

---

## 9. Resumen general del tema

* La **estimación puntual** da un solo valor (`x̄` para `µ`, `p̂` para `P`), pero no informa sobre el error; la **estimación por intervalo** sí lo hace.
* Un **intervalo de confianza del (1 − α)·100 %** cumple `P(θ̂1 < θ < θ̂2) = 1 − α` y se expresa como **estimador ± margen de error**.
* Se pueden controlar la **precisión** (amplitud) y la **confiabilidad** (confianza) del intervalo.
* Para la **media con σ conocida** se usa `E = z(α/2) · σ/√n`.
* Para la **media con σ desconocida y n > 30** se usa `s` en lugar de `σ`, con el valor `z`.
* Para la **media con σ desconocida y n ≤ 30** se usa la distribución **t-Student** con `n − 1` grados de libertad: `E = t(α/2, n−1) · s/√n`.
* Para la **proporción** se usa `E = z(α/2) · √(p̂(1−p̂)/n)`.
* En **población finita** se multiplica el error estándar por `√((N − n)/(N − 1))`.
* Los valores críticos se obtienen con `qnorm()` (normal) y `qt()` (t-Student) en R.
* Siempre se interpreta el intervalo indicando el **nivel de confianza**, el **parámetro** estimado y sus **unidades**.
