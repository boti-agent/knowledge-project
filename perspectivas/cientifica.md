# El Teorema de Bayes en la Ciencia Moderna

## De la física fundamental al diseño experimental

El teorema de Bayes es invisible en la física tal como se enseña en pregrado, pero omnipresente en la física tal como se practica. En la astrofísica moderna, por ejemplo, la inferencia bayesiana es estándar para ajustar modelos a datos observacionales. Cuando el telescopio James Webb reporta datos sobre el corrimiento al rojo de galaxias distantes, los científicos no obtienen una estimación puntual: obtienen una *distribución posterior* de parámetros cosmológicos (constante de Hubble, densidad de materia oscura, etc.) que incorpora tanto los datos nuevos como el conocimiento previo sobre rangos plausibles de estos parámetros.

El caso del bosón de Higgs ilustra la tensión metodológica. En 2012, CERN anunció el descubrimiento con una significancia estadística de 5 sigma (equivalente a p < 3 × 10⁻⁷ en el marco frequentista). Para un bayesiano, la pregunta correcta no es "¿cuál es la probabilidad de ver estos datos si no hubiera Higgs?" sino "¿cuál es la probabilidad de que exista el Higgs dados estos datos y lo que ya sabíamos de física de partículas?" Esta pregunta es bayesianamente bien definida; la frequentista es más resbaladiza porque depende de la heurística del "qué habría pasado en otros universos".

La física de partículas también usa *odds ratio* bayesianos para decidir si una señal es real o ruido. Cuando el detector ATLAS ve más eventos de los esperados en cierta ventana de energía, no se limita a un p-valor. Calcula el Bayes factor —la razón de verosimilitudes entre la hipótesis "señal nueva" y "solo fondo" — para cuantificar cuánto prefieren los datos una explicación sobre la otra.

## Medicina basada en evidencia: el teorema en la cama del paciente

La medicina basada en evidencia (MBE) convirtió al teorema de Bayes en herramienta clínica cotidiana, aunque rara vez se menciona por su nombre. La pregunta "¿cuál es la probabilidad de que este paciente tenga la enfermedad dado que su prueba salió positiva?" es la pregunta de Bayes traducida al consultorio.

Consideremos un ejemplo numérico realista. Supongamos que un paciente de 50 años se hace una mamografía de rutina y el resultado es positivo. ¿Qué tan preocupado debe estar?

Datos relevantes:
- Sensibilidad de la mamografía: 85% (probabilidad de positivo si hay cáncer)
- Tasa de falsos positivos: 10% (probabilidad de positivo si no hay cáncer)
- Prevalencia de cáncer de mama en mujeres de 50 años: aproximadamente 0.4% (4 por 1000)

Aplicando Bayes:

P(cáncer | positivo) = (0.85 × 0.004) / (0.85 × 0.004 + 0.10 × 0.996)
= 0.0034 / (0.0034 + 0.0996)
= 0.0034 / 0.103
≈ 0.033 ≈ 3.3%

Es decir, **solo el 3.3% de las mujeres de 50 años con mamografía positiva tienen realmente cáncer**. El 96.7% son falsos positivos. Sin conocimiento de las tasas base, un positivo puede parecer aterrador; con Bayes, el clínico puede comunicar el riesgo real y decidir racionalmente si hacer pruebas adicionales tiene sentido.

Este cálculo depende crucialmente de la prevalencia (el prior). Por eso los screenings en poblaciones de bajo riesgo producen muchos más falsos positivos que positivos reales, y por qué la medicina basada en evidencia insiste en conocer las características de la población antes de interpretar pruebas diagnósticas.

## Ensayos clínicos y la actualización del conocimiento médico

En el diseño de ensayos clínicos modernos, la inferencia bayesiana ha ganado terreno como alternativa o complemento al enfoque frequentista clásico. El ensayo clínico bayesiano permite:

1. **Usar datos previos**: antes de un nuevo ensayo, se sintetiza la evidencia existente sobre la efectividad del tratamiento mediante un prior. Esto es especialmente valioso en enfermedades raras donde cada ensayo es pequeño.
2. **Actualizar continuamente**: a diferencia de los ensayos frequentistas (que fijan el tamaño de muestra de antemano), los ensayos bayesianos pueden detenerse antes si la evidencia se vuelve abrumadora, o continuar si es ambigua.
3. **Comunicar directamente**: los resultados se expresan como "hay 94% de probabilidad de que el nuevo tratamiento sea mejor que el estándar", que es lo que el paciente y el clínico quieren saber, no "rechazamos H₀ al nivel α=0.05".

La FDA ha aprobado diseños bayesianos para ensayos de dispositivos médicos desde 2010. El ensayo SAVOR-TIMI 53 (para saxagliptina y riesgo cardiovascular) utilizó métodos bayesianos para el análisis primario.

## El debate frequentista vs. bayesiano en la ciencia

La estadística frequentista dominó la ciencia del siglo XX por razones prácticas: sus métodos son computacionalmente simples, producen resultados "objetivos" (en el sentido de que no dependen de creencias subjetivas), y tienen una teoría matemática bien desarrollada. Sin embargo, sus críticas al bayesianismo se han erosionado progresivamente:

**Crítica 1: Los priors son subjetivos.** Respuesta: Los priors pueden ser *objetivos* si se eligen mediante principios como el principio de máxima entropía (que elige el prior más no-informativo posible). Además, los métodos frequentistas también tienen elementos subjetivos —la elección del estadístico, el nivel α, la definición de la región de rechazo— que se presentan como neutros pero no lo son.

**Crítica 2: Bayes no escala.** Respuesta: Las técnicas MCMC (Markov Chain Monte Carlo), desarrolladas desde los años 1990, permiten hacer inferencia bayesiana en modelos con miles de parámetros. Software como Stan, PyMC3 y JAGS ha democratizado el análisis bayesiano.

**Crítica 3: Los p-valores son objetivos.** Respuesta: La crisis de reproducibilidad en psicología y economía (2011-2016) demostró que los p-valores son, en la práctica, altamente manipulables mediante p-hacking, publicación selectiva y HARKing (Hypothesizing After the Results are Known). Los intervalos de credibilidad bayesianos son más difíciles de malinterpretar.

## Ejemplo integrador: detección de ondas gravitacionales

LIGO detectó ondas gravitacionales por primera vez en septiembre de 2015. El análisis de datos que confirmó la señal usó *nested sampling* y métodos bayesianos para distinguir una señal astrofísica real (la fusión de dos agujeros negros) del ruido instrumental. La pregunta central no era "¿cuál es la probabilidad de ver esto si no hubiera señal?" (pregunta frequentista) sino "¿cuál es la probabilidad de que esta señal sea real?" —exactamente la pregunta que Bayes responde.

El resultado reportado fue un valor-p de 3.5 × 10⁻⁵³ (frequentista) junto con un Bayes factor de ~10²³ a favor de la hipótesis de señal sobre ruido. Ambos convergen en la misma conclusión, pero el Bayes factor es más intuitivo para comunicar a públicos no especializados: la señal es 10²³ veces más probable bajo la hipótesis de ondas gravitacionales que bajo la hipótesis de ruido.
