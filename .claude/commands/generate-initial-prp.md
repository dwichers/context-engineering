# Generate Initial PRP Document

Generate a comprehensive Initial PRP (Product Requirements Prompt) document based on an Initial ARG document.

## ARG Document Path: $ARGUMENTS

This must be the path to the initial ARG document: `_ce/arg/initial/[filename].md`

---

## Process

### Step 1: Load & Validate ARG Document

1. **Read the ARG document**:
   ```bash
   Read $ARGUMENTS
   ```

2. **Validate completeness**:
   - Check if all important sections are filled in
   - Identify missing information
   - If critical information is missing, ask user for completion

3. **Extract key information**:
   - Project name and description
   - Complete technical stack
   - Core features list
   - Data model and entities
   - Security requirements
   - Performance targets
   - Development phases

### Step 2: Research Phase

**CRITICAL**: Extensive research is essential for a good PRP.

#### 2.1 Codebase Analysis

If there's an existing codebase:
- Search for similar patterns
- Identify project structure conventions
- Note existing testing patterns
- Check deployment configurations

#### 2.2 Framework & Library Research

For each technology in the stack:

1. **Framework Documentation**:
   ```yaml
   # Example for FastAPI:
   - url: https://fastapi.tiangolo.com/
     sections:
       - Project Structure
       - Dependency Injection
       - Database Integration
       - Testing
       - Deployment
     critical_gotchas:
       - Async/await requirements
       - Pydantic v2 compatibility
       - CORS configuration
   ```

2. **Best Practices Search**:
   - Search for "[framework] project structure best practices"
   - Search for "[framework] production deployment"
   - Search for "[framework] testing strategies"

3. **Common Pitfalls**:
   - Search for "[framework] common mistakes"
   - Search for "[framework] gotchas"
   - Document version compatibility issues

#### 2.3 Integration Research

For all external services/APIs from ARG:
- API documentation URLs
- Authentication methods
- Rate limits
- SDKs available
- Example implementations

#### 2.4 Similar Projects Research

Search for open-source projects that are similar:
- GitHub repositories with good architecture
- Starter templates for the tech stack
- Example implementations

Save relevant links in the PRP.

#### 2.5 Examples Folder Check

Check `_ce/examples/` for:
- Relevant code examples
- UI components
- API patterns
- Testing patterns

### Step 3: Feature Separation (CRITICAL!)

**MOST IMPORTANT STEP**: Identify and separate features that do NOT belong to the foundation.

#### 3.1 Analyze Features from ARG

From the Initial ARG, categorize ALL features into:

**A. FOUNDATION (stays in Initial PRP)**:
- ✅ Project structure & configuration
- ✅ Database setup & basic schema
- ✅ Authentication & Authorization (user management)
- ✅ Core API structure
- ✅ Frontend routing & layout
- ✅ Basic UI components (buttons, forms, layouts)
- ✅ CI/CD pipeline
- ✅ Docker setup
- ✅ Documentation structure

**B. FEATURES (become Feature ARGs)**:
- ❌ Business logic features (everything not auth/basic)
- ❌ Advanced UI features
- ❌ External integrations (email, payment, etc.)
- ❌ Reporting/analytics features
- ❌ Admin panels (beyond basic CRUD)
- ❌ Notification systems
- ❌ File uploads/storage
- ❌ Search functionality
- ❌ Real-time features (WebSockets, etc.)
- ❌ Export/import features

#### 3.2 Create Feature ARG Documents

For EACH feature in category B:

1. **Determine feature number**:
   - Check `_ce/arg/feature/` for existing features
   - Assign next sequential number
   - Order by logical dependency (001, 002, 003, etc.)

2. **Generate Feature ARG** using template:
   ```bash
   Read _ce/arg/feature/template/feature-arg-template.md
   ```

3. **Fill Feature ARG** with information from Initial ARG:
   - Feature name & description
   - Priority (from Initial ARG priorities)
   - Dependencies (determine which features must come first)
   - Technical specs (extracted from Initial ARG)
   - Acceptance criteria
   - Data model changes
   - API endpoints
   - UI components

