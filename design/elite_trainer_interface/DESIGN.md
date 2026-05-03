---
name: Elite Trainer Interface
colors:
  surface: '#111316'
  surface-dim: '#111316'
  surface-bright: '#37393d'
  surface-container-lowest: '#0c0e11'
  surface-container-low: '#1a1c1f'
  surface-container: '#1e2023'
  surface-container-high: '#282a2d'
  surface-container-highest: '#333538'
  on-surface: '#e2e2e6'
  on-surface-variant: '#c2c6d6'
  inverse-surface: '#e2e2e6'
  inverse-on-surface: '#2f3034'
  outline: '#8c909f'
  outline-variant: '#424754'
  surface-tint: '#adc6ff'
  primary: '#adc6ff'
  on-primary: '#002e6a'
  primary-container: '#4d8eff'
  on-primary-container: '#00285d'
  inverse-primary: '#005ac2'
  secondary: '#4edea3'
  on-secondary: '#003824'
  secondary-container: '#00a572'
  on-secondary-container: '#00311f'
  tertiary: '#ffb786'
  on-tertiary: '#502400'
  tertiary-container: '#df7412'
  on-tertiary-container: '#461f00'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#d8e2ff'
  primary-fixed-dim: '#adc6ff'
  on-primary-fixed: '#001a42'
  on-primary-fixed-variant: '#004395'
  secondary-fixed: '#6ffbbe'
  secondary-fixed-dim: '#4edea3'
  on-secondary-fixed: '#002113'
  on-secondary-fixed-variant: '#005236'
  tertiary-fixed: '#ffdcc6'
  tertiary-fixed-dim: '#ffb786'
  on-tertiary-fixed: '#311400'
  on-tertiary-fixed-variant: '#723600'
  background: '#111316'
  on-background: '#e2e2e6'
  surface-variant: '#333538'
typography:
  display-lg:
    fontFamily: Space Grotesk
    fontSize: 48px
    fontWeight: '700'
    lineHeight: '1.1'
  h1:
    fontFamily: Space Grotesk
    fontSize: 32px
    fontWeight: '600'
    lineHeight: '1.2'
  h2:
    fontFamily: Space Grotesk
    fontSize: 24px
    fontWeight: '600'
    lineHeight: '1.3'
  body-lg:
    fontFamily: Inter
    fontSize: 18px
    fontWeight: '400'
    lineHeight: '1.6'
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '400'
    lineHeight: '1.5'
  body-sm:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '400'
    lineHeight: '1.4'
  label-caps:
    fontFamily: Space Grotesk
    fontSize: 12px
    fontWeight: '700'
    lineHeight: '1'
    letterSpacing: 0.05em
  price-display:
    fontFamily: Space Grotesk
    fontSize: 20px
    fontWeight: '700'
    lineHeight: '1'
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  unit: 4px
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 48px
  container-max: 1440px
  gutter: 20px
---

## Brand & Style

The design system is engineered for the serious collector and competitive player, balancing the nostalgia of the franchise with a sophisticated, high-performance aesthetic. It evokes the feeling of a premium digital pokedex or a professional financial trading platform, applied to the world of TCG.

The visual style is **Glassmorphic Minimalism**. By utilizing deep charcoal surfaces and translucent slate overlays, the system allows the vibrant artwork of the cards to remain the focal point. Subtle background blurs and micro-interactions provide a sense of technical depth, while high-octane accent colors provide immediate "type" recognition. The result is a sleek, gamer-centric environment that feels both authoritative and immersive.

## Colors

The palette is anchored by "Abyssal Charcoal" and "Slate Shadow" to provide a low-fatigue environment for long collection-browsing sessions. 

### Accent System
- **Functional Accents:** Used for primary actions, navigation states, and systemic feedback.
- **Type Accents:** A specialized palette used exclusively for Pokémon elemental classification. These should be used sparingly—primarily in badges, energy icons, and card borders—to prevent visual clutter.
- **Status Colors:** Success (Owned) uses a vibrant Emerald; Missing/Warning uses a muted Slate or High-Contrast Amber for market alerts.

## Typography

The design system employs a dual-font strategy to balance character with readability.

- **Space Grotesk** is used for headlines, prices, and labels. Its geometric, slightly technical nature reinforces the "gamer-centric" vibe and provides a high-tech feel to data points like market prices and HP counts.
- **Inter** is the workhorse for all body copy, descriptions, and data-heavy tables. Its neutral, utilitarian design ensures that card effects and fine print remain legible even at small sizes in dark mode.

All numerical data (prices, set numbers) should utilize tabular sizing to ensure vertical alignment in lists.

## Layout & Spacing

This design system utilizes a **12-column fluid grid** for dashboard views and a **dynamic masonry grid** for card galleries.

- **Card Grids:** Use a responsive auto-fit pattern. Minimum card width is 180px for desktop views to allow for readable titles and prices.
- **Rhythm:** An 8px base unit drives all spacing. Component internals (like card padding) use 16px (md), while section margins use 48px (xl) to create breathing room between data clusters.
- **Density:** High-density views are preferred for "Collection" screens, while low-density, centered layouts are used for "Card Detail" views.

## Elevation & Depth

Hierarchy is established through **Tonal Layering** combined with **Backdrop Blurs**.

1.  **Level 0 (Background):** #0F1115. The base canvas.
2.  **Level 1 (Surface):** #1A1D23. Used for card containers and navigation bars.
3.  **Level 2 (Active/Hover):** #262A33. Applied to hovered cards or active menu items.
4.  **Level 3 (Popovers/Modals):** Semi-transparent Slate (#1A1D23 at 80% opacity) with a 20px backdrop blur and a 1px subtle border (#FFFFFF10).

Shadows are used sparingly. When used, they should be "Ambient Shadows"—deep, wide blurs with very low opacity (25%) to simulate a soft glow rather than a harsh drop-shadow.

## Shapes

The design system uses **Rounded (0.5rem)** corners as the standard. This mimics the physical radius of a standard Pokémon card, creating a subconscious link between the digital UI and the physical hobby.

- **Standard Components:** Buttons, input fields, and small cards use 8px (0.5rem).
- **Large Containers:** Dashboard widgets and main card displays use 16px (1rem).
- **Interactive Elements:** Checkboxes and radio buttons maintain a slight 4px radius rather than being fully circular or sharp, maintaining the system's modern edge.

## Components

### Card Grids
Cards are the primary unit of the system. Each card should feature a 1px inner border to define it against the dark background. On hover, the card should scale slightly (1.02x) and increase the intensity of its type-specific accent glow.

### Status Badges (Owned/Missing)
- **Owned:** A "Pill" shape with a subtle green tint background and a high-contrast green text/check icon.
- **Missing:** A "Pill" with a Ghost-style border (1px slate) and muted grey text, indicating a placeholder state.

### Price Displays
Prices should always be displayed in **Space Grotesk**. Upward trends are shown in secondary (green) with a small chevron, while downward trends use fire-red. Always include the "Market Price" label in the `label-caps` style above the value.

### Buttons
- **Primary:** Solid fill using the Primary Color. High-contrast white text.
- **Secondary:** Ghost style with a 1px border of the Primary Color.
- **Type-Specific:** For "Filter by Type," buttons should adopt the specific elemental color when active.

### Input Fields
Inputs use the `surface-bright` color with a 1px border. Focus state should be indicated by a vibrant primary-color glow and a transition of the border color.