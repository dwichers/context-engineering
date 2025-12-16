# Execute Initial PRP

Implement the complete initial project setup according to the Initial PRP document.

## PRP File: $ARGUMENTS

This must be the path to the initial PRP document: `_ce/prp/initial/[filename].md`

---

## Execution Process

### Step 1: Load PRP & Preparation

1. **Read the PRP document**:
   ```bash
   Read $ARGUMENTS
   ```

2. **Understand all context**:
   - Read all documentation references
   - Understand technology stack
   - Review all implementation tasks
   - Note validation gates
   - Check for gotchas

3. **Verify prerequisites**:
   - Check if required tools installed (Node, Python, Docker, etc.)
   - Verify environment setup
   - Confirm no conflicting files exist

### Step 2: ULTRATHINK & Planning

**CRITICAL**: Think deeply before starting implementation.

1. **Analyze the implementation blueprint**:
   - Understand dependencies between tasks
   - Identify critical path
   - Note parallel vs sequential tasks

2. **Create comprehensive task list** using TodoWrite:
   ```
   - Task 1: Project Initialization
   - Task 2: Database Setup
   - Task 3: Authentication Implementation
   - Task 4: Backend Core Structure
   - Task 5: Frontend Setup
   - Task 6: Base UI Components
   - Task 7: CI/CD Pipeline
   - Task 8: Docker Configuration
   - Task 9: Documentation
   - Task 10: Final Validation
   ```

3. **Identify potential issues**:
   - Version compatibility concerns?
   - Configuration complexity?
   - Integration challenges?

4. **Plan validation strategy**:
   - When to run syntax checks?
   - When to run tests?
   - Integration test timing?

### Step 3: Execute Implementation

**Work through each task systematically**:

#### For Each Task:

1. **Mark task as in_progress** (IMPORTANT: Only ONE task in_progress at a time)

2. **Read task details from PRP**:
   - Understand goal
   - Review steps
   - Check PATTERN references
   - Note CRITICAL items

3. **Implement the task**:
   - Create/modify files as specified
   - Follow patterns from PRP
   - Add error handling
   - Add logging where appropriate

4. **Add inline documentation**:
   - Docstrings for functions/classes
   - Comments for complex logic
   - Type hints/annotations

5. **Run task-level validation** (from PRP):
   ```bash
   # Example validation from PRP
   python -c "from src.core.database import engine; engine.connect()"
   ```

6. **Fix any issues immediately**:
   - Don't move to next task with failing validation
   - Iterate until task validation passes

7. **Mark task as completed** IMMEDIATELY after success

8. **Move to next task**

#### Specific Implementation Guidelines:

**Project Initialization (Task 1)**:
- Create directory structure EXACTLY as specified in PRP
- Initialize package managers (npm, poetry, pip)
- Create configuration files
- Setup .env.example
- Initialize git if needed

**Database Setup (Task 2)**:
- Configure database connection (using params from PRP)
- Setup ORM/migration tool
- Create models as specified
- Run initial migration
- Verify connection works

**Authentication (Task 3)**:
- Implement password hashing (bcrypt/argon2)
- Create JWT token generation/validation
- Implement auth endpoints (register, login, refresh)
- Add auth middleware/dependencies
- Test auth flow manually

**Backend Core (Task 4)**:
- Setup FastAPI/Express/etc app
- Configure CORS
- Add error handling middleware
- Setup logging
- Create health check endpoint

**Frontend Setup (Task 5)**:
- Initialize React/Vue/Next project
- Configure routing
- Setup API client
- Configure state management (if needed)
- Setup build tools

**Base UI Components (Task 6)**:
- Create layout components
- Implement auth pages (login, register)
- Add error/loading states
- Style with CSS framework
- Test responsive design

**CI/CD Pipeline (Task 7)**:
- Create GitHub Actions / GitLab CI config
- Setup linting jobs
- Setup test jobs
- Setup build jobs
- Test workflow locally if possible

**Docker Configuration (Task 8)**:
- Create Dockerfiles
- Create docker-compose.yml
- Configure volumes
- Test containers build
- Test containers run

**Documentation (Task 9)**:
- Write comprehensive README
- Document environment variables
- Add setup instructions
- Document architecture
- Create deployment guide

### Step 4: Progressive Validation

**Run validation after EACH major component**:

**After Backend Foundation**:
```bash
cd backend
ruff check . --fix
mypy .
pytest tests/unit -v
python src/main.py --help  # Verify it runs
```

**After Frontend Setup**:
```bash
cd frontend
npm run lint
npm run type-check
npm run build  # Verify build works
```

**After Docker Setup**:
```bash
docker-compose build
docker-compose up -d
docker-compose ps  # Check all services running
```

### Step 5: Comprehensive Testing

**Level 1: Syntax & Style** (from PRP validation loop)
```bash
# Run ALL linting and type checking
[Execute commands from PRP Level 1]
# CRITICAL: Fix all errors before proceeding
```

**Level 2: Unit Tests** (from PRP validation loop)
```bash
# Run ALL unit tests
[Execute commands from PRP Level 2]
# Target: > 80% coverage
# CRITICAL: All tests must pass
```

**Level 3: Integration Tests** (from PRP validation loop)
```bash
# Start all services
docker-compose up -d

# Run integration test commands from PRP
[Execute manual tests from PRP Level 3]

# Example:
curl http://localhost:8000/api/v1/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email": "test@example.com", "password": "Test123!"}'

# Verify response is 201 Created
```

**Level 4: E2E Manual Testing**:
```bash
# Open browser
# Navigate to http://localhost:3000
# Test complete user flow:
# 1. Register new user - should succeed
# 2. Login with user - should get token
# 3. Access protected page - should work
# 4. Logout - should redirect to login
# 5. Try to access protected page - should redirect
```

