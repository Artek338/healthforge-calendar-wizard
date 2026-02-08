# Gemini Prompts for Calendar Wizard Mockups

Use these prompts with **Google Gemini** (with Imagen 3) or **NanoBanana** to generate visual mockups.

---

## 🎨 Prompt 1: Step 1 - Use Case Selection

```text
Create a modern, clean UI mockup for a calendar configuration wizard - Step 1.

LAYOUT:
- White background with soft shadows
- Top: Progress indicator showing "Step 1 of 5" with filled dot on step 1
- Center: Large heading "What will you use this calendar for?"
- Below heading: Subtext "Choose a template to get started quickly"

CONTENT - 5 OPTION CARDS (arranged in 2 columns):

Card 1: "Patient Appointments"
- Icon: 📅 (or medical calendar icon)
- Description: "Schedule patient visits and consultations"
- Style: Light blue accent color (#E1F5FF)

Card 2: "Resource & Equipment Booking"
- Icon: 🏥 (or medical equipment icon)
- Description: "Book MRI, CT scanners, and treatment rooms"
- Style: Light green accent color (#E1FFE1)

Card 3: "Staff Scheduling"
- Icon: 👥 (or nurse/doctor icon)
- Description: "Manage shifts and on-call rotations"
- Style: Light purple accent color (#F5E1FF)

Card 4: "Events & Meetings"
- Icon: 📋 (or clipboard icon)
- Description: "Schedule team meetings and training"
- Style: Light yellow accent color (#FFF4E1)

Card 5: "Other/Custom"
- Icon: ⚙️ (or settings icon)
- Description: "Start with a blank calendar"
- Style: Light gray accent color (#F5F5F5)

DESIGN STYLE:
- Modern, clean healthcare UI
- Rounded corners (8px radius)
- Each card has hover state (slight elevation/shadow)
- Cards are clickable/selectable
- Font: Sans-serif (Inter or similar)
- Accessible colors (WCAG AA compliant)

FOOTER:
- Left: "Skip wizard" link (gray, small)
- Right: "Next →" button (disabled/gray until selection made)

DIMENSIONS: 1200x800px (desktop view)
```

---

## 🎨 Prompt 2: Step 2 - Timezone Setup (CRITICAL!)

```text
Create a modern UI mockup for a calendar configuration wizard - Step 2 (Timezone Setup).

LAYOUT:
- White background
- Top: Progress indicator "Step 2 of 5" with filled dots on steps 1-2
- Heading: "Timezone & Location Setup"

SECTION 1 - AUTO-DETECTION (top):
Box with light green background (#E8F5E9):
- Icon: ✅ checkmark
- Text: "We've detected your timezone: Europe/Warsaw (GMT+1)"
- Small link below: "Change timezone"

SECTION 2 - CROSS-TIMEZONE QUESTION (middle):
- Question: "Will users book from different timezones?"
- Subtext: "For example, telehealth appointments with patients in other regions"
- Two radio buttons:
  ○ "No - All users in same timezone" (selected by default)
  ○ "Yes - Users may be in different timezones"

SECTION 3 - AUSTRALIA DST WARNING (expanded view):
Red/orange warning box (#FFF3E0 background):
- Icon: ⚠️ warning triangle
- Heading: "AUSTRALIA DETECTED"
- Text:
  "Important: Australia has complex DST rules:
   • NSW, VIC, SA, TAS: DST observed
   • QLD, WA, NT: NO DST
   • This creates 5 different timezone zones during summer

   We'll handle this automatically, but please verify times
   carefully in Preview (Step 5)."
- Link at bottom: "Learn more about DST handling →"

TECHNICAL INFO BOX (bottom, light blue #E1F5FF):
- Icon: ℹ️ info
- Text: "All times will be stored in UTC and displayed in local timezone"

FOOTER:
- Left: "← Back" button
- Right: "Next →" button (blue, enabled)

DESIGN STYLE:
- Healthcare/medical UI aesthetic
- Clear visual hierarchy
- Warning box prominent but not alarming
- Accessible design (WCAG AA)
- Font: Sans-serif

DIMENSIONS: 1200x900px
```

---

## 🎨 Prompt 3: Step 3 - Date/Time Configuration

```text
Create a modern, clean UI mockup for a calendar configuration wizard - Step 3 (Date & Time).

LAYOUT:
- White background
- Top: Progress indicator "Step 3 of 5" with filled dots on steps 1-3
- Heading: "Date & Time Configuration"
- Subtext: "Set your default availability and appointment rules"

CONTENT - FORM SECTION:
1. Slot Duration:
   - Radio options: 15 min, 30 min (selected with "Recommended" badge), 60 min, Custom
2. Availability:
   - Days: Weekday pills (M, T, W, T, F selected in blue; S, S unselected in gray)
   - Hours: "From 08:00 AM" to "06:00 PM" (modern dropdowns)
3. Booking Window:
   - Dropdown selected: "90 days ahead"
4. Buffer Time:
   - Radio options: None, 5 min, 10 min (selected), 15 min

INFO BOX (bottom):
- Light blue background
- Icon: ℹ️
- Text: "Buffer time allows for 10 minutes of preparation between each patient visit."

FOOTER:
- Left: "← Back" button
- Right: "Next →" button (blue, enabled)

DESIGN STYLE:
- HealthForge clean UI aesthetic
- Modern form controls
- Subtle borders and shadows
- Professional medical software feel

DIMENSIONS: 1200x900px
```

---

## 🎨 Prompt 4: Step 4 - Display Preferences

```text
Create a modern UI mockup for a calendar configuration wizard - Step 4 (Display Preferences).

LAYOUT:
- White background
- Top: Progress indicator "Step 4 of 5" with filled dots on steps 1-4
- Heading: "Display & Permissions"

LEFT PANEL - PREFERENCES:
1. Default View:
   - Segmented control: [Month] [Week (Selected)] [Day]
2. Info to Display:
   - Checkboxes: [x] Time, [x] Patient Name, [ ] Location, [x] Status
3. User Permissions:
   - Toggle switches:
     - [On] Allow creating new appointments
     - [On] Allow editing
     - [Off] Allow deleting

RIGHT PANEL - PREVIEW CARD:
- A small "Live Preview" card showing a mini week view
- Clean layout with blue accent for appointments

FOOTER:
- Left: "← Back" button
- Right: "Next →" button (blue, enabled)

DESIGN STYLE:
- Professional, high-fidelity UI
- Segmented controls and toggle switches should look premium
- Healthcare-inspired icons

DIMENSIONS: 1200x850px
```

---

## 🎨 Prompt 3: Step 5 - Preview & Test

```text
Create a modern UI mockup for a calendar configuration wizard - Step 5 (Preview & Test).

LAYOUT:
- White background
- Top: Progress indicator "Step 5 of 5" with all 5 dots filled
- Heading: "Preview & Test Your Calendar"
- Subtext: "Review your settings and test booking before deployment"

LEFT PANEL (40% width) - VALIDATION CHECKLIST:
White box with rounded corners, titled "Configuration Summary":

✅ Use Case: Patient Appointments
✅ Timezone: Europe/Warsaw (GMT+1)
   • Cross-timezone: Disabled
✅ Availability: Mon-Fri, 8:00 AM - 6:00 PM
✅ Slot duration: 30 minutes
✅ Buffer time: 10 minutes
✅ Booking window: 90 days ahead
✅ No configuration errors detected

Button below: "🧪 Book Sample Appointment" (outlined, blue)

RIGHT PANEL (60% width) - CALENDAR PREVIEW:
Interactive calendar widget showing:
- Month view (February 2026)
- Today highlighted
- Available time slots shown (green)
- Timezone displayed at top: "Showing times in: Europe/Warsaw (GMT+1)"
- Sample appointment: "9:00 AM - Dr. Smith" (blue block)
- Hover tooltip: "February 10, 9:00 AM (30 min)"

BELOW CALENDAR:
Test booking confirmation (light green box #E8F5E9):
- Icon: ✅
- Text: "Test booking successful!
        Appointment created: Feb 10, 9:00 AM - 9:30 AM
        Timezone verified: Europe/Warsaw"

FOOTER:
- Left: "← Back" button
- Center: "Save as Draft" button (gray outline)
- Right: "✅ DEPLOY" button (large, green, prominent)

DESIGN STYLE:
- Modern healthcare UI
- Calendar looks realistic (like FullCalendar.js)
- Clear visual feedback for validation
- Professional, clean design
- Accessible (WCAG AA)

DIMENSIONS: 1400x1000px (wider for calendar preview)
```

