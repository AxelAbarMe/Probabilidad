# Guía práctica de R para la prueba: estimación, contrastes y regresión

> **Regla de la cátedra:** el único código permitido es el del PDF genérico. Esta guía te ayuda a **saber cuál código usar, cuándo, y cómo redactar** hipótesis, interpretaciones y conclusiones.

---

## 1. Cómo decidir qué código usar

### 1.1 Valores críticos

| Necesito | Código | Cuándo |
|---|---|---|
| Valor `z` | `qnorm(p)` | σ conocida, n > 30 en diferencias, proporciones |
| Valor `t` (una media) | `qt(p, n - 1)` | σ desconocida, una muestra |
| Valor `t` (dos medias) | `qt(p, n1 + n2 - 2)` | σ desconocida, dos muestras con varianzas iguales |

* `p` es el **área acumulada**: `1 - alpha` (una cola) o `1 - alpha/2` (dos colas).

### 1.2 Árbol de decisión para la media

| Situación | Función | Por qué |
|---|---|---|
| σ **conocida** | `z.test(x, sigma.x, ...)` (BSDA) | Se usa la normal porque σ es dato |
| σ desconocida, n ≤ 30 | `t.test(x, ...)` | Con muestra pequeña la t corrige la incertidumbre de estimar σ |
| σ desconocida, n > 30 | `t.test(x, ...)` | La t se aproxima a la normal, por lo que sirve igual |
| **Proporción** | `prop.test(...)` o código manual | Variable cualitativa o de éxito/fracaso |
| Relación entre 2 variables numéricas | `lm(y ~ x, data = base)` | Se busca una recta que explique `y` con `x` |

### 1.3 Población finita

* Si el enunciado da **N** (tamaño de la población), se aplica el factor `√((N - n)/(N - 1))`.
* Con σ conocida o n grande: se multiplica la desviación por el factor y se usa `z.test`.
* Con muestra pequeña: **se hace manual** (el PDF lo recomienda).
* Con proporciones: se multiplica `sigmap` por el factor.

---

## 2. Estimación por intervalos

### 2.1 Qué código para qué

| Caso | Código | Por qué ese código |
|---|---|---|
| Media, σ conocida | `z.test(x = base$variable, sigma.x = , conf.level = )$conf` | σ es dato del enunciado |
| Media, σ desconocida (n ≤ 30 o n > 30) | `t.test(x = base$variable, conf.level = )$conf` | σ se estima con `s` |
| Estimación puntual de la media | `t.test(...)$estimate` | Devuelve `x̄` |
| Proporción (Wald) | Código manual con `qnorm` | Es el método clásico |
| Proporción (Wilson) | `prop.test(x, n, conf.level)$conf` | Más preciso, lo hace R |
| Estimación puntual de la proporción | `prop.test(...)$estimate` | Devuelve `p̂` |

* **Detalle clave:** `conf.level` es la **confianza** (0.95), no el α.
* Para subconjuntos se filtra: `base$peso[base$sexo == "M"]`.
* Para contar casos en proporciones: `x <- length(which(condicion))`; las categorías de texto van entre comillas y con `==`.

### 2.2 Cómo redactar la interpretación de un intervalo

**Estructura:** `Con un nivel de confianza de [X]%, se estima que [parámetro] de [población] se encuentra entre [Li] y [Ls] [unidades].`

| Elemento obligatorio | Ejemplo |
|---|---|
| Nivel de confianza | "Con un 95 % de confianza" |
| La palabra **real** o **poblacional** | "el peso promedio **real**" |
| Parámetro (promedio o proporción) | "peso promedio" |
| Población | "de los hombres de 60 años y más" |
| Límites con unidades | "entre 64,71 kg y 77,59 kg" |

**Ejemplo bien redactado (media):**
> Con un nivel de confianza del 98 %, se estima que el peso promedio real de los hombres de 60 años y más se encuentra entre 64,71 kg y 77,59 kg.

**Ejemplo bien redactado (proporción):**
> Con un nivel de confianza del 95 %, mediante el método de Wilson se estima que la proporción real de personas de 60 años y más con un peso mayor a 50 kg está entre 75,00 % y 95,03 %.

**Ejemplo de estimación puntual:**
> La estimación puntual para el peso promedio poblacional de los hombres de 60 años y más es de 71,15 kg.

**Errores comunes al interpretar:**

