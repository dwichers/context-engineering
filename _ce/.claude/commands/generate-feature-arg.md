# Generate Feature ARG Document

Genereer een gestructureerd Feature ARG (Application Requirements Generator) document voor een nieuwe feature.

## Feature Description: $ARGUMENTS

Dit bevat de beschrijving van de feature die toegevoegd moet worden aan de applicatie.

---

## Process

### Step 1: Context Gathering

1. **Check for Initial ARG**:
   - Look for initial ARG document in `_ce/arg/initial/`
   - Read it to understand the existing project context
   - Extract technical stack, data model, existing features

2. **Check for Existing Features**:
   - List files in `_ce/arg/feature/`
   - Read recent feature ARGs to understand numbering and dependencies
   - Identify highest feature number

3. **Understand Codebase** (if code exists):
   - Run `tree -L 3 -I 'node_modules|__pycache__|.git'` to see structure
   - Identify affected files/components
   - Note existing patterns to follow

### Step 2: Feature Analysis

Analyze the user's feature description:
- What functionality does it add?
- Which users benefit?
- How does it integrate with existing features?
- What are the dependencies?

### Step 3: Interactive Questioning

Stel gerichte vragen om een compleet beeld te krijgen. Gebruik de template `_ce/arg/feature/template/feature-arg-template.md` als leidraad.

**Belangrijke vraaggebieden**:

1. **Feature Scope & Goals**
   - Wat is het exacte doel van deze feature?
   - Welk probleem lost het op voor gebruikers?
   - Hoe verhoudt het zich tot bestaande features?
   - Is dit een must-have of nice-to-have?

2. **User Story & Acceptance Criteria**
   - Wie is de gebruiker?
   - Wat wil de gebruiker doen?
   - Waarom wil de gebruiker dit?
   - Wat zijn de success criteria?

3. **Technical Implementation**
   - Welke componenten moeten aangepast worden?
   - Welke nieuwe components nodig?
   - Database wijzigingen nodig?
   - API endpoints nodig?

4. **UI/UX Specifications**
   - Nieuwe pagina's/views nodig?
   - Wijzigingen aan bestaande UI?
   - Design voorbeelden of wireframes?
   - Interactie patronen?

5. **Data & API**
   - Welke data moet opgeslagen worden?
   - Database schema wijzigingen?
   - Nieuwe API endpoints?
   - External API integraties?

6. **Dependencies**
   - Afhankelijk van andere features?
   - Nieuwe libraries/packages nodig?
   - Breaking changes mogelijk?

7. **Testing & Performance**
   - Welke test scenarios?
   - Performance requirements?
   - Edge cases?
   - Error handling scenarios?

**Strategie**:
- Stel 3-5 vragen per ronde
- Gebruik AskUserQuestion voor multiple choice
- Itereer totdat volledig beeld
- Document onzekerheden

### Step 4: Determine Feature Number & Dependencies

1. **Calculate next feature number**:
   - List existing feature ARGs
   - Find highest number
   - Assign next sequential number

2. **Identify dependencies**:
   - Which features must exist first?
   - Order features logically
   - Note in dependencies section

### Step 5: Generate Feature ARG

1. **Read template**:
   ```bash
   Read _ce/arg/feature/template/feature-arg-template.md
   ```

2. **Fill all sections**:
   - Feature Metadata (number, name, priority, complexity)
   - Feature Overview (description, user story, business value)
   - Acceptance Criteria (functional & non-functional)
   - Technical Specifications (components, API, database)
   - UI/UX Specifications (pages, flows, wireframes)
   - API Specifications (endpoints, requests, responses)
   - Data Model (new/modified models, validation)
   - Security Considerations
   - Performance Considerations
   - Testing Strategy
   - Dependencies & Integration
   - Implementation Plan (step-by-step)
   - Error Handling
   - Success Metrics
   - Open Questions
   - References

3. **Generate filename**:
   ```
   Format: [number]-[feature-name]-feature-arg.md
   Example: 003-user-notifications-feature-arg.md
   ```

4. **Save**:
   ```
   Location: _ce/arg/feature/[filename].md
   ```

### Step 6: Review & Validation

1. Check completeness:
   - All sections filled
   - Dependencies identified
   - Implementation plan clear
   - Open questions documented

2. Show summary to user:
   ```
   ✅ Feature ARG gegenereerd: _ce/arg/feature/[filename].md

   Feature: [Name]
   Number: [X]
   Priority: [Priority]
   Complexity: [Complexity]
   Dependencies: [List of dependent features]

   Summary:
   - [X] acceptance criteria defined
   - [Y] API endpoints specified
   - [Z] database changes needed
   - Implementation estimated: [time]

   Open questions:
   - [Question 1]
   - [Question 2]

   Volgende stap:
   /generate-feature-prp _ce/arg/feature/[filename].md
   ```

---

## Important Guidelines

### DO:
- ✅ Check existing ARGs for context
- ✅ Assign logical feature number
- ✅ Identify all dependencies
- ✅ Be specific about technical requirements
- ✅ Define clear acceptance criteria
- ✅ Document all API specifications
- ✅ Plan database migrations if needed
- ✅ Consider security implications
- ✅ Estimate complexity realistically
- ✅ Reference existing code patterns

### DON'T:
- ❌ Skip dependency analysis
- ❌ Assume feature works in isolation
- ❌ Forget about database migrations
- ❌ Ignore security considerations
- ❌ Skip API specification details
- ❌ Forget error handling planning
- ❌ Miss integration points
- ❌ Create unrealistic estimates

---

## Quality Checklist

Before finalizing Feature ARG:

- [ ] Feature number is correct and sequential
- [ ] All dependencies identified
- [ ] Acceptance criteria are measurable
- [ ] Technical specifications are complete
- [ ] UI/UX is described (with references if available)
- [ ] API endpoints fully specified
- [ ] Database changes documented
- [ ] Security considerations addressed
- [ ] Performance requirements defined
- [ ] Testing strategy outlined
- [ ] Implementation plan is step-by-step
- [ ] Error handling scenarios covered
- [ ] Success metrics defined
- [ ] Open questions documented
- [ ] References added

---

## Example Interaction

```
User: /generate-feature-arg "Add email notifications when tasks are assigned"

AI: Ik ga een Feature ARG document maken voor email notificaties.
    Laat me eerst wat context verzamelen...

[Leest initial ARG en bestaande features]

AI: Ik zie dat:
    - Project gebruikt FastAPI backend
    - Er zijn al 2 features: (1) User auth, (2) Task management
    - Database heeft User en Task tables

    Dit wordt feature #003.

[Stelt vragen via AskUserQuestion]

Question 1: "Wanneer moeten email notificaties verstuurd worden?"
Options:
  - Direct bij task assignment
  - Dagelijkse digest van nieuwe tasks
  - Both (real-time + daily digest)

Question 2: "Welke email service provider?"
Options:
  - SendGrid
  - Mailgun
  - AWS SES
  - Resend
  - Andere (specificeer)

[Meer vragen over template, content, unsubscribe, etc.]

AI: ✅ Feature ARG gegenereerd: _ce/arg/feature/003-email-notifications-feature-arg.md

Feature: Email Notifications
Number: 003
Priority: High
Complexity: Medium
Dependencies: Feature #002 (Task Management)

Summary:
- 5 acceptance criteria defined
- 3 new API endpoints (configure notifications, send, unsubscribe)
- Database: Add notification_preferences table + email_logs table
- Integration: SendGrid API
- Implementation estimated: 3-4 days

Open questions:
- Rate limiting for email sending?
- Email templates versioning strategy?

Volgende stap:
/generate-feature-prp _ce/arg/feature/003-email-notifications-feature-arg.md
```

---

## Success Criteria

Het /generate-feature-arg commando is succesvol wanneer:

1. ✅ Feature number correct bepaald op basis van bestaande features
2. ✅ Alle dependencies geïdentificeerd
3. ✅ Compleet ARG document volgens template
4. ✅ Voldoende detail voor PRP generatie
5. ✅ Integration points met bestaande code duidelijk
6. ✅ Open vragen en aannames gedocumenteerd
7. ✅ Gebruiker begrijpt volgende stappen

---

**Remember**: Een goede Feature ARG moet naadloos integreren met bestaande features en codebase!