# Filtros Bayesianos de Spam: Cuando Thomas Bayes Limpió Tu Bandeja de Entrada

## El problema del correo no deseado

Cada día se envían más de **347 mil millones de correos electrónicos** en el mundo, y aproximadamente el **45-47%** de todo ese tráfico es spam. Para usuarios individuales y empresas por igual, la pregunta nunca ha sido si recibirás spam, sino si tu filtro será lo suficientemente inteligente para separarlo del correo legítimo sin comerse tus mensajes importantes. Durante décadas,解决这个问题 fue uno de los grandes retos de la ingeniería de software.

Los primeros filtros de spam usaban **reglas heurísticas**: listas de palabras prohibidas, direcciones IP bloqueadas, servidores de correo conocidos por enviar basura. Eran frágiles, fáciles de evadir (solo había que escribir "fr33" en lugar de "free") y requerían actualizaciones manuales constantes. La revolución llegó cuando alguien recordó a un ministro presbiteriano inglés del siglo XVIII.

## Breve biografía de Thomas Bayes

Thomas Bayes (1702-1761) fue un matemático y religioso británico que, tras su muerte, dejó un manuscrito publicado póstumamente con un título que es ya leyenda: *"An Essay Towards Solving a Problem in the Doctrine of Chances"*. En ese ensayo presentaba lo que hoy conocemos como el **Teorema de Bayes**, una fórmula para actualizar la probabilidad de una hipótesis a la luz de nueva evidencia.

La fórmula central es:

```
P(H | E) = [P(E | H) × P(H)] / P(E)
```

Donde:
- `P(H)` es la probabilidad **previa** (prior) de la hipótesis
- `P(E|H)` es la verosimilitud (likelihood) de la evidencia dada la hipótesis
- `P(E)` es la probabilidad marginal de la evidencia
- `P(H|E)` es la probabilidad **posterior** de la hipótesis dado la evidencia

Stephen Stigler, historiador de la estadística, ha argumentado que el verdadero origen del teorema podría atribuirse al matemático francés **Pierre-Simon Laplace**, quien lo redescubrió y expandió de manera independiente. Sin embargo, Bayes lleva el nombre, y su framework es el que underlies los filtros de spam modernos.

## La idea central: clasificación de texto como probabilidad

El insight genius de aplicar Bayes al filtrado de texto es treating cada palabra como una pieza de evidencia independiente que actualiza la probabilidad de que un correo sea spam o no. Si la palabra "viagra" aparece en un correo no solicitado con alta frecuencia, y casi nunca aparece en correo legítimo, entonces ver esa palabra aumenta la probabilidad de que el correo sea spam. Lo mismo con "gratis", "urgente", "limpieza-de-forex", etc.

La fórmula de **Naive Bayes** (llamada "naive" porque asume que las palabras son condicionalmente independientes dado el estado de spam/no-spam, lo cual es una simplificación pero funciona sorprendentemente bien en la práctica) para dos clases es:

```
P(spam | palabras) ∝ P(spam) × ∏ P(palabra_i | spam)
P(no-spam | palabras) ∝ P(no-spam) × ∏ P(palabra_i | no-spam)
```

El clasificador simplemente compara cuál de las dos probabilidades posteriores es mayor.

## Historia: el filtro de Sahami y la era dorada del spam (1998-2002)

El primer filtro Bayesiano práctico para spam fue construido por **Marios Sahami, David Heckerman, Eric Horvitz** y otros investigadores de Microsoft Research en 1998, en un artículo seminal titulado *"A Bayesian Approach to Filtering E-Mail"*. El contexto era urgente: para 1998, el spam representaba ya cerca del 10% del correo electrónico total, y la cifra crecía exponencialmente.

Lo notable del enfoque de Sahami era que usaba un **clasificador bayesiano ingenuo** entrenado con un conjunto relativamente pequeño de ejemplos. El sistema aprendía qué combinaciones de palabras eran más Indicativas de spam. Los investigadores notaron que palabras como "billion", "dollar", "unsubscribe", y "free" eran strong predictors.

## El invento de Paul Graham (2002)

El nombre más asociado con los filtros Bayesianos de spam en la cultura popular es **Paul Graham**, quien en 2002 publicó un artículo court pero enormemente influyente: *"A Plan for Spam"*. Graham era un programmer y empresario conocido por cofounder Y Combinator, pero en ese momento era simplemente alguien que estaba harto del spam.

La propuesta de Graham era elegantemente simple:

1. **Entrena el filtro con correos reales del usuario.** El filtro aprende las palabras específicas que aparecen en el spam que tú recibes y en el correo legítimo que tú consideras importante.
2. **Cada palabra tiene una "solidez"** (strength) basada en su probabilidad condicional: `P(palabra | spam)` vs `P(palabra | no-spam)`.
3. **Combina las "solideces"** de todas las palabras en un correo para calcular una puntuación final de spam.
4. **Si la puntuación supera un umbral**, el correo se clasifica como spam.

