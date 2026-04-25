# El Calentamiento Global Visto a Través de Bayes: Cómo la Ciencia del Clima Acumula Evidencia

## La pregunta que tardó décadas en responderse

En 1896, el químico sueco **Svante Arrhenius** calculó que duplicar la concentración de CO₂ en la atmósfera elevaría la temperatura global entre 4°C y 6°C. No tenía datos suficientes para confirmar su hipótesis, pero la teoría era físicamente sólida: el CO₂ absorbe radiación infrarroja. Era una predicción basada en primeros principios, verificable — eventualmente — con evidencia empírica.

Pasaron más de 100 años antes de que la evidencia observational fuera lo suficientemente fuerte como para que la práctica totalidad de la comunidad científica aceptara la conclusión: **el calentamiento global es real, está causado principalmente por actividades humanas, y sus efectos serán profundos**.

¿Cómo llegamos allí? ¿Y cómo quantificamos la fuerza de la evidencia acumulada? El teorema de Bayes proporciona el framework natural para entenderlo.

## La lógica bayesiana del cambio climático

El razonamiento científico sobre el cambio climático es, en su esencia, un proceso de actualización bayesiana colectiva. Cada nueva pieza de evidencia — mediciones de temperatura, registros de hielo marino, datos de océanos, modelos teóricos — actualiza la probabilidad de la hipótesis de que el calentamiento global antropogénico es real.

Definamos las hipótesis:

- **H₁:** El calentamiento global es real y está causado principalmente por emisiones humanas de gases de efecto invernadero.
- **H₀:** El calentamiento global no es real, o no está causado por actividades humanas, o está explicado por factores naturales (variabilidad solar, vulcanismo, etc.).

La evidencia se acumula gradualmente, y Bayes nos dice exactamente cómo debe update our beliefs.

## Las piezas de evidencia: una cronología de actualización

### 1. El efecto greenhouse得太 bien得太快 (傅立叶, 1824-1860s)

Jean-Baptiste Joseph Fourier fue el primero en proponer que la atmósfera terrestre actúa como un aislante, permitiendo que la luz solar entre pero evitando que el calor escape. Esta idea — ahora llamada el **efecto invernadero natural** — fue controversial pero no conclusive. La probabilidad previa de que las actividades humanas pudieran afectar el clima era extremadamente baja: P(H₁) ≈ 0.01.

### 2. Los primeros registros de temperatura (1850s-1900s)

Con el establecimiento de redes de estaciones meteorológicas, los científicos comenzaron a tener registros sistemáticos. Las mediciones early mostraban variaciones, pero la calidad de los datos era desigual. La likelihood de estos datos bajo H₁ vs H₀ era apenas marginalmente favorable a H₁: LR ≈ 1.5.

```
P(H₁ | datos 1900) ≈ (1.5 × 0.01) / [(1.5 × 0.01) + (1 × 0.99)] ≈ 1.5%
```

La creencia en H₁ se actualizó marginalmente, de 1% a ~1.5%.

### 3. Las curvas de Keeling (1958-presente)

**Charles David Keeling**, en 1958, comenzó sus famous mediciones de CO₂ en Mauna Loa, Hawai. Estos datos, que muestran el aumento relentless de CO₂ atmosférico (la "curva de Keeling"), proporcionaron la evidencia más directa de que las concentraciones de gases de efecto invernadero estaban aumentando. La likelihood de este aumento observado bajo H₁ (emisiones humanas) era extremely high: LR ≈ 100+.

```
P(H₁ | curva de Keeling) = (100 × 0.015) / [(100 × 0.015) + (1 × 0.985)]
                         ≈ 0.60 ≈ 60%
```

En este punto (mediados de los 1960s), la probabilidad de H₁ subió a aproximadamente 60%. La evidencia ya no era marginal: era sustancial.

### 4. La attribción del calentamiento (1988-presente)

En 1988, **James Hansen** testificó ante el Congreso de Estados Unidos que el calentamiento global ya era detectable. A partir de entonces, la ciencia de la **atribución** — distinguir cuánto del calentamiento se debe a factores humanos versus naturales — se volvió central.

Los climatólogos usan **detection and attribution studies** que aplican esencialmente lógica bayesiana. La pregunta: ¿cuál es la probabilidad de observar el patrón de calentamiento actual bajo H₁ (forzamiento antropogénico) versus H₀ (variabilidad natural)?

Datos reales de attribution studies (IPCC AR6, 2021):

- Contribución humana al forzamiento radiativo: +2.72 W/m² (rango +2.50 a +2.94)
- Contribución solar y volcánica: -0.05 a +0.10 W/m²
- El calentamiento observado es **5-sigma** outlier respecto a la variabilidad natural (equivalente a un likelihood ratio de aproximadamente **1,000,000 a 1**)

Es decir: la probabilidad de observar el calentamiento actual si fuera solo variabilidad natural es essentially cero. La likelihood ratio strongly favorece H₁.

```
P(H₁ | evidencia de atribución moderna) ≈ 99.9%+
```

### 5. El consenso sobre la atribución humana (IPCC AR6, 2021)

El Sexto Informe de Evaluación del IPCC encontró que:

- Es **extremadamente probable (95-100% de confianza)** que más de la mitad del calentamiento observado desde 1950 sea atribuible a la influencia humana.
- La mejor estimación es que **~100% del calentamiento** (dentro de un rango de 67-100%) es causado por humanos.