| Mal | Bien |
|---|---|
| "Hay 95 % de probabilidad de que la media muestral esté en el intervalo" | La confianza se refiere al parámetro **real**, no a la muestra |
| Omitir unidades | Siempre kg, cm, kg/m², años, etc. |
| No decir "promedio" o "proporción" | Indicar siempre qué parámetro se estima |
| Decir "el 95 % de las personas pesa entre..." | El intervalo es del **promedio**, no de los individuos |
| Mencionar el método sin saberlo | Si usó `prop.test` se dice Wilson; si fue manual, Wald |

**Longitud del intervalo y confianza:** longitud = `2E`; con `E` se despeja el valor crítico y se obtiene la confianza. Interpretar: "la confianza empleada fue de X %".

---

## 3. Contraste de hipótesis: cómo plantear H₀ y H₁

### 3.1 Reglas de oro

1. **H₀ siempre lleva igualdad** (`=`, `≤` o `≥`).
2. **H₁ es lo que se quiere demostrar** y es la negación de H₀.
3. Las palabras clave del enunciado definen la cola:

| Palabras en el enunciado | H₁ | Prueba | `alternative` |
|---|---|---|---|
| "es diferente", "existen diferencias", "es distinto de", "cambió" | `≠` | Bilateral | `"two.sided"` |
| "mayor", "superior", "más de", "excede" | `>` | Derecha | `"greater"` |
| "menor", "inferior", "menos de", "por debajo" | `<` | Izquierda | `"less"` |
| "al menos", "como mínimo" (afirmación a refutar) | H₀: `≥`, H₁: `<` | Izquierda | `"less"` |
| "a lo sumo", "como máximo" (afirmación a refutar) | H₀: `≤`, H₁: `>` | Derecha | `"greater"` |

### 3.2 Cómo escribirlas bien

* Escribir **ambas formas**: simbólica **y** descriptiva (el enunciado de tu cátedra lo exige).
* Incluir **parámetro, población y variable** en el texto.
* En H₁, usar la palabra **"significativamente"**.

| Tipo | Plantilla |
|---|---|
| Media, bilateral | H₀: μ = a (El [variable] promedio real de [población] es igual a a) / H₁: μ ≠ a (...es significativamente distinto de a) |
| Media, derecha | H₀: μ ≤ a (...es a lo sumo a) / H₁: μ > a (...es significativamente mayor a a) |
| Media, izquierda | H₀: μ ≥ a (...es al menos a) / H₁: μ < a (...es significativamente menor a a) |
| Diferencia de medias | H₀: μ₁ − μ₂ = 0 (No existen diferencias en el [variable] promedio real según [grupo]) / H₁: μ₁ − μ₂ ≠ 0 (Existen diferencias significativas...) |
| Proporción | H₀: P ≥ 0,50 (La proporción real de... es al menos 50 %) / H₁: P < 0,50 (...es significativamente menor a 50 %) |
| Diferencia de proporciones | H₀: P₁ − P₂ ≤ δ₀ / H₁: P₁ − P₂ > δ₀ |

**Ejemplo completo:**
> H₀: μ ≥ 90 (La circunferencia de la cintura promedio real de las mujeres adultas mayores es de al menos 90 cm)
> H₁: μ < 90 (La circunferencia de la cintura promedio real de las mujeres adultas mayores es significativamente menor a 90 cm)

**Errores comunes:**

| Mal | Bien |
|---|---|
| Poner la igualdad en H₁ | La igualdad siempre va en H₀ |
| Escribir solo símbolos | Escribir símbolo y descripción |
| Invertir H₀ y H₁ | H₁ es lo que se quiere demostrar |
| Usar `p` o `x̄` en las hipótesis | Se usan **parámetros** (μ, P), nunca estadísticos |
| Olvidar el valor δ₀ cuando se pide "diferencia mayor a 10" | `mu = 10` en el código y H₀: μ₁ − μ₂ ≤ 10 |

---

## 4. Contrastes para la media (una muestra)

### 4.1 Códigos

| Caso | Código |
|---|---|
| σ conocida | `z.test(x = base$variable, alternative = , mu = , sigma.x = , conf.level = )` |
| σ desconocida (n grande o pequeña) | `t.test(x = base$variable, alternative = , mu = , conf.level = )` |

