# Generate/Update CLAUDE.md

Analyze the project and update CLAUDE.md with project-specific information while maintaining the generic workflow foundation.

---

## Process

### Step 1: Analyze Current State

#### 1.1 Read Current CLAUDE.md
```bash
Read CLAUDE.md
```

**Check for**:
- Does it have project-specific information already?
- Is the generic workflow foundation still intact?
- What sections need updating?

#### 1.2 Find Project Documents

**Search for ARG documents**:
```bash
Glob **/*-initial-arg.md in _ce/arg/initial/
Glob **/*-feature-arg.md in _ce/arg/feature/
```

**Search for PRP documents**:
```bash
Glob **/*-initial-prp.md in _ce/prp/initial/
Glob **/*-feature-prp.md in _ce/prp/feature/
```

**Priority**:
1. If Initial PRP exists → Use this (most complete context)
2. Else if Initial ARG exists → Use this
3. Else → Use codebase analysis only

#### 1.3 Analyze Project Structure
```bash
# Check for common project files
Read package.json (if exists - Frontend)
Read requirements.txt (if exists - Python backend)
Read pyproject.toml (if exists - Python backend)
Read Cargo.toml (if exists - Rust)
Read go.mod (if exists - Go)
Read composer.json (if exists - PHP)
Read Gemfile (if exists - Ruby)
Read pom.xml (if exists - Java/Maven)
Read build.gradle (if exists - Java/Gradle)

# Check for environment files
Read .env.example (if exists)

# Check for Docker
Read docker-compose.yml (if exists)
Read Dockerfile (if exists)

# Check for CI/CD
Glob .github/workflows/*.yml
Glob .gitlab-ci.yml
```

### Step 2: Extract Project Information

From the documents and files found, extract:

#### 2.1 Project Metadata
- **Project Name**: From ARG/PRP or infer from root directory name
- **Description**: From ARG/PRP project goal/description section
- **Phase**: Initial (foundation only), Features (some features done), Production (all features done)

#### 2.2 Technology Stack

**Backend**:
- Framework (FastAPI, Express, Django, Rails, etc.)
- Language & version (Python 3.11, Node 18, etc.)
- Key libraries/packages

**Frontend**:
- Framework (React, Vue, Angular, Svelte, etc.)
- Language (TypeScript, JavaScript)
- UI library (Material-UI, Tailwind, Bootstrap, etc.)
- Build tool (Vite, Webpack, etc.)

**Database**:
- Type (PostgreSQL, MySQL, MongoDB, etc.)
- ORM/ODM (SQLAlchemy, Prisma, Mongoose, etc.)
- Migration tool (Alembic, Prisma, etc.)

**Infrastructure**:
- Containerization (Docker, Docker Compose)
- CI/CD (GitHub Actions, GitLab CI, etc.)
- Hosting/Deployment (Vercel, Railway, AWS, etc.)
- Cloud services used

#### 2.3 Project Structure

**Create a tree** of important directories:
```
project/
├── backend/
│   ├── app/
│   ├── tests/
│   └── alembic/
├── frontend/
│   ├── src/
│   └── public/
└── _ce/
```

Only include actual existing directories.

#### 2.4 Key Dependencies

**Backend** (from requirements.txt, package.json, etc.):
- List 10-15 most important packages with versions
- Group by category (web framework, database, auth, testing, etc.)

**Frontend** (from package.json):
- List 10-15 most important packages with versions
- Group by category (framework, UI, state management, testing, etc.)

#### 2.5 Development Commands

**From package.json scripts** or **common commands**:

Backend:
```bash
# Development
python -m uvicorn app.main:app --reload  # or npm run dev

# Testing
pytest  # or npm test

# Linting
ruff check .  # or npm run lint

# Database migrations
alembic upgrade head
```

Frontend:
```bash
# Development
npm run dev

# Build
npm run build

# Testing
npm test

# Linting
npm run lint
```

#### 2.6 Environment Variables

**From .env.example** or **ARG/PRP**:
```
DATABASE_URL=postgresql://...
SECRET_KEY=your-secret-key
API_KEY=your-api-key
```

List required variables with descriptions.

#### 2.7 External Services

**From ARG/PRP** "External Integrations" or "Third-Party Services":
- Service name
- Purpose
- API documentation URL
- Authentication method