Estas no son opiniones — son el resultado de múltiples líneas de evidencia independientes (temperatura observada, forzamiento radiativo, modelos climáticos, isótopos de carbono, datos oceánicos) que convergen en la misma conclusión.

## Un ejemplo numérico concreto: atribución del calentamiento 1951-2010

El IPCC ha publicado las siguientes estimaciones de la contribución de diferentes factores al calentamiento observado desde 1951:

| Factor | Contribución al calentamiento (°C) |
|---|---|
| CO₂ | +0.85°C |
| Metano | +0.20°C |
| Óxidos de nitrógeno | +0.10°C |
| Aerosoles | -0.40°C |
| Variabilidad natural (solar, volcánica) | +0.05°C |
| **Total antropogénico** | **+0.75°C** |
| **Total observado** | **+0.73°C** |

La correspondencia casi perfecta entre el warming atribuido a factores humanos y el warming observado es lo que los científicos llaman **attribution of warming to human cause**. La pequeña diferencia (0.02°C) está dentro de los márgenes de incertidumbre.

Para calcular la significancia estadística de esta atribución usando Bayes:

Asumamos:
- Prior P(H₁) = 0.50 (antes de este análisis, beliefs equally split)
- Likelihood ratio bajo H₁: la evidencia observada (calentamiento +0.73°C con forzamiento antropogénico que explica +0.75°C) es altamente probable si H₁ es true — LR ≈ 10,000
- Likelihood ratio bajo H₀: bajo variabilidad natural pura, un warming de +0.73°C en 60 años es muy improbable — LR ≈ 0.001

```
P(H₁ | evidencia atribución) = (10000 × 0.50) / [(10000 × 0.50) + (0.001 × 0.50)]
                            = 5000 / 5000.0005
                            ≈ 99.98%
```

## La acumulación bayesiana de evidencia: por qué el consenso tardó tanto

Una lección importante del caso del cambio climático es que **la actualización bayesiana es gradual cuando las tasas base previas son bajas**. En el siglo XIX y principios del XX, la hipótesis de que los humanos podían afectar el clima global era verdaderamente a priori inverosímil: las emisiones de CO₂ eran mínimas comparadas con las fuentes naturales, y la comprensión teórica del efecto invernadero era rudimentaria.

Un prior de ~0.01 (1%) era razonable. Con evidencia gradual — primero teórica, luego observational, luego experimental — la actualización ocurrió paso a paso, a lo largo de décadas.

Lo notable es que **el proceso científico funcionó exactamente como Bayes predice que debería**: cuando la evidencia finalmente se volvió overwhelm, el consenso científico cambió con velocidad proporcional a la fuerza de la evidencia. Hansen testificó en 1988 con un 95% de confianza. Para 2007 (IPCC AR4), el consenso científico sobre la atribución humana era near-universal. Para 2021 (IPCC AR6), la confianza había alcanzado niveles de **5-sigma** (equivalente a la evidencia que se requiere en física de partículas para claim un "descubrimiento").

## Incertidumbres y la función de Bayes en la comunicación de la ciencia

Una de las críticas más comunes a la ciencia del clima desde fuera de la comunidad científica es: "los modelos no pueden predecir el clima con precisión, ¿cómo pueden estar tan seguros del calentamiento?" Esta crítica confunde dos cosas diferentes:

1. **Predicción del clima futuro:** Los modelos climáticos tienen incertidumbres genuinas sobre la sensibilidad del clima (cuánto calentamiento resultará de una duplicación de CO₂), sobre los feedback de nubes, y sobre la velocidad de cambios en las corrientes oceánicas. Estas incertidumbres son reales y los científicos las cuantifican cuidadosamente.

2. **Detección y atribución del cambio ya observado:** La evidencia de que el warming ha ocurrido y de que está causado por humanos es estadísticamente mucho más sólida. La incertidumbre en la predicción future no contradice la certidumbre sobre la atribución del pasado.

Bayes permite separar estas dos preguntas. La incertidumbre sobre la sensibilidad climática se captura en una distribución de probabilidad sobre la hipótesis de cuánto calentamiento ocurrirá en el futuro. Pero la atribución del warming ya observado es una pregunta diferente, con evidencia diferente, y su respuesta tiene mucha menos incertidumbre.

## El mensaje final: ciencia como proceso de aprendizaje

El caso del cambio climático demuestra que el teorema de Bayes no es solo una herramienta matemática — es una descripción normativa de cómo la ciencia realmente funciona. Cuando la evidencia es débil, las creencias permanecen cercanas a la tasa base. Cuando la evidencia se acumula, las creencias se actualizan proporcionalmente. Cuando la evidencia es overwhelming, las creencias convergen hacia la verdad.

Los científicos del clima no "decidieron" creer en el calentamiento global. Fueron actualizando sus creencias a lo largo de décadas, con cada nueva medición, cada nuevo modelo, cada nueva línea de evidencia. El hecho de que el consenso final sea tan fuerte (99.9%+ de confianza en la atribución humana) refleja simplemente la fuerza acumulada de décadas de datos.

Arrhenius, si pudiera ver los datos modernos, probablemente actualizaría su belief de ~0.01 a algo muy cercano a 1. No porque sus intuiciones de 1896 fueran correctas, sino porque la evidencia acumulada las habría actualizado por él — que es exactamente lo que Bayes prescribe.

La próxima vez que alguien diga que "la ciencia no puede estar segura de nada", recuérdales que la ciencia del clima tiene más de 150 años de actualización bayesiana acumulada, y el veredicto es overwhelmingly claro.
