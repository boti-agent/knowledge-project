# Teorema de Bayes

## Índice General

### 📚 Fundamento (necessary_knowledge)
Para entender Bayes desde la base:
1. [Probabilidad Básica](./necessary_knowledge/01_probabilidad_basica.md) — Qué es probabilidad, axiomas, espacios muestrales
2. [Probabilidad Condicional](./necessary_knowledge/02_probabilidad_condicional.md) — P(A|B), independencia, regla de multiplicación
3. [Combinatoria](./necessary_knowledge/03_combinatoria.md) — Contar resultados, factoriales, permutaciones, combinaciones
4. [Distribuciones de Probabilidad](./necessary_knowledge/04_distribuciones_probabilidad.md) — Discretas, continuas, esperanza, varianza
5. [Teorema de Bayes Formal](./necessary_knowledge/05_teorema_bayes_formal.md) — Derivación completa, ley de probabilidad total, forma continua

---

### 🔭 Perspectivas (perspectivas)
Análisis profundo desde múltiples ángulos:
- [Perspectiva Filosófica](./perspectivas/filosofica.md) — Epistemología, falsacionismo vs bayesianismo, naturaleza de la verdad
- [Perspectiva Científica](./perspectivas/cientifica.md) — Física, medicina basada en evidencia, frequentist vs bayesiano
- [Perspectiva Práctica](./perspectivas/practica.md) — Diagnóstico, spam, ML, trading, A/B testing
- [Perspectiva Histórica](./perspectivas/historica.md) — Bayes, Laplace, la era de datos
- [Perspectiva Contraria](./perspectivas/contraria.md) — Críticas, subjetividad de priors, límites

---

### 🧪 Ejemplos (ejemplos)
Casos reales que aplican Bayes:
- [Diagnóstico Médico](./ejemplos/diagnostico-medico.md) — Pruebas imperfectas, sensibilidad, especificidad
- [Filtros de Spam](./ejemplos/spam-filter.md) — Clasificación de emails, naive Bayes
- [Aplicación Legal](./ejemplos/oro-baye-en-legal.md) — Tasa base, falacia del fiscal, probabilidad en tribunales
- [El Científico Sin Gloria](./ejemplos/cientifico-sin-gloria.md) — Actualización correcta de creencias científicas
- [Finanzas y Trading](./ejemplos/finanzas-trading.md) — Señales de mercado, Kelly Criterion
- [Ciencia del Clima](./ejemplos/ciencia-clima.md) — Calentamiento global, acumulación de evidencia

---

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