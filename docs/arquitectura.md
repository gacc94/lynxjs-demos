# Arquitectura del Monorepo

## Estructura de archivos

```
lynxjs-demos/
├── package.json              ← Raiz del monorepo
├── tsconfig.base.json        ← Config TypeScript base
├── apps/                     ← Proyectos LynxJS
│   └── <proyecto>/
│       ├── package.json      ← Dependencias y scripts del proyecto
│       ├── tsconfig.json     ← Extiende tsconfig.base.json
│       ├── lynx.config.ts    ← Config de build de LynxJS (webpack/rspeedy)
│       ├── src/
│       │   ├── main.ts       ← Entry point (background thread)
│       │   ├── App.tsx       ← Componente raiz (ReactLynx)
│       │   └── main-thread.ts ← Entry point del main thread (opcional)
│       └── assets/           ← Recursos estaticos
├── docs/                     ← Documentacion
├── .opencode/                ← Config de opencode (agents, plugins)
└── opencode.json             ← Config de opencode (skills, MCP, etc.)
```

## Decisiones de diseño

### Workspaces

El `package.json` raiz declara `"workspaces": ["apps/*"]`. Esto permite:

- **Dependencias compartidas**: TypeScript, linters y tooling comun se instalan una sola vez en `node_modules/` raiz con `bun install`.
- **Scripts globales**: `bun run build`, `bun run lint` y `bun run typecheck` ejecutan en todos los proyectos via `bun run --filter '*'`.
- **Filtrado por proyecto**: `bun run --filter apps/<proyecto> build` ejecuta scripts solo en un proyecto especifico.

### TypeScript

`tsconfig.base.json` define las opciones estrictas base. Cada proyecto en `apps/<proyecto>/tsconfig.json` la extiende con `"extends": "../../tsconfig.base.json"` y agrega paths especificos del proyecto.

```json
{
  "extends": "../../tsconfig.base.json",
  "compilerOptions": {
    "outDir": "./dist",
    "rootDir": "./src"
  },
  "include": ["src"]
}
```

### LynxJS config

Cada proyecto define su propio `lynx.config.ts` con la configuracion de bundle (webpack o rspeedy), entry points y assets.

### Dependencias por proyecto

Cada `apps/<proyecto>/package.json` es independiente en sus dependencias de runtime (`@lynx-js/react`, etc.). Dependencias de desarrollo (TypeScript, linters) viven en el `package.json` raiz.

## Threads en LynxJS

LynxJS usa arquitectura dual-thread:

| Thread | Archivo tipico | Responsabilidad |
|---|---|---|
| **Background** | `src/main.ts` | Logica de negocio, estado, llamadas API |
| **Main** | `src/main-thread.ts` | UI rendering, animaciones, gestos |

La comunicacion entre threads se hace via el sistema de eventos de LynxJS.

## Ver tambien

- [Documentacion oficial de LynxJS](https://lynxjs.org/)
- [lynx-community/skills](https://skills.sh/lynx-community/skills)
