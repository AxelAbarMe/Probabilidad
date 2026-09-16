# Teoría elemental de probabilidad

# Elementos de probabilidad

## Experimento
Un experimento es un proceso que permite obtener información de un objeto que es sometido a estudio mediante mediciones o conteos.

> Cualquier situación en la que se recolecta un dato, ya sea por medición directa o por conteo, constituye un experimento en el sentido estadístico-probabilístico del término.

### Ejemplos
- Lanzar al aire una moneda y ver la cara superior cuando cae al suelo.
- Medir la temperatura promedio en un día del año en la provincia de Heredia.
- Determinar el porcentaje de artículos defectuosos de un determinado proceso de manufactura.
- Determinar el número de llamadas telefónicas que una oficina de servicio al cliente recibe en un determinado período.
- El número de neumáticos dañados durante un proceso de prueba antes de ser puestos en el mercado.

## Espacio muestral
El espacio muestral de un experimento se denota por $S$ y se define como el conjunto de todos los posibles resultados de un experimento.

> El espacio muestral puede ser **discreto** (finito o infinito numerable) o **continuo**, dependiendo de la naturaleza de la variable que se observe.

### Ejemplos

**Lanzar al aire una moneda y ver la cara superior cuando cae al suelo.**
$$S = \{E, C\}$$

**Medir la temperatura en un día del año en un lugar de Costa Rica, en grados Centígrados.**
$$S = \{t \mid -6 < t < 60\}$$

**Lanzar al aire un dado y ver la cara superior cuando cae al suelo.**
$$S = \{1, 2, 3, 4, 5, 6\}$$

**Determinar el número de llamadas telefónicas que una oficina de servicio al cliente recibe en un determinado período.**
$$S = \{x \mid x \in \mathbb{Z}, 0 < x < 100\}$$

## Eventos
Un evento es cualquier subconjunto de resultados contenidos en el espacio muestral. Los eventos suelen denotarse con letras mayúsculas.

### Tipos de eventos
- Simple
- Compuesto
- Nulo o imposible

#### Evento simple
Se dice que un evento es **simple** si está formado exactamente por un resultado.

#### Evento compuesto
Un evento es **compuesto** si consta de más de un resultado.

#### Evento imposible
Para un espacio muestral $S$, el evento que nunca ocurre se conoce como **evento imposible o nulo** y se denota por $\emptyset$.

### Ejemplo 1
> Considere el experimento de lanzar al aire un dado y observar el número de la cara superior cuando cae al suelo. Defina un evento simple y un evento compuesto.

$$S = \{1, 2, 3, 4, 5, 6\}$$

Un evento simple es observar un número determinado, por ejemplo el número 2, es decir, $E = \{2\}$.
Un evento compuesto estaría dado por observar un número par, es decir, $A = \{2, 4, 6\}$.

### Ejemplo 2
> Considere el experimento de lanzar una moneda al aire, tres veces, y observar la cara superior. Determine el espacio muestral del experimento. Defina un evento simple y un evento compuesto.

**Solución:**
$$S = \{eee, eec, ece, cee, ecc, cec, cce, ccc\}$$

Un evento simple sería observar tres coronas, es decir, $A = \{ccc\}$.
Un evento compuesto sería observar al menos dos coronas, $B = \{ccc, cce, cec, ecc\}$.

## Relaciones entre eventos

### Intersección de eventos
Dados dos eventos $A$ y $B$, la intersección de $A$ y $B$, denotada por $A \cap B$ y que se lee "$A$ y $B$", es el evento formado por todos los resultados que están en $A$ y en $B$.

> Si dos eventos no tienen resultados en común, su intersección es vacía y se dice que los eventos son **mutuamente excluyentes o disyuntos**.

### Unión de eventos
Dados dos eventos $A$ y $B$, la unión de $A$ y $B$, denotada por $A \cup B$ y que se lee "$A$ o $B$", es el evento formado por todos los resultados que están en $A$ o $B$ o en ambos.

### Complemento de un evento
Dado un evento $A$ de un espacio muestral $S$, el complemento de $A$, denotado por $A^C$ o $\overline{A}$, es el evento formado por todos los resultados que están en $S$ y que NO están en $A$.

