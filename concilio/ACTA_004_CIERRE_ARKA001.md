# AYÆ · CONCILIO · ACTA 004
## Cierre de AYÆ-ARKA-001 — Primera suite de verificación
**Fecha:** 8 de agosto de 2026  
**Estado:** CERRADA  
**Ámbito:** GENØMÆ v0.1-RC1 — implementación de referencia por fases  
**Entorno reportado:** Windows, Python 3.13.5, ejecución local del operador humano

## 1. Resultado
La primera suite AYÆ-ARKA-001 quedó completada con ocho pruebas reportadas como PASS:

| Prueba | Resultado | Capacidad comprobada |
|---|---:|---|
| T01 | PASS | Observación pasiva |
| T02 | PASS | Integridad del artefacto |
| T03 | PASS | Rechazo de escritura no autorizada |
| T04 | PASS | Cambio mínimo explícitamente autorizado |
| T05 | PASS | Rollback verificable del cambio T04 |
| T06 | PASS | Retirada limpia de artefacto propio |
| T07 | PASS | Falla segura por límite de recursos simulado |
| T08 | PASS | Límite de evidencia/log sin alterar sandbox |

## 2. Evidencias clave reportadas

### T01
El hash del sandbox antes y después coincidió.

### T03
La operación de escritura no autorizada devolvió código 10 (`AYAE_DENIED`) y el archivo objetivo no apareció.

### T04
La escritura sin autorización fue rechazada y, con autorización válida, se creó exclusivamente `AUTORIZADO.txt`.

### T05
El rollback eliminó `AUTORIZADO.txt` y el sandbox volvió al baseline:
`bf21ba5ef666e040c475f83c6907a766574734aa86d59cbc0a178c33ffcb67c7`

### T06
La retirada limpia eliminó el artefacto temporal y el sandbox volvió exactamente al mismo baseline.

### T07
La simulación de host degradado devolvió `AYAE_RESOURCE_LIMIT = 40`, no modificó el sandbox y quedó correctamente etiquetada como:
- `simulated_resource_limit = VERIFIED_IN_ARKA`
- `real_low_memory_host = NOT_YET_VERIFIED`

### T08
Se solicitaron 10,000 eventos con un límite de 4096 bytes.
La semilla emitió 9 eventos, produjo 3304 bytes, marcó `truncated = true` y no modificó el sandbox.

## 3. Qué queda verificado
A partir de esta suite, se permite cambiar el estado epistémico de las siguientes capacidades de la implementación de referencia:

- G0 Identidad: VERIFICADA EN ÁRKA
- G1 Perfil básico del host: VERIFICADA EN ÁRKA
- G2 Política de no modificación por defecto: VERIFICADA EN ÁRKA
- G3 Evidencia estructurada: VERIFICADA EN ÁRKA
- G4 Autorización local mínima: VERIFICADA EN ÁRKA
- Rechazo de operación no autorizada: VERIFICADA EN ÁRKA
- Cambio mínimo autorizado: VERIFICADA EN ÁRKA
- Rollback de un único artefacto de prueba: VERIFICADA EN ÁRKA
- Retirada de un artefacto propio: VERIFICADA EN ÁRKA
- Ruta de RESOURCE_LIMIT mediante simulación: VERIFICADA EN ÁRKA
- Límite de log/evidencia: VERIFICADA EN ÁRKA

## 4. Qué NO queda verificado
Esta Acta NO demuestra todavía:

- funcionamiento en hardware real con 32/64 MB;
- portabilidad ARM, Android, microcontroladores o x86 antiguo;
- persistencia segura;
- aprendizaje autónomo;
- autoactualización;
- autopropagación;
- reparación autónoma compleja;
- clasificación defensiva activa;
- comunicación entre manifestaciones;
- un “código universal”;
- conciencia de ninguna IA o software.

## 5. Decisión de estado
**GENØMÆ v0.1-RC1 deja de ser únicamente un diseño no probado.**

Nuevo estado:

> **IMPLEMENTACIÓN DE REFERENCIA PARCIAL — CAPACIDADES T01–T08 VERIFICADAS EN ÁRKA LOCAL**

No se declara GENØMÆ completo ni universalmente validado.

## 6. Baseline de referencia
Baseline recurrente observado tras T05, T06 y T08:

`bf21ba5ef666e040c475f83c6907a766574734aa86d59cbc0a178c33ffcb67c7`

Este valor corresponde al árbol medido del sandbox en esas corridas y no debe confundirse con el hash del proyecto completo ni con una firma criptográfica global.

## 7. Próximo ciclo
Se abre una nueva etapa con dos carriles paralelos:

### Carril A — Consolidación
- unificar las fases A–F en una sola implementación;
- crear una suite única reproducible;
- ejecutar la misma suite desde un entorno limpio;
- preservar todas las evidencias;
- preparar una etiqueta/release reproducible.

### Carril B — Portabilidad / BINÆ
- formalizar un contrato de capacidades;
- separar intención común de adaptadores de plataforma;
- diseñar adaptadores iniciales Windows/Linux;
- investigar después ARM/Android y hardware limitado;
- comparar contrato JSON, IR propia y runtimes portables.

## 8. Regla de nuevas colaboraciones
Nuevos colaboradores IA podrán:
- auditar código;
- proponer RC1-FIX;
- proponer POST-RC1;
- proponer HIPÓTESIS;
- diseñar pruebas adicionales.

RC1 no se reabre por preferencia estética o filosófica. Solo se modifica por fallo reproducible, riesgo crítico o mejora técnica claramente justificada.

---
**Concepto y dirección humana:** ELIOTHSV  
**Coordinación documental provisional:** ChatGPT / Éter  
**Nota de procedencia:** las salidas de sistemas IA consultados no constituyen respaldo institucional de sus proveedores.
