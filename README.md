# 🌳 Árboles de Decisión: Métricas de Selección y Construcción Paso a Paso

Este repositorio contiene ejercicios prácticos y guías metodológicas sobre la construcción de **Árboles de Decisión**. Se aborda desde el cálculo fundamental de impureza hasta la selección óptima de atributos mediante la **Entropía de Shannon** y la **Ganancia de Información (Information Gain)**.

## 📐 Conceptos Teóricos Fundamentales

Para determinar la mejor forma de dividir un conjunto de datos y tomar decisiones en modelos supervisados, se aplican tres métricas clave:

### 1. Entropía H(S)
Mide la **incertidumbre o desorden** de un conjunto de datos S.
* Un valor de 1 indica **máxima impureza** (ejemplo: 50% de probabilidad para cada clase).
* Un valor de 0 indica **pureza total** (todos los ejemplos pertenecen a una misma clase).

**Fórmula:**
`H(S) = - ∑ [ p_i * log2(p_i) ]`

### 2. Entropía Ponderada H_ponderada(S, A)
Mide la incertidumbre remanente tras dividir el conjunto de datos S utilizando los valores de un atributo A. Calcula el promedio ponderado de la entropía de cada subconjunto según su proporción de datos.

**Fórmula:**
`H_ponderada(S, A) = ∑ [ (|S_v| / |S|) * H(S_v) ]`

### 3. Ganancia de Información IG(S, A)
Representa la **reducción de incertidumbre** lograda al clasificar por el atributo A. El atributo con la **mayor ganancia de información** se selecciona como el **nodo raíz** o nodo de corte principal.

**Fórmula:**
`IG(S, A) = H(S) - H_ponderada(S, A)`

📚 Casos de Estudio Incluidos
📄 Caso 1: Evaluación de Métricas de Impureza (Métricas para construir árboles de decisión.pdf)
Problema: Evaluar si la variable Edad es adecuada para predecir la compra de un producto en una muestra de 10 clientes (5 Compran / 5 No Compran).

Entropía Inicial H(S): 1.0000 (Incertidumbre máxima).

Entropías de Subconjuntos: H(Joven) = 0.8113 y H(Mayor) = 0.9183.

Ganancia de Información: IG(S, Edad) = 0.1245.

Conclusión: Partiendo de una entropía general de 1, el atributo Edad es útil para dividir el conjunto de datos ya que genera una ganancia de información positiva (0,1245), demostrando que reduce la incertidumbre del conjunto original de 1 a 0,8755 aproximadamente.

📄 Caso 2: Construcción Completa de Árbol (Árbol de Decisión.pdf)
Problema: Clasificar si 10 clientes de una empresa de telecomunicaciones aceptarán una oferta comercial evaluando tres atributos: Edad, Uso de Datos y si Tiene Línea Fija.

Comparativa de Atributos:

Tiene Línea Fija: Entropía Ponderada = 0.0000 | Ganancia de Información = 1.0000 (Máxima)

Uso de Datos: Entropía Ponderada = 0.4000 | Ganancia de Información = 0.6000

Edad: Entropía Ponderada = 0.5510 | Ganancia de Información = 0.4490

Resolución:
El atributo Tiene Línea Fija logra una división pura (H = 0) en un solo paso, clasificando el 100% de los datos sin requerir divisiones adicionales.

Estructura del Árbol:

Nodo Raíz: ¿Tiene Línea Fija?

Si la respuesta es "Sí" -> ACEPTA OFERTA (5 de 5 ejemplos, H=0)

Si la respuesta es "No" -> NO ACEPTA OFERTA (5 de 5 ejemplos, H=0)

🔮 Reglas de Extracción de Conocimiento
A partir del modelo resuelto, la predicción se resume en reglas lógicas condicionales:

Regla 1: SI Tiene Línea Fija == "Sí" ==> Predicción: Aceptará la Oferta.

Regla 2: SI Tiene Línea Fija == "No" ==> Predicción: No Aceptará la Oferta.

🛠️ Estructura del Repositorio
Métricas para construir árboles de decisión.pdf: Documento metodológico enfocado en el cálculo matemático paso a paso de H(S) e IG(S, A).

Árbol de Decisión.pdf: Ejercicio práctico interactivo y gráfico con resolución de nodo raíz y árbol final.
