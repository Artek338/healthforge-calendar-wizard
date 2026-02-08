# Research Report - HealthForge Calendar Wizard Discovery

**Project:** HealthForge Calendar Wizard
**Date:** 2026-02-07
**Phase:** Discovery
**Research Lead:** PM (Artur)

---

## EXECUTIVE SUMMARY

Conducted comprehensive market research, competitive analysis, and medical use case identification for the Calendar Wizard feature in HealthForge. Key findings:

**Market Gap Identified:** None of the major low-code platforms (Retool, Bubble.io, OutSystems) have a dedicated calendar configuration wizard - all use manual configuration through property panels. This confirms an opportunity for HealthForge.

**Primary Use Cases:** Patient appointment booking (most critical), Operating Room scheduling, Staff shifts management, Equipment booking, ED flow management.

**Critical Technical Challenge:** Timezone handling, especially Australia (5 timezone zones during DST) and healthcare cross-timezone scenarios.

**Recommended Approach:** Multi-step wizard (staged disclosure) with smart defaults, proactive timezone warnings, and pre-built medical templates.

---

## 1. COMPETITIVE ANALYSIS

### 1.1 Retool

**Calendar Implementation:**
- Uses FullCalendar.js library
- Configuration through property panel (manual)
- **NO wizard for setup**

**User Feedback:**
- Community forum shows configuration difficulties
- Event creation requires manual setup in property panel
- Users ask about: 15-minute intervals, week/day views, styling

**Strengths:**
- Comprehensive documentation
- Active community

**Weaknesses:**
- High technical barrier for non-tech users
- Trial-and-error approach to configuration
- No guided onboarding

