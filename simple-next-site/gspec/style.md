---
gspec-version: 1.2.1
---

# Visual Style Guide

## 1. Overview

- **Design Vision**: A clean, professional interface that communicates expertise and trustworthiness. The design recedes to let content take center stage — clear typography, generous whitespace, and purposeful color usage.
- **Target Platforms**: Responsive web (Mobile-First, scaling to Desktop/Tablet).
- **Visual Personality**: Professional, Approachable, Reliable, Pragmatic.
- **Design Rationale**: A professional services site must project competence and trustworthiness at a glance. The restrained palette and clear typography let the content speak, while strategic use of color draws attention to key actions. The minimal aesthetic avoids visual noise that could undermine credibility.

## 2. Color Palette

High-contrast and professional, designed for readability across devices and lighting conditions.

### Primary Colors

| Color Name | Hex | Usage |
| :--- | :--- | :--- |
| **Primary** | `#2563EB` | Primary action color. Used for primary buttons, active states, and key highlights. |
| **Primary Dark** | `#1D4ED8` | Hover states for primary actions. |
| **Primary Light** | `#60A5FA` | Accents on dark backgrounds. |

### Secondary Colors

| Color Name | Hex | Usage |
| :--- | :--- | :--- |
| **Slate Dark** | `#0F172A` | Dark mode background. |
| **Slate Surface** | `#1E293B` | Dark mode cards/surfaces. |
| **Paper White** | `#FFFFFF` | Light mode background. |

### Neutral Colors

| Role | Light Mode | Dark Mode | Usage |
| :--- | :--- | :--- | :--- |
| **Text Primary** | `#0F172A` | `#F8FAFC` | Headings, main body text. |
| **Text Secondary** | `#64748B` | `#94A3B8` | Labels, helper text, supporting content. |
| **Text Disabled** | `#CBD5E1` | `#475569` | Disabled fields, placeholders. |
| **Border** | `#E2E8F0` | `#334155` | Dividers, input borders. |

### Semantic Colors

| State | Color | Hex | Usage |
| :--- | :--- | :--- | :--- |
| **Success** | Emerald | `#10B981` | Success confirmations, positive feedback. |
| **Error** | Red | `#EF4444` | Validation errors, destructive actions. |
| **Warning** | Amber | `#F59E0B` | Non-critical alerts, warnings. |
| **Info** | Sky | `#0EA5E9` | Informational tooltips, notes. |

---

## 3. Typography

Typography is the primary interface element. It must be legible and convey professionalism.

### Font Families

- **Primary (UI & Headings)**: **Inter** (Google Fonts). Clean, highly legible, with a tall x-height.
- **Monospace (Code & Data)**: **JetBrains Mono** or system monospace fallback. Used for code snippets or technical content if needed.

### Type Scale (Mobile-First)

| Level | Size (rem/px) | Line Height | Weight | Usage |
| :--- | :--- | :--- | :--- | :--- |
| **H1** | `1.875rem` (30px) | `1.2` | Bold (700) | Page titles |
| **H2** | `1.5rem` (24px) | `1.3` | SemiBold (600) | Section headers |
| **H3** | `1.25rem` (20px) | `1.4` | Medium (500) | Sub-sections, card titles |
| **Body Lg** | `1.125rem` (18px) | `1.5` | Regular (400) | Featured text, hero subtitles |
| **Body Base** | `1rem` (16px) | `1.5` | Regular (400) | Default text, descriptions |
| **Body Sm** | `0.875rem` (14px) | `1.4` | Regular (400) | Metadata, captions |
| **Caption** | `0.75rem` (12px) | `1.4` | Medium (500) | Tiny labels, tags |

---

## 4. Spacing & Layout

Standard 4px grid system.

### Spacing Scale

- **xs**: `4px` (0.25rem) — Tight grouping (tags, icon+text)
- **sm**: `8px` (0.5rem) — Component internal spacing
- **md**: `16px` (1rem) — Standard separation between elements
- **lg**: `24px` (1.5rem) — Section separation
- **xl**: `32px` (2rem) — Major layout breaks

### Grid System

- **Container**: Max-width 1152px centered with horizontal padding for comfortable reading width.
- **Columns**: Single-column layout on mobile. Multi-column grids on desktop where appropriate.

### Layout Patterns

- **Mobile-first**: Single-column stacked layout.
- **Desktop**: Multi-column grids for cards and feature sections.
- **Flex containers**: Always apply `min-width: 0` on flex children that wrap content to prevent the flexbox `min-width: auto` default from causing horizontal overflow on mobile.
- **Content wrappers**: Use `overflow: hidden` on bounded containers (cards, main content area) to clip any remaining overflow.

---

## 5. Themes

### Light Mode (Default)
- **Background**: `#FFFFFF`
- **Surface**: `#F8FAFC` or `#FFFFFF` with borders.
- **Text**: `#0F172A`

### Dark Mode
- **Background**: `#0F172A` (Not pure black, reduces contrast strain).
- **Surface**: `#1E293B`
- **Primary Action**: `#2563EB` stands out vividly.
- **Text**: `#F8FAFC` for high legibility.

### Theme Switching
- Toggleable via a control in the site header.
- System preference default on first visit.
- Token mapping: light/dark overrides swap `--color-background`, `--color-surface`, `--color-text-primary`, `--color-text-secondary`, `--color-text-disabled`, and `--color-border`.

---

## 6. Components

### Buttons

