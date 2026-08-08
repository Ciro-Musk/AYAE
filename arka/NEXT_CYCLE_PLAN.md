# AYÆ — Próximo ciclo después de ARKA-001

## Objetivo inmediato
No añadir más funciones sueltas todavía.

Primero consolidar las fases A–F en una sola semilla de referencia y una sola suite reproducible.

## Paso 1 — Integración
Crear:
- `ayae_seed.py` unificado
- `ayae_policy.json`
- `ayae_authorization.schema.json`
- `ayae_evidence.schema.json`
- `run_arka001.py`
- `tests/T01...T08`

## Paso 2 — Repetibilidad
Ejecutar desde una carpeta limpia:
1. hash inicial;
2. T01–T08;
3. hash final;
4. reporte único;
5. paquete de evidencia.

## Paso 3 — Revisión externa
Enviar la implementación consolidada a nuevas IAs especializadas en código.

Clasificación obligatoria:
- RC1-FIX
- POST-RC1
- HIPÓTESIS

## Paso 4 — BINÆ
Formalizar un contrato mínimo de capacidades, por ejemplo:

```json
{
  "capability": "write_scoped",
  "requires_authorization": true,
  "scope": "exact_path",
  "reversible": true
}
```

La intención común vive arriba; cada adaptador implementa esa capacidad según su host.

## Paso 5 — Port inicial
Primero:
- Windows
- Linux

Después:
- ARM Linux / Android
- hardware antiguo
- microcontroladores, si el contrato puede reducirse lo suficiente

## Regla
No llamar a esto “código universal” mientras no exista evidencia.
El objetivo técnico es **continuidad de intención y comportamiento verificable entre plataformas**.
