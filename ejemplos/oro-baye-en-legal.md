# El Teorema de Bayes en el Sistema Legal: Cuando la Intuición Engaña a la Justicia

## La falacia de la tasa base en el aula

Imaginemos el siguiente escenario que los profesores de derecho usan rutinariamente para demonstrar cómo la intuición humana falla en probabilidad:

> *Un crimen ha sido cometido. El único testigo lo presenció bajo condiciones de luz deficientes. El testigo dice que el culpable era rubio. En la ciudad donde ocurrió el crimen, el 90% de la población es morena y solo el 10% es rubia. El testigo es confiable en el 80% de los casos (es decir, identifica correctamente el color del cabello en 8 de cada 10 ocasiones).*

> *Pregunta: ¿Cuál es la probabilidad de que el culpable sea rubio, dado que el testigo lo identificó como rubio?*

La respuesta intuitiva de la mayoría de la gente — incluyendo muchos abogados, jueces y jurados — es aproximadamente 80%, porque el testigo es confiable en el 80%. Pero esto es **incorrecto**.

La respuesta correcta se obtiene con el teorema de Bayes:

```
P(rubio | testigo dice rubio) = [P(testigo dice rubio | rubio) × P(rubio)] / P(testigo dice rubio)
```

Calculémoslo:

- P(testigo dice rubio | rubio) = 0.80 (sensibilidad del testigo)
- P(rubio) = 0.10 (tasa base de rubios en la población)
- P(testigo dice rubio) = P(testigo dice rubio | rubio) × P(rubio) + P(testigo dice rubio | moreno) × P(moreno)
- P(testigo dice rubio | moreno) = 0.20 (probabilidad de error, es decir, que el testigo diga rubio siendo moreno)
- P(moreno) = 0.90

```
P(testigo dice rubio) = (0.80 × 0.10) + (0.20 × 0.90) = 0.08 + 0.18 = 0.26

P(rubio | testigo dice rubio) = (0.80 × 0.10) / 0.26 = 0.08 / 0.26 ≈ 30.8%
```

Es decir: **la probabilidad de que el culpable sea rubio es de solo ~31%**, no 80%. La razón: aunque el testigo tiene razón el 80% de las veces, los morenos son nueve veces más comunes en la población. Los errores del testigo (decir "rubio" cuando es moreno) dominan porque hay muchos más morenos entre los cuales "equivocarse".

Este fenómeno se llama la **falacia de la tasa base** (*base rate fallacy*), y es una de las formas más documentadas en que la probabilidad humana falla sistemáticamente.

## El teorema de Bayes como estándar legal: el caso de Regina vs. Adams

El uso explícito del teorema de Bayes en un tribunal tiene una historia corta y controversial. En **1996**, en el caso **R v Adams** (Crown Court, Winchester, Inglaterra), el juez Ognall permitió — por primera vez en la historia del derecho anglosajón — que se presentara testimonio usando el teorema de Bayes para evaluar la fuerza probatoria de evidencia compleja.

El caso involucraba al Sr. Adams, acusado de asesinato. La evidencia física era circumstantial (huellas dactilares parciales, análisis estadístico de coincidencias). El statist fue llamado a testificar sobre la fuerza de la evidencia. El defense lo utilizó para argumentar que la evidencia no era tan fuerte como la Crown claimaba.

La reacción de la comunidad legal fue polarizada. Barristers y jueces argumentaron que el razonamiento Bayesiano era demasiado difícil para que los jurados lo comprendieran y que introducía una aura de precisión matemática ficticia en un proceso que es inherentemente about weighing human testimony and credibility. Lord Bingham, entre otros, expressaron preocupación de que el teorema de Bayes "le da al evidence una apariencia de precisión científica que no merece".

Sin embargo, el caso sentó un precedente: en principe, los métodos estadísticos pueden presentarse ante un jurado, aunque la cuestión de cómo presentarlos de manera comprensible sigue siendo debatida.

## La falacia del fiscal (*prosecutor's fallacy*)

Uno de los conceptos más peligrosos en la aplicación de probabilidad al derecho es lo que se conoce como la **falacia del fiscal**: ocurre cuando se confunde la probabilidad de que la evidencia sea observada *si* el acusado es inocente, con la probabilidad de que el acusado sea inocente *si* la evidencia fue observada.

En términos formales:
- **Lo que NO debemos decir:** "La probabilidad de encontrar este ADN si el acusado fuera inocente es 1 en 10 millones. Por lo tanto, hay una probabilidad de 1 en 10 millones de que sea inocente."
- **Lo que SÍ debemos decir:** "Si el acusado fuera inocente, esperaríamos encontrar esta coincidencia de ADN en aproximadamente 1 de cada 10 millones de casos similares. Esto es evidencia muy fuerte en su contra, pero la conclusión depende también de qué tan plausible es la hipótesis de que alguien más dejó esa muestra."

