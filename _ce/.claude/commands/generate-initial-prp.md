# Generate Initial PRP Document

Genereer een uitgebreid Initial PRP (Product Requirements Prompt) document op basis van een Initial ARG document.

## ARG Document Path: $ARGUMENTS

Dit moet het pad zijn naar het initial ARG document: `_ce/arg/initial/[filename].md`

---

## Process

### Step 1: Load & Validate ARG Document

1. **Read the ARG document**:
   ```bash
   Read $ARGUMENTS
   ```

2. **Validate completeness**:
   - Check of alle belangrijke secties zijn ingevuld
   - Identificeer missing information
   - Als kritieke informatie ontbreekt, vraag gebruiker om aanvulling

3. **Extract key information**:
   - Project naam en beschrijving
   - Complete technical stack
   - Core features lijst
   - Data model en entities
   - Security requirements
   - Performance targets
   - Development phases

### Step 2: Research Phase

**CRITICAL**: Uitgebreid research is essentieel voor een goed PRP.

#### 2.1 Codebase Analysis

Als er een bestaande codebase is:
- Search voor vergelijkbare patterns
- Identificeer project structure conventions
- Note existing testing patterns
- Check deployment configurations

#### 2.2 Framework & Library Research

Voor elke technology in de stack:

1. **Framework Documentation**:
   ```yaml
   # Bijvoorbeeld voor FastAPI:
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
   - Zoek naar "[framework] project structure best practices"
   - Zoek naar "[framework] production deployment"
   - Zoek naar "[framework] testing strategies"

3. **Common Pitfalls**:
   - Search voor "[framework] common mistakes"
   - Search voor "[framework] gotchas"
   - Document version compatibility issues

#### 2.3 Integration Research

Voor alle external services/APIs uit ARG:
- API documentation URLs
- Authentication methods
- Rate limits
- SDKs available
- Example implementations

#### 2.4 Similar Projects Research

Search voor open-source projecten die vergelijkbaar zijn:
- GitHub repositories met goede architecture
- Starter templates voor de tech stack
- Example implementations

Sla relevante links op in het PRP.

#### 2.5 Examples Folder Check

Check `_ce/examples/` voor:
- Relevante code voorbeelden
- UI components
- API patterns
- Testing patterns

### Step 3: Generate PRP Structure

1. **Read the PRP template**:
   ```bash
   Read _ce/prp/initial/template/initial-prp-template.md
   ```

2. **Fill all sections** met informatie uit:
   - ARG document
   - Research findings
   - Framework documentation
   - Best practices

### Step 4: Create Implementation Blueprint

Dit is het belangrijkste deel - gedetailleerde tasks met:

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

**Voor elke task**:
- Specificeer PATTERN from examples or framework
- Lijst FILES to create/modify
- Geef PSEUDOCODE voor critical parts
- Specificeer VALIDATION steps

### Step 5: Create Validation Loops

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

### Step 6: Add Gotchas & Anti-patterns

Document CRITICAL information:
```python
# CRITICAL: [Framework] requires [specific setup]
# GOTCHA: [Common mistake]
# PATTERN: [Best practice to follow]
# ANTI-PATTERN: ❌ Don't [bad practice]
```

### Step 7: Generate Filename & Save

1. **Generate filename**:
   ```
   Format: YYYY-MM-DD-[project-name]-initial-prp.md
   Example: 2024-03-15-task-management-initial-prp.md
   ```

2. **Save document**:
   ```
   Location: _ce/prp/initial/[filename].md
   ```

### Step 8: Quality Check & Confidence Score

Beoordeel het PRP op:
- [ ] Alle context included (docs, examples, gotchas)
- [ ] Validation gates zijn executable
- [ ] References naar existing patterns
- [ ] Clear implementation path voor elke task
- [ ] Error handling documented
- [ ] Security considerations addressed
- [ ] Performance targets specified

**Score PRP op schaal 1-10**:
- 8-10: High confidence, one-pass implementation mogelijk
- 6-7: Medium confidence, mogelijk iteratie nodig
- <6: Low confidence, meer research of ARG detail nodig

### Step 9: User Guidance

Informeer gebruiker over:
```
✅ Initial PRP gegenereerd: _ce/prp/initial/[filename].md

Het PRP bevat:
- Complete implementation blueprint met [X] taken
- Validation loops voor self-checking
- [Y] framework documentation references
- [Z] gotchas en best practices

Confidence Score: [score]/10
[Uitleg van score]

Volgende stap:
/execute-initial _ce/prp/initial/[filename].md

Dit zal:
1. Project structure opzetten
2. Dependencies installeren
3. Database schema creëren
4. Authentication implementeren
5. Base UI componenten maken
6. CI/CD pipeline configureren
7. Alles testen en valideren
```

---

## Research Guidelines

### DO:
- ✅ Zoek official documentation voor alle frameworks
- ✅ Zoek naar production-ready examples
- ✅ Document version numbers en compatibility
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
- [ ] PATTERN references from examples/docs
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

Het /generate-initial-prp commando is succesvol wanneer:

1. ✅ Compleet PRP document gegenereerd volgens template
2. ✅ All necessary research completed en gedocumenteerd
3. ✅ Implementation blueprint met concrete, uitvoerbare tasks
4. ✅ Validation loops zijn executable en compleet
5. ✅ Gotchas en best practices gedocumenteerd
6. ✅ Confidence score is realistisch en explained
7. ✅ Document opgeslagen op juiste locatie
8. ✅ Gebruiker begrijpt volgende stappen

---

**Remember**: Een goed PRP is de sleutel tot successful one-pass implementation. Neem de tijd voor thorough research!