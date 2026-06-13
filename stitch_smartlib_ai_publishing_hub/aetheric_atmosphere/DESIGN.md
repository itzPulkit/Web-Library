---
name: Aetheric Atmosphere
colors:
  surface: '#fff8f5'
  surface-dim: '#e5d7cf'
  surface-bright: '#fff8f5'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#fff1e8'
  surface-container: '#f9ebe2'
  surface-container-high: '#f4e6dc'
  surface-container-highest: '#eee0d7'
  on-surface: '#211a15'
  on-surface-variant: '#524438'
  inverse-surface: '#372f29'
  inverse-on-surface: '#fceee5'
  outline: '#857467'
  outline-variant: '#d8c3b3'
  surface-tint: '#8c4f08'
  primary: '#8c4f08'
  on-primary: '#ffffff'
  primary-container: '#f2a359'
  on-primary-container: '#6b3a00'
  inverse-primary: '#ffb878'
  secondary: '#53606d'
  on-secondary: '#ffffff'
  secondary-container: '#d4e1f0'
  on-secondary-container: '#586471'
  tertiary: '#00677d'
  on-tertiary: '#ffffff'
  tertiary-container: '#5dc1de'
  on-tertiary-container: '#004d5e'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#ffdcc1'
  primary-fixed-dim: '#ffb878'
  on-primary-fixed: '#2e1500'
  on-primary-fixed-variant: '#6c3a00'
  secondary-fixed: '#d7e4f3'
  secondary-fixed-dim: '#bbc8d7'
  on-secondary-fixed: '#101d28'
  on-secondary-fixed-variant: '#3c4854'
  tertiary-fixed: '#b2ebff'
  tertiary-fixed-dim: '#71d3f1'
  on-tertiary-fixed: '#001f27'
  on-tertiary-fixed-variant: '#004e5e'
  background: '#fff8f5'
  on-background: '#211a15'
  surface-variant: '#eee0d7'
typography:
  display-lg:
    fontFamily: Hanken Grotesk
    fontSize: 48px
    fontWeight: '700'
    lineHeight: 56px
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Hanken Grotesk
    fontSize: 32px
    fontWeight: '600'
    lineHeight: 40px
  headline-md:
    fontFamily: Hanken Grotesk
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
  body-lg:
    fontFamily: Manrope
    fontSize: 18px
    fontWeight: '400'
    lineHeight: 28px
  body-md:
    fontFamily: Manrope
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  label-md:
    fontFamily: Geist
    fontSize: 14px
    fontWeight: '500'
    lineHeight: 20px
    letterSpacing: 0.05em
  label-sm:
    fontFamily: Geist
    fontSize: 12px
    fontWeight: '500'
    lineHeight: 16px
    letterSpacing: 0.03em
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
  xl: 40px
  gutter: 24px
  margin-mobile: 16px
  margin-desktop: 64px
---

## Brand & Style

This design system creates a dualistic emotional experience centered on "Aetheric Intelligence." It bridges the gap between high-tech precision and natural atmospheric comfort. 

The brand personality is **sophisticated, adaptive, and intentional**. In its "Daylight" state, it evokes the serenity of a sun-drenched library, emphasizing eye comfort and cognitive ease through "paper" textures and warm, low-blue-light frequencies. In its "Icey" dark state, it shifts into a futuristic, technical environment inspired by deep-sea luminescence and high-performance computing.

The style is a hybrid of **Minimalism** and **Glassmorphism**, utilizing translucent layers to suggest depth and intelligence while maintaining a clean, structured layout that feels both grounded and ethereal.

## Colors

The palette is built on two distinct environmental modes that radically transform the UI's mood.

**Daylight Mode (Warm/Soft):**
- **Primary:** Soft Amber (#F2A359), used for key actions and focus states, inspired by the gradient in the reference image.
- **Surface:** Cream (#FFF9F2), providing a paper-like, low-glare backdrop.
- **Text:** Muted Charcoal (#2E3A46), ensuring high legibility without the harshness of pure black.

**Icey Dark Mode (Cool/Technical):**
- **Primary:** Crystal Cyan (#00F2FF), providing a high-contrast "glow" for critical interactions.
- **Surface:** Deep Indigo (#16213E), layered with subtle frosted glass effects.
- **Text:** Arctic White (#E0FBFC), optimized for clarity against dark backgrounds.

## Typography

The typographic hierarchy balances modern precision with human-centric readability. 

**Hanken Grotesk** is used for headlines to provide a sharp, contemporary "Aetheric" look. **Manrope** handles body copy, chosen for its balanced proportions and exceptional legibility across both light and dark modes. **Geist** is reserved for labels and technical data, reinforcing the futuristic intelligence of the system.

In Daylight mode, typography uses slightly heavier weights to maintain contrast against the warm cream background. In Icey mode, weights are slightly refined to prevent "glow" bleeding on high-contrast displays.

## Layout & Spacing

The layout follows a **Fluid Grid** system based on a 4px base unit. 

- **Desktop:** 12-column grid with a 24px gutter and generous 64px side margins to create an "airy" feel.
- **Tablet:** 8-column grid with a 16px gutter.
- **Mobile:** 4-column grid with 16px margins. 

The rhythm is intentionally spacious. Elements are grouped using generous padding to emphasize the aetheric, uncluttered brand narrative. Vertically, sections are separated by `xl` (40px) or `2xl` (80px) gaps to prevent cognitive overload.

## Elevation & Depth

Visual hierarchy is treated differently across the two modes to maintain the atmospheric shift.

**Daylight Elevation:**
Uses **Ambient Shadows**. Surfaces feel like stacked sheets of premium paper. Shadows are extra-diffused, using a warm tint (e.g., `rgba(242, 163, 89, 0.08)`) rather than grey. Borders are rarely used; depth is created purely through subtle tonal shifts and soft shadows.

**Icey Dark Elevation:**
Uses **Glassmorphism and Glow**. Surfaces are semi-transparent with a high backdrop-blur (20px-30px). Elevation is indicated by "inner glow" borders (0.5px stroke in Cyan at 20% opacity) rather than drop shadows. This creates the illusion of floating, luminous panels.

## Shapes

The design uses a **Rounded (0.5rem / 8px)** base to strike a balance between geometric technicality and organic comfort. 

- **Input Fields & Small Buttons:** 8px radius.
- **Cards & Modals:** 16px (rounded-lg) to 24px (rounded-xl) for a friendlier, more contained feel.
- **Selection Pills:** Fully rounded (pill-shaped) to distinguish them from structural elements.

In Icey mode, shapes are often reinforced with a hairline stroke to maintain definition against the deep indigo background.

## Components

**Buttons:**
- **Primary:** Soft Amber gradient in Daylight; Cyan glow gradient in Icey. Text is always high-contrast against the fill.
- **Ghost:** Hairline borders. In Icey mode, these use the frosted glass effect.

**Input Fields:**
- **Daylight:** Soft cream fill with a subtle 1px border that darkens on focus.
- **Icey:** Translucent dark fill with a "glow" border on focus. Labels use Geist for a technical feel.

**Cards:**
- Main content containers. In Daylight, they utilize the "Paper" texture—a very subtle grain overlay at 3% opacity. In Icey, they utilize a 10% opacity white overlay with backdrop blur to create the "frosted" effect.

**Chips & Indicators:**
- Used for status and tags. These should be pill-shaped. In Icey mode, these can function as small light sources, using a subtle outer glow (neon-effect) for active states.