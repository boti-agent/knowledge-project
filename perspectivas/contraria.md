# Críticas al Teorema de Bayes: quando el framework falla o se sobreusa

## La subjetividad de los priors: ¿ciencia o opinión?

La crítica más frecuente y más fundamental contra el bayesianismo es que los priors son inevitavelmente subjetivos, y por tanto la inferencia bayesiana no puede ser objetiva. Dos científicos con priors diferentes ante los mismos datos llegarán a conclusiones diferentes. Si la ciencia aspira a la objetividad, ¿cómo puede aceptar un método que produce resultados basados en opiniones previas?

Esta crítica tiene peso real. Considere el debate sobre la existencia de ondas gravitacionales antes de 2015. Un científico con un prior alto en la relatividad general (digamos, P(existe)=0.99) interpretaría señales ambiguas como evidencia fuerte a favor. Otro con un prior escéptico (P(existe)=0.1) requeriría evidencia mucho más contundente. ¿Quién tiene razón? En principio, la respuesta se encuentra en los datos —pero los datos tardaron 50 años en ser lo suficientemente claros.

El bayesianismo objetivo intenta resolver esto mediante priors de referencia: distribuciones que codifican *minimal prior information*, como el prior de Jeffreys (proporcional a la raíz cuadrada de la información de Fisher). El problema es que estos priors a menudo son improperantes (no normalizan) o producen resultados contraintuitivos en modelos complejos. Y en la práctica, incluso los "objetivos" son elecciones con consecuencias.

E.T. Jaynes (1922-2003), uno de los defensores más elocuentes del bayesianismo, respondió que toda inferencia científica requiere supuestos previos —la diferencia es que el bayesianismo los hace explícitos mientras que el frequentismo los oculta. Esta es una respuesta parcial satisfactoria: hace al bayesianismo *más* honesto, pero no resuelve el problema de que conclusiones diferentes pueden ser igualmente "racionales" según el prior elegido.

## El problema de la referencia clase

Un problema técnico pero importante es la *referencia class problem* (problema de la clase de referencia). Para aplicar Bayes, necesitamos un prior P(θ) que represente nuestra creencia sobre el parámetro antes de ver los datos. Pero ¿a qué *clase* de eventos similares debemos mirar para estimar ese prior?

Frank Knight, en su libro "Risk, Uncertainty and Profit" (1921), distinguió entre riesgo (incertidumbre cuantificable) y ambigüedad (incertidumbre donde las probabilidades ni siquiera están bien definidas). El problema de la clase de referencia es fundamentalmente un problema de ambigüedad: ¿cuál es la frecuencia base correcta para calcular P(enfermedad)?

En el ejemplo de la mamografía, la prevalencia de cáncer de mama en "mujeres de 50 años" depende de la población específica. ¿Mujeres estadounidenses? ¿Mexicanas? ¿De una clínica urbana particular? Los datos demográficos varían. Elegir la referencia clase correcta es, en la práctica, una decisión tan importante como la evidencia misma —y Bayes no nos dice cómo tomar esa decisión.

## El problema de la conjugated y la maldición de la dimensionalidad

La versión "limpia" del teorema de Bayes que se enseña en introductorios —donde se pueden hacer los cálculos a mano con distribuciones conjugadas— es aplicable solo a una tiny fracción de modelos reales. Cuando el modelo tiene cientos de parámetros, la distribución posterior es intratable analíticamente.

Los métodos MCMC han revolucionado la práctica, pero vienen con sus propios problemas:

1. **Convergencia**: ¿cómo sabemos que la cadena ha convergido a la distribución estacionaria y no está atrapada en un modo local? Los diagnósticos estándar (R-hat, ESS) son necesarios pero no suficientes.

2. **Escalabilidad**: MCMC no escala bien a datos masivos. Cada iteración requiere pasar por todos los datos. Métodos como SGD amortizado (amortized inference) o inferencia variacional aproximada son más rápidos pero introducen sesgo.

3. **Especificación del modelo**: especificar un modelo bayesiano completo con priors adecuados para miles de parámetros es un arte que requiere expertise considerable. No es algo que un analyst de datos casual haga en una tarde.

## Sobreutilización y abuso: Bayes como justificación post-hoc

Un riesgo práctico del bayesianismo —y de cualquier framework flexible— es que puede ser usado para justificar prácticamente cualquier conclusión. Si el analyst tiene suficiente libertad para elegir priors, y los priors pueden ser actualizados con verosimilitudes elegidas *ad hoc*, el resultado puede ser Bayesianismo de fachada: una apariencia de rigor cuantitativo sin la substance.

