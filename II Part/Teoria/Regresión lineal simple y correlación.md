# Regresión Lineal

**Autor:** E. A.  
**Fecha:** 2026-10-29  

## Asociación de variables: regresión lineal simple

El modelo de regresión lineal simple:

$$Y = a + bX + \epsilon$$

tal que $a$ y $b$ son los parámetros del modelo.

### Ejemplo

Se tiene que uno de los factores que puede indicar sobrepeso u obesidad en las personas es la medida de la circunferencia del brazo. Considere la base de datos `base_creles` e investigue la existencia de una posible relación lineal entre las variables índice de masa corporal (`imc`) y la circunferencia del brazo (`muac`).

El modelo de regresión lineal simple puede estimarse en R con ayuda de la función `lm()`. El modelo debe expresarse de la forma $y \sim x$, donde $y$ es la variable dependiente y $x$ es la variable independiente.

```r
mod_creles <- lm(imc ~ muac, data = base_creles)
mod_creles
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
##     1     2     3     4     5     6     7     8     9    10    11    12    13 
## -2.69  0.79 -3.27  4.52 -0.16 -6.48  4.05  0.05 -2.69  1.84  0.58  4.11 -0.74 
##    14    15    16    17    18    19    20    21    22    23    24    25    26 
##  0.05  0.52 -0.27  0.52 -2.21  1.79 -2.48 -0.01  0.84 -0.95  2.99  2.37  0.52 
##    27    28    29    30    31    32    33    34    35    36    37    38    39 
## -0.16  2.52  1.79 -1.30  1.37  0.58 -1.89 -0.42 -2.54  2.52  2.11 -1.48 -0.27 
##    40    41    42    43    44    45    46    47    48    49    50 
## -2.74 -0.74  0.99 -5.36  0.11  5.99 -2.69 -1.89 -1.07  4.26 -3.27

```

## Grados de libertad

Los grados de libertad del modelo ($n$ menos el número de coeficientes a estimar) pueden obtenerse de la siguiente manera:

```r
mod_creles$df
## [1] 48

```

## Coeficiente de correlación de Pearson

En el caso de variables continuas con distribución normal medidas a partir de muestras aleatorias, el nivel de asociación lineal entre dos variables puede medirse por medio del coeficiente de correlación $r$ de Pearson.

El coeficiente $r$ de Pearson es tal que $-1 \leq r \leq 1$ en donde:

* $r = -1$ indica relación lineal perfecta e inversa, es decir, el aumento de una variable implica la disminución de la otra.
* $r = 1$ indica relación lineal perfecta directa, esto es, el aumento de una variable implica el aumento de la otra.
* $r = 0$ indica ausencia de relación lineal entre las variables.

Una clasificación general basada en el valor absoluto es la siguiente:

* **0,00 a menos de 0,10:** Correlación nula o muy débil (sin relación lineal significativa).
* **0,10 a menos de 0,30:** Correlación débil (baja).
* **0,30 a menos de 0,50:** Correlación moderada (media).
* **0,50 a 1,00:** Correlación fuerte (alta).

```r
cor(base_creles$muac, base_creles$imc, method = "pearson")
## [1] 0.7302046

```

## Coeficiente de determinación

El $R^2$ o coeficiente de determinación del modelo resulta de elevar al cuadrado el coeficiente de correlación de Pearson.

Representa el porcentaje de variabilidad de la variable respuesta que es explicado por las variables predictoras.

Entre más cercano a 1 (100%) se encuentre el $R^2$, mejor es el ajuste del modelo.

```r
r2 <- cor(x = base_creles$muac, y = base_creles$imc)^2; r2
## [1] 0.5331987

```

O bien,

```r
summary(mod_creles)$r.squared
## [1] 0.5331987

```

**Interpretación:** 53,32% de la variabilidad en el índice de masa corporal es explicado por la variabilidad en la circunferencia del brazo.

La función `summary()` permite obtener un resumen de la estimación del modelo.

```r
summary(mod_creles)
## 
## Call:
## lm(formula = imc ~ muac, data = base_creles)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -6.4793 -1.7885  0.0207  1.6823  5.9915 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)  4.62375    2.86887   1.612    0.114    
## muac         0.73539    0.09932   7.405 1.77e-09 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.534 on 48 degrees of freedom
## Multiple R-squared:  0.5332, Adjusted R-squared:  0.5235 
## F-statistic: 54.83 on 1 and 48 DF,  p-value: 1.768e-09

```

## Recta de regresión

Una manera de representarla gráficamente es con la función `visreg()` del paquete `visreg`.

```r
#install.packages("visreg")
visreg::visreg(mod_creles)

```

Otra forma es utilizar la opción `geom_smooth` del paquete `ggplot2`.

```r
library(ggplot2)
gr <- ggplot(data = base_creles, aes(x = muac, y = imc)) +
      geom_point()
gr  

```

