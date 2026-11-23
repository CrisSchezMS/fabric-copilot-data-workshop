---
name: scd2-databricks
description: Diseña y revisa historificación Slowly Changing Dimension tipo 2 para Databricks, Delta y PySpark con pruebas y reglas explícitas.
---

Lee `standards/scd2.md` y `examples/scd2_reference.py`. Antes de generar SQL
o PySpark identifica tabla origen/destino, claves, columnas históricas,
semántica temporal, valores nulos, duplicados y estrategia de concurrencia.
Si falta una decisión relevante, pregúntala; no inventes un `MERGE` genérico.
Propón una implementación Delta idempotente para los requisitos acordados,
con pruebas para cambios, no cambios, nulos, claves repetidas, late-arriving,
intervalos y dos ejecuciones. Ejecuta las pruebas disponibles y presenta
sus resultados. El algoritmo Python es una referencia local, no es un MERGE
distribuido ni prueba atomicidad/concurrencia en Databricks. No escribas en
ninguna tabla remota sin autorización específica.
