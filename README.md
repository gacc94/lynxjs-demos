# LynxJS Demos

Monorepositorio con proyectos demo del framework [LynxJS](https://lynxjs.org/) para desarrollo de aplicaciones hibridas.

## Estructura

```
lynxjs-demos/
├── package.json          ← workspaces, scripts globales
├── tsconfig.base.json    ← config TypeScript base compartida
├── apps/                 ← proyectos LynxJS (cada uno con su package.json)
│   ├── demo-uno/
│   └── demo-dos/
├── openspec/             ← especificaciones del proyecto (OpenSpec)
│   ├── specs/            ← especificaciones principales
│   └── changes/          ← cambios en progreso
├── docs/                 ← documentacion de arquitectura
├── .opencode/            ← config de opencode (commands, skills)
├── opencode.json
└── .gitignore
```

Ver [`docs/arquitectura.md`](docs/arquitectura.md) para mas detalle sobre la estructura del monorepo y decisiones de diseño.

## Skills

Este proyecto usa skills de [lynx-community/skills](https://skills.sh/lynx-community/skills):

| Skill | Uso |
|---|---|
| `reactlynx-best-practices` | Arquitectura dual-thread y patrones ReactLynx |
| `fiber-element` | API nativa FiberElement sin ReactLynx/JSX |
| `lynx-typescript` | Tipado TypeScript, eventos y componentes |
| `lynx-devtool` | Debugging con Chrome DevTools Protocol |
| `lynx-trace-analysis` | Analisis de trazas de rendimiento |
| `lynx-trace-record` | Guia para grabar trazas de rendimiento |
| `habitat-usage` | Dependencias multi-repo con Habitat |
| `debug-info-remapping` | Remapeo de debug info |

## Requisitos

- [Bun](https://bun.sh/) >= 1.2
- [OpenSpec](https://github.com/Fission-AI/OpenSpec) (desarrollo con especificaciones)

## Uso

```bash
# Instalar dependencias de todos los proyectos
bun install

# Build de todos los proyectos
bun run build

# Build de un proyecto especifico
bun run --filter apps/demo-uno build

# Lint y typecheck global
bun run lint
bun run typecheck
```

## Agregar un nuevo proyecto

```bash
mkdir -p apps/<nombre>
cd apps/<nombre>
bun init -y
# Agregar lynx.config.ts y dependencias LynxJS
```

## OpenSpec

El proyecto usa [OpenSpec](https://github.com/Fission-AI/OpenSpec) para desarrollo guiado por especificaciones. Esto asegura que cada funcionalidad nueva tenga specs, diseño y tareas antes de implementar.

### Comandos rapidos

```bash
/opsx:new       # Iniciar un nuevo cambio
/opsx:continue  # Crear siguiente artefacto
/opsx:ff        # Fast-forward: crear todos los artefactos de planificacion
/opsx:apply     # Implementar tareas
/opsx:verify    # Validar implementacion contra spec
/opsx:archive   # Archivar cambio completado
```

Ver [`docs/openspec.md`](docs/openspec.md) para la guia completa del workflow OPSX.
