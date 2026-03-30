# Reference: Política de Autoría

## Trigger

Antes de persistir el **primer** fichero de la sesión.  
Señales adicionales: usuario pregunta "¿cómo firmo?", "¿quién firma?", "autoría".

## Pregunta Única (una sola vez por sesión)

> *"¿Cómo quieres firmar los documentos?*
> *A) `Autor: [nombre] (asistido por IA)` — trazabilidad completa*
> *B) `Autor: [nombre]` — firma limpia*
> *C) Sin campo de autoría"*

Recuerda la elección durante **toda la sesión** sin volver a preguntar.

## Cambiar la Elección

Para modificarla en cualquier momento: *"cambia la autoría"*.

## Formato por Tipo de Documento

| Tipo de documento | Formato del campo |
|---|---|
| Con frontmatter YAML (ADR, RFC, spec) | Campo `author:` dentro del bloque `---` |
| Sin frontmatter (Changelog, Runbook, Glosario) | Línea `**Autor:** X` inmediatamente tras el H1 |

### Ejemplos

**Opción A — con frontmatter:**
```yaml
---
title: ADR-005 Migración a PostgreSQL
author: Ana López (asistido por IA)
date: 2026-03-30
---
```

**Opción B — sin frontmatter:**
```markdown
# Changelog: Migración a PostgreSQL

**Autor:** Ana López
```

**Opción C:** no se añade ningún campo de autoría al documento.

## Precedencia

§6.1 — **P2**: si el repositorio ya define una convención de autoría propia
(por ejemplo, un campo `author` fijo en sus ADRs existentes o una plantilla en
`CONTRIBUTING.md`), esa convención prevalece sobre esta política.  
Solo aplica esta política cuando el repo no define autoría propia.

## Regla de No Auto-Atribución

Ningún documento persistido debe mencionar IA, Claude ni esta skill como autor.  
Excepción única: la coletilla `(asistido por IA)` si el usuario eligió Opción A.
