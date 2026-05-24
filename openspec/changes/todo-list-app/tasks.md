## 1. Project Setup

- [ ] 1.1 Create `apps/todo-app/` directory structure with `src/` and `src/components/`
- [ ] 1.2 Create `package.json` with name, dependencies (`@lynx-js/react`, `@lynx-js/rspeedy`), and scripts (build, lint, typecheck)
- [ ] 1.3 Create `tsconfig.json` extending `../../tsconfig.base.json` with Lynx-specific options
- [ ] 1.4 Create `lynx.config.ts` with Rspeedy configuration for ReactLynx bundling

## 2. Design System Tokens

- [ ] 2.1 Create `src/App.css` with all Lumina Tech design tokens as CSS custom properties (colors, typography, spacing, rounded corners, elevation)
- [ ] 2.2 Define typography classes matching headline-md, body-md, body-lg, label-caps, button-text
- [ ] 2.3 Define utility classes for spacing (8px base grid), rounded corners, and elevation levels
- [ ] 2.4 Define safe area CSS variables and edge-to-edge layout classes using `env(safe-area-inset-*)` with zero fallback

## 3. Data Model & State Management

- [ ] 3.1 Define `Task` TypeScript interface and action types (add, remove, toggle, reorder, update) in `src/types.ts`
- [ ] 3.2 Implement `taskReducer` pure function handling all task state transitions
- [ ] 3.3 Create `useTaskManager` custom hook wrapping `useReducer` with memoized action dispatchers

## 4. Core Component — TaskInput

- [ ] 4.1 Create `src/components/TaskInput.tsx` with title and description inputs
- [ ] 4.2 Implement submit handler that validates non-empty title and dispatches ADD action
- [ ] 4.3 Clear inputs after successful task creation
- [ ] 4.4 Style inputs following Lumina Tech input specs (light bg, 1px border, amber focus, 8px radius)

## 5. Core Component — TaskItem

- [ ] 5.1 Create `src/components/TaskItem.tsx` rendering task card with title, description, completion toggle, and delete button
- [ ] 5.2 Implement tap handler on completion indicator to dispatch TOGGLE action
- [ ] 5.3 Implement tap handler on delete button with `catchtap` to stop propagation
- [ ] 5.4 Implement inline edit mode: tap title/description to edit, submit on blur/enter
- [ ] 5.5 Style card following Lumina Tech card specs (white bg, 8px radius, 24px padding, subtle border)
- [ ] 5.6 Apply muted/completed styling (reduced opacity, strikethrough title) when `completed: true`

## 6. Core Component — TaskList & EmptyState

- [ ] 6.1 Create `src/components/TaskList.tsx` as a `scroll-view` rendering filtered/ordered `TaskItem` components
- [ ] 6.2 Create `src/components/EmptyState.tsx` with contextual message (no tasks vs no search results)
- [ ] 6.3 Style EmptyState following Lumina elevation Level 1 (surface-container-low, 16px radius, 48px+ padding)
- [ ] 6.4 Wire EmptyState to show when filtered task list is empty

## 7. Search & Filter

- [ ] 7.1 Create `src/components/SearchBar.tsx` with text input and clear button
- [ ] 7.2 Implement real-time search using `useMemo` to filter tasks by case-insensitive match on title and description
- [ ] 7.3 Create `src/components/FilterBar.tsx` with "All", "Active", "Completed" filter chips
- [ ] 7.4 Implement filter chip active/inactive states and apply filter to displayed task list
- [ ] 7.5 Style SearchBar following Lumina input specs, FilterBar chips using label-caps typography with amber accent for active state

## 8. Gestures — Swipe to Delete & Complete

- [ ] 8.1 Add `main-thread:bindtouchstart`, `main-thread:bindtouchmove`, `main-thread:bindtouchend` on TaskItem
- [ ] 8.2 Implement swipe detection logic (horizontal swipe distance > 80px threshold) with `'main thread'` directive
- [ ] 8.3 Show delete visual indicator (red background) on left-to-right swipe past 40px
- [ ] 8.4 Show complete visual indicator (amber background) on right-to-left swipe past 40px
- [ ] 8.5 Dispatch delete or toggle action via `runOnBackground` when threshold is crossed on touchend
- [ ] 8.6 Animate task item back to origin on swipe below threshold using `setStyleProperty` on main thread

## 9. Gestures — Drag to Reorder

- [ ] 9.1 Add long-press detection (touchstart → 300ms hold → activate drag) with `'main thread'` directive
- [ ] 9.2 Apply elevated visual (scale 1.03, shadow) on drag mode activation
- [ ] 9.3 Track vertical touchmove delta and compute target insertion index
- [ ] 9.4 Animate surrounding items to make space for dragged item using `setStyleProperty` transforms
- [ ] 9.5 On touchend, dispatch REORDER action via `runOnBackground` with new index
- [ ] 9.6 Cancel drag on minimal vertical movement (< 10px) and restore original position

## 10. App Shell & Integration

- [ ] 10.1 Create `src/App.tsx` composing all components (SearchBar, FilterBar, TaskInput, TaskList)
- [ ] 10.2 Wire `useTaskManager` hook to provide state and dispatchers to child components
- [ ] 10.3 Create `src/main.ts` as background thread entry point rendering `App`
- [ ] 10.4 Ensure no native module calls in render scope — all background-only logic in effects/event handlers
- [ ] 10.5 Apply overall app styling: `var(--color-background)` page background extending full-bleed behind system bars, 16px horizontal margins, edge-to-edge layout with safe area insets for iOS status bar and Android navigation bar

## 11. Verification

- [ ] 11.1 Run `bun run --filter apps/todo-list build` and verify successful build
- [ ] 11.2 Run `bun run --filter apps/todo-list typecheck` and fix any TypeScript errors
- [ ] 11.3 Run `bun run --filter apps/todo-list lint` and fix any lint issues
- [ ] 11.4 Verify all checkboxes in task management spec are implemented (create, view, toggle, edit, delete)
- [ ] 11.5 Verify search and filter work correctly with combined criteria
- [ ] 11.6 Verify swipe-to-delete, swipe-to-complete, and drag-to-reorder gestures function
- [ ] 11.7 Verify design system compliance: colors, typography, spacing, shapes match Lumina Tech specs
- [ ] 11.8 Verify edge-to-edge layout: content not obscured by iOS status bar or Android navigation bar, background extends full-bleed behind system bars
