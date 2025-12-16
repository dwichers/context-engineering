# Context Engineering Workflow for Claude Code

A structured workflow system for building applications with AI assistance through comprehensive context documents.

---

## What This Repository Does

This repository provides a phased development workflow that transforms an application idea into implemented code through structured documentation:

1. **ARG Documents** (Application Requirements Generator) - Define WHAT to build
2. **PRP Documents** (Product Requirements Prompt) - Define HOW to build it
3. **Execution** - Implement following the blueprint with built-in validation

The workflow separates foundation (project setup, auth, database) from business features, making complex projects manageable.

---

## Repository Structure

```
context-engineering-claude/
├── .claude/                           # Context Engineering directory
│   │   └── commands/              # Slash commands for Claude Code
│   │       ├── initial.md         # Generate initial ARG
│   │       ├── generate-initial-prp.md
│   │       ├── generate-feature-arg.md
│   │       ├── generate-feature-prp.md
│   │       ├── execute-initial.md
│   │       ├── execute-feature.md
│   │       └── generate-claude.md # Update CLAUDE.md with project info
│   ├── arg/                       # Requirements documents
│   │   ├── initial/               # Initial project requirements
│   │   │   └── template/          # Template for initial ARG
│   │   └── feature/               # Individual feature requirements
│   │       └── template/          # Template for feature ARG
│   ├── prp/                       # Implementation blueprints
│   │   ├── initial/               # Foundation implementation guide
│   │   │   └── template/          # Template for initial PRP
│   │   └── feature/               # Feature implementation guides
│   │       └── template/          # Template for feature PRP
│   └── examples/                  # Code examples and reference patterns
├── CLAUDE.md                      # Guidelines for Claude Code
└── README.md                      # This file
```

---

## How It Works

### Phase 1: Define Requirements (ARG)

**Command**: `/initial "your app idea"`

Creates an **Initial ARG** document through interactive questions:
- Technology stack
- Core features
- Data model
- Security requirements
- Performance targets

**Output**: `.claude/arg/initial/YYYY-MM-DD-[project-name]-initial-arg.md`

---

### Phase 2: Generate Implementation Plan (PRP)

**Command**: `/generate-initial-prp .claude/arg/initial/[your-arg-file].md`

**What happens**:
1. **Research**: Gathers documentation for frameworks, libraries, deployment platforms
2. **Feature Separation**: Automatically separates business features from foundation
   - **Foundation** (stays in Initial PRP): Project structure, database, authentication, core API, base UI, CI/CD, Docker
   - **Business Features** (separate Feature ARGs): All business logic, integrations, advanced UI, reporting, admin panels
3. **Blueprint Creation**: Generates detailed implementation steps with pseudocode, patterns, and validation commands

**Outputs**:
- `.claude/prp/initial/YYYY-MM-DD-[project-name]-initial-prp.md` (foundation only)
- `.claude/arg/feature/001-[feature-name]-feature-arg.md` (for each separated business feature)
- `.claude/arg/feature/002-[feature-name]-feature-arg.md`
- etc.

---

### Phase 3: Implement Foundation

**Command**: `/execute-initial .claude/prp/initial/[your-prp-file].md`

**What happens**:
- Reads complete PRP with all context
- Implements tasks systematically (one at a time)
- Runs validation after each task
- Fixes issues immediately
- Reports completion with validation results

**Implements**:
- Project structure
- Database setup & migrations
- Authentication & authorization
- Core API structure
- Frontend foundation
- Base UI components
- CI/CD pipeline
- Docker configuration
- Documentation

**Does NOT implement**: Business features (those are in separate Feature ARGs)

---

### Phase 4: Implement Features

For each business feature (in numbered order):

**Step 1**: `/generate-feature-prp .claude/arg/feature/001-[feature-name]-feature-arg.md`
- Generates implementation blueprint for the feature
- Output: `.claude/prp/feature/001-[feature-name]-feature-prp.md`

**Step 2**: `/execute-feature .claude/prp/feature/001-[feature-name]-feature-prp.md`
- Implements the feature following the PRP
- Runs progressive validation
- Reports completion

Repeat for feature 002, 003, etc.

---

### Adding New Features Later

**Command**: `/generate-feature-arg "description of new feature"`

Creates a new Feature ARG through interactive questions, then follow Phase 4.

---

### Updating CLAUDE.md with Project Information

**Command**: `/generate-claude`

**What it does**:
- Analyzes your project structure and existing ARG/PRP documents
- Extracts technology stack, dependencies, and project-specific patterns
- Updates `CLAUDE.md` with project-specific information while preserving the generic workflow foundation
- Provides Claude Code with essential context about your specific project


---

## Key Concepts

### ARG (Application Requirements Generator)

Defines **WHAT** to build:
- Features and functionality
- User stories
- Acceptance criteria
- Data models
- API specifications
- UI requirements
- Testing strategy

### PRP (Product Requirements Prompt)

Defines **HOW** to build it:
- Complete context (documentation, examples, gotchas)
- Detailed implementation blueprint
- File-by-file instructions with pseudocode
- Validation commands
- Known issues and solutions
- Anti-patterns to avoid

### Feature Separation (Step 2.2)

**Critical concept**: During `/generate-initial-prp`, the AI automatically:
1. Analyzes ALL features from the Initial ARG
2. Identifies foundation vs business features
3. Keeps foundation in Initial PRP
4. Creates separate Feature ARG for each business feature
5. Numbers them in logical dependency order

