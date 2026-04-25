# Aplicaciones Prácticas del Teorema de Bayes

## Diagnóstico médico: el teorema en la práctica clínica diaria

El ejemplo clásico del diagnóstico médico es quizás la aplicación más inmediata y humanamente significativa del teorema de Bayes. Considere el caso de la enfermedad de Lyme. Un paciente camina por un bosque, nota una picadura de garrapata y desarrolla un sarpullido. Se hace la prueba de ELISA (primer paso diagnóstico) y sale positiva. ¿Cuál es la probabilidad real de tener la enfermedad?

Datos:
- Prevalencia de enfermedad de Lyme en zona endémica tras picadura de garrapata confirmada: ~5% (1 en 20)
- Sensibilidad de ELISA: 70% (detecta 7 de cada 10 casos reales)
- Especificidad de ELISA: 95% (5% de falsos positivos)

P(Lyme | positivo) = (0.70 × 0.05) / (0.70 × 0.05 + 0.05 × 0.95) = 0.035 / 0.0505 ≈ 69%

Sorprendentemente alta. Pero aquí el ELISA es solo tamizaje. La práctica clínica exige confirmación con Western Blot si ELISA es positivo. Con dos pruebas positivas independientes (excepto en el raro caso de sensibilidad condicionada), las probabilidades se actualizan drásticamente:

P(Lyme | ambas positivas) = (0.70 × 0.70 × 0.05) / [combinación compleja] ≈ 93%

Esto explica por qué los protocolos clínicos no tratan sobre la base de una sola prueba positiva: la actualización bayesiana secuencial converge hacia la verdad a medida que se acumulan pruebas independientes.

## Filtros anti-spam: Bayes en tu correo

Los filtros de spam basados en Bayes ("naive Bayes") son una de las aplicaciones más antiguas y exitosas de machine learning probabilístico en producción. El principio es simple: para cada palabra en un correo, calculamos P(spam | contiene esa palabra), combinando la evidencia de todas las palabras del mensaje.

El filtro naive Bayes asume —incorrectamente, pero de forma útil— que las palabras son independientes entre sí. Esta "ingenuidad" es calculable: en lugar de computar P(spam | w₁, w₂, ..., wₙ) directamente (lo que requeriría estimar probabilidades conjuntas para todas las combinaciones posibles de palabras), se asume:

P(spam | w₁, w₂, ..., wₙ) ∝ P(spam) × P(w₁|spam) × P(w₂|spam) × ... × P(wₙ|spam)

Paul Graham, en su influyente essay de 2002 "A Plan for Spam", propuso un sistema donde:
1. Se calculan las frecuencias de cada palabra en correos conocidos como spam y no-spam
2. Se asigna a cada palabra un "spam score" = P(palabra|spam) / (P(palabra|spam) + P(palabra|no-spam))
3. Se combinan los scores de todas las palabras del correo

Los mejores filtros modernos (CRM114, SpamAssassin con módulos bayesianos, los filtros de Gmail) usan variantes de este enfoque, logrando tasas de detección superiores al 99% con tasas de falsos positivos inferiores al 0.1%.

## Machine learning: clasificación y更新 continua

En machine learning contemporáneo, Bayes permea desde los métodos más elementales hasta los más avanzados:

**Naive Bayes para clasificación de texto**: Reuters-21578, 20 Newsgroups, spam detection — todos usan variantes del clasificador naive Bayes. La simplicidad es una ventaja: entrena en segundos con millones de documentos, no requiere GPU, y produce probabilidades calibradas (no solo etiquetas).

**Bayesian Networks (Redes Bayesianas)**: modelos gráficos que representan dependencias condicionales entre variables. Usados en diagnóstico médico (HUGIN), análisis de riesgo financiero (BayesiaLab), y biología computacional (reconstrucción de redes génicas).

**Markov Chain Monte Carlo (MCMC)**: la herramienta computacional que hizo posible la estadística bayesiana moderna. Permite estimar posteriores de modelos complejos —redes neuronales bayesianas, modelos jerárquicos, modelos de mezcla— que serían intratables analíticamente.

