# El Científico Sin Gloria: Actualización de Creencias en la Ciencia Real

## La trampa del confirmación

Imagine a un astrofísico que ha dedicado 30 años de su carrera a desarrollar una teoría sobre la naturaleza de la materia oscura. Su teoría predice que las curvas de rotación de ciertas galaxias deberían seguir un patrón específico. Finalmente, un nuevo telescopio produce datos que parecen confirmar esa predicción. ¿Debería el científico creer en los resultados? ¿Cuánto debería actualizar su confianza en la teoría?

Este escenario ilustra uno de los dilemas más profundos de la epistemología científica: **¿cómo debe un científico actualizar sus creencias a la luz de nueva evidencia?** La respuesta aparentemente obvia — "creer la evidencia" — esconde problemas sutiles que han causado errores históricos monumentales.

El teorema de Bayes proporciona un framework riguroso para esta pregunta, pero también revela dos errores simétricos igualmente graves.

## Los dos errores: updating troppo poco y troppo mucho

El filósofo de la ciencia **Colin Howson** y el statistician **Larry Laudan** popularizaron dos términos del italiano que capturan los extremos del espectro:

- **Updating troppo poco (*conservadurismo epistémico*):** Ignorar o subestimar evidencia nueva que contradice o apoya una teoría. El científico se ancla en su creencia previa y trata la evidencia nueva como ruido.

- **Updating troppo tanto (*impulsividad epistémica*):** Aceptar evidencia nueva sin el peso adecuado, actualizando demasiado drásticamente la probabilidad de una hipótesis. El científico se enamora del dato fresco y abandona una teoría bien establecida prematuramente.

La mayoría de los científicos se consideran inmunes a estos errores, pero la historia de la ciencia está llena de ejemplos de ambos.

## El caso histórico: la "partícula X" de Cecil Powell

En 1950, el físico Cecil Powell, descubridor del pión, estaba analizando datos de emulsiones fotográficas de rayos cósmicos en busca de nuevas partículas subatómicas. En una serie de placas, observó un patrón que parecía indicar la existencia de una partícula nunca antes vista — una partícula con una masa intermediaria entre el muón y el protón.

La evidencia era tentadora pero no conclusiva. Powell had been burned before by wishful thinking (a common pathology in particle physics, where new particles were occasionally "discovered" only to be later attributed to experimental artifacts).

Powell's prior belief about new particle discoveries was deliberately skeptical — after all, false positives were common in his field. He estimated P(new particle exists) ≈ 0.01 based on historical base rates (roughly 1 in 100 candidate signals in cosmic ray experiments turned out to be genuine new particles).

The likelihood of observing the pattern he saw, if the particle existed, was moderately high: perhaps 0.6 (60% chance of seeing such a pattern given a real particle with the hypothesized properties). The likelihood of seeing the pattern if there was no particle: low, perhaps 0.05 (a 5% chance of such a pattern arising from background noise).

Applying Bayes:
```
P(particle exists | observed pattern) = (0.6 × 0.01) / [(0.6 × 0.01) + (0.05 × 0.99)]
                                      = 0.006 / (0.006 + 0.0495)
                                      = 0.006 / 0.0555
                                      ≈ 0.108 ≈ 10.8%
```

Even with a promising signal, Powell's skeptical prior limited his posterior to just ~11%. He didn't publish immediately. He requested more data. Three months later, a second, independent experiment confirmed the particle (now known as the kaon). With that confirmation:

```
P(particle exists | two independent confirmations) = updated...
```

Assuming independent experiments each with the same likelihood structure, we can update sequentially or compute directly with the prior now being 0.108:

```
Posterior ≈ (0.6² × 0.01) / [(0.6² × 0.01) + (0.05² × 0.99)]
          = (0.36 × 0.01) / (0.0036 + 0.002475)
          = 0.0036 / 0.006075
          ≈ 0.593 ≈ 59.3%
```

With two independent confirmations, belief jumped to ~59%. Powell then published, and the particle (the K+ kaon) was indeed confirmed by many subsequent experiments. His cautious updating — neither ignoring the initial evidence nor overreacting to it — led to a correct conclusion.

## El contraste: el "descubrimiento" de la fusión fría (1989)

En 1989, los químicos Martin Fleischmann y Stanley Pons announced at a University of Utah press conference that they had achieved **cold fusion** — nuclear fusion at room temperature, something that had eluded physicists for decades. The implications were staggering: limitless clean energy.