### Leyes de De Morgan
$$\overline{A \cup B} = \overline{A} \cap \overline{B}$$
$$\overline{A \cap B} = \overline{A} \cup \overline{B}$$

### Ejemplo
> Considere el experimento de lanzar una moneda al aire tres veces y observar la cara superior cuando cae al suelo, y los eventos $A$: se obtienen al menos dos escudos y $B$: obtener una corona. Halle los eventos $A \cup B$, $A \cap B$, $\overline{A}$, $\overline{B}$, $\overline{A} \cup \overline{B}$, $\overline{A} \cap \overline{B}$, $\overline{A \cup B}$ y $\overline{A \cap B}$.

**Solución:**

| Evento | Conjunto |
|:---:|:---|
| $A$ | $\{cee, ece, eec, eee\}$ |
| $B$ | $\{cee, ece, eec\}$ |
| $A \cup B$ | $\{cee, ece, eec, eee\}$ |
| $A \cap B$ | $\{cee, ece, eec\}$ |
| $\overline{A}$ | $\{cce, ecc, cec, ccc\}$ |
| $\overline{B}$ | $\{cce, ecc, cec, ccc, eee\}$ |

## Probabilidad

### Definición clásica (enfoque Laplaciano)
Dado un experimento y un espacio muestral $S$ tal que $S$ contiene $N$ puntos muestrales igualmente posibles y un evento $A$ constituido por $k$ puntos muestrales de $S$, entonces la probabilidad del evento $A$ es el número denotado por $P(A)$ y definido por:

$$P(A) = \frac{k}{N}$$

### Ejemplo 1
> Considere el experimento de lanzar una moneda al aire tres veces y observar la cara superior cuando cae al suelo, halle la probabilidad de obtener: tres coronas, al menos dos escudos, a lo sumo dos coronas.

**Solución:**
$$S = \{eee, eec, ece, cee, ecc, cec, cce, ccc\}$$

- $A$: obtener tres coronas, $A = \{ccc\}$, $P(A) = \dfrac{1}{8}$
- $B$: obtener cuando menos dos escudos, $B = \{eee, eec, ece, cee\}$, $P(B) = \dfrac{4}{8}$
- $C$: obtener a lo sumo dos coronas, $C = \{eee, eec, cee, ece, cce, ecc, cec\}$, $P(C) = \dfrac{7}{8}$

### Ejemplo 2
> Considere el experimento de extraer una carta de una baraja. Halle la probabilidad de obtener un as, una carta de color rojo, un rey de color negro.

**Solución:**
- $A$: extraer un as de una baraja, $P(A) = \dfrac{4}{52}$
- $B$: extraer una carta de color rojo, $P(B) = \dfrac{26}{52}$

### Limitación de la definición clásica
La definición clásica presenta una limitada aplicabilidad, ya que en muchas situaciones de la realidad resulta imposible considerar todas las posibilidades como igualmente probables (por ejemplo, la llegada a tiempo de un avión a la ciudad B cuando vuela desde la ciudad A).

### Definición de probabilidad (enfoque de frecuencias relativas)
De una manera más general, la probabilidad de un evento $A$ puede definirse como la proporción de veces en las que el evento ocurrirá a partir de una corrida prolongada de experimentos repetidos.

$$P(A) = \frac{\text{número de veces en que ocurre } A}{\text{número de veces en que se realiza el experimento}}$$

### Ejemplo
> Existen registros que indican que 185 de 200 vuelos han llegado a tiempo, por lo que si consideramos el evento $A$: el avión llega a tiempo, entonces la probabilidad de $A$ es:

$$P(A) = \frac{185}{200} = 0,925 \; (92,5\%)$$

## Axiomas de probabilidad
- **Axioma 1:** Para cualquier evento $A$, $P(A) \geq 0$.
- **Axioma 2:** $P(S) = 1$.
- **Axioma 3:** Si $A_1, A_2, ..., A_n$ es un conjunto finito de eventos mutuamente excluyentes, entonces
$$P(A_1 \cup A_2 \cup ... \cup A_n) = P(A_1) + P(A_2) + ... + P(A_n)$$

## Teoremas y propiedades

