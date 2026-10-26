> **Teoría de la decisión**

# Contraste de hipótesis

## 1. Generalidades del procedimiento de prueba

* La **estimación** busca aproximar un parámetro poblacional con los datos de una muestra.
* En el **contraste de hipótesis**, cuando ya existe una idea sobre el valor de un parámetro, se plantea una **proposición** y se contrasta con la información muestral.
* Se plantean dos proposiciones: la que propone quien investiga y su **negación**.
* Estas proposiciones sobre uno o varios parámetros poblacionales se llaman **hipótesis**, y se busca verificar cuál de ellas es la correcta.

| Hipótesis | Símbolo | Descripción |
|---|---|---|
| **Nula** | `H0` | Plantea una **igualdad** y es la que se somete a prueba |
| **Alternativa** | `H1` | **Niega** la hipótesis nula; es la afirmación que se acepta si la muestra indica que `H0` no es verdadera |

* `H1` es un planteamiento **complementario** a `H0`.

### Formas de plantear un contraste (para un parámetro `θ`)

| Tipo de prueba | Hipótesis nula | Hipótesis alternativa |
|---|---|---|
| **Bilateral** | `H0: θ = θ0` | `H1: θ ≠ θ0` |
| **Unilateral derecha** | `H0: θ ≤ θ0` | `H1: θ > θ0` |
| **Unilateral izquierda** | `H0: θ ≥ θ0` | `H1: θ < θ0` |

### Ejemplo: nota promedio de un curso de matemática

* La nota promedio **podría ser menor a 60**. Si se sustenta estadísticamente, se aplicará un plan de ajuste para aumentarla.
* La afirmación de que la nota es menor a 60 es la que se quiere sustentar, por lo que se establece como **hipótesis alternativa**.

```
H0: µ ≥ 60   La nota promedio real en el curso es al menos 60.
H1: µ < 60   La nota promedio real en el curso es significativamente menor a 60.
```

---

## 2. Región de rechazo y estadístico de prueba

| Concepto | Definición |
|---|---|
| **Región de rechazo** | Conjunto de valores para los cuales la hipótesis nula **debe ser rechazada** |
| **Estadístico de prueba** | Valor obtenido a partir de los **datos de la muestra**, sobre el cual se fundamenta la decisión de rechazar o no `H0` |

---

## 3. Errores en el contraste de hipótesis

* Al probar una hipótesis puede rechazarse `H0` siendo verdadera, o no rechazarse siendo falsa. Ambas situaciones son **errores**.

| Error | Cuándo ocurre | Probabilidad |
|---|---|---|
| **Tipo I** | Se **rechaza** `H0` dado que es **verdadera** | `α = P(rechazar H0 \| H0 es verdadera)` |
| **Tipo II** | **No se rechaza** `H0` dado que es **falsa** | `β = P(no rechazar H0 \| H0 es falsa)` |

* La probabilidad del error tipo I (`α`) se llama **nivel de significancia** de la prueba.

### Ejemplo: tiempo de atención en una oficina bancaria

* Se afirma que el tiempo promedio de atención es de **al menos 25 minutos**. Se tiene `σ = 2,8` min y una muestra de **30 personas**.

**a) Hipótesis**

```
H0: µ ≥ 25   El tiempo promedio real de atención es de al menos 25 minutos.
H1: µ < 25   El tiempo promedio real de atención es significativamente menor a 25 minutos.
```

**b) Interpretación de los errores**

| Error | Interpretación en el contexto |
|---|---|
| **Tipo I** | Decir que el tiempo promedio real de atención es **significativamente menor a 25 minutos** cuando en realidad **no lo es** |
| **Tipo II** | Decir que el tiempo promedio real de atención es **de al menos 25 minutos** cuando en realidad es **significativamente menor** |

---

## 4. Potencia de la prueba

* La **potencia de prueba** es la probabilidad de **rechazar `H0` cuando en verdad es falsa**.

```
Potencia(θ) = P(rechazar H0 | H0 es falsa) = 1 − β(θ)
```

