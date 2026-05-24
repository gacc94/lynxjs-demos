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
├── docs/                 ← documentacion de arquitectura
├── .opencode/
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
