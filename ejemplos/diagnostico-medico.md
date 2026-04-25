# El Teorema de Bayes en el Diagnóstico Médico: Por Qué un Test Positivo No Significa Lo Que Crees

## La intuición que nos engaña

Imagina la siguiente situación: te haces una prueba médica y el resultado llega con dos palabras que pueden cambiar tu vida: **positivo**. Antes de entrar en pánico, respira. La estadística detrás de ese resultado es mucho más sutil de lo que la mayoría de los médicos — y de los pacientes — tienden a pensar. El culpable de la confusión es un concepto contra-intuitivo llamado **tasa base** (base rate), y el instrumento para desenredarlo es el Teorema de Bayes.

Vamos a desglosarlo con números reales.

## Las pruebas médicas imperfectas: sensibilidad y especificidad

Toda prueba de diagnóstico tiene dos parámetros fundamentales que los fabricantes reportan:

- **Sensibilidad (recall):** La probabilidad de que la prueba detecte correctamente a alguien que **sí** tiene la enfermedad. Si la sensibilidad es del 99%, significa que de cada 100 personas enfermas, la prueba detectará 99 (y fallará en 1, lo que se llama **falso negativo**).
- **Especificidad:** La probabilidad de que la prueba identifique correctamente a alguien que **no** tiene la enfermedad. Si la especificidad es del 95%, significa que de cada 100 personas sanas, la prueba correctly identificará 95 como sanas (y erróneamente etiquetará a 5 como enfermas, generando **falsos positivos**).

## El caso concreto: la prueba de VIH

Usemos datos近似ados de pruebas de detección de VIH de tercera generación, ampliamente usadas en laboratorios clínicos:

- **Sensibilidad:** ~99.5% (de 1,000 personas con VIH, 995 darán positivo)
- **Especificidad:** ~99.9% (de 1,000 personas sin VIH, 999 darán negativo)

Esto parece excelente. Pero aquí es donde la tasa base entra en juego.

Supongamos que la prevalencia del VIH en la población general de un país desarrollado es aproximadamente **0.3%** (3 personas por cada 1,000). Ahora imagina que te haces la prueba y das **positivo**. ¿Cuál es la probabilidad real de que tengas VIH?

La respuesta naive sería: "99.5%, porque la sensibilidad es 99.5%." Pero eso es **incorrecto**. Lo que realmente queremos saber es: de todas las personas que dan positivo, ¿cuántas realmente tienen la enfermedad? A eso lo llamamos **valor predictivo positivo (VPP)**.

## Aplicando el Teorema de Bayes

La fórmula de Bayes en este contexto es:

```
P(enfermedad | positivo) = [P(positivo | enfermedad) × P(enfermedad)] / P(positivo)
```

Donde:
- `P(positivo | enfermedad)` = sensibilidad = 0.995
- `P(enfermedad)` = prevalencia (tasa base) = 0.003
- `P(positivo)` = probabilidad total de dar positivo = P(positivo|enfermedad) × P(enfermedad) + P(positivo|sano) × P(sano)

Calculémoslo con una población de **100,000 personas**:

| Grupo | Personas | Positivos | Negativos |
|---|---|---|---|
| Con VIH | 300 | 298.5 (verdaderos +) | 1.5 (falsos -) |
| Sin VIH | 99,700 | 99.7 (falsos +) | 99,600.3 (verdaderos -) |

Total de positivos = 298.5 + 99.7 = **398.2**

De esos 398.2 positivos, solo **298.5** son verdaderos positivos. Por lo tanto:

```
VPP = 298.5 / 398.2 ≈ 74.9%
```

Es decir: **de cada 10 personas que dan positivo, aproximadamente 3 NO tienen VIH**. A pesar de que la prueba tiene una sensibilidad del 99.5% y especificidad del 99.9%.

## ¿Por qué pasa esto?

Porque la **tasa base** (la prevalencia de la enfermedad en la población) es muy baja. Cuando una enfermedad afecta a pocas personas en la población general, incluso una pequeña tasa de falsos positivos puede superar en número a los verdaderos positivos. En nuestro ejemplo, los 99.7 falsos positivos casi igualan a los 298.5 verdaderos positivos.

## El caso de las mamografías

El mismo fenómeno ocurre con las mamografías para detectar cáncer de mama en mujeres jóvenes. En mujeres de 40-49 años sin factores de riesgo específicos, la prevalencia del cáncer de mama es aproximadamente **0.5%**. Con una sensibilidad del 85% y especificidad del 90-95% para mamografías estándar:

En una cohorte de 10,000 mujeres:
- Con cáncer: 50
- Sin cáncer: 9,950

Positivos verdaders: 50 × 0.85 = 42.5
Falsos positivos: 9,950 × (1 - 0.93) ≈ 696.5

VPP ≈ 42.5 / 739 ≈ **5.7%**

Es decir: **de cada 100 mujeres que dan positivo en una mamografía rutinaria, menos de 6 realmente tienen cáncer**. El resto enfrentan la angustia de un falso positivo, con todas las consecuencias psicológicas y médicas que eso implica.

## La paradoja del detector de enfermedades raras

Este patrón se conoce como la **paradoja de las pruebas de detección**: mientras más sensible y específica parezca una prueba, más nos confiamos — pero si la enfermedad es suficientemente rara, los falsos positivos dominan los resultados positivos.

La solución no es hacer pruebas menos sensibles, sino **entender la estadística**. El teorema de Bayes nos dice que para enfermedades muy raras, incluso las mejores pruebas necesitan confirmaciones. Por eso en la práctica médica seria se usa el concepto de **prueba de cribado + prueba confirmatoria**: un test inicial con alta sensibilidad (para no perder casos) seguido de una prueba de confirmación con alta especificidad.

## ¿Qué debe hacer un paciente?

1. **Pregunta la tasa base:** Si te dicen "positivo", pregunta cuál es la prevalencia de esa enfermedad en tu población.
2. **Exige confirmación:** Un resultado positivo en una prueba de cribado debe siempre confirmarse con una segunda prueba independiente.
3. **No asumas certeza:** La palabra "positivo" en medicina nunca significa 100%. Bayes nos recuerda que sin conocer las probabilidades previas, interpretar evidencia nueva es muy difícil.

## Conclusión

El teorema de Bayes no es solo una curiosidad matemática: es una herramienta de supervivencia epistémica. En el contexto médico, puede ser la diferencia entre una decisión informada y un pánico innecesario. La próxima vez que alguien diga "el test dio positivo", recuerda: la respuesta correcta a "¿qué tan probable es que esté enfermo?" depende no solo de la prueba, sino también de **a quién se la hiciste**.
