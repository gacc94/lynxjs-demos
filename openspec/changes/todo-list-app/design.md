## Context

This is a greenfield ReactLynx TODO list app within the `lynxjs-demos` monorepo. No existing apps exist in `apps/`. The project must follow the AGENTS.md conventions (dual-thread architecture, `lynx.config.ts`, extends `tsconfig.base.json`) and implement the Lumina Tech design system defined in the root `DESIGN.md`.

LynxJS uses a dual-thread model: background thread (`src/main.ts`) for logic/state, and main thread for UI rendering. Gestures must use `main-thread:` event prefixes for synchronous, jank-free interactions. All state mutations happen on the background thread.

## Goals / Non-Goals

**Goals:**
- Full task CRUD with title, description, and completion state
- Text search with real-time filtering across title and description
- Gesture-based swipe-to-delete, swipe-to-complete, and drag-to-reorder
- Lumina Tech design system applied via CSS custom properties and token-based components
- Clean dual-thread separation: state logic in background, gesture handling on main thread
- TypeScript strict mode with proper ReactLynx type annotations

**Non-Goals:**
- Persistent storage (no AsyncStorage/SQLite — in-memory only)
- Backend API integration (no sync, no auth)
- Accessibility beyond standard Lynx platform support
- Multiple task lists or categories
- i18n / localization
- Unit/integration tests in this initial implementation

## Decisions

### 1. Project build tool: Rspeedy (`@lynx-js/rspeedy`)

**Rationale:** Rspeedy is the modern Lynx build tool based on Rspack. It replaces the older webpack-based `lynx.config.ts` approach. The `AGENTS.md` mentions both options, but Rspeedy is preferred for new projects.

**Alternative:** Webpack-based `lynx.config.ts` — older, slower, not recommended for new projects.

### 2. State management: `useReducer` pattern

**Rationale:** The task state has multiple operations (add, remove, toggle, reorder, edit) that modify the same array. `useReducer` centralizes all transitions in a pure reducer, making state changes predictable and testable. This lives in the background thread context (inside a custom hook).

**Alternative:** Multiple `useState` calls — would scatter mutation logic across event handlers, making reordering and optimistic updates harder to reason about.

### 3. Gesture handling: Main thread touch events

**Rationale:** LynxJS supports `main-thread:` prefixed event attributes for synchronous gesture handling. Swipe and drag require frame-synchronous response to feel responsive. We use `main-thread:bindtouchstart`, `main-thread:bindtouchmove`, and `main-thread:bindtouchend` for all gesture interactions. The main thread computes the gesture velocity/distance and calls `runOnBackground` to dispatch state changes back to the background thread.

**Alternative:** Background thread gesture handlers — would introduce visible lag due to thread switching overhead, degrading the UX for swipe-to-delete and drag-to-reorder.

### 4. Design system application: CSS custom properties

**Rationale:** Lumina Tech is defined as a token set (colors, typography, spacing, rounded corners). CSS custom properties (`--color-primary`, `--font-body-md`, etc.) defined in a root stylesheet allow all components to reference design tokens by name. This keeps the design system DRY and makes future theming straightforward.

**Alternative:** Inline styles or JS constants — would couple design tokens to component logic and make it harder to maintain consistency.

### 5. Component structure: Flat hierarchy with single App root

**Rationale:** A TODO list app is conceptually simple. A flat component tree (`App` → `TaskList`, `TaskInput`, `SearchBar`, `FilterBar`; `TaskList` → `TaskItem`[]) avoids unnecessary nesting. Each component owns its responsibilities clearly.

**Alternative:** Compound component pattern with context — overkill for this scope.

### 6. Task data model: Plain TypeScript interface

```typescript
interface Task {
  id: string;
  title: string;
  description: string;
  completed: boolean;
  createdAt: number;
}
```

**Rationale:** Simple, serializable, sufficient for all CRUD operations. `id` uses `crypto.randomUUID()` (available in Lynx runtime). `createdAt` as epoch ms for stable sorting.

### 7. Edge-to-edge layout: CSS safe area env variables

**Rationale:** The app must render edge-to-edge on both iOS (behind status bar + home indicator) and Android (behind status bar + navigation bar). Lynx supports `env(safe-area-inset-top)`, `env(safe-area-inset-right)`, `env(safe-area-inset-bottom)`, and `env(safe-area-inset-left)` in CSS. The root container uses `padding-top: env(safe-area-inset-top)` and `padding-bottom: env(safe-area-inset-bottom)` to avoid content overlap with system bars. The background color extends full-bleed behind the bars for a seamless edge-to-edge experience.

**Alternative:** Platform-specific JS APIs for safe area — more complex and not needed when CSS env variables handle both platforms uniformly.

### 8. Search: Real-time client-side filter

**Rationale:** No backend means all tasks are in memory. Filter/search runs as a derived computation from the task list state. A `useMemo` that filters tasks by search query (case-insensitive match on title + description) and completion status filter.

## Project Structure

```
apps/todo-app/
├── package.json
├── tsconfig.json
├── lynx.config.ts
└── src/
    ├── main.ts              # Background thread entry
    ├── App.tsx              # Root ReactLynx component
    ├── App.css              # App-level styles + design tokens
    └── components/
        ├── TaskInput.tsx     # Task creation form
        ├── TaskList.tsx      # Scrollable task list
        ├── TaskItem.tsx      # Individual task row (with gestures)
        ├── SearchBar.tsx     # Search input
        ├── FilterBar.tsx     # Completion status filter chips
        └── EmptyState.tsx    # Empty list placeholder
```

## Risks / Trade-offs

- **In-memory only**: Tasks are lost on app restart. Acceptable for a demo; persistence can be added later.
- **Touch gesture complexity**: Swipe-to-delete and drag-to-reorder on main thread require careful coordinate math. Threshold tuning (swipe distance, drag activation) may need iteration.
- **No main-thread.ts**: The app doesn't require a separate main-thread entry since all main-thread logic is inline via `'main thread'` directives in component files. If gesture logic grows complex, extracting a `main-thread.ts` may be warranted.
- **Lynx runtime availability**: Features like `runOnMainThread`, `useMainThreadRef`, and `main-thread:` events require Lynx runtime >= 3.2. The skill docs reference these APIs as available.