The scientific community's prior on cold fusion was extremely low — perhaps P(cold fusion is real) ≈ 0.0001 or less. Cold fusion had been tried many times before and always failed. The theoretical physics underlying it was shaky at best.

Fleischmann and Pons presented what they claimed was excess heat production in an electrochemistry experiment that could only be explained by nuclear fusion. But the evidence was noisy, the controls were inadequate, and the signal disappeared when other labs tried to replicate it.

Using a Bayesian framework, even granting generous likelihood ratios:
- P(observed heat | cold fusion real) ≈ 0.5 (they saw something, even if artifact)
- P(observed heat | cold fusion NOT real) ≈ 0.3 (artifacts and measurement errors are common)

```
P(cold fusion real | observed heat) = (0.5 × 0.0001) / [(0.5 × 0.0001) + (0.3 × 0.9999)]
                                     ≈ 0.00005 / 0.3
                                     ≈ 0.00017 ≈ 0.017%
```

Even with a seemingly positive experimental result, the astronomically low prior on cold fusion meant the posterior probability remained vanishingly small. The scientific community, correctly applying Bayesian reasoning implicitly, rejected the claim within months. The subsequent replication failures confirmed this.

This case illustrates **updating too much**: if Fleischmann and Pons had been rational Bayesians, they would have recognized that even exciting experimental data cannot overcome a prior that low without overwhelming evidence from multiple independent sources.

## El caso moderno: las anomalías del modelo estándar

Hoy en día, la física de partículas enfrenta lo que se llama la **"crisis de la significancia estadística"**. En los últimos años, varios experimentos (el momento magnético anómalo del muón, desintegraciones de mesones B, etc.) han mostrado desviaciones sutiles pero persistentes respecto a las predicciones del Modelo Estándar.

¿Cómo debe la comunidad física actualizar sus creencias?

Supongamos que un experimento reporta una anomalía con un **likelihood ratio** de 10 (la evidencia es 10 veces más probable bajo la hipótesis de "nueva física" que bajo el Modelo Estándar). El prior de "nueva física" (antes de este experimento) basado en décadas de fracasos experimentales y la elegancia teórica del Modelo Estándar podría estimarse en perhaps 0.01 (1%).

```
P(nueva física | anomalía) = (10 × 0.01) / [(10 × 0.01) + (1 × 0.99)]
                          = 0.1 / (0.1 + 0.99)
                          ≈ 0.092 ≈ 9.2%
```

Even with a likelihood ratio of 10 — a result that sounds exciting — the posterior probability of new physics is less than 10%, given how skeptical we should be based on historical base rates. This is why physicists demand **5-sigma significance** (likelihood ratios of millions to one) before claiming discovery. Each anomaly observed independently updates the prior further, and when several independent anomalies converge on the same theoretical direction, belief accumulates more substantially.

## La moraleja bayesiana para la ciencia

El teorema de Bayes nos enseña que la ciencia es un proceso de **actualización iterativa y acumulativa** de creencias, no de aceptar o rechazar teorías de golpe. Los elementos clave:

1. **Tasas base importan:** Las teorías que son más "a priori" plausibles (por simplicidad, elegancia, coherencia con conocimientos previos) merecen más peso inicial. Esto no es subjetividad — es epistemic humility ante la historia de la ciencia.

2. **Evidencia única rara vez es suficiente:** Un solo experimento positivo, por impresionante que parezca, tiene likelihood ratios finitos. La ciencia avanza cuando resultados independientes convergen.

3. **El "crédito" de una teoría debe ser proporcional al peso de la evidencia:** Una teoría que sobrevive a miles de experimentos fallidos de refutación merece más crédito que una que simplemente的解释 un resultado.

4. **La reproducibilidad es clave:** Un resultado que no puede ser reproducido por equipos independientes tiene likelihood ratio que colapsa a 1 (la evidencia no es más probable bajo H que bajo ¬H). Bayes no puede salvar lo que no se replica.

El científico ideal, según el framework bayesiano, es aquel que tiene creencias firmes pero no inquebrantables — que actualiza su imagen del mundo con cada nuevo dato, pero que se asegura de que el dato tenga el peso suficiente antes de cambiar de opinión. Es un acto de equilibrio fino entre la apertura al descubrimiento y el escepticismo disciplinado.

Thomas Bayes, si pudiera ver cómo su teorema se aplica en los pasillos de los laboratorios modernos, probablemente tendría una sonrisa. Después de todo, él mismo era un científico: testarudo con sus creencias previas, pero siempre dispuesto a actualizar cuando la evidencia lo mereciera.