4. **Save Feature ARG**:
   ```
   Location: _ce/arg/feature/[number]-[feature-name]-feature-arg.md
   Format: 001-user-profile-management-feature-arg.md
   ```

5. **Repeat for ALL features** in category B

#### 3.3 Inform User

After separating features, inform the user:

```
🔍 Feature Separation Complete!

Foundation Features (in Initial PRP):
- Project initialization
- Database setup
- Authentication & user management
- Core API structure
- Frontend foundation
- CI/CD & Docker

Separated Features (Feature ARGs created):
[List all created feature ARGs with numbers]

✅ Generated Feature ARGs:
1. _ce/arg/feature/001-[name]-feature-arg.md - [Priority: High]
2. _ce/arg/feature/002-[name]-feature-arg.md - [Priority: High]
3. _ce/arg/feature/003-[name]-feature-arg.md - [Priority: Medium]
...

Recommended Implementation Order:
1. Execute Initial PRP first (/execute-initial)
2. Then implement features in numbered order:
   - /generate-feature-prp _ce/arg/feature/001-...
   - /execute-feature _ce/prp/feature/001-...
   - (repeat for each feature)
```

**CRITICAL**: The Initial PRP should ONLY contain the foundation. All business features MUST be separated!

---

### Step 4: Generate Initial PRP Structure

1. **Read the PRP template**:
   ```bash
   Read _ce/prp/initial/template/initial-prp-template.md
   ```

2. **Fill all sections** with information from:
   - ARG document (ONLY foundation parts)
   - Research findings
   - Framework documentation
   - Best practices

**IMPORTANT**: The Initial PRP contains ONLY the foundation - NOT the separated features!

---

### Step 5: Create Implementation Blueprint

This is the most important part - detailed tasks with:

#### Task 1: Project Initialization
- Directory structure creation
- Package initialization (npm init, poetry init, etc.)
- Git setup
- .env.example creation
- Configuration files

#### Task 2: Database Setup
- Database schema design (based on ARG data model)
- Migration setup (Alembic, Prisma, etc.)
- Initial migration
- Seed data (if needed)

#### Task 3: Authentication & Authorization
- Password hashing setup
- JWT token generation
- Auth endpoints (register, login, refresh)
- Auth middleware/dependencies
- Permission checking

#### Task 4: Core Backend Structure
- API routing setup
- Error handling middleware
- Logging configuration
- Validation schemas
- Database connection pooling

#### Task 5: Frontend Setup
- Framework initialization
- Routing configuration
- API client setup
- State management (if needed)
- UI component library setup

#### Task 6: Base UI Components
- Layout components
- Authentication pages
- Error pages
- Loading states
- Responsive design setup

#### Task 7: CI/CD Pipeline
- GitHub Actions / GitLab CI setup
- Linting automation
- Test automation
- Build automation
- Deployment automation

#### Task 8: Docker & Deployment
- Dockerfiles creation
- docker-compose for development
- Production deployment configuration
- Environment variables setup

#### Task 9: Documentation
- README with setup instructions
- API documentation (Swagger/OpenAPI)
- Architecture documentation
- Deployment guide

**For each task**:
- Specify PATTERN from examples or framework
- List FILES to create/modify
- Provide PSEUDOCODE for critical parts
- Specify VALIDATION steps

**REMINDER**: Only foundation tasks! Business features are already separated in Step 3.

---

### Step 6: Create Validation Loops

Define executable validation commands:

**Level 1: Syntax & Style**
```bash
# Backend
cd backend && ruff check . && mypy .

# Frontend
cd frontend && npm run lint && npm run type-check
```

**Level 2: Unit Tests**
```bash
# Backend
pytest tests/unit -v --cov

# Frontend
npm run test
```

**Level 3: Integration Tests**
```bash
# Manual tests or E2E framework
docker-compose up -d
curl http://localhost:8000/health
```

