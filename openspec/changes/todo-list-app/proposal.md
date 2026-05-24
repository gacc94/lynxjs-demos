## Why

The monorepo currently has no apps. A TODO list app provides a practical, feature-rich demo that exercises ReactLynx dual-thread architecture, gesture handling, animations, and state management — all while adhering to the Lumina Tech design system defined in the project's DESIGN.md.

## What Changes

- Create `apps/todo-app/` as a new ReactLynx project with full configuration (`package.json`, `tsconfig.json`, `lynx.config.ts`)
- Implement a complete TODO list application featuring task CRUD operations (create, read, update, delete)
- Add search/filter functionality for tasks
- Add gesture-based task reordering (drag/swipe to reorder)
- Implement swipe-to-delete and swipe-to-complete gestures
- Style all components following the Lumina Tech design system (colors, typography, spacing, rounded corners, elevation)
- Support dual-thread architecture: background thread for logic, main thread for UI rendering

## Capabilities

### New Capabilities
- `task-management`: Core task CRUD operations — create, read, update, and delete tasks with title, description, and completion state
- `task-search-filter`: Search and filter tasks by text query and completion status
- `task-gestures`: Gesture-based task interactions — swipe to delete, swipe to complete, drag to reorder
- `lumina-design-system`: Application of the Lumina Tech design system tokens (colors, typography, spacing, shapes) to all UI components

### Modified Capabilities
<!-- No existing capabilities to modify -->

## Impact

- New project: `apps/todo-app/` (all files new, no existing code affected)
- Dependencies: `@lynx-js/react`, `@lynx-js/types`, `@lynx-js/rspeedy` (or equivalent Lynx toolchain)
- Design system: Implements `DESIGN.md` Lumina Tech tokens via a shared CSS/theming approach
- No breaking changes — greenfield project
