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

# Variables aleatorias continuas

## Definición
Se dice que una variable $X$ es **continua** si su conjunto de posibles valores es un intervalo de números, esto es, si dados $a$ y $b$, $a < b$, cualquier número $x$, $a \leq x \leq b$ es posible.

### Ejemplos de variables continuas
- La profundidad de un lago.
- La altura de una montaña.
- La longitud de una carretera.

## Función de densidad de probabilidad
La distribución de probabilidad o función de densidad de probabilidad de una v.a. continua $X$, es una función $f(x)$ tal que para todo $a$ y $b$, $a \leq b$ se tiene que:

$$P(a \leq X \leq b) = \int_a^b f(x)\,dx$$

> Esto es, la probabilidad de que $X$ tome un valor en el intervalo $[a,b]$ es el área limitada por la curva de la función $f(x)$ (función de densidad de probabilidad), las rectas $x=a$, $x=b$ y el eje $X$.

### Condiciones
Si $f(x)$ es la función de densidad de probabilidad para una variable aleatoria continua $X$, se tiene que:
- $f(x) \geq 0, \; \forall x$
- $\displaystyle\int_{-\infty}^{+\infty} f(x)\,dx = 1$

## Función acumulada de distribución
Si $X$ es variable aleatoria continua con función de densidad de probabilidad $f(x)$, entonces la función acumulada de distribución de $X$ se denota como $F(x)$ y se define por:

$$F(x) = P(X \leq x) = \int_{-\infty}^{x} f(t)\,dt$$

> Para cada $x$, $F(x)$ representa el área bajo la curva de densidad a la izquierda de $x$.

Si $X$ es una variable aleatoria continua con función de densidad de probabilidad $f(x)$ y función acumulada $F(x)$, entonces para cualesquiera dos valores $a$ y $b$ con $a < b$ tenemos que:

$$P(a \leq X \leq b) = \int_a^b f(x)\,dx$$

### Propiedades
Si $X$ es variable aleatoria continua entonces para cualesquiera valores $a$ y $b$ con $a < b$ se tiene que:

$$P(a \leq X \leq b) = P(a \leq X < b) = P(a < X \leq b) = P(a < X < b) = F(b) - F(a)$$

Además,

$$P(X \leq b) = P(X < b) = F(b)$$
$$P(X \geq b) = P(X > b) = 1 - F(b)$$

## Valor esperado de una v.a. continua
Sea $X$ una variable aleatoria continua con función de densidad de probabilidad $f(x)$. El valor esperado de $X$ se denota por $E(X)$, $\mu_X$ o simplemente $\mu$ y se define por:

$$\mu = E(X) = \int_{-\infty}^{+\infty} x \cdot f(x)\,dx$$

## Varianza de una v.a. continua
Sea $X$ una variable aleatoria continua con función de densidad de probabilidad $f(x)$. La varianza de $X$ se denota por $V(X)$ o $\sigma_X^2$ y se define por:

$$\sigma_X^2 = V(X) = \int_{-\infty}^{+\infty} (x - E(X))^2 \cdot f(x)\,dx$$

## Distribuciones de probabilidad para variables continuas
Algunas distribuciones de probabilidad para variables continuas son:
- Distribución uniforme continua.
- Distribución normal.
- Distribución normal estándar.
- Distribución t–student.
- Distribución chi-cuadrada.

## Distribución normal

Una variable $X$ tiene una distribución normal con parámetros $\mu$ y $\sigma$, donde $\mu \in \mathbb{R}$ y $\sigma > 0$, si su función de densidad está dada por:

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2} \quad \text{si } x \in \mathbb{R}$$

*(Figura 1: curva normal en forma de campana para $\mu = 60$ y $\sigma = 6$, simétrica alrededor de $x=60$.)*

### Características
- Tiene perfil de campana y sus tres medidas principales de posición (media, moda y mediana) son iguales.
- Es simétrica con respecto a su media.
- La curva normal es decreciente uniformemente a partir del valor central.
- El valor central de la curva normal es la media.

### Cálculo de probabilidades
Si $X$ es una variable aleatoria con distribución normal, entonces para cualesquiera $a$ y $b$ con $a < b$, se tiene que:

$$P(a \leq X \leq b) = \int_a^b \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2} dx$$

*(Figura 2: región sombreada representando $P(X \leq 61)$ para $\mu=60$ y $\sigma=6$.)*

$$P(X \leq 61/\mu=60, \sigma=6) = \int_{-\infty}^{61} \frac{1}{6\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-60}{6}\right)^2} dx$$

### Ejemplo 1 (redes sociales)
> El número de horas semanales que las personas dedican a sus redes sociales sigue una distribución normal con promedio 20 horas y desviación estándar 3,5 horas. Si se escoge una persona al azar, ¿cuál es la probabilidad de que su tiempo dedicado a las redes sociales sea:
> a) entre 18 y 23 horas.
> b) al menos 21 horas.
> c) a lo sumo 20 horas.
> d) determine la cantidad de horas dedicadas por el 15 % y el 70 % de las personas.

*(Figura 3: curva normal para $\mu=20$ y $\sigma=3,5$.)*

**a) Entre 18 y 23 horas**

*(Figura 4: región sombreada $P(18 < X < 23)$ dado $\mu=20$ y $\sigma=3,5$.)*

$$P(18 < X < 23/\mu=20,\sigma=3,5) = \int_{18}^{23} \frac{1}{3,5\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-20}{3,5}\right)^2} dx = 0,5204$$

**b) Al menos 21 horas**

$$P(X \geq 21/\mu=20,\sigma=3,5) = 1 - F(21) = 1 - 0,6125 = 0,3875$$

**c) A lo sumo 20 horas**

$$P(X \leq 20/\mu=20,\sigma=3,5) = F(20) = 0,5000$$

**d) Cantidad de horas dedicadas por el 15 % y el 70 % de las personas**

Se piden hallar la región limitada por el cuantil 15 y el 70.

Con R:
```r
qnorm(0.15, 20, 3.5)
## [1] 16.37248
qnorm(0.70, 20, 3.5)
## [1] 21.8354
```

### Ejemplo 1 (usando R)
> Repita el ejemplo anterior utilizando funciones de R.

**a) Entre 18 y 23 horas**

$$P(18 < X < 23/\mu=20,\sigma=3,5) = F(23) - F(18) = 0,8043 - 0,2839 = 0,5204$$

```r
pnorm(23, 20, 3.5) - pnorm(18, 20, 3.5)
## [1] 0.5204624
```

**b) Al menos 21 horas**

$$P(X \geq 21/\mu=20,\sigma=3,5) = 1 - F(21) = 1 - 0,6125 = 0,3875$$

```r
1 - pnorm(21, 20, 3.5)
## [1] 0.3875485
```

**c) A lo sumo 20 horas**

$$P(X \leq 20/\mu=20,\sigma=3,5) = F(20) = 0,5000$$

```r
pnorm(20, 20, 3.5)
## [1] 0.5
```

**d) Cantidad de horas dedicadas por el 15 % y el 70 % de las personas**

```r
qnorm(0.15, 20, 3.5)
## [1] 16.37248
qnorm(0.70, 20, 3.5)
## [1] 21.8354
```

### Ejemplo 2 (colesterol)
> Suponga que el nivel de colesterol total en la sangre de un grupo de personas jóvenes sigue una distribución normal con promedio de 190 mg/dl con desviación estándar de 19 mg/dl. Con base en dicha información calcule:
> a) ¿qué porcentaje de personas tienen un nivel de colesterol total menor a 200 mg/dl?
> b) ¿cuál es la probabilidad que una persona joven elegida al azar presente un nivel de colesterol total entre 175 y 200 mg/dl?
> c) Determine el nivel de colesterol total mínimo del 30 % de las personas con el nivel de colesterol más alto.
> d) Si se tienen 200 personas jóvenes, ¿cuántas tendrán un nivel de colesterol total superior a 220 mg/dl?
> e) Determine el nivel de colesterol total máximo del 40 % de las personas con el nivel de colesterol más bajo.
> f) Determine los niveles de colesterol total que presenta el 40 % central de las personas.

**a) Porcentaje con colesterol menor a 200 mg/dl**

Debe hallarse $P(X < 200/\mu=190,\sigma=19) = F(200)$

```r
pnorm(200, 190, 19)
## [1] 0.7006656
```