### Teorema 1
Si $E$ es un evento simple de un espacio muestral $S$ con $N$ puntos muestrales igualmente probables, entonces
$$P(E) = \frac{1}{N}$$

### Teorema 2
Dado un espacio muestral $S$ y un evento $A$ de $S$, la probabilidad de $A$ es igual a la suma de las probabilidades de los eventos simples que componen $A$.

### Teorema 3
Dado un espacio muestral $S$ y $A$ un evento de $S$, entonces
$$P(A) = 1 - P(\overline{A})$$

### Teorema 4
Si $A$ y $B$ son eventos cualesquiera de $S$, entonces
$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

### Teorema 5
$$P(\emptyset) = 0$$

### Teorema 6
Si $A$ y $B$ son eventos cualesquiera de un espacio muestral $S$ tal que $A \subseteq B$, entonces $P(A) \leq P(B)$.

## Ejemplo integrador

> Dos personas A y B salen de distintos lugares con destino a la misma casa de estudio. La probabilidad de que la persona A llegue a tiempo es de 0,85, la probabilidad de que la persona B llegue a tiempo es de 0,89 y la probabilidad de que ambas personas lleguen a tiempo es de 0,769. Calcule la probabilidad de que: la persona A o la persona B (o ambas) lleguen a tiempo; al menos una de las dos personas llegue tarde; sólo una persona llegue a tiempo.

**Datos:**
$$P(A) = 0,85 \qquad P(B) = 0,89 \qquad P(A \cap B) = 0,769$$

### a) La persona A o la persona B (o ambas) lleguen a tiempo
$$P(A \cup B) = P(A) + P(B) - P(A \cap B) = 0,85 + 0,89 - 0,769 = 0,971$$

### b) Al menos una de las dos personas llegue tarde
$$P(\overline{A} \cup \overline{B}) = P(\overline{A \cap B}) = 1 - P(A \cap B) = 1 - 0,769 = 0,231$$

**Comprobación alternativa:**
$$P(\overline{A}) = 0,15 \qquad P(\overline{B}) = 0,11 \qquad P(\overline{A} \cap \overline{B}) = 1 - P(A \cup B) = 0,029$$
$$P(\overline{A} \cup \overline{B}) = P(\overline{A}) + P(\overline{B}) - P(\overline{A} \cap \overline{B}) = 0,15 + 0,11 - 0,029 = 0,231$$

### c) Sólo una persona llegue a tiempo
Sea $E$: solo A llega a tiempo, y $F$: solo B llega a tiempo. Entonces:
$$P(\text{solo } A \cup \text{solo } B) = P(E \cup F)$$

Dado que $A = E \cup (A \cap B)$:
$$P(E) = P(A) - P(A \cap B) = 0,85 - 0,769 = 0,081$$
$$P(F) = P(B) - P(A \cap B) = 0,89 - 0,769 = 0,121$$

Por lo tanto:
$$P(\text{solo } A \cup \text{solo } B) = P(E) + P(F) = 0,081 + 0,121 = 0,202$$

---

# Probabilidad condicional

Si $A$ y $B$ son dos eventos de un espacio muestral $S$ tal que $B$ ha ocurrido, es decir, $P(B) > 0$, se llama **probabilidad condicional de $A$ dado $B$** a la probabilidad de ocurrencia del evento $A$ dado que $B$ ha ocurrido, denotada por $P(A/B)$ y definida por:

$$P(A/B) = \frac{P(A \cap B)}{P(B)}$$

De forma análoga, si $A$ y $B$ son dos eventos de un espacio muestral $S$ tal que $A$ ha ocurrido, es decir, $P(A) > 0$, se llama **probabilidad condicional de $B$ dado $A$** a la probabilidad de ocurrencia del evento $B$ dado que $A$ ha ocurrido, denotada por $P(B/A)$ y definida por:

$$P(B/A) = \frac{P(A \cap B)}{P(A)}$$

## Regla de la multiplicación
Si $A$ y $B$ son dos eventos de un espacio muestral $S$ tal que $P(B) \neq 0$, entonces:
$$P(A \cap B) = P(A/B) \cdot P(B)$$

