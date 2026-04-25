# Probabilidad Condicional

## La Idea Central

La probabilidad condicional responde: **¿Cuál es la probabilidad de A dado que sé que B ocurrió?**

Se denota `P(A|B)` y se lee "probabilidad de A dado B".

## Definición Formal

```
P(A|B) = P(A ∩ B) / P(B)
```

siempre que P(B) > 0.

Esto requiere que B tenga probabilidad positiva — no puedes conditionar en un evento imposible.

## Ejemplo: Moneda y Dado

Imagina que lanzas una moneda y un dado.

- Espacio muestral: 12 resultados igualmente probables
- A = "la moneda cae águila" (6 resultados)
- B = "el dado cae 4" (2 resultados: A4, K4)

```
P(A) = 6/12 = 0.5
P(B) = 2/12 = 1/6 ≈ 0.167

P(A ∩ B) = 1/12 ≈ 0.083

P(A|B) = (1/12) / (2/12) = 1/2 = 0.5
```

Dado que el dado cayó 4, la moneda sigue siendo equally probable de águila o sol — las monedas no tienen memoria.

## Dependencia e Independencia

**Independencia:** A y B son independientes si saber que B ocurrió no cambia la probabilidad de A.

```
P(A|B) = P(A)
```

Equivalentemente:

```
P(A ∩ B) = P(A) * P(B)
```

**Dependencia:** La mayoría de los eventos reales son dependientes. Por ejemplo, "lluvia" y "llevar paraguas" son dependientes — si llovió, es más probable que hayas llevado paraguas.

## La Regla de la Multiplicación

De la definición anterior:

```
P(A ∩ B) = P(B) * P(A|B) = P(A) * P(B|A)
```

Esta relación es simétrica y es la base para calcular probabilidades de eventos compuestos.

## Ejemplo Más Sustancial: Diagnóstico Médico

Imagina una prueba para una enfermedad rara:

- Prevalencia de la enfermedad: 1% (0.01)
- Sensibilidad de la prueba: 99% (P(positivo|enfermo) = 0.99)
- Especificidad de la prueba: 95% (P(negativo|sano) = 0.95)

Queremos saber: si el test da positivo, ¿cuál es la probabilidad real de estar enfermo?

```
P(enfermo|positivo) = P(positivo|enfermo) * P(enfermo) / P(positivo)
```

Primero calculamos P(positivo):

```
P(positivo) = P(positivo|enfermo)P(enfermo) + P(positivo|sano)P(sano)
            = (0.99)(0.01) + (0.05)(0.99)
            = 0.0099 + 0.0495 = 0.0594
```

Entonces:

```
P(enfermo|positivo) = (0.99)(0.01) / 0.0594 ≈ 0.167
```

**Solo 16.7%** de los positivos están realmente enfermos, aunque la prueba tenga 99% de sensibilidad. Esto es contraintuitivo y muestra por qué Bayes es crucial.

## Por Qué Importa para Bayes

El teorema de Bayes es esencialmente una fórmula para invertir probabilidades condicionales:

```
P(A|B) = P(B|A) * P(A) / P(B)
```

Conocemos P(B|A) y queremos encontrar P(A|B). La diferencia entre "probabilidad de enfermedad dado test positivo" y "probabilidad de test positivo dado enfermedad" es enorme y sutil.

## Conceptos Erróneos Comunes

1. **Confusión de dirección:** La sensibilidad de un test (99%) no implica que 99% de los positivos estén enfermos.
2. **Ignorar tasas base:** En el ejemplo anterior, la enfermedad es rara (1%) — esto domina el resultado.
3. **Asumir independencia cuando no existe:** La mayor fuente de errores en razonamiento probabilístico.