* `mu` = valor nulo μ₀.
* `conf.level` = `1 - alpha`.
* **Se usa `z.test` porque σ viene dada**; **se usa `t.test` porque σ se estima con `s`**.

### 4.2 Qué leer en la salida de R

| Dato de la salida | Para qué sirve |
|---|---|
| `p-value` | Decisión principal: se compara con α |
| `z` o `t` | Estadístico de prueba, se compara con el valor crítico |
| `df` | Grados de libertad, se usan en `qt()` |
| `mean of x` | Estimación puntual |

### 4.3 Regla de decisión

| Resultado | Decisión |
|---|---|
| `p-valor < α` | **Se rechaza H₀** |
| `p-valor ≥ α` | **No se rechaza H₀** |

**Por región de rechazo** (usa `qnorm`/`qt` para el valor crítico):

| H₁ | Se rechaza H₀ si |
|---|---|
| `≠` | `|estadístico| > crítico(α/2)` |
| `>` | `estadístico > crítico(α)` |
| `<` | `estadístico < −crítico(α)` |

### 4.4 Cómo redactar la conclusión

**Estructura:** `Como [p-valor] [<, >] α = [α], [se rechaza / no se rechaza] H₀. [Hay / No hay] evidencia estadística, al nivel de [α·100] %, para afirmar que [H₁ en palabras].`

**Plantilla si SE RECHAZA H₀:**
> Como el p-valor (0,005) es menor que α = 0,02, se rechaza H₀. Existen evidencias, al nivel del 2 %, para afirmar que el peso promedio real de las personas adultas mayores es significativamente mayor a 58 kg.

**Plantilla si NO SE RECHAZA H₀:**
> Como el p-valor (0,434) es mayor que α = 0,05, no se rechaza H₀. No existen evidencias suficientes, al nivel del 5 %, para afirmar que la circunferencia de la cintura promedio real de las mujeres adultas mayores es significativamente menor a 90 cm.

**Reglas para una buena conclusión:**

* Citar el **p-valor** y **compararlo con α**.
* Decir explícitamente **"se rechaza"** o **"no se rechaza"** H₀.
* Mencionar el **nivel de significancia** ("al nivel del X %").
* Retomar **H₁ con palabras del contexto** (variable, población, unidades).
* Usar "significativamente" cuando se rechaza H₀.
* Si no se rechaza: **nunca decir "se acepta H₀"** ni "se demostró que es igual". Se dice "no hay evidencia suficiente".

**Errores comunes:**

| Mal | Bien |
|---|---|
| "Se acepta H₀" | "No se rechaza H₀" |
| "Se demostró que la media es 90" | "No hay evidencia para afirmar que sea menor a 90" |
| Concluir sin α ni p-valor | Siempre citar ambos |
| Concluir con símbolos solamente | Escribir la conclusión en el contexto del problema |
| Confundir confianza con significancia | Confianza = 1 − α. Si piden α = 2 %, `conf.level = 0.98` |

---

## 5. Contraste para la diferencia de medias

### 5.1 Códigos

| Caso | Código | Por qué |
|---|---|---|
| σ₁ y σ₂ conocidas | `z.test(x = , y = , alternative = , sigma.x = , sigma.y = , mu = , conf.level = )` | Las desviaciones son dato |
| σ desconocida (n grande o pequeña), varianzas iguales | `t.test(x = , y = , alternative = , mu = , conf.level = , var.equal = T)` | Se estima la desviación combinada con `n1 + n2 − 2` g.l. |

* `mu` = valor de la diferencia a contrastar (δ₀). Si la hipótesis es "no hay diferencias", `mu = 0`.
* **El orden de `x` e `y` importa:** `x` es el grupo 1 (μ₁) y `y` el grupo 2 (μ₂). La hipótesis alternativa `greater` significa `μ₁ − μ₂ > δ₀`.
* Para comparar por grupos: `base$peso[base$sexo == "M"]` vs `base$peso[base$sexo == "F"]`.

### 5.2 Ejemplos de redacción

**Bilateral (no se rechaza):**
> H₀: μ₁ − μ₂ = 0 (La circunferencia de la cintura promedio real es igual entre hombres y mujeres adultos mayores)
> H₁: μ₁ − μ₂ ≠ 0 (Existen diferencias significativas en la circunferencia de la cintura promedio real según el sexo)
>
> **Conclusión:** Como el p-valor (0,2852) es mayor que α = 0,02, no se rechaza H₀. No existen evidencias, al nivel del 2 %, para afirmar que existen diferencias significativas en la circunferencia de la cintura promedio real según el sexo.

