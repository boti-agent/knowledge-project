# Historia del Teorema de Bayes: del puzzle matemático a la herramienta central de la era digital

## Thomas Bayes: el hombre detrás del teorema

Thomas Bayes (1701-1761) fue un ministro presbiteriano y matemático inglés que vivió casi toda su vida en Tunbridge Wells, Kent. Miembro de la Royal Society desde 1742, Bayes fue un pensador original pero nada prolific: solo publicó dos trabajos en vida, ninguno de ellos sobre el teorema que llevaría su nombre. Su obra principal, "An Essay towards solving a Problem in the Doctrine of Chances" (1763), fue publicada póstumamente por su amigo Richard Price, quien encontró el ensayo entre los papeles de Bayes y lo presentó a la Royal Society.

Price, un matemático y filósofo moral igualmente notable, añadió su propia explicación del método y lo presentó como una solución al "problema de la inferencia inversa": dados los eventos observados, ¿cómo inferimos las causas que los produjeron? Este es el problema inverso que Bayes resolvió con su teorema.

El trabajo de Bayes fue pasado por alto durante décadas. No fue hasta los años 1790s, cuando Pierre-Simon Laplace lo rediscover y generalizó independientemente, que la inferencia bayesiana comenzó su carrera como herramienta matemática.

## Pierre-Simon Laplace: el verdadero padre del bayesianismo

Pierre-Simon Laplace (1749-1827) desarrolló lo que ahora se llama inferencia bayesiana de manera completamente independiente y mucho más completa. En una serie de artículos publicados entre 1771 y 1786, Laplace estableció los fundamentos de lo que hoy conocemos como el teorema de Bayes y lo aplicó a problemas astronómicos concretos.

Uno de los casos más famous es su análisis de la duración de la vida: Laplace usó registros demográficos para estimar la esperanza de vida en Francia, aplicando un método que esencialmente calculaba la distribución posterior de la tasa de mortalidad condicional a los datos observados. También aplicó sus métodos al problema de la estimación de la masa de Saturno y a la predicción de eclipses.

Laplace articuló claramente el *principio de indiferencia* (también llamado principio de razón insuficiente): si no hay evidencia que favorezca una hipótesis sobre otra, se deben asignar probabilidades iguales a todas. Este principio conduce directamente a los priors uniformes y fue durante mucho tiempo la base de la "escuela bayesiana objetiva".

La famosa frase frecuentemente atribuida a Laplace —"la probabilidad es el sentido común reducido a cálculo"— captura su visión de que la inferencia probabilística es simplemente una extensión formalizada del juicio humano.

## El siglo de la transición: de Bayes a la estadística moderna

Durante el siglo XIX, el trabajo de Laplace fue continuado por figuras como Carl Friedrich Gauss (quien derivó la distribución normal de errores usando argumentos esencialmente bayesianos), John Venn (lógico y proponente de la interpretación frecuentista), y especialmente John Maynard Keynes, quien en su "Treatise on Probability" (1921) sentó las bases formales para una lógica de la probabilidad.

El siglo XX comenzó con una bifurcación profunda:

**Ronald Fisher y la escuela frequentista**: Fisher desarrolló la estimación por máxima verosimilitud (MLE), las pruebas de significancia, y el diseño de experimentos. Sus métodos se impusieron gradualmente en biología, agricultura y medicina experimental. Fisher *rechazó* explícitamente el bayesianismo, argumentando que la inferencia debe basarse únicamente en los datos observados, no en creencias previas.

**La síntesis Neyman-Pearson**: Jerzy Neyman y Egon Pearson formalizaron las pruebas de hipótesis nulas, los intervalos de confianza, y la distinción entre errores Tipo I y II. Esta metodología se convirtió en el estándar de la ciencia positivista del siglo XX y marginalizó al bayesianismo casi por completo.

Durante este período, el bayesianismo fue relegado a la oscuridad académica. La mayoría de los departamentos de estadística enseñaban solo métodos frequentistas, y las revistas de ciencia aceptaban (y muchas aún aceptan) solo resultados en términos de p-valores y intervalos de confianza.

