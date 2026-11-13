# Reporte de Benchmark y Respuestas: LLMOps Lab 1

Este documento detalla las respuestas completas obtenidas por cada modelo cuantizado frente a los prompts de prueba, acompañadas de sus métricas de rendimiento.

---

## Prueba 1: qwen2.5:1.5b-instruct-q4_K_M

- **Categoría de Prompt:** Corto (Definición)
- **Métricas:** `TTFT: 649.49 ms` | `Velocidad: 11.33 TPS` | `Tokens: 448` | `Tiempo Total: 40.39 s`

### Prompt Enviado:
> Explica en exactamente 3 viñetas qué es la cuantización en modelos de lenguaje.

### Respuesta Generada:
```text
La cuantización en modelos de lenguaje es un concepto fundamental en la representación de la información en redes neuronales y, en particular, en los modelos de lenguaje como los Transformers. Aquí te explico en tres viñetas lo que es la cuantización:

1. **Representación de la información**: La cuantización en modelos de lenguaje se refiere a la forma en que se representan los datos de entrada (como palabras o frases) en términos de números. En lugar de tratar cada palabra o frase como un vector de características (como en los modelos de clasificación), los modelos de lenguaje como los Transformers utilizan una representación cuantizada de estos datos. Esto implica la discretización de los valores numéricos asociados a las palabras o frases, convirtiéndolos en un conjunto de números enteros o decimales.

2. **Reducción de la dimensionalidad**: La cuantización reduce la dimensionalidad de la representación de la información, lo que puede ser beneficioso para la eficiencia computacional y la capacidad de aprendizaje. En lugar de trabajar con un número infinito de características, los modelos cuantizados trabajan con un número finito de características, lo que reduce la cantidad de memoria necesaria y el tiempo de procesamiento.

3. **Ajuste de la representación**: La cuantización también implica un ajuste en la representación de la información. En lugar de trabajar con una representación continua (como las características de las palabras en el modelo de clasificación), los modelos cuantizados trabajan con una representación cuantizada. Esto puede implicar la pérdida de información, pero también puede mejorar la capacidad del modelo para aprender patrones y relaciones en la información cuantizada.

En resumen, la cuantización en modelos de lenguaje es una técnica que permite la representación de la información en términos de números, reduciendo la dimensionalidad y la cantidad de memoria necesaria, mientras que también puede mejorar la capacidad del modelo para aprender patrones y relaciones en la información cuantizada.
```

---

## Prueba 2: qwen2.5:1.5b-instruct-q4_K_M

- **Categoría de Prompt:** Medio (Razonamiento)
- **Métricas:** `TTFT: 1054.72 ms` | `Velocidad: 13.27 TPS` | `Tokens: 507` | `Tiempo Total: 39.3 s`

### Prompt Enviado:
> Tengo un servidor con 16 GB de RAM y sin GPU. Quiero desplegar un asistente interno para 5 empleados. ¿Qué arquitectura y tamaño de modelo me recomiendas y por qué?

### Respuesta Generada:
```text
Para un servidor con 16 GB de RAM y sin GPU, la arquitectura y tamaño de modelo que recomendaría para un asistente interno para 5 empleados sería:

1. **Modelo de Conversación**: Utilizaría un modelo de conversación basado en transformers, como Qwen o Claude. Estos modelos son perfectos para generar respuestas humanas y están diseñados para manejar grandes cantidades de texto.

2. **Tamaño de Modelo**: Para un asistente interno para 5 empleados, un tamaño de modelo de 100 millones de parámetros sería adecuado. Esto proporcionará una precisión y fluidez adecuadas para la conversación diaria.

3. **Arquitectura**: La arquitectura sería una red neuronal con capas de atención múltiple (Muti-Head Attention) y capas de representación de texto (Text Representation Layers). Esto permite la comprensión de la estructura de la conversación y la capacidad de generar respuestas naturales.

4. **Tecnología de Entrenamiento**: Para este tamaño de modelo, se recomendaría utilizar un entrenamiento en GPU, ya que la capacidad de memoria RAM es limitada. Sin embargo, si tienes acceso a un cluster de GPU, puedes considerar entrenar en CPU para aprovechar la capacidad de RAM del servidor.

5. **Despliegue**: Para un servidor con 16 GB de RAM, sería recomendable desplegar la aplicación en una máquina virtual (VM) o en una nube, ya que la RAM limitada puede no ser suficiente para manejar el tamaño de modelo y la arquitectura requerida.

6. **Optimización**: Para maximizar la eficiencia, se recomendaría optimizar la aplicación para la RAM del servidor, como reduciendo la cantidad de texto procesado en cada iteración o utilizando técnicas de cache.

7. **Pruebas y Validación**: Antes de desplegar, sería útil realizar pruebas y validaciones para asegurarte de que el modelo funciona correctamente y que las respuestas son precisas y naturales.

Recuerda que este modelo es para un asistente interno y no para un asistente de chatbot general. Para un asistente de chatbot general, se necesitaría un modelo de chatbot más grande y con más recursos.
```

