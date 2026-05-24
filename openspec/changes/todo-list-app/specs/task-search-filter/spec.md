## ADDED Requirements

### Requirement: User can search tasks by text
The system SHALL filter the task list in real-time as the user types a search query, matching against task title and description.

#### Scenario: Search matches title
- **WHEN** user types a search query that partially matches a task title
- **THEN** that task is displayed in the filtered results

#### Scenario: Search matches description
- **WHEN** user types a search query that partially matches a task description
- **THEN** that task is displayed in the filtered results

#### Scenario: Search is case-insensitive
- **WHEN** user types a search query in a different case than the task text
- **THEN** matching tasks are still displayed (case-insensitive comparison)

#### Scenario: No search matches
- **WHEN** user types a query that matches no tasks
- **THEN** the list displays an empty state with a message indicating no results found

#### Scenario: Clear search restores full list
- **WHEN** user clears the search query
- **THEN** all tasks are displayed again

### Requirement: User can filter tasks by completion status
The system SHALL provide filter chips to show all tasks, only completed tasks, or only active (uncompleted) tasks.

#### Scenario: Filter active tasks
- **WHEN** user selects the "Active" filter chip
- **THEN** only tasks with `completed: false` are displayed

#### Scenario: Filter completed tasks
- **WHEN** user selects the "Completed" filter chip
- **THEN** only tasks with `completed: true` are displayed

#### Scenario: Show all tasks (default)
- **WHEN** user selects the "All" filter chip or no filter is active
- **THEN** all tasks are displayed regardless of completion status

#### Scenario: Combined search and filter
- **WHEN** both a text search query and a completion filter are active
- **THEN** only tasks matching both criteria are displayed

### Requirement: Search and filter preserve task order
The system SHALL maintain the existing task ordering when applying search and filter.

#### Scenario: Filter preserves order
- **WHEN** a filter is applied
- **THEN** matching tasks retain their relative order from the full list

## REMOVED Requirements
<!-- None -->

## MODIFIED Requirements
<!-- None -->

## RENAMED Requirements
<!-- None -->