**Gaussian Processes**: modelos bayesianos no paramétricos para regresión y clasificación. Dominan en optimización de hiperparámetros (SMBO, basados en Gaussian Processes) y en inferencia de funciones donde se necesita incertidumbre cuantificada.

## Trading algorítmico: cuando los mercados son probabilities

Los fondos de cobertura cuantitativos usan Bayes de formas que raramente se publican, pero el marco conceptual es estándar en gestión de riesgos:

**Actualización de posiciones**: un trader tiene una tesis fundamental ("esta acción vale $X") pero recibe datos nuevos (reporte de ganancias, cambio en tasas de interés). El enfoque bayesiano actualiza la distribución de precio justo en lugar de mantener la tesis original inmutable o descartarla por un mal trimestre.

**Pairs trading**: se identifica una relación de cointegración entre dos acciones. Cuando divergen, se asume que volverán a converger. El tamaño de la posición se determina por el *spread* actual relativo al spread histórico, actualizando dinámicamente según la probabilidad de reversión a la media.

**Ejemplo numérico**: Un fondo tiene un modelo que asigna P(subida >5% en 30 días) = 0.55 para el índice S&P500 (es decir, una ligera ventaja sobre el random walk). Después de tres días consecutivos de caídas de 1% cada uno, ¿debería el gestor aumentar o reducir la exposición?

Si el modelo actualiza el prior inicial P(subida) = 0.50 con los datos nuevos (usando Bayes), y los datos son consistentes con la hipótesis de "caída temporal" vs. "inicio de corrección", la posición podría *aumentarse* si la tesis original se fortalece, no debilitarse emocionalmente por las pérdidas recientes. Este es el principio del "Kelly criterion" bayesiano: tamaño de apuesta proporcional a la ventaja estimada.

## Toma de decisiones empresarial

Las grandes corporaciones usan Bayes implícita y explícitamente en la toma de decisiones:

**A/B testing bayesiano**: en lugar de esperar alcanzar significancia α=0.05 con muestra fija, los tests bayesianos calculan continuamente P(versión A > versión B) y detienen el experimento cuando esta probabilidad cruza un umbral (típicamente 0.95 o 0.99). Amazon, Netflix y Google usan variantes de este enfoque para decidir qué diseño de página, qué algoritmo de recomendación o qué precio maximiza ingresos.

**Estimación de demanda**: antes de lanzar un producto, se tiene un prior sobre la demanda basado en productos similares. Los datos de pre-venta actualizan este prior. Si la demanda observada supera el rango esperado, el prior se actualiza agresivamente y se ajusta la producción.

**Due diligence en M&A**: en fusiones y adquisiciones, los equipos de valoración construyen modelos de flujo de caja descontado con distribuciones de probabilidad para cada supuesto. Los escenarios (base, optimista, pesimista) se actualizan con los resultados de la debida diligencia según su verosimilitud observada.

## El teorema de Bayes y la inteligencia artificial moderna

Los Large Language Models (LLMs) tienen una conexión profunda con Bayes que rara vez se hace explícita. La generación de texto token por token es, en su nivel más fundamental, una inferencia bayesiana: el modelo calcula P(próximo_token | contexto) y muestrea de esa distribución. El preentrenamiento establece priors sobre el lenguaje; el fine-tuning los actualiza; el few-shot prompting proporciona evidencia nueva que el modelo incorpora.

Cuando un LLM dice "given the context, X is most likely", está haciendo approximate inference bayesiana — usando redes neuronales para aproximar la distribución posterior de secuencias de texto coherentes dado un prompt. Los métodos de RLHF (Reinforcement Learning from Human Feedback) son, estructuralmente, un proceso de actualización de priors según preferencias humanas.

La próxima frontera —los modelos que razonan explícitamente, como los que usan chain-of-thought prompting— pueden verse como intentos de hacer que la inferencia bayesiana sea más *transparente*, haciendo visible el proceso de actualización de creencias en lugar de simplemente entregar la distribución final.
