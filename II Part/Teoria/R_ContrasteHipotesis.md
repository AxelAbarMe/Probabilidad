# Contraste de hipótesis con R
**Autor:** E. A.
**Fecha:** 2026-05-28  

---

```r
# cargando la base
library(readxl)
base_creles <- read_excel("/Users/eduardo/Documents/trabajo/curso_R/base_creles.xlsx")

```

---

## Contraste de hipótesis para la media

Suponga que las variables continuas que se mencionan a continuación siguen una distribución normal.

### σ conocida

Para el caso de σ conocida se utiliza la función `z.test(x, alternative, mu, sigma.x, conf.level, ...)` del paquete `BSDA`, donde:

* **`x`**: vector de datos.
* **`alternative (H1)`**: representa la hipótesis alternativa:
* μ != μ₀ -> "two.sided"
* μ > μ₀  -> "greater"
* μ < μ₀  -> "less"


* **`mu`**: representa el valor de μ₀.
* **`sigma.x`**: valor de la desviación estándar poblacional.
* **`conf.level`**: nivel de confianza de la prueba (1 - α).

> **Nota para los ejercicios:** En los apartados H₀ y H₁ debe escribirse la hipótesis tanto en forma estadística (usando los símbolos correspondientes) como en forma escrita/descriptiva. Asimismo, en la sección de Conclusión se debe agregar la interpretación del resultado obtenido a partir del p-valor o la región de rechazo.

#### Ejemplo

Investigue si la circunferencia de la cintura de las mujeres adultas mayores es inferior a 90 cm. Suponga en este caso que la desviación estándar poblacional es de 8.10 cm y utilice un nivel de significancia de 5%.

**Planteamiento de hipótesis:**

H₀: μ ≥ 90 (La circunferencia de la cintura promedio de las mujeres adultas mayores es mayor o igual a 90 cm)

H₁: μ < 90 (La circunferencia de la cintura promedio de las mujeres adultas mayores es inferior a 90 cm)

```r
if(!require("BSDA")){
  install.packages("BSDA")
  library("BSDA")
}

z.test(x = base_creles$cc[base_creles$sexo=="F"],
       alternative = "less",
       mu = 90,
       sigma.x = 8.10,
       conf.level = 0.95)

```

**Resultado:**

```text
## 
## 	One-sample z-Test
## 
## data:  base_creles$cc[base_creles$sexo == "F"]
## z = -0.16631, p-value = 0.434
## alternative hypothesis: true mean is less than 90
## 95 percent confidence interval:
##        NA 92.30481
## sample estimates:
## mean of x 
##  89.74074

```

**Cálculo del estadístico de prueba y valor crítico:**

```r
x_bar <- mean(base_creles$cc[base_creles$sexo=="F"]) # 89.74074
n <- length(base_creles$cc[base_creles$sexo=="F"])   # 27
sigma <- 8.10
mu0 <- 90
alpha <- 0.05

# Estadístico z calculando manualmente: z = (x_bar - mu0) / (sigma / sqrt(n))
z_calc <- (x_bar - mu0) / (sigma / sqrt(n)) # -0.16631

# Valor crítico Z_alpha (cola izquierda)
z_crit <- qnorm(alpha) # -1.644854
c(Z_calculado = z_calc, Z_critico = z_crit)

```

**Conclusión:** Como el p-valor (0.434) es mayor que el nivel de significancia α = 0.05 (y el estadístico z_calculado = -0.16631 no cae en la región de rechazo z < -1.644854), no se rechaza H₀. No existe evidencia estadística suficiente para afirmar que la circunferencia de la cintura promedio de las mujeres adultas mayores sea inferior a 90 cm.

---

### σ desconocida y muestra grande (n > 30)

Para el caso de σ desconocida y muestra grande se utiliza la función `t.test(x, alternative, mu, conf.level, ...)`, donde:

* **`x`**: vector de datos.
* **`alternative`**: representa la hipótesis alternativa:
* μ != μ₀ -> "two.sided"
* μ > μ₀  -> "greater"
* μ < μ₀  -> "less"


* **`mu`**: representa el valor de μ₀.
* **`conf.level`**: nivel de confianza de la prueba.

#### Ejemplo

Considere la base `base_creles` y determine si el peso promedio de las personas adultas mayores es mayor a 58 kg. Utilice un nivel de significancia de 2%.

**Planteamiento de hipótesis:**