* A mayor potencia, menor es la probabilidad de cometer error tipo II.

---

## 5. Probabilidad de error tipo II

### Ejemplo: oficina bancaria

* Mismos datos: `H0: µ ≥ 25`, `H1: µ < 25`, `σ = 2,8`, `n = 30`.
* `H0` se rechaza si el tiempo promedio muestral es **menor a 23**, y el verdadero valor es **22 minutos**.

**a) Probabilidad de error tipo II**

```
β = P(x̄ ≥ 23 | µ = 22)
```

```r
mu <- 22; n <- 30; sigma <- 2.8
beta <- 1 - pnorm(23, mu, sigma/sqrt(n))
beta
## [1] 0.02522363
```

* La probabilidad de cometer error tipo II es de aproximadamente **0,0252 (2,52 %)**.

**b) Potencia de la prueba**

```
Potencia = 1 − β = 1 − 0,0252 = 0,9748
```

* La potencia de la prueba es de aproximadamente **97,48 %**.

---

## 6. Valor p

* Muchos estadísticos prefieren **no fijar a priori** el nivel de significancia y decidir según el **valor p** (*p value*).
* El **valor p** (nivel crítico) es la probabilidad de observar una diferencia (o valor) **tan extrema o más extrema** que la observada en la muestra, **asumiendo que `H0` es cierta**.

### Cálculo del valor p según `H1` (con `s_obs` el valor observado del estadístico)

| Hipótesis alternativa | Valor p |
|---|---|
| `H1: θ < θ0` | `P(S ≤ s_obs \| H0)` |
| `H1: θ > θ0` | `P(S ≥ s_obs \| H0)` |
| `H1: θ ≠ θ0` | `2 · P(S ≥ \|s_obs\| \| H0)` |

### Regla de decisión

* Un valor p **pequeño** apoya a `H1`.
* Se debe considerar el nivel de significancia: **`H0` se rechaza si valor p < α**.

| Resultado | Decisión |
|---|---|
| `valor p < α` | **Se rechaza** `H0` (hay evidencia a favor de `H1`) |
| `valor p ≥ α` | **No se rechaza** `H0` (no hay evidencia suficiente a favor de `H1`) |

### Ejemplo 1: oficina bancaria (valor p = 0,0001, α = 5 %)

```
H0: µ ≥ 25
H1: µ < 25
0,0001 < 0,05  ⇒  se rechaza H0
```

* **Interpretación:** existen evidencias, al nivel del 5 %, para decir que el tiempo promedio real de atención al cliente es **significativamente menor a 25 minutos**.

### Ejemplo 2: nota promedio del curso de matemática (valor p = 0,07, α = 3 %)

```
H0: µ ≥ 60
H1: µ < 60
0,07 > 0,03  ⇒  no se rechaza H0
```

* **Interpretación:** al nivel de significancia del 3 %, **no hay evidencias suficientes** para afirmar que la nota promedio real en el curso es significativamente menor a 60.

---

## 7. Contraste de hipótesis para la proporción poblacional

### Distribución y estadístico de prueba

* Si `Yi ~ Bernoulli(P)`, entonces `X = ΣYi ~ Bin(n, P)`.
* Por aproximación normal, la proporción muestral se distribuye:

```
p̂ = X/n  ~  N( P , √(P(1 − P)/n) )
```

* Con `P0` como **valor nulo** de la proporción, el **estadístico de prueba** es:

```
Z = (p̂ − P0) / √( P0(1 − P0) / n )  ~  N(0, 1)
```

### Hipótesis y región de rechazo

| Hipótesis nula | Hipótesis alternativa | Región de rechazo |
|---|---|---|
| `H0: P = P0` | `H1: P ≠ P0` | `z < −z(α/2)` ó `z > z(α/2)` |
| `H0: P ≤ P0` | `H1: P > P0` | `z > zα` |
| `H0: P ≥ P0` | `H1: P < P0` | `z < −zα` |

### Valor p (aproximación normal)

