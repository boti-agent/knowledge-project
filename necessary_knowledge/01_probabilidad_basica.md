# Probabilidad Básica

## Concepto

La probabilidad mide qué tan probable es que ocurra un evento. Se expresa como un número entre 0 y 1, donde 0 significa imposible y 1 significa seguro.

## Formalmente

Dado un **espacio muestral** Ω (todos los posibles resultados) y un **evento** A (un subconjunto de resultados que nos interesan):

```
P(A) = casos favorables / casos totales
```

## Axiomas de Kolmogorov

1. **No negatividad:** P(A) ≥ 0 para cualquier evento A
2. **Normalización:** P(Ω) = 1 (algun resultado siempre ocurre)
3. **Aditividad:** Si A y B son mutuamente excluyentes (no pueden ocurrir juntos), entonces P(A ∪ B) = P(A) + P(B)

## Ejemplo: Dado justo

Un dado tiene 6 caras. La probabilidad de sacar un 3 es:

```
P(3) = 1/6 ≈ 0.167
```

La probabilidad de sacar un número par (2, 4, 6):

```
P(par) = 3/6 = 1/2 = 0.5
```

## Probabilidad vs Odds

Los **odds** son otra forma de expresar probabilidad:

```
odds(A) = P(A) / P(¬A) = P(A) / (1 - P(A))
```

Si P(A) = 0.75, entonces odds = 0.75/0.25 = 3 (3 a 1 a favor).

## Espaço Muestral Discreto vs Continuo

- **Discreto:** resultados contables (dado, moneda, dados)
- **Continuo:** resultados en un rango (altura, temperatura, tiempo)

Para continuos, la probabilidad de un punto específico es técnicamente 0 — trabajamos con intervalos.

## Ley de los Grandes Números

Si repites un experimento muchas veces, la frecuencia relativa se acerca a la probabilidad teórica. Por eso la definición clásica (frecuentista) de probabilidad funciona: es el límite de observaciones repetidas.

## Conceptos Clave para Bayes

- La probabilidad es una medida de **creencia** o **frecuencia**
- Toda probabilidad es condicional aunque no lo parezca (respecto a información previa)
- P(A) puede interpretarse como la creencia en A antes de ver nueva evidencia

## Relación con Bayes

El teorema de Bayes trabaja con probabilidades condicionales y requiere entender:
- P(A) como **prior** (creencia antes de evidencia)
- P(A|B) como **posterior** (creencia actualizada después de ver B)
- P(B|A) como **likelihood** (cuánto probable es ver B si A es cierto)