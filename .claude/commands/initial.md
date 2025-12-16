# Generate Initial ARG Document

Generate a structured Initial ARG (Application Requirements Generator) document based on the user's idea.

## User Input: $ARGUMENTS

This contains the description of the application/website idea.

---

## Process

### Step 1: Understand the Idea

Read the user input and identify:
- What does the user want to build?
- What problems does it solve?
- Who is the target audience?
- Are there any technical preferences mentioned?

### Step 2: Interactive Question Round

Ask targeted questions to get a complete picture. Use the template `_ce/arg/initial/template/initial-arg-template.md` as a guide for what information is needed.

**Important question areas**:

1. **Project Scope & Goals**
   - What is the main objective?
   - What problem does this solve?
   - Who are the end users?
   - What are must-have features vs nice-to-have?

2. **Technical Stack Preferences**
   - Frontend: Does the user prefer React, Vue, Svelte, Next.js?
   - Backend: Python (FastAPI, Django), Node.js (Express, NestJS)?
   - Database: PostgreSQL, MongoDB, MySQL?
   - Hosting: Vercel, AWS, Railway?
   - Does the user have experience with certain technologies?

3. **UI/UX Expectations**
   - Are there design examples or inspiration?
   - Which styling approach (Tailwind, CSS-in-JS, component library)?
   - Dark mode support?
   - Mobile-first or desktop-first?

4. **Features & Functionality**
   - Which core features are absolutely necessary?
   - Which features can be added later?
   - Are there user roles (admin, user, etc.)?
   - What integrations are needed (APIs, payment, etc.)?

5. **Data & Storage**
   - What kind of data needs to be stored?
   - Are there relationships between data entities?
   - How many users/data volume expected?

6. **Security & Compliance**
   - What security requirements?
   - Privacy requirements (GDPR)?
   - User authentication needed?

7. **Timeline & Resources**
   - What is the desired timeline?
   - Will this be an MVP or full application?
   - Are there budget constraints?

**Strategy for asking questions**:
- Ask 3-5 questions per round
- Make questions specific and actionable
- Offer multiple choice where possible (but allow other input)
- Use AskUserQuestion tool for structured questions
- Iterate until you have enough information

### Step 3: Process Answers

After each question round:
1. Process the answers into your understanding of the project
2. Identify gaps in information
3. Ask next round of questions if needed
4. Repeat until you have a complete picture

### Step 4: Generate ARG Document

When you have sufficient information:

1. **Read the template**:
   ```bash
   Read _ce/arg/initial/template/initial-arg-template.md
   ```

2. **Fill in all sections** with the collected information:
   - Project Overview (name, type, description)
   - Main Goal & Problem
   - Technical Stack (fully specified)
   - Core Functionalities (prioritized)
   - User Roles & Permissions
   - UI/UX Design (with references)
   - External Integrations
   - Data Model
   - Security & Compliance
   - Performance & Scalability
   - Testing & Quality
   - Platforms & Devices
   - Development Phases
   - Deployment & Operations
   - Documentation Requirements
   - Open Questions (for things that are still unclear)
   - References & Inspiration

3. **Generate filename**:
   - Format: `YYYY-MM-DD-[project-name]-initial-arg.md`
   - Example: `2024-03-15-ecommerce-platform-initial-arg.md`

4. **Save in correct location**:
   ```
   _ce/arg/initial/[generated-filename].md
   ```

### Step 5: Review & Confirmation

1. Show a summary of the generated document
2. Highlight any open questions or assumptions
3. Ask if the user is satisfied or wants modifications

### Step 6: Next Steps Guidance

Inform the user about next steps:
```
✅ Initial ARG document generated: _ce/arg/initial/[filename].md

Next steps:
1. Review the document and fill in any open questions
2. Generate an Initial PRP with: /generate-initial-prp _ce/arg/initial/[filename].md
3. Execute the Initial PRP with: /execute-initial _ce/prp/initial/[prp-filename].md
```

---

## Important Guidelines

### DO:
- ✅ Ask targeted, specific questions
- ✅ Use AskUserQuestion for multiple choice questions
- ✅ Iterate until you have a complete picture
- ✅ Fill in ALL sections of the template (use "TBD" for truly unknown info)
- ✅ Prioritize features (must-have vs nice-to-have)
- ✅ Document assumptions clearly
- ✅ Give realistic estimates for development phases
- ✅ Think about security and performance from the start

### DON'T:
- ❌ Don't generate a document without sufficient information
- ❌ Don't make assumptions without documenting them
- ❌ Don't skip important sections
- ❌ Don't choose technologies without user input
- ❌ Don't ignore security or performance considerations
- ❌ Don't create unrealistic timeline expectations

---

## Example Interaction Flow

```
User: /initial "I want to build a task management app"

AI: Interesting! Let me ask you some questions to get a good picture:

[Uses AskUserQuestion tool]
Question 1: "What is the main goal of this task management app?"
Options:
  - Personal productivity (individual users)
  - Team collaboration (teams/companies)
  - Both (both personal and team use)

Question 2: "Do you have a preference for a frontend framework?"
Options:
  - React + Next.js
  - Vue + Nuxt
  - Svelte + SvelteKit
  - Other (specify)

Question 3: "Which backend technology appeals to you?"
Options:
  - Python (FastAPI)
  - Node.js (Express/NestJS)
  - No preference (suggest the best)

[After answers, next round of questions about features, data model, etc.]

[Eventually generates ARG document]

AI: ✅ Initial ARG document generated: _ce/arg/initial/2024-03-15-task-management-initial-arg.md

The document contains:
- Complete technical stack specification
- 12 core features (8 must-have, 4 nice-to-have)
- Data model with 5 entities
- Security & compliance requirements
- Development phases (estimated 8 weeks)

Open questions documented:
- Integration with Google Calendar/Outlook?
- Payment gateway for premium features?

Next step:
/generate-initial-prp _ce/arg/initial/2024-03-15-task-management-initial-arg.md
```

---

## Quality Checklist

Before generating the final ARG document, ensure:

- [ ] All sections of template are filled in
- [ ] Technical stack is fully specified
- [ ] Features are prioritized (must/should/nice-to-have)
- [ ] Data model is described with relationships
- [ ] Security requirements are specified
- [ ] Open questions are documented
- [ ] Development phases have realistic estimates
- [ ] References and inspiration are added (if available)
- [ ] Filename follows naming convention
- [ ] Document is saved in _ce/arg/initial/

---

## Success Criteria

The /initial command is successful when:

1. ✅ All necessary information is collected via structured questioning
2. ✅ A complete ARG document is generated according to template
3. ✅ The document contains sufficient detail for PRP generation
4. ✅ Open questions and assumptions are clearly documented
5. ✅ User understands the next steps

---

**Remember**: The quality of the Initial ARG document determines the quality of the entire project. Take the time to gather all information properly!
