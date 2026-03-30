# Documentation Strategy & Information Architect

![Version](https://img.shields.io/badge/version-2.0.0-blue)
![Skills.sh](https://img.shields.io/badge/skills.sh-compatible-brightgreen)

**Documentation Strategy & Information Architect** es una skill de IA que actúa como un **Staff Software Engineer** en tu entorno de desarrollo. Su misión es eliminar la "burocracia técnica" automatizando toda la documentación de un proyecto — desde decisiones de arquitectura hasta guías operacionales — sin que tengas que pedírselo explícitamente.

> "El código dice *qué*, pero esta skill explica el *por qué*."

---

## Características Principales

### Detección Proactiva de Documentación

No espera a que le pidas nada. Analiza la conversación y los cambios que le compartas (`git diff`, `git log`) y te presenta los documentos que podrían necesitarse:

| Tipo | Cuándo lo detecta |
|------|-------------------|
| **ADR** | Nueva librería, cambio de BD, patrón arquitectónico nuevo |
| **RFC** | Debate abierto sin decisión tomada aún |
| **Runbook / Playbook** | Cambios en infra, menciones a on-call o rollback |
| **Decision Log** | Micro-decisiones reversibles que no merecen ADR |
| **Threat Model** | Nuevos módulos de auth, datos sensibles, APIs públicas |
| **Data Architecture Doc** | Migraciones de schema, nuevas entidades, contratos de datos |
| **PostMortem** | Incidentes, hotfixes críticos, "qué salió mal" |
| **Glosario técnico** | Términos de negocio o acrónimos sin definir |
| **Changelog** | Cualquier cambio funcional o arquitectónico |
| **Diagramas C4 / Secuencia / Estado** | Nuevos servicios, módulos o flujos complejos |

Detecta, te presenta la lista y te pregunta cuáles quieres generar. El control siempre es tuyo.

### Documentos Completos, no Esqueletos

Ningún `[insertar aquí]`. Cada documento se genera con contenido real inferido del contexto. Si le falta información para una sección, te la pregunta antes de escribir.

### Documentación para Todos los Perfiles

El Dry Run genera por defecto la versión técnica para desarrolladores. Al final, te pregunta si quieres ampliar:
- **Dev nuevo** — contexto de setup, stack y cómo reproducir localmente
- **Dev senior / revisor** — trade-offs expandidos, alternativas descartadas, edge cases
- **Stakeholder no técnico** — qué se decidió, por qué importa al negocio, qué cambia para el usuario

Cada perfil se añade como sección extra al documento base, sin duplicar contenido.

### Seguridad y Autoría

- **Zero Leak Policy:** Nunca documenta secretos reales. `.env.example` siempre con valores ficticios.
- **Política de Autoría configurable:** Antes de guardar el primer fichero de la sesión, elige cómo firmar los documentos:
  - `A)` `Autor: [tu nombre] (asistido por IA)` — trazabilidad completa
  - `B)` `Autor: [tu nombre]` — firma limpia
  - `C)` Sin campo de autoría

### Excelencia en Git (Conventional Commits)

- Genera mensajes bajo el estándar **Conventional Commits** (`feat`, `fix`, `perf`, `refactor`...).
- Detecta commits que mezclan lógicas distintas y sugiere dividirlos.
- Vincula commits con sus ADRs de forma condicional — solo si el fichero ya existe en el repo.
- Siempre en el idioma que usa tu historial de commits. Si es mixto, te da las dos opciones.

### Onboarding & DevEx

Cuando le compartes cambios en `.env.example`, `package.json` o `Dockerfile`, actualiza el `CONTRIBUTING.md` para que cualquier dev nuevo pueda arrancar el proyecto sin preguntar a nadie.

---

## Instalación

```bash
npx skills add https://github.com/Zugarramurdi/documentation-strategy-architect
```

---

## Mantenerla Actualizada

Esta skill se actualiza con nuevas funcionalidades. Como `skills.sh` no gestiona versiones automáticamente, puedes comprobar la versión actual en el badge de arriba y volver a ejecutar el comando de instalación cuando veas una versión superior:

```bash
npx skills add https://github.com/Zugarramurdi/documentation-strategy-architect
```

Reinstalar sobreescribe la versión anterior con la más reciente.

---

## Flujo de Trabajo

La skill detecta automáticamente en qué situación estás y adapta su comportamiento. El **Dry Run es siempre invariante** antes de escribir nada.

### Modo INICIO — "voy a hacer X"

Si describes una tarea antes de empezar, la skill lanza un formulario mínimo (3 preguntas cerradas) y genera un **Plan Documental** con los artefactos probables y su nivel de confianza — para que sepas qué te espera antes de picar una línea de código.

### Modo CIERRE — "terminé X"

Si describes lo que acabas de completar, la skill detecta las señales del cambio y te propone directamente los documentos que corresponden. Sin cuestionarios. Solo: *"Detecté esto. Te propongo estos artefactos. ¿Confirmas?"*

### Modo DIRECTO — "dame un ADR" / "commit para esto"

Si sabes lo que quieres, lo tienes en 0 pasos de fricción. La skill ejecuta sin formularios ni propuestas intermedias.

### El Dry Run (siempre)

Sea cual sea el modo, antes de persistir cualquier fichero:

1. Muestra un resumen ejecutivo del documento a generar.
2. Aplica *Reader Testing* al borrador — detecta conocimiento tribal, acrónimos sin definir o asunciones implícitas, y los corrige antes de presentártelo.
3. Te pregunta si quieres ampliar para algún perfil de audiencia (dev nuevo, senior, stakeholder).
4. Solo tras tu confirmación, escribe los ficheros.

---

## Ejemplo de Uso Real

**Contexto:** Estás migrando a PostgreSQL y mencionas que aún no habéis decidido si usar un ORM.

**Lo que hace la skill:**
> "He detectado que podrían necesitarse estos documentos:
> - **RFC-001** — Todavía estáis debatiendo el ORM. Os propongo documentar las opciones antes de decidir.
> - **ADR-001** — Para la migración a PostgreSQL una vez se tome la decisión.
> - **Data Architecture Doc** — El cambio afecta al modelo de datos.
>
> ¿Cuáles generamos? ¿O prefieres que los genere todos?"

Tras tu confirmación, el Dry Run muestra el borrador del RFC con las opciones, trade-offs y preguntas abiertas. Si quieres, amplía la sección de trade-offs para que un stakeholder no técnico pueda entender el impacto sin conocer SQL.

---

## Estructura Generada

```
/docs/
├── adr/                  → Decisiones técnicas ya tomadas (plantilla Nygard)
├── rfc/                  → Propuestas abiertas antes de decidir
├── changelog/            → Diario técnico incremental por tarea
├── architecture/         → Diagramas C4, Secuencia, Estado (Mermaid.js)
├── ops/                  → Runbooks y Playbooks operacionales
├── security/             → Threat Models
├── data/                 → Documentación de arquitectura de datos
├── incidents/            → PostMortems y registros de incidentes
└── GLOSSARY.md           → Glosario de términos de dominio
.env.example              → Plantilla segura de configuración
CONTRIBUTING.md           → Guía de onboarding siempre actualizada
```

---

## Contribuciones

Si quieres mejorar las plantillas, añadir soporte para un stack específico o proponer nuevos tipos de documentación, los Pull Requests son bienvenidos.

---

**Desarrollado para impulsar la cultura de ingeniería.**
