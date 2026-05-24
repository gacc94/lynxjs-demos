---
name: Lumina Tech
colors:
  surface: '#fff7fd'
  surface-dim: '#e2d7e3'
  surface-bright: '#fff7fd'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#fcf0fd'
  surface-container: '#f6eaf7'
  surface-container-high: '#f0e5f1'
  surface-container-highest: '#eadfeb'
  on-surface: '#1f1a22'
  on-surface-variant: '#49454a'
  inverse-surface: '#352e37'
  inverse-on-surface: '#f9edfa'
  outline: '#7a757a'
  outline-variant: '#cbc5ca'
  surface-tint: '#615d61'
  primary: '#000000'
  on-primary: '#ffffff'
  primary-container: '#1d1b1e'
  on-primary-container: '#878286'
  inverse-primary: '#cbc5c9'
  secondary: '#7d5700'
  on-secondary: '#ffffff'
  secondary-container: '#fdbb38'
  on-secondary-container: '#6e4c00'
  tertiary: '#000000'
  on-tertiary: '#ffffff'
  tertiary-container: '#161c28'
  on-tertiary-container: '#7e8493'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#e7e1e5'
  primary-fixed-dim: '#cbc5c9'
  on-primary-fixed: '#1d1b1e'
  on-primary-fixed-variant: '#494649'
  secondary-fixed: '#ffdeaa'
  secondary-fixed-dim: '#fdbb38'
  on-secondary-fixed: '#271900'
  on-secondary-fixed-variant: '#5f4100'
  tertiary-fixed: '#dde2f4'
  tertiary-fixed-dim: '#c1c6d7'
  on-tertiary-fixed: '#161c28'
  on-tertiary-fixed-variant: '#414755'
  background: '#fff7fd'
  on-background: '#1f1a22'
  surface-variant: '#eadfeb'
typography:
  display-lg:
    fontFamily: DM Sans
    fontSize: 48px
    fontWeight: '700'
    lineHeight: 56px
    letterSpacing: -0.02em
  display-lg-mobile:
    fontFamily: DM Sans
    fontSize: 36px
    fontWeight: '700'
    lineHeight: 44px
    letterSpacing: -0.02em
  headline-md:
    fontFamily: DM Sans
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
  body-lg:
    fontFamily: DM Sans
    fontSize: 18px
    fontWeight: '400'
    lineHeight: 28px
  body-md:
    fontFamily: DM Sans
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  label-caps:
    fontFamily: Open Sans
    fontSize: 12px
    fontWeight: '700'
    lineHeight: 16px
    letterSpacing: 0.08em
  button-text:
    fontFamily: DM Sans
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 20px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  base: 8px
  gutter: 24px
  margin-mobile: 16px
  margin-desktop: 64px
  container-max: 1280px
---

## Brand & Style

This design system is engineered for high-performance technology platforms and developer-centric interfaces. The brand personality is **sophisticated, forward-thinking, and precise**, evoking a sense of "premium utility." 

The design style follows a **Modern Corporate** aesthetic with **Glassmorphic** influences. While originally conceived as a nocturnal environment, this light-mode adaptation maintains technical clarity through high-contrast surfaces and refined color accents. It utilizes a crisp, luminous base palette contrasted with vibrant amber accents to create a high-focus environment. UI elements are structured using a rigorous grid system, punctuated by soft, translucent surfaces and subtle borders that mimic a sophisticated IDE or a high-end dashboard. The goal is to provide a sense of depth and technical clarity without overwhelming the user with unnecessary skeuomorphism.

## Colors

The palette is anchored in a **Light-Mode** strategy, shifting from a dark aesthetic to a clean, professional white and light-grey environment.

