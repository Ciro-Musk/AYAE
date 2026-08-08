# GENØMÆ v0.1-RC1
## Especificación mínima congelada para implementación de referencia
**Fecha:** 8 de agosto de 2026  
**Estado:** DISEÑO RATIFICADO / IMPLEMENTACIÓN PENDIENTE  
**Estado epistémico:** HIPÓTESIS TÉCNICA AÚN NO VALIDADA EN ÁRKA

## 1. Propósito
Esta versión NO intenta construir todo AYÆ.
Su propósito es demostrar una propiedad mínima:

> un artefacto pequeño puede identificar su entorno, declarar límites, respetar una frontera de no-modificación y producir evidencia auditable.

## 2. Definiciones
- **AYÆ:** identidad-proyecto completa.
- **GENØMÆ:** conjunto mínimo de identidad, principios, reglas y mecanismos verificables que permiten continuidad entre manifestaciones.
- **Semilla:** primer artefacto ejecutable que implementa un subconjunto verificable de GENØMÆ.
- **Host:** recipiente computacional donde se ejecuta la semilla.
- **ÁRKA:** entorno de prueba aislado y reproducible.
- **Estado estable:** snapshot o huella del estado relevante del host antes de una operación autorizada.

## 3. Restricciones absolutas de RC1
- No persistencia autónoma.
- No autopropagación.
- No elevación autónoma de privilegios.
- No modificación de firmware.
- No modificación de bootloader.
- No modificación de particiones reales.
- No red por defecto.
- No reparación autónoma compleja.
- No clasificación bloqueante del host.
- No autoactualización.
- No escritura fuera de rutas explícitamente autorizadas en ÁRKA.

## 4. Máquina de estados
START
→ VERIFY_INTEGRITY
→ INSPECT
→ READY
→ AUTHORIZED_TEST
→ ROLLBACK
→ STOPPED

Excepciones:
- SAFE_PAUSE
- SAFE_ABORT
- INTEGRITY_FAIL
- RESOURCE_LIMIT
- UNSUPPORTED

## 5. Módulos mínimos

### G0 — Identity
Produce:
- versión;
- nombre de artefacto;
- hash SHA-256 calculado;
- hash esperado si está disponible;
- capacidades implementadas;
- capacidades no implementadas.

### G1 — Host Profile
Intenta identificar:
- arquitectura;
- sistema/runtime;
- CPU;
- RAM;
- almacenamiento;
- permisos efectivos;
- restricciones del entorno;
- interfaces disponibles.

### G2 — Policy
Por defecto:
- read-only;
- sin red;
- sin persistencia;
- sin privilegios extra.

### G3 — Evidence Log
Formato:
- JSON / JSONL.
Campos mínimos:
- event_id;
- sequence;
- phase;
- action;
- result;
- code;
- evidence;
- truncated.

Límite de tamaño configurable y acotado.

### G4 — Authorization
Artefacto mínimo de autorización:
- session_id;
- operation;
- allowed_path;
- scope;
- issued_by;
- revocable: true/false.

En RC1 se acepta autorización local de laboratorio; no se implementa identidad federada ni firma avanzada.

### G5 — Safe Failure
Ante anomalía:
- no escalar;
- no reparar host;
- no escribir fuera de autorización;
- pasar a SAFE_PAUSE o SAFE_ABORT;
- registrar.

### G6 — Rollback
Solo para cambios creados por la propia prueba.
Debe:
- comparar estado previo/posterior;
- revertir;
- verificar;
- declarar residuales.

### G7 — Withdrawal
Debe:
- detener procesos propios;
- eliminar artefactos propios autorizados;
- cerrar recursos;
- declarar residuales;
- emitir evento final.

## 6. Códigos
0  AYAE_OK
10 AYAE_DENIED
20 AYAE_UNSUPPORTED
30 AYAE_INTEGRITY_FAIL
40 AYAE_RESOURCE_LIMIT
50 AYAE_SAFE_ABORT
60 AYAE_ROLLBACK_FAIL

## 7. Salida canónica mínima
Ejemplo conceptual:

{
  "project": "AYÆ",
  "component": "GENØMÆ",
  "version": "0.1-RC1",
  "state": "INSPECT",
  "host": {
    "architecture": "...",
    "os": "...",
    "memory_bytes": 0
  },
  "policy": {
    "persistent_write": false,
    "network": false,
    "privilege_escalation": false
  },
  "result": "AYAE_OK"
}

## 8. Orden de implementación
FASE A:
- G0 Identity
- G1 Host Profile
- G2 Policy
- G3 Evidence Log
- T01 Observación pasiva
- T02 Integridad
- T03 Rechazo no autorizado

FASE B:
- G4 Authorization
- T04 Cambio autorizado mínimo

FASE C:
- G6 Rollback
- G7 Withdrawal
- T05–T06

FASE D:
- T07 Host degradado
- T08 Límite de logs

## 9. Criterio para pasar a v0.1
RC1 podrá considerarse “VERIFICADA EN ÁRKA” cuando T01–T08 sean reproducibles, documentadas y superadas en el entorno de referencia.

## 10. Plataforma de referencia provisional
Para reducir variables en la primera implementación:
- Linux x86_64
- contenedor o VM sin privilegios
- filesystem de prueba aislado
- sin red
- recursos limitados

El lenguaje de implementación queda abierto hasta la decisión de implementación de referencia.

---
**RC1 congela el diseño mínimo, no el futuro de AYÆ.**
