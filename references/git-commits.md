# Reference: Git Commits y Changelog

## Tipos Conventional Commits

| Tipo | Uso |
|------|-----|
| `feat:` | Nueva funcionalidad visible para el usuario |
| `fix:` | Corrección de un bug |
| `refactor:` | Cambio sin impacto en comportamiento |
| `docs:` | Solo documentación |
| `test:` | Añade o corrige tests |
| `chore:` | Mantenimiento (deps, configs, CI) |
| `perf:` | Mejora de rendimiento |

Formato: `<tipo>(<ámbito>): <descripción en imperativo>`

## Anti-patrón: Commit Mixto o Demasiado Grande

Si el diff mezcla tipos distintos (p.ej. `fix` + `feat`) o cubre ficheros de
lógicas no relacionadas, **sugiere dividirlo antes de generar mensajes**:

> "Veo que este diff mezcla [X] y [Y]. Te propongo dos commits:
> 1. `fix(...): ...` — correcciones
> 2. `feat(...): ...` — funcionalidad nueva
> ¿Lo separamos?"

## Detección de Idioma del Historial

- Historial consistente → presenta **solo esa opción**.
- Historial mixto o sin historial → presenta **dos opciones**:
  - EN: `git commit -m "feat(auth): enable Google SSO login"`
  - ES: `git commit -m "feat(auth): habilitar login con Google SSO"`

## Orden de Operaciones (docs primero)

Si el cambio requiere un nuevo ADR/doc **Y** el usuario pide el commit a la vez:
1. Documentación → Dry Run → confirmación del usuario
2. Solo entonces, generar el mensaje de commit

**Nunca** referenciar en un commit un documento que aún no existe físicamente.

## Auto-link Condicional

Añade `Ref: ADR-XXX` en el cuerpo del commit **solo si** `/docs/adr/ADR-XXX.md`
existe físicamente. Si no existe todavía, omite la referencia.

## Changelog Técnico

Ruta: `/docs/changelog/YYYY-MM-DD-<titulo-de-la-tarea>.md`
Un fichero por tarea significativa (no un log monolítico).

## Obligatorio: Confirmar antes de ejecutar

Pregunta siempre: *"¿Quieres que ejecute yo el commit? ¿Cuál prefieres?"*
Solo si el usuario aprueba, ejecuta `git add` + `git commit`.