### Step 6: Fix Issues & Iterate

**If validation fails at any level**:

1. **Read the error carefully**:
   - Understand root cause
   - Check PRP for gotchas related to this error

2. **Fix the issue**:
   - Don't band-aid - fix properly
   - Follow patterns from PRP
   - Maintain code quality

3. **Re-run validation**:
   - Run same validation again
   - Verify fix worked
   - Check for side effects

4. **Iterate until all pass**:
   - Don't skip failing tests
   - Don't ignore linting errors
   - Don't proceed with broken code

### Step 7: Final Validation Checklist

Go through PRP's final validation checklist:

```bash
# From PRP Final Validation Checklist
[ ] Directory structure matches specification
[ ] Git repository initialized
[ ] .gitignore configured
[ ] .env.example complete
[ ] Backend server starts
[ ] Database connection works
[ ] Migrations run successfully
[ ] Authentication endpoints work
[ ] Protected routes require auth
[ ] All backend tests pass
[ ] No linting errors (backend)
[ ] No type errors (backend)
[ ] Frontend builds successfully
[ ] Dev server runs
[ ] Routing works
[ ] API client configured
[ ] Auth flow works (register/login/logout)
[ ] All frontend tests pass
[ ] No linting errors (frontend)
[ ] No type errors (frontend)
[ ] Docker containers build
[ ] docker-compose starts services
[ ] CI/CD workflow runs successfully
[ ] README is comprehensive
[ ] All environment variables documented
[ ] Security measures in place
```

**CRITICAL**: ALL items must be checked before marking as complete.

### Step 8: Review PRP Again

**Re-read the PRP document** to ensure nothing was missed:
- Check all tasks completed
- Verify all files created
- Confirm all patterns followed
- Validate all success criteria met

### Step 9: Completion Report

Generate comprehensive completion report:

```
✅ Initial Project Setup Complete!

Implementation Summary:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📦 Project Structure
- Backend: [framework] with [database]
- Frontend: [framework] with [styling]
- Infrastructure: Docker + [CI/CD platform]

✅ Completed Tasks:
1. ✓ Project initialization
2. ✓ Database setup & migrations
3. ✓ Authentication & authorization
4. ✓ Backend core structure
5. ✓ Frontend setup & routing
6. ✓ Base UI components
7. ✓ CI/CD pipeline
8. ✓ Docker configuration
9. ✓ Documentation

📊 Validation Results:
- Linting: ✅ Pass (0 errors)
- Type Checking: ✅ Pass (0 errors)
- Unit Tests: ✅ Pass ([X]/[X] tests, [Y]% coverage)
- Integration Tests: ✅ Pass (all endpoints working)
- E2E Tests: ✅ Pass (complete user flow verified)

🔐 Security:
- ✅ Password hashing implemented
- ✅ JWT authentication working
- ✅ CORS configured
- ✅ Input validation in place
- ✅ Environment variables secured

📁 Generated Files:
[List all created files organized by category]

🚀 How to Run:

Development mode:
$ docker-compose up -d
$ open http://localhost:3000

Testing:
$ cd backend && pytest tests/ -v
$ cd frontend && npm test

🎯 Next Steps:

The foundation is ready! You can now implement features.

Recommended order:
1. Review _ce/arg/feature/ for available features
2. Or create new feature: /generate-feature-arg "[description]"
3. Generate feature PRP: /generate-feature-prp _ce/arg/feature/[file].md
4. Implement feature: /execute-feature _ce/prp/feature/[file].md

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Important Guidelines

### DO:
- ✅ Read PRP completely before starting
- ✅ Use TodoWrite to track all tasks
- ✅ Mark only ONE task as in_progress at a time
- ✅ Complete tasks fully before moving to next
- ✅ Run validation after each task
- ✅ Fix all issues immediately
- ✅ Follow all PATTERNS from PRP
- ✅ Heed all CRITICAL notes
- ✅ Write tests as you implement
- ✅ Document complex logic
- ✅ Validate progressively, not just at end
- ✅ Re-read PRP before marking complete

### DON'T:
- ❌ Skip tasks or take shortcuts
- ❌ Move to next task with failing validation
- ❌ Ignore linting or type errors
- ❌ Skip writing tests
- ❌ Forget error handling
- ❌ Miss security implementations
- ❌ Skip documentation
- ❌ Ignore CRITICAL notes in PRP
- ❌ Deviate from specified patterns
- ❌ Mark task complete before validation passes
- ❌ Skip final checklist review

---

## Error Handling Strategy

### When Build Fails:
1. Read error message completely
2. Check PRP for related gotchas
3. Search documentation for error
4. Fix root cause (not symptoms)
5. Re-run build
6. Verify fix worked

### When Tests Fail:
1. Understand what test is checking
2. Debug why it's failing
3. Fix implementation (not test)
4. Verify test passes
5. Check for side effects

### When Integration Fails:
1. Test components individually first
2. Verify each service running
3. Check network connectivity
4. Verify configuration
5. Check logs for errors
6. Fix and re-test

---

## Success Criteria

The /execute-initial command is successful when:

1. ✅ ALL tasks from PRP completed
2. ✅ ALL validation gates pass
3. ✅ ALL tests pass (>80% coverage)
4. ✅ NO linting or type errors
5. ✅ Application runs in Docker
6. ✅ Complete user flow works (register → login → use → logout)
7. ✅ CI/CD pipeline successful
8. ✅ Documentation complete
9. ✅ Final validation checklist 100% checked
10. ✅ PRP re-read and verified complete

---

**Remember**: The initial setup is the foundation. Take time to do it right - it will save time later!
