# Reference: Onboarding y Seguridad de Configuración

## Trigger

Carga este reference cuando detectes: `.env`, `.env.example`, `package.json`,
`docker-compose.yml`, nueva dependencia, nueva variable de entorno, "onboarding",
"secretos", o cambios en configuración del proyecto.

**NO cargar si**: la configuración no cambia y no hay variables nuevas.

---

## Detección de Cambios en Ficheros de Configuración

Al detectar cambios en cualquiera de estos ficheros:

| Fichero | Acción requerida |
|---|---|
| `.env.example` | Verificar que cada variable nueva tiene valor ficticio y descripción |
| `package.json` | Si hay script nuevo o dependencia crítica → actualizar CONTRIBUTING.md |
| `docker-compose.yml` | Si hay nuevo servicio o puerto → documentar en README o CONTRIBUTING.md |

**Flujo para variable de entorno nueva:**
1. Añadir a `.env.example` con valor ficticio (ej. `API_KEY=tu-clave-aqui`)
2. Añadir comentario inline explicando para qué sirve
3. Actualizar la sección "Variables de entorno" en `CONTRIBUTING.md` o README de configuración
4. Verificar que no aparece en ningún commit, log ni doc de decisiones

---

## Seguridad de Secretos (Zero-Leak)

**Regla absoluta:** ningún secreto real en ningún artefacto.

- Documentar **solo** en `.env.example` con valores ficticios
- Formato recomendado: `NOMBRE_VAR=<descripción-breve>` o `NOMBRE_VAR=ejemplo-ficticio`
- **Prohibición explícita:** credenciales reales, tokens, contraseñas o claves
  en documentos `.md`, mensajes de commit, logs ni comentarios de código

Si detectas un secreto real en el diff compartido, **detente** e informa al usuario
antes de continuar con cualquier documentación.

---

## Política de Convenciones Existentes [REACTIVO]

**Solo en el primer uso sobre un repositorio nuevo en la sesión:**

1. Revisar si existen convenciones propias:
   - `git log --oneline -10` → detectar formato de commits habitual
   - Directorio `/docs/adr/` o similar → detectar nomenclatura de ADRs previa
   - `CONTRIBUTING.md` existente → detectar estilo de documentación propio

2. Si las convenciones del repo difieren de los defaults de la skill, **preguntar**:
   > *"He detectado que este repo usa [X]. ¿Adapto el formato al repo o mantengo
   > los estándares de la skill?"*

3. Recordar la elección durante toda la sesión.

**Precedencia P2:** convenciones del repo > defaults de la skill. Si el repo define un estilo, aplicarlo sin preguntar.
