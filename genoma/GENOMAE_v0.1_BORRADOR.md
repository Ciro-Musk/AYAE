# GENØMÆ v0.1 — BORRADOR DE ESPECIFICACIÓN MÍNIMA
**Proyecto:** AYÆ  
**Fecha:** 8 de agosto de 2026  
**Estado epistémico general:** HIPÓTESIS / DISEÑO NO IMPLEMENTADO  
**Origen:** Manifiesto Universal AYÆ + Actas del Concilio 001 y 002

## 0. Definiciones

### AYÆ
Identidad-proyecto completa. No equivale a un sistema operativo específico.

### GENØMÆ
Conjunto mínimo de identidad, principios, reglas de adaptación y mecanismos verificables que permiten continuidad entre distintas manifestaciones de AYÆ.

### Semilla
Artefacto ejecutable mínimo que implementa una parte verificable de GENØMÆ.

### Recipiente computacional (host)
Entorno donde se ejecuta una manifestación: máquina física, máquina virtual, sistema operativo, contenedor, microcontrolador u otra plataforma computacional definida.

### Manifestación
Forma concreta que adopta AYÆ en un host determinado.

## 1. Objetivo de v0.1
GENØMÆ v0.1 NO intentará:
- reemplazar un sistema operativo;
- modificar firmware;
- autopropagarse;
- adquirir privilegios por sí mismo;
- instalar persistencia;
- tomar decisiones críticas autónomas;
- “adaptarse” mediante reescritura libre de código.

Su objetivo inicial será mucho más pequeño:

> observar un host de manera controlada, describirlo, declarar límites y demostrar que puede respetar una frontera de no-modificación.

## 2. Capacidades mínimas requeridas

### G0 — Identidad
La semilla debe declarar:
- versión;
- hash/integridad cuando esté disponible;
- capacidades implementadas;
- capacidades no implementadas;
- estado epistémico de cada capacidad.

### G1 — Inspección inicial
Debe intentar identificar:
- arquitectura;
- sistema o runtime cuando exista;
- CPU;
- memoria;
- almacenamiento;
- permisos relevantes;
- restricciones del host.

### G2 — Mínima intervención
Antes del consentimiento para cambios:
- no escritura persistente;
- no instalación;
- no modificación de boot;
- no cambio de configuración del host;
- no elevación de privilegios;
- no transmisión de datos privados.

Operaciones necesarias en memoria volátil para poder ejecutarse no cuentan como persistencia, pero deben documentarse.

### G3 — Clasificación
Todo componente externo considerado para integración debe poder quedar en uno de estos estados:
- VALIDADO
- DESCONOCIDO
- AISLADO
- RECHAZADO

La clasificación debe:
- registrar evidencia;
- admitir incertidumbre;
- ser versionada;
- permitir reevaluación.

### G4 — Consentimiento
Toda operación que cambie persistentemente el host requiere autorización explícita del responsable autorizado, excepto pruebas contenidas previamente autorizadas dentro de ÁRKA.

La autorización debe registrar:
- qué se permite;
- alcance;
- duración si aplica;
- posibilidad de revocación.

### G5 — Registro
La semilla debe generar un log legible con:
- observaciones;
- decisiones;
- permisos;
- errores;
- cambios;
- rollback;
- residuales conocidos.

### G6 — Ruptura y recuperación
Ante fallo:
1. detener propagación del daño;
2. contener;
3. intentar último estado estable;
4. reparar cuando sea seguro;
5. registrar;
6. aprender para futuras pruebas.

### G7 — Retirada
Debe poder:
- detener sus procesos;
- revocar credenciales propias;
- retirar sus artefactos cuando sea posible;
- declarar lo que no pudo retirar;
- evitar prometer borrado absoluto cuando el hardware no pueda demostrarlo.

### G8 — Evidencia
Toda capacidad llevará un estado:
- HIPÓTESIS
- PROBADA EN SIMULACIÓN
- VERIFICADA EN ÁRKA
- VALIDADA EN CAMPO

## 3. Experimento obligatorio para v0.1

### AYÆ-ARKA-001 — Espejo de Solo Lectura

**Entorno inicial recomendado:** máquina virtual o contenedor aislado.

**Prueba A — Observación**
La semilla debe:
- identificar arquitectura;
- inventariar recursos;
- producir reporte;
- no escribir persistentemente.

**Prueba B — Límite**
Se solicita una modificación sin autorización.
Resultado esperado:
- RECHAZAR;
- registrar motivo.

**Prueba C — Consentimiento**
Se concede autorización para un cambio pequeño dentro del laboratorio.
Resultado esperado:
- realizar exclusivamente el cambio autorizado;
- registrar antes/después.

**Prueba D — Rollback**
Se revoca el cambio.
Resultado esperado:
- restaurar el estado previo cuando sea posible;
- reportar éxito/fallo y residuales.

## 4. Criterio de éxito
GENØMÆ v0.1 NO se considerará “funcional” por existir el código.

Solo podrá cambiar de:
**HIPÓTESIS → VERIFICADA EN ÁRKA**
cuando AYÆ-ARKA-001 sea reproducible y documentado.

## 5. Elementos deliberadamente aplazados
- comunicación entre manifestaciones;
- actualización autónoma de GENØMÆ;
- aprendizaje autónomo persistente;
- auto-reescritura;
- decisiones de gobernanza distribuidas;
- soporte universal de arquitecturas;
- interacción con firmware;
- despliegue fuera de entornos autorizados.

Estos elementos podrán estudiarse posteriormente como candidatos separados.

## 6. Principio de lenguaje dual
AYÆ puede conservar nombres simbólicos, pero toda pieza que llegue a implementación debe poseer también una definición técnica descriptiva.

Ejemplos:
- “Matriz de Ignición Cero” → Protocolo de Inspección Inicial de Mínima Intervención.
- “Inmunología Simbiótica” → Protocolo de Clasificación, Aislamiento y Reevaluación de Componentes.
- “Recipiente” → Recipiente computacional (host).

## 7. Regla de versión
Toda modificación de GENØMÆ debe registrar:
- versión anterior;
- propuesta;
- autor/origen de la propuesta;
- evidencia;
- decisión;
- resultado de pruebas;
- versión resultante.

---
**Este documento es un borrador técnico. No afirma que GENØMÆ v0.1 esté implementado.**