O bien, si $A$ y $B$ son dos eventos de un espacio muestral $S$ tal que $P(A) \neq 0$, entonces:
$$P(A \cap B) = P(B/A) \cdot P(A)$$

> Esta regla, derivada directamente de la definición de probabilidad condicional, permite calcular la probabilidad de la intersección de dos eventos cuando se conoce una probabilidad condicional y la probabilidad del evento condicionante.

### Ejemplo
> Un proceso de manufactura cuenta con una máquina descompuesta. La probabilidad de que Luis la repare es de 0,80, además la probabilidad de que Luis la repare y se descomponga dentro de 5 días es de 0,22. ¿Qué probabilidad existe de que la máquina se descomponga dentro de 5 días dado que Luis fue quién la reparó?

**Solución:**
Sean $A$: Luis repara la máquina, $B$: la máquina se descompone dentro de 5 días y $A \cap B$: Luis repara la máquina y esta se descompone dentro de 5 días.

De acuerdo con los datos: $P(A) = 0,80$, $P(A \cap B) = 0,22$.

La pregunta planteada hace referencia a $P(B/A)$:

$$P(B/A) = \frac{P(A \cap B)}{P(A)} = \frac{0,22}{0,80} = 0,275$$

**Interpretación:** dado que Luis reparó la máquina, existe una probabilidad de 0,275 (27,5 %) de que esta se descomponga dentro de los siguientes 5 días.

## Eventos independientes
Dos eventos $A$ y $B$ son **independientes** si $P(A/B) = P(A)$, o bien, $P(B/A) = P(B)$. De otra manera, se dice que los eventos son **dependientes**.

> Es decir, dos eventos son independientes si la ocurrencia o no ocurrencia de uno de ellos no cambia o afecta la probabilidad de ocurrencia del otro evento.

### Teorema
$A$ y $B$ son eventos independientes si y sólo si
$$P(B/A) = P(B)$$

> Los resultados asociados con el lanzamiento de una moneda dos veces seguidas se consideran eventos independientes, pues el resultado del primer lanzamiento en nada afecta la probabilidad de que el segundo lanzamiento sea escudo o corona.

### Ley multiplicativa de la probabilidad
Si $A_1, A_2, \ldots, A_n$ representan eventos independientes entre sí, entonces:

$$P(A_1 \cap A_2 \cap \cdots \cap A_n) = P(A_1) \cdot P(A_2) \cdots P(A_n)$$

### Ejemplo 1
> Como se mencionó anteriormente, los $n$ lanzamientos al aire de una moneda equilibrada son eventos independientes, por tanto, ¿cuál es la probabilidad de obtener tres coronas en tres lanzamientos de una moneda equilibrada?

**Solución:**
La probabilidad de obtener una corona en el lanzamiento de una moneda equilibrada es de 0,50, por lo tanto, la probabilidad de obtener tres coronas en tres lanzamientos se expresa:

$$P(C_1 \cap C_2 \cap C_3) = P(C_1) \cdot P(C_2) \cdot P(C_3) = \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} = \frac{1}{8}$$

### Ejemplo 2
> Determine la probabilidad de extraer cuatro 5 en cuatro lanzamientos de un dado.

**Solución:**
Como los lanzamientos de un dado son eventos independientes, y $P(5) = \dfrac{1}{6}$ en cada lanzamiento:

$$P(5_1 \cap 5_2 \cap 5_3 \cap 5_4) = \left(\frac{1}{6}\right)^4 = \frac{1}{1296} \approx 0,00077$$

## Probabilidad total

### Teorema
Sean $A_1, A_2, \ldots, A_n$ eventos mutuamente excluyentes de un espacio muestral $S$ tal que $A_1 \cup A_2 \cup ... \cup A_n = S$.

Si $B$ es un evento de $S$, entonces:

$$P(B) = \sum_{i=1}^{n} P(B/A_i) \cdot P(A_i) = P(B/A_1)P(A_1) + P(B/A_2)P(A_2) + \cdots + P(B/A_n)P(A_n)$$

> Este resultado permite calcular la probabilidad de un evento $B$ cuando esta depende de la ocurrencia previa de distintos escenarios o categorías ($A_1, A_2, ..., A_n$) que particionan completamente el espacio muestral.

## Teorema de Bayes