H₀: μ ≤ 58 (El peso promedio de las personas adultas mayores es menor o igual a 58 kg)

H₁: μ > 58 (El peso promedio de las personas adultas mayores es mayor a 58 kg)

```r
t.test(x = base_creles$peso,
       alternative = "greater",
       mu = 58,
       conf.level = 0.98)

```

**Resultado:**

```text
## 
## 	One Sample t-test
## 
## data:  base_creles$peso
## t = 2.6619, df = 49, p-value = 0.005239
## alternative hypothesis: true mean is greater than 58
## 98 percent confidence interval:
##  59.01772      Inf
## sample estimates:
## mean of x 
##  62.90727

```

**Cálculo del estadístico de prueba y valor crítico:**

```r
# Valor crítico t con 49 grados de libertad para alpha = 0.02
t_crit <- qt(1 - 0.02, df = 49) # 2.109873
c(t_calculado = 2.6619, t_critico = t_crit)

```

**Conclusión:** Dado que el p-valor (0.005239) es menor que el nivel de significancia α = 0.02 y el estadístico de prueba t_calculado = 2.6619 es mayor que el valor crítico t_crítico = 2.109873, se rechaza H₀. Existe evidencia estadística suficiente con un 98% de confianza para afirmar que el peso promedio de las personas adultas mayores es mayor a 58 kg.

---

### σ desconocida y muestra pequeña (n ≤ 30)

Para el caso de σ desconocida y muestra pequeña se utiliza la función `t.test(x, alternative, mu, conf.level, ...)`, donde:

* **`x`**: vector de datos.
* **`alternative`**: representa la hipótesis alternativa:
* μ != μ₀ -> "two.sided"
* μ > μ₀  -> "greater"
* μ < μ₀  -> "less"


* **`mu`**: representa el valor de μ₀.
* **`conf.level`**: nivel de confianza de la prueba.

#### Ejemplo

Se quiere determinar si el imc promedio de los hombres es superior a 24 kg/m². Utilice un nivel de significancia de 3%.

**Planteamiento de hipótesis:**

H₀: μ ≤ 24 (El IMC promedio de los hombres adultos mayores es menor o igual a 24 kg/m²)

H₁: μ > 24 (El IMC promedio de los hombres adultos mayores es superior a 24 kg/m²)

```r
t.test(x = base_creles$imc[base_creles$sexo=="M"],
       alternative = "greater",
       mu = 24,
       conf.level = 1 - 0.03)

```

**Resultado:**

```text
## 
## 	One Sample t-test
## 
## data:  base_creles$imc[base_creles$sexo == "M"]
## t = 3.104, df = 22, p-value = 0.002588
## alternative hypothesis: true mean is greater than 24
## 97 percent confidence interval:
##  24.83228      Inf
## sample estimates:
## mean of x 
##  26.30435

```

**Cálculo del estadístico de prueba y valor crítico:**

```r
# Grados de libertad = n - 1 = 23 - 1 = 22
t_crit <- qt(1 - 0.03, df = 22) # 1.9742
c(t_calculado = 3.104, t_critico = t_crit)

```

**Conclusión:** Como el p-valor (0.002588) es menor que α = 0.03 (y t_calculado = 3.104 > t_crítico = 1.9742), se rechaza la hipótesis nula H₀. Con un 97% de confianza se concluye que el IMC promedio de los hombres es significativamente superior a 24 kg/m².

---

## Contraste de hipótesis para la diferencia de medias

### σ conocida

Para el caso de σ conocida se utiliza la función `z.test(x, y, alternative, mu, sigma.x, sigma.y, conf.level, ...)` del paquete `BSDA`, donde:

* **`x`**: vector de datos de una muestra.
* **`y`**: vector de datos de la otra muestra.
* **`alternative`**: representa la hipótesis alternativa: “two.sided”, “greater” o “less”.
* **`mu`**: representa el valor de μ₁ - μ₂, o bien, el δ₀.
* **`sigma.x`**: valor de la desviación estándar poblacional de una muestra.
* **`sigma.y`**: valor de la desviación estándar poblacional de la otra muestra.
* **`conf.level`**: nivel de confianza de la prueba.

#### Ejemplo

Investigue si existen diferencias en la circunferencia de la cintura promedio de las personas adultas mayores según el sexo. Suponga en este caso que la desviación estándar poblacional es de 16.31 cm para los hombres y de 8.10 cm para las mujeres. Utilice un nivel de significancia de 2%.

