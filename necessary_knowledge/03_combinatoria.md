# Combinatoria: Contar Resultados

## El Problema Fundamental

Antes de calcular probabilidades, necesitas **contar** cuántos resultados posibles hay. La combinatoria es la rama de las matemáticas que se dedica a esto.

## Principio de Multiplicación

Si un proceso tiene dos etapas independientes:
- Etapa 1: m posibles resultados
- Etapa 2: n posibles resultados

Entonces el proceso completo tiene **m × n** resultados posibles.

**Ejemplo:** Lanzar moneda (2 resultados) y dados (6 resultados):
- Resultados totales = 2 × 6 = 12

## Permutaciones: Orden Importa

Una **permutación** es un arreglo ordenado de elementos. El orden importa.

**Fórmula:**
```
P(n, r) = n! / (n - r)!
```

Donde:
- n = total de elementos
- r = elementos que elegimos
- n! = n × (n-1) × (n-2) × ... × 1 (factorial)

**Ejemplo:** ¿Cuántas formas de asignar primer, segundo y tercer lugar en una carrera de 8 corredores?

```
P(8, 3) = 8! / (8-3)! = 8! / 5! = 40320 / 120 = 336
```

**8 × 7 × 6 = 336** — tiene sentido: 8 opciones para primer lugar, 7 para segundo, 6 para tercero.

## Combinaciones: Orden No Importa

Una **combinación** es un grupo donde el orden no importa.

**Fórmula:**
```
C(n, r) = n! / (r! * (n - r)!)
```

Se lee como "n choose r" o "n sobre r".

**Ejemplo:** ¿Cuántos equipos de 3 personas puedes formar de un grupo de 8?

```
C(8, 3) = 8! / (3! * 5!) = 56
```

**Nota:** C(8,3) = C(8,5) — elegir 3 de 8 es lo mismo que excluir 5 de 8.

## La Relación entre Permutaciones y Combinaciones

```
P(n, r) = C(n, r) * r!
```

Primero eliges el grupo (combinación), luego lo ordenas (permutación).

## Ejemplo con Probabilidad: Póker

En una mano de póker de 5 cartas de un mazo de 52:

```
C(52, 5) = 52! / (5! * 47!) = 2,598,960 manos posibles
```

La probabilidad de un flush (5 cartas del mismo palo, sin straight):

```
P(flush) = 4 * C(13, 5) / C(52, 5) ≈ 0.002
```

(aproximadamente 0.2% — muy poco probable)

## Principio de Adición

Si tienes dos conjuntos disjuntos (no se overlap):
- |A| = m resultados
- |B| = n resultados

El total de resultados en A o B es **m + n**.

**Ejemplo:** Lanzar moneda o dados (no ambos):

- moneda: 2 resultados
- dado: 6 resultados
- total: 2 + 6 = 8

## Factorial y el Espacio Muestral

Los factoriales crecen extremadamente rápido:

```
5! = 120
10! = 3,628,800
20! ≈ 2.4 × 10^18
52! ≈ 8.07 × 10^67
```

Por esto no puedes simplemente listar todos los resultados en problemas combinatorios reales — el espacio muestral puede serastronómicamente grande.

## Aplicación en Probabilidad Discreta

Para calcular P(A) en un espacio discreto:

```
P(A) = |A| / |Ω|
```

donde |A| es el tamaño del evento y |Ω| es el tamaño del espacio muestral.

**Ejemplo:** ¿Cuál es la probabilidad de sacar exactamente 2 águilas en 3 lanzamientos de moneda?

- Espacio muestral: 2^3 = 8 resultados
- Resultados con exactamente 2 águilas: C(3,2) = 3 (A-A-S, A-S-A, S-A-A)
- P = 3/8 = 0.375

## Por Qué Importa para Bayes

Para aplicar el teorema de Bayes en espacios discretos, necesitas poder contar:
- Casos favorables para P(B|A)
- Casos totales para P(B)
- Casos favorables para P(A) y P(¬A)

Si no puedes contar correctamente, tus probabilidades serán incorrectas. La combinatoria es la herramienta que hace posible contar cuando los espacios son grandes.