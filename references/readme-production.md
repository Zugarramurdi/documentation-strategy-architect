# Referencia: README Production-Ready

## Trigger

Carga esta referencia cuando detectes:
- Repo sin README o README vacío
- README < 20 líneas
- Placeholders evidentes: `TODO`, `[descripción]`, `Coming soon`

## Pregunta Única

> ¿Es proyecto nuevo (genero estructura completa) o hay README existente que mejorar (auditoría + mejoras)?

No hagas más preguntas antes de conocer la respuesta.

## 8 Bloques Mínimos Production-Ready

| # | Bloque | Contenido esperado |
|---|--------|--------------------|
| 1 | **Nombre + descripción** | Una frase exacta: qué hace, para quién, en qué contexto |
| 2 | **Badges** | Solo los relevantes: CI, cobertura, versión. Omite los decorativos |
| 3 | **Qué resuelve** | 3-5 bullets: problema que elimina, beneficio clave, diferenciador |
| 4 | **Quick Start** | Prerreqs (versiones exactas) · clone · install · run · resultado esperado |
| 5 | **Variables de entorno** | Tabla críticas + referencia a `.env.example` |
| 6 | **Comandos comunes** | Tabla: comando · descripción · resultado esperado |
| 7 | **Stack tecnológico** | Lista compacta de tecnologías con versiones |
| 8 | **Licencia** | Tipo + enlace a `./LICENSE` |

## Quick Start — Ejemplo de referencia

```bash
git clone https://github.com/org/repo && cd repo
cp .env.example .env
npm install && npm run dev
# Resultado esperado: "Server running on http://localhost:3000"
```

Prerrequisitos van ANTES del bloque bash: `Node 20+, Docker 24+`.

## Reglas de Calidad

- Quick Start ejecutable sin contexto previo: `clone → install → run` sin leer nada más.
- Cada comando documenta su resultado esperado.
- Sin acrónimos sin definir en primera mención (¿lo entendería un dev externo?).
- Sin `TODO`, `WIP` ni placeholders en el output final.
- Ningún enlace que apunte a docs internas sin URL real.

## Flujo

**Proyecto nuevo** → genera estructura completa con smart placeholders; señala qué secciones requieren datos reales.

**README existente** →
1. Auditoría: detecta qué bloques de los 8 faltan o están incompletos.
2. Lista priorizada de mejoras (lo crítico primero).
3. Dry run antes de aplicar.