**Planteamiento de hipótesis:**

H₀: μ₁ - μ₂ = 0 (La circunferencia de la cintura promedio es igual entre hombres y mujeres)

H₁: μ₁ - μ₂ != 0 (Existen diferencias en la circunferencia de la cintura promedio según el sexo)

```r
z.test(x = base_creles$cc[base_creles$sexo=="M"],
       y = base_creles$cc[base_creles$sexo=="F"],
       alternative = "two.sided",
       sigma.x = 16.31,
       sigma.y = 8.10,
       mu = 0,
       conf.level = 0.98)

```

**Resultado:**

```text
## 
## 	Two-sample z-Test
## 
## data:  base_creles$cc[base_creles$sexo == "M"] and base_creles$cc[base_creles$sexo == "F"]
## z = 1.0688, p-value = 0.2852
## alternative hypothesis: true difference in means is not equal to 0
## 98 percent confidence interval:
##  -4.704738 12.701517
## sample estimates:
## mean of x mean of y 
##  93.73913  89.74074

```

**Cálculo del estadístico de prueba y valor crítico:**

```r
alpha <- 0.02
z_crit <- qnorm(1 - alpha/2) # Valor crítico bilaterial 2.3263
c(z_calculado = 1.0688, z_critico_bilateral = z_crit)

```

**Conclusión:** Dado que el p-valor (0.2852) es superior al nivel de significancia α = 0.02 (y el estadístico |z_calculado| = 1.0688 < 2.3263), no se rechaza H₀. No existe evidencia estadística suficiente para sostener que existan diferencias significativas en la circunferencia de la cintura promedio según el sexo.

---

### σ desconocida y muestra grande (n > 30)

Para el caso de σ desconocida y muestra grande se utiliza la función `t.test(x, y, alternative, mu, conf.level, var.equal...)`, donde:

* **`x`**: vector de datos de una muestra.
* **`y`**: vector de datos de la otra muestra.
* **`alternative`**: representa la hipótesis alternativa: “two.sided”, “greater” o “less”.
* **`mu`**: representa el valor de μ₁ - μ₂, o bien, δ₀.
* **`conf.level`**: nivel de confianza de la prueba.
* **`var.equal`**: indica si las variancias poblacionales son iguales

#### Ejemplo

Considere la base `base_creles` y determine si existe una diferencia mayor a 10 kg en el peso promedio de las personas adultas mayores según el sexo. Utilice un nivel de significancia de 5%.

**Planteamiento de hipótesis:**

H₀: μ₁ - μ₂ ≤ 10 (La diferencia de peso promedio entre hombres y mujeres es menor o igual a 10 kg)

H₁: μ₁ - μ₂ > 10 (La diferencia de peso promedio entre hombres y mujeres es mayor a 10 kg)

```r
mean(base_creles$peso[base_creles$sexo=="M"])

```

**Resultado:**

```text
## [1] 71.14625

```

```r
mean(base_creles$peso[base_creles$sexo=="F"])

```

**Resultado:**

```text
## [1] 55.88889

```

```r
t.test(x = base_creles$peso[base_creles$sexo=="M"],
       y = base_creles$peso[base_creles$sexo=="F"],
       alternative = "greater",
       mu = 10,
       conf.level = 0.95,
       var.equal = T)

```

**Resultado:**

```text
## 
## 	Two Sample t-test
## 
## data:  base_creles$peso[base_creles$sexo == "M"] and base_creles$peso[base_creles$sexo == "F"]
## t = 1.7412, df = 48, p-value = 0.04403
## alternative hypothesis: true difference in means is greater than 10
## 95 percent confidence interval:
##  10.19313      Inf
## sample estimates:
## mean of x mean of y 
##  71.14625  55.88889

```

**Cálculo del estadístico de prueba y valor crítico:**

```r
t_crit <- qt(1 - 0.05, df = 48) # 1.677224
c(t_calculado = 1.7412, t_critico = t_crit)

```

**Conclusión:** Como el p-valor (0.04403) es menor que el nivel de significancia α = 0.05 y el estadístico t_calculado = 1.7412 es mayor que t_crítico = 1.6772, se rechaza H₀. Se concluye con un 95% de confianza que la diferencia en el peso promedio entre hombres y mujeres adultas mayores es significativamente mayor a 10 kg.

---

### σ desconocida y muestra pequeña (n ≤ 30)