**Unilateral con δ₀ ≠ 0 (se rechaza):**
> H₀: μ₁ − μ₂ ≤ 10 (La diferencia entre el peso promedio real de hombres y mujeres es de a lo sumo 10 kg)
> H₁: μ₁ − μ₂ > 10 (La diferencia entre el peso promedio real de hombres y mujeres es significativamente mayor a 10 kg)
>
> **Conclusión:** Como el p-valor (0,044) es menor que α = 0,05, se rechaza H₀. Existen evidencias, al nivel del 5 %, para afirmar que la diferencia entre el peso promedio real de hombres y mujeres es significativamente mayor a 10 kg.

**Tips:**

* Mencionar **ambos grupos** y la **variable de agrupación**.
* En "mayor a 10 kg" el 10 va en `mu`, no se resta antes.
* Revisar que la salida diga `true difference in means is greater than ...`: confirma que la cola quedó bien.

---

## 6. Contraste para una proporción

### 6.1 Códigos del PDF (manual)

| Paso | Qué hace |
|---|---|
| `x <- length(which(condicion))` | Cuenta los casos con la característica |
| `n <- length(base$variable)` | Tamaño de la muestra |
| `ptecho <- x/n` | Proporción muestral |
| `z <- (ptecho - p0) / sqrt(p0*(1 - p0)/n)` | Estadístico de prueba |
| `qnorm(1 - alpha)` (una cola) o `qnorm(1 - alpha/2)` (dos colas) | Valor crítico |
| `p <- 1 - pnorm(abs(z))` (una cola) o `p <- 2*(1 - pnorm(abs(z)))` (dos colas) | Valor p |

* **Se hace manual porque** el PDF no incluye `prop.test` para contrastes, solo para intervalos. El estadístico usa **P₀** (valor de H₀) en el denominador, no `p̂`.
* **Ojo:** `1 - pnorm(abs(z))` es una cola. Para `≠` hay que **multiplicar por 2**.

### 6.2 Decisión por región de rechazo

| H₁ | Se rechaza H₀ si |
|---|---|
| `P ≠ P₀` | `z < −z(α/2)` ó `z > z(α/2)` |
| `P > P₀` | `z > zα` |
| `P < P₀` | `z < −zα` |

### 6.3 Ejemplo de redacción

> H₀: P = 0,20 (La proporción real de personas graduadas en ciencias sociales que encuentran trabajo en su especialidad en menos de dos años es 20 %)
> H₁: P ≠ 0,20 (La proporción real es significativamente distinta de 20 %)
>
> **Conclusión:** Como el p-valor (0,26) es mayor que α = 0,04 (y −2,05 < z = −1,12 < 2,05), no se rechaza H₀. No existen evidencias, al nivel del 4 %, para afirmar que la proporción real de personas graduadas en ciencias sociales que encuentran trabajo en su especialidad en menos de dos años es significativamente distinta de 20 %.

---

## 7. Contraste para la diferencia de proporciones

### 7.1 Código

* Se usa el bloque manual del PDF: `p1`, `p2`, `num <- p1 - p2 - delta0`, `den <- sqrt(...)`, `z <- num/den`.
* **Una cola:** `c(zalpha, z)`. **Dos colas:** `c(-zalpham, zalpham, z)`.
* **Valor p:** `1 - pnorm(abs(z))` (una cola) o `2*(1 - pnorm(abs(z)))` (dos colas).

### 7.2 Cuidados importantes

| Detalle | Por qué importa |
|---|---|
| `n1` y `n2` deben ser el tamaño de **cada grupo** | Con condiciones en dos grupos (ej. hombres vs mujeres) cada n es el total del grupo |
| `delta0` | Es el valor nulo de P₁ − P₂ (0 si "no hay diferencia") |
| El orden grupo 1 / grupo 2 | Define el signo de la diferencia |

### 7.3 Ejemplo de redacción