**Why**: Prevents the Initial PRP from becoming too large, which causes the AI to forget things during implementation.

---

## Slash Commands Reference

| Command | Purpose | Input | Output |
|---------|---------|-------|--------|
| `/initial` | Start new project | Project description | Initial ARG |
| `/generate-initial-prp` | Create foundation blueprint | Initial ARG path | Initial PRP + Feature ARGs |
| `/execute-initial` | Build foundation | Initial PRP path | Working foundation |
| `/generate-feature-arg` | Define new feature | Feature description | Feature ARG |
| `/generate-feature-prp` | Create feature blueprint | Feature ARG path | Feature PRP |
| `/execute-feature` | Build feature | Feature PRP path | Working feature |
| `/generate-claude` | Update CLAUDE.md | None (auto-detects) | Updated CLAUDE.md |

---

## File Naming Conventions

```
# ARG Documents
.claude/arg/initial/2024-03-15-task-manager-initial-arg.md
.claude/arg/feature/001-user-notifications-feature-arg.md
.claude/arg/feature/002-reporting-dashboard-feature-arg.md

# PRP Documents
.claude/prp/initial/2024-03-15-task-manager-initial-prp.md
.claude/prp/feature/001-user-notifications-feature-prp.md
.claude/prp/feature/002-reporting-dashboard-feature-prp.md
```

---

## Templates

All templates are located in their respective directories:

- **Initial ARG Template**: `.claude/arg/initial/template/initial-arg-template.md`
- **Feature ARG Template**: `.claude/arg/feature/template/feature-arg-template.md`
- **Initial PRP Template**: `.claude/prp/initial/template/initial-prp-template.md`
- **Feature PRP Template**: `.claude/prp/feature/template/feature-prp-template.md`

Templates are automatically used by the slash commands - you typically don't need to reference them directly.

---

## Examples Directory

The `.claude/examples/` directory is for storing:
- Code examples you find useful
- UI component templates
- Framework boilerplates
- Design patterns
- Repository clones for reference

**Usage**: Reference examples in your ARG documents, and the AI will use them as patterns when generating PRPs.

---

## Tips

### Writing Good ARG Documents

1. **Be specific** about requirements and acceptance criteria
2. **Include examples** or links to similar features
3. **Define data relationships** clearly
4. **Specify security requirements** upfront
5. **Set realistic performance targets**

### Feature Separation

Features that should be **separated** (not in foundation):
- Business logic features
- External integrations (email, payment, notifications)
- Advanced UI features
- Reporting/analytics
- Admin panels beyond basic user management
- File upload/storage
- Search functionality
- Real-time features (WebSockets)
- Export/import features

Features that **stay in foundation**:
- Project structure
- Database setup (basic schema only)
- Authentication & authorization
- Core API structure
- Frontend routing & layout
- Basic UI components
- CI/CD pipeline
- Docker setup

### During Implementation

1. **Let the AI use TodoWrite** to track tasks
2. **Run validation** after each major step
3. **Fix issues immediately** - don't accumulate technical debt
4. **Follow patterns** from PRPs and existing code
5. **Don't skip tests** - they catch issues early
6. **Keep CLAUDE.md updated** - Run `/generate-claude` after major changes to ensure Claude Code has current project context

### Common Issues

**Issue**: PRP is too large and AI forgets things
- **Solution**: Feature separation should have caught this. Check if business features were properly separated.

**Issue**: AI doesn't follow established patterns
- **Solution**: Add examples to `.claude/examples/` and reference them in ARG documents.

**Issue**: Generated code doesn't match requirements
- **Solution**: Be more specific in ARG acceptance criteria.

---

## Workflow Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│ 1️⃣ REQUIREMENTS GATHERING                                       │
│    /initial "project description"                               │
│    → .claude/arg/initial/[date]-[name]-initial-arg.md          │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│ 2️⃣ PLANNING + FEATURE SEPARATION                                │
│    /generate-initial-prp [initial-arg-path]                     │
│                                                                  │
│    STEP 2.1: Research (docs, patterns, gotchas)                │
│                                                                  │
│    STEP 2.2: FEATURE SEPARATION ⭐                              │
│    ├─ Foundation → .claude/prp/initial/[date]-[name]-initial-prp.md│
│    └─ Business Features → .claude/arg/feature/001-[feature]-feature-arg.md│
│                                                                  │
│    OUTPUTS:                                                      │
│    → .claude/prp/initial/[date]-[name]-initial-prp.md          │
│    → .claude/arg/feature/001-[feature]-feature-arg.md           │
│    → .claude/arg/feature/002-[feature]-feature-arg.md           │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│ 3️⃣ FOUNDATION IMPLEMENTATION                                    │
│    /execute-initial [initial-prp-path]                          │
│    → Working foundation (auth, DB, core API, base UI, CI/CD)   │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│ 4️⃣ FEATURE IMPLEMENTATION (repeat for each feature)             │
│    /generate-feature-prp [feature-arg-path]                     │
│    → .claude/prp/feature/[number]-[feature]-feature-prp.md      │
│                                                                  │
│    /execute-feature [feature-prp-path]                          │
│    → Working feature                                            │
└─────────────────────────────────────────────────────────────────┘
```

---

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI
- Git repository

---

## License

This workflow system is provided as-is for use with Claude Code.
