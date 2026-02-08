# Product Requirements Document (PRD)
## HealthForge Calendar Wizard

**Version:** 1.0
**Date:** 2026-02-07
**Status:** Draft for Review
**Author:** Product Manager (Artur)
**Stakeholders:** Engineering, Design, Product, Healthcare Solutions Team

---

## 1. EXECUTIVE SUMMARY

### Problem
The Calendar widget in HealthForge is a popular component but suffers from high configuration complexity. Users face:
- 20-45 minutes average setup time for a working calendar
- ~25-30% of deployed calendars have timezone errors that surface only in production
- Analysis paralysis from dozens of configuration options without guidance
- Lack of healthcare-specific context and templates
- High support ticket volume (calendar configuration is top support category)

### Solution
A 5-step configuration wizard that guides users through calendar setup in <5 minutes with proactive timezone error prevention, medical use case templates, and interactive preview/testing. The wizard transforms a complex manual process into a guided, confidence-building experience.

### Business Impact
- **Timezone errors:** 25-30% → <5%
- **Time-to-working-calendar:** 20-45 min → <5 min
- **Widget adoption:** +40% increase expected
- **Support tickets:** -60% reduction
- **Completion rate:** 35% → 80%+

### North Star Metric
"Number of users with a working calendar (without timezone errors) within 7 days of adding the widget"

### Market Differentiation
Competitive analysis shows NO major low-code platform (Retool, Bubble.io, OutSystems) has a dedicated calendar configuration wizard. This represents a significant opportunity for HealthForge to differentiate, especially given the healthcare focus where timezone accuracy is critical for patient care.

---

## 2. PROBLEM STATEMENT

### 2.1 Core Problems (RICE Prioritized)

| Priority | Problem | RICE Score | Impact |
|----------|---------|------------|--------|
| #1 | Timezone errors in production | 2400 | Patient care implications, 25-30% error rate |
| #2 | High entry barrier (time/complexity) | 1200 | 45min setup blocks adoption |
| #3 | Option overload (analysis paralysis) | 960 | Cognitive overload, confusion |
| #4 | Lack of medical context | 720 | Generic calendar doesn't fit healthcare workflows |
| #5 | General configuration errors | 540 | Rework, frustration, support burden |

### 2.2 Problem Details

#### Timezone Errors (Priority #1 - RICE 2400)
- **Current State:** ~25-30% of calendars have timezone issues (DST transitions, cross-timezone booking, UTC vs local confusion)
- **Healthcare Impact:** Wrong appointment times = missed patient care, medication timing errors, multi-campus coordination failures
- **Australia Challenge:** 5 timezone zones during DST (NSW/VIC/SA/TAS observe DST, QLD/WA/NT do not), creates border complications
- **User Experience:** Errors surface only when end-users (patients) use the calendar, causing rework and lost trust

#### High Entry Barrier (Priority #2 - RICE 1200)
- **Current State:** 20-45 minutes to configure even a simple appointment calendar
- **User Quote (Kasia persona):** "I'm afraid I'll break something. There are so many options I don't understand."
- **Adoption Blocker:** Non-technical healthcare coordinators avoid the Calendar widget entirely
- **Completion Rate:** Only 35% of users who start calendar configuration finish it

#### Option Overload (Priority #3 - RICE 960)
- **Current State:** Dozens of fields in property panel without contextual guidance
- **User Behavior:** Trial-and-error approach, copy-paste from documentation, support tickets
- **Competitive Insight:** Retool community forums show similar frustration patterns

---

## 3. GOALS & SUCCESS METRICS

### 3.1 Business Goals

**Primary:**
1. Reduce timezone error rate from 25-30% to <5%
2. Reduce time-to-working-calendar from 20-45 min to <5 min
3. Increase Calendar widget adoption by +40% within 3 months
4. Reduce calendar configuration support tickets by -60%

**Secondary:**
5. Increase wizard completion rate to 80%+
6. Achieve >60% test booking usage in Step 5 (Preview)
7. Maintain <20% wizard skip rate (advanced users)

### 3.2 Success Metrics & KPIs

| Metric | Baseline | Target | Measurement Method |
|--------|----------|--------|-------------------|
| **Timezone Error Rate** | 25-30% | <5% | % of calendars with timezone errors in first week of use |
| **Time-to-Working-Calendar** | 20-45 min | <5 min | Timestamp: widget drag to successful deployment |
| **Calendar Widget Adoption** | Current baseline | +40% | % of users who add Calendar widget to apps |
| **Support Tickets** | Current volume | -60% | # of calendar configuration tickets |
| **Wizard Completion Rate** | 35% (manual config) | 80%+ | % who complete wizard vs abandon |
| **User Satisfaction** | N/A | 4.5/5 | Post-wizard survey (NPS) |
| **Test Booking Usage** | N/A | >60% | % users who click "Book Sample Appointment" |
| **Back Navigation Rate** | N/A | <30% | % users who use [← BACK] (indicates confusion) |

### 3.3 Leading vs Lagging Indicators

**Leading Indicators (track weekly):**
- Wizard start rate
- Step completion by step (funnel analysis)
- Validation error rate at Step 5
- Skip wizard rate

**Lagging Indicators (track monthly):**
- Timezone error rate (7-day post-deployment)
- Support ticket volume
- Calendar widget adoption rate
- User retention with Calendar widget

---

## 4. USER PERSONAS

### 4.1 Primary Persona: Kasia - Medical Coordinator

**Demographics:**
- Age: 34
- Role: Medical coordinator at outpatient clinic
- Organization: 15 doctors, 4 locations
- Experience: 5 years in healthcare administration

**Technical Skills:** 2/5 (comfortable with Office, Gmail, basic apps; avoids complex tech)

**Job-to-be-Done:**
"Enable patients to book appointments online without involving front desk staff, freeing up 2-3 hours/week currently spent on manual calendar management"

**Frustrations:**
- Excel/Google Calendar don't integrate with clinic's patient management system
- Calendly is expensive and not tailored to Polish healthcare workflows
- Fears breaking technical configurations: "What if I mess something up?"
- Overwhelmed by technical jargon and too many options

**Success Criteria for Wizard:**
- Must complete setup in <10 minutes without technical assistance
- Must feel confident the calendar is correctly configured
- Must not encounter confusing technical terms
- Must prevent errors that would cause patient confusion

**Quote:** "I just want a calendar that works for patient appointments. I don't need all these advanced options."

---

### 4.2 Secondary Persona: Tomek - Hospital IT Admin

**Demographics:**
- Age: 42
- Role: IT administrator at district hospital
- Organization: 300-bed hospital
- Experience: 12 years in healthcare IT

**Technical Skills:** 4/5 (technical background, comfortable with code, but prefers low-code for speed)

**Job-to-be-Done:**
"Build a hospital resource booking system (operating rooms, equipment, staff) that integrates with legacy HIS and meets RODO/NFZ compliance requirements"

**Frustrations:**
- Low-code tools don't understand healthcare-specific workflows
- Integration with legacy Hospital Information Systems is complex
- Compliance requirements (RODO, NFZ audits) are non-negotiable
- Timezone handling for multi-campus hospitals is error-prone