| Hipótesis alternativa | Valor p |
|---|---|
| `H1: P ≠ P0` | `2 · P(Z ≥ \|z_obs\|)` |
| `H1: P > P0` | `P(Z ≥ \|z_obs\|)` |
| `H1: P < P0` | `P(Z ≥ \|z_obs\|)` |

* `H0` se rechaza si **valor p < α**.

### Ejemplo 1: empleo de personas graduadas en ciencias sociales (prueba bilateral)

* CONARE señala que alrededor del **20 %** de las personas graduadas en ciencias sociales encuentran trabajo en su especialidad en menos de dos años. En una muestra de **500** personas graduadas, **90** lo lograron. Nivel de significancia del **4 %**.

```
H0: P = 0,20   La proporción real que encuentra trabajo en su especialidad es 20 %.
H1: P ≠ 0,20   La proporción real es significativamente distinta de 20 %.
```

```r
alpha <- 0.04; alpham <- alpha/2; P0 <- 0.20
n <- 500; x <- 90; p <- 0.18
zalpham <- qnorm(1 - alpham)
z <- (0.18 - 0.20) / sqrt(0.20*(1 - 0.20)/500)
c(-zalpham, zalpham, z)
## [1] -2.053749  2.053749 -1.118034
```

* **Por estadístico de prueba:** como `−2,05 < −1,12 < 2,05`, `z` no cae en la región de rechazo y **no se rechaza `H0`**.
* **Por valor p:** `p = 2 · P(Z ≥ |z_obs|) = 2 · (1 − F(|z_obs|)) ≈ 0,26`; como `0,26 > 0,04`, **no se rechaza `H0`**.
* **Interpretación:** no existen evidencias, al nivel del 4 %, para decir que la proporción real de personas graduadas en ciencias sociales que encuentran trabajo en su especialidad en menos de dos años es significativamente distinta de 20 %.

### Ejemplo 2: conocimiento del nombre genérico de la metadina (prueba unilateral izquierda)

* En un estudio con **102** personas, solo **47** conocían el nombre genérico de la metadina. Con un nivel de significancia del **1 %**, ¿hay evidencia fuerte de que **menos de la mitad** lo conoce?

```
H0: P ≥ 0,50   La proporción real que conoce el nombre genérico es al menos 50 %.
H1: P < 0,50   La proporción real que conoce el nombre genérico es significativamente menor a 50 %.
```

```r
alpha <- 0.01; P0 <- 0.50
n <- 102; x <- 47; p <- 0.4608
zalpha <- qnorm(1 - alpha)
z <- (0.4608 - 0.50) / sqrt(0.50*(1 - 0.50)/102)
c(-zalpha, z)
## [1] -2.3263479 -0.7918012
```

* **Por estadístico de prueba:** como `−0,79 > −2,33`, **no se rechaza `H0`**.
* **Por valor p:** `p = P(Z > |z_obs|) ≈ 0,214`; como `0,214 > 0,01`, **no se rechaza `H0`**.
* **Interpretación:** no existen evidencias, al nivel del 1 %, para decir que la proporción real de personas que conocen el nombre genérico de la metadina es significativamente menor al 50 %.

---

## 8. Contraste de hipótesis para la diferencia de medias (poblaciones normales)

* Sean dos variables aleatorias `X` y `Y` con medias `µ1` y `µ2`. Con `(µ1 − µ2)0 = δ` como **valor nulo de la diferencia**, el contraste se plantea de tres formas:

| Hipótesis nula | Hipótesis alternativa |
|---|---|
| `H0: µ1 − µ2 = δ` | `H1: µ1 − µ2 ≠ δ` |
| `H0: µ1 − µ2 ≤ δ` | `H1: µ1 − µ2 > δ` |
| `H0: µ1 − µ2 ≥ δ` | `H1: µ1 − µ2 < δ` |

* Plantear `H0: µ1 = µ2` equivale a `H0: µ1 − µ2 = 0` (es decir, `δ = 0`).

### 8.1 Variancias poblacionales conocidas

```
z = [ (x̄1 − x̄2) − δ ] / √( σ1²/n1 + σ2²/n2 )   ~  N(0, 1)
```

