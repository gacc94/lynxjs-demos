## ADDED Requirements

### Requirement: User can swipe to delete a task
The system SHALL support a horizontal swipe gesture on a task item to trigger deletion, with a visual confirmation threshold.

#### Scenario: Swipe past threshold triggers delete
- **WHEN** user swipes a task item horizontally past the defined threshold distance
- **THEN** the task is removed from the list

#### Scenario: Swipe below threshold cancels
- **WHEN** user swipes a task item horizontally but releases before the threshold distance
- **THEN** the task item animates back to its original position and is not deleted

#### Scenario: Visual feedback during swipe
- **WHEN** user is swiping a task item
- **THEN** a visual indicator (e.g., background color change or icon reveal) shows the action that will be performed upon threshold crossing

#### Scenario: Swipe with main-thread handler
- **WHEN** user performs a swipe gesture on a task item
- **THEN** all touch event handling (touchstart, touchmove, touchend) SHALL run on the main thread using `main-thread:` prefixed event attributes and `'main thread'` directive for jank-free response

### Requirement: User can swipe to toggle task completion
The system SHALL support a horizontal swipe gesture in the opposite direction to toggle task completion status.

#### Scenario: Swipe opposite direction toggles completion
- **WHEN** user swipes a task item horizontally in the direction opposite to the delete swipe, past the threshold
- **THEN** the task completion status is toggled

#### Scenario: Completion swipe shows distinct visual
- **WHEN** user swipes in the completion direction
- **THEN** a distinct visual indicator different from the delete indicator is shown

### Requirement: User can drag to reorder tasks
The system SHALL support drag-to-reorder via long-press and vertical drag gesture to change task order in the list.

#### Scenario: Long-press activates drag mode
- **WHEN** user performs a long-press on a task item
- **THEN** the task enters a "dragging" state with elevated visual (scale and shadow)

#### Scenario: Drag repositions task
- **WHEN** user drags the task vertically past another task's position
- **THEN** the task list reorders, inserting the dragged task at the new position

#### Scenario: Release commits new order
- **WHEN** user releases the dragged task at a new position
- **THEN** the task remains at that position, and the reorder is committed to state via `runOnBackground`

#### Scenario: Drag with main-thread handler
- **WHEN** user performs a drag gesture on a task item
- **THEN** all touch event handling for the drag SHALL run on the main thread, and state mutations SHALL dispatch to background thread via `runOnBackground`

#### Scenario: Cancel drag on minimal movement
- **WHEN** user long-presses but moves less than a minimum distance before releasing
- **THEN** the task returns to its original position without reordering

## REMOVED Requirements
<!-- None -->

## MODIFIED Requirements
<!-- None -->

## RENAMED Requirements
<!-- None -->