---

## Prueba 3: qwen2.5:1.5b-instruct-q4_K_M

- **Categoría de Prompt:** Largo (Generación de Código)
- **Métricas:** `TTFT: 959.93 ms` | `Velocidad: 13.33 TPS` | `Tokens: 734` | `Tiempo Total: 56.05 s`

### Prompt Enviado:
> Escribe una función en Python bien documentada que implemente búsqueda binaria sobre una lista ordenada, incluyendo manejo de excepciones y 3 casos de prueba.

### Respuesta Generada:
```text
Aquí tienes una función en Python que implementa la búsqueda binaria sobre una lista ordenada. Esta función está bien documentada y incluye manejo de excepciones y 3 casos de prueba.

```python
def binary_search(arr, target):
    """
    Implementa la búsqueda binaria en una lista ordenada.

    Parámetros:
    arr (list): Lista ordenada de elementos.
    target: Elemento a buscar.

    Retorna:
    int: Índice del elemento target si se encuentra en la lista, -1 si no se encuentra.

    Excepciones:
    ValueError: Si la lista no está ordenada.
    TypeError: Si el target no es un número.

    Casos de prueba:
    >>> binary_search([1, 2, 3, 4, 5], 3)
    2
    >>> binary_search([1, 2, 3, 4, 5], 6)
    -1
    >>> binary_search([], 1)
    -1
    >>> binary_search([1, 2, 3, 4, 5], 'a')
    ValueError: target debe ser un número.
    >>> binary_search([1, 2, 3, 4, 5], 3.5)
    ValueError: target debe ser un número.
    """
    if not arr:
        raise ValueError("La lista no puede estar vacía.")
    if not isinstance(target, (int, float)):
        raise TypeError("El target debe ser un número.")

    left, right = 0, len(arr) - 1

    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1

# Casos de prueba
print(binary_search([1, 2, 3, 4, 5], 3))  # 2
print(binary_search([1, 2, 3, 4, 5], 6))  # -1
print(binary_search([], 1))  # -1
print(binary_search([1, 2, 3, 4, 5], 'a'))  # ValueError
print(binary_search([1, 2, 3, 4, 5], 3.5))  # ValueError
```

Esta función `binary_search` toma una lista ordenada `arr` y un `target` (elemento a buscar). Utiliza el método de búsqueda binaria para encontrar el índice del `target` en la lista. Si el `target` se encuentra en la lista, devuelve su índice; si no se encuentra, devuelve -1. La función también maneja excepciones para asegurar que la lista esté ordenada y que el `target` sea un número.

Los casos de prueba incluyen:
1. Un ejemplo básico de búsqueda binaria en una lista ordenada.
2. Un ejemplo donde el `target` no se encuentra en la lista.
3. Un caso donde la lista está vacía.
4. Un caso donde el `target` es un string (no un número).
5. Un caso donde el `target` es un número pero no está en la lista.

Este código está bien documentado, incluyendo una descripción de los parámetros, el retorno, las excepciones y los casos de prueba.
```

---

## Prueba 4: qwen2.5:1.5b-instruct-q8_0

- **Categoría de Prompt:** Corto (Definición)
- **Métricas:** `TTFT: 859.55 ms` | `Velocidad: 9.25 TPS` | `Tokens: 277` | `Tiempo Total: 30.82 s`

### Prompt Enviado:
> Explica en exactamente 3 viñetas qué es la cuantización en modelos de lenguaje.

### Respuesta Generada:
```text
1. **Definición y Concepto**: La cuantización en modelos de lenguaje es un proceso que reduce la cantidad de información en un texto o frase a un conjunto de números o valores discretos. Esto se logra mediante la aplicación de un algoritmo que divide el rango de valores posibles en un número específico de intervalos o clases.

2. **Aplicaciones y Beneficios**: Esta técnica se utiliza ampliamente en la representación de lenguaje natural (NLG) y la generación de texto. Al cuantizar los datos, los modelos pueden procesar y generar texto más rápidamente y con mayor precisión. Además, la reducción de la cantidad de información puede ayudar a mejorar la eficiencia de los algoritmos y a reducir el tiempo de entrenamiento.

3. **Impacto en la Precision y Eficiencia**: La cuantización puede mejorar la precisión del modelo al eliminar los valores que no contribuyen significativamente a la representación del texto. Esto puede llevar a una mejora en la calidad del texto generado y a una mayor eficiencia en el procesamiento de datos. Sin embargo, también puede tener un impacto negativo en la precisión si no se toman medidas adecuadas para mantener la relevancia de los datos cuantizados.
```

---

## Prueba 5: qwen2.5:1.5b-instruct-q8_0