## La revolución bayesiana: años 1960-1990

El renacimiento del bayesianismo tiene tres padres fundadores reconocibles:

1. **Harold Jeffreys** (1891-1989): su libro "Theory of Probability" (1939, tercera edición 1961) argumentó powerfully por la inferencia bayesiana como fundamento de toda la ciencia. Jeffreys desarrolló los priors de referencia basados en la información de Fisher, intentando crear priors "objetivos" que no influyeran indebidamente en las conclusiones.

2. **Leonard J. Savage** (1917-1971): su "Foundations of Statistics" (1954) intentó derivar la probabilidad subjetiva de los axiomas de la teoría de la decisión. Savage demostró que todo agente que actúa consistentemente (sigue ciertos axiomas de racionalidad) debe comportarse como si tuviera creencias probabilísticas y utilidades, y debe actualizar esas creencias según la regla de Bayes. Este resultado —el teorema de representación de Savage— fue fundamental para justificar el bayesianismo como teoría normativa de la racionalidad.

3. **Dennis Lindley** (1923-2013) y **Jimmy Savage** (rediterr): juntos y por separado, Lindley y otros promoteieron el bayesianismo en el Reino Unido y Estados Unidos, estableciendo programas de investigación bayesiana en universidades clave.

## La revolución computacional: MCMC cambia todo

El obstáculo más práctico para el bayesianismo siempre había sido computacional. Para calcular la distribución posterior P(θ|datos) ∝ P(datos|θ) × P(θ), se necesitaba resolver integrales que en modelos realistas — con cientos o miles de parámetros — eran simplemente intratables analíticamente.

La solución llegó en los años 1990 con los algoritmos MCMC (Markov Chain Monte Carlo):

- **Metropolis-Hastings** (publicado originalmente en 1953 por Metropolis et al., olvidado, y rediscoverto por Hastings en 1970)
- **Gibbs Sampling** (Geman y Geman, 1984)
- **El algoritmo de Slice** (Neal, 1993)

Pero el evento que democratizó completamente la inferencia bayesiana fue la publicación de **WinBUGS** (Bayesian inference Using Gibbs Sampling) en 1997 por el MRC Biostatistics Unit de Cambridge. Por primera vez, investigadores sin doctorado en métodos computacionales podían especificar un modelo bayesiano complejo en un lenguaje declarativo y obtener muestras de la distribución posterior.

Hoy, **Stan** (desarrollado por Gelman, Goodrich, y colaboradores, publicado en 2012) es el estándar de facto. PyMC3, Pyro (Uber), NumPyro, y otros frameworks han seguido, permitiendo inferencia bayesiana como parte de pipelines de machine learning estándar.

## Bayes en la era de los datos

La explosión de datos de los siglos XXI ha sido, paradójicamente, tanto una bendición como un desafío para el bayesianismo:

**Ventaja**: más datos = mejor actualización. Los priors tienen menos influencia cuando hay mucha evidencia, y los métodos bayesianos convergen a las frecuencias observadas.

**Desafío**: los modelos deben escalar. La inferencia variacional (variational inference), los métodos de Laplace aproximados, y las técnicas de inference amortizada (como las que usan redes neuronales para aproximar la inferencia bayesiana) son áreas de investigación activa.

Google usa inferencia bayesiana para actualizar modelos de lenguaje y ranking de búsqueda. Netflix la usa para recomendadores. SpaceX la usa para estimar la posición de cohetes en tiempo real. Los laboratorios farmacéuticos la usan para diseñar ensayos adaptativos.

De ser un interés matemático marginal discutido en la esquina de la filosofía de la ciencia, Bayes se ha convertido en la columna vertebral metodológica de la era de datos. Lo que Price presentó a la Royal Society en 1763 como un puzzle matemático elegante ahora procesa petabytes de información every día, decide治疗方法, filtra correos electrónicos, y aproxima la estructura del lenguaje humano.

No está mal para un ministro que escribió un ensayo solo para sí mismo.