La diferencia es sutil pero crítica. La primera afirmación ignora la tasa base: ¿cuántas personas en la población total podrían haber dejado esa muestra? Si hay 30 millones de personas que podrían ser la fuente, entonces "1 en 10 millones" significa que esperamos **3 personas** que coincidan, no que la probabilidad de inocencia sea 1/10,000,000.

## El caso DNA: cuando las match statistics se malinterpretan

Los laboratorios forenses de ADN reportan lo que se llama el **Random Match Probability (RMP)**: la probabilidad de que una persona elegida al azar de la población tenga un perfil de ADN que coincida con la evidencia. Valores típicos son del orden de 1 en cientos de miles de millones.

El problema es que los fiscales y a veces los jueces presentan el RMP como la probabilidad de que el acusado sea inocente. Pero el RMP no toma en cuenta:

1. **La tasa base de criminalidad:** ¿Cuántas personas con motivo y oportunidad existían en la escena?
2. **La posibilidad de contaminación** de la muestra
3. **La posibilidad de que el perfil corresponda a un familiar** del verdadero culpable (los perfiles de familiares pueden partial-match)
4. **El contexto de la investigación:** ¿Se seleccionó al accused porque matches la evidencia, o porque había other razones para sospecharlo?

Cuando se usa correctamente, el teorema de Bayes permite combinar el RMP con otras piezas de evidencia (testimonios, motive, alibi, etc.) para llegar a una evaluación más honesta de la probabilidad de culpabilidad.

## El teorema de Bayes como framework para jurados racionales

A pesar de las controversias, muchos estadísticos y filósofos del derecho argue que el teorema de Bayes proporciona el único framework matemáticamente coherente para actualizar creencias sobre la culpabilidad de un acusado a la luz de la evidencia. En este modelo:

- **Prior:** La probabilidad inicial de culpabilidad antes de ver la evidencia. En el contexto legal, algunos argue que debe ser *agnóstico* (50/50 para un accused que no ha sido juzgado aún), aunque otros sostienen que puede incorporate información sobre tasas de criminalidad en certain demographics (lo cual es problematic porque puede introducir sesgos).

- **Evidencia:** Cada pieza de evidencia (testimonio, ADN, alibi, etc.) actualiza la probabilidad de culpabilidad según su likelihood ratio. El teorema dice exactamente cómo hacer esto de manera coherente.

- **Posterior:** La probabilidad final de culpabilidad después de considerar toda la evidencia.

Lo que el teorema garantiza es que si dos personas comienzan con el mismo prior y consideran la misma evidencia en el mismo orden, ellas DEBEN llegar a la misma probabilidad posterior si usan la fórmula correcta. Es el único sistema que garantiza consistencia lógica en la actualización de creencias.

## El caso del testigo único: un ejemplo numérico completo

Consideremos un caso donde un testigo presencial, con un historial de confiabilidad del 75%, identifica a Juan como el culpable de un robo. La tasa base de criminalidad (robos per cápita en esa zona) es del 0.01% (1 de cada 10,000 personas cometen un robo en un período dado).

Datos:
- P(confiable) = 0.75 → P(error) = 0.25
- P(rubio | culpable rubio) no aplica aquí; usamos un modelo más simple

Supongamos que el testigo dice: "Juan fue el autor."

```
P(testigo dice Juan | Juan culpable) = 0.75
P(testigo dice Juan | Juan NO culpable) = 0.25

P(Juan culpable) = 0.0001 (tasa base de criminalidad)
P(Juan NO culpable) = 0.9999
```

```
P(testigo dice Juan) = (0.75 × 0.0001) + (0.25 × 0.9999)
                     = 0.000075 + 0.249975
                     = 0.25005

P(Juan culpable | testigo dice Juan) = (0.75 × 0.0001) / 0.25005
                                    ≈ 0.000075 / 0.25005
                                    ≈ 0.0003 = 0.03%
```

**Incluso con un testigo que tiene 75% de confiabilidad, la probabilidad de que Juan sea el culpable es de solo 0.03%**, dado que la tasa base de criminalidad es tan baja. Esto ilustra dramáticamente cómo un testigo aparentemente confiable puede ser casi inútil para establecer culpabilidad cuando la tasa base es muy baja.

## Hacia una justicia más bayesiana

Varios scholars, notablemente **Norman Fenton** (Queen Mary University of London) y **Martin Neil**, han advocated por la adopción de métodos Bayesianos formales en el análisis de evidencia forense. Su argumento: la alternativa — dejar que jurados y jueces razonen con intuiciones probabísticas — produce decisiones sistemáticamente sesgadas.

Su propuesta no es que los jurados calculen integrales, sino que se les presente la información en términos de **cocientes de verosimilitud** (*likelihood ratios*): ¿cuánto más probable es la evidencia si el acusado es culpable versus si es inocente? Este número es fácil de entender: si es 100, la evidencia es 100 veces más probable bajo la hipótesis de culpabilidad. Eso es una manera más honesta de presentar la evidencia que un "1 en 10 millones" que confunde más de lo que ilumina.

El teorema de Bayes, en el fondo, no es más que el sentido común expresado en matemáticas. La justicia sería mejor si más personas lo entendieran.
