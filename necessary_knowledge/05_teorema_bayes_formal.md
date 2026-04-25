# La Regla de Bayes: Derivación Formal

## Partiendo de la Probabilidad Condicional

Recordemos la definición de probabilidad condicional:

```
P(A|B) = P(A ∩ B) / P(B)
```

Esto se puede reescribir como:

```
P(A ∩ B) = P(B) * P(A|B)
```

Por simetría ( intercambiando A y B):

```
P(A ∩ B) = P(A) * P(B|A)
```

## La Derivación

Igualando las dos expresiones para P(A ∩ B):

```
P(B) * P(A|B) = P(A) * P(B|A)
```

Despejando P(A|B):

```
P(A|B) = P(A) * P(B|A) / P(B)
```

**Esa es la forma más simple del teorema de Bayes.**

## La Forma Completa (Ley de Probabilidad Total)

Para que la fórmula sea útil, necesitamos expandir P(B) cuando A puede descomponerse en múltiples partes.

Si {A_1, A_2, ..., A_n} es una partición del espacio muestral (mutuamente excluyentes y exhaustivos), entonces para cualquier B:

```
P(B) = Σ P(B|A_i) * P(A_i)
```

Sustituyendo en Bayes:

```
P(A_k|B) = P(A_k) * P(B|A_k) / Σ P(A_i) * P(B|A_i)
```

## Ejemplo Numérico Completo

Imaginemos un sistema de diagnóstico médico para una enfermedad con tres variantes:

**Datos:**
- Variante A: prevalencia 50%, prueba positiva 90% de las veces
- Variante B: prevalencia 30%, prueba positiva 80% de las veces
- Variante C: prevalencia 20%, prueba positiva 70% de las veces

El paciente da positivo. ¿Cuál es la probabilidad de cada variante?

```
P(A|pos) = (0.5 * 0.9) / [(0.5*0.9) + (0.3*0.8) + (0.2*0.7)]
         = 0.45 / [0.45 + 0.24 + 0.14]
         = 0.45 / 0.83
         = 0.542
```

**P(B|pos) = 0.24 / 0.83 = 0.289**

**P(C|pos) = 0.14 / 0.83 = 0.169**

## Forma con Odds (Odds Form)

Los odds ofrecen una perspectiva alternativa:

```
Odds(A|B) = Odds(A) * P(B|A) / P(B|¬A)
```

O equivalentemente:

```
Odds(A|B) = Odds(A) * LikelihoodRatio(A→B)
```

donde **Likelihood Ratio** = P(B|A) / P(B|¬A).

Esta forma es útil cuando no conoces P(B) directamente — solo necesitas comparar cómo B se comporta bajo A vs ¬A.

## Forma Continua del Teorema de Bayes

Cuando tanto A como B son continuos, el teorema se expresa en términos de densidades:

```
f(θ|x) = f(x|θ) * f(θ) / ∫ f(x|θ') * f(θ') dθ'
```

Donde:
- f(θ) = prior sobre el parámetro θ
- f(x|θ) = verosimilitud (likelihood)
- f(θ|x) = posterior (creencia actualizada sobre θ después de ver x)
- El denominador es la evidencia (marginal likelihood)

## El Papel de la Evidencia (Normalizadora)

El denominador P(B) o ∫ f(x|θ')f(θ')dθ' asegura que la probabilidad total sea 1.

```
P(A|B) + P(¬A|B) = 1
```

Esto no es trivial — si la normalización falla, tendrías probabilidades que no suman 1, lo cual violaría los axiomas de Kolmogorov.

## Casos Especiales: Conjugación

Cuando el prior y el posterior pertenecen a la misma familia de distribuciones, se llaman **conjugados**. Esto simplifica enormemente los cálculos.

**Ejemplo:** Likelihood binomial + prior beta → posterior beta.

El prior beta tiene forma:
```
f(θ) = θ^(α-1) * (1-θ)^(β-1)
```

Después de observar datos (n ensayos con k éxitos):
```
f(θ|datos) ∝ θ^(α+k-1) * (1-θ)^(β+n-k-1)
```

Esto es otro beta, con parámetros actualizados α' = α + k, β' = β + n - k.

**No necesitas integrales** — solo sumar y restar parámetros.

## Por Qué Es Importante

El teorema de Bayes no es solo una fórmula — es un **framework para actualizar creencias sistemáticamente**. Cada pieza de nueva evidencia ajusta tus probabilidades en proporción a cuán probable hace esa evidencia bajo diferentes hipótesis.

La elegancia de la derivación viene de cómo conecta las piezas:
- Probabilidad condicional (definición básica)
- Simetría de intersección (intercambio A/B)
- Ley de probabilidad total (particionar el espacio)
- Normalización (asegurar que todo sume 1)

Todo fluendo naturalmente desde los axiomas de Kolmogorov hasta la herramienta más poderosa de la inferencia estadística.