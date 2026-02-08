# Calendar Wizard Flow Design

**Project:** HealthForge Calendar Wizard
**Date:** 2026-02-07
**Designer:** Product Manager + UX
**Status:** Draft for Review

---

## EXECUTIVE SUMMARY

Designed 5-step wizard flow that:
- Reduces setup time from 45 min → <5 min
- **Proactively prevents timezone errors** (Priority #1 problem)
- Guides non-technical users (Kasia persona)
- Provides escape hatch for advanced users
- Includes preview/test before deployment

**Key Innovation:** Step 2 (Timezone Setup) is PROACTIVE - detects problematic scenarios and warns BEFORE configuration, not after.

---

## WIZARD OVERVIEW

### Entry Point
User drags Calendar widget from Advanced section to canvas → Wizard automatically pops up (modal or side panel).

### Total Steps: 5
1. Use Case Selection
2. ⭐ Timezone & Locale Setup (Critical)
3. Date/Time Configuration
4. Display Preferences
5. Preview & Test

### Estimated Time: 3-5 minutes

### Exit Options
- **Complete wizard** → Calendar deployed with full configuration
- **Skip wizard** (link) → Manual configuration (for advanced users)
- **Save draft** → Wizard state saved, can return later

---

## STEP-BY-STEP FLOW

---

## STEP 1: Use Case Selection

### Objective
Identify user's primary calendar use case to load appropriate template with smart defaults.

### UI Layout
```
┌─────────────────────────────────────────────────────┐
│  Calendar Setup Wizard                      [Step 1 of 5] │
├─────────────────────────────────────────────────────┤
│                                                       │
│  What will you use this calendar for?                │
│                                                       │
│  ┌──────────────────────────────────────────────┐  │
│  │  📅  Patient Appointments                     │  │
│  │  Schedule patient visits, consultations       │  │
│  │  [SELECT]                                     │  │
│  └──────────────────────────────────────────────┘  │
│                                                       │
│  ┌──────────────────────────────────────────────┐  │
│  │  🏥  Resource & Equipment Booking             │  │
│  │  Operating rooms, MRI machines, treatment bays│  │
│  │  [SELECT]                                     │  │
│  └──────────────────────────────────────────────┘  │
│                                                       │
│  ┌──────────────────────────────────────────────┐  │
│  │  👥  Staff Scheduling                         │  │
│  │  Doctor/nurse shifts, on-call rotations      │  │
│  │  [SELECT]                                     │  │
│  └──────────────────────────────────────────────┘  │
│                                                       │
│  ┌──────────────────────────────────────────────┐  │
│  │  📋  Events & Meetings                        │  │
│  │  Training sessions, department meetings       │  │
│  │  [SELECT]                                     │  │
│  └──────────────────────────────────────────────┘  │
│                                                       │
│  ┌──────────────────────────────────────────────┐  │
│  │  ⚙️  Other / Custom                           │  │
│  │  I'll configure it myself                     │  │
│  │  [SELECT]                                     │  │
│  └──────────────────────────────────────────────┘  │
│                                                       │
│  [Skip wizard - Configure manually] ─────────────────│
│                                                       │
│                            [← BACK]  [NEXT →]        │
└─────────────────────────────────────────────────────┘
```

### Options

**1. Patient Appointments** (Recommended for majority)
- Icon: 📅
- Description: "Schedule patient visits, consultations, and follow-ups"
- Loads: Appointment template
- Defaults:
  - 30-min slots
  - Business hours: 8 AM - 6 PM
  - Booking window: 90 days ahead
  - Required fields: Patient name, contact, appointment type

**2. Resource & Equipment Booking**
- Icon: 🏥
- Description: "Operating rooms, MRI machines, treatment bays"
- Loads: Resource template
- Defaults:
  - Flexible duration (user-defined per booking)
  - 24/7 availability (configurable)
  - Required fields: Resource name, booking purpose, responsible person

**3. Staff Scheduling**
- Icon: 👥
- Description: "Doctor/nurse shifts, on-call rotations"
- Loads: Shift template
- Defaults:
  - 8-hour shifts
  - Weekly view
  - Required fields: Staff member, shift type, location

**4. Events & Meetings**
- Icon: 📋
- Description: "Training sessions, department meetings"
- Loads: Events template
- Defaults:
  - 1-hour events
  - Monthly view
  - Required fields: Event name, organizer, attendees

**5. Other / Custom**
- Icon: ⚙️
- Description: "I'll configure it myself"
- Loads: Minimal defaults
- Proceeds to manual-like configuration

### Logic
- Selection → Wizard loads corresponding template
- Template = pre-configured defaults for steps 2-4
- User can override any default in subsequent steps

### Validation
- Required: User must select one option to proceed

### Back Navigation
- N/A (first step)

---

## STEP 2: ⭐ Timezone & Locale Setup (CRITICAL)

### Objective
**PROACTIVELY prevent timezone errors** - highest priority (RICE 2400).

Auto-detect user timezone, identify problematic scenarios (DST, cross-timezone), configure UTC storage + local display.

### UI Layout (Single-Timezone Scenario)
```
┌─────────────────────────────────────────────────────┐
│  Calendar Setup Wizard                      [Step 2 of 5] │
├─────────────────────────────────────────────────────┤
│                                                       │
│  Timezone & Regional Settings                        │
│                                                       │
│  ✅ We've detected your timezone:                    │
│     Europe/Warsaw (GMT+1)                            │
│     [Change timezone]                                │
│                                                       │
│  Question: Will users book appointments from other   │
│  time zones? (e.g., telehealth, multi-location)     │
│                                                       │
│  ⚪ No - All users are in the same timezone          │
│  ⚪ Yes - Users may be in different timezones        │
│                                                       │
│  [i] Info: We'll store all times in UTC and display  │
│      them in each user's local timezone automatically│
│                                                       │
│  Date Format:                                         │
│  ⚪ DD/MM/YYYY (European)                             │
│  ⚪ MM/DD/YYYY (US)                                   │
│  ⚪ YYYY-MM-DD (ISO)                                  │
│                                                       │
│  Time Format:                                         │
│  ⚪ 24-hour (14:30)                                   │
│  ⚪ 12-hour (2:30 PM)                                 │
│                                                       │
│                                                       │
│                            [← BACK]  [NEXT →]        │
└─────────────────────────────────────────────────────┘
```

### UI Layout (Cross-Timezone Scenario - User selects "Yes")
```
┌─────────────────────────────────────────────────────┐
│  Calendar Setup Wizard                      [Step 2 of 5] │
├─────────────────────────────────────────────────────┤
│                                                       │
│  Cross-Timezone Setup                                 │
│                                                       │
│  You've indicated users will be in different         │
│  timezones. Please select which regions:             │
│                                                       │
│  ☑ Europe                                            │
│  ☑ North America                                     │
│  ☐ Asia                                               │
│  ☐ Australia/Oceania                                  │
│  ☐ South America                                      │
│  ☐ Africa                                             │
│                                                       │
│  ⚠️ AUSTRALIA DETECTED                               │
│  ┌──────────────────────────────────────────────┐  │
│  │ Important: Australia has complex DST rules:   │  │
│  │                                                │  │
│  │ • NSW, VIC, SA, TAS: DST observed            │  │
│  │ • QLD, WA, NT: NO DST                         │  │
│  │ • This creates 5 different time zones during  │  │
│  │   Australian summer                           │  │
│  │                                                │  │
│  │ We'll automatically handle this, but please   │  │
│  │ verify appointment times are displayed        │  │
│  │ correctly in your preview (Step 5).          │  │
│  │                                                │  │
│  │ [Learn more about DST handling →]             │  │
│  └──────────────────────────────────────────────┘  │
│                                                       │
│  Configuration:                                       │
│  ✅ Store times in UTC                                │
│  ✅ Display in user's local timezone                  │
│  ✅ Auto-adjust for DST transitions                   │
│                                                       │
│                            [← BACK]  [NEXT →]        │
└─────────────────────────────────────────────────────┘
```

### Detection Logic

**1. Auto-Detect User Timezone**
```javascript
// Browser API
const userTimezone = Intl.DateTimeFormat().resolvedOptions().timeZone;
// Example: "Europe/Warsaw", "America/New_York", "Australia/Sydney"
```

**2. DST Detection**
```javascript
// Check if timezone observes DST
function hasDST(timezone) {
  const jan = new Date(2026, 0, 1);
  const jul = new Date(2026, 6, 1);
  const janOffset = getTimezoneOffset(jan, timezone);
  const julOffset = getTimezoneOffset(jul, timezone);
  return janOffset !== julOffset;
}
```

**3. Australia Detection**
```javascript
// If user selects Australia/Oceania OR detected timezone is Australia/*
if (timezone.startsWith('Australia/')) {
  showAustraliaDSTWarning();
}
```

### Cross-Timezone Questions (if "Yes" selected)

**"Which regions will your users be in?"**
- Multi-select checkboxes
- Options:
  - Europe
  - North America (US/Canada/Mexico)
  - Asia
  - Australia/Oceania ⚠️ (triggers warning)
  - South America
  - Africa
  - Middle East

**Australia Warning (if selected):**
```
⚠️ AUSTRALIA DETECTED

Important: Australia has complex DST rules:
• NSW, VIC, SA, TAS: DST observed
• QLD, WA, NT: NO DST
• This creates 5 different time zones during Australian summer

We'll automatically handle this, but please verify appointment
times are displayed correctly in your preview (Step 5).

[Learn more about DST handling →] (opens help doc)
```

### Configuration Applied (Behind the Scenes)

**Single Timezone:**
- Storage: UTC
- Display: User's detected timezone
- DST: Auto-handled by Luxon/date-fns-tz

**Cross-Timezone:**
- Storage: UTC (always)
- Display: Each user sees their local timezone
- Timezone display: "Europe/Warsaw (GMT+1)" shown explicitly in calendar
- Warning: DST transitions shown before/after time change

### Validation

**Required:**
- Timezone must be confirmed (auto-detected, user can change)
- Cross-timezone question must be answered

**Optional:**
- Region selection (only if cross-timezone = Yes)

### Smart Defaults

Based on Step 1 use case:
- **Patient Appointments:** Likely cross-timezone (telehealth) → Default "Yes" pre-selected
- **Resource/Equipment:** Likely same location → Default "No" pre-selected
- **Staff Scheduling:** Likely same location → Default "No" pre-selected
- **Events:** Depends → No default

### Edge Cases

**User Changes Timezone:**
- Dropdown with all IANA timezone options
- Search/filter enabled (long list)

**No Timezone Detected (unlikely):**
- Force user to select from dropdown
- No auto-detection fallback

**Multiple Facilities/Locations:**
- User may need separate calendars for each location
- Warning: "Consider creating separate calendars for each facility if they're in different timezones"

### Help/Info Tooltips

**"Why UTC storage?"**
> "Storing times in UTC (Coordinated Universal Time) ensures accuracy across timezones and prevents errors during DST transitions. Users always see times in their local timezone."

**"What if my users don't know timezones?"**
> "Don't worry - they won't need to. The calendar automatically detects each user's timezone and shows times correctly. They just see their local time."

### Back Navigation
- ← BACK returns to Step 1
- Selections preserved (user can change use case)

---

## STEP 3: Date/Time Configuration

### Objective
Configure how calendar handles dates, times, slots, and availability.

### UI Layout
```
┌─────────────────────────────────────────────────────┐
│  Calendar Setup Wizard                      [Step 3 of 5] │
├─────────────────────────────────────────────────────┤
│                                                       │
│  Date & Time Settings                                │
│                                                       │
│  Appointment Duration (Slot Size):                   │
│  ⚪ 15 minutes                                        │
│  ⚪ 30 minutes ✓ (Recommended for appointments)      │
│  ⚪ 60 minutes                                        │
│  ⚪ Custom: [___] minutes                             │
│                                                       │
│  Availability (When can appointments be booked?):    │
│  Days:     ☑ Mon  ☑ Tue  ☑ Wed  ☑ Thu  ☑ Fri        │
│            ☐ Sat  ☐ Sun                              │
│                                                       │
│  Hours:    From: [08:00 ▼]  To: [18:00 ▼]          │
│                                                       │
│  Booking Window (How far ahead?):                    │
│  ⚪ 30 days                                           │
│  ⚪ 90 days ✓ (Recommended)                          │
│  ⚪ 6 months                                          │
│  ⚪ 1 year                                            │
│  ⚪ No limit                                          │
│                                                       │
│  Buffer Time (Between appointments):                 │
│  ⚪ None                                              │
│  ⚪ 5 minutes                                         │
│  ⚪ 10 minutes ✓                                      │
│  ⚪ 15 minutes                                        │
│                                                       │
│  [i] Info: Buffer time prevents back-to-back         │
│      appointments and allows for cleanup/prep.       │
│                                                       │
│                                                       │
│                            [← BACK]  [NEXT →]        │
└─────────────────────────────────────────────────────┘
```

### Fields

**1. Appointment Duration (Slot Size)**
- Options: 15 min, 30 min, 60 min, Custom
- Smart default based on Step 1:
  - Patient Appointments: 30 min
  - Resource Booking: 60 min (flexible)
  - Staff Scheduling: 480 min (8 hours)
  - Events: 60 min

**2. Availability**
- Days: Multi-select checkboxes (Mon-Sun)
- Hours: From/To dropdowns (30-min increments)
- Smart default:
  - Patient Appointments: Mon-Fri, 8 AM - 6 PM
  - Resource: 24/7 (all days, all hours)
  - Staff: Mon-Sun, 24/7 (shift coverage)
  - Events: Mon-Fri, 9 AM - 5 PM

**3. Booking Window**
- How far in advance can users book?
- Options: 30 days, 90 days, 6 months, 1 year, No limit
- Smart default:
  - Patient: 90 days (standard for healthcare)
  - Resource: 30 days (shorter planning window)
  - Staff: No limit (long-term roster)
  - Events: 6 months

**4. Buffer Time**
- Time between appointments for prep/cleanup
- Options: None, 5, 10, 15 minutes
- Smart default:
  - Patient: 10 min (cleanup, sanitization)
  - Resource: 15 min (room turnover)
  - Staff: None (shifts are contiguous)
  - Events: 5 min (buffer between meetings)

### Validation

**Required:**
- Slot duration must be > 0
- At least one day selected
- Hours: "From" must be before "To"

**Warnings:**
- If "To" is before "From" (crosses midnight): "Availability spans midnight. Confirm this is correct."
- If no days selected: "You must select at least one day."

### Smart Defaults Logic

Defaults already pre-filled based on Step 1 use case. User can override.

### Back Navigation
- ← BACK returns to Step 2
- All selections preserved

---

## STEP 4: Display Preferences

### Objective
Configure how calendar is visually displayed and which fields are shown.

### UI Layout
```
┌─────────────────────────────────────────────────────┐
│  Calendar Setup Wizard                      [Step 4 of 5] │
├─────────────────────────────────────────────────────┤
│                                                       │
│  Display Settings                                     │
│                                                       │
│  Default Calendar View:                              │
│  ⚪ Month view (Overview of full month)              │
│  ⚪ Week view ✓ (Recommended for appointments)       │
│  ⚪ Day view (Detailed hourly schedule)              │
│                                                       │
│  [Preview of selected view]                          │
│  ┌──────────────────────────────────────────────┐  │
│  │   MON    TUE    WED    THU    FRI            │  │
│  │  8:00   [____] [____] [____] [____]          │  │
│  │  8:30   [____] [____] [____] [____]          │  │
│  │  9:00   [Appt] [____] [Appt] [____]          │  │
│  │  ...                                          │  │
│  └──────────────────────────────────────────────┘  │
│                                                       │
│  Information to Display on Calendar:                 │
│  ☑ Appointment time                                  │
│  ☑ Patient/client name                               │
│  ☐ Appointment type                                  │
│  ☐ Location                                          │
│  ☐ Status (confirmed/pending)                        │
│                                                       │
│  Allow Users to:                                     │
│  ☑ Create new appointments                           │
│  ☑ Edit existing appointments                        │
│  ☑ Delete appointments                               │
│  ☑ View appointment details                          │
│                                                       │
│  [Advanced Settings →] (escape hatch)                │
│                                                       │
│                            [← BACK]  [NEXT →]        │
└─────────────────────────────────────────────────────┘
```

### Fields

**1. Default Calendar View**
- Month, Week, Day
- Smart default based on Step 1:
  - Patient Appointments: Week view (see availability at a glance)
  - Resource: Day view (detailed hourly schedule)
  - Staff: Week view (overview of shifts)
  - Events: Month view (long-term planning)

**2. Information to Display**
- Multi-select checkboxes
- Options (based on Step 1 template):
  - Patient Appointments: Time, Name, Type, Location, Status
  - Resource: Time, Resource name, Purpose, Responsible person
  - Staff: Time, Staff member, Shift type, Location
  - Events: Time, Event name, Organizer, Attendees

**3. User Permissions**
- What can end-users do?
- Options: Create, Edit, Delete, View details
- Smart defaults: All enabled (can be restricted later)

**4. Advanced Settings (Escape Hatch)**
- Link to full manual configuration
- "Need more control? Configure advanced settings manually."
- Opens property panel with all options

### Validation

**Required:**
- Calendar view must be selected
- At least "View details" permission enabled

### Back Navigation
- ← BACK returns to Step 3
- All selections preserved

---

## STEP 5: Preview & Test ⭐

### Objective
**Prevent production errors** - let user test calendar before deployment.

Interactive preview shows how calendar will look with sample data. User can test booking scenario.

### UI Layout
```
┌─────────────────────────────────────────────────────┐
│  Calendar Setup Wizard                      [Step 5 of 5] │
├─────────────────────────────────────────────────────┤
│                                                       │
│  Preview Your Calendar                               │
│                                                       │
│  This is how your calendar will look:                │
│                                                       │
│  ┌──────────────────────────────────────────────┐  │
│  │  [< February 2026 >]          [Week View ▼]  │  │
│  │                                               │  │
│  │   MON 10  TUE 11  WED 12  THU 13  FRI 14    │  │
│  │  8:00                                         │  │
│  │  8:30   [John Doe]  [________]  [________]   │  │
│  │  9:00   [________]  [Jane Smi]  [________]   │  │
│  │  9:30   [________]  [________]  [Test User]  │  │
│  │ 10:00   [________]  [________]  [________]   │  │
│  │  ...                                          │  │
│  │                                               │  │
│  │  Timezone: Europe/Warsaw (GMT+1)             │  │
│  └──────────────────────────────────────────────┘  │
│                                                       │
│  ✅ Test: Try booking an appointment                 │
│  [Book Sample Appointment]                           │
│                                                       │
│  Validation:                                          │
│  ✅ Timezone configured correctly                    │
│  ✅ Availability matches your settings               │
│  ✅ Slot duration: 30 minutes                        │
│  ✅ No configuration errors detected                 │
│                                                       │
│  ⚠️ Reminders:                                       │
│  • If users are in different timezones, they'll see │
│    times in THEIR local timezone automatically      │
│  • DST transitions will be handled automatically    │
│                                                       │
│  Need to change something?                           │
│  [← Go back to edit]                                 │
│                                                       │
│                                                       │
│           [CANCEL]  [SAVE AS DRAFT]  [DEPLOY →]     │
└─────────────────────────────────────────────────────┘
```

### Features

**1. Interactive Preview**
- Shows actual calendar with sample appointments
- User can interact: click slots, view details
- **Timezone displayed explicitly:** "Europe/Warsaw (GMT+1)"

**2. Test Booking**
- Button: "Book Sample Appointment"
- Opens booking modal
- User fills: Name, Time slot
- Appointment appears in calendar → Confirms setup works

**3. Validation Checklist**
- ✅ Auto-checks configuration
- Displays:
  - ✅ Timezone configured correctly
  - ✅ Availability matches settings
  - ✅ Slot duration correct
  - ✅ No errors detected
- OR warnings:
  - ⚠️ "No availability configured - calendar will be empty"
  - ⚠️ "Cross-timezone setup detected - verify times display correctly"

**4. Reminders (Context-Sensitive)**

If cross-timezone enabled:
```
⚠️ Reminders:
• Users in different timezones will see times in THEIR local timezone
• Example: 2:00 PM in New York = 8:00 PM in Warsaw
• DST transitions handled automatically
```

If Australia selected:
```
⚠️ Australia DST Reminder:
• Australia has complex DST rules (5 timezones during summer)
• Verify times are correct for your specific state
• QLD/WA/NT do NOT observe DST
```

**5. Edit Options**
- [← Go back to edit] - Returns to previous steps
- [Advanced Settings] - Opens manual config

### Validation

**Required before Deploy:**
- User must test booking (or explicitly skip: "I'll test later")
- No critical errors detected

**Warnings (Non-Blocking):**
- User can proceed despite warnings

### Actions

**CANCEL**
- Discard wizard, return to manual config
- Confirmation: "Are you sure? Your progress will be lost."

**SAVE AS DRAFT**
- Save wizard state
- Calendar NOT deployed yet
- User can return later: "Continue setup"

**DEPLOY →**
- Apply configuration to Calendar widget
- Widget appears on canvas, fully configured
- Success message: "✅ Calendar configured successfully!"

---

## DECISION TREE / BRANCHING LOGIC

```
START: User drags Calendar widget
  ↓
STEP 1: Use Case Selection
  │
  ├─→ Patient Appointments ──→ Load Appointment Template
  ├─→ Resource Booking ──────→ Load Resource Template
  ├─→ Staff Scheduling ──────→ Load Shift Template
  ├─→ Events & Meetings ─────→ Load Events Template
  └─→ Other/Custom ──────────→ Load Minimal Template
  ↓
STEP 2: Timezone Setup
  │
  ├─→ Auto-detect timezone
  │
  ├─→ Q: Cross-timezone? NO ──→ Single-timezone config → STEP 3
  │
  └─→ Q: Cross-timezone? YES ─→ Select regions
                                  │
                                  ├─→ Australia selected? NO → STEP 3
                                  │
                                  └─→ Australia selected? YES → Show DST Warning → STEP 3
  ↓
STEP 3: Date/Time Configuration
  │
  └─→ Smart defaults loaded (based on Step 1) → User can override → STEP 4
  ↓
STEP 4: Display Preferences
  │
  ├─→ Configure view + fields
  │
  └─→ [Advanced Settings] → Escape to manual config (optional)
  ↓
STEP 5: Preview & Test
  │
  ├─→ Show preview
  ├─→ Run validation
  ├─→ Show warnings (if any)
  │
  ├─→ User tests booking → Success → DEPLOY
  │
  ├─→ User finds issue → [← Go Back] → Edit previous steps
  │
  ├─→ User satisfied → DEPLOY → Calendar configured ✅
  │
  └─→ Or → SAVE AS DRAFT / CANCEL
```

---

## ERROR PREVENTION STRATEGIES

### 1. Proactive Timezone Warnings (Step 2)
- **BEFORE** user finishes setup, not after
- Australia DST warning shown immediately when region selected
- Clear explanation of complexity

### 2. Smart Defaults (All Steps)
- Pre-fill fields based on use case
- Reduces cognitive load
- User can override but doesn't have to figure out from scratch

### 3. Validation (Step 5)
- Automated checks before deployment
- Catches errors: missing availability, conflicting settings, etc.
- Non-blocking warnings (user can proceed but aware)

### 4. Preview/Test (Step 5)
- Interactive preview = confidence boost
- Test booking verifies setup works
- Prevents "deploy and then discover errors"

### 5. Clear Language (All Steps)
- No technical jargon
- Explain "why" (e.g., "Why UTC storage?")
- Visual aids (calendar preview, timezone map)

---

## ESCAPE HATCHES (For Advanced Users)

### 1. Skip Wizard Entirely
- Link at top: "Skip wizard - Configure manually"
- For users who know what they're doing
- Proceeds directly to property panel

### 2. Advanced Settings Link (Step 4)
- "Need more control? Configure advanced settings manually."
- Opens property panel while preserving wizard progress
- Can return to wizard

### 3. Save as Draft
- Partial configuration saved
- User can return later: "Continue calendar setup"
- Useful if interrupted or need more info

### 4. Back Navigation (Every Step)
- [← BACK] button
- Preserves selections
- No loss of progress

---

## ACCESSIBILITY (WCAG 2.1 AA)

### Keyboard Navigation
- Tab order: logical (top-to-bottom, left-to-right)
- Enter/Space: Select options
- Arrow keys: Navigate radio buttons/checkboxes
- Esc: Cancel/close wizard

### Screen Reader Support
- All form fields labeled
- Aria-labels for icons
- Step indicator announced: "Step 2 of 5: Timezone Setup"
- Validation errors announced

### Visual
- High contrast text (minimum 4.5:1 ratio)
- Large touch targets (min 44×44px)
- Clear focus indicators
- Icons + text labels (not just icons)

### Color
- Don't rely on color alone for warnings
- ⚠️ Warning icon + text
- ✅ Success icon + text

---

## MOBILE/TABLET CONSIDERATIONS

### Responsive Design
- Wizard adapts to smaller screens
- Stack options vertically (not horizontal)
- Larger touch targets on mobile

### Touch Gestures
- Swipe left/right to navigate steps (optional)
- Tap to select options
- Pinch-to-zoom on preview calendar (Step 5)

### Performance
- Wizard loads <500ms (UX requirement)
- Preview calendar renders <1s
- No lag during interaction

---

## SUCCESS METRICS (Wizard Flow)

### Completion Rate
- **Target:** 80%+
- **Measure:** % of users who complete wizard (Deploy) vs abandon

### Time to Complete
- **Target:** 3-5 minutes
- **Measure:** Timestamp from Step 1 start to Deploy click

### Back Navigation Rate
- **Target:** <30%
- **Measure:** % of users who use [← BACK] button (indicates confusion)

### Skip Rate
- **Target:** <20%
- **Measure:** % of users who click "Skip wizard"

### Validation Errors
- **Target:** <10%
- **Measure:** % of users who see validation errors in Step 5

### Test Booking Usage
- **Target:** >60%
- **Measure:** % of users who click "Book Sample Appointment" in Step 5

---

## NEXT STEPS

1. ✅ Wizard Flow Design Complete (This Document)
2. ⏳ **Design Mockups** (UI/UX team)
   - High-fidelity designs for all 5 steps
   - Interactive prototype (Figma)
3. ⏳ **PRD Writing** (Task #6)
   - Incorporate wizard flow into PRD
4. ⏳ **User Stories** (Task #7)
   - Break down wizard into user stories
5. ⏳ **Dev Handoff**
   - Technical specification
   - API requirements
   - Data model

---

**Wizard Flow Design Complete** | Ready for PRD integration