Puede trazarse la línea de regresión en el diagrama de dispersión:

```r
ggplot(data = base_creles, aes(x = muac, y = imc)) +
  geom_point() +
  geom_smooth(method = lm) # adjunta la línea de regresión, IC 95% 

```

## Coeficientes de regresión

Puede obtenerse cada coeficiente de regresión por medio de la instrucción `modelo$coef[1]` y `modelo$coef[2]`, donde la palabra `modelo` hace referencia al nombre del modelo de regresión:

```r
mod_creles$coef[1]
## (Intercept) 
##    4.623752

```

```r
mod_creles$coef[2]
##     muac 
## 0.735389

```

## Evaluación del modelo: Error estándar de estimación

```r
summary(mod_creles)$sigma
## [1] 2.534439

```

## Inferencias sobre los coeficientes de regresión

Determine la significancia del modelo de regresión que plantea la relación entre la circunferencia del brazo y el índice de masa corporal.

* $H_0: b = 0$: La pendiente de la recta de regresión real es cero. No existe relación lineal entre la circunferencia del brazo y el índice de masa corporal.
* $H_1: b \neq 0$: La pendiente de la recta de regresión real es significativamente distinta de cero. Existe relación lineal entre la circunferencia del brazo y el índice de masa corporal.

### Valor $p$ para los coeficientes del modelo

La posición 7 nos brinda el valor $p$ para la estimación de $a$ y la posición 8 se refiere al valor $p$ de la estimación de $b$.

```r
coef(summary(mod_creles))[c(7,8)]
## [1] 1.135841e-01 1.767958e-09

```

Como $0,0000 < 0,05$, se rechaza la hipótesis nula, es decir, hay evidencias, al nivel del 5%, para indicar que existe relación lineal significativa entre la circunferencia del brazo y el IMC.

### Intervalo de confianza para los coeficientes

En R pueden obtenerse directamente con la función `confint()`.

```r
confint(mod_creles, level = 0.95)
##                  2.5 %     97.5 %
## (Intercept) -1.1444896 10.3919943
## muac         0.5357014  0.9350766

```

## Supuestos del modelo

### Normalidad de residuos

Los residuos se distribuyen de manera normal con media $0$ y varianza $\sigma^2$, esto es:

$$\epsilon \sim N(0, \sigma^2)$$

Para corroborar este supuesto puede utilizarse la prueba de normalidad Shapiro-Wilk.

* $H_0$: Los residuos se distribuyen de manera normal.
* $H_1$: Los residuos no se distribuyen de manera normal.

```r
shapiro.test(mod_creles$residuals)
## 
##  Shapiro-Wilk normality test
## 
## data:  mod_creles$residuals
## W = 0.98702, p-value = 0.8537

```

Como $0,8537 > 0,05$ no se rechaza la hipótesis nula. Puede concluirse que no existen evidencias, al nivel del 5%, para indicar que los residuos no se distribuyen de manera normal.

### Varianza constante

* $H_0$: La varianza de los residuos es constante.
* $H_1$: La varianza de los residuos no es constante.

Este contraste puede realizarse en R mediante el uso de la función `ncvTest()` (*non constant variance Test*) del paquete `car`.

```r
#install.packages("car")
car::ncvTest(mod_creles)
## Non-constant Variance Score Test 
## Variance formula: ~ fitted.values 
## Chisquare = 0.2807537, Df = 1, p = 0.59621

```

Como $0,5962 > 0,05$ no se rechaza la hipótesis nula. No existe evidencia, al nivel del 5%, para indicar que la varianza de los residuos no es constante.

### Otros supuestos del modelo

* El número de observaciones $n$ debe ser mayor que el número de parámetros por estimar.
* Variabilidad en los valores de $X$, es decir, no todos los valores de $X$ en una muestra deben ser iguales.
* El modelo de regresión está correctamente especificado, es decir, que los datos se ajustan para trabajar un modelo lineal.

## Uso del modelo para nuevas predicciones

Una vez aceptado el modelo, pueden realizarse predicciones de valores para nuevas observaciones con ayuda de la función `predict()`.

Para predecir el valor promedio del `imc` para personas con una medida de la circunferencia del brazo de $27\text{ cm}$:

```r
predict(mod_creles, data.frame(muac = 27))
##        1 
## 24.47925

```

Se espera que, en promedio, una persona con una circunferencia del brazo de $27\text{ cm}$ presente un índice de masa corporal de $24,48\text{ kg/m}^2$.

### Intervalo de predicción

```r
predict(mod_creles, 
        data.frame(muac = 27), 
        interval = "prediction")
##        fit      lwr      upr
## 1 24.47925 19.32205 29.63646

```

Con un nivel de confianza de 95%, el verdadero índice de masa corporal para una circunferencia del brazo de $27\text{ cm}$ se encuentra entre $19,32$ y $29,64\text{ kg/m}^2$.

```