Esto es especialmente problemático en el mundo empresarial y de data science, donde "hicimos un análisis bayesiano" se ha convertido en un shorthand para "usamos probabilidades" sin la metodología rigorosa que Bayes exige.

El caso del problema de la inferencia causal es instructivo. Judea Pearl y otros han argumentado que el bayesianismo puro es insuficiente para la inferencia causal porque no distingue entre correlación y causalidad. Para hacer afirmación causales, se necesitan supuestos adicionales (como los que captura el *do-calculus*). Bayes puede ser el lenguaje de la actualización de creencias, pero no es suficiente por sí solo para derivar relaciones causales de datos observacionales.

## Cuándo Bayes falla en la práctica

Hay situaciones donde el marco bayesiano es genuinamente inadecuado:

**1. Datos muy escasos o zero-shot**: Si no hay datos previos relevantes y el prior debe ser pura conjetura, el resultado bayesiano es esencialmente el prior disfrazado de análisis. En estos casos, el análisis de sensibilidad (ver cómo cambian los resultados con priors diferentes) es obligatorio, no opcional.

**2. Modelos mal especificados**: Si el modelo P(datos|θ) no captura la estructura real de los datos, el posterior será preciso sobre el modelo equivocado. En la práctica, *todos* los modelos están mal especificados en algún grado. Detectar cuándo el mal ajuste es fatal requiere experiencia y herramientas de diagnóstico que van más allá de Bayes.

**3. Decisiones de alta tensión con costos asimétricos**: En decisiones donde un tipo de error es mucho más costoso que otro (por ejemplo, aprobar un medicamento tóxico vs. rechazar uno beneficioso), la decisión óptima no es siempre la que maximiza la precisión del modelo. Requiere una función de utilidad explícita, y la elección de esa función es un acto moral/político, no científico.

**4. Interpretivismo y constructivismo sociales**: En ciencias sociales, muchas veces el objeto de estudio no tiene una "verdad" objetiva independiente del observador. Si la "prevalencia" de un fenómeno social depende de cómo lo definamos, el prior no es una distribución de probabilidad sobre una realidad fija, sino una convención social. Bayes no puede resolver debates ontológicos.

## Aportaciones genuinas de los detractores

Las críticas más constructivas al bayesianismo vienen de tradiciones diversas y han enriquecido tanto la estadística como la filosofía de la ciencia:

**La escuela frequentista** ha desarrollado herramientas que el bayesianismo genuinamente no puede replicar: propiedades asintóticas de estimadores, teoría de decisión minimax, análisis de sensibilidad en términos de cobertura de intervalos de confianza. Estas herramientas son complementarias, no competidoras.

**Los críticos de la "objetividad" bayesiana** (como Stephen Zuckerman y más recientemente David Colquhoun) han contribuido a iluminar la crisis de reproducibilidad en ciencia, argumentando que la proliferación de análisis bayesianos "自由度 flexible" es parcialmente responsable de la falta de replicabilidad. Si el analyst puede especificar priors y stopping rules a voluntad, es fácil encontrar "evidencia" para casi cualquier hipótesis.

**La escuela de inferencia fiducial** (R.A. Fisher, en su etapa tardía) intentó crear un tercer camino entre bayesianismo y frequentismo que preservara la noción de "parámetro fijo pero desconocido" sin requerir priors subjetivos. Aunque la inferencia fiducial tiene problemas técnicos profundos, su motivación —buscar objetividad sin subjetividad— sigue siendo valiosa.

**Los teóricos de la decisión robusta** (como Isaac Levi y Lorenzo G. T. Karma) han argumentado que la elección del prior no debe ser un acto de fe sino un acto de decisión bajo incertidumbre, donde la prudencia exige considerar múltiples priors plausibles en lugar de colapsar a uno.

La lección honesta es que Bayes es un framework extraordinariamente poderoso cuando se aplica a problemas bien definidos con datos adecuados, priors informativas, y modelos correctamente especificados. En esos contextos, domina. En contextos donde esas condiciones no se cumplen —y son más comunes de lo que quisiéramos admitir— sus limitaciones son reales y sus críticos merecen ser escuchados.

La mejor estadística es la que elige el método correcto para el problema específico, sin dogma. A veces ese método es Bayes. A veces no.
