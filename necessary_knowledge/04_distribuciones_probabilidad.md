# Distribuciones de Probabilidad

## Qué Es una Distribución

Una distribución de probabilidad describe cómo se distribuyen los resultados posibles de una variable aleatoria. Es una función que asigna una probabilidad a cada resultado posible.

## Variables Aleatorias

Una **variable aleatoria** es una función que asigna un número a cada resultado del espacio muestral.

- **Discreta:** toma valores contables (número de águilas en 10 lanzamientos)
- **Continua:** toma valores en un rango continuo (altura, temperatura)

## Distribuciones Discretas

### Distribución Uniforme Discreta

Todos los resultados tienen igual probabilidad.

**Ejemplo:** Lanzar un dado equilibrado.

```
P(X = k) = 1/6  para k = 1, 2, 3, 4, 5, 6
```

### Distribución Binomial

Modela el número de éxitos en n ensayos independientes, cada uno con probabilidad p.

**Fórmula:**
```
P(X = k) = C(n, k) * p^k * (1-p)^(n-k)
```

**Parámetros:**
- n = número de ensayos
- p = probabilidad de éxito
- k = número de éxitos

**Ejemplo:** ¿Cuántas águilas en 10 lanzamientos de moneda justa (p=0.5)?

```
P(X = 7) = C(10, 7) * 0.5^7 * 0.5^3
         = 120 * 0.00781 * 0.125
         = 0.117
```

### Distribución de Poisson

Modela el número de eventos que ocurren en un intervalo de tiempo o espacio, cuando los eventos son independientes y la tasa promedio es constante.

**Fórmula:**
```
P(X = k) = (λ^k * e^(-λ)) / k!
```

**Parámetro:**
- λ = número promedio de eventos por intervalo

**Ejemplo:** Un sitio web recibe en promedio 3 visitantes por minuto. ¿Cuál es la probabilidad de recibir exactamente 5?

```
P(X = 5) = (3^5 * e^(-3)) / 5! ≈ 0.1008
```

## Distribuciones Continuas

### Distribución Uniforme Continua

Todos los valores en el rango [a, b] son equally probable.

```
f(x) = 1/(b-a)  para a ≤ x ≤ b
```

**Ejemplo:** Un número aleatorio entre 0 y 1.

### Distribución Normal (Gaussiana)

La distribución más importante en estadística. Aparece naturalmente en fenómenos con múltiples factores independientes.

**Fórmula:**
```
f(x) = (1 / (σ√(2π))) * e^(-(x-μ)² / (2σ²))
```

**Parámetros:**
- μ = media (centro)
- σ = desviación estándar (dispersión)

**Propiedades:**
- 68% de la masa entre μ-σ y μ+σ
- 95% entre μ-2σ y μ+2σ
- 99.7% entre μ-3σ y μ+3σ

## Esperanza y Varianza

### Esperanza (Valor Esperado)

La media ponderada de todos los valores posibles, donde el peso es la probabilidad.

**Variable discreta:**
```
E[X] = Σ x_i * P(X = x_i)
```

**Variable continua:**
```
E[X] = ∫ x * f(x) dx
```

**Propiedades:**
```
E[aX + b] = aE[X] + b
E[X + Y] = E[X] + E[Y]
```

### Varianza

Mide qué tan dispersos están los valores alrededor de la media.

```
Var(X) = E[(X - E[X])²] = E[X²] - (E[X])²
```

**Propiedades:**
```
Var(aX + b) = a² Var(X)
Var(X + Y) = Var(X) + Var(Y)  si X e Y son independientes
```

### Desviación Estándar

```
σ = √Var(X)
```

Es más interpretable que la varianza porque está en las mismas unidades que X.

## Distribuciones y Bayes

El teorema de Bayes en su forma continua utiliza **distribuciones**:

```
f(θ|x) = f(x|θ) * f(θ) / f(x)
```

- f(θ) = distribución prior (creencia antes de ver datos)
- f(x|θ) = verosimilitud (likelihood)
- f(θ|x) = distribución posterior (creencia actualizada)
- f(x) = evidencia (normalizadora)

Cuando los espacios son continuos, las probabilidades de puntos específicos son 0 — trabajamos con densidades y integrales.

## Ley de los Grandes Números (Versión Formal)

Si X_1, X_2, ..., X_n son variables aleatorias independientes e idénticamente distribuidas (i.i.d.) con esperanza μ, entonces:

```
(X_1 + ... + X_n) / n → μ  cuando n → ∞
```

La media muestral converge a la media teórica conforme aumenta el tamaño de la muestra. Esto justifica el uso de promedios para estimar parámetros desconocidos.