### 8.2 Variancias desconocidas y muestras grandes (n1 > 30 y n2 > 30)

```
z = [ (x̄1 − x̄2) − δ ] / √( s1²/n1 + s2²/n2 )   ~  N(0, 1)
```

**Región de rechazo (casos 8.1 y 8.2)**

| Hipótesis nula | Hipótesis alternativa | Región de rechazo |
|---|---|---|
| `H0: µ1 − µ2 = δ` | `H1: µ1 − µ2 ≠ δ` | `z < −z(α/2)` ó `z > z(α/2)` |
| `H0: µ1 − µ2 ≤ δ` | `H1: µ1 − µ2 > δ` | `z > zα` |
| `H0: µ1 − µ2 ≥ δ` | `H1: µ1 − µ2 < δ` | `z < −zα` |

**Valor p**

| Hipótesis alternativa | Valor p |
|---|---|
| `H1: µ1 − µ2 ≠ δ` | `2 · P(Z ≥ \|z_obs\|)` |
| `H1: µ1 − µ2 > δ` | `P(Z ≥ \|z_obs\|)` |
| `H1: µ1 − µ2 < δ` | `P(Z ≥ \|z_obs\|)` |

* `H0` se rechaza si **valor p < α**.

#### Ejemplo 1: rendimiento de estudiantes de zona rural y urbana (prueba bilateral)

* Zona rural: `n1 = 32`, `x̄1 = 79,8`, `s1 = 8`. Zona urbana: `n2 = 36`, `x̄2 = 84,7`, `s2 = 9`. Distribuciones normales, α = **1 %**.

```
H0: µ1 = µ2   No existen diferencias significativas en el rendimiento promedio real según la zona de residencia.
H1: µ1 ≠ µ2   Existen diferencias significativas en el rendimiento promedio real según la zona de residencia.
```

```r
alpha <- 0.01; alpham <- alpha/2
n1 <- 32; xbarra1 <- 79.8; s1 <- 8
n2 <- 36; xbarra2 <- 84.7; s2 <- 9
delta <- 0
num <- (xbarra1 - xbarra2) - (delta)
den <- sqrt(s1^2/n1 + s2^2/n2)
z <- num/den
zalpham <- qnorm(1 - alpham)
c(-zalpham, zalpham, z)
## [1] -2.575829  2.575829 -2.376849
```

* **Por estadístico de prueba:** como `−2,58 < −2,38 < 2,58`, **no se rechaza `H0`**.
* **Por valor p:** `p = 2 · P(Z ≥ |z_obs|) = 0,0175`; como `0,0175 > 0,01`, **no se rechaza `H0`**.
* **Interpretación:** no hay evidencias, al nivel del 1 %, para decir que existen diferencias significativas en el rendimiento promedio real en el curso según la zona de residencia.

#### Ejemplo 2: puntajes de la PAA en las carreras A y B (prueba unilateral)

* Carrera A: `n1 = 64`, `x̄1 = 695`, `s1 = 70`. Carrera B: `n2 = 144`, `x̄2 = 716`, `s2 = 78`. Ambas distribuciones aproximadamente normales, α = **5 %**.
* Se quiere establecer si el puntaje en la carrera B es **mayor** que en la carrera A.

```
H0: µ1 ≥ µ2   El puntaje promedio real de la carrera A es mayor o igual al de la carrera B.
H1: µ1 < µ2   El puntaje promedio real de la carrera B es significativamente mayor al de la carrera A.
```

```
z = (695 − 716) / √(70²/64 + 78²/144) = −21 / 10,90 ≈ −1,93
Región de rechazo: z < −z0,05 = −1,645
```

* Como `−1,93 < −1,645`, **se rechaza `H0`**: hay evidencias, al nivel del 5 %, para decir que el puntaje promedio real en la PAA de la carrera B es significativamente mayor al de la carrera A.

#### Ejemplo 3: salarios en dos empresas (diferencia mayor a un valor δ)

