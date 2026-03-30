# Reference: Formatos de Modo INICIO y CIERRE

## Modo INICIO — Formato del Plan Documental

Tras recibir las 3 respuestas del formulario, genera el Plan Documental con esta estructura:

```
## Plan Documental: "{descripción de la tarea}"
Basado en: {tipo} | Decisión arq: {respuesta} | Seguridad: {respuesta}

- [CASI SEGURO] {artefacto} — {motivo en una línea}
- [PROBABLE]    {artefacto} — {motivo en una línea}
- [OPCIONAL]    {artefacto} — solo si {condición}
- [SIEMPRE]     Changelog al cerrar la tarea

¿Ajustas algo o empezamos?
```

**Niveles de confianza:**
- `[CASI SEGURO]` — el tipo de cambio lo requiere casi siempre
- `[PROBABLE]` — depende de detalles que aún no conoces
- `[OPCIONAL]` — solo si se cumple una condición específica
- `[SIEMPRE]` — invariante para toda tarea (changelog)

El Plan es una propuesta, no un contrato. El usuario puede ajustar antes de empezar.

---

## Modo CIERRE — Formato de Propuesta Activa

Emite la propuesta con esta estructura. Sin preguntas abiertas antes ni después:

```
📋 Detecté: {tarea inferida} completada.

Propuesta:
→ ✅ {artefacto_1} — {alcance en una línea}
→ ✅ {artefacto_2} — {alcance en una línea}
→ ❓ {artefacto_3} — solo si {condición}

¿Confirmas, ajustas o quitas algo?
```

**Semántica de iconos:**
- `✅` — incluido por defecto, se genera si el usuario confirma sin cambios
- `❓` — requiere confirmación explícita antes de generar

**Regla:** "¿Confirmas, ajustas o quitas algo?" es siempre la última línea. No añadas preguntas adicionales.
