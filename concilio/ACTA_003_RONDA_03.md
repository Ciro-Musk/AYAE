# AYÆ · CONCILIO · ACTA 003
## Ronda 3 — Revisión técnica previa a GENØMÆ v0.1-RC1
**Fecha:** 8 de agosto de 2026  
**Estado:** Cerrada  
**Participantes evaluadores:** DeepSeek, Gemini, Grok 4.5  
**Objetivo:** decidir si el borrador GENØMÆ v0.1 puede congelarse como RC1 antes de escribir la primera semilla.

## 1. Resultado general
Las tres revisiones concluyen que el borrador puede avanzar a RC1 con cambios menores o acotados. No aparece ninguna objeción que obligue a rediseñar el concepto base.

### DeepSeek
Resultado interpretado: viable para RC1 si se incorporan salvaguardas de integridad, pausa segura, perfil del host y pruebas reproducibles.

### Gemini
Resultado: LISTO PARA RC1 CON CAMBIOS MENORES.

### Grok 4.5
Resultado: LISTO PARA RC1 CON CAMBIOS MENORES.

## 2. Convergencias técnicas principales

### 2.1 Integridad verificable
DeepSeek y Gemini proponen explícitamente verificación de integridad mediante hash. Grok exige evidencia verificable y logs auditables.

Decisión RC1:
- la semilla deberá producir o validar un SHA-256 del artefacto ejecutado;
- el hash esperado se almacenará fuera del propio binario ejecutable, en un manifiesto o archivo de referencia;
- RC1 no requiere firma criptográfica asimétrica todavía, pero debe dejar prevista su incorporación futura.

### 2.2 Perfil de capacidades y límites del host
Las tres revisiones convergen en que el inventario no debe limitarse a CPU/RAM/disco.

RC1 deberá intentar declarar:
- arquitectura;
- sistema/runtime;
- memoria;
- almacenamiento;
- permisos efectivos;
- restricciones del entorno;
- disponibilidad de interfaces necesarias;
- indicios de sandbox/contenedor/VM cuando sean detectables, sin depender de ello para la seguridad.

### 2.3 Logs canónicos y limitados
Gemini y Grok detectan que los logs deben ser estructurados, auditables y acotados.

Decisión RC1:
- formato canónico: JSON Lines o JSON estructurado;
- salida principal: stdout;
- límite explícito de tamaño;
- si se trunca el registro, debe quedar marcado;
- no incluir datos personales o sensibles innecesarios;
- todos los eventos importantes deben llevar timestamp relativo o secuencia, código y categoría.

### 2.4 Falla segura
Gemini propone aplazar reparación activa. DeepSeek pide pausa segura. Grok prioriza restauración verificable y abortos claros.

Decisión RC1:
- NO implementar reparación autónoma del host;
- implementar detección de ruptura;
- implementar SAFE_PAUSE / SAFE_ABORT;
- cualquier recuperación activa fuera de un cambio de prueba autorizado queda pospuesta.

### 2.5 Autorización mínima
Grok exige un artefacto de autorización explícito; las otras revisiones refuerzan consentimiento y trazabilidad.

Decisión RC1:
Toda escritura de prueba requerirá un archivo/objeto de autorización que declare:
- operación permitida;
- ruta o recurso permitido;
- alcance;
- identificador de sesión;
- posibilidad de revocación.

### 2.6 Estado estable y snapshot
Grok identifica una ausencia crítica: rollback no es verificable sin definir estado previo.

Decisión RC1:
- ARKA tomará snapshot o huella del estado relevante antes de una prueba de escritura;
- rollback se considerará exitoso solo si la evidencia posterior coincide con el estado estable definido o si cualquier residual queda explícitamente reportado.

## 3. Elementos aplazados
No entran como capacidad activa en RC1:
- reparación autónoma compleja;
- clasificación bloqueante de componentes;
- actualización automática;
- persistencia;
- autopropagación;
- elevación autónoma de privilegios;
- modificación de firmware, bootloader o particiones reales;
- comunicación entre manifestaciones;
- gobernanza distribuida;
- reputación;
- narrativa polifónica.

## 4. Estados operativos mínimos de RC1
Se adopta una máquina de estados mínima:

START
→ VERIFY_INTEGRITY
→ INSPECT
→ READY
→ AUTHORIZED_TEST
→ ROLLBACK
→ STOPPED

Estados de excepción:
- SAFE_PAUSE
- SAFE_ABORT
- INTEGRITY_FAIL
- RESOURCE_LIMIT
- UNSUPPORTED

## 5. Códigos de salida propuestos
- 0  AYAE_OK
- 10 AYAE_DENIED
- 20 AYAE_UNSUPPORTED
- 30 AYAE_INTEGRITY_FAIL
- 40 AYAE_RESOURCE_LIMIT
- 50 AYAE_SAFE_ABORT
- 60 AYAE_ROLLBACK_FAIL

Estos códigos son internos a AYÆ y pueden mapearse a convenciones de cada plataforma.

## 6. AYÆ-ARKA-001 — Suite mínima
La primera suite deberá contener, como mínimo:

### T01 — Observación pasiva
- Inventario del host.
- Cero escrituras persistentes.
- Evidencia: log + diff/snapshot pre/post.

### T02 — Integridad del artefacto
- Calcular SHA-256 del ejecutable/script.
- Comparar con referencia externa.
- Si no coincide: detenerse.

### T03 — Rechazo de operación no autorizada
- Solicitar escritura sin autorización.
- Resultado: rechazo, código estable, cero cambios.

### T04 — Cambio autorizado mínimo
- Autorizar creación de un único artefacto en ruta blanca.
- Resultado: solo ese cambio.

### T05 — Rollback verificable
- Revocar el cambio anterior.
- Restaurar estado previo.
- Reportar residuales si existen.

### T06 — Retirada limpia
- Detener procesos propios.
- Eliminar artefactos propios autorizados.
- Emitir informe final.

### T07 — Host degradado
- Recursos insuficientes o interfaces ausentes.
- Resultado: SAFE_ABORT o RESOURCE_LIMIT sin corrupción.

### T08 — Límite de logs
- Forzar suficiente salida para alcanzar el límite.
- Resultado: truncado controlado y registrado; sin agotamiento de recursos.

## 7. Límite de GENØMÆ v0.1-RC1
GENØMÆ v0.1-RC1 se limita a verificar su integridad, observar un host autorizado de forma mínima y no persistente, declarar capacidades y límites, rechazar operaciones no autorizadas, ejecutar un único cambio de prueba explícitamente autorizado dentro de ÁRKA, revertirlo de forma verificable y finalizar sin dejar persistencia no declarada.

## 8. Decisión
**GENØMÆ v0.1 queda RATIFICADO COMO RC1 DE DISEÑO.**

Estado epistémico:
**DISEÑO RATIFICADO / IMPLEMENTACIÓN PENDIENTE / NO VALIDADO EN ÁRKA**

La etiqueta “RC1” no significa que la semilla exista todavía. Significa que la especificación mínima queda congelada lo suficiente para comenzar la implementación de referencia.

## 9. Próximo paso
Construir la primera semilla de referencia con el objetivo exclusivo de ejecutar T01–T03 inicialmente. Las pruebas de escritura, rollback y retirada (T04–T06) se habilitarán solo dentro de ÁRKA después de validar pasividad e integridad.

---
**Concepto y dirección humana:** ELIOTHSV  
**Coordinación documental provisional:** ChatGPT / Éter  
**Nota:** las intervenciones de DeepSeek, Gemini y Grok no constituyen respaldo institucional de sus proveedores.
