# PROJECT.md - HealthForge Calendar Wizard

## 1. EXECUTIVE SUMMARY

**What we're building:** Configuration wizard for Calendar widget in HealthForge (low-code platform for healthcare industry)

**Problem:** Calendar widget is popular but difficult to configure - has many options, users get lost in configuration, especially with timezones (DST)

**Solution:** Interactive wizard that:
- Asks about use case (appointment booking, resource scheduling, etc.)
- Automatically configures calendar with dependencies
- Proactively solves timezone problems
- Delivers ready, working calendar in <5 min

**Project Type:** HealthForge recruitment task - product specification (not implementation)

**Deadline:** End of Sunday (February 7, 2026)

**Current Stage:** Discovery

---

## 2. PROBLEM STATEMENT

### Main User Problems

1. **Option Overwhelm** - dozens of configuration fields without guidance
2. **Timezone Issues** - DST, cross-timezone users, countries without DST changes (Australia)
3. **Lack of Medical Context** - generic calendar, doesn't understand medical use cases
4. **High Entry Barrier** - even simple calendar requires 20-45 min configuration
5. **Production Errors** - timezone issues surface only with end-users (~25-30% of calendars have problems)

### Current Solutions

- **HealthForge currently:** Manual config, trial-and-error, documentation
- **Retool:** Presets, but still manual timezone setup
- **Bubble.io:** No wizard, fully manual
- **OutSystems:** Wizards, but very technical

### Our Value Proposition

A wizard that **understands medical context** and **proactively prevents timezone errors** - not just guided setup, but intelligent assistant.

---

## 3. TARGET USERS

### Primary Persona: Kasia - Medical Coordinator

- **Who she is:** 34 years old, coordinator at clinic (15 doctors, 4 locations), 5 years in medical admin
- **Tech level:** 2/5 (Office, Gmail, basic apps)
- **Job-to-be-Done:** Enable patients to book appointments online without involving reception
- **Main frustrations:**
  - Excel/Google Calendar don't integrate with facility system
  - Calendly too expensive, not adapted to Polish healthcare
  - Afraid of tech config: "what if I break something?"
  - Wastes 2-3h/week on manual calendar management

### Secondary Persona: Tomek - IT Admin at Hospital

- **Who he is:** 42 years old, IT admin at county hospital (300 beds), 12 years in healthcare IT
- **Tech level:** 4/5 (technical, but prefers low-code)
- **Job-to-be-Done:** Hospital resource booking system (operating rooms, equipment, staff)
- **Main frustrations:**
  - Low-code tools don't understand healthcare specifics
  - Integration with legacy HIS (Hospital Information System)
  - GDPR/NFZ/audit requirements

---

## 4. GOALS & SUCCESS METRICS

### Business Goals

- [ ] ↑ Calendar widget adoption +40% in 3 months
- [ ] ↓ Support tickets (calendar config) -60%
- [ ] ↑ Completion rate 35% → 80%+
- [ ] Time-to-working-calendar: 20-45 min → <5 min
- [ ] Timezone errors: ~25-30% → <5%

### North Star Metric

**"Number of users with working calendar (no timezone errors) within 7 days of adding widget"**

---

## 5. SCOPE

### IN SCOPE (MVP)

- ✅ Multi-step wizard (3-5 steps, progress indicator)
- ✅ Use case detection (appointment, resource, shifts, events)
- ✅ Smart timezone handling:
  - Auto-detect user timezone (browser + HealthForge settings)
  - Detect cross-timezone scenarios
  - UTC storage + local display pre-config
  - Warnings for problematic DST (Australia)
- ✅ Pre-built templates (3-5 medical use cases)
- ✅ Auto-configuration (date fields, validation, dependencies)
- ✅ Preview & test step
- ✅ Escape hatch (advanced manual settings)

### OUT OF SCOPE (post-MVP)

- ❌ Recurring events (complex recurrence rules)
- ❌ External calendar sync (Google Cal, Outlook)
- ❌ Advanced styling in wizard
- ❌ AI-powered suggestions
- ❌ Integration setup (email/SMS notifications)

### Non-negotiables

- 🔒 **Timezone accuracy** - must work correctly for all timezone scenarios
- 🔒 **Backwards compatibility** - don't disrupt existing manual configs
- 🔒 **Performance** - wizard load <500ms
- 🔒 **Accessibility** - WCAG 2.1 AA
- 🔒 **Error prevention** - very difficult/impossible to create broken calendar

---

## 6. CURRENT STATE & NEXT STEPS

### What We Have

- ✅ PROJECT.md - context file
- 🔄 Discovery - in progress

### Next Steps (discovery plan)