Lo que hacía especial el plan de Graham era la personalización: un filtro entrenado con TU correo es mejor que uno genérico porque captura TU definición de spam. Lo que para ti es spam puede no serlo para otro (por ejemplo, correos de tiendas online que sí te interesan).

## Ejemplo numérico completo

Supongamos que tenemos el siguiente corpus de entrenamiento:

**Spam (200 correos):**
- Palabra "gratis": aparece en 120 correos → P(gratis|spam) = 120/200 = 0.60
- Palabra "viagra": aparece en 80 correos → P(viagra|spam) = 80/200 = 0.40
- Palabra "reunión": aparece en 5 correos → P(reunión|spam) = 5/200 = 0.025

**No-spam (300 correos):**
- Palabra "gratis": aparece en 3 correos → P(gratis|no-spam) = 3/300 = 0.01
- Palabra "viagra": aparece en 0 correos → P(viagra|no-spam) = 0/300 = 0
- Palabra "reunión": aparece en 80 correos → P(reunión|no-spam) = 80/300 ≈ 0.267

**Priors:**
- P(spam) = 200/500 = 0.40
- P(no-spam) = 300/500 = 0.60

Recibimos un correo con el texto: **"gratis开会 gratis reunión Viagra"** (usando "开会" como ruido).

Para calcular la puntuaciónspam de cada palabra, usamos la formula naive:

Para "gratis":
```
P(spam|gratis) ∝ 0.40 × 0.60 = 0.24
P(no-spam|gratis) ∝ 0.60 × 0.01 = 0.006
Ratio = 0.24 / 0.006 = 40 → fuerte indicativo de spam
```

Para "viagra":
```
P(spam|viagra) ∝ 0.40 × 0.40 = 0.16
P(no-spam|viagra) ∝ 0.60 × 0 = 0 → Ratio = infinito
→ La palabra "viagra" es un smoking gun de spam
```

Para "reunión":
```
P(spam|reunión) ∝ 0.40 × 0.025 = 0.01
P(no-spam|reunión) ∝ 0.60 × 0.267 = 0.16
Ratio = 0.01 / 0.16 = 0.0625 → indicativo de no-spam
```

El filtro combina todos los tokens. En la práctica se usa una función de combinación (como la media geométrica de los cocientes) para obtener una puntuación entre 0 y 1. Si la puntuación combinada supera ~0.9, el correo se marca como spam.

## La evolución: de Graham a los filtros modernos

Después de 2002, los filtros Bayesianos se volvieron ubicuos en clientes de correo. **SpamAssassin** (open source), **Bogofilter**, **狐狸獭** (Claws Mail), y muchos otros implementaron variantes del esquema de Graham. Apple Mail, Gmail, Outlook — todos incorporate componentes bayesianos en sus filtros.

Pero los spammers no se quedaron quietos. Pronto aprendieron a evadir los filtros:

- **Inserción de palabras legítimas** entre las spam: "gr a t i s" para romper el pattern de "gratis"
- **Cambio ortográfico**: "v1agra", "vìagra", "v-i-a-g-r-a"
- **Mezclar mayúsculas y minúsculas**
- **Usar imágenes** en lugar de texto (los filtros no podían — en ese momento — analizar imágenes)

Los filtros respondieron evolucionando hacia **modelos híbridos**: reglas heurísticas + Bayes + reputación del remitente + verificación SPF/DKIM/DMARC + blacklists en tiempo real. Hoy, Gmail claima tener menos del 0.1% de spam en las bandejas de entrada de sus usuarios.

## Lecciones más amplias

El caso de los filtros Bayesianos de spam es un ejemplo extraordinario de cómo una teoría matemática del siglo XVIII encontró aplicación práctica en un problema del siglo XXI. Hay varias lecciones:

1. **La "ingenuidad" de Naive Bayes es su fortaleza**: asumir independencia condicional es incorrecto en el sentido estricto, pero los resultados prácticos son extraordinariamente buenos. La simplicidad del modelo lo hace rápido, interpretable y entrenable con poca data.

2. **El aprendizaje adaptativo es clave**: a diferencia de las listas negras estáticas, un filtro Bayesiano se personaliza con el uso. Cada vez que el usuario marca un correo como spam o como no-spam, el filtro actualiza sus probabilidades.

3. **El teorema de Bayes es un framework de sentido común formalizado**: cuando不知道怎么matemáticamente actualizar creencias a la luz de evidencia, Bayes nos da el procedimiento correcto. Los ingenieros de spam descubrieron naipes que Bayes ya había sentado hace 250 años.

Así que la próxima vez que un correo tuyo llegue a la carpeta correcta sin que te des cuenta del trabajo que eso tomó, piensa en Thomas Bayes — el ministro que inventó la manera correcta de aprender de la experiencia.
