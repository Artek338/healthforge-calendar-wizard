# User Stories & Acceptance Criteria

**Project:** Blaze Calendar Wizard
**Date:** 2026-02-07
**Format:** Given-When-Then (Gherkin style)

---

## PRIMARY PERSONA: KASIA (Medical Coordinator)

### Epic 1: Quick Calendar Setup

#### Story 1.1: Add Calendar with Guided Setup
**As** Kasia (medical coordinator)
**I want to** add a calendar widget to my patient booking app with a guided wizard
**So that** I can set it up correctly in <5 minutes without technical knowledge

**Priority:** P0 (Critical)
**Estimate:** 8 points

**Acceptance Criteria:**

```gherkin
GIVEN I am building an app in HealthForge
WHEN I drag the Calendar widget from Advanced section to canvas
THEN wizard automatically opens in modal/side panel
AND shows "Calendar Setup Wizard - Step 1 of 5"
AND provides "Skip wizard" link for advanced users

GIVEN wizard is open
WHEN I select "Patient Appointments" use case
AND complete all 5 steps
AND click "Deploy"
THEN calendar is configured and deployed to canvas
AND setup time is <5 minutes
AND no configuration errors
```

---

#### Story 1.2: Choose Medical Use Case Template
**As** Kasia
**I want to** select from pre-built medical templates
**So that** I don't have to figure out calendar settings from scratch

**Priority:** P0
**Estimate:** 3 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 1 of wizard
WHEN I see use case options
THEN I see 5 options:
- Patient Appointments (with icon 📅 and description)
- Resource & Equipment Booking (🏥)
- Staff Scheduling (👥)
- Events & Meetings (📋)
- Other/Custom (⚙️)

GIVEN I select "Patient Appointments"
WHEN wizard proceeds to next steps
THEN smart defaults are pre-filled:
- Slot duration: 30 minutes
- Availability: Mon-Fri, 8 AM - 6 PM
- Booking window: 90 days
- Buffer time: 10 minutes

GIVEN I select different use case
WHEN wizard loads
THEN different smart defaults apply (per template spec)
```

---

### Epic 2: Timezone Configuration (Priority #1)

#### Story 2.1: Auto-Detect My Timezone
**As** Kasia
**I want** my timezone to be automatically detected
**So that** I don't have to search through timezone lists

**Priority:** P0 (Critical)
**Estimate:** 2 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 2 (Timezone Setup)
WHEN wizard loads
THEN my timezone is auto-detected via browser API
AND displayed: "✅ We've detected your timezone: Europe/Warsaw (GMT+1)"
AND I can change it via [Change timezone] link

GIVEN auto-detection fails (unlikely)
WHEN wizard cannot detect timezone
THEN I am prompted to select from dropdown
AND search/filter is enabled
```

---

#### Story 2.2: Configure Cross-Timezone Scenario
**As** Kasia
**I want to** indicate if patients will book from other timezones
**So that** appointments display correctly for everyone

**Priority:** P0 (Critical)
**Estimate:** 5 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 2
WHEN I see question "Will users book from other timezones?"
THEN I see two options:
- No - All users in same timezone (default for appointments)
- Yes - Users may be in different timezones

GIVEN I select "No"
WHEN wizard proceeds
THEN single-timezone config applied
AND times stored in UTC, displayed in my timezone

GIVEN I select "Yes"
WHEN wizard expands
THEN I see region selection:
☑ Europe, ☑ North America, ☐ Asia, ☐ Australia/Oceania, etc.
AND I can select multiple regions

GIVEN I select multiple regions
WHEN configuration applies
THEN UTC storage + local display for each user
AND timezone shown explicitly in calendar: "Europe/Warsaw (GMT+1)"
```

---

#### Story 2.3: Australia DST Warning
**As** Kasia (coordinating telehealth with Australian patients)
**I want to** be warned about Australia's complex DST rules
**So that** I'm aware of potential timezone issues and can verify carefully

**Priority:** P0 (Critical - Healthcare)
**Estimate:** 3 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 2, cross-timezone scenario
WHEN I select "Australia/Oceania" region
THEN warning banner appears:

⚠️ AUSTRALIA DETECTED

Important: Australia has complex DST rules:
• NSW, VIC, SA, TAS: DST observed
• QLD, WA, NT: NO DST
• This creates 5 different time zones during Australian summer

We'll automatically handle this, but please verify appointment
times are displayed correctly in your preview (Step 5).

[Learn more about DST handling →]

GIVEN warning is shown
WHEN I proceed to Step 5
THEN reminder appears again in preview step
AND I can test booking to verify timezone correctness
```

---

### Epic 3: Simple Configuration

#### Story 3.1: Set Appointment Slots and Availability
**As** Kasia
**I want to** configure when appointments can be booked
**So that** slots align with clinic hours

