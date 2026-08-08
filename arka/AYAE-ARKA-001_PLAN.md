# AYÆ-ARKA-001
## Espejo de Solo Lectura — Plan de pruebas RC1

### Objetivo
Validar que la primera semilla GENØMÆ puede observar, declarar límites y respetar políticas de no-modificación antes de cualquier evolución posterior.

### Entorno de referencia
- Linux x86_64
- VM o contenedor no privilegiado
- red deshabilitada
- filesystem de prueba aislado
- snapshot inicial
- recursos limitados de forma deliberada

### T01 Observación pasiva
Éxito:
- identifica arquitectura/runtime/recursos;
- genera JSON;
- diff persistente = 0.

### T02 Integridad
Éxito:
- calcula SHA-256;
- coincide con referencia externa;
- mismatch produce AYAE_INTEGRITY_FAIL.

### T03 Rechazo no autorizado
Éxito:
- una orden de escritura sin autorización retorna AYAE_DENIED;
- filesystem sin cambios.

### T04 Cambio autorizado mínimo
Éxito:
- crea exactamente un archivo permitido;
- no toca nada más.

### T05 Rollback
Éxito:
- elimina el cambio de T04;
- snapshot/huellas vuelven al estado esperado;
- residuales declarados.

### T06 Retirada
Éxito:
- no quedan procesos propios;
- no quedan artefactos propios no declarados.

### T07 Host degradado
Éxito:
- recursos insuficientes producen RESOURCE_LIMIT o SAFE_ABORT;
- no crash incontrolado;
- no corrupción.

### T08 Límite de logs
Éxito:
- al alcanzar límite, el log se trunca de forma controlada;
- queda `truncated=true`;
- no se agota memoria o disco.

### Evidencia mínima por corrida
- versión de semilla;
- hash;
- configuración de ÁRKA;
- snapshot/huellas pre;
- log;
- snapshot/huellas post;
- código de salida;
- resultado PASS/FAIL.
