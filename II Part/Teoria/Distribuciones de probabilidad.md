# Distribuciones de probabilidad

# Variables aleatorias

## Definición de Variable Aleatoria
Una variable aleatoria constituye una función que asigna a cada resultado del espacio muestral un número real.

$$X: S \rightarrow \mathbb{R}$$

### Ejemplo 1
> Considere el experimento de lanzar al aire una moneda y observar la cara superior cuando cae al suelo.

$S = \{e, c\}$, con $s_1 = e$, $s_2 = c$.

Sea $X$: Número de escudos que se observa en la cara superior, cuando la moneda cae al suelo. Los valores que puede tomar $X$ pueden definirse de la siguiente manera:

- $X(s_1) = 1$: Valor numérico de observar un escudo en la cara superior, cuando la moneda cae al suelo.
- $X(s_2) = 0$: Valor numérico de NO observar escudo en la cara superior, cuando la moneda cae al suelo.

### Ejemplo 2
> Considere el experimento de lanzar al aire un par de dados y observar las caras superiores cuando caen al suelo.

$$S = \{(1,1), (1,2), ..., (6,6)\}$$

Sea $X$: Asignar a cada punto $(m,n)$ de $S$ la suma de los puntos numéricos que se obtienen en las caras de los dados.

- $X(1,1) = 2$: Valor numérico de observar un 1 en la cara superior de cada dado.
- $X(1,2) = 3$: Valor numérico de observar un 1 en la cara superior del primer dado y un 2 en la cara superior del segundo dado.
- $X(2,1) = 3$: Valor numérico de observar un 2 en la cara superior del primer dado y un 1 en la cara superior del segundo dado.
- $\vdots$
- $X(6,6) = 12$: Valor numérico de observar un 6 en la cara superior del primer dado y un 6 en la cara superior del segundo dado.

### Ejemplo 3
> Considere el experimento de examinar botellas plásticas en una línea de producción hasta encontrar una botella defectuosa.

$$S = \{D, ND, NND, NNND, \ldots\}$$

$X$: Asignar a cada punto de $S$ el número de la inspección donde se detecta una botella defectuosa.

- $X(D) = 1$: Valor numérico de observar una botella defectuosa en la 1era inspección.
- $X(ND) = 2$: Valor numérico de observar una botella defectuosa en la 2nda inspección.
- $X(NND) = 3$: Valor numérico de observar una botella defectuosa en la 3ra inspección.
- $\vdots$
- $X(NNN...D) = n$: Valor numérico de observar una botella defectuosa en la n-ésima inspección.

## Tipos de variables aleatorias
Las variables aleatorias se clasifican en:
- Discretas
- Continuas

### Variables aleatorias discretas
Una **variable aleatoria discreta** es aquella cuyo conjunto de resultados es un conjunto finito o infinito contable de valores posibles.

> **Nota:** se dice que un conjunto $A$ es finito si es vacío o se compone de exactamente $n$ elementos, $n \in \mathbb{Z}^+$. Cualquier otro conjunto es infinito. Por ejemplo: el conjunto $A = \{1,2,3,4\}$ es un conjunto finito, mientras que el conjunto $\mathbb{N} = \{1,2,3,4,...\}$ es un conjunto infinito contable.

## Distribución de probabilidad de una variable discreta

### Función de densidad de probabilidad
Sea $X$ una variable aleatoria discreta, se llama función de densidad de probabilidad de $X$ a la función denotada por $f$ y definida por:

$$f(x) = P(X = x)$$

para todo número real $x$. La función de densidad de probabilidad consiste en asignar a cada resultado posible de $X$ su respectiva probabilidad de ocurrencia.

> La función de densidad de probabilidad también se conoce con el nombre de **distribución de probabilidad de $X$**. En el caso de variables aleatorias discretas, también se conoce como **función de probabilidad de masa**, la cual se denota por $f(x)$ o $p(x)$:
> $$f(x) = p(x) = P(X = x)$$
> Las variables de los ejemplos 1, 2 y 3 definidas anteriormente son ejemplos de variables aleatorias discretas.