Para el caso de σ desconocida y muestra pequeña se utiliza la función `t.test(x, y, alternative, mu, conf.level, var.equal...)`, donde:

* **`x`**: vector de datos de una muestra.
* **`y`**: vector de datos de la otra muestra.
* **`alternative`**: representa la hipótesis alternativa: “two.sided”, “greater” o “less”.
* **`mu`**: representa el valor de μ₁ - μ₂, o bien, δ₀.
* **`conf.level`**: nivel de confianza de la prueba.
* **`var.equal`**: indica si las variancias poblacionales son iguales.

#### Ejemplo

Se quiere determinar si existen diferencias en el imc promedio según el sexo. Utilice un nivel de significancia de 3%.

**Planteamiento de hipótesis:**

H₀: μ₁ - μ₂ = 0 (El IMC promedio de hombres y mujeres es igual)

H₁: μ₁ - μ₂ != 0 (El IMC promedio difiere según el sexo)

```r
t.test(x = base_creles$imc[base_creles$sexo=="M"],
       y = base_creles$imc[base_creles$sexo=="F"],
       alternative = "two.sided",
       mu = 0,
       conf.level = 0.97,
       var.equal = T)

```

**Resultado:**

```text
## 
## 	Two Sample t-test
## 
## data:  base_creles$imc[base_creles$sexo == "M"] and base_creles$imc[base_creles$sexo == "F"]
## t = 1.076, df = 48, p-value = 0.2873
## alternative hypothesis: true difference in means is not equal to 0
## 97 percent confidence interval:
##  -1.207063  3.445389
## sample estimates:
## mean of x mean of y 
##  26.30435  25.18519

```

**Cálculo del estadístico de prueba y valor crítico:**

```r
t_crit <- qt(1 - 0.03/2, df = 48) # 2.2415
c(t_calculado = 1.076, t_critico_bilateral = t_crit)

```

**Conclusión:** Ya que el p-valor (0.2873) es mayor que α = 0.03, no se rechaza H₀. No existe evidencia suficiente para concluir que existan diferencias significativas en el IMC promedio entre hombres y mujeres de 60 años y más.

---

## Contraste de hipótesis para la proporción poblacional

Para el caso de la proporción poblacional se utiliza la función `prop.test(x, n, alternative, conf.level, correct)`, cuando p(1-p) ≥ 5.

donde:

* **`x`**: el número de elementos que cumplen con la característica de interés en la muestra.
* **`n`**: total de datos de la muestra.
* **`alternative`**: representa la hipótesis alternativa: “two.sided”, “greater” o “less”.
* **`p`**: representa el valor de P₀.
* **`conf.level`**: nivel de confianza de la prueba (1 - α).
* **`correct`**: indica si es necesario la corrección de Yates.

### Ejemplo

Se quiere determinar si la proporción de hombres es menor a 50%. Utilice un nivel de significancia de 5%.

**Planteamiento de hipótesis:**

H₀: P ≥ 0.50 (La proporción poblacional de hombres es mayor o igual al 50%)

H₁: P < 0.50 (La proporción poblacional de hombres es inferior al 50%)

```r
x <- length(which(base_creles$sexo== "M"))
n <- length(base_creles$sexo)
prop.test(x = x, 
          n = n,
          p = 0.50,
          alternative = "less",
          conf.level = 0.95,
          correct = F)

```

**Resultado:**

```text
## 
## 	1-sample proportions test without continuity correction
## 
## data:  x out of n, null probability 0.5
## X-squared = 0.32, df = 1, p-value = 0.2858
## alternative hypothesis: true p is less than 0.5
## 95 percent confidence interval:
##  0.000000 0.574993
## sample estimates:
##    p 
## 0.46

```

**Cálculo del estadístico de prueba y valor crítico:**

```r
p_hat <- x / n # 0.46
p0 <- 0.50
z_calc <- (p_hat - p0) / sqrt(p0 * (1 - p0) / n) # -0.5656854 (Nota: X-squared = z^2 = 0.32)
z_crit <- qnorm(0.05) # -1.644854
c(Z_calculado = z_calc, Z_critico = z_crit)

```

**Conclusión:** Como el p-valor (0.2858) es mayor que el nivel de significancia α = 0.05, no se rechaza H₀. No hay suficiente evidencia estadística para afirmar que la proporción de hombres en la población sea inferior al 50%.

---

## Contraste de hipótesis para la diferencia proporciones

