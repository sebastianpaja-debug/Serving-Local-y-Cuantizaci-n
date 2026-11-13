# Entregable Laboratorio 1: Benchmarking de Serving Local y Cuantización

- **Curso:** LLMOps, Serving Local y Arquitecturas RAG
- **Estudiante:** SEBASTIAN CAMILO PAJA BARRIOS
- **Hardware Utilizado:** Intel Core i3-1115G4 (2 núcleos, 3.0 GHz), 8 GB RAM, Windows 11 Home 25H2 con Docker Desktop (WSL2)
- **Fecha:** 13 de noviembre de 2026

---

## Análisis Técnico de Resultados

### 1. Impacto en Memoria (MEM USAGE y KV Cache)
> ¿Cuál fue la diferencia exacta en MB/GB de RAM consumida entre `q4_K_M` y `q8_0` al ejecutar `docker stats`? ¿Por qué el consumo en ejecución supera el tamaño del archivo en disco?

**Respuesta:**
En los dos casos la RAM usada fue mayor que el peso del archivo en disco 986 MB y 1,6 GB. Esto pasa porque además de los pesos, Ollama reserva memoria para el KV Cache, donde guarda la información de los 2048 tokens de contexto que configuramos con num_ctx. A eso se le suman los buffers de cálculo y lo que ya consume el propio servidor de Ollama. Si se aumentara el num_ctx, el KV Cache también crecería y la RAM usada sería todavía mayor.

---

### 2. Ancho de Banda de Memoria y Velocidad (TPS)
> En inferencia sobre CPU, el cuello de botella suele ser el ancho de banda de la memoria RAM. ¿En qué porcentaje aumentó la velocidad (TPS) al pasar de 8 bits a 4 bits?

**Respuesta:**
El modelo de 4 bits fue más rápido en las tres pruebas. En promedio pasé de unos 8,6 tokens por segundo con q8_0 a 12,6 con q4_K_M, casi un 47 % más. En el prompt de código, por ejemplo, subió de 8,4 a 13,3 TPS.

Como el modelo corre solo en CPU, para cada token tiene que leer todos los pesos desde la RAM. El q4 pesa 986 MB y el q8 1,6 GB, entonces con q4 se mueven menos datos y por eso genera más rápido. Mis valores salieron más bajos que los de la guía, porque mi procesador es un i3 de 2 núcleos.

---

### 3. Latencia Inicial (TTFT) y Fase Prefill
> ¿Por qué el `TTFT (ms)` es significativamente más alto en el Prompt Largo que en el Prompt Corto?

**Respuesta:**
El prompt de código tuvo un TTFT más alto que el corto: con q4 fue 960 ms frente a 649 ms, y con q8 1.387 ms frente a 860 ms. Aunque el que más tardó fue el prompt medio, que llegó a casi 1,8 segundos con q8.

Esto pasa porque antes de dar el primer token el modelo procesa todo el prompt de entrada en la fase de Prefill. El prompt medio es el que tiene más texto, ya que describe el servidor, la RAM y los empleados, y por eso se demoró más. El de código pide una respuesta larga, pero la pregunta como tal es más corta. El modelo de 8 bits también tardó más en todos los casos, porque procesa más datos en esa fase.

---

### 4. Calidad vs. Eficiencia en `resultados_benchmark.md`
> Revisando las 6 respuestas completas generadas, ¿hubo alguna degradación perceptible en la lógica del código Python o en el razonamiento generado por el modelo de 4 bits frente al de 8 bits?

**Respuesta:**
type resultados_benchmark.md

---
*Nota: Adjuntar junto con este documento los archivos generados `resultados_benchmark.csv` y `resultados_benchmark.md`.*