### Condiciones
Si $f(x)$ es la función de probabilidad de masa de una variable aleatoria discreta $X$, entonces:
- $f(x) \geq 0, \; \forall x$
- $\displaystyle\sum_{\forall x} f(x) = 1$

### Ejemplo 4
> Considere el experimento de lanzar al aire una moneda en tres ocasiones consecutivas y observar su cara superior cuando cae al suelo. Además, sea $X$ la variable que asigna el número de coronas obtenidas durante los tres lanzamientos. Construya una distribución de probabilidad para este ejemplo.

**Solución:**

El espacio muestral del experimento está dado por:
$$S = \{eee, eec, ece, cee, ecc, cec, cce, ccc\}$$

$X$: la variable que asigna el número de coronas obtenidas durante los tres lanzamientos.
$P(X = x)$: la probabilidad de obtener $x$ número de coronas durante los tres lanzamientos. Los valores que puede tomar $X$ son: $x = 0, 1, 2, 3$.

La probabilidad asociada a cada valor de $x$ es:

| $x$ | $f(x)$ |
|:---:|:---:|
| 0 | $1/8$ |
| 1 | $3/8$ |
| 2 | $3/8$ |
| 3 | $1/8$ |

Finalmente, la distribución de probabilidad o función de probabilidad de masa de la variable $X$ es:

$$f(x) = \begin{cases} 1/8 & \text{si } x = 0 \\ 3/8 & \text{si } x = 1 \\ 3/8 & \text{si } x = 2 \\ 1/8 & \text{si } x = 3 \\ 0 & \text{en otro caso} \end{cases}$$

O bien:

$$f(x) = \begin{cases} 0,125 & \text{si } x = 0 \\ 0,375 & \text{si } x = 1 \\ 0,375 & \text{si } x = 2 \\ 0,125 & \text{si } x = 3 \\ 0 & \text{en otro caso} \end{cases}$$

## Representación gráfica
En el caso de variables aleatorias discretas, su función de probabilidad de masa puede representarse con una **gráfica de bastones o de barras verticales**.

### Ejemplo 5
> Represente gráficamente la distribución de probabilidad de la variable aleatoria del Ejemplo 4.

*(Gráfico de bastones/barras verticales con $f(x)$ en el eje vertical y $x = 0,1,2,3$ en el eje horizontal, alcanzando 0,375 en $x=1$ y $x=2$, y 0,125 en $x=0$ y $x=3$.)*

### Ejemplo 6
> Represente gráficamente la distribución de una variable aleatoria $X$ tal que $f(1) = 0,1$, $f(2) = 0,22$, $f(3) = 0,2$, $f(4) = 0,12$, $f(5) = 0,2$ y $f(6) = 0,16$.

## Distribución acumulada

Sea $(S, \mathcal{F}, P)$ un espacio de probabilidad y $X: S \to \mathbb{R}$ una variable aleatoria. Se llama **función de distribución acumulada** de la variable aleatoria $X$ a la función $F$ definida por:

$$F(X = x) = P(\{S : X(S) \leq x\}) = P(X \leq x)$$

> En algunas ocasiones, para resaltar que $F$ es la función de distribución acumulada de $X$, se escribe $F_X$ en lugar de $F$.

### Caso discreto
Sea $X$ una variable aleatoria discreta. La función de distribución acumulada de $X$ se denota por $F(x)$ y se define por:

$$F(x) = F(X = x) = P(X \leq x)$$

Para un número real $x_0$, la expresión $F(x_0) = P(X \leq x_0)$ consiste en la suma de todos los valores $f(x)$ para los cuales $x \leq x_0$. Es decir,

$$F(x_0) = F(X = x_0) = \sum_{x \leq x_0} f(x)$$

### Ejemplo 7 (repuestos defectuosos)
> Sea $X$: el número de repuestos defectuosos de un lote seleccionado al azar. Determine la función de distribución acumulada $F(x)$.

**Solución:**

Para hallar $F(x)$ es importante conocer la función $f(x)$. Los valores que puede tomar $X$ son $0, 1, 2, 3$ y la probabilidad de $x$ viene dada por:

$$f(0) = P(X=0) = \frac{2}{8} = 0,250$$
$$f(1) = P(X=1) = \frac{3}{8} = 0,375$$
$$f(2) = P(X=2) = \frac{1}{8} = 0,125$$
$$f(3) = P(X=3) = \frac{2}{8} = 0,250$$

Los valores de la función acumulada $F(x)$ para la variable $X$ corresponden a:

$$F(0) = P(X \leq 0) = P(X=0) = f(0)$$
$$F(1) = P(X \leq 1) = f(0) + f(1)$$
$$F(2) = P(X \leq 2) = f(0) + f(1) + f(2)$$
$$F(3) = P(X \leq 3) = f(0) + f(1) + f(2) + f(3)$$

Es decir:

| $x$ | $f(x)$ | $F(x)$ |
|:---:|:---:|:---:|
| 0 | $2/8$ | $2/8$ |
| 1 | $3/8$ | $5/8$ |
| 2 | $1/8$ | $6/8$ |
| 3 | $2/8$ | $1$ |

O bien:

$$F(x) = \begin{cases} 0,000 & \text{si } x < 0 \\ 0,250 & \text{si } 0 \leq x < 1 \\ 0,625 & \text{si } 1 \leq x < 2 \\ 0,750 & \text{si } 2 \leq x < 3 \\ 1,000 & \text{si } x \geq 3 \end{cases}$$

### Probabilidad en un intervalo
En general, para una variable aleatoria discreta con función de probabilidad acumulada $F(x)$, para cualesquiera dos números reales $a$ y $b$ con $a \leq b$ se tiene que:

$$P(a \leq X \leq b) = F(b) - F(a^-)$$

donde $a^-$ representa el valor máximo posible de $X$ que sea estrictamente menor que $a$.

### Ejemplo 8
> Si $F(1) = 0,65$, $F(2) = 0,73$, $F(3) = 0,85$, $F(4) = 0,91$, $F(5) = 0,96$ y $F(6) = 1$, entonces calcule: $P(2 \leq X \leq 5)$; $P(X = 3)$; $P(1 < X \leq 4)$.

**Solución:**

$$P(2 \leq X \leq 5) = F(5) - F(1) = 0,96 - 0,65 = 0,31$$
$$P(X = 3) = F(3) - F(2) = 0,85 - 0,73 = 0,12$$
$$P(1 < X \leq 4) = F(4) - F(1) = 0,91 - 0,65 = 0,26$$

## Valor esperado

Sea $X$ una v.a.d. que toma los valores $x_1, x_2, \ldots, x_i, \ldots$ con probabilidades $f(x_1), f(x_2), \ldots, f(x_i), \ldots$. La media o **valor esperado** de $X$, denotado por $E(X)$ o por $\mu_X$, se define como:

$$\mu_X = E(X) = \sum_{i} x_i \cdot f(x_i)$$

o bien, se puede escribir solo como:

$$\mu_X = E(X) = \sum_{R_X} x \cdot f(x)$$

> El valor esperado existe, siempre y cuando la serie converja absolutamente; caso contrario se dice que la media no existe.

## Variancia

Sea $X$ una v.a.d. con valores $x_1, x_2, \ldots, x_i, \ldots$. La **variancia** de $X$, denotada por $Var(X)$, $V(X)$ o $\sigma_X^2$, se define como:

$$\sigma_X^2 = Var(X) = E([X - E(X)]^2)$$

También puede expresarse como:

$$Var(X) = \sum_{R_X} (x - \mu_X)^2 \cdot f(x)$$

> Válido siempre que la serie sea convergente cuando los valores de $X$ constituyan un conjunto infinito numerable.

### Fórmula alternativa (fórmula abreviada)
Sea $X$ una v.a. Si $Var(X)$ existe, entonces:

$$Var(X) = E(X^2) - [E(X)]^2$$

Es decir,

$$Var(X) = \sum_{\forall x} x^2 f(x) - [E(X)]^2 = \sum_{\forall x} x^2 f(x) - \left(\sum_{\forall x} x f(x)\right)^2$$

> Esta forma resulta más práctica para el cálculo, ya que evita trabajar directamente con las desviaciones respecto a la media.

## Desviación estándar