Para el caso de la diferencia de proporciones poblacionales se utiliza la función `prop.test(x, n, alternative, conf.level, correct)`, cuando p₁(1-p₁) ≥ 5, p₂(1-p₂) ≥ 5 y δ = 0.

donde:

* **`x`**: un vector con la cantidad de elementos de cada muestra
* **`n`**: vector con el total de datos de CADA muestra.
* **`alternative`**: representa la hipótesis alternativa: “two.sided”, “greater” o “less”.
* **`p`**: representa el valor de P₁ - P₂, o bien, el δ₀.
* **`conf.level`**: nivel de confianza de la prueba.
* **`correct`**: indica si es necesario la corrección por continuidad cuando el δ = 0.

### Ejemplo

Se quiere determinar si la proporción de hombres y de mujeres adultos mayores es la misma. Utilice un nivel de significancia de 5%.

**Planteamiento de hipótesis:**

H₀: P₁ - P₂ = 0 (La proporción de hombres y mujeres es igual)

H₁: P₁ - P₂ != 0 (La proporción de hombres y mujeres es diferente)

```r
x1 <- length(which(base_creles$sexo == "M"))
x2 <- length(which(base_creles$sexo == "F"))
n1 <- length(base_creles$sexo)
n2 <- length(base_creles$sexo)
prop.test(x = c(x1, x2), 
          n = c(n1, n2),
          alternative = "two.sided",
          conf.level = 0.95,
          correct = T)

```

**Resultado:**

```text
## 
## 	2-sample test for equality of proportions with continuity correction
## 
## data:  c(x1, x2) out of c(n1, n2)
## X-squared = 0.36, df = 1, p-value = 0.5485
## alternative hypothesis: two.sided
## 95 percent confidence interval:
##  -0.2953682  0.1353682
## sample estimates:
## prop 1 prop 2 
##   0.46   0.54

```

**Cálculo del estadístico de prueba y valor crítico:**

```r
z_crit <- qnorm(1 - 0.05/2) # 1.959964
c(Chi2_calculado = 0.36, Z_critico_bilateral = z_crit)

```

**Conclusión:** Dado que el p-valor (0.5485) es superior a α = 0.05, no se rechaza la hipótesis nula H₀. Se concluye que la proporción de hombres y de mujeres adultas mayores no presenta diferencias significativas.

---

### Proporciones con δ ≠ 0

En caso de δ ≠ 0 se trabaja directamente calculando el estadístico Z con la fórmula:

Por lo tanto, el estadístico de prueba está dado por z, tal que:

z = (p̂₁ - p̂₂ - δ₀) / √[ p̂₁(1 - p̂₁)/n₁ + p̂₂(1 - p̂₂)/n₂ ]

#### Ejemplo

Se desea conocer si la proporción de hombres adultos mayores con imc > 30 es superior a 5% a la proporción de mujeres adultas mayores con imc > 30. Utilice un nivel de significancia de 5%.

**Planteamiento de hipótesis:**

H₀: P₁ - P₂ ≤ 0.05 (La diferencia en la proporción de IMC > 30 entre hombres y mujeres es menor o igual al 5%)

H₁: P₁ - P₂ > 0.05 (La proporción de hombres con IMC > 30 supera en más de 5% a la de mujeres)

```r
alpha <- 0.05; delta0 <- 0.05; 
x1 <- length(which(base_creles$sexo == "M" & base_creles$imc > 30))
x2 <- length(which(base_creles$sexo == "F" & base_creles$imc > 30))
n1 <- length(which(base_creles$sexo == "M"))
n2 <- length(which(base_creles$sexo == "F"))
p1 <- x1/n1; p2 <- x2/n2
num <- p1 - p2 - delta0
den <- sqrt(p1*(1 - p1)/n1 + p2*(1 - p2)/n2)
z <- num/den
zalpha <- qnorm(1 - alpha)
p_val <- 1 - pnorm(z)

c(Z_critico = zalpha, Z_calculado = z, P_valor = p_val)

```

**Resultado:**

```text
## [1] 1.6448536 0.9986842 0.1589710

```

**Conclusión:** Puesto que el estadístico de prueba z_calculado = 0.9986842 es menor que el valor crítico z_alpha = 1.6448536 (y el p-valor = 0.158971 > 0.05), no se rechaza H₀. No hay evidencia suficiente para afirmar que la proporción de hombres con obesidad (IMC > 30) supere en más de un 5% a la proporción de mujeres.