* Empresa 1: `n1 = 36`, `x̄1 = 300`, `s1 = 13`. Empresa 2: `n2 = 40`, `x̄2 = 285`, `s2 = 12`. α = **2 %**, `δ = 10`.
* Se quiere verificar si la diferencia entre los salarios promedio es **mayor a $10**.

```
H0: µ1 − µ2 ≤ 10   La diferencia entre los salarios promedio reales es de a lo sumo $10.
H1: µ1 − µ2 > 10   La diferencia entre los salarios promedio reales es significativamente mayor a $10.
```

```r
n1 <- 36; xbarra1 <- 300; s1 <- 13
n2 <- 40; xbarra2 <- 285; s2 <- 12
alpha <- 0.02; delta <- 10
zalpha <- qnorm(1 - alpha)
z <- ((xbarra1 - xbarra2) - delta) / sqrt(s1^2/n1 + s2^2/n2)
c(zalpha, z)
## [1] 2.053749 1.740000
```

* Como `1,74 < 2,05`, **no se rechaza `H0`**: no hay evidencias, al nivel del 2 %, para decir que la diferencia entre los salarios promedio reales es significativamente mayor a $10.

| Error | Interpretación en el contexto |
|---|---|
| **Tipo I** | Decir que la diferencia entre los salarios promedio es **significativamente mayor a $10** cuando en realidad es **a lo sumo $10** |
| **Tipo II** | Decir que la diferencia es **a lo sumo $10** cuando en realidad es **significativamente mayor a $10** |

### 8.3 Muestras pequeñas (n1 ≤ 30 o n2 ≤ 30)

* **Condición:** poblaciones normales con **variancias iguales** (σX = σY).
* Se usa la distribución **t-Student** con **`n1 + n2 − 2` grados de libertad**.

**Desviación estándar combinada**

```
sp = √( [ (n1 − 1)·s1² + (n2 − 1)·s2² ] / (n1 + n2 − 2) )
```

**Estadístico de prueba**

```
t = [ (x̄1 − x̄2) − δ ] / ( sp · √(1/n1 + 1/n2) )   ~  t(n1+n2−2)
```

**Región de rechazo**

| Hipótesis nula | Hipótesis alternativa | Región de rechazo |
|---|---|---|
| `H0: µ1 − µ2 = δ` | `H1: µ1 − µ2 ≠ δ` | `t < −t(α/2, n1+n2−2)` ó `t > t(α/2, n1+n2−2)` |
| `H0: µ1 − µ2 ≤ δ` | `H1: µ1 − µ2 > δ` | `t > t(α, n1+n2−2)` |
| `H0: µ1 − µ2 ≥ δ` | `H1: µ1 − µ2 < δ` | `t < −t(α, n1+n2−2)` |

**Valor p**

| Hipótesis alternativa | Valor p |
|---|---|
| `H1: µ1 − µ2 ≠ δ` | `2 · P(T ≥ \|t_obs\|)` |
| `H1: µ1 − µ2 > δ` | `P(T ≥ \|t_obs\|)` |
| `H1: µ1 − µ2 < δ` | `P(T ≥ \|t_obs\|)` |

#### Ejemplo 1: rendimiento en Estadística, universidades públicas y privadas

* Notas de 10 estudiantes de cada tipo de universidad; α = **3 %**. Se quiere saber si el rendimiento en la universidad **pública** es **mayor**.

```r
pub <- c(93, 82, 75, 74, 45, 59, 59, 94, 90, 46)
pri <- c(67, 60, 70, 76, 40, 72, 52, 51, 73, 44)
```

```
H0: µ1 ≤ µ2   El rendimiento promedio real en universidades públicas es menor o igual al de las privadas.
H1: µ1 > µ2   El rendimiento promedio real en universidades públicas es significativamente mayor.
```