A la raíz cuadrada positiva de la variancia se le conoce como **desviación estándar** y se denota por $\sigma_X$, es decir:

$$\sigma_X = \sqrt{Var(X)}$$

---

# Distribuciones de probabilidad de variables aleatorias discretas

Algunas distribuciones específicas de probabilidad para variables discretas son:
- Distribución Uniforme discreta
- Distribución de Bernoulli
- Distribución Binomial
- Distribución de Poisson
- Distribución Hipergeométrica
- Distribución Geométrica

## Distribución Uniforme discreta
Una variable aleatoria discreta $X$ tiene una **distribución uniforme**, si todos los valores de $X$ presentan la misma probabilidad de ocurrencia.

Su función de probabilidad de masa está dada por:

$$f(x) = \begin{cases} \dfrac{1}{n} & \text{si } x = 1, 2, ..., n \\ 0 & \text{en otro caso} \end{cases}$$

### Ejemplo
> El lanzamiento de un dado balanceado constituye un ejemplo de variable aleatoria discreta con distribución uniforme.

$$f(x) = \begin{cases} \dfrac{1}{6} & \text{si } x = 1, 2, ..., 6 \\ 0 & \text{en otro caso} \end{cases}$$

*(Gráfico de bastones: todos los valores $x = 1, 2, 3, 4, 5, 6$ con altura constante $f(x) = 0,167$.)*

## Distribución Binomial

Un **experimento binomial** es aquel que cumple con las siguientes características:
- Consta de $n$ pruebas idénticas.
- Cada prueba consta de dos resultados posibles, llamados éxito y fracaso.
- La probabilidad de tener éxito en una sola prueba es igual a $p$ y se mantiene constante para cada prueba o ensayo. Por su parte, la probabilidad de fracaso es igual a $1-p$ o bien $q = 1-p$.
- Las pruebas son independientes, lo que significa que el resultado de una prueba no incide en el resultado de otra.

Con base en las características anteriores, cuando se aplica la distribución binomial se tiene que:
- $X$: Variable en estudio.
- $x$: número de éxitos en la muestra.
- $n$: número de ensayos o pruebas.
- $p$: Probabilidad de éxito.
- $1-p$: Probabilidad de fracaso.

### Función de probabilidad de masa
Una variable aleatoria $X$ tiene distribución binomial con parámetros $n$ y $p$ si su función de probabilidad de masa está dada por:

$$f(x/n,p) = \begin{cases} \binom{n}{x} p^x (1-p)^{n-x} & \text{si } 0 \leq x \leq n \\ 0 & \text{en otro caso} \end{cases}$$

Si una variable aleatoria $X$ tiene distribución binomial con parámetros $n$ y $p$, entonces se denota por $X \sim B(n,p)$.

### Función de probabilidad acumulada

$$F(x) = \begin{cases} 0 & \text{si } x < 0 \\ \displaystyle\sum_{x} \binom{n}{x} p^x (1-p)^{n-x} & \text{si } 0 \leq x \leq n \\ 1 & \text{si } x > n \end{cases}$$

### Valor esperado, varianza y desviación estándar

> **Teorema:** Si $X$ es una variable aleatoria con distribución de probabilidad binomial, su promedio (o valor esperado), varianza y desviación estándar están dados, respectivamente, por:

$$E(X) = \mu = np$$
$$Var(X) = \sigma^2 = np(1-p)$$
$$sd(X) = \sqrt{\sigma^2} = \sqrt{np(1-p)}$$

### Funciones en R
- `pbinom(q, size, prob)` para probabilidad acumulada.
- `dbinom(x, size, prob)` para probabilidad puntual.

```r
pbinom(12, 16, 0.7)  # probabilidad acumulada en x = 12
## [1] 0.7541441
```

### Ejemplo (vacunación)
> Considere que a mayo de 2022 el 85,5 % de las personas en Costa Rica cuentan con la primera dosis de la vacuna contra la COVID-19. Suponga que se seleccionan 25 personas, encuentre la probabilidad de que las personas que cuentan con la primera dosis de la vacuna sean:
> a. exactamente 18
> b. 20 o más pero menos de 23.
> c. menos de 4.
> d. más de 5.
> e. 5 personas no cuenten con la primera dosis.
> f. Determine el valor esperado y la desviación estándar de que las personas cuenten con la primera dosis de la vacuna.