### Step 7: Add Gotchas & Anti-patterns

Document CRITICAL information:
```python
# CRITICAL: [Framework] requires [specific setup]
# GOTCHA: [Common mistake]
# PATTERN: [Best practice to follow]
# ANTI-PATTERN: ❌ Don't [bad practice]
```

### Step 8: Generate Filename & Save

1. **Generate filename**:
   ```
   Format: YYYY-MM-DD-[project-name]-initial-prp.md
   Example: 2024-03-15-task-management-initial-prp.md
   ```

2. **Save document**:
   ```
   Location: _ce/prp/initial/[filename].md
   ```

### Step 9: Quality Check & Confidence Score

Assess the PRP on:
- [ ] All context included (docs, examples, gotchas)
- [ ] Validation gates are executable
- [ ] References to existing patterns
- [ ] Clear implementation path for each task
- [ ] Error handling documented
- [ ] Security considerations addressed
- [ ] Performance targets specified

**Score PRP on scale 1-10**:
- 8-10: High confidence, one-pass implementation possible
- 6-7: Medium confidence, possible iteration needed
- <6: Low confidence, more research or ARG detail needed

### Step 10: User Guidance

Inform user about:
```
✅ Initial PRP generated: _ce/prp/initial/[filename].md

🔍 Feature Separation Complete!

Foundation in Initial PRP:
- Complete implementation blueprint with [X] foundation tasks
- Validation loops for self-checking
- [Y] framework documentation references
- [Z] gotchas and best practices

Separated Features (Feature ARGs created):
✅ Generated [N] Feature ARGs:
1. _ce/arg/feature/001-[name]-feature-arg.md - [Priority]
2. _ce/arg/feature/002-[name]-feature-arg.md - [Priority]
3. _ce/arg/feature/003-[name]-feature-arg.md - [Priority]
... (list all created features)

Confidence Score: [score]/10
[Explanation of score]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📋 Recommended Implementation Order:

PHASE 1 - Foundation:
/execute-initial _ce/prp/initial/[filename].md

This will implement:
1. Set up project structure
2. Install dependencies
3. Create database schema (basic tables only)
4. Implement authentication
5. Create base UI components
6. Configure CI/CD pipeline
7. Docker setup
8. Documentation
9. Test and validate everything

PHASE 2 - Features (implement in numbered order):
For each feature:
  1. /generate-feature-prp _ce/arg/feature/[number]-[name]-feature-arg.md
  2. /execute-feature _ce/prp/feature/[number]-[name]-feature-prp.md
  3. Test & validate
  4. Move to next feature

Start with:
/execute-initial _ce/prp/initial/[filename].md

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Research Guidelines

### DO:
- ✅ Search official documentation for all frameworks
- ✅ Search for production-ready examples
- ✅ Document version numbers and compatibility
- ✅ Include specific documentation URLs
- ✅ Note rate limits for external APIs
- ✅ Find starter templates/boilerplates
- ✅ Check for recent blog posts with gotchas
- ✅ Look for GitHub repos with similar stack
- ✅ Research deployment platforms documentation
- ✅ Find testing strategies for the stack

### DON'T:
- ❌ Skip research and guess best practices
- ❌ Include outdated documentation
- ❌ Forget to document library versions
- ❌ Ignore framework-specific gotchas
- ❌ Skip security best practices research
- ❌ Forget about deployment considerations
- ❌ Miss authentication/authorization patterns
- ❌ Overlook database migration strategies

---

## PRP Quality Checklist

Before saving the PRP, ensure:

### Feature Separation (CRITICAL!)
- [ ] ALL business features extracted from Initial ARG
- [ ] Feature ARG documents created for each separated feature
- [ ] Features numbered in logical dependency order
- [ ] Each Feature ARG has clear dependencies noted
- [ ] Initial PRP contains ONLY foundation tasks
- [ ] User informed about separated features

### Context Completeness
- [ ] All framework documentation URLs included
- [ ] Specific sections to read highlighted
- [ ] Critical gotchas documented
- [ ] Library versions specified
- [ ] Similar project references added
- [ ] Examples from _ce/examples/ referenced

### Implementation Blueprint
- [ ] All tasks clearly defined
- [ ] Task order is logical (dependencies respected)
- [ ] FILES to create/modify listed for each task
- [ ] PATTERN references from _ce/examples/ docs
- [ ] PSEUDOCODE for complex parts
- [ ] VALIDATION steps for each task

### Technical Completeness
- [ ] Database schema fully designed
- [ ] Authentication flow detailed
- [ ] API structure planned
- [ ] Frontend routing planned
- [ ] State management chosen (if needed)
- [ ] Error handling strategy defined
- [ ] Logging strategy defined

### DevOps & Deployment
- [ ] Docker configuration planned
- [ ] CI/CD pipeline defined
- [ ] Environment variables documented
- [ ] Deployment strategy specified
- [ ] Monitoring/logging planned

### Testing Strategy
- [ ] Unit test requirements defined
- [ ] Integration test scenarios listed
- [ ] E2E test plan created
- [ ] Coverage targets set
- [ ] Testing tools specified

### Documentation Requirements
- [ ] README structure defined
- [ ] API documentation approach chosen
- [ ] Code comment guidelines specified
- [ ] User documentation planned (if needed)

### Validation Loops
- [ ] Level 1: Syntax/style commands are executable
- [ ] Level 2: Unit test commands specified
- [ ] Level 3: Integration test procedures defined
- [ ] All validation expected outcomes documented

---

## Example Output Structure

```markdown
# Initial Project Setup - Product Requirements Prompt (PRP)