```r
alpha <- 0.03; delta <- 0
n1 <- 10; xbarra1 <- mean(pub); s1 <- sd(pub)
n2 <- 10; xbarra2 <- mean(pri); s2 <- sd(pri)
num <- (xbarra1 - xbarra2) - (delta)
sp <- sqrt(((n1 - 1)*s1^2 + (n2 - 1)*s2^2)/(n1 + n2 - 2))
den <- sp*sqrt(1/n1 + 1/n2)
t <- num/den
talpha <- qt(1 - alpha, n1 + n2 - 2)
c(talpha, t)
## [1] 2.007067 1.563112
```

* También puede resolverse con la función `TTestA()` del paquete `DescTools`.
* **Por estadístico de prueba:** como `1,56 < 2,01`, **no se rechaza `H0`**.
* **Por valor p:** `p = P(T ≥ |t_obs|) = 1 − pt(1,56; 18) ≈ 0,068`; como `0,068 > 0,03`, **no se rechaza `H0`**.
* **Interpretación:** no hay evidencias, al nivel del 3 %, para decir que el rendimiento promedio real en el curso de Estadística es significativamente mayor en las universidades públicas.

#### Ejemplo 2: tiempo de montaje en dos fábricas (diferencia igual a δ)

* Fábrica A: `n1 = 10`, `x̄1 = 10,7` min, `s1 = 1,98` min. Fábrica B: `n2 = 12`, `x̄2 = 17,8` min, `s2 = 2,07` min. α = **4 %**.
* Se quiere verificar si existe una diferencia de **5 minutos** entre los tiempos promedio de montaje.

```
H0: µ1 − µ2 = 5   Existe una diferencia de 5 minutos en el tiempo promedio real de montaje entre las fábricas.
H1: µ1 − µ2 ≠ 5   La diferencia en el tiempo promedio real de montaje es significativamente distinta de 5 minutos.
```

```
sp = √( [9·(1,98)² + 11·(2,07)²] / 20 ) ≈ 2,03
t  = [ (10,7 − 17,8) − 5 ] / ( 2,03 · √(1/10 + 1/12) ) ≈ −13,92
Región de rechazo: t < −t(0,02; 20) ≈ −2,197  ó  t > 2,197
```

* Como `−13,92 < −2,197`, **se rechaza `H0`**: hay evidencias, al nivel del 4 %, para decir que la diferencia en el tiempo promedio real de montaje entre las fábricas es significativamente distinta de 5 minutos.

| Error | Interpretación en el contexto |
|---|---|
| **Tipo I** | Decir que la diferencia entre los tiempos promedio de montaje es **significativamente distinta de 5 minutos** cuando en realidad **es de 5 minutos** |
| **Tipo II** | Decir que la diferencia entre los tiempos promedio de montaje **es de 5 minutos** cuando en realidad es **significativamente distinta de 5 minutos** |

---

## 9. Resumen de estadísticos de prueba

| Contraste | Condición | Estadístico | Distribución |
|---|---|---|---|
| **Proporción** | Aproximación normal | `(p̂ − P0) / √(P0(1−P0)/n)` | `N(0, 1)` |
| **Diferencia de medias** | σ1², σ2² conocidas | `[(x̄1 − x̄2) − δ] / √(σ1²/n1 + σ2²/n2)` | `N(0, 1)` |
| **Diferencia de medias** | σ² desconocidas, n1 > 30 y n2 > 30 | `[(x̄1 − x̄2) − δ] / √(s1²/n1 + s2²/n2)` | `N(0, 1)` |
| **Diferencia de medias** | σ² desconocidas e iguales, n1 ≤ 30 o n2 ≤ 30 | `[(x̄1 − x̄2) − δ] / (sp·√(1/n1 + 1/n2))` | `t(n1+n2−2)` |

### Pasos para realizar un contraste de hipótesis

1. Identificar el **parámetro** y plantear `H0` y `H1` en el contexto del problema.
2. Fijar el **nivel de significancia** `α`.
3. Calcular el **estadístico de prueba** con los datos de la muestra.
4. Determinar la **región de rechazo** (o calcular el **valor p**).
5. **Decidir:** rechazar `H0` si el estadístico cae en la región de rechazo o si `valor p < α`.
6. **Interpretar** la decisión indicando el nivel de significancia, el parámetro y el contexto.