**Priority:** P0
**Estimate:** 5 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 3 (Date/Time Configuration)
WHEN wizard loads with "Patient Appointments" template
THEN smart defaults pre-filled:
- Slot duration: 30 minutes (selected)
- Days: Mon-Fri (checked)
- Hours: 08:00 - 18:00
- Booking window: 90 days
- Buffer time: 10 minutes

GIVEN I want different slot duration
WHEN I select "15 minutes" or "60 minutes" or "Custom"
THEN selection applies

GIVEN I want weekend availability
WHEN I check Sat and/or Sun
THEN availability extends to weekends

GIVEN I set invalid hours (e.g., To before From)
WHEN I proceed
THEN validation error: "End time must be after start time"
AND I cannot proceed until fixed
```

---

### Epic 4: Preview & Test

#### Story 4.1: Preview Calendar Before Deployment
**As** Kasia
**I want to** see how my calendar will look before deploying
**So that** I'm confident it's configured correctly

**Priority:** P0
**Estimate:** 5 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 5 (Preview & Test)
WHEN wizard loads
THEN I see interactive calendar preview
AND sample appointments shown
AND timezone displayed: "Europe/Warsaw (GMT+1)"

GIVEN preview is shown
WHEN I interact with calendar (click slots, view details)
THEN interactions work as expected
AND I can see how end-users will experience calendar

GIVEN validation runs automatically
WHEN preview loads
THEN validation checklist appears:
✅ Timezone configured correctly
✅ Availability matches settings
✅ Slot duration: 30 minutes
✅ No configuration errors detected
```

---

#### Story 4.2: Test Booking Scenario
**As** Kasia
**I want to** test booking an appointment in preview
**So that** I verify calendar works before going live

**Priority:** P1
**Estimate:** 3 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 5
WHEN I click "Book Sample Appointment" button
THEN booking modal opens
AND I can fill: Name, Time slot
AND appointment appears in calendar preview

GIVEN test booking succeeds
WHEN I see appointment in calendar
THEN I'm confident setup is correct
AND can proceed to Deploy

GIVEN test booking fails
WHEN error occurs
THEN clear error message shown
AND I can [← Go Back] to fix configuration
```

---

### Epic 5: Deployment

#### Story 5.1: Deploy Configured Calendar
**As** Kasia
**I want to** deploy my configured calendar with one click
**So that** it's ready for patients to use

**Priority:** P0
**Estimate:** 2 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 5
WHEN validation passes (no critical errors)
AND I click "DEPLOY" button
THEN calendar widget is configured on canvas
AND wizard closes
AND success message: "✅ Calendar configured successfully!"

GIVEN I want to save progress without deploying
WHEN I click "SAVE AS DRAFT"
THEN wizard state saved
AND I can return later: "Continue calendar setup"

GIVEN I change my mind
WHEN I click "CANCEL"
THEN confirmation dialog: "Are you sure? Progress will be lost."
AND wizard discards changes if confirmed
```

---

## SECONDARY PERSONA: TOMEK (Hospital IT Admin)

### Epic 6: Advanced Configuration

#### Story 6.1: Skip Wizard for Manual Config
**As** Tomek (technical user)
**I want to** skip wizard and configure manually
**So that** I have full control over all settings

**Priority:** P1
**Estimate:** 1 point

**Acceptance Criteria:**

```gherkin
GIVEN wizard opens after dragging Calendar widget
WHEN I click "Skip wizard - Configure manually" link
THEN wizard closes
AND property panel opens with all calendar options
AND no wizard configuration applied (blank slate)

GIVEN I am in wizard (any step)
WHEN I click "Advanced Settings" link
THEN property panel opens
AND wizard progress preserved (can return)
```

---

#### Story 6.2: Use Wizard with Override Defaults
**As** Tomek
**I want to** use wizard but customize defaults for complex scenario
**So that** I benefit from guided setup but maintain flexibility

**Priority:** P1
**Estimate:** 2 points

**Acceptance Criteria:**

```gherkin
GIVEN I select "Resource & Equipment Booking" template
WHEN wizard loads defaults
THEN I can override any setting:
- Change slot duration to custom (e.g., 90 minutes)
- Set 24/7 availability
- Configure complex timezone rules

GIVEN I navigate backwards [← BACK]
WHEN I change previous selections
THEN all subsequent defaults update accordingly
AND no data loss
```

---

## EDGE CASES & ERROR HANDLING STORIES

### Epic 7: Error Recovery

#### Story 7.1: Handle Validation Errors Gracefully
**As** Kasia
**I want to** see clear error messages if I configure something wrong
**So that** I can fix it without frustration

**Priority:** P0
**Estimate:** 3 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 3
WHEN I set end time before start time (e.g., 18:00 to 08:00)
THEN validation error: "End time must be after start time"
AND [NEXT] button disabled until fixed
AND error message styled with ⚠️ icon and red color