- **Primary**: Solid `#2563EB` background, white text. Border radius 6px. Full width on mobile for key actions.
- **Secondary**: Transparent/Outline. Border `#CBD5E1` (Light) / `#475569` (Dark). Text `#334155` / `#CBD5E1`.
- **Ghost**: No border, hover background. Used for tertiary actions.
- **Sizes**:
    - **Default**: 40px height.
    - **Large**: 48px height — Main CTAs.
    - **Touch Target**: Minimum 44x44px for tappable areas.

### Form Elements

- **Style**: Minimal. Border with rounded corners.
- **Default**: Background transparent. Border `#CBD5E1` (Light) / `#334155` (Dark).
- **Focus**: Border `#2563EB` (2px). Ring `rgba(37, 99, 235, 0.2)`.

### Cards & Containers

- **Style**: Flat or subtle border. Heavy shadows are avoided for a clean look.
- **Background**: `#FFFFFF` (Light) / `#1E293B` (Dark).
- **Border**: 1px solid `#E2E8F0` (Light) / `#334155` (Dark).
- **Radius**: 8px.

### Navigation

- **Mobile**: Hamburger menu triggered from the site header. Reveals a flat list of navigation destinations.
- **Desktop**: Horizontal link bar in the site header.
- **Footer**: Grouped link lists for primary navigation and legal links.

---

## 7. Visual Effects

### Shadows & Elevation
Minimalist approach.
- **None**: Most elements.
- **sm**: `0 1px 2px rgba(0, 0, 0, 0.05)` for cards to lift slightly off background.
- **md**: `0 4px 6px rgba(0, 0, 0, 0.07)` for floating elements or sticky headers.

### Border Radius
- **Standard**: 6px for inputs/buttons.
- **Large**: 8px for cards/containers.
- **Pills**: 9999px for status tags.

### Transitions & Animations
- **Speed**: Fast (150ms or 200ms).
- **Ease**: `cubic-bezier(0, 0, 0.2, 1)` (ease-out).
- **Feedback**: Immediate visual feedback on interaction (hover color shift, subtle scale reduction on press for buttons).
- **Loading States**: Skeleton screens or spinner indicators for async operations.

---

## 8. Iconography

### Icon Style
- **Library**: SVG-based icon library. Tree-shakeable inline SVG imports.
- **Style**: Outlined, 2px stroke.
- **Size**:
    - Small: 16px.
    - Standard: 20px.
    - Navigation: 24px.

### Usage Guidelines
- Pair icons with text labels in navigation for accessibility.
- Use familiar metaphors for common actions.

---

## 9. Imagery & Media

### Photography Style
Not applicable for initial launch. If marketing imagery is added later, it should be authentic and professional — not generic stock photography.

### Illustrations
Not applicable — the UI relies on typography, spacing, and iconography rather than illustrations. Empty states use icon + text patterns.

---

## 10. Accessibility

### Contrast Requirements
- Maintain WCAG AA standard (4.5:1) for normal text.
- Large text (18px+ or 14px+ bold) requires 3:1 minimum.

### Focus States
- Visible focus rings for keyboard/screen reader navigation.
- Focus ring style: 2px offset ring in primary color.

### Text Accessibility
- **Touch**: All interactive elements must have at least 44px hit areas.
- Minimum body font size: 16px (1rem).

---

## 11. Responsive Design

### Breakpoints
- **Mobile First**: Design for 375px width base.
- **sm**: 640px (Large phones)
- **md**: 768px (Tablets)
- **lg**: 1024px (Desktop)

### Mobile-Specific Patterns
- Touch targets: minimum 44x44px on all interactive elements.
- Mobile navigation: Hamburger menu pattern (see Components > Navigation).

---

## 12. Design Tokens

### Token Structure
- Naming convention: `--color-*`, `--font-*`, `--spacing-*`, `--shadow-*`, `--radius-*`, `--duration-*`
- Tokens are defined as framework-agnostic CSS custom properties

### Token Definitions

```css
:root {
  /* Colors — Primary */
  --color-primary: #2563EB;
  --color-primary-dark: #1D4ED8;
  --color-primary-light: #60A5FA;
  --color-primary-foreground: #FFFFFF;

  /* Colors — Semantic */
  --color-success: #10B981;
  --color-error: #EF4444;
  --color-warning: #F59E0B;
  --color-info: #0EA5E9;

  /* Colors — Light Mode (default) */
  --color-background: #FFFFFF;
  --color-surface: #F8FAFC;
  --color-text-primary: #0F172A;
  --color-text-secondary: #64748B;
  --color-text-disabled: #CBD5E1;
  --color-border: #E2E8F0;

  /* Typography */
  --font-family-sans: 'Inter', sans-serif;
  --font-family-mono: 'JetBrains Mono', monospace;
  --font-size-h1: 1.875rem;
  --font-size-h2: 1.5rem;
  --font-size-h3: 1.25rem;
  --font-size-body-lg: 1.125rem;
  --font-size-body: 1rem;
  --font-size-body-sm: 0.875rem;
  --font-size-caption: 0.75rem;
  --font-weight-regular: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;

  /* Spacing */
  --spacing-xs: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 1.5rem;
  --spacing-xl: 2rem;

  /* Border Radius */
  --radius-md: 0.375rem;
  --radius-lg: 0.5rem;
  --radius-full: 9999px;

  /* Shadows */
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.07);

  /* Transitions */
  --duration-fast: 150ms;
  --duration-medium: 200ms;
  --ease-out: cubic-bezier(0, 0, 0.2, 1);
}

/* Dark Mode */
[data-theme="dark"],
.dark {
  --color-background: #0F172A;
  --color-surface: #1E293B;
  --color-text-primary: #F8FAFC;
  --color-text-secondary: #94A3B8;
  --color-text-disabled: #475569;
  --color-border: #334155;
}
```

## 13. Usage Examples

### Component Combinations

To be defined.
