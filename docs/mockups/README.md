# Interactive HTML/CSS Mockups

This folder contains **professional, production-ready HTML/CSS mockups** for the Calendar Configuration Wizard.

## 🎯 Overview

High-quality, interactive mockups demonstrating the wizard flow with modern UX/UI standards, accessibility best practices, and healthcare aesthetic.

## 📁 Files

### Interactive HTML Mockups
- **`index.html`** - Landing page with overview of all mockups and navigation
- **`step-1-use-case.html`** - Use Case Selection (5 template cards)
- **`step-2-timezone.html`** - Timezone Setup with Australia DST warning ⚠️ (CRITICAL)
- **`step-5-preview.html`** - Preview & Test with calendar and validation checklist
- **`styles.css`** - Shared design system stylesheet

### How to View
1. Open `index.html` in your browser (recommended starting point)
2. Or directly open any step file (e.g., `step-2-timezone.html`)
3. All mockups are fully interactive with hover effects and clickable elements

## 🎨 Design System Features

- **CSS Variables:** Design tokens for colors, spacing (8px grid), typography
- **Responsive:** Desktop-first (1200px+) with mobile breakpoints
- **Accessible:** WCAG AA compliant, keyboard navigation, ARIA labels
- **Healthcare UI:** Professional medical software aesthetic
- **Semantic HTML5:** Proper heading hierarchy, form labels
- **Smooth Interactions:** Transitions, hover effects, visual feedback

## 🏗️ Technology Stack

- **HTML5** - Semantic markup
- **CSS3** - Modern features (Grid, Flexbox, CSS Variables)
- **JavaScript** - Minimal, only for interactive demonstrations
- **No Frameworks** - Pure code, ready for integration

## 📋 Mockup Details

### Step 1: Use Case Selection
- 5 clickable cards with healthcare templates
- Gradient backgrounds for visual hierarchy
- Progress indicator (Step 1 of 5)
- Disabled Next button until selection made

### Step 2: Timezone Setup (MOST CRITICAL)
- Auto-detection success box (green)
- Cross-timezone radio buttons
- Region checkboxes with Australia DST warning
- Prominent orange warning box for DST complexity
- Technical info box explaining UTC storage
- Interactive: Auto-demos Australia warning after 2 seconds

### Step 5: Preview & Test
- Two-panel layout (validation + calendar)
- Configuration summary checklist (7 items)
- Interactive calendar grid (week view)
- Sample appointments displayed
- Test booking button with success confirmation
- Deploy/Save/Cancel actions

## 🚀 Usage

### For Demonstration
Open `index.html` to see all mockups with descriptions and links.

### For Development
1. Use `styles.css` as base design system
2. Copy HTML structure for wizard implementation
3. Adapt JavaScript interactions for real functionality
4. Replace mockup data with actual API calls

## 🎯 Key Highlights

1. **Proactive Error Prevention:** Step 2 warns about Australia DST BEFORE configuration
2. **Guided Flow:** Progressive disclosure reduces cognitive load
3. **Visual Feedback:** Clear validation states and success confirmations
4. **Professional Quality:** Production-ready code, not wireframes

## 📊 Specifications Based On

- **WIZARD_FLOW.md** - Detailed 5-step flow design
- **GEMINI_PROMPTS.md** - UI specifications for each step
- **PRD.md** - Product requirements and user needs
- **METHODOLOGY.md** - Design principles and best practices

## 📝 Notes

- Mockups demonstrate UX/UI concepts, not full backend functionality
- Sample data used for calendar appointments
- Auto-demo features included (e.g., Australia warning auto-triggers)
- Color palette: Blue #2196F3, Green #4CAF50, Orange #FF9800, Red #F44336

## 🔗 Related Resources

- Wizard Flow Specification: `../WIZARD_FLOW.md`
- Product Requirements: `../PRD.md`
- User Stories: `../USER_STORIES.md`
- Methodology: `../../METHODOLOGY.md`

---

**Created:** February 2026
**Purpose:** Recruitment demonstration + design validation
**Status:** Ready for review and user testing