**Solución:**

Sea $X$: el número de personas que cuentan con la primera dosis de la vacuna.

```r
n <- 25; p <- 0.855
```

**a) Exactamente 18**

$$P(X=18/25, 0,855) = P(X=18) = \binom{25}{18} 0,855^{18}(1-0,855)^{25-18} = 0,0386$$

```r
dbinom(x = 18, size = 25, p = 0.855)
## [1] 0.03862248
```

O bien, $P(X=18) = F(18) - F(17)$:

```r
pbinom(18, 25, 0.855) - pbinom(17, 25, 0.855)
## [1] 0.03862248
```

**b) 20 o más pero menos de 23**

$$P(20 \leq X < 23) = F(22) - F(19)$$

```r
pbinom(22, 25, 0.855) - pbinom(19, 25, 0.855)
## [1] 0.5802025
```

O bien, $P(20 \leq X < 23) = P(X=20)+P(X=21)+P(X=22)$:

```r
dbinom(20, 25, 0.855) + dbinom(21, 25, 0.855) + dbinom(22, 25, 0.855)
## [1] 0.5802025
```

**c) Menos de 4**

$$P(X<4) = F(3)$$

```r
pbinom(3, 25, 0.855)
## [1] 5.216246e-16
```

**d) Más de 5**

$$P(X>5) = P(X=6)+P(X=7)+\cdots = 1 - F(5)$$

```r
1 - pbinom(5, 25, 0.855)
## [1] 1
```

**e) 5 personas no cuenten con la primera dosis**

En este caso $n = 25$ y $p = 0,145$ (probabilidad complementaria):

$$P(X=5) = F(5) - F(4)$$

```r
dbinom(5, 25, 0.145)
## [1] 0.1484233
```

**f) Valor esperado y desviación estándar**

Valor esperado:
$$E(X) = np = 25 \cdot 0,855 = 21,4$$

De cada 25 personas, aproximadamente 21 cuentan con la primera dosis de la vacuna contra la COVID-19.

Desviación estándar:
$$sd(X) = \sqrt{np(1-p)} = \sqrt{25 \cdot 0,855 \cdot 0,145} \approx \sqrt{3,1}$$

### Ejemplo (uso de Internet)
> Considere que un estudio sobre el uso del Internet indica que 55 % de las personas lo utilizan para recreación. Si se toma una muestra aleatoria de 50 personas (con reemplazo), determine la probabilidad de que:
> a) a lo sumo la mitad utilicen el Internet para recreación.
> b) exactamente trece utilicen el Internet para recreación.
> c) al menos 20 utilicen el Internet para recreación.
> d) exactamente, el 20 % de las personas no utilicen el Internet para recreación.

### Ejemplo (baloncesto)
> Una persona que juega Baloncesto hace 10 intentos al canasto desde el tiro libre en forma independiente con una efectividad desde el tiro libre de 60 %.
> a. ¿Cuál es la probabilidad que enceste exactamente ocho veces?
> b. ¿Cuál es la probabilidad que enceste al menos cinco veces?
> c. ¿Cuál es la probabilidad que no enceste más de cuatro veces?

## Distribución de Poisson

Una variable aleatoria $X$ tiene distribución de Poisson con parámetro $\lambda$ si su función de probabilidad de masa está dada por:

$$f(x/\lambda) = \begin{cases} \dfrac{\lambda^x e^{-\lambda}}{x!} & \text{si } x = 0, 1, 2, ... \\ 0 & \text{en otro caso} \end{cases}$$

donde $e = 2,71828\ldots$ y $\lambda = n \cdot p$ (promedio), $\lambda > 0$.

### Función de probabilidad acumulada

$$F(x) = \sum_{x} f(x/\lambda) = \sum_{x} \frac{\lambda^x e^{-\lambda}}{x!}$$

> La distribución de Poisson se aplica a varios fenómenos discretos de la naturaleza (esto es, aquellos fenómenos que ocurren $0,1,2,3,\ldots$ veces durante un periodo definido de tiempo o en un área determinada).

