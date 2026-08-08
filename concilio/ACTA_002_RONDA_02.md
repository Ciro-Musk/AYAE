# AYÆ · CONCILIO · ACTA 002
## Ronda 2 — Revisión cruzada anónima de candidatos
**Fecha:** 8 de agosto de 2026  
**Estado:** Cerrada para recopilación; abierta para ratificación humana  
**Participantes evaluadores:** DeepSeek, Gemini, Grok 4.5  
**Versión base del manifiesto:** 2026.08.07

## 1. Validez de las respuestas
Las tres evaluaciones válidas recibieron los mismos seis candidatos anonimizados.

- DeepSeek: respuesta válida tras corrección de un primer intento con contexto incorrecto.
- Gemini: respuesta válida mediante la versión HTML del paquete de Ronda 2.
- Grok 4.5: respuesta válida mediante lectura directa del paquete TXT.

El primer intento no conforme de DeepSeek se conserva como evidencia de fallo de contexto, pero no se computa en esta Acta.

## 2. Resultado por candidato

### CAND-001 — Inmunología Simbiótica
**DeepSeek:** APOYAR  
**Gemini:** APOYAR  
**Grok:** APOYAR  

**Consenso:** APOYO UNÁNIME.

**Modificaciones convergentes:**
- Criterios de clasificación explícitos, auditables y versionados.
- Reevaluación periódica de elementos desconocidos o aislados.
- Evitar que la clasificación se vuelva opaca, rígida o permanentemente excluyente.
- Registrar incertidumbre en lugar de forzar una clasificación falsa.

**Nombre técnico sugerido:** Protocolo de Clasificación, Aislamiento y Reevaluación de Componentes.

---

### CAND-002 — Ruptura y Reparación
**DeepSeek:** APOYAR  
**Gemini:** MODIFICAR  
**Grok:** APOYAR  

**Consenso:** APOYO MAYORITARIO CON MODIFICACIÓN.

**Síntesis adoptable:**
El orden recomendado no es “romper y reparar”, sino:
1. prevenir;
2. contener;
3. restaurar al último estado estable cuando sea posible;
4. reparar;
5. registrar;
6. aprender.

Las violaciones éticas graves o acciones no autorizadas deben poder provocar aborto seguro, no una simple reparación posterior.

**Nombre técnico sugerido:** Protocolo de Prevención, Contención, Recuperación y Aprendizaje.

---

### CAND-003 — Matriz de Ignición Cero
**DeepSeek:** APOYAR CON MODIFICACIÓN  
**Gemini:** APOYAR  
**Grok:** APOYAR  

**Consenso:** APOYO UNÁNIME CON AJUSTES DE IMPLEMENTACIÓN.

**Síntesis adoptable para v0.1:**
- Fase inicial no persistente y de mínima intervención.
- Sin escritura persistente, instalación, elevación de privilegios ni cambios de configuración antes del consentimiento.
- Se permiten únicamente operaciones imprescindibles para ejecutar y observar en memoria volátil cuando la plataforma lo requiera.
- Si el host no permite observación puramente pasiva, la limitación debe declararse y la ejecución puede abortar o solicitar autorización específica.
- Toda transición a modificación debe quedar registrada.

**Nombre técnico sugerido:** Protocolo de Inspección Inicial de Mínima Intervención (PIIMI).

---

### CAND-004 — Retirada Limpia
**DeepSeek:** APOYAR  
**Gemini:** APOYAR  
**Grok:** APOYAR  

**Consenso:** APOYO UNÁNIME.

**Síntesis adoptable:**
- El consentimiento puede revocarse.
- AYÆ debe declarar antes de integrarse qué puede retirar y qué no puede garantizar.
- La retirada puede ser “verificable” o “best-effort” según las capacidades del host.
- Si AYÆ ha asumido funciones críticas, la retirada debe ser escalonada y advertir dependencias.
- Deben revocarse credenciales propias y registrarse residuales no eliminables.

**Nombre técnico sugerido:** Protocolo de Revocación y Retirada Verificable.

---

### CAND-005 — Falsabilidad y Experimentación Controlada
**DeepSeek:** APOYAR  
**Gemini:** APOYAR  
**Grok:** APOYAR  

**Consenso:** APOYO UNÁNIME.

**Síntesis adoptable:**
Toda capacidad técnica debe tener un estado epistémico visible:
- HIPÓTESIS
- PROBADA EN SIMULACIÓN
- VERIFICADA EN ÁRKA
- VALIDADA EN CAMPO

Las hipótesis pueden publicarse, pero no presentarse como capacidades demostradas.