**Sources:**
- [Retool Calendar Docs](https://docs.retool.com/apps/reference/components/calendar)
- [Retool Community Forum](https://community.retool.com/t/how-to-create-event-by-selecting-a-date-on-the-calendar/16218)

---

### 1.2 Bubble.io

**Calendar Implementation:**
- Multiple calendar plugins (Full Calendar IO, Calendar Booking & Time Slots, etc.)
- Configuration by defining fields (start time, end time field)
- **NO wizard**

**Setup Process:**
- User selects plugin from marketplace
- Defines data fields manually
- Sets display options

**Strengths:**
- Multiple plugin options (flexibility)
- Plugin marketplace ecosystem

**Weaknesses:**
- Lack of standardization (each plugin different)
- Manual field mapping required
- No guided setup for timezone handling

**Sources:**
- [Bubble Full Calendar Plugin](https://manual.bubble.io/core-resources/bubble-made-plugins/full-calendar)
- [Bubble Plugin Marketplace](https://bubble.io/plugins/calendar)

---

### 1.3 OutSystems

**Calendar Implementation:**
- Calendar Widget for Reactive/Mobile apps
- FullCalendar wrapper
- **Has generic "Wizard Widget", but NOT specifically for calendar**

**Setup Process:**
- Drag-and-drop to canvas
- Property panel configuration
- Manual integration with data model

**Strengths:**
- Enterprise-grade platform
- Comprehensive component library

**Weaknesses:**
- Wizard widget is generic (not calendar-specific)
- Technical setup required
- Steep learning curve

**Sources:**
- [OutSystems Calendar Widget](https://www.outsystems.com/forge/component-overview/21491/calendar-widget-o11)
- [OutSystems Forum](https://www.outsystems.com/forums/discussion/43307/calendar-widget/)

---

### 1.4 Competitive Summary

| Platform | Has Calendar? | Has Wizard? | Setup Complexity | Target User |
|----------|---------------|-------------|------------------|-------------|
| Retool | ✅ (FullCalendar) | ❌ | HIGH | Technical |
| Bubble.io | ✅ (Multiple plugins) | ❌ | MEDIUM-HIGH | Semi-technical |
| OutSystems | ✅ (Widget) | ❌ (Generic only) | HIGH | Enterprise/Technical |
| **HealthForge (proposed)** | ✅ | ✅ (Calendar-specific) | LOW | Non-technical |

**Key Insight:** **MARKET GAP** - no platform has a dedicated calendar configuration wizard. This is an opportunity for HealthForge to differentiate.

---

## 2. HEALTHFORGE PLATFORM ANALYSIS

### 2.1 Platform Overview

**What is HealthForge:**
- No-code platform specializing in **healthcare applications**
- HIPAA & SOC 2 compliant
- Used by Fortune 500s and healthcare startups
- Drag-and-drop interface

**Target Users:**
- Healthcare administrators (non-technical)
- Clinical coordinators
- Medical practice managers
- Hospital IT departments

**Pricing:** Starting at $1,500/month (monthly billing) or $1,350/month (annual billing)

**Key Features:**
- Patient management apps
- Telehealth platforms
- EMR/EHR systems
- Scheduling tools
- Client portals
- Inventory management
- HIPAA-compliant data security

**Sources:**
- [HealthForge Homepage](#)
- [Healthcare Solutions](#)
- [Medical App Development](#)

---

### 2.2 Healthcare Focus Advantage

**Why HealthForge is uniquely positioned:**

1. **Healthcare-first platform** - understands medical workflows
2. **Compliance built-in** - HIPAA/SOC 2 already resolved
3. **Non-technical users** - perfect fit for wizard
4. **Scheduling is core use case** - calendar is a critical widget

**Implications for wizard:**
- Can include medical-specific templates
- Compliance considerations already handled by platform
- Users expect guided experience (non-technical)
- Timezone accuracy is CRITICAL (patient care implications)

---

## 3. WIZARD UX BEST PRACTICES

### 3.1 Wizard vs Progressive Disclosure

**Research findings:**

**Wizard (Staged Disclosure):**
- ✅ Linear step-by-step flow
- ✅ Good for distinct, sequential steps
- ✅ Reduces cognitive load (shows only current step)
- ✅ Clear progress indication
- ❌ Can be frustrating if user wants to return to earlier steps

**Progressive Disclosure:**
- ✅ All steps visible in one view
- ✅ Easy navigation between sections
- ✅ User can modify earlier choices
- ❌ Can overwhelm with complexity (everything at once)

**Best Practice Examples:**
- **Shopify onboarding wizard** - top-notch example
  - Concise content
  - Progress bars
  - Imagery for engagement
  - Seamless UX

**Recommendation for HealthForge:**
- **Hybrid approach** - wizard flow with "back" navigation capability
- Step indicator (progress bar)
- Escape hatch to "Advanced settings"
- Preview step before finalization

**Sources:**
- [Progressive Disclosure (NN/g)](https://www.nngroup.com/articles/progressive-disclosure/)
- [Wizard vs Progressive Form](https://medium.com/patternfly/comparing-web-forms-a-progressive-form-vs-a-wizard-110eefc584e7)
- [Onboarding Wizard Examples](https://userguiding.com/blog/what-is-an-onboarding-wizard-with-examples)

---

### 3.2 Low-Code Platform Trends (2026)

**Market Growth:**
- 65%+ app development activity will be low-code/no-code by 2026
- Citizen developers + enterprise digitization as drivers
- Accessibility > speed of traditional development

**UX Patterns:**
- Drag-and-drop UI (standard)
- Pre-built components (design best practices built-in)
- Automatic responsive layouts
- Visual configuration > manual coding

**Wizard Characteristics in low-code:**
- Simple, concise questions
- Visual feedback (preview)
- Smart defaults based on use case
- Minimal steps (3-5 optimal)

**Sources:**
- [Low-Code 2026 Trends](https://hackernoon.com/low-code-and-no-code-in-2026-the-way-i-pick-a-platform-without-regret)
- [Low-Code UX Challenges](https://www.aubergine.co/insights/ux-design-for-products-built-on-low-code-no-code-platforms)

---

## 4. TIMEZONE HANDLING RESEARCH

### 4.1 Best Practices (Industry Standard)

**Golden Rule:**
```
Store: UTC in database/backend
Display: Local timezone in frontend
Format: ISO 8601
```

**Why UTC Storage:**
- Standard reference point
- Minimizes conversion errors
- No DST ambiguity in storage
- Easy calculation of local times

**Frontend Conversion:**
- Browser timezone detection: `Intl.DateTimeFormat().resolvedOptions().timeZone`
- Libraries handle DST automatically
- Display format: locale-aware

**API Design:**
- **Accept:** Liberal (parse any timezone in request)
- **Return:** Conservative (always UTC in response)
- Robustness principle

**Sources:**
- [UTC Best Practices](https://weblog.west-wind.com/posts/2015/feb/10/back-to-basics-utc-and-timezones-in-net-web-apps)
- [3 Rules for Dates/Timezones](https://dev.to/corykeane/3-simple-rules-for-effectively-handling-dates-and-timezones-1pe0)
- [Enterprise Timezone Handling](https://medium.com/@20011002nimeth/handling-timezones-within-enterprise-level-applications-utc-vs-local-time-309cbe438eaf)

---

### 4.2 Australia DST Challenge

**Why Australia is Problematic:**

1. **Non-uniform DST adoption:**
   - NSW, VIC, SA, TAS, ACT: **DST observed**
   - QLD, WA, NT: **NO DST**

2. **5 Timezone Zones During Summer:**
   - Normally 3 standard zones
   - Increases to 5 during Australian summer
   - Cross-state operations complex

3. **Border Complications:**
   - NSW/QLD border = 1 hour difference (half the year)
   - Impact: transport schedules, meetings, school drop-offs
   - Medical appointments: patient confusion

4. **Healthcare Implications:**
   - Telehealth appointments across states
   - Multi-campus hospitals (different states)
   - Referrals/transfers between facilities
   - Medication schedules (critical timing)

**Sources:**
- [DST in Australia](https://en.wikipedia.org/wiki/Daylight_saving_time_in_Australia)
- [Australian Time Zones 2026](https://www.geocountries.com/timezones-abbreviations/australia)
- [DST Border Challenges](https://www.sbs.com.au/news/article/when-daylight-saving-time-starts-in-australia-in-2025/67t60uuqb)

---

### 4.3 Library Recommendations (2026)

**Temporal API:**
- **Status:** Not yet standard in browsers (polyfill available)
- **Features:** Immutable, timezone-aware, fixes Date object problems
- **Recommendation:** Future-proof choice, but requires polyfill currently

**Luxon:**
- **Built on:** Internationalization API (Intl)
- **Features:** Comprehensive date/time manipulation, extensive timezone support
- **Best for:** Complex date operations, multi-timezone apps
- **Bundle size:** Larger than date-fns

**date-fns-tz:**
- **Built on:** Intl API (similar to Tempo)
- **Features:** Modular, lightweight, essential functions
- **Best for:** Basic date operations, minimal bundle size
- **Approach:** Tree-shakeable imports

**Recommendation for HealthForge:**
- **Primary:** Luxon (comprehensive, healthcare needs complex scheduling)
- **Alternative:** date-fns-tz (if bundle size critical)
- **Future:** Migrate to Temporal API when standard

**Sources:**
- [JavaScript Temporal 2026](https://bryntum.com/blog/javascript-temporal-is-it-finally-here/)
- [Luxon vs date-fns-tz Comparison](https://medium.com/@sungbinkim98/comparing-date-fns-tz-and-luxon-55aee1bab550)
- [Date Library Comparison](https://npm-compare.com/date-fns,date-fns-tz,dayjs,luxon,moment)

---

## 5. MEDICAL USE CASES ANALYSIS

### 5.1 Top 5 Healthcare Calendar Use Cases

#### 1. **Patient Appointment Booking** ⭐ HIGHEST PRIORITY

**Description:**
- Online 24/7 booking for patient visits
- Multi-specialty support (different appointment types)
- Automated reminders (SMS/email)
- Self-service reschedule/cancel
- Multi-location support

**Complexity:** MEDIUM
**Frequency:** VERY HIGH (daily, multiple times)
**Timezone Sensitivity:** HIGH (patient may be in different timezone)

**Key Requirements:**
- Slot-based availability (15min, 30min, 60min intervals)
- Provider availability integration
- Insurance verification hooks
- No-show prevention (confirmations)
- Waitlist management

**Market Data:**
- Global medical scheduling software market: $6.1M by 2026
- Rapid digitalization driver: reduce wait times, automate processes

**Sources:**
- [Healthcare Appointment Software 2026](https://healthray.com/blog/doctor-appointment-system/healthcare-appointment-software/)
- [Best Medical Scheduling Software](https://www.noterro.com/blog/best-medical-appointment-scheduling-software)

---

#### 2. **Operating Room Scheduling** ⭐ HIGH COMPLEXITY

**Description:**
- Surgical procedure scheduling
- Multi-resource coordination (surgeon, nurses, anesthesiologist, equipment)
- Block scheduling vs open scheduling
- Vendor coordination (equipment/supplies delivery)

**Complexity:** VERY HIGH
**Frequency:** HIGH (daily in hospitals)
**Timezone Sensitivity:** MEDIUM (usually same-location, but multi-campus may be cross-timezone)

**Key Requirements:**
- Equipment allocation
- Staff availability (skill-based matching)
- Procedure duration estimation
- Emergency case accommodation
- Waitlist prioritization
- Post-op bed availability

**Scheduling Approaches:**
- **Block scheduling:** Time block assigned to specific surgeon/group
- **Open scheduling:** First-come-first-served, any surgeon

**Sources:**
- [OR Scheduling Software](https://surgicalendar.com/operating-room-scheduling-software/)
- [Best OR Scheduling](https://surgistream.com/2024/08/best-or-scheduling-software/)
- [Block vs Open Scheduling](https://hospitalmedicaldirector.com/operating-room-block-scheduling-versus-open-scheduling/)

---

#### 3. **Staff Scheduling (Shifts/On-Call)** ⭐ HIGH FREQUENCY

**Description:**
- Doctor/nurse shift management
- On-call rotations
- Multi-location coverage
- Preference-based vs pattern-based scheduling

**Complexity:** HIGH
**Frequency:** VERY HIGH (daily/weekly roster updates)
**Timezone Sensitivity:** MEDIUM (multi-location facilities)

**Key Requirements:**
- Union/regulatory constraints (max hours, min rest time)
- Skill-based matching
- Preference management
- Shift swap capabilities
- Mobile access (self-service)
- PTO/vacation management

**Scheduling Types:**
- **Pattern scheduling:** Staff commits to set shift types
- **Preference scheduling:** Individual preferences defined

**Sources:**
- [Healthcare Workforce Management](https://www.qgenda.com/)
- [Medical Staff Scheduling](https://shifton.com/healthcare)
- [Nurse Scheduling Best Practices](https://www.osplabs.com/insights/everything-you-need-to-know-about-nurse-scheduling/)

---

#### 4. **Medical Equipment/Resource Booking**

**Description:**
- MRI/CT scanner scheduling
- Specialized equipment booking
- Treatment room allocation
- Wheelchair/bed assignment

**Complexity:** MEDIUM
**Frequency:** MEDIUM-HIGH
**Timezone Sensitivity:** LOW (usually same-location)

**Key Requirements:**
- Resource availability tracking
- Maintenance scheduling (downtime)
- Conflict prevention
- Usage analytics
- Automated notifications

---

#### 5. **Emergency Department Flow Management**

**Description:**
- ED patient tracking
- Treatment bay assignment
- Multi-step workflow management
- Capacity monitoring

**Complexity:** VERY HIGH
**Frequency:** CONTINUOUS (24/7)
**Timezone Sensitivity:** LOW (real-time, same-location)

**Key Requirements:**
- Real-time updates
- Priority-based routing
- Triage integration
- Wait time estimation
- Bed/bay availability

---

### 5.2 Use Case Prioritization

**For Calendar Wizard MVP, prioritization:**

| Rank | Use Case | Rationale |
|------|----------|-----------|
| 1 | Patient Appointment Booking | Highest frequency, most common, moderate complexity, strong ROI |
| 2 | Resource/Equipment Booking | Similar to appointments, medium complexity, reusable template |
| 3 | Staff Shifts Scheduling | High frequency, but higher complexity (constraints) |
| 4 | OR Scheduling | Very high complexity, could be post-MVP (advanced template) |
| 5 | ED Flow | Real-time requirements beyond calendar scope |

**Recommendation:** MVP wizard should include templates for **#1, #2, #3** (patient appointments, resource booking, staff shifts).

---

## 6. KEY INSIGHTS & RECOMMENDATIONS

### 6.1 Market Opportunity

**Validated Gap:** No major low-code platform has a calendar configuration wizard
- Retool: ❌ No wizard
- Bubble: ❌ No wizard
- OutSystems: ❌ Generic only, not calendar-specific

**HealthForge Advantage:**
- Healthcare-first platform
- Non-technical user base (perfect for wizard)
- Calendar is core use case
- Can differentiate with medical-specific templates

---

### 6.2 Critical Success Factors

1. **Timezone Handling MUST BE BULLETPROOF**
   - Australia challenge (5 zones during DST)
   - Healthcare implications (patient care)
   - Proactive warnings + validation

2. **Medical Templates are Value**
   - Generic calendar = commodity
   - Healthcare-specific = differentiation
   - Pre-configured compliance/validation rules

3. **Guided UX for Non-Technical Users**
   - Kasia (coordinator) is not tech-savvy
   - Confidence-building important ("won't break it")
   - Clear, simple language (no technical jargon)

---

### 6.3 Recommended Wizard Approach

**Multi-step Wizard (Staged Disclosure)** with:

1. **Use Case Selection** (Step 1)
   - "What will you use this calendar for?"
   - Pre-built templates (appointment, resource, shifts)

2. **Timezone & Locale Setup** (Step 2)
   - Auto-detect user timezone
   - "Will users be in different timezones?" (Yes/No)
   - Australia DST warning (if applicable)

3. **Date/Time Configuration** (Step 3)
   - Slot duration (15/30/60 min)
   - Business hours
   - Date range (how far ahead bookable)

4. **Display & Validation** (Step 4)
   - Calendar view (month/week/day)
   - Required fields
   - Validation rules

5. **Preview & Test** (Step 5)
   - Interactive preview
   - Test scenario
   - "Looks good" → Deploy

**Escape Hatch:** "Advanced settings" link in each step

---

### 6.4 Alternative Solutions to Consider

1. **Smart Defaults + Progressive Disclosure**
   - Instead of wizard, very good defaults
   - Expandable sections for advanced settings
   - Pro: Faster for power users
   - Con: May not resolve confusion for beginners

2. **AI-Assisted Configuration**
   - ChatGPT-style conversational setup
   - Natural language: "I need a calendar for patient appointments..."
   - Pro: Very intuitive
   - Con: Unpredictable, harder to control

3. **Template Marketplace**
   - Community-contributed calendar configs
   - Clone & customize approach
   - Pro: Crowd-sourced patterns
   - Con: Quality control, discoverability

**Recommendation:** Multi-step wizard (primary) + smart defaults (fallback for existing users).

---

## 7. NEXT STEPS

### 7.1 Completed Research ✅

- [x] Competitive analysis (Retool, Bubble, OutSystems)
- [x] HealthForge platform understanding
- [x] Wizard UX best practices
- [x] Timezone handling deep dive
- [x] Medical use cases identification

### 7.2 Pending Tasks

- [ ] **Problem Prioritization (RICE Scoring)** - Task #4
  - Which problems have biggest usability impact?

- [ ] **Wizard Flow Design** - Task #5
  - Detailed step-by-step flow
  - Decision tree (branching logic)

- [ ] **PRD Writing** - Task #6
  - Comprehensive Product Requirements Document

- [ ] **User Stories & Acceptance Criteria** - Task #7
  - Given-When-Then format

- [ ] **Alternative Solutions Evaluation** - Task #8
  - Deep dive into alternatives
  - Recommendation with justification

---

## 8. RESEARCH SOURCES

### Competitive Intelligence
- [Retool Calendar Component](https://docs.retool.com/apps/reference/components/calendar)
- [Bubble.io Full Calendar](https://manual.bubble.io/core-resources/bubble-made-plugins/full-calendar)
- [OutSystems Calendar Widget](https://www.outsystems.com/forge/component-overview/21491/calendar-widget-o11)

### HealthForge Platform
- [HealthForge Homepage](#)
- [Medical App Development](#)
- [Healthcare Solutions](#)

### UX Best Practices
- [Progressive Disclosure (NN/g)](https://www.nngroup.com/articles/progressive-disclosure/)
- [Wizard vs Progressive Form](https://medium.com/patternfly/comparing-web-forms-a-progressive-form-vs-a-wizard-110eefc584e7)
- [Low-Code 2026 Trends](https://hackernoon.com/low-code-and-no-code-in-2026-the-way-i-pick-a-platform-without-regret)

### Timezone Handling
- [UTC Best Practices](https://weblog.west-wind.com/posts/2015/feb/10/back-to-basics-utc-and-timezones-in-net-web-apps)
- [Enterprise Timezone Handling](https://medium.com/@20011002nimeth/handling-timezones-within-enterprise-level-applications-utc-vs-local-time-309cbe438eaf)
- [DST in Australia](https://en.wikipedia.org/wiki/Daylight_saving_time_in_Australia)

### Medical Use Cases
- [Healthcare Appointment Software 2026](https://healthray.com/blog/doctor-appointment-system/healthcare-appointment-software/)
- [OR Scheduling Software](https://surgicalendar.com/operating-room-scheduling-software/)
- [Healthcare Workforce Management](https://www.qgenda.com/)

---

**Report Complete** | Next: Problem Prioritization (RICE Framework)