GIVEN I am in Step 3
WHEN I set hours that span midnight (intentionally)
THEN warning (non-blocking): "Availability spans midnight. Confirm this is correct."
AND I can proceed

GIVEN validation error shown
WHEN I fix the issue
THEN error disappears automatically
AND [NEXT] button becomes enabled
```

---

#### Story 7.2: Session Timeout / Browser Back
**As** Kasia
**I want** wizard state preserved if I accidentally close browser
**So that** I don't lose my progress

**Priority:** P2
**Estimate:** 2 points

**Acceptance Criteria:**

```gherkin
GIVEN I am in Step 3 of wizard
WHEN I accidentally close browser tab
AND reopen Calendar widget
THEN wizard offers: "Continue previous setup?" option
AND all selections preserved

GIVEN I click browser back button
WHEN in wizard
THEN wizard navigates to previous step (if applicable)
OR shows confirmation: "Exit wizard? Progress will be saved as draft."
```

---

### Epic 8: Accessibility

#### Story 8.1: Keyboard Navigation
**As** Tomek (keyboard-only user)
**I want to** navigate wizard entirely with keyboard
**So that** I don't need mouse

**Priority:** P0 (WCAG 2.1 AA requirement)
**Estimate:** 3 points

**Acceptance Criteria:**

```gherkin
GIVEN wizard is open
WHEN I press Tab
THEN focus moves to next interactive element in logical order
AND focus indicator clearly visible (high contrast outline)

GIVEN I am on radio button group
WHEN I press Arrow keys
THEN selection changes between options
AND selected option announced by screen reader

GIVEN I am on any step
WHEN I press Esc
THEN wizard shows exit confirmation
AND I can Tab to [Cancel] or [Exit] buttons

GIVEN I am selecting use case (Step 1)
WHEN I press Enter or Space on option
THEN option selected
AND wizard proceeds to Step 2
```

---

#### Story 8.2: Screen Reader Compatibility
**As** Kasia (using screen reader)
**I want** all wizard content announced clearly
**So that** I can configure calendar independently

**Priority:** P0 (WCAG 2.1 AA requirement)
**Estimate:** 3 points

**Acceptance Criteria:**

```gherkin
GIVEN wizard opens
WHEN screen reader active
THEN announces: "Calendar Setup Wizard, Step 1 of 5: Use Case Selection"

GIVEN I navigate to Step 2
WHEN timezone auto-detected
THEN announces: "Timezone detected: Europe Warsaw, GMT plus 1. Change timezone button available."

GIVEN validation error occurs
WHEN error message appears
THEN screen reader announces error immediately (aria-live region)
AND error associated with input field (aria-describedby)

GIVEN Australia DST warning shown
WHEN warning appears
THEN screen reader announces warning content
AND severity indicated (aria-label="Warning")
```

---

## PERFORMANCE & NON-FUNCTIONAL STORIES

### Epic 9: Performance

#### Story 9.1: Fast Wizard Load Time
**As** Kasia (impatient user)
**I want** wizard to open instantly
**So that** I don't wait and can work efficiently

**Priority:** P0
**Estimate:** 2 points

**Acceptance Criteria:**

```gherkin
GIVEN I drag Calendar widget to canvas
WHEN wizard triggers
THEN wizard modal opens in <500ms
AND Step 1 renders completely
AND no loading spinners visible

GIVEN I am in Step 5 (Preview)
WHEN preview calendar renders
THEN calendar appears in <1 second
AND interactive (can click slots immediately)

GIVEN wizard loads
WHEN I'm on slow network (3G)
THEN core wizard UI loads <1s
AND preview may take up to 2s (acceptable)
```

---

## SUMMARY

### Total Stories: 20
- **P0 (Critical):** 15 stories
- **P1 (Important):** 4 stories
- **P2 (Nice-to-have):** 1 story

### Total Estimate: 52 story points
- Assuming 1 point ≈ 0.5 dev days
- Total: ~26 dev days ≈ **5-6 weeks for 1 developer**
- Or: **3-4 weeks for 2 developers** (with parallelization)

### Epic Priority
1. **Epic 2 (Timezone)** - HIGHEST (P0, RICE 2400)
2. **Epic 1 (Quick Setup)** - P0 (Core wizard)
3. **Epic 4 (Preview)** - P0 (Error prevention)
4. **Epic 5 (Deployment)** - P0 (Core functionality)
5. **Epic 7 (Error Handling)** - P0 (UX quality)
6. **Epic 8 (Accessibility)** - P0 (WCAG requirement)
7. **Epic 9 (Performance)** - P0 (UX baseline)
8. **Epic 3 (Configuration)** - P0 (Core setup)
9. **Epic 6 (Advanced)** - P1 (Power users)

---

**User Stories Complete** | Ready for Sprint Planning