### Ejemplos de procesos de Poisson
- El número de errores de ortografía que se cometen al escribir una página.
- El número de llamadas telefónicas en una central telefónica por minuto.
- El número de servidores web accedidos por minuto.
- El número de personas atendidas en una oficina bancaria en una hora.

### Valor esperado y varianza

> **Teorema:** Si $X$ es una variable aleatoria que tiene distribución de Poisson con parámetro $\lambda$, entonces:

$$E(X) = Var(X) = \lambda$$

### Funciones en R
- `ppois(q, lambda)` para probabilidad acumulada.
- `dpois(x, lambda)` para probabilidad puntual.

```r
# Probabilidad puntual: P(X = 1 / λ = 4)
dpois(1, 4)
## [1] 0.07326256

# Probabilidad acumulada: F(X = 1 / λ = 4)
ppois(1, 4)
## [1] 0.09157819
```

### Ejemplo (reclamos de seguros)
> El número promedio de reclamos presentados a una compañía de seguros por daños sufridos en vehículos es de 2 por hora. Calcule la probabilidad que se presenten:
> a) exactamente 3 reclamos en 1 hora.
> b) 2 o 6 reclamos en 4 horas.
> c) al menos 4 reclamos en 3 horas.
> d) más de 7 pero menos de 14 reclamos en 6 horas.
> e) a lo sumo 2 reclamos en 45 minutos.

**Solución:**

Sea $X$: el número de reclamos presentados a una compañía de seguros por daños sufridos en vehículos.

**a) Exactamente 3 reclamos en 1 hora**

$$\lambda = 2 \cdot 1 = 2$$
$$P(X=3/\lambda=2) = \frac{2^3 e^{-2}}{3!}$$

**b) 2 o 6 reclamos en 4 horas**

$$\lambda = 2 \cdot 4 = 8$$
$$P(X=2 \text{ ó } X=6/\lambda=8) = P(X=2) + P(X=6) = 0,0107 + 0,1221 = 0,1329$$

**c) Al menos 4 reclamos en 3 horas**

$$\lambda = 2 \cdot 3 = 6$$
$$P(X \geq 4/\lambda=6) = P(X=4)+P(X=5)+\cdots$$
$$= 1 - (P(X=0)+P(X=1)+P(X=2)+P(X=3))$$
$$= 1 - F(3) = 0,8488$$

**d) Más de 7 pero menos de 14 reclamos en 6 horas**

$$\lambda = 2 \cdot 6 = 12$$
$$P(7 < X < 14/\lambda=12) = P(X=8)+P(X=9)+\cdots+P(X=13)$$
$$= F(13) - F(7)$$

**e) A lo sumo 2 reclamos en 45 minutos**

$$\lambda = 2 \cdot \frac{45}{60} = 1,5$$
$$P(X \leq 2/\lambda=1,5) = P(X=0)+P(X=1)+P(X=2) = F(2)$$

### Ejemplo (consulta externa de hospital)
> Se ha mencionado que en la consulta externa de un Hospital se atienden, en promedio, 3 personas por hora. Suponiendo que el número de personas atendidas en la consulta externa del hospital sigue una distribución de Poisson, determine la probabilidad de que se atiendan:
> a) exactamente 5 personas en una hora.
> b) a lo sumo 4 personas en dos horas.
> c) más de 3 pero menos de 7 en tres horas.
> d) 2 ó 3 personas en media hora.

### Ejemplo (bacterias en muestras de agua)
> Considere que el número de bacterias en muestras de 100 ml de agua en un cierto río sigue una distribución de Poisson con promedio de 5 bacterias por cada 100 ml de agua.
> a) Si se selecciona una muestra al azar. ¿Cuál es la probabilidad de obtener más de 4 bacterias?
> b) Si se selecciona al azar 10 muestras de agua de 100 ml. ¿Cuál es la probabilidad de que exactamente 3 muestras tengan un número de bacterias mayor a 4?
> c) Si se selecciona al azar 7 muestras de agua de 100 ml. ¿Cuál es la probabilidad de que a lo sumo 5 muestras tengan un número de bacterias mayor a 4?
