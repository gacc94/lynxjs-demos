## ADDED Requirements

### Requirement: User can create a task
The system SHALL allow the user to create a new task with a title and optional description.

#### Scenario: Create task with title only
- **WHEN** user enters a title in the task input and submits
- **THEN** a new task is added to the list with `completed: false`, a unique `id`, and the current timestamp as `createdAt`

#### Scenario: Create task with title and description
- **WHEN** user enters a title and description in the task input and submits
- **THEN** both fields are saved to the new task

#### Scenario: Reject empty title
- **WHEN** user submits the task input with an empty or whitespace-only title
- **THEN** no task is created and the input is not cleared

### Requirement: User can view all tasks
The system SHALL display all tasks in a scrollable list ordered by creation time (newest first).

#### Scenario: View populated list
- **WHEN** tasks exist in the list
- **THEN** all tasks are displayed with title, description preview, and completion status visible

#### Scenario: View empty list
- **WHEN** no tasks exist
- **THEN** an empty state placeholder is displayed with a message indicating no tasks

### Requirement: User can toggle task completion
The system SHALL allow the user to mark a task as completed or uncompleted via tap.

#### Scenario: Mark task as completed
- **WHEN** user taps the completion indicator on an uncompleted task
- **THEN** the task's `completed` status changes to `true` and the visual style updates to reflect completion

#### Scenario: Mark task as uncompleted
- **WHEN** user taps the completion indicator on a completed task
- **THEN** the task's `completed` status changes to `false` and the visual style reverts to the uncompleted state

### Requirement: User can edit a task
The system SHALL allow the user to edit the title and description of an existing task.

#### Scenario: Edit task title
- **WHEN** user taps on a task's title and modifies it
- **THEN** the task title is updated in the state

#### Scenario: Edit task description
- **WHEN** user taps on a task's description and modifies it
- **THEN** the task description is updated in the state

### Requirement: User can delete a task
The system SHALL allow the user to delete a task, removing it permanently from the list.

#### Scenario: Delete task via button
- **WHEN** user taps the delete action on a task
- **THEN** the task is removed from the list and no longer displayed

## REMOVED Requirements
<!-- None -->

## MODIFIED Requirements
<!-- None -->

## RENAMED Requirements
<!-- None -->