**b) Probabilidad entre 175 y 200 mg/dl**

Debe hallarse $P(175 < X < 200/\mu=190,\sigma=19) = F(200) - F(175)$

$$P(175 < X < 200/\mu=190,\sigma=19) = 0,7007 - 0,2149$$

**c) Nivel mínimo del 30 % con colesterol más alto**

```r
qnorm(0.70, 190, 19)
## [1] 199.9636
```

**d) Cantidad de personas con colesterol superior a 220 mg/dl (de 200 personas)**

Primero se obtiene $P(X > 220/\mu=190,\sigma=19) = 1 - F(220)$.

Luego, para obtener la cantidad de personas se multiplica el total de personas por la probabilidad de que se cumpla la característica:

```r
N <- 200; cantidad <- 200 * 0.0571
cantidad
## [1] 11.42
```

## Distribución normal estándar

Una variable aleatoria $X$ tiene una distribución normal estándar si $\mu = 0$ y $\sigma = 1$.

Si una variable $X$ tiene una distribución normal con parámetros $\mu$ y $\sigma$, entonces la variable

$$Z = \frac{X - \mu}{\sigma}$$

es una v.a. con distribución normal estándar.

### Ejemplo (redes sociales, usando estandarización)
> El número de horas semanales que las personas dedican a sus redes sociales sigue una distribución normal con promedio 20 horas y desviación estándar 3,5 horas. Si se escoge una persona al azar, ¿cuál es la probabilidad de que su tiempo dedicado a las redes sociales sea:
> a) entre 18 y 23 horas.
> b) al menos 21 horas.
> c) a lo sumo 20 horas.
> d) determine la cantidad de horas dedicadas por el 15 % y el 70 % de las personas.

**a) Entre 18 y 23 horas**

$$P(18 < X < 23/\mu=20,\sigma=3,5)$$

$$x = 18 \Rightarrow z = \frac{18-20}{3,5} \Rightarrow z = -0,57$$
$$x = 23 \Rightarrow z = \frac{23-20}{3,5} \Rightarrow z = 0,86$$

Así,

$$P(18 < X < 23/\mu=20,\sigma=3,5) = P(-0,57 < Z < 0,86) = F(0,86) - F(-0,57)$$

```r
pnorm(0.86) - pnorm(-0.57)
## [1] 0.5207666
```

**b) Al menos 21 horas**

$$x = 21 \Rightarrow z = \frac{21-20}{3,5} \Rightarrow z = 0,2857 \Rightarrow z = 0,29$$

$$P(X \geq 21/\mu=20,\sigma=3,5) = P(Z \geq 0,29) = 1 - F(0,29)$$

```r
1 - pnorm(0.29)
## [1] 0.3859081
```

**c) A lo sumo 20 horas**

$$x = 20 \Rightarrow z = \frac{20-20}{3,5} \Rightarrow z = 0,00$$

$$P(X \leq 20/\mu=20,\sigma=3,5) = P(Z \leq 0,00) = F(0,00)$$

```r
pnorm(0)
## [1] 0.5
```

**d) Cantidad de horas dedicadas por el 15 % y el 70 % de las personas**

Recordando que $Z = \dfrac{X-\mu}{\sigma}$:

```r
qnorm(0.15)
## [1] -1.036433
```

$$z = -1,04 \Rightarrow -1,03 = \frac{X-20}{3,5} \Rightarrow -1,03 \cdot 3,5 + 20 = X \Rightarrow X = 16,36$$

```r
qnorm(0.70)
## [1] 0.5244005
```

$$z = 0,52 \Rightarrow 0,52 = \frac{X-20}{3,5} \Rightarrow 0,52 \cdot 3,5 + 20 = X \Rightarrow X = 21,82$$

### Ejemplo propuesto (horas de estudio)
> El número de horas semanales que estudia una población de 140 estudiantes de una universidad determinada sigue una distribución normal con promedio 15 horas y desviación estándar 2,5 horas. Si se escoge un estudiante al azar, ¿cuál es la probabilidad de que estudie:
> a) entre 12 y 17 horas.
> b) al menos 14 horas.
> c) a lo sumo 13 horas.
> d) ¿cuántas horas estudia el 50 % central de las personas?

