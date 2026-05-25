# Revisión rápida: problemas detectados y tareas propuestas

## 1) Tarea de typo
**Problema detectado:** En el tutorial de `4-paths` aparece la frase "rather on the connection dialog", que es un error gramatical en inglés (debería ser "rather than in the connection dialog" o equivalente).

**Archivo:** `powerquery-docs/samples/trippin/4-paths/readme.md` (línea ~56).

**Tarea propuesta:** Corregir el texto para mejorar claridad y credibilidad del material didáctico.

---

## 2) Tarea de corrección de fallo
**Problema detectado:** En `OnTake` y `OnSkip` se documenta que `count` "should be >= 0", pero no hay validación explícita del parámetro antes de construir el estado. Esto permite valores negativos en la ruta de plegado, lo que puede generar URLs inválidas o comportamiento no esperado según backend.

**Archivo:** `powerquery-docs/samples/trippin/10-tableview1/trippin.pq` (líneas ~153 y ~161 para el contrato; implementación en `OnTake`/`OnSkip`).

**Tarea propuesta:** Añadir guard clauses en `OnTake` y `OnSkip` para rechazar `count < 0` con `error Error.Record(...)` descriptivo.

---

## 3) Tarea de comentario/documentación inconsistente
**Problema detectado:** El comentario del test dice: `test will fail if "Fail on Folding Error" is set to false`, pero el mismo tutorial indica que el default es `False` y que en ese modo las pruebas pueden pasar sin detectar ciertos fallos de folding. El comentario puede confundir sobre cuándo debe fallar realmente el test.

**Archivos:**
- `powerquery-docs/samples/trippin/10-tableview1/trippin.query.pq` (línea ~52).
- `powerquery-docs/samples/trippin/10-tableview1/readme.md` (líneas ~190 y ~487+ contexto de pruebas).

**Tarea propuesta:** Alinear comentario y tutorial con una redacción inequívoca sobre el setting requerido para validar el caso de error por folding.

---

## 4) Tarea de mejora de prueba
**Problema detectado:** `Test.IsFoldingError` compara el mensaje completo del error con un string literal en inglés. Esto vuelve la prueba frágil ante localización, cambios menores del mensaje o variaciones del motor.

**Archivo:** `powerquery-docs/samples/trippin/10-tableview1/trippin.query.pq` (líneas ~84-86).

**Tarea propuesta:** Reescribir la aserción para validar una señal más estable (por ejemplo, tipo/código de error cuando esté disponible, o patrón parcial robusto en lugar de igualdad exacta del mensaje).