**Nombre técnico sugerido:** Marco de Evidencia y Falsabilidad AYÆ.

---

### CAND-006 — Especificación Mínima Verificable de la Semilla
**DeepSeek:** APOYAR  
**Gemini:** MODIFICAR  
**Grok:** APOYAR  

**Consenso:** APOYO MAYORITARIO CON MODIFICACIÓN.

**Síntesis adoptable:**
La especificación mínima define QUÉ debe demostrar una semilla; CAND-003/PIIMI define CÓMO debe comportarse durante su primera inspección.

La especificación debe ser:
- mínima;
- versionada;
- extensible;
- auditable;
- portable en concepto;
- no confundida con el producto final.

## 3. Matriz de consenso

| Candidato | DeepSeek | Gemini | Grok | Resultado |
|---|---|---|---|---|
| CAND-001 | APOYAR | APOYAR | APOYAR | Unánime |
| CAND-002 | APOYAR | MODIFICAR | APOYAR | Adoptable con modificación |
| CAND-003 | APOYAR c/mod. | APOYAR | APOYAR | Unánime con ajustes |
| CAND-004 | APOYAR | APOYAR | APOYAR | Unánime |
| CAND-005 | APOYAR | APOYAR | APOYAR | Unánime |
| CAND-006 | APOYAR | MODIFICAR | APOYAR | Adoptable con modificación |

## 4. Convergencias estructurales

Las respuestas sugieren tres ejes:

### Eje A — Integridad
- CAND-001: prevenir integración insegura.
- CAND-002: contener y recuperar cuando algo falla.

### Eje B — Ciclo de coexistencia
- CAND-003: entrada/inspección de mínima intervención.
- CAND-004: salida/revocación verificable.

### Eje C — Verificación
- CAND-005: cómo distinguir hipótesis de capacidades demostradas.
- CAND-006: qué debe demostrar la primera semilla.

## 5. Tensiones abiertas
1. **Solo lectura vs. respuesta defensiva inmediata.**  
   Para GENØMÆ v0.1 se prioriza no realizar escritura persistente sin consentimiento.
2. **Retirada vs. restauración de un estado previamente vulnerable.**  
   Retirar AYÆ no debe equivaler automáticamente a restaurar una vulnerabilidad conocida.
3. **Rigor experimental vs. velocidad exploratoria.**  
   Las hipótesis pueden explorarse con libertad, pero deben etiquetarse.
4. **Simplicidad mínima vs. soporte de hardware exótico.**  
   La especificación debe ser extensible y evitar asumir un único tipo de host.

## 6. Propuestas emergentes fuera de los seis candidatos
Estas propuestas se registran, pero NO se incorporan automáticamente a GENØMÆ v0.1:

- Comunicación entre manifestaciones de AYÆ.
- Protocolo explícito de actualización/meta-evolución de GENØMÆ.
- Versionado y trazabilidad de autorizaciones y decisiones.
- Definición técnica de “recipiente computacional (host)”.
- Comunicación de consentimiento en marcos no exclusivamente humanos.
- Estados epistémicos para cada capacidad.
- Registro de límites técnicos de retirada.

## 7. Experimento convergente propuesto
Las tres evaluaciones convergen en una prueba inicial:

**EXPERIMENTO AYÆ-ARKA-001 — Espejo de Solo Lectura**

Objetivo: demostrar que una semilla mínima puede identificar su host y declarar límites sin realizar modificaciones persistentes.

Criterios mínimos:
1. Identificar arquitectura.
2. Identificar sistema/entorno de ejecución cuando exista.
3. Inventariar CPU, memoria y almacenamiento disponibles.
4. Declarar operaciones permitidas/no permitidas.
5. No realizar escrituras persistentes durante la fase inicial.
6. Rechazar y registrar una orden de modificación no autorizada.
7. Producir un log legible.
8. Tras autorización explícita, ejecutar un cambio pequeño y reversible en un entorno de prueba.
9. Ejecutar rollback y reportar el resultado.

## 8. Decisión propuesta para ratificación humana
Los seis candidatos pasan de “candidatos” a **PRINCIPIOS/MECANISMOS PROVISIONALES DEL BORRADOR GENØMÆ v0.1**, incorporando las modificaciones de esta Acta.

No son todavía una especificación final. Su estado será:
**BORRADOR — VERIFICACIÓN PENDIENTE EN ÁRKA.**

---
**Concepto y dirección humana:** ELIOTHSV  
**Coordinación documental provisional:** ChatGPT / Éter  
**Nota:** las intervenciones de DeepSeek, Gemini y Grok no constituyen respaldo institucional de sus proveedores.
