# Intervalos de confianza con R
**Autor:** E. A.  
**Fecha:** 2026-10-26  

---

## Estimación por intervalos: para la media (σ conocida)

Cuando la desviación estándar σ se conoce, el intervalo de confianza para la media se estima con la función `z.test(x, sigma.x, conf.level, ...)$conf` del paquete `BSDA`, donde:

* **`x`**: vector de datos.
* **`sigma.x`**: valor de la desviación estándar poblacional.
* **`conf.level`**: nivel de confianza.

### Ejemplo
Considere la base de datos `base_creles` y determine un intervalo de confianza del 95% para estimar el índice de masa corporal promedio real de las personas de 60 años y más. Suponga que para esta variable se conoce que la desviación estándar es de 4 kg/m².

```r
# cargando la base
library(readxl)
base_creles <- read_excel("/Users/eduardo/Documents/trabajo/curso_R/base_creles.xlsx")

# cargando el paquete BSDA
if(!require("BSDA")){
  install.packages("BSDA")
  library("BSDA")
}

z.test(x = base_creles$imc, sigma.x = 4, conf.level = 0.98)$conf

```

**Resultado:**

```text
## [1] 24.38402 27.01598
## attr(,"conf.level")
## [1] 0.98

```

---

## Estimación por intervalos: para la media (σ desconocida y muestra pequeña: n ≤ 30)

Cuando la variable de estudio se distribuye de manera normal, la desviación estándar σ no se conoce y la muestra es pequeña, el intervalo de confianza para la media se estima con la función `t.test(x, conf.level, ...)$conf`, donde:

* **`x`**: vector de datos.
* **`conf.level`**: nivel de confianza.

### Ejemplo

Considere la base de datos `base_creles` y determine un intervalo de confianza del 98% para estimar el peso promedio real de los hombres de 60 años y más. Suponga que la variable peso se distribuye de manera normal.

```r
t.test(x = base_creles$peso[base_creles$sexo == "M"],
       conf.level = 0.98)$conf

```

**Resultado:**

```text
## [1] 64.70725 77.58524
## attr(,"conf.level")
## [1] 0.98

```

Además, si se desea obtener la estimación puntual para la media poblacional puede utilizarse el código `t.test(x, conf.level, ...)$estimate`

### Ejemplo

Considere la base de datos `base_creles` y determine la estimación puntual del peso promedio de los hombres de 60 años y más. Utilice un nivel de confianza de 95%.

```r
t.test(x = base_creles$peso[base_creles$sexo == "M"],
       conf.level = 0.98)$estimate

```

**Resultado:**

```text
## mean of x 
##  71.14625

```

---

## Estimación por intervalos: para la media (σ desconocida y muestra grande: n > 30)

Cuando la variable de estudio se distribuye de manera normal, la desviación estándar σ no se conoce y la muestra es grande, el intervalo de confianza para la media puede estimarse con la función `t.test(x, conf.level, ...)$conf`, ya que cuando n tiende a infinito, la distribución t se asemeja a la distribución normal estándar.

* **`x`**: vector de datos.
* **`conf.level`**: nivel de confianza.

### Ejemplo

Considere la base de datos `base_creles` y determine un intervalo de confianza del 95% para estimar la circunferencia del brazo promedio real de las personas de 60 años y más.

```r
t.test(x = base_creles$muac, conf.level = 0.95)$conf

```

**Resultado:**

```text
## [1] 27.62394 29.69606
## attr(,"conf.level")
## [1] 0.95

```

Para determinar la estimación del ejemplo anterior, se puede colocar el siguiente segmento:

```r
t.test(x = base_creles$muac, conf.level = 0.95)$estimate

```

**Resultado:**

```text
mean of x
  28.66

```

---

## Estimación por intervalos: para la proporción

Para construir un intervalo de confianza para la estimación de la proporción se puede utilizar el siguiente código.

### Ejemplo

Considere la base de datos `base_creles` y determine un intervalo de confianza del 95% para estimar la proporción real de mujeres de 60 años y más.

En la `base_creles` las mujeres fueron codificadas con la letra F.

```r
x <- length(which(base_creles$sexo == "F"))
n <- length(base_creles$sexo)
p <- x/n
alpha <- 0.05; alpham <- alpha/2 
zalpham = qnorm(1 - alpham)
sigmap = sqrt(p*(1 - p)/n)
E <- zalpham*sigmap
c((Li = p - E), (Ls = p + E))

```

**Resultado:**

```text
## [1] 0.4018538 0.6781462

```

### Ejemplo

Considere la base de datos `base_creles` y determine un intervalo de confianza del 95% para estimar la proporción real de personas de 60 años y más con un peso mayor a 50 kg.

```r
x <- length(which(base_creles$peso > 50))
n <- length(base_creles$peso)
p <- x/n
alpha <- 0.05; alpham <- alpha/2 
zalpham = qnorm(1 - alpham)
sigmap = sqrt(p*(1 - p)/n)
E <- zalpham*sigmap
c((Li = p - E), (Ls = p + E))

```

**Resultado:**

```text
## [1] 0.7899269 0.9700731

```

---

Además, puede utilizarse la función `prop.test(x, n, conf.level, ...)$conf`, la cual nos da el intervalo de confianza de Wilson.

### Ejemplo

Considere la base de datos `base_creles` y determine un intervalo de confianza del 95% para estimar la proporción real de personas de 60 años y más con un peso mayor a 50 kg.

```r
prop.test(x = length(which(base_creles$peso > 50)),
          n = length(base_creles$peso),
          conf.level = 0.95)$conf

```

**Resultado:**

```text
## [1] 0.7499729 0.9502607
## attr(,"conf.level")
## [1] 0.95

```

---

Además, si se desea obtener la estimación puntual de la proporción puede utilizarse la función `prop.test(x, n, conf.level, ...)$estimate`.

### Ejemplo

Considere la base de datos `base_creles` y obtenga la estimación puntual de la proporción de personas de 60 años y más con un peso mayor a 50 kg. Utilice un nivel de confianza de 95%.

```r
prop.test(x = length(which(base_creles$peso > 50)),
          n = length(base_creles$peso),
          conf.level = 0.95)$estimate

```

**Resultado:**

```text
##    p 
## 0.88
```