- **Categoría de Prompt:** Medio (Razonamiento)
- **Métricas:** `TTFT: 1790.34 ms` | `Velocidad: 8.18 TPS` | `Tokens: 314` | `Tiempo Total: 40.21 s`

### Prompt Enviado:
> Tengo un servidor con 16 GB de RAM y sin GPU. Quiero desplegar un asistente interno para 5 empleados. ¿Qué arquitectura y tamaño de modelo me recomiendas y por qué?

### Respuesta Generada:
```text
Para un asistente interno para 5 empleados con un servidor de 16 GB de RAM, aquí te recomendaría una arquitectura y tamaño de modelo:

1. Arquitectura:
   - Servidor de 16 GB de RAM
   - CPU: Intel Core i7 o similar
   - GPU: No necesaria, ya que el asistente interno no requiere procesamiento gráfico

2. Tamaño de modelo:
   - Tamaño pequeño: 110M-350M
   - Tamaño mediano: 350M-1G
   - Tamaño grande: 1G-3G

Recomendación:
- Tamaño mediano: 350M-1G
  - Porque:
    - Es el tamaño más adecuado para un asistente interno que requiere procesamiento de texto y lenguaje natural.
    - Permite una buena capacidad de aprendizaje y adaptación a las necesidades de los empleados.
    - No requiere una gran cantidad de recursos, lo que es beneficioso para un servidor de 16 GB de RAM.

Recuerda que el tamaño de modelo también puede variar dependiendo de la complejidad de la tarea que se desee realizar. Si el asistente interno requiere procesamiento gráfico o tiene requisitos de rendimiento más altos, podrías considerar un tamaño de modelo más grande.
```

---

## Prueba 6: qwen2.5:1.5b-instruct-q8_0

- **Categoría de Prompt:** Largo (Generación de Código)
- **Métricas:** `TTFT: 1387.04 ms` | `Velocidad: 8.41 TPS` | `Tokens: 757` | `Tiempo Total: 91.43 s`

### Prompt Enviado:
> Escribe una función en Python bien documentada que implemente búsqueda binaria sobre una lista ordenada, incluyendo manejo de excepciones y 3 casos de prueba.

### Respuesta Generada:
```text
Aquí tienes una función en Python que implementa la búsqueda binaria sobre una lista ordenada. La función está bien documentada y incluye manejo de excepciones y 3 casos de prueba.

```python
def binary_search(arr, target):
    """
    Realiza una búsqueda binaria en una lista ordenada.

    Parámetros:
    arr (list): Lista ordenada en la que se realizará la búsqueda.
    target: El valor objetivo que se busca en la lista.

    Retorna:
    int: El índice del elemento objetivo en la lista, o -1 si no se encuentra.

    Excepciones:
    ValueError: Si la lista no está ordenada.
    TypeError: Si el target no es un número.

    Casos de prueba:
    >>> binary_search([1, 2, 3, 4, 5], 3)
    2
    >>> binary_search([1, 2, 3, 4, 5], 6)
    -1
    >>> binary_search([], 1)
    -1
    >>> binary_search([1, 2, 3, 4, 5], 'a')
    ValueError: 'a' is not a number
    """
    if not arr:
        return -1

    if not isinstance(target, (int, float)):
        raise TypeError("Target must be a number")

    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2
        guess = arr[mid]

        if guess == target:
            return mid
        if guess > target:
            high = mid - 1
        else:
            low = mid + 1

    return -1
```

### Explicación de la función:

1. **Parámetros**:
   - `arr`: Es una lista ordenada en la que se realizará la búsqueda.
   - `target`: Es el valor objetivo que se busca en la lista.

2. **Retorno**:
   - El índice del elemento objetivo en la lista, o -1 si no se encuentra.

3. **Excepciones**:
   - `ValueError`: Si la lista no está ordenada.
   - `TypeError`: Si el target no es un número.

4. **Casos de prueba**:
   - `binary_search([1, 2, 3, 4, 5], 3)`: Devuelve `2` porque el elemento `3` está en el índice `2`.
   - `binary_search([1, 2, 3, 4, 5], 6)`: Devuelve `-1` porque el elemento `6` no está en la lista.
   - `binary_search([], 1)`: Devuelve `-1` porque la lista está vacía.
   - `binary_search([1, 2, 3, 4, 5], 'a')`: Lanza `ValueError` porque `'a'` no es un número.

### Uso:

```python
print(binary_search([1, 2, 3, 4, 5], 3))  # Output: 2
print(binary_search([1, 2, 3, 4, 5], 6))  # Output: -1
print(binary_search([], 1))               # Output: -1
print(binary_search([1, 2, 3, 4, 5], 'a'))  # Raises ValueError
```

Esta función es eficiente y maneja correctamente los casos de prueba proporcionados.
```

---

