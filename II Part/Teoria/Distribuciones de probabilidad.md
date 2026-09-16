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
