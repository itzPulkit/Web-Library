---
name: Aetheric Intelligence Library
colors:
  surface: '#0b1326'
  surface-dim: '#0b1326'
  surface-bright: '#31394d'
  surface-container-lowest: '#060e20'
  surface-container-low: '#131b2e'
  surface-container: '#171f33'
  surface-container-high: '#222a3d'
  surface-container-highest: '#2d3449'
  on-surface: '#dae2fd'
  on-surface-variant: '#c7c4d7'
  inverse-surface: '#dae2fd'
  inverse-on-surface: '#283044'
  outline: '#908fa0'
  outline-variant: '#464554'
  surface-tint: '#c0c1ff'
  primary: '#c0c1ff'
  on-primary: '#1000a9'
  primary-container: '#8083ff'
  on-primary-container: '#0d0096'
  inverse-primary: '#494bd6'
  secondary: '#44e2cd'
  on-secondary: '#003731'
  secondary-container: '#03c6b2'
  on-secondary-container: '#004d44'
  tertiary: '#c4c7c9'
  on-tertiary: '#2d3133'
  tertiary-container: '#8e9193'
  on-tertiary-container: '#272a2c'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#e1e0ff'
  primary-fixed-dim: '#c0c1ff'
  on-primary-fixed: '#07006c'
  on-primary-fixed-variant: '#2f2ebe'
  secondary-fixed: '#62fae3'
  secondary-fixed-dim: '#3cddc7'
  on-secondary-fixed: '#00201c'
  on-secondary-fixed-variant: '#005047'
  tertiary-fixed: '#e0e3e5'
  tertiary-fixed-dim: '#c4c7c9'
  on-tertiary-fixed: '#191c1e'
  on-tertiary-fixed-variant: '#444749'
  background: '#0b1326'
  on-background: '#dae2fd'
  surface-variant: '#2d3449'
typography:
  display-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 48px
    fontWeight: '800'
    lineHeight: '1.1'
    letterSpacing: -0.02em
  display-lg-mobile:
    fontFamily: Plus Jakarta Sans
    fontSize: 32px
    fontWeight: '800'
    lineHeight: '1.2'
  headline-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 24px
    fontWeight: '700'
    lineHeight: '1.3'
    letterSpacing: -0.01em
  body-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 18px
    fontWeight: '400'
    lineHeight: '1.6'
    letterSpacing: 0.01em
  body-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 16px
    fontWeight: '400'
    lineHeight: '1.6'
  label-caps:
    fontFamily: Plus Jakarta Sans
    fontSize: 12px
    fontWeight: '600'
    lineHeight: '1.0'
    letterSpacing: 0.1em
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  unit: 8px
  container-max: 1440px
  gutter: 24px
  margin-desktop: 64px
  margin-mobile: 20px
  stack-sm: 12px
  stack-md: 24px
  stack-lg: 48px
---

## Brand & Style
The design system embodies a sophisticated, AI-driven digital sanctum. It targets intellectual professionals and researchers who seek a focus-oriented yet cutting-edge reading environment. The brand personality is "Cerebral, Luminescent, and Dimensional."

The visual style is **Modern Glassmorphism** integrated with **Tactile 3D layering**. It moves away from flat design by introducing Z-axis depth, utilizing frosted glass textures that appear to float over a deep, infinite void. The goal is to make digital assets feel like physical, light-emitting artifacts.

## Colors
The palette is rooted in a "Deep Space" hierarchy. 
- **Backgrounds:** Use `#020617` for the base canvas to provide maximum contrast for glass effects. 
- **Primary & Secondary:** Electric Indigo and Teal are used exclusively for interactive triggers, progress indicators, and AI-state highlights.
- **Glass Surfaces:** These are not just solid colors but semi-transparent layers (`rgba(15, 23, 42, 0.65)`) with a `backdrop-filter: blur(24px)`.
- **Highlights:** Use thin, high-contrast inner borders to simulate light catching the edge of glass.

## Typography
This design system utilizes **Plus Jakarta Sans** for its geometric clarity and modern terminal cuts. 
- **Weight Contrast:** Use ExtraBold (800) for page titles and Regular (400) for body text to create a clear informational hierarchy.
- **Letter Spacing:** Headlines use negative tracking to feel "tight" and engineered, while labels use wide tracking (10%) for a premium, editorial feel.
- **Color Application:** Primary body text should be Tertiary (`#F8FAFC`) at 90% opacity, while secondary metadata should drop to 60% to maintain depth.

## Layout & Spacing
The layout follows a **Fluid 12-Column Grid** with generous negative space to emphasize the 3D "floating" nature of the components. 
- **Z-Padding:** Elements should feel like they have internal "breathing room" (minimum 24px internal padding for glass cards).
- **Perspective:** On desktop, use a 1000px perspective value for container wrappers to allow for subtle 3D rotation on hover.
- **Reflow:** On mobile, columns collapse to a single stack, and horizontal margins reduce to 20px, but the "floating" card aesthetic remains via increased outer shadows.

## Elevation & Depth
Depth is the core differentiator of this design system. It is achieved through three layers:
1.  **The Void (Level 0):** The base background with subtle radial mesh gradients in the corners.
2.  **Floating Glass (Level 1):** Main content containers with 24px blur, a 1px `white/10%` border, and a soft `0 20px 40px rgba(0,0,0,0.4)` shadow.
3.  **Active Interactive (Level 2):** Elements being hovered or interacted with. These use a `translateZ(10px)` transform, increased blur (40px), and a secondary "glow" shadow using the primary Indigo color at 20% opacity.

## Shapes
A **Rounded** strategy is used to soften the technical nature of the AI. 
- **Standard Cards:** 1rem (16px) corner radius.
- **Buttons/Inputs:** 0.75rem (12px) for a modern, tactile feel.
- **Glass Overlays:** Use "Smoothing" (iOS-style squircles) where possible for a more organic feel against the rigid grid.

## Components
- **Glass Cards:** The primary container. Must have a `backdrop-filter: blur(20px)`, a semi-transparent dark fill, and a top-weighted 1px stroke to simulate a light source from above.
- **3D Action Buttons:** Use a solid primary-to-secondary gradient. On hover, apply a `box-shadow` of the same color to create a "neon underglow" effect and scale the button by 1.05x.
- **AI-Lume Inputs:** Form fields should be dark glass with a bottom-only 2px border that "ignites" into a teal gradient when focused.
- **Reading Progress Chips:** Small, pill-shaped glass elements with a micro-glow indicating the percentage of the book completed.
- **Floating Navigation:** A bottom-docked or side-mounted glass bar that uses high-intensity blur to separate itself from the content rolling beneath it.
- **Perspective Lists:** Vertical lists where items subtly tilt toward the cursor on hover, creating a tactile "browsing through a physical shelf" sensation.