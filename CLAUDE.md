# Claude Code Global Guidelines

## 🔄 Context Engineering Workflow Awareness

**IMPORTANT**: This repository uses a structured Context Engineering workflow for building applications.

### Workflow Structure
- **`_ce/`** - Main Context Engineering directory containing all workflow files
  - **`_ce/arg/`** - Application Requirements Generator documents
    - `_ce/arg/initial/` - Initial project setup requirements
    - `_ce/arg/feature/` - Individual feature requirements
  - **`_ce/prp/`** - Product Requirements Prompts (implementation blueprints)
    - `_ce/prp/initial/` - Initial setup implementation guides
    - `_ce/prp/feature/` - Feature implementation guides
  - **`_ce/examples/`** - Code examples, UI components, templates for reference
  - **`_ce/.claude/commands/`** - Custom slash commands for the workflow

### Available Workflow Commands

**Initial Project Setup**:
1. `/initial "[project description]"` - Generate Initial ARG document
2. `/generate-initial-prp [initial-arg-path]` - Generate Initial PRP
3. `/execute-initial [initial-prp-path]` - Implement initial setup

**Feature Development**:
1. `/generate-feature-arg "[feature description]"` - Generate Feature ARG
2. `/generate-feature-prp [feature-arg-path]` - Generate Feature PRP
3. `/execute-feature [feature-prp-path]` - Implement feature

### When to Use This Workflow

- **Starting a new project**: Use `/initial` to structure your idea
- **Adding features**: Use `/generate-feature-arg` for each new feature
- **Need implementation guidance**: Generate PRPs before coding
- **Want structured, validated implementation**: Execute PRPs with built-in validation

---

## 🔄 Project Awareness & Context

- **Check for ARG documents** in `_ce/arg/` to understand project requirements
- **Check for PRP documents** in `_ce/prp/` for implementation guidelines
- **Check for existing features** in `_ce/arg/feature/` to understand dependencies
- **Use examples** from `_ce/examples/` as reference patterns
- **Follow patterns** established in existing code and documented in PRPs

---

## 🧱 Code Structure & Modularity

- **Never create a file longer than 500 lines of code.** If a file approaches this limit, refactor by splitting it into modules or helper files.
- **Organize code into clearly separated modules**, grouped by feature or responsibility:
  - For backend APIs:
    - `models/` - Database models
    - `schemas/` - Pydantic validation schemas
    - `services/` - Business logic
    - `api/` - API endpoints/routes
    - `core/` - Core functionality (config, security, database)
  - For agents/AI features:
    - `agent.py` - Main agent definition and execution logic
    - `tools.py` - Tool functions used by the agent
    - `prompts.py` - System prompts
- **Use clear, consistent imports** (prefer absolute imports for clarity)
- **Use environment variables** for configuration (with `python-dotenv` and `load_dotenv()`)

---

## 🧪 Testing & Reliability

- **Always create tests for new features** (functions, classes, routes, etc.)
- **After updating any logic**, check whether existing tests need updating
- **Tests should live in a `/tests` folder** mirroring the main app structure
- **Test coverage target**: Minimum 80% for new code
- Include at least:
  - 1 test for expected/happy path use
  - 1 edge case test
  - 1 failure/error case test

### Test Structure Example
```
tests/
├── unit/
│   ├── test_models.py
│   ├── test_services.py
│   └── test_utils.py
├── integration/
│   ├── test_api.py
│   └── test_auth.py
└── conftest.py
```

---

## ✅ Task Management & Completion

### When Using PRPs
- **Use TodoWrite tool** to track PRP implementation tasks
- **Mark only ONE task as in_progress** at a time
- **Complete tasks fully** before moving to next
- **Run validation** after each task
- **Mark completed immediately** after validation passes

### General Task Tracking
- Document discovered sub-tasks as you work
- Update task status in real-time
- Keep tasks specific and actionable

---

## 📎 Style & Conventions

### General
- **Language preference**: Match the project's tech stack (Python, TypeScript, etc.)
- **Code formatting**: Use project's formatter (Black, Prettier, etc.)
- **Type hints**: Always use type hints/annotations
- **Validation**: Use Pydantic for data validation

