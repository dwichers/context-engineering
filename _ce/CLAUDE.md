# Claude Code Workflow Guidelines

## 🔄 Context Engineering Workflow

This repository uses a structured Context Engineering workflow for building applications through comprehensive context documents.

### Workflow Structure
- **`arg/`** - Application Requirements Generator documents (WHAT to build)
  - `arg/initial/` - Initial project requirements
  - `arg/feature/` - Individual feature requirements
- **`prp/`** - Product Requirements Prompts (HOW to build)
  - `prp/initial/` - Foundation implementation blueprints
  - `prp/feature/` - Feature implementation blueprints
- **`examples/`** - Code examples, UI components, reference patterns
- **`.claude/commands/`** - Workflow slash commands

### Workflow Commands

**Initial Project Setup**:
1. `/initial [description]` - Generate Initial ARG
2. `/generate-initial-prp [arg-path]` - Generate Initial PRP + Separate Business Features
3. `/execute-initial [prp-path]` - Implement foundation only

**Feature Development**:
1. `/generate-feature-arg [description]` - Generate Feature ARG
2. `/generate-feature-prp [arg-path]` - Generate Feature PRP
3. `/execute-feature [prp-path]` - Implement feature

---

## 🎯 Critical Concept: Feature Separation

**During `/generate-initial-prp` (Step 2.2)**, the system automatically:
1. Analyzes ALL features from Initial ARG
2. Identifies **Foundation** vs **Business Features**
3. Keeps foundation in Initial PRP (auth, DB, core API, base UI, CI/CD, Docker)
4. Creates separate Feature ARG for each business feature
5. Numbers them in logical dependency order

**Why**: Prevents Initial PRP from becoming too large, which causes implementation issues.

**Foundation Features** (stay in Initial PRP):
- Project structure
- Database setup (basic schema only)
- Authentication & authorization
- Core API structure
- Frontend routing & layout
- Base UI components
- CI/CD pipeline
- Docker setup

**Business Features** (separate Feature ARGs):
- All business logic features
- External integrations (email, payment, notifications)
- Advanced UI features
- Reporting/analytics
- Admin panels beyond basic user management
- File upload/storage
- Search functionality
- Real-time features (WebSockets)
- Export/import features

---

## ✅ Working with PRPs (Execute Commands)

### Before Starting
1. **Read entire PRP** before implementing
2. **Check dependencies** - verify required features are implemented
3. **Review affected files** - understand what to create/modify

### During Implementation
1. **Use TodoWrite** to track tasks from PRP
2. **Only ONE task in_progress** at a time
3. **Follow PATTERN references** from PRP exactly
4. **Heed all CRITICAL notes** in PRP
5. **Use pseudocode** as implementation guide
6. **Write tests** alongside implementation
7. **Run validation** after each task
8. **Fix issues immediately** - don't accumulate technical debt
9. **Mark completed** immediately after validation passes

### Validation Gates
PRPs specify 4 validation levels - run all before marking complete:
1. **Syntax & Style** - Linting, type checking (0 errors)
2. **Unit Tests** - All tests pass, >80% coverage for new code
3. **Integration Tests** - API endpoints, database operations work
4. **E2E Tests** - Complete user flows work

### Don't Skip
- ❌ Don't skip reading full PRP
- ❌ Don't skip dependency checks
- ❌ Don't ignore CRITICAL notes
- ❌ Don't skip error handling
- ❌ Don't skip writing tests
- ❌ Don't move forward with failing validation
- ❌ Don't mark complete without ALL validation passing

---

## 🔄 Integration with Existing Code

When modifying existing files:
- **PRESERVE existing functionality** unless explicitly changing it
- **Follow existing code style** and patterns
- **Check `examples/`** for reference implementations
- **Maintain backward compatibility** when possible
- **Update related tests** when changing functionality

---

## 📋 Task Management

- **Mark only ONE task as in_progress** at a time
- **Complete tasks fully** before moving to next (run validation, fix issues)
- **Mark completed immediately** after validation passes
- Don't batch completions - update in real-time

---

## 🧠 AI Behavior Rules

### General
- Never assume missing context - ask questions if uncertain
- Never hallucinate libraries or functions - only use verified packages
- Always confirm file paths exist before referencing
- Never delete or overwrite existing code unless explicitly instructed

### When Implementing from PRPs
- Read the entire PRP before starting (don't skim)
- Follow established patterns from codebase and PRP
- Run all validation gates as specified
- Iterate until validation passes - don't compromise on quality

### When Research is Needed
- Search official documentation for frameworks/libraries
- Look for established patterns in the codebase
- Check `examples/` for reference implementations
- Ask for clarification if requirements are ambiguous

---

## 🎯 Remember

**Context Engineering Principle**: Provide COMPLETE context for one-pass implementation success.

- **ARGs** define WHAT to build (requirements, acceptance criteria)
- **PRPs** define HOW to build it (context, blueprints, validation)
- **Execution** follows the blueprint with validation at every step

The workflow separates foundation from features to keep context manageable and implementation successful.
