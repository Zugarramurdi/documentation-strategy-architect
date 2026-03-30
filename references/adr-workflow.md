# Referencia: Flujo ADR / RFC

## Cuándo crear un ADR

| Umbral | Ejemplos |
|--------|----------|
| ✅ SÍ | Nueva dependencia externa, cambio de base de datos, nuevo patrón arquitectónico, decisión difícilmente reversible |
| ❌ NO | Typos, cambios de estilo/formato, tests unitarios sin impacto en API pública, experimentos WIP |

## Regla RFC → ADR

Si la decisión **aún no está tomada**, genera un RFC en `/docs/rfc/RFC-XXX.md`.
Al tomarse la decisión, convierte el RFC en ADR con referencia cruzada: `See: RFC-XXX`.

## Template Nygard

Ruta: `/docs/adr/ADR-XXX.md`

```markdown
# ADR-XXX: {Título descriptivo}

**Estatus:** {Propuesto | Aceptado | Deprecado | Sustituido por ADR-YYY}
**Fecha:** YYYY-MM-DD

## Contexto
{Problema técnico e impacto de la decisión para un dev que no estuvo en la reunión.}

## Decisión
{Qué se decidió. Una oración clara en voz activa.}

## Consecuencias

**Trade-offs positivos (+)**
- {beneficio concreto}

**Trade-offs negativos (−)**
- {coste o riesgo asumido}

## Notas de Implementación
{Pasos clave, configuración o restricciones relevantes para quien implementa.}
```

## Análisis de Regresión

Si código nuevo invalida un ADR o documento existente:
- Márcalo como `[DEPRECATED]` en el campo **Estatus**, o
- Actualízalo inmediatamente con la información correcta.

## Steps to Verify

**Pre-condición:** El ADR existe en `/docs/adr/` y el código asociado está implementado.

**Pasos:**
1. Abre el ADR y lee la sección "Decisión".
2. Verifica que el código refleja exactamente lo descrito.
3. Comprueba que no hay ADRs anteriores contradictorios sin marcar `[DEPRECATED]`.
4. Si existe un RFC de origen, confirma que referencia al ADR (`See: ADR-XXX`).

**Resultado esperado:** ADR y código coherentes; cadena RFC→ADR trazable sin ambigüedades.
**Rollback:** Si el ADR describe algo que ya no aplica, actualiza el campo **Estatus** a `Deprecado` y añade `Sustituido por ADR-YYY` si aplica.