### Python Specific
- **Follow PEP8**
- **Use `black` for formatting**
- **Use `ruff` for linting**
- **Use `mypy` for type checking**
- Use `FastAPI` for APIs
- Use `SQLAlchemy` or `SQLModel` for ORM
- Write **docstrings for every function** using Google style:
  ```python
  def example(param1: str, param2: int) -> dict:
      """
      Brief summary of what the function does.

      Args:
          param1: Description of param1
          param2: Description of param2

      Returns:
          Description of return value

      Raises:
          ValueError: When validation fails
      """
  ```

### TypeScript/JavaScript Specific
- **Use TypeScript** for type safety
- **Use ESLint** for linting
- **Use Prettier** for formatting
- **Document complex functions** with JSDoc comments
- Use **async/await** for asynchronous operations

---

## 📚 Documentation & Explainability

- **Update `README.md`** when:
  - New features are added
  - Dependencies change
  - Setup steps are modified
  - Project structure changes
- **Comment non-obvious code** - make it understandable to a mid-level developer
- **Add inline `# Reason:` comments** for complex logic explaining the why, not just the what
- **Update API documentation** (Swagger/OpenAPI) when adding/modifying endpoints
- **Document environment variables** in `.env.example`

---

## 🔒 Security Best Practices

- **Never commit sensitive data** (.env files, API keys, credentials)
- **Use environment variables** for secrets
- **Hash passwords** (bcrypt, argon2)
- **Validate all user inputs** (Pydantic schemas, zod, etc.)
- **Implement authentication** for protected routes
- **Check authorization** for user actions
- **Prevent SQL injection** (use ORM properly, parameterized queries)
- **Prevent XSS** (sanitize inputs, escape outputs)
- **Enable CORS** only for trusted origins

---

## ⚡ Performance Considerations

- **Database indexing**: Index frequently queried columns
- **Avoid N+1 queries**: Use eager loading, joins, or select_related
- **Implement pagination**: For lists that can grow large
- **Use caching**: For expensive or frequent operations
- **Optimize database queries**: Use query profiling
- **Lazy load where appropriate**: For frontend components
- **Connection pooling**: For database connections

---

## 🧠 AI Behavior Rules

### General Guidelines
- **Never assume missing context** - Ask questions if uncertain
- **Never hallucinate libraries or functions** - Only use known, verified packages
- **Always confirm file paths** exist before referencing them
- **Never delete or overwrite existing code** unless explicitly instructed
- **Follow established patterns** from the codebase and PRPs

### When Implementing from PRPs
- **Read the entire PRP** before starting implementation
- **Follow PATTERN references** exactly
- **Heed all CRITICAL notes** in the PRP
- **Use provided pseudocode** as implementation guide
- **Run validation gates** as specified
- **Don't skip error handling** even if not explicitly in PRP
- **Iterate until validation passes** - don't compromise on quality

### When Research is Needed
- **Search official documentation** for frameworks/libraries
- **Look for established patterns** in the codebase
- **Check `_ce/examples/`** for reference implementations
- **Document findings** for future reference
- **Ask for clarification** if requirements are ambiguous

---

## 🔄 Integration with Existing Code

When modifying existing code:
- **PRESERVE existing functionality** unless explicitly changing it
- **Follow existing code style** and patterns
- **Update related tests** when changing functionality
- **Check for breaking changes** and plan migration if needed
- **Maintain backward compatibility** when possible
- **Document breaking changes** clearly

---

## 📊 Validation & Quality Gates

### Before Committing Code
- [ ] Code follows style guidelines
- [ ] All linting passes (no errors)
- [ ] All type checking passes (no errors)
- [ ] All tests pass
- [ ] Code coverage meets target (>80% for new code)
- [ ] No security vulnerabilities introduced
- [ ] Documentation updated
- [ ] Environment variables documented

### Progressive Validation (when using PRPs)
1. **After each task**: Run task-specific validation
2. **After each component**: Run component-level tests
3. **After integration**: Run integration tests
4. **Before marking complete**: Run full validation suite

---

## 🎯 Remember

> **Context Engineering is about providing COMPLETE context for successful implementation.**
>
> - ARGs define WHAT to build
> - PRPs define HOW to build it
> - Execution follows the blueprint with validation at every step
>
> The result: **One-pass implementation success through comprehensive context.**

---

**Last Updated**: [Auto-updated by workflow]
