# Uso de Inteligencia Artificial

## Herramienta utilizada
- **Claude (Anthropic)** - Asistente de codificacion con capacidades agénticas

## Generado con asistencia de IA

### Pipeline de datos
- Notebook `Lab2_Motor_de_busqueda.ipynb` - apoyo para implementar y revisar TF-IDF, BM25 y las metricas de evaluacion desde cero
- Implementacion de BM25: `avgdl`, `idf_bm25(corpus)` y `bm25(doc, q, k1, b)`, junto con `buscar_bm25(consulta, k, k1, b)`
- Implementacion de las metricas de evaluacion: `precision_at_k`, `recall_at_k`, `mrr`, `average_precision` y `ndcg_at_k`
- Implementacion de `evaluar(buscar_fn)` y `tabla_comparativa(...)` para promediar las 5 metricas sobre las consultas etiquetadas y construir la tabla comparativa TF-IDF vs BM25 con columna de mejora porcentual
- Codigo para el barrido de hiperparametros (`k1`, `b`) tanto a nivel de score individual como a nivel de metricas agregadas (NDCG@5, MAP) via grid search con `evaluar()`

### Documentacion
- `AI_USAGE.md` - registro del uso de IA en este laboratorio

---

## Realizado por el estudiante

### Decisiones de diseno
- Decision de mantener `nlp` (spaCy) unicamente en la funcion `preprocesar`, y no en el calculo de TF-IDF, BM25 o las metricas, en linea con la restriccion del lab de no usar librerias de NLP/IR "para resolver" esos algoritmos
- Construccion y etiquetado manual de `qrels` con relevancia graduada (3/2/1) para 5 consultas, incluyendo la justificacion de cada nivel de relevancia segun el contenido real de cada documento del corpus
- Decision final del sistema de produccion (BM25) y de la metrica principal de seleccion (NDCG@5), justificada con base en los resultados reales obtenidos en el notebook

### Analisis
- Interpretacion de la tabla comparativa de metricas (`P@5`, `R@5`, `MRR`, `MAP`, `NDCG@5`) entre TF-IDF y BM25
- Verificacion del comportamiento de BM25 al variar `k1` y `b` contra los resultados reales del notebook, contrastandolos con la hipotesis inicial

### Documentacion academica
- Redaccion final de las respuestas justificadas solicitadas en el notebook, incluyendo el llenado de los valores reales de `(k1, b)` obtenidos del grid search en la respuesta de la pregunta B.4