*   **Primary (#0B090C):** The core "Deep Onyx" is used primarily for typography, high-contrast buttons, and brand-defining elements to maintain authority and a crisp, modern feel.
*   **Secondary (#F1B02D):** The "Amber Accent." Reserved for high-priority calls to action, active states, and critical branding highlights. It provides a warm, energetic contrast against the cool neutral surfaces.
*   **Tertiary (#E8EDFF):** A cool-toned off-white/blue used for subtle container backgrounds and decorative elements that require a slight distinction from the pure background.
*   **Neutral (#0F0A12):** Used primarily for secondary text levels and deep borders, ensuring maximum legibility on light backgrounds.

Color application should follow a 60-30-10 rule, where the light neutral surfaces dominate, the primary onyx provides structural definition, and the secondary amber is used sparingly for maximum impact.

## Typography

The typography system relies on **DM Sans** for its geometric clarity and modern proportions. It handles the majority of the information architecture, from bold display headlines to legible body copy.

*   **Headlines:** Use tight letter-spacing for large sizes to maintain a "locked-in" tech feel.
*   **Body:** Line height is generous (1.5x - 1.6x) to ensure long-form technical content remains digestible. Against light backgrounds, ensure body text utilizes the Primary onyx for optimal contrast.
*   **Labels:** **Open Sans** is introduced for utility labels and micro-copy. It is often set in uppercase with increased letter spacing to provide a distinct visual hierarchy from the primary content.

All typography should be rendered with anti-aliasing (font-smoothing) enabled to preserve the sharp edges of the geometric glyphs on high-density displays.

## Layout & Spacing

The layout is built on a **12-column fixed grid** for desktop, transitioning to a **4-column fluid grid** for mobile. 

*   **Rhythm:** A strict 8px baseline grid ensures vertical consistency. Spacing increments should always be multiples of 8 (8, 16, 24, 32, 48, 64).
*   **Responsive Reflow:** On mobile, side margins collapse to 16px. Desktop margins are expansive (64px+) to create an editorial, premium feel. 
*   **Containers:** Content is housed in "well-defined sections." These sections use large vertical padding (80px - 120px) to separate different conceptual areas of the product, preventing cognitive overload.

## Elevation & Depth

Hierarchy is established through **Tonal Layering** and **Soft Shadows** rather than the nocturnal glows of a dark theme.

1.  **Level 0 (Floor):** Pure Background (`#FFFFFF`).
2.  **Level 1 (Section):** Light Surface / Tertiary Background (`#E8EDFF`).
3.  **Level 2 (Cards):** Elevated White Surface with a very subtle 1px border.
4.  **Level 3 (Pop-overs):** White surface with a diffused 24px shadow (Color: `#0F0A12`, Opacity: 8%).

**Glassmorphism Effect:** For navigation bars and modal overlays, use a background-blur of `12px` and a semi-transparent white fill at 80% opacity. This maintains context while ensuring a light, airy feel.

## Shapes

The design system utilizes **Rounded (0.5rem)** corners as the standard. This strikes a balance between the "friendly" consumer-web look and the "sharp" professional-tool aesthetic.

*   **Standard Elements (Buttons, Inputs):** 8px (0.5rem) radius.
*   **Large Containers (Cards, Sections):** 16px (1rem) radius to soften the larger visual footprints.
*   **Interactive Accents:** Small badges or tags may use 4px (0.25rem) to appear more "instrument-like" and precise.

## Components

### Buttons
*   **Primary:** Solid Primary Onyx (`#0B090C`) with light text, or Solid Amber (`#F1B02D`) with dark text. 
*   **Secondary:** Ghost style. Transparent background, 1px border of Primary color, text in Primary color.
*   **Tertiary:** Text-only with an underline transition on hover.

### Cards
Cards are the primary structural unit. They should have a white background, an 8px border-radius, and a subtle internal padding of 24px. Use extremely light borders or very soft shadows to imply separation.

### Inputs
Fields use a light-grey fill or white with a 1px border to create a clean "form" look. Focus states must use a 1px Amber border to signify activity.

### Chips & Badges
Small, high-contrast pills. Use the `label-caps` typography. Backgrounds should be low-opacity versions of the accent colors (e.g., Amber at 15% opacity).

### Lists
Lists should avoid bullet points. Use 8px Amber squares or technical icons (like a chevron or a code bracket) as lead-in elements. Use horizontal dividers only when necessary, using a subtle neutral border token.