**Success Criteria for Wizard:**
- Must support complex scheduling scenarios (OR blocks, equipment conflicts)
- Must provide escape hatch to advanced settings (doesn't want wizard limitations)
- Must handle cross-timezone scenarios correctly (telehealth, multi-campus)
- Must generate audit-compliant configurations

**Quote:** "I need the wizard to handle the basics correctly, but give me full control when I need it."

---

## 5. USE CASES

### 5.1 Top 3 Medical Use Cases (MVP Scope)

#### Use Case #1: Patient Appointment Booking ⭐ PRIMARY
**Priority:** Highest (RICE-based prioritization)
**Frequency:** Very High (daily, multiple times)
**Complexity:** Medium
**Timezone Sensitivity:** High (telehealth, cross-timezone patients)

**Scenario:**
Kasia needs to set up online booking for a multi-specialty clinic. Patients should be able to:
- Book appointments 24/7 online
- Select appointment type (consultation, follow-up, procedure)
- Choose preferred doctor and time slot
- Receive automated SMS/email confirmations
- Reschedule or cancel if needed

**Wizard Template: "Patient Appointments"**
- Slot duration: 30 minutes (default)
- Business hours: Mon-Fri, 8 AM - 6 PM
- Booking window: 90 days ahead
- Buffer time: 10 minutes (cleanup between patients)
- Required fields: Patient name, contact, appointment type
- Validation: Prevent double-booking, check slot availability

**Success Criteria:**
- Zero timezone errors for cross-timezone telehealth appointments
- <5 min setup time
- Calendar correctly displays availability
- Test booking succeeds in preview

---

#### Use Case #2: Resource & Equipment Booking
**Priority:** High (reusable pattern, medium complexity)
**Frequency:** High
**Complexity:** Medium
**Timezone Sensitivity:** Low (usually same-location)

**Scenario:**
Tomek needs to manage hospital resources: MRI machines, operating rooms, treatment bays, specialized equipment. Multiple departments need to:
- Reserve resources in advance
- Check real-time availability
- Specify booking purpose and responsible person
- Account for equipment maintenance downtime
- Prevent booking conflicts

**Wizard Template: "Resource Booking"**
- Slot duration: 60 minutes (flexible per booking)
- Availability: 24/7 (configurable)
- Booking window: 30 days ahead
- Buffer time: 15 minutes (room turnover)
- Required fields: Resource name, booking purpose, responsible person
- Validation: Check availability, prevent overlaps

---

#### Use Case #3: Staff Scheduling (Shifts)
**Priority:** Medium-High (complex constraints)
**Frequency:** Very High (weekly roster updates)
**Complexity:** High
**Timezone Sensitivity:** Medium (multi-location facilities)

**Scenario:**
Hospital needs to manage doctor and nurse shifts, including:
- 8-hour shifts (day/night/swing)
- On-call rotations
- Multi-location coverage
- Union constraints (max hours, min rest periods)
- PTO/vacation integration
- Shift swap capabilities

**Wizard Template: "Staff Scheduling"**
- Slot duration: 480 minutes (8 hours)
- Availability: 24/7, Mon-Sun
- Booking window: No limit (long-term roster planning)
- Buffer time: None (shifts are contiguous)
- Required fields: Staff member, shift type, location
- Validation: Check max hours, rest periods, prevent conflicts

---

### 5.2 Out of Scope Use Cases (Post-MVP)

**Operating Room Scheduling:**
- Very high complexity (multi-resource coordination, block scheduling, surgeon preferences)
- Requires advanced features beyond MVP scope
- Candidate for v1.1 with dedicated OR template

**Emergency Department Flow Management:**
- Real-time requirements (24/7 continuous updates)
- Beyond calendar scope (needs workflow management)
- Different product category

**Recurring Events:**
- Complex recurrence rules (daily, weekly, monthly, custom patterns)
- Adds significant implementation complexity
- Post-MVP feature

---

## 6. FUNCTIONAL REQUIREMENTS

### 6.1 Wizard Entry & Launch

**REQ-WIZ-001:** Wizard Auto-Launch
**Priority:** MUST HAVE
**Description:** When user drags Calendar widget from component library to canvas, wizard automatically opens as a modal or side panel.
**Acceptance Criteria:**
- Wizard appears within 500ms of widget placement
- Wizard is prominent (modal overlay or full-width side panel)
- User can dismiss wizard with clear "Skip wizard - Configure manually" link
- Wizard state is saved if user navigates away

**REQ-WIZ-002:** Return to Wizard
**Priority:** MUST HAVE
**Description:** If user exits wizard without completing, provide "Continue setup" option to resume.
**Acceptance Criteria:**
- Wizard state persists in browser session
- "Continue setup" appears as badge on Calendar widget
- Resuming wizard returns to last completed step
- Draft configurations are saved in user's workspace

---

### 6.2 Step 1: Use Case Selection

**REQ-STEP1-001:** Use Case Templates
**Priority:** MUST HAVE
**Description:** Present 5 pre-defined use case templates with clear descriptions and icons.
**Templates:**
1. Patient Appointments (📅)
2. Resource & Equipment Booking (🏥)
3. Staff Scheduling (👥)
4. Events & Meetings (📋)
5. Other / Custom (⚙️)

**Acceptance Criteria:**
- Each template has icon, title, and 1-sentence description
- Templates are visually distinct (card-based UI)
- Selection highlights the chosen template
- Cannot proceed without selecting one template
- Template drives smart defaults in subsequent steps

**REQ-STEP1-002:** Template Default Configuration
**Priority:** MUST HAVE
**Description:** Each template pre-loads specific smart defaults for Steps 2-4.
**Mapping:**
- Patient Appointments → 30min slots, Mon-Fri 8-6, cross-timezone default YES
- Resource Booking → 60min slots, 24/7, cross-timezone default NO
- Staff Scheduling → 480min (8hr) slots, 24/7, cross-timezone default NO
- Events → 60min slots, Mon-Fri 9-5, month view
- Custom → Minimal defaults, user configures all

---

### 6.3 Step 2: Timezone & Locale Setup (CRITICAL PRIORITY)

**REQ-STEP2-001:** Auto-Detect User Timezone
**Priority:** MUST HAVE
**Description:** Automatically detect user's timezone using browser Intl API and display for confirmation.
**Acceptance Criteria:**
- Uses `Intl.DateTimeFormat().resolvedOptions().timeZone`
- Displays timezone as: "Europe/Warsaw (GMT+1)"
- User can change timezone via dropdown (searchable, all IANA zones)
- Detection happens immediately on step load (<100ms)

**REQ-STEP2-002:** Cross-Timezone Detection
**Priority:** MUST HAVE
**Description:** Ask user if calendar will be used across multiple timezones.
**Question:** "Will users book appointments from other timezones? (e.g., telehealth, multi-location)"
**Options:**
- No - All users are in the same timezone
- Yes - Users may be in different timezones

**Acceptance Criteria:**
- Radio button selection (only one choice)
- Smart default based on Step 1 template:
  - Patient Appointments: Default YES (telehealth assumption)
  - Resource/Staff: Default NO (same-location assumption)
- Selection triggers conditional Step 2B (region selection)

**REQ-STEP2-003:** Region Selection (Cross-Timezone)
**Priority:** MUST HAVE
**Description:** If "Yes" to cross-timezone, show multi-select region checkboxes.
**Regions:**
- Europe
- North America
- Asia
- Australia/Oceania ⚠️
- South America
- Africa
- Middle East

**Acceptance Criteria:**
- Multi-select checkboxes
- At least one region must be selected if cross-timezone = Yes
- Australia selection triggers REQ-STEP2-004

**REQ-STEP2-004:** Australia DST Warning ⭐ CRITICAL
**Priority:** MUST HAVE
**Description:** If Australia/Oceania is selected, display proactive DST complexity warning.
**Warning Content:**
```
⚠️ AUSTRALIA DETECTED

Important: Australia has complex DST rules:
• NSW, VIC, SA, TAS: DST observed
• QLD, WA, NT: NO DST
• This creates 5 different time zones during Australian summer

We'll automatically handle this, but please verify appointment times
are displayed correctly in your preview (Step 5).

[Learn more about DST handling →]
```

**Acceptance Criteria:**
- Warning appears prominently (yellow/orange alert box)
- Warning includes icon (⚠️) and text (not color-only)
- "Learn more" link opens help documentation
- Warning is dismissible but user must acknowledge
- Warning reminder appears again in Step 5 (Preview)

**REQ-STEP2-005:** UTC Storage Configuration
**Priority:** MUST HAVE
**Description:** All datetimes are stored in UTC in backend, displayed in local timezone in frontend.
**Acceptance Criteria:**
- Configuration is automatic (user doesn't need to understand UTC)
- Info tooltip explains: "We store all times in UTC (standard reference) and display them in each user's local timezone"
- Backend data model uses UTC timestamps (ISO 8601 format)
- Frontend uses Luxon or date-fns-tz for timezone conversion

**REQ-STEP2-006:** Date & Time Format Selection
**Priority:** SHOULD HAVE
**Description:** Allow user to choose date and time display formats.
**Options:**
- Date: DD/MM/YYYY (European), MM/DD/YYYY (US), YYYY-MM-DD (ISO)
- Time: 24-hour (14:30), 12-hour (2:30 PM)

**Acceptance Criteria:**
- Radio button selection
- Smart default based on detected timezone (Europe → 24hr, US → 12hr)
- Format persists across all calendar displays

---

### 6.4 Step 3: Date/Time Configuration

**REQ-STEP3-001:** Slot Duration Selection
**Priority:** MUST HAVE
**Description:** Define appointment/booking slot duration.
**Options:** 15 min, 30 min, 60 min, Custom (input field)
**Acceptance Criteria:**
- Radio buttons + custom input field
- Smart default loaded from Step 1 template
- Custom input validates: must be >0, must be integer
- Value is used to calculate available slots in calendar

**REQ-STEP3-002:** Availability Days Selection
**Priority:** MUST HAVE
**Description:** Select which days of week calendar is available.
**Options:** Mon, Tue, Wed, Thu, Fri, Sat, Sun (multi-select checkboxes)
**Acceptance Criteria:**
- At least one day must be selected (validation)
- Smart default from template (e.g., Mon-Fri for appointments)
- Visual preview shows selected days

**REQ-STEP3-003:** Availability Hours Selection
**Priority:** MUST HAVE
**Description:** Define daily hours when calendar is available.
**Fields:** From (dropdown), To (dropdown)
**Options:** 30-minute increments from 00:00 to 23:30
**Acceptance Criteria:**
- "From" time must be before "To" time (validation)
- If "To" < "From" (crosses midnight), show warning: "Availability spans midnight. Confirm this is correct."
- Smart default from template (e.g., 08:00-18:00 for appointments)
- Displays in user-selected time format (12hr/24hr from Step 2)

**REQ-STEP3-004:** Booking Window Selection
**Priority:** MUST HAVE
**Description:** How far in advance can users book?
**Options:** 30 days, 90 days, 6 months, 1 year, No limit
**Acceptance Criteria:**
- Radio button selection
- Smart default from template (90 days for appointments)
- "No limit" shows confirmation: "Users can book indefinitely. Confirm?"

**REQ-STEP3-005:** Buffer Time Selection
**Priority:** SHOULD HAVE
**Description:** Time between appointments for cleanup/preparation.
**Options:** None, 5 min, 10 min, 15 min
**Acceptance Criteria:**
- Radio button selection
- Smart default from template (10 min for appointments)
- Info tooltip: "Buffer time prevents back-to-back appointments and allows for cleanup/prep"
- Buffer time is added to slot duration in availability calculation

---

### 6.5 Step 4: Display Preferences

**REQ-STEP4-001:** Default Calendar View Selection
**Priority:** MUST HAVE
**Description:** Choose default view when calendar loads.
**Options:** Month view, Week view, Day view
**Acceptance Criteria:**
- Radio buttons with visual preview thumbnail
- Smart default from template (Week for appointments, Month for events)
- User can switch views in deployed calendar (view picker)

**REQ-STEP4-002:** Display Fields Selection
**Priority:** MUST HAVE
**Description:** Choose which information is displayed on calendar events.
**Fields (template-specific):**
- Patient Appointments: Time, Patient name, Appointment type, Location, Status
- Resource Booking: Time, Resource name, Purpose, Responsible person
- Staff Scheduling: Time, Staff member, Shift type, Location
- Events: Time, Event name, Organizer, Attendees

**Acceptance Criteria:**
- Multi-select checkboxes
- At least "Time" must be selected (validation)
- Fields are pre-selected based on template
- Changes reflect in preview (Step 5)

**REQ-STEP4-003:** User Permissions Configuration
**Priority:** SHOULD HAVE
**Description:** Define what end-users can do with calendar.
**Permissions:** Create, Edit, Delete, View details
**Acceptance Criteria:**
- Multi-select checkboxes
- Default: All enabled
- At least "View details" must be enabled (validation)
- Permissions are enforced in deployed calendar

**REQ-STEP4-004:** Advanced Settings Escape Hatch
**Priority:** MUST HAVE
**Description:** Link to manual configuration for advanced users.
**Acceptance Criteria:**
- Link: "Need more control? Configure advanced settings manually"
- Opens property panel in side-by-side mode
- Wizard progress is preserved
- User can return to wizard
- Manual changes override wizard defaults

---

### 6.6 Step 5: Preview & Test (CRITICAL PRIORITY)

**REQ-STEP5-001:** Interactive Calendar Preview
**Priority:** MUST HAVE
**Description:** Display fully functional calendar preview with sample data.
**Acceptance Criteria:**
- Preview shows calendar in configured view (month/week/day)
- Sample appointments are pre-populated (3-5 appointments)
- User can interact: click slots, view event details
- Timezone is displayed explicitly: "Europe/Warsaw (GMT+1)"
- Preview loads within 1 second

**REQ-STEP5-002:** Test Booking Functionality
**Priority:** MUST HAVE
**Description:** Allow user to test booking an appointment in preview.
**Acceptance Criteria:**
- Button: "Book Sample Appointment"
- Opens booking modal with form (name, time slot selection)
- Appointment appears in calendar preview immediately
- Confirms configuration works correctly
- Test data is NOT saved (preview only)
- >60% of users should use this feature (success metric)

**REQ-STEP5-003:** Validation Checklist
**Priority:** MUST HAVE
**Description:** Automated validation of configuration before deployment.
**Checks:**
- ✅ Timezone configured correctly
- ✅ Availability matches settings (days + hours)
- ✅ Slot duration configured
- ✅ No conflicting settings detected
- ⚠️ Warnings (non-blocking): No availability, cross-timezone reminder, etc.

**Acceptance Criteria:**
- Checklist displays in Step 5 sidebar
- Green checkmarks (✅) for passing checks
- Yellow warnings (⚠️) for non-blocking issues
- Red errors (❌) block deployment (must be fixed)
- All checks run automatically on step load

**REQ-STEP5-004:** Context-Sensitive Reminders
**Priority:** MUST HAVE
**Description:** Show relevant reminders based on configuration.
**Scenarios:**

**Cross-Timezone Enabled:**
```
⚠️ Reminders:
• Users in different timezones will see times in THEIR local timezone
• Example: 2:00 PM in New York = 8:00 PM in Warsaw
• DST transitions handled automatically
```

**Australia Selected:**
```
⚠️ Australia DST Reminder:
• Australia has complex DST rules (5 timezones during summer)
• Verify times are correct for your specific state
• QLD/WA/NT do NOT observe DST
```

**Acceptance Criteria:**
- Reminders are contextual (only show relevant ones)
- Reminders use ⚠️ icon + text (accessible)
- Reminders are dismissible but reappear if user returns to step

**REQ-STEP5-005:** Deployment Actions
**Priority:** MUST HAVE
**Description:** Provide clear actions to finalize or modify configuration.
**Actions:**
1. **CANCEL** - Discard wizard, return to manual config
2. **SAVE AS DRAFT** - Save progress, finish later
3. **← Go Back to Edit** - Return to previous steps
4. **DEPLOY →** - Apply configuration and close wizard

**Acceptance Criteria:**
- CANCEL shows confirmation: "Are you sure? Progress will be lost."
- SAVE AS DRAFT persists state in session storage
- Go Back preserves all Step 5 state
- DEPLOY validates one final time, then applies configuration
- Success message: "✅ Calendar configured successfully!"

---

### 6.7 Global Wizard Features

**REQ-GLOBAL-001:** Progress Indicator
**Priority:** MUST HAVE
**Description:** Show current step and overall progress.
**Display:** "Step 2 of 5: Timezone & Locale Setup"
**Acceptance Criteria:**
- Visible at top of wizard
- Updates on step navigation
- Shows step title + number
- Optional: Progress bar (20%, 40%, 60%, 80%, 100%)

**REQ-GLOBAL-002:** Back Navigation
**Priority:** MUST HAVE
**Description:** Allow user to return to previous steps.
**Acceptance Criteria:**
- [← BACK] button on all steps except Step 1
- Preserves all user selections
- No data loss on back navigation
- Back navigation rate <30% (success metric - indicates good UX)

**REQ-GLOBAL-003:** Keyboard Navigation
**Priority:** MUST HAVE (WCAG 2.1 AA)
**Description:** Full keyboard accessibility.
**Acceptance Criteria:**
- Tab order: logical (top-to-bottom, left-to-right)
- Enter/Space: Select options, trigger buttons
- Arrow keys: Navigate radio buttons
- Esc: Cancel/close wizard (with confirmation)

**REQ-GLOBAL-004:** Screen Reader Support
**Priority:** MUST HAVE (WCAG 2.1 AA)
**Description:** Full screen reader compatibility.
**Acceptance Criteria:**
- All form fields have labels (aria-label)
- Step changes are announced: "Step 2 of 5: Timezone Setup"
- Validation errors are announced immediately
- Icons have text alternatives

**REQ-GLOBAL-005:** Mobile Responsiveness
**Priority:** SHOULD HAVE
**Description:** Wizard adapts to mobile/tablet screens.
**Acceptance Criteria:**
- Options stack vertically on <768px screens
- Touch targets minimum 44×44px
- Preview calendar adapts to screen size
- All features functional on mobile

---

## 7. NON-FUNCTIONAL REQUIREMENTS

### 7.1 Performance

**NFR-PERF-001:** Wizard Load Time
**Requirement:** <500ms from widget drag to wizard display
**Rationale:** User expects immediate response to action
**Measurement:** 95th percentile load time

**NFR-PERF-002:** Preview Render Time
**Requirement:** <1 second to render Step 5 preview calendar
**Rationale:** Prevents user frustration during final step
**Measurement:** Average render time

**NFR-PERF-003:** Step Transition Time
**Requirement:** <200ms between step navigation
**Rationale:** Smooth, responsive experience
**Measurement:** 95th percentile transition time

**NFR-PERF-004:** Configuration Save Time
**Requirement:** <2 seconds from "Deploy" click to success message
**Rationale:** Immediate confirmation of successful setup
**Measurement:** Average save time

### 7.2 Accessibility (WCAG 2.1 Level AA)

**NFR-ACC-001:** Keyboard Navigation
**Requirement:** All wizard functions accessible via keyboard only
**Compliance:** WCAG 2.1.1 (Keyboard)

**NFR-ACC-002:** Screen Reader Support
**Requirement:** All content and functionality announced correctly by screen readers
**Testing:** NVDA, JAWS, VoiceOver compatibility
**Compliance:** WCAG 4.1.2 (Name, Role, Value)

**NFR-ACC-003:** Color Contrast
**Requirement:** Minimum 4.5:1 contrast ratio for text, 3:1 for UI components
**Compliance:** WCAG 1.4.3 (Contrast - Minimum)

**NFR-ACC-004:** Text Alternatives
**Requirement:** All non-text content has text alternative (icons, images)
**Compliance:** WCAG 1.1.1 (Non-text Content)

**NFR-ACC-005:** Focus Indicators
**Requirement:** Clear, visible focus indicators (2px outline minimum)
**Compliance:** WCAG 2.4.7 (Focus Visible)

### 7.3 Timezone Accuracy

**NFR-TZ-001:** UTC Storage Standard
**Requirement:** All datetimes stored in UTC (ISO 8601 format) in backend
**Rationale:** Industry best practice, prevents timezone errors
**Validation:** Backend data model audit

**NFR-TZ-002:** Local Display Conversion
**Requirement:** All datetimes displayed in user's local timezone in frontend
**Library:** Luxon or date-fns-tz (IANA timezone database)
**Validation:** Timezone conversion unit tests

**NFR-TZ-003:** DST Transition Handling
**Requirement:** Calendar correctly handles DST transitions (spring forward, fall back)
**Edge Cases:**
- Missing hour (spring forward: 2:00 AM → 3:00 AM)
- Duplicate hour (fall back: 2:00 AM occurs twice)
- No DST zones (Arizona, Queensland, etc.)

**Validation:** Automated tests for DST edge cases

**NFR-TZ-004:** Australia DST Complexity
**Requirement:** Correctly handle 5 Australian timezone zones during summer
**Zones:**
- AEDT (NSW, VIC, TAS, ACT): UTC+11
- ACDT (SA): UTC+10.5
- AEST (QLD): UTC+10 (no DST)
- ACST (NT): UTC+9.5 (no DST)
- AWST (WA): UTC+8 (no DST)

**Validation:** Manual testing with Australian timezone settings

**NFR-TZ-005:** Cross-Timezone Booking
**Requirement:** When user in Timezone A books appointment in Timezone B, both see correct local time
**Example:** User in New York (EST) books appointment at 2:00 PM → Provider in Warsaw sees 8:00 PM
**Validation:** Cross-timezone integration tests

### 7.4 Reliability & Error Handling

**NFR-REL-001:** Wizard State Persistence
**Requirement:** Wizard state persists if user navigates away or browser refreshes
**Storage:** Session storage (client-side)
**Duration:** Current browser session

**NFR-REL-002:** Configuration Validation
**Requirement:** All configurations validated before deployment (Step 5)
**Validation Types:**
- Required fields present
- Data types correct (numbers, dates)
- Logical consistency (From < To, etc.)
- No conflicting settings

**NFR-REL-003:** Error Recovery
**Requirement:** Graceful error handling with user-friendly messages
**Examples:**
- Network error: "Could not save configuration. Check your connection and try again."
- Validation error: "Availability hours: 'From' time must be before 'To' time."
- No generic error messages ("Error 500")

**NFR-REL-004:** Backwards Compatibility
**Requirement:** Wizard does not break existing manually-configured calendars
**Validation:** Regression tests on existing calendar configurations

### 7.5 Security & Compliance

**NFR-SEC-001:** HIPAA Compliance
**Requirement:** Calendar configuration and data storage comply with HIPAA
**Validation:** HealthForge platform already HIPAA-compliant (inherited)

**NFR-SEC-002:** Data Privacy
**Requirement:** No PII/PHI in wizard configuration (only metadata)
**Validation:** Data model audit

**NFR-SEC-003:** Input Sanitization
**Requirement:** All user inputs sanitized to prevent XSS/injection attacks
**Validation:** Security testing (OWASP Top 10)

### 7.6 Browser & Platform Support

**NFR-PLAT-001:** Browser Compatibility
**Supported Browsers:**
- Chrome 100+ (last 2 versions)
- Firefox 100+ (last 2 versions)
- Safari 15+ (last 2 versions)
- Edge 100+ (last 2 versions)

**Not Supported:**
- Internet Explorer (EOL)

**NFR-PLAT-002:** Device Support
**Devices:**
- Desktop: Windows, macOS, Linux
- Tablet: iPad, Android tablets (>768px)
- Mobile: iPhone, Android phones (>375px width) - SHOULD HAVE

**NFR-PLAT-003:** Timezone Database Updates
**Requirement:** Timezone data (IANA database) kept up-to-date
**Update Frequency:** Quarterly (or when IANA releases updates)
**Library:** Luxon/date-fns-tz auto-updates with npm

---

## 8. TECHNICAL SPECIFICATIONS

### 8.1 Architecture Overview

**Component Structure:**
```
CalendarWizard (React Component)
├── WizardShell (Progress, Navigation)
├── Step1_UseCase (Template Selection)
├── Step2_Timezone (Timezone Setup)
│   ├── TimezoneDetector (Intl API)
│   ├── RegionSelector (Cross-timezone)
│   └── AustraliaDSTWarning (Conditional)
├── Step3_DateTime (Slot, Availability, Booking Window)
├── Step4_Display (View, Fields, Permissions)
├── Step5_Preview (Preview, Validation, Deploy)
│   ├── CalendarPreview (Interactive)
│   ├── ValidationChecklist
│   └── DeploymentActions
└── WizardContext (State Management)
```

### 8.2 Data Model

**Wizard Configuration Object:**
```typescript
interface CalendarWizardConfig {
  // Step 1
  useCase: 'appointments' | 'resources' | 'shifts' | 'events' | 'custom';

  // Step 2
  timezone: {
    primary: string; // IANA timezone (e.g., "Europe/Warsaw")
    crossTimezone: boolean;
    regions?: string[]; // If crossTimezone = true
    dateFormat: 'DD/MM/YYYY' | 'MM/DD/YYYY' | 'YYYY-MM-DD';
    timeFormat: '24h' | '12h';
  };

  // Step 3
  dateTime: {
    slotDuration: number; // Minutes
    availableDays: string[]; // ['mon', 'tue', 'wed', ...]
    availableHours: {
      from: string; // "08:00"
      to: string;   // "18:00"
    };
    bookingWindow: number | null; // Days ahead, null = no limit
    bufferTime: number; // Minutes
  };

  // Step 4
  display: {
    defaultView: 'month' | 'week' | 'day';
    visibleFields: string[]; // ['time', 'name', 'type', ...]
    permissions: {
      create: boolean;
      edit: boolean;
      delete: boolean;
      view: boolean;
    };
  };

  // Metadata
  wizardVersion: string; // "1.0"
  createdAt: string; // ISO 8601 timestamp
  completed: boolean;
}
```

**Backend Storage:**
```sql
-- Calendar widget configuration table
CREATE TABLE calendar_widgets (
  id UUID PRIMARY KEY,
  user_id UUID NOT NULL,
  app_id UUID NOT NULL,
  wizard_config JSONB, -- CalendarWizardConfig
  manual_overrides JSONB, -- Advanced settings
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);

-- All datetimes stored in UTC
CREATE TABLE calendar_events (
  id UUID PRIMARY KEY,
  calendar_id UUID REFERENCES calendar_widgets(id),
  start_time TIMESTAMPTZ NOT NULL, -- UTC
  end_time TIMESTAMPTZ NOT NULL,   -- UTC
  timezone VARCHAR(50), -- User's timezone for reference
  -- ... other fields
);
```

### 8.3 Timezone Handling Implementation

**Library:** Luxon (primary recommendation)

**Key Functions:**
```typescript
import { DateTime } from 'luxon';

// Auto-detect user timezone
function detectUserTimezone(): string {
  return Intl.DateTimeFormat().resolvedOptions().timeZone;
  // Returns: "Europe/Warsaw", "America/New_York", etc.
}

// Convert UTC to local timezone for display
function utcToLocal(utcTimestamp: string, userTimezone: string): DateTime {
  return DateTime.fromISO(utcTimestamp, { zone: 'utc' })
    .setZone(userTimezone);
}

// Convert local time to UTC for storage
function localToUtc(localTime: string, userTimezone: string): DateTime {
  return DateTime.fromISO(localTime, { zone: userTimezone })
    .toUTC();
}

// Check if timezone observes DST
function hasDST(timezone: string): boolean {
  const jan = DateTime.now().set({ month: 1, day: 1 }).setZone(timezone);
  const jul = DateTime.now().set({ month: 7, day: 1 }).setZone(timezone);
  return jan.offset !== jul.offset;
}

// Detect Australia timezone
function isAustraliaTimezone(timezone: string): boolean {
  return timezone.startsWith('Australia/');
}
```

**DST Edge Case Handling:**
```typescript
// Handle missing hour (spring forward: 2:00 AM → 3:00 AM)
function handleSpringForward(dateTime: DateTime): DateTime {
  if (!dateTime.isValid && dateTime.invalidReason === 'unit out of range') {
    // Shift to next valid hour
    return dateTime.plus({ hours: 1 });
  }
  return dateTime;
}

// Handle duplicate hour (fall back: 2:00 AM occurs twice)
function handleFallBack(dateTime: DateTime, isDST: boolean): DateTime {
  // Store both occurrences with explicit DST flag
  return dateTime.set({ isDST });
}
```

### 8.4 API Endpoints

**POST /api/calendar-wizard/save-draft**
- Save wizard state (draft configuration)
- Request: `CalendarWizardConfig` (partial)
- Response: `{ draftId: string }`

**POST /api/calendar-wizard/deploy**
- Deploy calendar configuration
- Request: `CalendarWizardConfig` (complete)
- Validation: Server-side validation of all fields
- Response: `{ calendarId: string, success: boolean }`

**GET /api/calendar-wizard/templates**
- Fetch available use case templates
- Response: `Template[]` with default configurations

**GET /api/timezones**
- Fetch IANA timezone list (searchable)
- Response: `{ timezones: string[] }`

**POST /api/calendar-wizard/validate**
- Validate configuration before deployment (Step 5)
- Request: `CalendarWizardConfig`
- Response: `{ valid: boolean, errors: string[], warnings: string[] }`

### 8.5 Testing Strategy

**Unit Tests:**
- Timezone detection logic
- UTC ↔ Local conversion functions
- DST transition handling
- Validation rules (Step 5 checklist)
- Template default configurations

**Integration Tests:**
- Wizard flow (Step 1 → Step 5 → Deploy)
- Cross-timezone booking scenarios
- Australia DST edge cases
- State persistence (save draft, resume)

**E2E Tests (Playwright/Cypress):**
- Complete wizard flow (happy path)
- Back navigation preserves state
- Validation errors block deployment
- Preview calendar displays correctly
- Timezone accuracy verification

**Accessibility Tests:**
- Keyboard navigation (Tab order)
- Screen reader compatibility (NVDA, JAWS)
- Color contrast validation (axe-core)
- Focus indicators visible

**Performance Tests:**
- Wizard load time <500ms (Lighthouse)
- Step transition <200ms
- Preview render <1s

**Timezone Accuracy Tests:**
```typescript
describe('Timezone Accuracy', () => {
  test('DST spring forward: 2:00 AM → 3:00 AM', () => {
    // Test missing hour handling
  });

  test('DST fall back: 2:00 AM occurs twice', () => {
    // Test duplicate hour handling
  });

  test('Australia: 5 timezones during summer', () => {
    // Test NSW (DST) vs QLD (no DST)
  });

  test('Cross-timezone booking: NYC → Warsaw', () => {
    // User in NYC books 2:00 PM → Provider in Warsaw sees 8:00 PM
  });
});
```

---

## 9. MVP SCOPE (IN/OUT)

### 9.1 IN SCOPE (MVP - Must Ship)

**Wizard Core:**
- ✅ 5-step wizard flow (Use Case, Timezone, DateTime, Display, Preview)
- ✅ Progress indicator (Step X of 5)
- ✅ Back navigation with state preservation
- ✅ Skip wizard option (advanced users)
- ✅ Save draft functionality

**Use Case Templates (3 required):**
- ✅ Patient Appointments
- ✅ Resource & Equipment Booking
- ✅ Staff Scheduling
- ❌ Events & Meetings (nice-to-have, can be v1.1)
- ❌ Custom (minimal defaults, low priority)

**Timezone Handling (CRITICAL):**
- ✅ Auto-detect user timezone (Intl API)
- ✅ Cross-timezone detection (Yes/No)
- ✅ Region selection (if cross-timezone)
- ✅ Australia DST warning (proactive)
- ✅ UTC storage + local display configuration
- ✅ Date/time format selection

**Date/Time Configuration:**
- ✅ Slot duration selection
- ✅ Availability days (multi-select)
- ✅ Availability hours (from/to)
- ✅ Booking window selection
- ✅ Buffer time selection

**Display Preferences:**
- ✅ Default view selection (month/week/day)
- ✅ Display fields selection (template-specific)
- ✅ User permissions (create/edit/delete/view)
- ✅ Advanced settings escape hatch

**Preview & Validation:**
- ✅ Interactive calendar preview
- ✅ Test booking functionality
- ✅ Validation checklist (automated)
- ✅ Context-sensitive reminders (Australia, cross-timezone)
- ✅ Deploy action

**Non-Functional:**
- ✅ WCAG 2.1 AA accessibility
- ✅ Wizard load <500ms
- ✅ Mobile responsive (SHOULD HAVE - may punt to v1.1 if timeline tight)
- ✅ Keyboard navigation
- ✅ Screen reader support

### 9.2 OUT OF SCOPE (Post-MVP)

**Templates:**
- ❌ Operating Room scheduling (very high complexity)
- ❌ Emergency Department flow (real-time, different product)
- ❌ Community-contributed template marketplace

**Advanced Features:**
- ❌ Recurring events (complex recurrence rules)
- ❌ External calendar sync (Google Calendar, Outlook)
- ❌ Advanced styling customization in wizard
- ❌ AI-powered configuration suggestions
- ❌ Multi-language wizard (English only for MVP)

**Integrations:**
- ❌ Email/SMS notification setup (separate feature)
- ❌ Payment processing integration
- ❌ Video conferencing integration (Zoom, Teams)

**Analytics (in wizard):**
- ❌ Usage analytics dashboard in wizard
- ❌ Calendar performance metrics display
- (Platform analytics will track wizard usage, but not exposed in wizard UI)

**Advanced Timezone:**
- ❌ Custom timezone overrides per event
- ❌ Historical timezone data (pre-2020)
- ❌ Timezone change notifications for users

### 9.3 Rationale for MVP Scope

**Why 3 templates (not 5)?**
- RICE prioritization shows Patient Appointments, Resource Booking, Staff Scheduling are highest value
- Events & Meetings has overlap with custom configuration
- Reduces initial development effort by ~20%
- Can add templates post-MVP based on usage data

**Why Australia warning (not all DST complexities)?**
- Australia is most problematic (5 zones during DST)
- Healthcare context = likely Australian users (telehealth)
- Proactive warning prevents majority of errors
- Other DST transitions handled automatically by library (Luxon)

**Why no recurring events?**
- Adds significant UI complexity (recurrence rules, exceptions)
- Less critical for appointment booking (primary use case)
- Can be added as separate feature post-MVP

---

## 10. USER JOURNEY (Step-by-Step)

### 10.1 Happy Path: Kasia Sets Up Patient Appointments

**Context:** Kasia (medical coordinator) needs online appointment booking for her clinic.

**Step 0: Entry**
- Kasia drags "Calendar" widget from Advanced section to canvas
- Wizard modal appears immediately (<500ms)
- Title: "Calendar Setup Wizard"
- Subtitle: "Let's set up your calendar in less than 5 minutes"

**Step 1: Use Case Selection (30 seconds)**
- Kasia sees 5 template options with icons and descriptions
- She selects: "📅 Patient Appointments - Schedule patient visits, consultations"
- Template loads smart defaults (30min slots, Mon-Fri 8-6, etc.)
- Clicks [NEXT →]

**Step 2: Timezone Setup (45 seconds)**
- Wizard auto-detects: "✅ We've detected your timezone: Europe/Warsaw (GMT+1)"
- Question: "Will users book from other timezones?"
- Kasia selects: "⚪ Yes - Users may be in different timezones" (telehealth)
- Region selection appears
- She checks: ☑ Europe, ☑ North America (many patients abroad)
- Info tooltip explains UTC storage (she doesn't need to understand details)
- Date format: DD/MM/YYYY (European, pre-selected)
- Time format: 24-hour (pre-selected)
- Clicks [NEXT →]

**Step 3: Date/Time Configuration (60 seconds)**
- Slot duration: "⚪ 30 minutes ✓ (Recommended)" - already selected
- Days: Mon-Fri already checked (she keeps it)
- Hours: From 08:00 to 18:00 (she changes to 09:00 - 17:00)
- Booking window: "⚪ 90 days ✓" - keeps default
- Buffer time: "⚪ 10 minutes ✓" - keeps default (cleanup between patients)
- Clicks [NEXT →]

**Step 4: Display Preferences (45 seconds)**
- Default view: "⚪ Week view ✓" - keeps default (sees weekly availability)
- Display fields: Time, Patient name, Appointment type - all checked
- Permissions: All enabled (Create, Edit, Delete, View)
- Clicks [NEXT →]

**Step 5: Preview & Test (90 seconds)**
- Interactive preview loads showing week view with sample appointments
- Timezone clearly displayed: "Europe/Warsaw (GMT+1)"
- Validation checklist:
  - ✅ Timezone configured correctly
  - ✅ Availability: Mon-Fri, 09:00-17:00
  - ✅ Slot duration: 30 minutes
  - ✅ No errors detected
- Reminder box:
  ```
  ⚠️ Cross-timezone reminder:
  • Users in different timezones will see times in their local timezone
  • Example: 2:00 PM in New York = 8:00 PM in Warsaw
  ```
- Kasia clicks [Book Sample Appointment]
  - Selects slot: Wednesday 10:00 AM
  - Fills name: "Test Patient"
  - Appointment appears in calendar ✅
- She's confident it works!
- Clicks [DEPLOY →]

**Step 6: Success**
- Success message: "✅ Calendar configured successfully!"
- Calendar widget appears on canvas, fully configured
- Kasia can now add to her patient portal app
- **Total time: ~4 minutes**

**Outcome:**
- Kasia has a working, timezone-accurate calendar without technical knowledge
- Zero timezone errors (UTC storage, local display)
- Confidence: "That was easier than I expected!"

---

### 10.2 Alternative Path: Tomek (Advanced User) Uses Escape Hatch

**Context:** Tomek (IT admin) needs operating room scheduling with complex rules.

**Step 0-1:**
- Tomek drags Calendar, wizard opens
- He selects "🏥 Resource & Equipment Booking" (closest template)

**Step 2:**
- Auto-detects timezone: Europe/Warsaw
- Cross-timezone: No (same hospital)
- Continues

**Step 3-4:**
- Starts configuring, but realizes he needs OR-specific settings (block scheduling, multi-resource constraints)
- Clicks: "Need more control? Configure advanced settings manually"
- Wizard minimizes to side panel
- Property panel opens with full manual configuration
- Tomek configures:
  - Block scheduling logic
  - Equipment allocation rules
  - Surgeon preference matching
- Wizard progress is preserved (can return if needed)

**Outcome:**
- Wizard provided good starting point (template defaults)
- Escape hatch allowed advanced customization without wizard limitations
- Best of both worlds

---

### 10.3 Error Recovery Path: User Fixes Validation Error

**Context:** User misconfigures availability hours.

**Step 3:**
- User sets: From 18:00, To 08:00 (backwards - crosses midnight)
- Clicks [NEXT →]
- Validation error appears:
  ```
  ⚠️ Availability hours: 'From' time must be before 'To' time.
  If your calendar spans midnight, confirm this is correct.
  [Confirm] [Fix]
  ```
- User clicks [Fix]
- Changes to: From 08:00, To 18:00
- Clicks [NEXT →]
- Proceeds to Step 4

**Outcome:**
- Error caught before deployment (not in production)
- Clear error message (not technical jargon)
- Easy recovery (inline fix)

---

## 11. EDGE CASES & ERROR HANDLING

### 11.1 Timezone Edge Cases

**Edge Case 1: DST Spring Forward (Missing Hour)**
- **Scenario:** User books appointment at 2:30 AM on DST transition day (2:00 → 3:00 AM)
- **Handling:**
  - Luxon detects invalid time
  - Automatically shifts to 3:30 AM (next valid hour)
  - Warning shown: "⚠️ This time falls during DST transition (2:00 AM doesn't exist). Shifted to 3:30 AM."
- **Validation:** Unit test with `DateTime.invalid` handling

**Edge Case 2: DST Fall Back (Duplicate Hour)**
- **Scenario:** User books appointment at 2:30 AM on fall back day (2:00 AM occurs twice)
- **Handling:**
  - Store UTC timestamp (unambiguous)
  - Display with DST indicator: "2:30 AM (DST)" vs "2:30 AM (Standard)"
  - User sees clarification if booking during this hour
- **Validation:** Manual test during fall DST transition

**Edge Case 3: Australia Cross-State Booking**
- **Scenario:** Patient in Queensland (no DST) books appointment with provider in New South Wales (DST)
- **Handling:**
  - Patient sees: "10:00 AM AEST (Queensland time)"
  - Provider sees: "11:00 AM AEDT (NSW time)"
  - Stored as UTC: "2026-01-15T00:00:00Z"
  - Both see correct local time
- **Validation:** Integration test with QLD/NSW timezones

**Edge Case 4: User Changes Timezone After Setup**
- **Scenario:** User configures calendar in Europe/Warsaw, later moves to America/New_York
- **Handling:**
  - Existing appointments remain in UTC (unchanged)
  - User's browser auto-detects new timezone
  - All times display in new local timezone automatically
  - No reconfiguration needed
- **Validation:** E2E test with browser timezone override

**Edge Case 5: Timezone Not Detected**
- **Scenario:** `Intl.DateTimeFormat()` fails (unlikely, but possible in old browsers)
- **Handling:**
  - Show dropdown: "Please select your timezone"
  - No default selection (force user to choose)
  - Cannot proceed without selection
- **Validation:** Mock Intl API failure

### 11.2 Configuration Edge Cases

**Edge Case 6: Availability Spans Midnight**
- **Scenario:** User sets hours: From 22:00, To 02:00 (night shift)
- **Handling:**
  - Validation warning: "⚠️ Availability spans midnight (22:00 → 02:00 next day). Confirm this is correct."
  - User must acknowledge: [Confirm]
  - Calendar correctly shows slots across midnight boundary
- **Validation:** Unit test for midnight-spanning slots

**Edge Case 7: No Days Selected**
- **Scenario:** User unchecks all days in Step 3
- **Handling:**
  - Validation error: "❌ You must select at least one day."
  - [NEXT →] button disabled until fixed
  - Cannot proceed
- **Validation:** Form validation test

**Edge Case 8: Slot Duration Exceeds Availability Window**
- **Scenario:** User sets 8-hour slots but availability is only 09:00-17:00 (8 hours)
- **Handling:**
  - Warning: "⚠️ Only 1 slot will fit in your availability window. Consider reducing slot duration or extending hours."
  - Non-blocking (user can proceed)
  - Preview shows single slot
- **Validation:** Slot calculation logic test

**Edge Case 9: Booking Window in Past**
- **Scenario:** User sets booking window = 30 days, but availability starts tomorrow
- **Handling:**
  - No special handling (booking window is forward-looking)
  - Validation: Availability must have at least one future date
- **Validation:** Date range validation test

### 11.3 User Interaction Edge Cases

**Edge Case 10: Browser Back Button**
- **Scenario:** User clicks browser back button during wizard
- **Handling:**
  - Wizard state persists in session storage
  - On return, show prompt: "Continue calendar setup?" [Yes] [No]
  - [Yes] → Resume wizard at last step
  - [No] → Discard draft
- **Validation:** Browser navigation test

**Edge Case 11: Session Timeout**
- **Scenario:** User leaves wizard open for >30 minutes, session expires
- **Handling:**
  - Draft saved in session storage (client-side, survives short timeouts)
  - On next action, check backend session
  - If expired: "Your session has expired. Please log in again to continue."
  - After re-login, resume wizard from draft
- **Validation:** Session expiration simulation

**Edge Case 12: Network Failure on Deploy**
- **Scenario:** User clicks [DEPLOY →], network request fails
- **Handling:**
  - Error message: "❌ Could not save configuration. Check your internet connection and try again."
  - [Retry] button
  - Draft preserved (no data loss)
  - Retry up to 3 times with exponential backoff
- **Validation:** Network failure simulation (mock API)

**Edge Case 13: Concurrent Edits (Rare)**
- **Scenario:** User opens same calendar in two browser tabs, edits both
- **Handling:**
  - Last save wins (optimistic locking)
  - Warning: "⚠️ This calendar was modified in another tab. Your changes will overwrite those changes."
  - User must confirm
- **Validation:** Multi-tab simulation

### 11.4 Accessibility Edge Cases

**Edge Case 14: Screen Reader Navigation**
- **Scenario:** Blind user navigates wizard with NVDA
- **Handling:**
  - Step changes announced: "Step 2 of 5: Timezone and Locale Setup"
  - All form fields labeled clearly
  - Validation errors announced immediately
  - Focus moves to error field
- **Validation:** NVDA/JAWS testing

**Edge Case 15: Keyboard-Only Navigation**
- **Scenario:** User navigates without mouse (keyboard only)
- **Handling:**
  - Tab order logical (top-to-bottom, left-to-right)
  - All interactive elements keyboard-accessible
  - Focus indicators clearly visible (2px blue outline)
  - Esc key closes wizard (with confirmation)
- **Validation:** Manual keyboard-only test

**Edge Case 16: High Contrast Mode**
- **Scenario:** User enables Windows High Contrast Mode
- **Handling:**
  - All UI elements remain visible
  - Color-only information has text/icon alternative (⚠️ + text)
  - Focus indicators adapt to high contrast
- **Validation:** Windows High Contrast Mode testing

### 11.5 Data Edge Cases

**Edge Case 17: Very Long Booking Window (1 year+)**
- **Scenario:** User selects "No limit" booking window
- **Handling:**
  - Warning: "⚠️ Unlimited booking window. Users can book appointments indefinitely. Confirm?"
  - Preview calendar shows next 90 days (not infinite)
  - Backend pagination handles large date ranges
- **Validation:** Performance test with large date ranges

**Edge Case 18: Extremely Short Slots (5 min)**
- **Scenario:** User sets custom slot duration = 5 minutes
- **Handling:**
  - Allow (valid use case: quick consultations)
  - Warning: "⚠️ Very short slots (5 min). Ensure this matches your workflow."
  - Preview shows dense schedule
- **Validation:** UI rendering test with many small slots

**Edge Case 19: Template Conflict After Manual Override**
- **Scenario:** User selects Patient Appointments template, manually changes to 8-hour slots (incompatible)
- **Handling:**
  - Allow (user override takes precedence)
  - No automatic reversal
  - Validation in Step 5 may warn if settings are unusual
- **Validation:** Template override behavior test

---

## 12. DEPENDENCIES & INTEGRATIONS

### 12.1 Internal Dependencies (HealthForge Platform)

**DEP-INT-001: Calendar Widget Component**
- **Dependency:** Existing Calendar widget in HealthForge component library
- **Integration Point:** Wizard configures widget properties
- **Risk:** Widget API changes could break wizard
- **Mitigation:** Version compatibility checks, deprecation warnings

**DEP-INT-002: Component Property Panel**
- **Dependency:** HealthForge property panel system (for "Advanced Settings" escape hatch)
- **Integration Point:** Wizard opens property panel side-by-side
- **Risk:** Property panel redesign could affect UX
- **Mitigation:** Decouple wizard from property panel UI (API-based)

**DEP-INT-003: User Authentication & Session Management**
- **Dependency:** HealthForge authentication system
- **Integration Point:** Wizard requires authenticated user session
- **Risk:** Session timeout during wizard flow
- **Mitigation:** Client-side draft saves, session extension on user activity

**DEP-INT-004: Data Storage (Backend)**
- **Dependency:** HealthForge database (PostgreSQL)
- **Integration Point:** Wizard saves configuration to `calendar_widgets` table
- **Risk:** Database schema changes
- **Mitigation:** Use ORM migrations, backward-compatible schema changes

**DEP-INT-005: Platform Analytics**
- **Dependency:** HealthForge analytics system (event tracking)
- **Integration Point:** Wizard emits events (step completions, errors, deployments)
- **Risk:** Analytics API changes
- **Mitigation:** Graceful degradation (analytics failure doesn't block wizard)

### 12.2 External Dependencies (Libraries)

**DEP-EXT-001: Luxon (Timezone Library)**
- **Library:** `luxon` v3.x
- **Purpose:** Timezone detection, UTC conversion, DST handling
- **Risk:** Library updates could change behavior
- **Mitigation:** Pin major version, comprehensive timezone tests, periodic updates
- **Alternative:** `date-fns-tz` if bundle size becomes critical

**DEP-EXT-002: React (UI Framework)**
- **Library:** `react` v18.x
- **Purpose:** Wizard UI components
- **Risk:** Breaking changes in React 19+
- **Mitigation:** Gradual migration, feature flags for new React versions

**DEP-EXT-003: IANA Timezone Database**
- **Dependency:** IANA timezone data (embedded in Luxon)
- **Purpose:** Accurate timezone rules (DST transitions, etc.)
- **Update Frequency:** Quarterly (IANA releases updates)
- **Risk:** Outdated timezone data causes errors
- **Mitigation:** Automated dependency updates (Dependabot), quarterly reviews

**DEP-EXT-004: Form Validation Library**
- **Library:** `zod` or `yup` (TBD by engineering)
- **Purpose:** Schema-based validation (Step 5 checklist)
- **Risk:** Schema validation bugs
- **Mitigation:** Comprehensive validation tests, manual QA

### 12.3 Integration Points Summary

| Integration | Type | Critical? | Failure Impact | Mitigation |
|-------------|------|-----------|----------------|------------|
| Calendar Widget API | Internal | ✅ YES | Wizard non-functional | API versioning, compatibility layer |
| Property Panel | Internal | No | Advanced users can't escape hatch | Fallback to full manual config |
| Authentication | Internal | ✅ YES | Wizard blocked | Session persistence, re-auth prompt |
| Database | Internal | ✅ YES | Cannot save config | Retry logic, error recovery |
| Analytics | Internal | No | No metrics (wizard still works) | Graceful degradation |
| Luxon | External | ✅ YES | Timezone errors | Pin version, comprehensive tests |
| IANA Timezone DB | External | ✅ YES | Incorrect timezone data | Automated updates, quarterly reviews |

---

## 13. LAUNCH PLAN

### 13.1 Development Phases

**Phase 1: Foundation**
- Set up wizard component structure
- Implement WizardShell (progress, navigation, state management)
- Build Step 1: Use Case Selection
- Integrate with HealthForge component library
- **Deliverable:** Wizard shell + Step 1 functional

**Phase 2: Timezone ⭐ CRITICAL**
- Implement Step 2: Timezone Setup
- Integrate Luxon library for timezone handling
- Build timezone auto-detection
- Implement cross-timezone flow
- Build Australia DST warning system
- Comprehensive timezone unit tests
- **Deliverable:** Step 2 functional, timezone tests passing

**Phase 3: Configuration**
- Implement Step 3: Date/Time Configuration
- Implement Step 4: Display Preferences
- Template default loading logic
- Form validation (inline errors)
- **Deliverable:** Steps 3-4 functional

**Phase 4: Preview & Validation**
- Implement Step 5: Preview & Test
- Build interactive calendar preview
- Implement test booking functionality
- Build validation checklist
- Context-sensitive reminders
- **Deliverable:** Step 5 functional, end-to-end wizard flow works

**Phase 5: Polish & Testing**
- Accessibility improvements (WCAG 2.1 AA compliance)
- Mobile responsiveness
- Error handling & edge cases
- Performance optimization (<500ms load target)
- **Deliverable:** Production-ready wizard

**Phase 6: QA & Beta**
- Internal QA testing across all scenarios
- Beta rollout to selected users (Kasia/Tomek personas)
- Bug fixes based on feedback
- Analytics instrumentation
- **Deliverable:** Beta-tested wizard

**Phase 7: Production Launch**
- Gradual rollout to HealthForge users
- Monitoring & support readiness
- Documentation (user guide, video tutorial)
- **Deliverable:** Wizard live in production

### 13.2 Rollout Strategy

**Phased Rollout Plan:**

**Stage 1: Internal Launch (0% → 5%)**
- Enable wizard for internal HealthForge team members
- Dogfooding: Internal team builds calendars using wizard
- Monitor metrics: completion rate, errors, support requests
- Fix critical bugs (hotfix if needed)

**Stage 2: Beta Launch (5% → 20%)**
- Enable for beta user group:
  - Healthcare coordinators (Kasia persona)
  - Hospital IT admins (Tomek persona)
- Send personalized onboarding emails
- Schedule feedback calls (30-min each)
- Iterate based on feedback

**Stage 3: Gradual Rollout (20% → 50%)**
- Enable for 50% of new Calendar widget users
- A/B test: Wizard vs Manual Config
- Compare metrics:
  - Time-to-working-calendar
  - Completion rate
  - Timezone error rate
- Monitor support ticket volume

**Stage 4: Full Rollout (50% → 100%)**
- Enable wizard for 100% of users
- Keep "Skip wizard" option visible (estimated 20% usage)
- Platform-wide announcement:
  - Email newsletter
  - In-app notification
  - Blog post: "Introducing Calendar Wizard"

**Stage 5: Post-Launch Optimization**
- Monitor North Star Metric: "Users with working calendar (no timezone errors) in 7 days"
- Iterate based on analytics:
  - Funnel analysis (identify drop-off points)
  - Common validation errors
  - Test booking usage rate (target >60%)
- Plan v1.1 features (additional templates, recurring events, etc.)

### 13.3 Feature Flags

**FF-001: wizard_enabled**
- **Default:** `false` (disabled)
- **Rollout:** Gradual (0% → 5% → 20% → 50% → 100%)
- **Purpose:** Master switch for wizard feature

**FF-002: wizard_skip_enabled**
- **Default:** `true`
- **Purpose:** Show "Skip wizard" link (for advanced users)
- **Can disable post-launch if skip rate is too high (>30%)

**FF-003: australia_dst_warning**
- **Default:** `true`
- **Purpose:** Show Australia DST warning in Step 2
- **Can disable if proven unnecessary (but unlikely)

**FF-004: test_booking_required**
- **Default:** `false`
- **Purpose:** Require users to test booking before Deploy (Step 5)
- **Can enable if validation errors are high in production

**FF-005: wizard_templates**
- **Default:** `['appointments', 'resources', 'shifts']` (3 templates for MVP)
- **Purpose:** Control which templates are shown
- **Can add `'events'`, `'or_scheduling'` post-MVP

### 13.4 Success Criteria for Launch

**Go/No-Go Criteria (Must Meet Before Full Rollout):**

✅ **Functional:**
- All 5 wizard steps functional (end-to-end flow works)
- Timezone accuracy tests passing (100% pass rate)
- Australia DST scenario tested manually
- Preview calendar renders correctly

✅ **Performance:**
- Wizard load time <500ms (95th percentile)
- Step transition <200ms
- Deploy action <2s

✅ **Accessibility:**
- WCAG 2.1 AA compliance verified (axe-core scan passes)
- Keyboard navigation tested (all features accessible)
- Screen reader tested (NVDA/JAWS, no critical issues)

✅ **Quality:**
- Zero P0/P1 bugs in beta testing
- <5 P2 bugs (non-critical, can fix post-launch)
- Beta user satisfaction >4/5 (NPS survey)

✅ **Operational:**
- Support documentation ready (user guide, troubleshooting)
- Internal training complete (support team knows how to help users)
- Monitoring dashboards set up (wizard metrics, error tracking)
- Rollback plan documented (how to disable wizard if critical issues)

---

## 14. SUCCESS METRICS & KPIS

### 14.1 North Star Metric

**"Number of users with a working calendar (without timezone errors) within 7 days of adding the widget"**

**Measurement:**
```sql
SELECT COUNT(DISTINCT user_id)
FROM calendar_widgets
WHERE created_at >= NOW() - INTERVAL '7 days'
  AND wizard_config->>'completed' = 'true'
  AND id NOT IN (
    SELECT calendar_id
    FROM calendar_errors
    WHERE error_type = 'timezone'
  );
```

**Target:** Increase by 60% compared to pre-wizard baseline

---

### 14.2 Primary Metrics (Track Weekly)

**1. Timezone Error Rate ⭐ TOP PRIORITY**
- **Definition:** % of calendars with timezone errors in first 7 days of use
- **Baseline:** 25-30%
- **Target:** <5%
- **Measurement:**
  ```sql
  SELECT
    COUNT(DISTINCT calendar_id) FILTER (WHERE error_type = 'timezone') * 100.0 /
    COUNT(DISTINCT calendar_id)
  FROM calendar_widgets w
  LEFT JOIN calendar_errors e ON w.id = e.calendar_id AND e.detected_at <= w.created_at + INTERVAL '7 days'
  WHERE w.created_at >= NOW() - INTERVAL '30 days';
  ```
- **Goal:** Reduce patient care errors, increase trust in platform

**2. Time-to-Working-Calendar**
- **Definition:** Median time from widget drag to successful deployment
- **Baseline:** 20-45 minutes (manual config)
- **Target:** <5 minutes
- **Measurement:**
  ```sql
  SELECT PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY
    EXTRACT(EPOCH FROM (deployed_at - started_at)) / 60
  ) AS median_minutes
  FROM wizard_sessions
  WHERE completed = true AND created_at >= NOW() - INTERVAL '7 days';
  ```
- **Goal:** Reduce entry barrier, increase adoption

**3. Wizard Completion Rate**
- **Definition:** % of users who complete wizard vs abandon
- **Baseline:** 35% (manual config completion)
- **Target:** 80%+
- **Measurement:**
  ```sql
  SELECT
    COUNT(*) FILTER (WHERE completed = true) * 100.0 / COUNT(*) AS completion_rate
  FROM wizard_sessions
  WHERE created_at >= NOW() - INTERVAL '7 days';
  ```
- **Goal:** Smooth UX, minimal friction

**4. Calendar Widget Adoption**
- **Definition:** % of active users who add Calendar widget to apps
- **Baseline:** Current adoption rate (TBD)
- **Target:** +40% increase
- **Measurement:**
  ```sql
  SELECT
    COUNT(DISTINCT user_id) FILTER (WHERE has_calendar = true) * 100.0 /
    COUNT(DISTINCT user_id) AS adoption_rate
  FROM user_apps
  WHERE created_at >= NOW() - INTERVAL '30 days';
  ```
- **Goal:** Wizard makes calendar more accessible

**5. Support Ticket Reduction**
- **Definition:** # of calendar configuration support tickets
- **Baseline:** Current ticket volume (TBD)
- **Target:** -60% reduction
- **Measurement:** Zendesk tag "calendar-config" ticket count
- **Goal:** Reduce support burden, improve user self-service

---

### 14.3 Secondary Metrics (Track Weekly)

**6. Test Booking Usage (Step 5)**
- **Definition:** % of users who click "Book Sample Appointment" in preview
- **Target:** >60%
- **Measurement:** Analytics event "wizard_test_booking_clicked"
- **Goal:** Users validate configuration before deploying

**7. Back Navigation Rate**
- **Definition:** % of users who use [← BACK] button
- **Target:** <30%
- **Measurement:** Analytics event "wizard_back_clicked" (unique users)
- **Insight:** High back rate = confusion or unclear instructions

**8. Skip Wizard Rate**
- **Definition:** % of users who click "Skip wizard"
- **Target:** <20%
- **Measurement:** Analytics event "wizard_skipped"
- **Insight:** Advanced users who prefer manual config (expected)

**9. Validation Error Rate**
- **Definition:** % of users who see validation errors in Step 5
- **Target:** <10%
- **Measurement:** Analytics event "wizard_validation_error"
- **Insight:** High error rate = poor smart defaults or confusing UX

**10. User Satisfaction (NPS)**
- **Definition:** Post-wizard survey: "How likely are you to recommend this wizard?"
- **Target:** NPS >50 (4.5/5 stars)
- **Measurement:** In-app survey after Deploy (optional, 20% sample rate)
- **Goal:** Qualitative feedback on wizard experience

---

### 14.4 Funnel Analysis (Step Completion)

**Wizard Funnel (Track drop-off at each step):**

| Step | Event | Target Completion |
|------|-------|-------------------|
| Entry | `wizard_opened` | 100% |
| Step 1 | `wizard_step1_completed` | 95% |
| Step 2 | `wizard_step2_completed` | 90% |
| Step 3 | `wizard_step3_completed` | 87% |
| Step 4 | `wizard_step4_completed` | 85% |
| Step 5 | `wizard_deployed` | 80% |

**Drop-off Analysis:**
- If Step 1 → Step 2 drop-off >5%: Use case selection unclear
- If Step 2 → Step 3 drop-off >5%: Timezone setup too complex
- If Step 5 → Deploy drop-off >5%: Validation errors or lack of confidence

---

### 14.5 Leading Indicators (Real-Time Dashboard)

**Dashboard Metrics (Update every 5 minutes):**

1. **Wizard Start Rate**
   - # of wizard sessions started (today, this week)
   - Trend: Increasing = good adoption

2. **Active Wizard Sessions**
   - # of users currently in wizard
   - Alert if >100 (capacity planning)

3. **Deployment Rate**
   - # of successful deployments (today, this week)
   - Trend: Should match wizard start rate × 80%

4. **Error Rate (Real-Time)**
   - # of validation errors, deployment failures
   - Alert if >5% of sessions

5. **Support Ticket Spike**
   - # of "calendar-config" tickets in last 24 hours
   - Alert if >10 tickets (investigate issue)

---

### 14.6 Lagging Indicators (Monthly Review)

**Monthly Business Review Metrics:**

1. **Calendar Widget Retention**
   - % of users who keep using Calendar widget after 30 days
   - Target: >70% retention

2. **Wizard ROI**
   - Time saved per user: (45 min - 5 min) × # users = total hours saved
   - Support cost reduction: (baseline tickets - current tickets) × avg ticket cost
   - Target: Positive ROI within 3 months

3. **Timezone Error Trends**
   - Month-over-month change in timezone error rate
   - Target: Continuous decrease toward <5%

4. **Feature Usage (Wizard vs Manual)**
   - % of calendars created via wizard vs manual config
   - Target: >80% wizard usage (20% manual is acceptable for advanced users)

---

### 14.7 Instrumentation Plan

**Analytics Events to Track:**

```typescript
// Step progression
track('wizard_opened', { useCase: null });
track('wizard_step1_completed', { useCase: 'appointments' });
track('wizard_step2_completed', { crossTimezone: true, regions: ['Europe', 'North America'] });
track('wizard_step3_completed', { slotDuration: 30, bufferTime: 10 });
track('wizard_step4_completed', { defaultView: 'week' });
track('wizard_deployed', { totalTime: 240 }); // seconds

// User interactions
track('wizard_back_clicked', { fromStep: 3, toStep: 2 });
track('wizard_skipped', { atStep: 1 });
track('wizard_test_booking_clicked');
track('wizard_advanced_settings_clicked');

// Errors
track('wizard_validation_error', { field: 'availableHours', error: 'from > to' });
track('wizard_deployment_failed', { reason: 'network_error' });

// Warnings
track('australia_dst_warning_shown');
track('cross_timezone_reminder_shown');
```

**Custom Metrics (Prometheus/Grafana):**
```
wizard_completion_rate{} = 0.82
wizard_median_time_seconds{} = 240
wizard_timezone_error_rate{} = 0.04
wizard_skip_rate{} = 0.18
```

---

## APPENDIX

### A. Glossary

**DST (Daylight Saving Time):** Practice of advancing clocks during warmer months so that darkness falls later. Causes timezone offset changes (spring forward, fall back).

**IANA Timezone Database:** Authoritative source for timezone rules (maintained by ICANN). Includes historical and current DST rules for all regions.

**ISO 8601:** International standard for date/time representation (e.g., `2026-02-07T14:30:00Z`).

**Luxon:** Modern JavaScript library for date/time manipulation, built on Intl API. Successor to Moment.js.

**RICE Scoring:** Prioritization framework: (Reach × Impact × Confidence) / Effort.

**UTC (Coordinated Universal Time):** Primary time standard, not subject to DST. All times stored in UTC for consistency.

**WCAG (Web Content Accessibility Guidelines):** International standards for web accessibility. Level AA is common compliance target.

---

### B. References

**Research Documents:**
- Research Report: [RESEARCH_REPORT.md](./RESEARCH_REPORT.md)
- Problem Prioritization: [PROBLEM_PRIORITIZATION.md](./PROBLEM_PRIORITIZATION.md)
- Wizard Flow Design: [WIZARD_FLOW.md](./WIZARD_FLOW.md)

**External Sources:**
- Luxon Documentation: https://moment.github.io/luxon/
- IANA Timezone Database: https://www.iana.org/time-zones
- WCAG 2.1 Guidelines: https://www.w3.org/WAI/WCAG21/quickref/
- HealthForge Platform: #

---

### C. Open Questions (For Engineering Review)

1. **Library Choice:** Luxon vs date-fns-tz? (Recommendation: Luxon for comprehensive features, but engineering should validate bundle size impact)

2. **State Management:** React Context vs Redux vs Zustand? (Recommendation: React Context for wizard-local state, Redux if platform already uses it)

3. **Backend Storage:** JSONB (PostgreSQL) vs relational tables for wizard config? (Recommendation: JSONB for flexibility, but discuss with DB team)

4. **Wizard UI:** Modal vs Side Panel vs Inline? (Recommendation: Modal for focus, but UX team should validate)

5. **Mobile Support:** MVP or v1.1? (Recommendation: SHOULD HAVE for MVP, but can punt if timeline tight)

6. **Template Extensibility:** How easy should it be to add new templates post-MVP? (Design plugin architecture?)

7. **Analytics Platform:** Segment, Mixpanel, custom? (Align with platform standard)

8. **Error Monitoring:** Sentry, Bugsnag, custom? (Align with platform standard)

---

### D. Change Log

| Date | Version | Changes | Author |
|------|---------|---------|--------|
| 2026-02-07 | 1.0 | Initial PRD draft | PM (Artur) |

---

**END OF DOCUMENT**

**Total Pages:** ~30 (printed)
**Word Count:** ~12,000 words
**Format:** Amazon 6-Pager style (comprehensive, actionable)

**Next Steps:**
1. Engineering review (technical feasibility, effort estimation)
2. Design review (UI/UX mockups for all 5 steps)
3. Stakeholder approval (Product, Healthcare Solutions Team)
4. User story breakdown (Sprint planning)
5. Development kickoff (Week 1 of launch plan)
