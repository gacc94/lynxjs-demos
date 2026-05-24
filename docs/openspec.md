# OpenSpec (OPSX) — Desarrollo con Especificaciones

Este proyecto usa OpenSpec para guiar el desarrollo con un flujo basado en artefactos: propuesta, especificaciones, diseño y tareas antes de implementar.

## Workflow OPSX

### Ciclo de un cambio

```
/opsx:new "descripcion"     ← Inicia un cambio nuevo
       │
       ▼
/opsx:continue              ← Crea el primer artefacto listo (propuesta)
       │
       ▼
/opsx:continue              ← Siguiente artefacto (especificaciones)
       │
       ▼
/opsx:continue              ← Siguiente artefacto (diseño)
       │
       ▼
/opsx:continue              ← Siguiente artefacto (tareas)
       │
       ▼
/opsx:apply                 ← Implementa las tareas
       │
       ▼
/opsx:verify                ← Valida que la implementacion cumple la spec
       │
       ▼
/opsx:archive               ← Archiva el cambio completado
```

### Atajos

| Comando | Proposito |
|---|---|
| `/opsx:explore` | Explorar ideas, investigar problemas (sin estructura) |
| `/opsx:new` | Iniciar un nuevo cambio |
| `/opsx:continue` | Crear siguiente artefacto segun dependencias |
| `/opsx:ff` | Fast-forward — crea todos los artefactos de planificacion a la vez |
| `/opsx:apply` | Implementar tareas, actualizando artefactos segun sea necesario |
| `/opsx:verify` | Validar que la implementacion coincide con las especificaciones |
| `/opsx:sync` | Sincronizar delta specs a main specs |
| `/opsx:archive` | Archivar un cambio completado |
| `/opsx:bulk-archive` | Archivar multiples cambios completados a la vez |

### Comandos legacy

- `/opsx:propose "idea"` — Crea todos los artefactos de planificacion a la vez (preferir OPSX para cambios complejos, util para cambios simples)

## Estructura de archivos

```
openspec/
├── specs/           ← Especificaciones principales del proyecto
│   └── *.md         ← Specs en formato Given/When/Then
└── changes/         ← Cambios en progreso
    └── <change-id>/ ← Cada cambio con sus artefactos
        ├── proposal.md
        ├── specs.md
        ├── design.md
        └── tasks.md
```

## Reglas del proyecto

Cuando se creen specs para este proyecto, usar el formato estandar de OpenSpec con schema `spec-driven`.

### Contexto del proyecto para specs

- **Tech stack**: TypeScript, LynxJS, ReactLynx, Bun
- **Arquitectura**: Monorepo con workspaces, dual-thread (background/main)
- **Package manager**: Bun con workspaces
- **Testing**: A definir por proyecto

## Ver tambien

- [Documentacion oficial de OpenSpec](https://github.com/Fission-AI/OpenSpec)
- [OPSX Workflow Reference](https://github.com/Fission-AI/OpenSpec/blob/main/docs/opsx-workflow.md)
