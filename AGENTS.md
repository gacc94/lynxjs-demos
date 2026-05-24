# AGENTS.md

Monorepo LynxJS con proyectos demo en `apps/`. Sin apps creadas aun — todo proyecto nuevo debe seguir la estructura de abajo.

## Comandos

```bash
bun install                  # instala todas las dependencias (raiz + workspaces)
bun run build                # build de todos los proyectos
bun run lint                 # lint de todos los proyectos
bun run typecheck            # typecheck en todos los proyectos
bun run clean                # borra dist/ de todos los proyectos
bun run --filter apps/<app> build  # build de un solo proyecto
bun run --filter apps/<app> lint   # lint de un solo proyecto
```

No uses `npm`, `npx`, `pnpm`, ni `yarn` — el repo usa **bun** como package manager y runner.

## Estructura de un proyecto LynxJS

Cada app en `apps/<nombre>/` requiere:

```
apps/<nombre>/
├── package.json       ← dependencias propias (@lynx-js/react, etc.)
├── tsconfig.json      ← obligatorio: extends ../../tsconfig.base.json
├── lynx.config.ts     ← config de build (webpack o rspeedy)
└── src/
    ├── main.ts        ← entry point background thread
    ├── App.tsx        ← componente raiz ReactLynx
    └── main-thread.ts ← entry point main thread (opcional)
```

**Reglas al crear un proyecto nuevo:**

- `tsconfig.json` siempre extiende `../../tsconfig.base.json`
- Siempre tiene `lynx.config.ts` en la raiz del proyecto
- El entry point del background thread es `src/main.ts`
- El entry point del main thread es `src/main-thread.ts`

## LynxJS — datos clave para no errar

- **Arquitectura dual-thread**: background (`main.ts`) para logica, main thread (`main-thread.ts`) para UI. No son intercambiables.
- **ReactLynx**, no React — APIs distintas, revisar skills antes de escribir componentes.
- Las skills de `lynx-community/skills` cubren: tipado TS, devtool, trazas, FiberElement, Habitat, debug-info. Usarlas cuando corresponda.

## Skills del proyecto

Las skills se cargan desde `.agents/skills/` (configurado en `opencode.json`). Son 8 skills de `lynx-community/skills` activas para todo el monorepo.

## Convenciones

- Usar `"type": "module"` o no en `package.json` segun lo requiera el proyecto
- Respeta el `tsconfig.base.json` raiz como fuente de verdad de TS
- No duplicar `devDependencies` que ya estan en la raiz (TypeScript, etc.)