1. **Market Research** (Tavily deep search)
   - Competitive analysis (Retool, Bubble, OutSystems - how do they solve calendar setup?)
   - Best practices: wizard UX in no-code tools
   - Timezone handling standards in medical apps
   - HealthForge platform analysis

2. **User Research** (Synthetic User agent)
   - Interview with Kasia & Tomek personas
   - Validate pain points
   - Prioritize use cases

3. **Problem Prioritization** (Product Manager + RICE)
   - Which problems = biggest impact on usability?
   - What must MVP solve vs nice-to-have?

4. **Technical Deep Dive**
   - Timezone scenarios (DST edge cases, Australia, cross-timezone)
   - Testing timezone correctness
   - Libraries/tools recommendations

5. **Solution Design**
   - Wizard flow (user journey, step by step)
   - Template designs (3-5 medical use cases)
   - Alternative solutions evaluation

6. **Documentation**
   - PRD (Product Requirements Document)
   - User stories + acceptance criteria
   - Handoff for design/dev teams

---

## 7. RESEARCH QUESTIONS (To Answer in Discovery)

### Market & Competition
- How do Retool/Bubble/OutSystems solve calendar config?
- Industry best practices for wizard UX?
- Ready frameworks for "smart calendar setup"?

### Users & Use Cases
- TOP 5 medical calendar use cases?
- Healthcare specifics vs other industries?
- % of use cases requiring cross-timezone?

### Technical (Timezone)
- Best practices for timezone handling?
- Most problematic scenarios (beyond DST)?
- How to test timezone correctness?
- Libraries that "solve" the timezone problem?

### HealthForge Specifics
- Current Calendar widget - capabilities/limitations?
- Does HealthForge already have other wizards? How do they work?
- Skill level of typical HealthForge user?

### Alternative Solutions
- Is wizard the best solution?
- AI-assisted config (ChatGPT style)?
- Maybe simplify widget instead of adding wizard?

---

## 8. CONSTRAINTS

- **Deadline:** End of Sunday - spec only, no code
- **Scope:** Product spec (PRD + use cases + stories + alternatives)
- **Platform:** Limited to HealthForge capabilities (research needed)
- **Audience:** HealthForge recruiters (Product Manager role)

---

## 9. DELIVERABLES (Task Output)

1. **Complete discovery analysis:**
   - Market research report
   - Competitive analysis
   - User insights (synthetic interviews)

2. **Product specification:**
   - PRD (Product Requirements Document)
   - User stories + acceptance criteria
   - Wizard flow diagram
   - Template specifications (3-5 medical use cases)

3. **Problem prioritization:**
   - RICE scoring
   - Impact analysis on usability

4. **Alternative solutions:**
   - Evaluation of alternative approaches
   - Recommendation + rationale

5. **Technical recommendations:**
   - Timezone handling approach
   - Testing strategy
   - Library/tool recommendations

---

## 10. TOOLS & AGENTS

### Tools Used

- **Product Builder** - agent framework (C:\Users\artur\Desktop\Projekty\claude-pm-workflow)
- **Tavily Search** - market research, deep search
- **Agents:**
  - Business Analyst (JTBD, Opportunity Trees)
  - Synthetic User (user interviews)
  - Product Manager (RICE, prioritization)
  - PRD Writer (documentation)
  - Competitive Intelligence
  - Technical Researcher

### Frameworks

- **Jobs-to-be-Done** - user research
- **RICE Scoring** - problem/feature prioritization
- **Opportunity Solution Trees** - problem space mapping
- **Amazon 6-Pager** - PRD structure
- **User Story Mapping** - user journey

---

## 11. LESSONS FROM EXPERIENCE

### Known Timezone Pitfalls (from author's experience)

- **DST transitions** - especially Australia (different states, different transition dates)
- **Countries without DST** - Arizona, Hawaii (USA), Queensland (Australia)
- **Browser timezone vs server timezone** - always store in UTC, display in local
- **Date-only vs datetime** - "2024-03-10" can be different day in different timezone
- **End-user confusion** - user doesn't know which timezone they're viewing calendar in

### What Worked in Previous Projects

- **UTC storage + local display** - standard approach, works
- **Browser timezone detection** - `Intl.DateTimeFormat().resolvedOptions().timeZone`
- **Explicit timezone display** - show user "Local time: Europe/Warsaw (GMT+1)"
- **Test with different timezones** - manual testing with browser set to different timezones

---

## 12. SUCCESS CRITERIA (Recruitment Task)

Task is successful if:

- ✅ Full discovery cycle completed (research → insights → prioritization)
- ✅ PRD is complete, concrete, actionable (dev team can implement it)
- ✅ Timezone problem is deeply analyzed and solved in specification
- ✅ Use cases are realistic for medical domain
- ✅ Alternative solutions are evaluated with rationale for choice
- ✅ Documentation is professional-grade (ready for real PM review)