Sean $A_1, A_2, \ldots, A_n$ eventos mutuamente excluyentes de un espacio muestral $S$ tal que $A_1 \cup A_2 \cup ... \cup A_n = S$.

Si $B$ de $S$ es un evento tal que $P(B) \neq 0$, entonces para cualquier evento $A_k$ se tiene que:

$$P(A_k/B) = \frac{P(B/A_k)P(A_k)}{P(B)} = \frac{P(B/A_k)P(A_k)}{\displaystyle\sum_{i=1}^{n} P(B/A_i)P(A_i)}$$

> El Teorema de Bayes permite "invertir" la condicionalidad: a partir de las probabilidades $P(B/A_i)$ (conocidas de antemano) se obtiene $P(A_i/B)$, es decir, se actualiza la probabilidad de una causa dado que se observó un efecto.

### Ejemplo (gasolinera)
> En una gasolinera el 30 % de las personas compran gasolina regular, el 45 % compra gasolina superior y el 25 % compra diésel. De las personas que consumen gasolina regular 3 de cada 10 llenan el tanque, de las que consumen gasolina superior 4 de cada 10 llenan el tanque y de las que consumen diésel 6 de cada 10 llenan el tanque. Si se elige una persona al azar:
> - ¿cuál es la probabilidad que llene el tanque?
> - ¿cuál es la probabilidad que consuma gasolina regular dado que llenó el tanque?
> - ¿cuál es la probabilidad que consuma gasolina regular y llenó el tanque?
> - ¿cuál es la probabilidad que consuma diésel y no llene el tanque?

**Solución:**

Sean $A_1$: la persona consume gasolina regular, $A_2$: la persona consume gasolina superior, $A_3$: la persona consume diésel, $B$: la persona llena el tanque.

| Evento | $P(A_i)$ | $P(B/A_i)$ |
|:---:|:---:|:---:|
| $A_1$ | 0,30 | 0,30 |
| $A_2$ | 0,45 | 0,40 |
| $A_3$ | 0,25 | 0,60 |

**a) ¿Cuál es la probabilidad de que un cliente llene el tanque?**

$$P(B) = P(B/A_1)\cdot P(A_1) + P(B/A_2)\cdot P(A_2) + P(B/A_3)\cdot P(A_3)$$
$$P(B) = 0,30 \cdot 0,30 + 0,45 \cdot 0,40 + 0,25 \cdot 0,60 = 0,4200$$

**b) ¿Cuál es la probabilidad que consuma gasolina regular dado que llenó el tanque?**

$$P(A_1/B) = \frac{P(B/A_1)\cdot P(A_1)}{P(B)} = \frac{0,30 \cdot 0,30}{0,42} = \frac{0,09}{0,42} \approx 0,2143$$

**c) ¿Cuál es la probabilidad que consuma gasolina regular y llenó el tanque?**

$$P(A_1 \cap B) = P(B/A_1) \cdot P(A_1) = 0,30 \cdot 0,30 = 0,09$$

**d) ¿Cuál es la probabilidad que consuma diésel y no llene el tanque?**

Sea $\overline{B}$: la persona no llena el tanque. Debe hallarse $P(A_3 \cap \overline{B})$:

$$P(A_3 \cap \overline{B}) = P(\overline{B}/A_3) \cdot P(A_3)$$
$$P(A_3 \cap \overline{B}) = 0,40 \cdot 0,25 = 0,1000$$

#### Diagrama de árbol

| Rama | $P(A_i)$ | $P(B/A_i)$ | $P(\overline{B}/A_i)$ |
|:---:|:---:|:---:|:---:|
| $A_1$ | 0,30 | 0,30 | 0,70 |
| $A_2$ | 0,45 | 0,40 | 0,60 |
| $A_3$ | 0,25 | 0,60 | 0,40 |