---

## 🎨 Prompt 4: Progress Indicator (Optional)

```text
Create a simple horizontal progress indicator for a 5-step wizard.

DESIGN:
- 5 circular steps connected by lines
- Each step numbered: 1, 2, 3, 4, 5
- Step labels below circles:
  1. "Use Case"
  2. "Timezone"
  3. "Configuration"
  4. "Display"
  5. "Preview"

STATES (show 3 variations):
1. Step 1 active (step 1 filled blue, others gray outline)
2. Step 2 active (steps 1-2 filled blue, 3-5 gray outline)
3. Step 5 active (all steps filled blue - complete)

STYLE:
- Modern, minimal design
- Blue: #2196F3
- Gray: #BDBDBD
- Line thickness: 2px
- Circle diameter: 40px
- Font: Sans-serif, 12px for labels

DIMENSIONS: 800x120px
```

---

## 🎨 Prompt 5: Complete Wizard Flow (Optional)

```text
Create an overview showing all 5 wizard steps in a single image.

LAYOUT:
Vertical flow with 5 panels, each showing a simplified version of the step:

STEP 1: Use Case Selection (5 cards with icons)
↓ (arrow)

STEP 2: Timezone Setup (auto-detect box + warning)
↓

STEP 3: Date/Time Config (form fields: slot duration, hours, etc.)
↓

STEP 4: Display Preferences (calendar view options, checkboxes)
↓

STEP 5: Preview & Test (mini calendar + validation checklist)

STYLE:
- Each step in a light gray rounded box
- Step numbers prominent (1-5)
- Arrows between steps
- Simplified/condensed view of each step
- Healthcare UI aesthetic
- Clean, professional

DIMENSIONS: 1000x2000px (tall, vertical flow)
```

---

## 📝 INSTRUKCJE UŻYCIA

### Krok 1: Gemini

1. Otwórz: <https://gemini.google.com>
2. Wklej jeden z promptów powyżej
3. Poczekaj na wygenerowanie obrazu
4. Download obrazu jako PNG

### Krok 2: NanoBanana (alternatywa)

1. Skopiuj prompt
2. Użyj w NanoBanana z Gemini backend
3. Export PNG

### Krok 3: Zapisz pliki

Zapisz wygenerowane obrazy jako:

- `docs/mockups/step-1-use-case.png`
- `docs/mockups/step-2-timezone.png`
- `docs/mockups/step-5-preview.png`
- `docs/mockups/progress-indicator.png` (optional)
- `docs/mockups/full-flow.png` (optional)

### Krok 4: Wrzuć na Miro

- Dodaj mockupy do swojego Miro board
- Oznacz jako "UI Mockups - Wizard Flow"

### Krok 5: Git

```bash
cd /c/Users/artur/Desktop/Projekty/healthforge-calendar-wizard
git add docs/mockups/
git commit -m "feat: Add visual mockups for wizard steps 1, 2, 5"
git push
```

---

## 🎯 PRIORYTET

**Must-have (min 2 mockupy):**

1. ✅ **Step 2 - Timezone** (NAJWAŻNIEJSZE! - pokazuje Australia warning)
2. ✅ **Step 1 - Use Case** (początek wizarda, medical templates)

**Nice-to-have:**
3. Step 5 - Preview (pokazuje validation)
4. Progress Indicator
5. Full Flow

---

## 💡 TIPS

- **Iteruj:** Jeśli pierwszy output nie jest idealny, popraw prompt:
  - "Make the warning box more prominent"
  - "Use softer colors"
  - "Make text larger"

- **Spójność:** Użyj tych samych kolorów we wszystkich mockupach:
  - Primary blue: #2196F3
  - Success green: #4CAF50
  - Warning orange: #FF9800
  - Error red: #F44336

- **Jakość:** Poproś o "high resolution, 2x scale" jeśli obraz jest rozmazany

---

**Gotowe do użycia! Skopiuj prompty i wklej w Gemini!** 🚀
