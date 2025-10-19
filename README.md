# 🚀 Phased Application Development with Context Engineering

An AI-driven development workflow system that helps you transform an application idea into a fully structured, implemented project with validated code.

---

## 📚 Table of Contents

- [What is Context Engineering?](#what-is-context-engineering)
- [Quick Start](#-quick-start)
- [Workflow Overview](#-workflow-overview)
- [Repository Structure](#-repository-structure)
- [Detailed Workflow](#-detailed-workflow)
- [Slash Commands Reference](#-slash-commands-reference)
- [Best Practices](#-best-practices)
- [Examples](#-examples)
- [FAQ](#-faq)

---

## What is Context Engineering?

Context Engineering is a discipline focused on engineering **complete context** for AI coding assistants, ensuring they have sufficient information to successfully execute end-to-end tasks.

### Why Context Engineering?

**Traditional approaches:**
- ❌ **Vibe Coding**: "Build me an app" → unpredictable results
- ❌ **Prompt Engineering**: Focus on clever wording → limited scope
- ❌ **Ad-hoc AI usage**: No structure → many iterations needed

**Context Engineering:**
- ✅ **Structured process**: From idea → ARG → PRP → validated code
- ✅ **Comprehensive context**: All docs, patterns, gotchas included
- ✅ **Self-validating**: AI can test and improve its own work
- ✅ **One-pass success**: Enough context for correct implementation on first try

### Core Principles

1. **Context is King**: Include ALL necessary documentation, examples, and caveats
2. **Validation Loops**: Provide executable tests/lints the AI can run and fix
3. **Information Dense**: Use keywords and patterns from the codebase
4. **Progressive Success**: Start simple, validate, then enhance

---

## 🎯 Quick Start

### Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- Git repository cloned

### Step 1: Start with an Idea

```bash
# In Claude Code, use the /initial command
/initial "I want to build a task management application for teams"
```

Claude asks interactive questions to fully develop your idea:
- Which technology stack?
- Which core features?
- Who are the users?
- Security requirements?
- Performance targets?

**Result**: `_ce/arg/initial/YYYY-MM-DD-[project-name]-initial-arg.md`

### Step 2: Generate Initial PRP

```bash
# Generate implementation blueprint
/generate-initial-prp _ce/arg/initial/[your-initial-arg-file].md
```

Claude performs extensive research and creates a PRP with:
- Complete implementation blueprint
- Framework documentation references
- Database schema design
- Authentication setup
- Testing strategy
- Validation commands

**Result**: `_ce/prp/initial/YYYY-MM-DD-[project-name]-initial-prp.md`

### Step 3: Execute Initial Setup

```bash
# Implement the foundation
/execute-initial _ce/prp/initial/[your-initial-prp-file].md
```

Claude implements:
- ✅ Project structure
- ✅ Database setup & migrations
- ✅ Authentication & authorization
- ✅ Backend API foundation
- ✅ Frontend setup & routing
- ✅ Base UI components
- ✅ CI/CD pipeline
- ✅ Docker configuration
- ✅ Complete documentation

**Validation**: All tests pass, code is production-ready!

### Step 4: Add Features

```bash
# Feature 1: Generate ARG
/generate-feature-arg "Add email notifications when tasks are assigned"

# Feature 1: Generate PRP
/generate-feature-prp _ce/arg/feature/001-email-notifications-feature-arg.md

# Feature 1: Implement
/execute-feature _ce/prp/feature/001-email-notifications-feature-prp.md
```

**Repeat for each feature!**

---

## 🎯 Workflow Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                   CONTEXT ENGINEERING WORKFLOW                   │
└─────────────────────────────────────────────────────────────────┘

1️⃣ IDEA PHASE
   ├─ Describe your application idea
   └─ /initial "[description]"
      └─> _ce/arg/initial/[project]-initial-arg.md

2️⃣ INITIAL SETUP PLANNING + FEATURE SEPARATION
   ├─ /generate-initial-prp [initial-arg-path]
   │
   ├─ STEP 2.1: Research
   │    ├─ Research frameworks, best practices
   │    └─ Design database schema
   │
   ├─ STEP 2.2: FEATURE SEPARATION (CRITICAL!)
   │    ├─ Analyze ALL features from Initial ARG
   │    ├─ Foundation features → stay in Initial PRP
   │    ├─ Business features → separate Feature ARGs
   │    └─> CREATE: _ce/arg/feature/001-[name]-feature-arg.md
   │         CREATE: _ce/arg/feature/002-[name]-feature-arg.md
   │         CREATE: _ce/arg/feature/003-[name]-feature-arg.md
   │         ... (all business features)
   │
   └─ STEP 2.3: Initial PRP (foundation only!)
      └─> _ce/prp/initial/[project]-initial-prp.md

3️⃣ INITIAL SETUP EXECUTION (Foundation Only!)
   ├─ /execute-initial [initial-prp-path]
   ├─ Implement: DB (basic), Auth, Core APIs, Base UI, CI/CD
   ├─ Run validations (linting, tests, E2E)
   └─> ✅ Production-ready foundation (NO business features yet!)

4️⃣ FEATURE DEVELOPMENT
   For each Feature ARG (auto-generated in step 2.2):

   ├─ A: Feature ARG already exists from step 2.2!
   │    └─> _ce/arg/feature/[number]-[name]-feature-arg.md
   │
   │    OR manually add new feature:
   │    /generate-feature-arg "[feature description]"
   │    └─> _ce/arg/feature/[next-number]-[name]-feature-arg.md
   │
   ├─ B: /generate-feature-prp [feature-arg-path]
   │    ├─ Research specific implementation
   │    ├─ Define integration points
   │    └─> _ce/prp/feature/[number]-[name]-feature-prp.md
   │
   └─ C: /execute-feature [feature-prp-path]
        ├─ Implement backend + frontend
        ├─ Write & run tests
        └─> ✅ Feature complete & validated

5️⃣ ITERATION
   └─ Repeat step 4 for each next feature (in numbered order!)

┌─────────────────────────────────────────────────────────────────┐
│                    RESULT: COMPLETE APP                          │
│  - Structured development                                        │
│  - Fully tested                                                  │
│  - Production-ready                                              │
│  - Documented                                                    │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📁 Repository Structure

```
context-engineering-claude/
├── _ce/                                    # Context Engineering directory
│   ├── .claude/
│   │   ├── commands/                       # Slash commands
│   │   │   ├── initial.md                  # /initial command
│   │   │   ├── generate-initial-prp.md     # /generate-initial-prp
│   │   │   ├── generate-feature-arg.md     # /generate-feature-arg
│   │   │   ├── generate-feature-prp.md     # /generate-feature-prp
│   │   │   ├── execute-initial.md          # /execute-initial
│   │   │   └── execute-feature.md          # /execute-feature
│   │   └── settings.local.json             # Claude Code settings
│   │
│   ├── arg/                                # Application Requirements Generator
│   │   ├── initial/                        # Initial project requirements
│   │   │   ├── template/
│   │   │   │   └── initial-arg-template.md
│   │   │   └── [generated-initial-args].md
│   │   └── feature/                        # Feature requirements
│   │       ├── template/
│   │       │   └── feature-arg-template.md
│   │       └── [generated-feature-args].md
│   │
│   ├── prp/                                # Product Requirements Prompts
│   │   ├── initial/                        # Initial setup blueprints
│   │   │   ├── template/
│   │   │   │   └── initial-prp-template.md
│   │   │   └── [generated-initial-prps].md
│   │   └── feature/                        # Feature implementation blueprints
│   │       ├── template/
│   │       │   └── feature-prp-template.md
│   │       └── [generated-feature-prps].md
│   │
│   └── examples/                           # Code examples & references
│       └── README.md
│
├── CLAUDE.md                               # Global AI guidelines
├── README.md                               # This file
└── [your-project-files-here]/             # Generated application code
```

---

## 🔄 Detailed Workflow

### Phase 1: Initial ARG Generation

**Command**: `/initial "[project description]"`

**What happens:**
1. Claude asks targeted questions about your project:
   - Project type & target audience
   - Technical stack preferences
   - Core functionalities
   - UI/UX expectations
   - Data model
   - Security & compliance
   - Performance targets

2. Claude fills the Initial ARG template with:
   - ✅ Project overview
   - ✅ Complete technical stack
   - ✅ Prioritized features (must/should/nice-to-have)
   - ✅ Data model with entities and relationships
   - ✅ Security requirements
   - ✅ Development phases
   - ✅ Deployment strategy

**Output**: `_ce/arg/initial/YYYY-MM-DD-[project-name]-initial-arg.md`

**Tips**:
- Be specific in your answers
- Add references to inspiration
- Document open questions clearly

---

### Phase 2: Initial PRP Generation + Feature Separation

**Command**: `/generate-initial-prp _ce/arg/initial/[file].md`

**What happens:**

#### Step 2.1: Research & Planning

1. **Research Phase**:
   - Searches framework documentation
   - Finds best practices for the tech stack
   - Analyzes comparable open-source projects
   - Identifies common gotchas
   - Searches deployment guides

#### Step 2.2: Feature Separation (**CRITICAL!**)

**This is the most important step to prevent the Initial PRP from becoming too large!**

2. **Feature Separation**:
   - Analyzes ALL features from the Initial ARG
   - Categorizes into **Foundation** vs **Business Features**

   **Foundation** (stays in Initial PRP):
   - ✅ Project structure
   - ✅ Database setup (basic schema)
   - ✅ Authentication & user management
   - ✅ Core API structure
   - ✅ Frontend foundation
   - ✅ CI/CD & Docker

   **Business Features** (become Feature ARGs):
   - ❌ All business logic
   - ❌ External integrations
   - ❌ Advanced UI features
   - ❌ Reporting/analytics
   - ❌ Notifications
   - ❌ etc.

3. **Generate Feature ARG Documents**:
   - For EACH business feature, a Feature ARG is created
   - Numbered sequentially (001, 002, 003, etc.)
   - Ordered by logical dependencies
   - Saved in `_ce/arg/feature/[number]-[feature-name]-feature-arg.md`

#### Step 2.3: Blueprint Creation (Foundation Only!)

4. **Initial PRP Blueprint** (ONLY foundation):
   - Task 1: Project initialization
   - Task 2: Database setup (basic schema)
   - Task 3: Authentication implementation
   - Task 4: Backend core structure
   - Task 5: Frontend setup
   - Task 6: Base UI components
   - Task 7: CI/CD pipeline
   - Task 8: Docker configuration
   - Task 9: Documentation

5. **Validation Strategy**:
   - Level 1: Linting & type checking commands
   - Level 2: Unit tests
   - Level 3: Integration tests
   - Level 4: E2E manual tests

**Outputs**:
- `_ce/prp/initial/YYYY-MM-DD-[project-name]-initial-prp.md` (foundation only!)
- `_ce/arg/feature/001-[feature]-feature-arg.md` (business feature 1)
- `_ce/arg/feature/002-[feature]-feature-arg.md` (business feature 2)
- ... (all business features separated)

**Confidence Score**: 8-10/10 for production-ready implementation

**Contains**:
```yaml
Documentation URLs:
  - Official framework docs with specific sections
  - Database/ORM guides
  - Authentication library documentation
  - Deployment platform guides

Implementation Tasks:
  - Detailed pseudocode
  - PATTERN references
  - CRITICAL notes
  - Validation commands per task

Gotchas:
  - Framework-specific quirks
  - Version compatibility issues
  - Common pitfalls
  - Security considerations
```

---

### Phase 3: Initial Setup Execution

**Command**: `/execute-initial _ce/prp/initial/[file].md`

**What happens:**
1. **Preparation**:
   - Reads entire PRP
   - Understands all tasks
   - Creates TodoWrite task list
   - Plans validation strategy

2. **Implementation** (per task):
   ```
   FOR EACH TASK:
     - Mark as in_progress
     - Read task details & PATTERNS
     - Implement following pseudocode
     - Write tests
     - Run task validation
     - Fix any issues
     - Mark as completed
   ```

3. **Progressive Validation**:
   - After backend: Lint + type check + unit tests
   - After frontend: Lint + type check + build
   - After Docker: Container build + compose up
   - Final: Full validation suite

4. **Result**:
   - ✅ Complete project structure
   - ✅ Working database with migrations
   - ✅ Functional authentication
   - ✅ API endpoints tested
   - ✅ Frontend with routing
   - ✅ UI components styled
   - ✅ CI/CD pipeline configured
   - ✅ Docker setup working
   - ✅ All tests passing (>80% coverage)
   - ✅ Documentation complete

**Duration**: Depending on project complexity (usually 15-30 minutes)

---

### Phase 4: Feature Development Cycle

#### 4.1: Feature ARG Generation

**Command**: `/generate-feature-arg "[feature description]"`

**What happens:**
1. **Context Gathering**:
   - Reads initial ARG for project context
   - Lists existing features for dependency analysis
   - Determines next feature number
   - Analyzes current codebase structure

2. **Interactive Questioning**:
   - Feature scope & goals
   - User stories & acceptance criteria
   - Technical implementation details
   - UI/UX specifications
   - API requirements
   - Database changes needed
   - Dependencies on other features
   - Testing scenarios

3. **Generates Feature ARG**:
   ```yaml
   Feature Metadata:
     - Number: 003 (auto-determined)
     - Name: Email Notifications
     - Priority: High
     - Complexity: Medium
     - Dependencies: [Feature #002]

   Technical Specs:
     - Backend components
     - Frontend components
     - API endpoints
     - Database changes
     - External integrations

   Implementation Plan:
     - Step-by-step tasks
     - Estimated time
     - Testing strategy
   ```

**Output**: `_ce/arg/feature/[number]-[name]-feature-arg.md`

---

#### 4.2: Feature PRP Generation

**Command**: `/generate-feature-prp _ce/arg/feature/[file].md`

**What happens:**
1. **Loads Context**:
   - Feature ARG
   - Initial ARG (for project stack)
   - Dependency features (if any)
   - Current codebase structure

2. **Research Phase**:
   - Framework-specific implementation patterns
   - External API/service documentation
   - Similar implementations (GitHub, blog posts)
   - Codebase pattern analysis

3. **Creates Implementation Blueprint**:
   ```yaml
   Task 1: Database Migration
     - Create migration file
     - Add new tables/columns
     - Add indexes
     - Validation: Run migration, verify schema

   Task 2: Backend Models/Schemas
     - Create SQLAlchemy models
     - Create Pydantic schemas
     - Add validation rules
     - Validation: Unit tests for models

   Task 3: Backend Business Logic
     - Implement service functions
     - Add error handling
     - Add logging
     - Validation: Unit tests for services

   Task 4: API Endpoints
     - Create router
     - Implement endpoints
     - Add authentication
     - Validation: Integration tests

   Task 5: Frontend API Client
     - Create API functions
     - Add error handling
     - Validation: Type checking

   Task 6: Frontend UI
     - Create components
     - Add validation
     - Style components
     - Validation: Component tests

   Task 7: Testing
     - Unit tests (backend)
     - Integration tests (API)
     - Component tests (frontend)
     - E2E tests (manual)

   Task 8: Documentation
     - Update README
     - Update API docs
     - Code comments
   ```

4. **Validation Strategy**:
   - Executable commands per level
   - Expected outcomes
   - Error handling guidance

**Output**: `_ce/prp/feature/[number]-[name]-feature-prp.md`

**Confidence Score**: 7-10/10 depending on feature complexity

---

#### 4.3: Feature Execution

**Command**: `/execute-feature _ce/prp/feature/[file].md`

**What happens:**
1. **Pre-flight Checks**:
   - Verify dependencies implemented
   - Check for file conflicts
   - Plan integration points

2. **Task-by-Task Implementation**:
   - Database migration → Test connection
   - Backend models → Unit tests
   - Backend logic → Unit tests
   - API endpoints → Integration tests
   - Frontend API client → Type check
   - Frontend UI → Component tests
   - Full integration → E2E tests

3. **Progressive Validation**:
   ```bash
   After each task:
     - Run task-specific validation
     - Fix issues immediately
     - Don't proceed if failing

   After backend complete:
     - Lint & type check
     - All unit tests
     - All integration tests

   After frontend complete:
     - Lint & type check
     - All component tests
     - Build succeeds

   Final:
     - Full E2E test suite
     - Performance check
     - Security review
   ```

4. **Integration with Existing Code**:
   - Preserves existing functionality
   - Follows established patterns
   - Updates related tests
   - Maintains backward compatibility

5. **Result**:
   - ✅ Feature fully implemented
   - ✅ All acceptance criteria met
   - ✅ All tests passing
   - ✅ No linting/type errors
   - ✅ Integrated with existing features
   - ✅ Documentation updated

**Duration**: Depending on feature complexity (usually 10-45 minutes per feature)

---

## 📖 Slash Commands Reference

### `/initial "[project description]"`

**Purpose**: Generate an Initial ARG document for your project idea.

**Usage**:
```bash
/initial "A task management platform for remote teams with real-time collaboration"
```

**Output**: `_ce/arg/initial/YYYY-MM-DD-[project-name]-initial-arg.md`

**Next step**: `/generate-initial-prp [generated-file]`

---

### `/generate-initial-prp [initial-arg-path]`

**Purpose**: Generate an Initial PRP with complete implementation blueprint.

**Usage**:
```bash
/generate-initial-prp _ce/arg/initial/2024-03-15-task-platform-initial-arg.md
```

**Output**: `_ce/prp/initial/YYYY-MM-DD-[project-name]-initial-prp.md`

**Next step**: `/execute-initial [generated-file]`

---

### `/execute-initial [initial-prp-path]`

**Purpose**: Implement the complete initial project setup.

**Usage**:
```bash
/execute-initial _ce/prp/initial/2024-03-15-task-platform-initial-prp.md
```

**Result**: Complete working application foundation with:
- Database & migrations
- Authentication & authorization
- Backend API
- Frontend application
- Tests
- CI/CD
- Docker setup
- Documentation

**Next step**: Start with features!

---

### `/generate-feature-arg "[feature description]"`

**Purpose**: Generate a Feature ARG for a new feature.

**Usage**:
```bash
/generate-feature-arg "Add real-time notifications using WebSockets"
```

**Output**: `_ce/arg/feature/[number]-[name]-feature-arg.md`

**Next step**: `/generate-feature-prp [generated-file]`

---

### `/generate-feature-prp [feature-arg-path]`

**Purpose**: Generate a Feature PRP with implementation blueprint.

**Usage**:
```bash
/generate-feature-prp _ce/arg/feature/003-realtime-notifications-feature-arg.md
```

**Output**: `_ce/prp/feature/003-realtime-notifications-feature-prp.md`

**Next step**: `/execute-feature [generated-file]`

---

### `/execute-feature [feature-prp-path]`

**Purpose**: Implement the feature according to the PRP.

**Usage**:
```bash
/execute-feature _ce/prp/feature/003-realtime-notifications-feature-prp.md
```

**Result**: Complete feature implementation with tests and validation.

**Next step**: Next feature!

---

## ⭐ Best Practices

### For Initial ARG
✅ **DO**:
- Be specific about requirements
- Add references to inspiration
- Think about future scalability
- Document assumptions clearly
- Prioritize features realistically

❌ **DON'T**:
- Give vague descriptions
- Want too many features at once
- Ignore security
- Skip testing strategy

### For Feature ARGs
✅ **DO**:
- Check dependencies on other features
- Think about backward compatibility
- Define clear acceptance criteria
- Plan database migrations
- Document edge cases

❌ **DON'T**:
- Build features in isolation
- Make breaking changes without migration path
- Skip API specifications
- Forget error handling

### For Execution
✅ **DO**:
- Read the complete PRP first
- Follow PATTERN references exactly
- Run validation after each task
- Fix issues immediately (don't accumulate)
- Write tests alongside implementation

❌ **DON'T**:
- Skip tasks or take shortcuts
- Continue with failing validation
- Ignore CRITICAL notes
- Ignore linting/type errors
- Write tests afterwards

### General Tips
1. **Iterate on ARGs**: Take time to make good ARGs
2. **Trust the process**: The workflow is designed for success
3. **Validate progressively**: Not just at the end
4. **Document during development**: Not afterwards
5. **Use examples**: Place good examples in `_ce/examples/`

---

## 💡 Examples

### Example 1: E-commerce Platform

```bash
# Step 1: Initial ARG
/initial "An e-commerce platform with product catalog, shopping cart, checkout, and admin panel"

# Claude asks about:
# - Payment providers (Stripe, PayPal?)
# - Inventory management
# - User roles (customer, admin, vendor?)
# - Shipping integration
# - Product categories/filtering

# Result: _ce/arg/initial/2024-03-15-ecommerce-platform-initial-arg.md

# Step 2: Generate Initial PRP
/generate-initial-prp _ce/arg/initial/2024-03-15-ecommerce-platform-initial-arg.md

# Claude researches:
# - E-commerce frameworks
# - Payment gateway integrations
# - Best practices for cart implementation
# - Security for checkout process

# Result: _ce/prp/initial/2024-03-15-ecommerce-platform-initial-prp.md

# Step 3: Execute Initial Setup
/execute-initial _ce/prp/initial/2024-03-15-ecommerce-platform-initial-prp.md

# Claude implements:
# ✅ User authentication (customer, admin roles)
# ✅ Database (products, orders, cart, users)
# ✅ Basic API endpoints
# ✅ Admin dashboard foundation
# ✅ Frontend routing
# ✅ All tests passing

# Steps 4-6: Features
/generate-feature-arg "Product catalog with search and filtering"
# → Feature #001

/generate-feature-arg "Shopping cart with session persistence"
# → Feature #002 (depends on #001)

/generate-feature-arg "Stripe checkout integration"
# → Feature #003 (depends on #002)

# Implement each:
/generate-feature-prp _ce/arg/feature/001-product-catalog-feature-arg.md
/execute-feature _ce/prp/feature/001-product-catalog-feature-prp.md

# ... repeat for #002, #003, etc.
```

---

### Example 2: SaaS Dashboard

```bash
# Initial setup for analytics dashboard
/initial "A SaaS analytics dashboard with real-time data visualization and team collaboration"

# Features might be:
# - #001: Real-time data streaming (WebSockets)
# - #002: Interactive charts (Chart.js/D3.js)
# - #003: Team workspace management
# - #004: Export reports (PDF/Excel)
# - #005: Custom dashboard builder
# - #006: Email alerts & notifications

# Each feature gets:
# - ARG document with requirements
# - PRP document with implementation
# - Validation after execution
```

---

## ❓ FAQ

### Q: Do I have to follow the entire workflow?

A: For best results: yes! But you can also:
- Only generate ARG for requirements documentation
- Use ARG + PRP without execution (as a guide)
- Go directly to feature development if foundation already exists

### Q: Can I customize the templates?

A: Absolutely! Templates are in `_ce/*/template/` and can be adapted to your needs.

### Q: What if I don't have a tech stack preference?

A: Claude will make suggestions based on your requirements. You can also ask for pros/cons of different stacks.

### Q: How long does a complete initial setup take?

A: Depending on complexity, usually 15-45 minutes for a production-ready foundation.

### Q: Can I stop midstream and continue later?

A: Yes! All state is saved in the generated documents. You can always continue where you left off.

### Q: What if the AI makes a mistake?

A: The validation loops ensure errors are detected. The AI will iterate until validation passes. If that doesn't work, you can fix manually.

### Q: Can I use existing code?

A: Yes! Place examples in `_ce/examples/` and reference them in your ARG documents.

### Q: Does this work for all programming languages?

A: The workflow works for all languages. Templates can be adapted for specific stacks (Python, TypeScript, Go, etc.).

### Q: What about deployment?

A: The initial PRP contains deployment strategy and Docker setup. Some features may also have deployment impacts.

### Q: Can I implement features in a different order?

A: As long as dependencies are respected, you can do features in any order. The numbering system is for organization, not obligation.

---

## 🎯 Next Steps

1. **Start your first project**:
   ```bash
   /initial "[your project idea]"
   ```

2. **Explore the templates**:
   - View `_ce/arg/initial/template/initial-arg-template.md`
   - View `_ce/prp/initial/template/initial-prp-template.md`

3. **Add examples**:
   - Place code examples in `_ce/examples/`
   - Reference them in your ARGs

4. **Build something awesome**! 🚀

---

## 📚 Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Context Engineering Best Practices](https://docs.anthropic.com/)
- [Project Repository](https://github.com/yourusername/context-engineering)

---

## 🤝 Contributing

Contributions are welcome! See `CONTRIBUTING.md` for details.

---

## 📄 License

[MIT License](LICENSE)

---

**Built with ❤️ using Context Engineering**

*Stop "vibe coding" - start with structured, validated development!*