**Generated from**: _ce/arg/initial/2024-03-15-task-management-initial-arg.md
**Generated on**: 2024-03-15
**Project Name**: Task Management Application

## Purpose
Setup complete foundation for a task management application with:
- FastAPI backend with PostgreSQL
- React + Next.js frontend with Tailwind CSS
- JWT authentication
- Docker development environment
- CI/CD pipeline

## Core Principles
[From template]

## Project Overview
[From ARG]

## All Needed Context

### Documentation & References
```yaml
# Backend Framework
- url: https://fastapi.tiangolo.com/tutorial/
  why: Project structure, dependency injection, testing
  critical: Async/await patterns, Pydantic v2 usage

- url: https://www.sqlalchemy.org/
  why: ORM setup, migrations with Alembic
  critical: Async engine setup, relationship patterns

# Frontend Framework
- url: https://nextjs.org/docs
  why: App router, API routes, deployment
  critical: Server components vs client components

# And more...
```

### Known Gotchas
```python
# CRITICAL: FastAPI requires async throughout
# CRITICAL: Next.js 13+ App Router is different from Pages Router
# GOTCHA: PostgreSQL requires psycopg2-binary for development
# etc...
```

## Implementation Blueprint

### Task 1: Project Initialization
[Detailed implementation steps with pseudocode]

### Task 2: Database Setup
[Detailed implementation steps with pseudocode]

[... etc for all tasks ...]

## Validation Loop
[Executable commands]

## Final Validation Checklist
[Comprehensive checklist]

**Confidence Score: 9/10**

High confidence because:
- Popular tech stack with excellent documentation
- Many similar projects exist
- Clear patterns from official docs
- Well-defined requirements in ARG

Minor uncertainty:
- Specific state management needs might evolve
```

---

## Success Criteria

The /generate-initial-prp command is successful when:

1. ✅ Complete PRP document generated according to template
2. ✅ All necessary research completed and documented
3. ✅ Implementation blueprint with concrete, executable tasks
4. ✅ Validation loops are executable and complete
5. ✅ Gotchas and best practices documented
6. ✅ Confidence score is realistic and explained
7. ✅ Document saved in correct location
8. ✅ User understands next steps

---

**Remember**: A good PRP is the key to successful one-pass implementation. Take the time for thorough research!
