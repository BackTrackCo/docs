# Diagram Implementation Guide

This document outlines which diagrams are static images vs Mermaid code, and provides recommendations for future updates.

## Static Images (Custom Designed)

These diagrams have been converted to static SVG images for better visual quality and Mintlify compatibility:

### 1. **Fee Distribution** (`/images/fee-distribution.svg`)
**Used in:**
- `contracts/core-contracts.mdx`
- `contracts/architecture.mdx`

**Why static:** 
- Key visual appearing in multiple locations
- Benefits from custom color scheme and precise layout
- Complex hierarchical flow with split calculations

**Update process:** Edit the SVG file directly or recreate in Figma/Excalidraw

---

### 2. **Escrow vs Exact Comparison** (`/images/escrow-vs-exact.svg`)
**Used in:**
- `x402-integration/escrow-scheme.mdx`

**Why static:**
- Hero diagram introducing core concepts
- Side-by-side comparison benefits from custom layout
- Visual polish important for first impression

**Update process:** Edit the SVG file directly or recreate in design tool

---

## Mermaid Diagrams (Code-Based)

These diagrams remain as Mermaid code with professional theming applied:

### Sequence Diagrams
**Files:**
- All payment flow examples in `contracts/examples.mdx`
- Escrow scheme sequence in `x402-integration/escrow-scheme.mdx`
- Overview flow in `x402-integration/overview.mdx`

**Theme applied:**
```yaml
%%{init: {'theme':'base', 'themeVariables': {
  'primaryColor':'#f3f4f6',
  'primaryTextColor':'#1f2937',
  'primaryBorderColor':'#9ca3af',
  'lineColor':'#6b7280',
  'actorBkg':'#e0e7ff',
  'noteBkgColor':'#fef3c7'
}}}%%
```

**Why Mermaid:**
- Version-controlled and easy to update
- Clear temporal flow (timeline-based)
- Standard format for sequence diagrams

---

### Flowcharts
**Files:**
- Decision tree in `x402-integration/comparison.mdx`
- Logic tree in `conditions.mdx`
- Relationship diagrams in `factories.mdx`

**Theme applied:**
- Consistent color scheme with custom node styling
- Orange (#f59e0b) for escrow decisions
- Blue (#4f46e5) for exact decisions
- Gray (#64748b) for questions/intermediate nodes

**Why Mermaid:**
- Simple decision flows
- Easy to maintain as logic changes
- Code-based editing workflow

---

### State Diagrams
**Files:**
- Payment state machine in `core-contracts.mdx`
- Request status states in `core-contracts.mdx`

**Why Mermaid:**
- Perfect for state machines
- Clear state transitions
- Industry standard format

---

## Recommended for Conversion to Static

These diagrams would benefit from custom design in future iterations:

1. **Decision Tree** (`comparison.mdx`) - Could be a visually compelling infographic
2. **Condition Logic Tree** (`conditions.mdx`) - Complex nested logic might be clearer with custom layout
3. **Payment State Machine** (`core-contracts.mdx`) - Hero diagram that could be more polished

## Best Practices

### When to use Static Images:
- Hero/featured diagrams
- Complex layouts with custom positioning
- Diagrams appearing in multiple locations
- When visual brand consistency is critical

### When to use Mermaid:
- Sequence diagrams (temporal flows)
- Simple flowcharts and decision trees
- State machines
- Diagrams that change frequently
- Internal documentation

### Theming Standards:
All Mermaid diagrams should use the base theme with these colors:
- **Primary:** #f3f4f6 (light gray)
- **Escrow/Orange:** #f59e0b
- **Exact/Blue:** #4f46e5
- **Success/Green:** #10b981
- **Warning/Yellow:** #fef3c7
- **Text:** #1f2937

### File Organization:
- Static images: `/images/diagram-name.svg`
- ASCII source: `/images/diagram-name-ascii.txt` (for reference)
- Always include alt text describing the diagram