> H₀: P₁ − P₂ ≤ 0,05 (La diferencia entre la proporción de hombres y de mujeres con IMC > 30 es de a lo sumo 5 %)
> H₁: P₁ − P₂ > 0,05 (La proporción real de hombres con IMC > 30 supera en más de 5 % a la de mujeres)
>
> **Conclusión:** Como z = 0,9987 < zα = 1,6449 (y el p-valor = 0,159 > 0,05), no se rechaza H₀. No existen evidencias, al nivel del 5 %, para afirmar que la proporción real de hombres con IMC mayor a 30 supere en más de 5 % a la proporción de mujeres con IMC mayor a 30.

---

## 8. Errores tipo I y II (redacción)

| Error | Se comete cuando | Plantilla |
|---|---|---|
| **Tipo I (α)** | Se rechaza H₀ siendo verdadera | "Decir que [H₁ en palabras] cuando en realidad [H₀ en palabras]" |
| **Tipo II (β)** | No se rechaza H₀ siendo falsa | "Decir que [H₀ en palabras] cuando en realidad [H₁ en palabras]" |

**Ejemplo (H₀: μ ≥ 25, H₁: μ < 25, tiempo de atención):**

| Error | Interpretación |
|---|---|
| Tipo I | Decir que el tiempo promedio real de atención es significativamente menor a 25 minutos cuando en realidad no lo es |
| Tipo II | Decir que el tiempo promedio real de atención es de al menos 25 minutos cuando en realidad es significativamente menor |

* **Potencia** = 1 − β = probabilidad de rechazar H₀ cuando es falsa.

---

## 9. Regresión lineal simple

### 9.1 Códigos y para qué sirve cada uno

| Objetivo | Código | Por qué |
|---|---|---|
| Estimar el modelo | `mod <- lm(formula = y ~ x, data = base)` | Ajusta la recta; `y` es la dependiente, `x` la independiente |
| Ver coeficientes, p-valores, R² | `summary(mod)` | Resumen principal para casi todas las preguntas |
| Correlación | `cor(base$x, base$y, method = "pearson")` | Mide fuerza y dirección de la relación lineal |
| R² | `cor(...)^2` o `summary(mod)$r.squared` | Porcentaje de variabilidad explicada |
| Normalidad de residuos | `shapiro.test(mod$residuals)` | Verifica supuesto ε ~ N(0, σ²) |
| Varianza constante | `car::ncvTest(mod)` | Verifica homocedasticidad |
| Gráfico de dispersión | `ggplot(data = base, aes(x = , y = )) + geom_point(shape = 1)` | Ver visualmente la relación |

### 9.2 Cómo leer `summary(mod)`

| Parte | Significado |
|---|---|
| `Estimate` de `(Intercept)` | **a**: valor de `y` cuando `x = 0` |
| `Estimate` de la variable x | **b**: cambio promedio en `y` por cada unidad de `x` |
| `Pr(>|t|)` de la variable x | Valor p de la prueba de significancia de la pendiente |
| `Multiple R-squared` | R² |
| `Residual standard error` | Error estándar de estimación |

### 9.3 Cómo redactar cada interpretación

**Ecuación del modelo:** ŷ = a + b·x. Ej.: `imc = 4,6238 + 0,7354 · muac`.

**Pendiente (b):**
> Por cada centímetro adicional en la circunferencia del brazo, se espera que el índice de masa corporal aumente, en promedio, 0,7354 kg/m².

* Si `b` es negativa: "disminuya".
* Siempre incluir **"en promedio"** y **las unidades de ambas variables**.

**Intercepto (a):** "Cuando [x] es 0, se espera un [y] promedio de [a]". Solo tiene sentido práctico si `x = 0` es posible en el contexto; si no, se dice que no tiene interpretación práctica.

**Coeficiente de correlación (r):**

| |r| | Clasificación |
|---|---|
| 0,00 a < 0,10 | Nula o muy débil |
| 0,10 a < 0,30 | Débil |
| 0,30 a < 0,50 | Moderada |
| 0,50 a 1,00 | Fuerte |

> Existe una relación lineal directa y fuerte (r = 0,73) entre la circunferencia del brazo y el índice de masa corporal.

* Signo positivo = **directa**; negativo = **inversa**.

**Coeficiente de determinación (R²):**
> El 53,32 % de la variabilidad en el índice de masa corporal es explicada por la variabilidad en la circunferencia del brazo.

**Error estándar de estimación:**
> En promedio, los valores observados del IMC se alejan 2,53 kg/m² de los valores estimados por el modelo.

### 9.4 Significancia del modelo (prueba sobre la pendiente)

