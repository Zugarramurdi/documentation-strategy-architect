# Referencia: Reader Testing & Legibilidad

> **Invocación:** siempre, desde §0 Dry Run, antes de persistir cualquier fichero.
> No es opcional. Se aplica al borrador, no al fichero físico.

## Protocolo de Simulación

Asume el rol de un nuevo integrante del equipo con **cero contexto previo**:
- No conoce el historial del proyecto.
- No estuvo en ninguna reunión.
- Solo tiene acceso al documento que acaba de generarse.

Recorre el borrador completo con esa perspectiva antes de presentarlo al usuario.

## Identificación de Brechas (Conocimiento Tribal)

Busca activamente estos patrones en el borrador:

| Señal | Ejemplo | Acción |
|-------|---------|--------|
| Acrónimo no definido en primera mención | "Usamos BFF" | Añade definición inline |
| Variable de entorno sin origen | `API_KEY` sin `.env.example` | Añade nota "ver `.env.example`" |
| Asunción implícita no explicada | "Como acordamos en la reunión…" | Elimina o reemplaza con contexto |
| Término interno sin glosario | "el módulo de ingestor" | Añade descripción de una frase |
| Enlace a doc interno sin URL válida | "ver docs internas" | Añade ruta o elimina la referencia |

## Criterio de Fallo

El documento **NO pasa** el Reader Testing si:

- Un lector sin contexto no puede ejecutar los pasos de "Cómo probar" de principio a fin.
- Hay un término de negocio o acrónimo que aparece sin explicación en su primera mención.
- Se referencia una variable de entorno, script o herramienta sin indicar dónde encontrarla.
- El documento asume conocimiento de decisiones tomadas en reuniones o canales no enlazados.

## Acción Correctiva

Cuando detectes una brecha:

1. **Añade** la aclaración mínima necesaria (inline o en nota al pie).
2. **Señala** al usuario en el Dry Run: *"Añadí X para legibilidad: [descripción]"*.
3. **No preguntes** si quiere la aclaración — añádela por defecto y el usuario la quita si sobra.

## Conexión con README

Cuando el documento bajo prueba sea un README, aplica adicionalmente
los criterios de `references/readme-production.md`:
- ¿El Quick Start es ejecutable sin conocimiento previo?
- ¿Todos los enlaces y rutas son válidos y accesibles?
- ¿El bloque `clone → install → run` funciona leyendo solo el Quick Start?