Example:
- **Stripe**: Payment processing (https://stripe.com/docs/api)
- **SendGrid**: Email delivery (https://docs.sendgrid.com/)
- **AWS S3**: File storage (https://docs.aws.amazon.com/s3/)

#### 2.8 Code Patterns & Conventions

**From PRP "Patterns" section** or **codebase analysis**:

- File naming (kebab-case, snake_case, PascalCase)
- Import style (absolute, relative)
- Component structure (functional, class-based)
- API structure (REST, GraphQL)
- Error handling patterns
- Logging patterns

#### 2.9 Testing Strategy

**From PRP or codebase**:
- Testing framework (pytest, jest, vitest)
- Test structure (unit, integration, e2e)
- Coverage target
- Test file naming convention

#### 2.10 Known Issues & Gotchas

**From PRP "Gotchas" or "Known Issues"**:
- Framework-specific issues
- Version compatibility issues
- Common mistakes
- Performance considerations

#### 2.11 Implementation Status

**From Feature ARGs**:
```
✅ Foundation: Complete
✅ Feature 001: User Authentication - Complete
🚧 Feature 002: Dashboard - In Progress
⏳ Feature 003: Reporting - Not Started
```

### Step 3: Generate Project-Specific Section

Using the extracted information, create the project-specific content:

#### 3.1 Load Template
```bash
Read .claude/CLAUDE-template.md
```

#### 3.2 Fill Template Placeholders

Replace all `{{PLACEHOLDER}}` markers with extracted information:

**{{PROJECT_NAME}}**: Extracted project name

**{{PROJECT_DESCRIPTION}}**: Brief description from ARG/PRP

**{{BACKEND_STACK}}**:
```markdown
- **Framework**: FastAPI 0.104.1
- **Language**: Python 3.11
- **Key Libraries**:
  - Pydantic 2.5 (validation)
  - SQLAlchemy 2.0 (ORM)
  - Alembic 1.12 (migrations)
  - python-jose (JWT auth)
```

**{{FRONTEND_STACK}}**:
```markdown
- **Framework**: React 18.2 with TypeScript
- **Build Tool**: Vite 5.0
- **UI Library**: Material-UI (MUI) 5.14
- **State Management**: React Query + Context API
- **Routing**: React Router 6.20
```

**{{DATABASE_STACK}}**:
```markdown
- **Database**: PostgreSQL 15
- **ORM**: SQLAlchemy 2.0
- **Migrations**: Alembic 1.12
```

**{{INFRASTRUCTURE_STACK}}**:
```markdown
- **Containerization**: Docker + Docker Compose
- **CI/CD**: GitHub Actions
- **Deployment**: Railway (backend), Vercel (frontend)
```

**{{PROJECT_STRUCTURE}}**: Tree structure from step 2.3

**{{BACKEND_DEPENDENCIES}}**:
```markdown
**Web Framework**:
- fastapi==0.104.1
- uvicorn[standard]==0.24.0

**Database**:
- sqlalchemy==2.0.23
- alembic==1.12.1
- psycopg2-binary==2.9.9

**Authentication**:
- python-jose[cryptography]==3.3.0
- passlib[bcrypt]==1.7.4

**Testing**:
- pytest==7.4.3
- pytest-asyncio==0.21.1
```

**{{FRONTEND_DEPENDENCIES}}**: Similar format

**{{BACKEND_COMMANDS}}**: Commands from step 2.5

**{{FRONTEND_COMMANDS}}**: Commands from step 2.5

**{{ENVIRONMENT_VARIABLES}}**:
```markdown
Required environment variables (see `.env.example`):

**Backend**:
- `DATABASE_URL` - PostgreSQL connection string
- `SECRET_KEY` - JWT secret key (generate with `openssl rand -hex 32`)
- `CORS_ORIGINS` - Allowed CORS origins (comma-separated)

**Frontend**:
- `VITE_API_URL` - Backend API URL
```

**{{EXTERNAL_SERVICES}}**: From step 2.7

**{{CODE_ORGANIZATION}}**:
```markdown
- **Backend**: Feature-based modules in `app/`
  - `app/models/` - SQLAlchemy models
  - `app/schemas/` - Pydantic schemas
  - `app/api/` - API routes
  - `app/services/` - Business logic
  - `app/core/` - Config, security, database

- **Frontend**: Feature-based components
  - `src/components/` - Reusable components
  - `src/features/` - Feature-specific code
  - `src/api/` - API client
  - `src/hooks/` - Custom React hooks
```

**{{NAMING_CONVENTIONS}}**:
```markdown
- **Files**: kebab-case for frontend, snake_case for backend
- **Components**: PascalCase
- **Functions**: camelCase (frontend), snake_case (backend)
- **Constants**: UPPER_SNAKE_CASE
- **Database tables**: snake_case, plural
```

**{{TESTING_STRATEGY}}**: From step 2.9

**{{KNOWN_ISSUES}}**: From step 2.10 (or "None documented yet" if empty)

**{{IMPLEMENTATION_STATUS}}**: From step 2.11

### Step 4: Preserve Generic Foundation

**CRITICAL**: The generic workflow sections must NEVER be modified:

**Keep unchanged**:
- "Context Engineering Workflow" section (lines 1-62 in template)
- "Working with PRPs" section
- "Integration with Existing Code" section
- "Task Management" section
- "AI Behavior Rules" section
- "Remember" section

**Only replace**:
- Content between `{{PROJECT_SPECIFIC_START}}` and `{{PROJECT_SPECIFIC_END}}`
- This becomes the new "Project-Specific Information" section

### Step 5: Handle Missing Information

If some information cannot be extracted:

**Option 1 - No ARG/PRP exists**:
```markdown
## 📦 Project-Specific Information

> ⚠️ **No ARG/PRP documents found yet.**
>
> Run `/initial "your project description"` to start the Context Engineering workflow.
> After generating ARG and PRP documents, run `/generate-claude` again to populate this section.

### Technology Stack
(To be populated after running `/generate-initial-prp`)
```

**Option 2 - Partial information**:
Fill what you can find, mark missing sections:
```markdown
### External Services & Integrations
(No external services documented yet)
```

**Option 3 - Ask user** (for critical missing info):
If tech stack cannot be determined from any files:
```
I couldn't find package.json, requirements.txt, or similar dependency files.
What is your technology stack?

1. Python (FastAPI/Django/Flask)
2. Node.js (Express/NestJS)
3. TypeScript (Next.js/Remix)
4. Other (specify)
```

### Step 6: Update CLAUDE.md

**Compare versions**:
1. Read current CLAUDE.md
2. Check if project-specific section exists
3. Determine update strategy:
   - **No project section**: Insert new section after "Feature Separation"
   - **Has project section**: Replace entire project section
   - **Keep generic sections**: Never modify workflow sections

**Write updated CLAUDE.md**:
```bash
Write CLAUDE.md with merged content
```

### Step 7: Validation & Report

#### 7.1 Validate Structure
Check the updated CLAUDE.md has:
- ✅ Generic workflow sections intact
- ✅ Project-specific section present
- ✅ All placeholders replaced (no `{{}}` remaining)
- ✅ Proper markdown formatting
- ✅ All sections have content (no empty sections)

#### 7.2 Generate Report

```
✅ CLAUDE.md Updated Successfully!

📋 Summary of Changes
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📦 Project Information
- Name: [Project Name]
- Description: [Brief description]
- Phase: [Initial/Features/Production]

🔧 Technology Stack Detected
Backend:
  - [Framework] [version]
  - [Database] [version]

Frontend:
  - [Framework] [version]
  - [UI Library] [version]

📚 Documentation Sources
- Initial ARG: [✅/❌] _ce/arg/initial/[filename]
- Initial PRP: [✅/❌] _ce/prp/initial/[filename]
- Feature ARGs: [X] features documented
- Codebase Analysis: [✅/❌]

✨ Sections Updated
- [✅] Technology Stack
- [✅] Project Structure
- [✅] Dependencies
- [✅] Development Commands
- [✅] Environment Variables
- [✅] Code Patterns
- [❌] External Services (none found)
- [✅] Implementation Status

⚠️ Manual Review Needed
- [ ] Verify environment variables are complete
- [ ] Add any missing external services
- [ ] Update known issues/gotchas as you discover them

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

💡 Next Steps:
1. Review the updated CLAUDE.md
2. Add any additional project-specific patterns
3. Update as project evolves
4. Re-run `/generate-claude` after major changes

The updated CLAUDE.md now provides project-specific context
while maintaining the generic Context Engineering workflow foundation.
```

---

## Important Guidelines

### DO:
- ✅ Analyze ALL available sources (ARG, PRP, package files, codebase)
- ✅ Preserve generic workflow sections completely
- ✅ Fill all placeholders with real data
- ✅ Mark missing information clearly
- ✅ Include version numbers for dependencies
- ✅ Keep project-specific section concise (focus on essentials)
- ✅ Update implementation status from feature ARGs
- ✅ Include actual commands that work for this project
- ✅ Extract patterns from existing PRPs

### DON'T:
- ❌ Don't modify generic workflow sections
- ❌ Don't leave `{{PLACEHOLDER}}` markers in final output
- ❌ Don't invent/hallucinate dependencies or services
- ❌ Don't make assumptions about tech stack if no evidence
- ❌ Don't include outdated information
- ❌ Don't make project section too verbose (keep it actionable)
- ❌ Don't skip validation checks

---

## Success Criteria

The `/generate-claude` command is successful when:

1. ✅ CLAUDE.md contains accurate project-specific information
2. ✅ Generic workflow sections remain unchanged
3. ✅ All placeholders are replaced with real data
4. ✅ Tech stack is correctly identified
5. ✅ Development commands are accurate and tested
6. ✅ Environment variables are documented
7. ✅ No markdown syntax errors
8. ✅ Implementation status reflects current state
9. ✅ Missing information is clearly marked
10. ✅ Document is concise and actionable

---

**Remember**: CLAUDE.md is included with every Claude Code request. Keep the project-specific section focused on essential information that helps Claude Code understand this specific project while maintaining the generic workflow foundation.
