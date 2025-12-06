# Design Guidelines: Interactive Data Visualization Dashboard

## Design Approach
**Reference-Based:** Drawing inspiration from Vercel and Notion's minimal, data-focused aesthetics with emphasis on clarity, breathing room, and subtle sophistication.

## Core Design Principles
1. **Data First:** Charts and visualizations are the heroes—supporting UI recedes
2. **Generous Whitespace:** Let data breathe with ample spacing between components
3. **Subtle Depth:** Use shadows sparingly for elevation, not decoration
4. **Clean Hierarchy:** Clear visual distinction between primary data and supporting insights

## Typography System
**Primary Font:** Inter (Google Fonts)
- Dashboard Title: 2.5rem (40px), font-weight 700, letter-spacing -0.02em
- Section Headers: 1.5rem (24px), font-weight 600
- Chart Titles: 1.125rem (18px), font-weight 600
- Insight Card Values: 2rem (32px), font-weight 700
- Insight Card Labels: 0.875rem (14px), font-weight 500, text-gray-600
- Body Text: 1rem (16px), font-weight 400

## Layout System
**Spacing Units:** Tailwind's 4, 6, 8, 12, 16, 24 (focus on multiples of 4)
- Container: max-w-7xl, centered, px-6 py-16
- Section Spacing: mb-16 between major sections
- Card Padding: p-8
- Chart Container Padding: p-6

**Grid Structure:**
- Insight Cards: 3-column grid (grid-cols-3) with gap-6
- Charts Section: 2-column grid (grid-cols-2) with gap-8 for radar + bar
- Word Cloud: Full-width standalone section

## Component Specifications

### Dashboard Header
- Centered title with subtle description underneath
- Download button: Top-right absolute position, subtle ghost button style
- Bottom border or divider to separate from content

### Chart Containers
- White background (bg-white)
- Border radius: rounded-xl (12px)
- Shadow: shadow-sm (subtle)
- Border: 1px solid gray-100
- Minimum height: 400px for charts
- Chart titles above visualization, left-aligned

### Insight Cards
- Three cards in a row showcasing: "Top Concern", "Lowest Concern", "Average Score"
- Each card structure:
  - Large numerical value or label (top)
  - Small descriptive label (bottom)
  - Accent border-left (4px) in distinct muted color per card (blue, green, purple)
- Hover state: Slight shadow elevation (shadow-md)

### Word Cloud
- Black background container (bg-gray-900 or similar dark) with rounded-xl
- White text for contrast
- Padding: p-12
- Height: 500px
- Words scale based on frequency/importance

### Download Button
- Ghost/outline style (border, transparent background)
- Icon + "Download PNG" text
- Hover: Subtle background fill (gray-50)

## Animation Strategy
**AOS Implementation (Minimal):**
- Insight cards: fade-up with stagger (100ms delay between)
- Chart containers: fade-in (no directional movement to avoid distraction)
- Word cloud: fade-in with slight delay
- Duration: 600ms for all animations
- Easing: ease-in-out

**Critical:** Animations should feel polished but not gimmicky—data takes priority

## Color Palette Philosophy
Use neutral grays as the foundation with minimal accent colors:
- Chart colors: Use Plotly's default vibrant palette for data visualization
- Borders: gray-200
- Text hierarchy: gray-900 (primary), gray-600 (secondary), gray-400 (tertiary)
- Accent borders for insight cards: Subtle blue, green, purple (muted tones)

## Page Background
- Off-white or very light gray (gray-50) to create subtle contrast with white cards
- NOT pure white to avoid flatness

## Responsive Behavior
- Desktop (default): 2-column charts, 3-column insights
- Tablet: 2-column insights, stacked charts
- Mobile: Single column everything

## Interactive States
- Chart tooltips: Plotly's default with clean styling
- Hover on cards: Elevation increase (shadow transition)
- Download button: Smooth background transition on hover

## Polish Details
- All containers use consistent rounded-xl corners
- Shadows are subtle and consistent (shadow-sm default, shadow-md on hover)
- Transitions: 200ms for hover states
- Focus states: Maintain accessibility with visible focus rings

This dashboard should feel like a premium analytics tool—clean, focused, and effortlessly professional.