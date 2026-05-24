## ADDED Requirements

### Requirement: Design tokens available as CSS custom properties
The system SHALL define all Lumina Tech design tokens from `DESIGN.md` as CSS custom properties in a root-level stylesheet, accessible to all components.

#### Scenario: Color tokens are available
- **WHEN** a component references `var(--color-primary)` or any other design token color
- **THEN** the correct hex color from the Lumina Tech palette is resolved

#### Scenario: Typography tokens are available
- **WHEN** a component references `var(--font-body-md)` or any typography token
- **THEN** the correct font family, size, weight, and line height are applied

#### Scenario: Spacing tokens use 8px base grid
- **WHEN** a component references any spacing token (e.g., `--spacing-base: 8px`)
- **THEN** all spacing values are multiples of 8px as defined in the design system

### Requirement: Buttons follow Lumina Tech button styles
The system SHALL render buttons matching the three button tiers: Primary (solid onyx/amber), Secondary (ghost with border), and Tertiary (text-only).

#### Scenario: Primary button uses onyx background
- **WHEN** a Primary button is rendered
- **THEN** it SHALL have a solid `#000000` (primary) background with `#ffffff` text, 8px border-radius, and `button-text` typography

#### Scenario: Delete action uses error color
- **WHEN** a destructive action button (delete) is rendered
- **THEN** it SHALL use the `--color-error` (`#ba1a1a`) token for background or text

#### Scenario: Amber accent used for create/submit actions
- **WHEN** a positive action (create, submit) is rendered
- **THEN** it SHALL use the `--color-secondary` (`#7d5700` / `#fdbb38`) token as accent

### Requirement: Cards follow Lumina Tech card styles
The system SHALL render task items as cards with white background, 8px border-radius, and 24px internal padding.

#### Scenario: Task card has correct styling
- **WHEN** a task item card is rendered
- **THEN** it SHALL have `var(--color-surface-container-low)` background, 8px border-radius, 24px padding, and a subtle 1px border using `var(--color-outline-variant)`

#### Scenario: Completed task has muted styling
- **WHEN** a task is marked as completed
- **THEN** the card SHALL apply reduced opacity or a strikethrough on the title to visually distinguish it

### Requirement: Input fields follow Lumina Tech input styles
The system SHALL render text inputs with light background, 1px border, and amber focus state.

#### Scenario: Default input style
- **WHEN** a text input is rendered in its default state
- **THEN** it SHALL have a light background (`var(--color-surface-container-lowest)`), 1px border (`var(--color-outline-variant)`), and 8px border-radius

#### Scenario: Input focus state
- **WHEN** a text input receives focus
- **THEN** its border SHALL change to `var(--color-secondary)` (#7d5700 amber) to indicate focus

### Requirement: Chips and badges follow Lumina Tech styles
The system SHALL render filter chips using `label-caps` typography with low-opacity accent backgrounds.

#### Scenario: Active filter chip style
- **WHEN** a filter chip is in its active/selected state
- **THEN** it SHALL have an amber background at 15% opacity with primary onyx text

#### Scenario: Inactive filter chip style
- **WHEN** a filter chip is in its inactive state
- **THEN** it SHALL have a neutral surface background with secondary text color

### Requirement: Typography follows Lumina Tech scale
The system SHALL use the defined typography scale: `headline-md` for app title, `body-md` for task titles, `body-lg` for search input, `label-caps` for chips/badges, and `button-text` for buttons.

#### Scenario: App title uses headline-md
- **WHEN** the app title is rendered
- **THEN** it SHALL use DM Sans, 24px, weight 600, line height 32px

#### Scenario: Task title uses body-md
- **WHEN** a task title is rendered
- **THEN** it SHALL use DM Sans, 16px, weight 400, line height 24px

#### Scenario: Filter chips use label-caps
- **WHEN** a filter chip is rendered
- **THEN** it SHALL use Open Sans, 12px, weight 700, line height 16px, letter spacing 0.08em, uppercase

### Requirement: Empty state follows Lumina Tech elevation system
The system SHALL render the empty state placeholder using the defined tonal layering for depth.

#### Scenario: Empty state card
- **WHEN** the empty state is rendered
- **THEN** it SHALL use a Level 1 surface background (`var(--color-surface-container-low)`) with rounded corners (16px) and adequate vertical padding (48px+)

### Requirement: Edge-to-edge layout with safe area insets
The system SHALL render edge-to-edge on iOS and Android, respecting system bar safe areas so that no content is obscured by the status bar or navigation bar.

#### Scenario: Content avoids iOS status bar
- **WHEN** the app runs on iOS
- **THEN** the root layout SHALL apply `padding-top: env(safe-area-inset-top)` to offset content below the status bar

#### Scenario: Content avoids Android navigation bar
- **WHEN** the app runs on Android with a navigation bar
- **THEN** the root layout SHALL apply `padding-bottom: env(safe-area-inset-bottom)` to offset content above the navigation bar

#### Scenario: Background extends full-bleed behind system bars
- **WHEN** the app renders
- **THEN** the page background color SHALL extend behind the status bar and navigation bar for a seamless edge-to-edge appearance

#### Scenario: Safe area fallback when env variables are unavailable
- **WHEN** `env(safe-area-inset-*)` values are not available (e.g., older runtime or web preview)
- **THEN** the layout SHALL fall back to zero (no extra padding) without breaking the layout

## REMOVED Requirements
<!-- None -->

## MODIFIED Requirements
<!-- None -->

## RENAMED Requirements
<!-- None -->