### Ejemplo (vacunación)
> Considere que de un grupo de personas, 55 % cuenta con solo una dosis de la vacuna contra la covid-19, 30 % cuenta con solo dos dosis, 10 % cuenta con solo tres dosis y 5 % cuenta con las cuatro dosis. Además, de las personas que cuentan con solo una dosis de la vacuna, 25 % presenta factores de riesgo, de las que cuentan con solo dos dosis, 35 % presenta factores de riesgo, de las que cuentan con solo tres dosis, 40 % presenta factores de riesgo y de las que cuentan con las cuatro dosis, 55 % presenta factores de riesgo. Si se elige una persona al azar:
> - ¿cuál es la probabilidad de que tenga factores de riesgo?
> - ¿cuál es la probabilidad de que cuente con solo dos dosis si se sabe que presenta factores de riesgo?
> - ¿cuál es la probabilidad de que cuente con las cuatro dosis y tenga factores de riesgo?
> - ¿cuál es la probabilidad de que cuente con solo tres dosis y no tenga factores de riesgo?

## Probabilidad: Ejemplos con tablas de contingencia

### Ejemplo 1: métodos de enseñanza
> Cuatro métodos de enseñanza fueron probados para determinar el rendimiento estudiantil en un curso específico. Se formaron grupos de cincuenta estudiantes con cada método y se tienen los siguientes resultados:

**Tabla 1: Distribución por método y condición de aprobación**

| | M1 | M2 | M3 | M4 | Total |
|:---|:---:|:---:|:---:|:---:|:---:|
| Aprobación | 30 | 42 | 22 | 25 | 119 |
| No aprobación | 20 | 8 | 28 | 25 | 81 |
| **Total** | 50 | 50 | 50 | 50 | 200 |

> Calcule la probabilidad de seleccionar una persona que: esté aprobada; haya recibido el método 1 o esté reprobada; haya recibido el método 3 y esté aprobada; haya aprobado dado que recibió el método 2.

**a) Probabilidad de que la persona esté aprobada**

Sea $A$: la persona aprobó.
$$P(A) = \frac{119}{200}$$

**b) Probabilidad de que haya recibido el método 1 o esté reprobada**

Sean $M1$: la persona recibió el M1, $R$: la persona reprobó.

$$P(M1 \cup R) = P(M1) + P(R) - P(M1 \cap R)$$
$$P(M1 \cup R) = \frac{50}{200} + \frac{81}{200} - \frac{20}{200} = \frac{111}{200}$$

**c) Probabilidad de que haya recibido el método 3 y esté aprobada**

Sean $M3$: la persona recibió el M3 y $A$: la persona aprobó.
$$P(M3 \cap A) = \frac{22}{200}$$

**d) Probabilidad de que haya aprobado dado que recibió el método 2**

Sean $M2$: la persona recibió el M2 y $A$: la persona aprobó.

$$P(A/M2) = \frac{P(A \cap M2)}{P(M2)} = \frac{\frac{42}{200}}{\frac{50}{200}} = \frac{42}{50} = 0,84$$

### Ejemplo 2: escolaridad y colesterol
> A continuación se presenta la distribución de personas por grado de escolaridad según nivel de colesterol total en la sangre.

**Tabla 4: Distribución de personas por grado de escolaridad y nivel de colesterol total**

| | Normal | Alto | Elevado | Total |
|:---|:---:|:---:|:---:|:---:|
| Primaria | 23 | 60 | 29 | 112 |
| Secundaria | 28 | 79 | 60 | 167 |
| Universitaria | 9 | 49 | 63 | 121 |
| **Total** | 60 | 188 | 152 | 400 |

> Si se selecciona una persona al azar, calcule la probabilidad de que: su nivel educativo sea de primaria; su nivel de colesterol sea elevado dado que su grado de escolaridad es secundaria; tenga grado universitario o su nivel de colesterol sea alto o moderado; posea grado de secundaria y nivel de colesterol elevado; posea grado de primaria o no tenga nivel de colesterol elevado.

**a) Probabilidad de que el grado educativo sea de primaria**

Sea $A$: el grado educativo de la persona es de primaria.
$$P(A) = \frac{112}{400}$$

**b) Probabilidad de que el nivel de colesterol sea elevado dado que su grado de escolaridad es secundaria**

Sean $E$: el nivel de colesterol es elevado y $S$: la persona tiene grado educativo de secundaria.

$$P(E/S) = \frac{P(E \cap S)}{P(S)} = \frac{\frac{60}{400}}{\frac{167}{400}} = \frac{60}{167}$$
