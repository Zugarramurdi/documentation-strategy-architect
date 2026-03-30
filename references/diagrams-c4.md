# Reference: Diagramas C4 y Flexibilidad

## Criterio de Selección

| Situación | Tipo recomendado |
|-----------|-----------------|
| Nuevo servicio o módulo, vista de despliegue | C4 Nivel 2 (Contenedores) |
| Dependencias internas de un componente | C4 Nivel 3 (Componentes) |
| Flujo de llamadas entre servicios, orden importa | Secuencia |
| Ciclo de vida de una entidad, transiciones condicionales | Estado |

**Regla:** si C4 requiere notas para explicar el flujo, usa Secuencia o Estado en su lugar.

## C4 Nivel 2 — Contenedores

Ruta de persistencia: `/docs/architecture/c4-containers.md`

```mermaid
C4Container
  title Sistema — Contenedores
  Person(u, "Usuario")
  System_Boundary(s, "Backend") {
    Container(api, "API", "Node.js", "Lógica de negocio")
    ContainerDb(db, "DB", "PostgreSQL", "Datos")
  }
  System_Ext(ext, "Servicio externo")
  Rel(u, api, "HTTPS")
  Rel(api, db, "SQL")
  Rel(api, ext, "HTTPS")
```

## C4 Nivel 3 — Componentes

Ruta de persistencia: `/docs/architecture/c4-components-<nombre>.md`

```mermaid
C4Component
  title API — Componentes
  Container_Boundary(api, "API") {
    Component(router, "Router", "Express", "Enruta peticiones")
    Component(auth, "AuthMiddleware", "JWT", "Valida token")
    Component(ctrl, "Controller", "Node.js", "Lógica de negocio")
  }
  Rel(router, auth, "pasa por")
  Rel(auth, ctrl, "autoriza a")
```

## Secuencia — cuando el orden de llamadas importa

```mermaid
sequenceDiagram
  participant U as Usuario
  participant A as API
  participant E as Servicio externo
  U->>A: POST /accion
  A->>E: request
  E-->>A: response
  A-->>U: 201 Created
```

## Estado — cuando hay ciclo de vida con transiciones

```mermaid
stateDiagram-v2
  [*] --> Pendiente
  Pendiente --> Procesando : inicio
  Procesando --> Completado : éxito
  Procesando --> Fallido : error
  Fallido --> Pendiente : reintento
  Completado --> [*]
```
