# Teorema de Bayes

## Definición

El teorema de Bayes describe la probabilidad de un evento basado en conocimiento previo que puede estar relacionado con ese evento. Es una manera de actualizar creencias cuando nueva evidencia aparece.

**Formula:**
```
P(A|B) = P(B|A) * P(A) / P(B)
```

Donde:
- `P(A|B)` — Probabilidad de A dado que B ocurrió (probabilidad posterior)
- `P(B|A)` — Probabilidad de B dado que A ocurrió (verosimilitud / likelihood)
- `P(A)` — Probabilidad base de A (prior)
- `P(B)` — Probabilidad de B (evidencia total)

## Idea Central

No empezamos de cero. Cada nueva pieza de información ajusta lo que creemos. Bayes formaliza cómo hacer eso bien.

## Preguntas Clave

- ¿Cómo actualizar creencias cuando llega evidencia nueva?
- ¿Por qué las probabilidades previas importan tanto?
- ¿Cómo separa el ruido de la señal?
- ¿Dónde falla la intuición sin Bayes?

## Por Qué Importa

- Medicina: diagnóstico con pruebas imperfectas
- Machine learning: clasificación, spam, recomendaciones
- Ciencia: actualización de hipótesis
- Vida diaria: tomar decisiones con información incompleta

## Título Alternativo
"Cómo actualizar creencias correctamente"