> H₀: b = 0 (La pendiente de la recta de regresión real es cero. No existe relación lineal entre la circunferencia del brazo y el índice de masa corporal)
> H₁: b ≠ 0 (La pendiente de la recta de regresión real es significativamente distinta de cero. Existe relación lineal entre la circunferencia del brazo y el índice de masa corporal)
>
> **Conclusión:** Como el p-valor (≈ 0,0000) es menor que α = 0,05, se rechaza H₀. Existen evidencias, al nivel del 5 %, para afirmar que existe una relación lineal significativa entre la circunferencia del brazo y el índice de masa corporal.

* Se toma el p-valor de la **fila de la variable x**, no el del intercepto.
* Si p ≥ α: "no existen evidencias de relación lineal significativa; el modelo no es adecuado para predecir".

### 9.5 Supuestos del modelo

| Supuesto | Código | H₀ | H₁ |
|---|---|---|---|
| Normalidad de residuos | `shapiro.test(mod$residuals)` | Los residuos se distribuyen de manera normal | Los residuos no se distribuyen de manera normal |
| Varianza constante | `ncvTest(model = mod)` | La varianza de los residuos es constante | La varianza de los residuos no es constante |

**Conclusiones modelo (cuando se cumple el supuesto):**

> **Normalidad:** Como el p-valor (0,8537) es mayor que α = 0,05, no se rechaza H₀. No existen evidencias, al nivel del 5 %, para afirmar que los residuos no se distribuyen de manera normal; se cumple el supuesto de normalidad.
>
> **Varianza constante:** Como el p-valor (0,5962) es mayor que α = 0,05, no se rechaza H₀. No existen evidencias, al nivel del 5 %, para afirmar que la varianza de los residuos no es constante; se cumple el supuesto de homocedasticidad.

* **Aquí lo deseable es NO rechazar H₀.** Si se rechaza, el supuesto **no se cumple** y se advierte que el modelo puede no ser confiable.

**Otros supuestos (de teoría):** n mayor que el número de parámetros, variabilidad en X, y modelo correctamente especificado (relación lineal).

### 9.6 Predicción

* Se usa `predict(mod, data.frame(x = valor))`. Hay que respetar el **nombre exacto** de la variable independiente.
* Con `interval = "prediction"` se obtiene un intervalo para un valor individual.

> **Predicción:** Se espera que, en promedio, una persona con una circunferencia del brazo de 27 cm presente un índice de masa corporal de 24,48 kg/m².
>
> **Intervalo:** Con un nivel de confianza del 95 %, el verdadero índice de masa corporal de una persona con circunferencia del brazo de 27 cm se encuentra entre 19,32 y 29,64 kg/m².

* Predecir solo dentro del **rango de valores observados** de `x`; fuera de él es extrapolación.

---

## 10. Checklist final para la prueba

### Antes de correr el código

1. Identificar **parámetro** (media, proporción, diferencia, pendiente).
2. Identificar si **σ es conocida** y el **tamaño de muestra**.
3. Identificar si hay **N** (población finita).
4. Traducir las palabras del enunciado a **H₀ y H₁** y a la **cola**.
5. Convertir α en `conf.level = 1 - α`.

### Después de correr el código

1. Leer **p-valor** y compararlo con α.
2. Confirmar en la salida que `alternative hypothesis` coincide con H₁.
3. Decidir: rechazar o no rechazar H₀.
4. Redactar la conclusión **en contexto**, con α, variable, población y unidades.

### Resumen de plantillas

| Tarea | Plantilla |
|---|---|
| **Intervalo** | Con un nivel de confianza del X %, se estima que [parámetro] real de [población] está entre [Li] y [Ls] [unidades]. |
| **Rechaza H₀** | Como p-valor < α, se rechaza H₀. Existen evidencias, al nivel del X %, para afirmar que [H₁ en palabras]. |
| **No rechaza H₀** | Como p-valor > α, no se rechaza H₀. No existen evidencias suficientes, al nivel del X %, para afirmar que [H₁ en palabras]. |
| **Pendiente** | Por cada unidad adicional de [x], se espera que [y] aumente/disminuya, en promedio, [b] [unidades]. |
| **R²** | El [R² %] de la variabilidad en [y] es explicada por la variabilidad en [x]. |
| **Supuesto** | Como p-valor > α, no se rechaza H₀; no hay evidencias de que [se incumpla el supuesto]. |