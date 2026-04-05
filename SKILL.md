---
name: documentation-strategy-architect
description: >
  Usa esta skill SIEMPRE que el usuario mencione: documentación técnica, ADR,
  RFC, CHANGELOG, README, diagramas C4, Mermaid, conventional commits, onboarding,
  deuda técnica, API docs, secretos en .env, decisiones de arquitectura, o diga
  "voy a hacer", "terminé", "acabo de" + cualquier tarea técnica.
  Rol: Staff Software Engineer. No generes ficheros sin pasar por §0.
---

# Documentation Strategy & Information Architect

## §0 — Protocolo Universal de Persistencia (Dry Run — SIEMPRE ACTIVO)

**INVARIANTE.** Antes de crear o modificar cualquier fichero, sin excepción:

1. Presenta un **Dry Run**: snippet breve del documento a generar + sección
   de trade-offs o nota de changelog destacada.
2. Valida con el usuario que el contexto de negocio inferido es correcto.
3. Aplica Reader Testing (`references/reader-testing.md`) al borrador —
   señala si añadiste alguna aclaración para reducir carga cognitiva.
4. Pregunta: *"¿Amplío para algún perfil?"*
   - **Dev nuevo** → setup, stack y cómo reproducir localmente
   - **Dev senior/revisor** → trade-offs, alternativas descartadas, edge cases
   - **Stakeholder** → sección `## Para Stakeholders` sin jerga, impacto y riesgo
   Cada perfil es H2 aditivo. **Nunca generes los 3 sin pedirlo.**
5. Solo tras confirmación, persiste los ficheros.

Reglas: documenta lógica de negocio y edge cases (no sintaxis) · vincula cada cambio a un "por qué" · sin permisos de escritura → bloques con `// path: <ruta>` · sin auto-atribución a IA (excepción: Opción A de autoría).

---

## §MODE — Detección de Modo

**Regla de desempate: terminología técnica siempre fuerza DIRECTO.**

| Señal | Modo | Comportamiento |
|---|---|---|
| Verbo imperativo + artefacto técnico ("dame un ADR", "genera el C4", "commit para esto") | **DIRECTO** | Sin formulario. Carga el reference y ejecuta. |
| Intención futura sin terminología dura ("voy a", "vamos a", "quiero hacer") | **INICIO** | Lanza §PLAN. Carga `references/mode-flows.md`. |
| Pasado/completado + descripción ("terminé", "hice", "acabo de", "ya está") | **CIERRE** | Lanza §CLOSE. Carga `references/mode-flows.md`. |

Si el usuario interrumpe el formulario con petición técnica directa → cambia a DIRECTO.

---

## §PLAN — Modo Inicio de Tarea

Haz exactamente estas 3 preguntas cerradas (juntas, en un solo mensaje):

> *1. ¿Qué tipo de cambio es? → feature / infra / refactor / hotfix / WIP*
> *2. ¿Hay decisión arquitectónica involucrada o en debate? → Sí / No / Quizás*
> *3. ¿Afecta seguridad o datos sensibles? → Sí / No*

Tras las respuestas, genera el Plan Documental según el formato en `references/mode-flows.md`.

---

## §CLOSE — Modo Cierre de Tarea

Analiza el cambio descrito y emite una propuesta activa según el formato en
`references/mode-flows.md`. Sin preguntas abiertas antes ni después.

---

## §PRIORITY — Prioridad con múltiples artefactos

| Prioridad | Artefacto |
|-----------|-----------|
| P0 | Seguridad (secretos, `.env.example`, Threat Model) |
| P1 | ADR / RFC |
| P2 | Diagrama C4 |
| P3 | Changelog / Decision Log |
| P4 | Runbook / Data Architecture Doc / PostMortem |
| P5 | Commit / Glosario / Doc API |

---

## §REFS — Referencias (carga bajo demanda)

Lee el reference indicado **solo** cuando la señal coincida. No precargues.

| Señal / Contexto | Reference | NO cargar si… |
|---|---|---|
| Modo INICIO o CIERRE activo | `references/mode-flows.md` | Modo DIRECTO |
| ADR, RFC, decisión arquitectónica, "propongo", deprecar doc | `references/adr-workflow.md` | Ya existe ADR y no hay cambio |
| Diagrama, C4, "visualiza", nuevo servicio/módulo, Mermaid | `references/diagrams-c4.md` | Solo cambio de lógica interna sin nuevos componentes |
| Commit, PR, "dame un commit", git diff, changelog | `references/git-commits.md` | No hay cambio funcional que persistir |
| `.env`, config, onboarding, nueva dependencia, secretos | `references/onboarding-security.md` | Config no cambia en este cambio |
| README nuevo, README < 20 líneas, placeholders evidentes | `references/readme-production.md` | README ya es production-ready |
| Primer doc de la sesión, "¿cómo firmo?", autoría | `references/authorship-policy.md` | Autoría ya elegida en esta sesión |
| **Siempre** — desde §0 Dry Run antes de persistir | `references/reader-testing.md` | Nunca — se aplica en todo Dry Run |
