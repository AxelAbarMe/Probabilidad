# Regresión lineal simple y correlación

Hay 2 tipos:

* Simple: Relación entre dos variables
* Múltiple: Relación entre varias variables

Variables Dependientes (x)

Variables Independientes (y)

### Y=a+bX+ϵ

> a,b son parámetros a estudiar, estimar a y b, obtener

### `lm(fórmula, data)`
  * fórmula = y ~ x
  * data = base de datos

---

# R

## Regresión Lineal

**E. A.**

**2026-10-29**

---

## Asociación de variables: regresión lineal simple

El modelo de regresión lineal simple:

Y = a + bX + ϵ

tal que **a** y **b** son los parámetros del modelo.

---

### Ejemplo

Se tiene que uno de los factores que puede indicar sobrepeso u obesidad en las personas es la medida de la circunferencia del brazo. Considere la base de datos `base_creles` e investigue la existencia de una posible relación lineal entre las variables índice de masa corporal (`imc`) y la circunferencia del brazo (`muac`).

El modelo de regresión lineal simple puede estimarse en R con ayuda de la función `lm()`. El modelo debe expresarse de la forma `y ~ x`, donde **y** es la variable dependiente y **x** es la variable independiente.

```r
mod_creles <- lm(imc ~ muac, data = base_creles)
mod_creles

```

```text
## 
## Call:
## lm(formula = imc ~ muac, data = base_creles)
## 
## Coefficients:
## (Intercept)         muac  
##      4.6238       0.7354

```

También pueden obtenerse los valores estimados del modelo.

```r
#lm(ps ~ imc)$fitted
round(mod_creles$fitted, 2)

```

```text
##     1     2     3     4     5     6     7     8     9    10    11    12    13 
## 26.69 25.21 22.27 24.48 28.16 24.48 25.95 25.95 26.69 28.16 27.42 28.89 23.74 
##    14    15    16    17    18    19    20    21    22    23    24    25    26 
## 25.95 24.48 22.27 24.48 25.21 25.21 24.48 23.01 28.16 25.95 23.01 29.63 24.48 
##    27    28    29    30    31    32    33    34    35    36    37    38    39 
## 28.16 24.48 25.21 33.30 29.63 27.42 28.89 27.42 21.54 24.48 28.89 24.48 22.27 
##    40    41    42    43    44    45    46    47    48    49    50 
## 23.74 23.74 23.01 30.36 28.89 23.01 26.69 28.89 20.07 23.74 22.27

```

## Residuos del modelo

La diferencia entre los valores observados y los valores estimados son los residuos del modelo. Estos pueden obtenerse de la siguiente manera:

```r
round(mod_creles$residuals, 2)

```

```text
##     1     2     3     4     5     6     7     8     9    10    11    12    13 
## -2.69  0.79 -3.27  4.52 -0.16 -6.48  4.05  0.05 -2.69  1.84  0.58  4.11 -0.74 
##    14    15    16    17    18    19    20    21    22    23    24    25    26 
##  0.05  0.52 -0.27  0.52 -2.21  1.79 -2.48 -0.01  0.84 -0.95  2.99  2.37  0.52 
##    27    28    29    30    31    32    33    34    35    36    37    38    39 
## -0.16  2.52  1.79 -1.30  1.37  0.58 -1.89 -0.42 -2.54  2.52  2.11 -1.48 -0.27 
##    40    41    42    43    44    45    46    47    48    49    50 
## -2.74 -0.74  0.99 -5.36  0.11  5.99 -2.69 -1.89 -1.07  4.26 -3.27

```

---

## Grados de libertad

Los grados de libertad del modelo (n menos el número de coeficientes a estimar) pueden obtenerse de la siguiente manera:

```r
mod_creles$df

```

```text
## [1] 48

```

---

## Coeficiente de determinación

El R2 o coeficiente de determinación del modelo resulta de elevar al cuadrado el coeficiente de correlación de Pearson.

Representa el porcentaje de variabilidad de la variable respuesta que es explicado por las variables predictoras.

Entre más cercano a 1 (100%) se encuentre el R2, mejor es el ajuste del modelo.

```r
r2 <- cor(base_creles$muac, base_creles$imc)^2; r2

```

```text
## [1] 0.5331987

```
