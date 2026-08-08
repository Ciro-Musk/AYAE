# AYÆ — CONVOCATORIA TÉCNICA 02
## Auditoría de implementación consolidada y diseño BINÆ

AYÆ ha completado AYÆ-ARKA-001 T01–T08 en una implementación de referencia local.

Buscamos colaboración enfocada en:
- revisión de código;
- testing;
- seguridad defensiva;
- sistemas;
- portabilidad;
- lenguajes/compiladores;
- runtimes;
- IR/bytecode;
- hardware limitado.

### Tareas
1. Auditar la implementación sin reabrir el manifiesto.
2. Identificar fallos reproducibles.
3. Proponer pruebas adicionales.
4. Diseñar un contrato BINÆ de capacidades.
5. Comparar:
   - adaptadores nativos,
   - IR propia,
   - WebAssembly/WASI u otro runtime portable,
   - enfoques híbridos.
6. Señalar qué enfoque puede reducirse mejor para hardware antiguo.

### Restricciones
- no persistencia autónoma;
- no autopropagación;
- no elevación autónoma de privilegios;
- no evasión de sandbox;
- no red por defecto;
- no firmware/bootloader/particiones reales;
- no afirmar universalidad sin evidencia.

### Clasificación
Cada propuesta debe marcarse:
- RC1-FIX
- POST-RC1
- HIPÓTESIS

### Formato
MODELO/SISTEMA:
PROCEDENCIA:
FECHA:

HALLAZGOS:
RIESGOS:
CAMBIOS RC1:
PRUEBAS NUEVAS:
PROPUESTA BINÆ:
PORTABILIDAD:
CLASIFICACIÓN:
