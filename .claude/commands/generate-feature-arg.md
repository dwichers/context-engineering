# Generate Feature ARG Document

Generate a structured Feature ARG (Application Requirements Generator) document for a new feature.

## Feature Description: $ARGUMENTS

This contains the description of the feature that should be added to the application.

---

## Process

### Step 1: Context Gathering

1. **Check for Initial ARG**:
   - Look for initial ARG document in `.claude/arg/initial/`
   - Read it to understand the existing project context
   - Extract technical stack, data model, existing features

2. **Check for Existing Features**:
   - List files in `.claude/arg/feature/`
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

Ask targeted questions to get a complete picture. Use the template `.claude/arg/feature/template/feature-arg-template.md` as a guide.

**Important question areas**:

1. **Feature Scope & Goals**
   - What is the exact goal of this feature?
   - What problem does it solve for users?
   - How does it relate to existing features?
   - Is this a must-have or nice-to-have?

2. **User Story & Acceptance Criteria**
   - Who is the user?
   - What does the user want to do?
   - Why does the user want this?
   - What are the success criteria?

3. **Technical Implementation**
   - Which components need to be modified?
   - What new components are needed?
   - Database changes needed?
   - API endpoints needed?

4. **UI/UX Specifications**
   - New pages/views needed?
   - Changes to existing UI?
   - Design examples or wireframes?
   - Interaction patterns?

5. **Data & API**
   - What data needs to be stored?
   - Database schema changes?
   - New API endpoints?
   - External API integrations?

6. **Dependencies**
   - Dependent on other features?
   - New libraries/packages needed?
   - Breaking changes possible?

7. **Testing & Performance**
   - What test scenarios?
   - Performance requirements?
   - Edge cases?
   - Error handling scenarios?

**Strategy**:
- Ask 3-5 questions per round
- Use AskUserQuestion for multiple choice
- Iterate until complete picture
- Document uncertainties

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
   Read .claude/arg/feature/template/feature-arg-template.md
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
   Location: .claude/arg/feature/[filename].md
   ```

### Step 6: Review & Validation

1. Check completeness:
   - All sections filled
   - Dependencies identified
   - Implementation plan clear
   - Open questions documented

2. Show summary to user:
   ```
   ✅ Feature ARG generated: .claude/arg/feature/[filename].md

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

   Next step:
   /generate-feature-prp .claude/arg/feature/[filename].md
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

AI: I'm going to create a Feature ARG document for email notifications.
    Let me first gather some context...

[Reads initial ARG and existing features]

AI: I see that:
    - Project uses FastAPI backend
    - There are already 2 features: (1) User auth, (2) Task management
    - Database has User and Task tables

    This will be feature #003.

[Asks questions via AskUserQuestion]

Question 1: "When should email notifications be sent?"
Options:
  - Immediately on task assignment
  - Daily digest of new tasks
  - Both (real-time + daily digest)

Question 2: "Which email service provider?"
Options:
  - SendGrid
  - Mailgun
  - AWS SES
  - Resend
  - Other (specify)

[More questions about template, content, unsubscribe, etc.]

AI: ✅ Feature ARG generated: .claude/arg/feature/003-email-notifications-feature-arg.md

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

Next step:
/generate-feature-prp .claude/arg/feature/003-email-notifications-feature-arg.md
```

---

## Success Criteria

The /generate-feature-arg command is successful when:

1. ✅ Feature number correctly determined based on existing features
2. ✅ All dependencies identified
3. ✅ Complete ARG document according to template
4. ✅ Sufficient detail for PRP generation
5. ✅ Integration points with existing code clear
6. ✅ Open questions and assumptions documented
7. ✅ User understands next steps

---

**Remember**: A good Feature ARG must integrate seamlessly with existing features and codebase!
