# Initial Project Setup - Product Requirements Prompt (PRP)

**Generated from**: `$ARGUMENTS`
**Generated on**: [Date]
**Project Name**: [Name from ARG document]

---

## 🎯 Purpose

Dit PRP document beschrijft **ALLEEN** de project foundation setup. Business features zijn gescheiden in aparte Feature ARG documenten.

**Foundation Scope** (ONLY these in this PRP):
- ✅ Project structuur en configuratie
- ✅ Development environment setup
- ✅ Database setup met BASIC schema (users, auth tables only)
- ✅ Authentication & Authorization (user registration, login, roles)
- ✅ Core API structure (routing, middleware, error handling)
- ✅ Frontend foundation (routing, layout, basic UI components)
- ✅ CI/CD pipeline
- ✅ Docker configuratie
- ✅ Documentation structure

**NOT in Foundation** (These are separate features):
- ❌ Business logic features
- ❌ Advanced UI features
- ❌ External integrations (email, payment, notifications)
- ❌ Reporting/analytics
- ❌ Admin panels beyond basic user management
- ❌ File upload/storage
- ❌ Search functionality
- ❌ Real-time features

**Separated Features**: [List will be added during generation]

## Core Principles

1. **Context is King**: Alle nodige documentatie, voorbeelden en caveats zijn meegenomen
2. **Validation Loops**: Executable tests/lints voor self-validation
3. **Information Dense**: Keywords en patterns uit de codebase en ARG
4. **Progressive Success**: Start simpel, valideer, dan enhance
5. **Global Rules**: Volg alle regels in CLAUDE.md

---

## 📋 Project Overview

### Project Name & Description
[Haal uit ARG document]

### Technology Stack

#### Frontend
- **Framework**: [uit ARG]
- **Styling**: [uit ARG]
- **State Management**: [uit ARG]
- **UI Components**: [uit ARG]
- **Build Tool**: [uit ARG]

#### Backend
- **Framework**: [uit ARG]
- **Database**: [uit ARG]
- **ORM**: [uit ARG]
- **Authentication**: [uit ARG]
- **API Type**: [uit ARG]

#### Infrastructure
- **Frontend Hosting**: [uit ARG]
- **Backend Hosting**: [uit ARG]
- **CI/CD**: [uit ARG]
- **Containerization**: [uit ARG]

---

## 📚 All Needed Context

### Documentation & References

```yaml
# Framework Documentation
- url: [Link naar main framework docs]
  why: Setup guides, best practices, project structure
  critical: [Belangrijke secties om te lezen]

- url: [Link naar database/ORM docs]
  why: Schema design, migrations, queries
  critical: [Belangrijke secties]

- url: [Link naar authentication library docs]
  why: Setup, configuration, best practices
  critical: [Security considerations]

# Deployment & Infrastructure
- url: [Link naar hosting platform docs]
  why: Deployment configuration, environment setup
  critical: [Deployment strategies]

# UI/UX Resources
- url: [Link naar component library docs]
  why: Component usage, theming, customization
  critical: [Setup and configuration]

- url: [Link naar design system indien van toepassing]
  why: Design patterns, color schemes, typography

# Examples from Codebase
- file: _ce/examples/[relevant-example-1]
  why: [Pattern om te volgen - bijvoorbeeld: project structure]

- file: _ce/examples/[relevant-example-2]
  why: [Pattern om te volgen - bijvoorbeeld: authentication setup]
```

### Known Gotchas & Library Quirks

```python
# CRITICAL: [Framework naam] requires [specific setup]
# CRITICAL: [Database] migrations must be run in order
# CRITICAL: [Auth library] requires environment variables set before import
# CRITICAL: [Deployment platform] needs specific build commands
# CRITICAL: [Styling framework] requires PostCSS configuration
# GOTCHA: [Specific version compatibility issue]
# GOTCHA: [Common pitfall met dit framework]
```

---

## 🏗️ Project Structure

### Desired Directory Structure

```bash
project-root/
├── .github/
│   └── workflows/
│       └── ci.yml                    # CI/CD pipeline
├── frontend/                          # Frontend application
│   ├── src/
│   │   ├── components/               # React/Vue/etc components
│   │   │   ├── ui/                   # Base UI components
│   │   │   ├── layout/               # Layout components
│   │   │   └── features/             # Feature-specific components
│   │   ├── pages/                    # Page components/routes
│   │   ├── hooks/                    # Custom hooks
│   │   ├── lib/                      # Utilities and helpers
│   │   ├── styles/                   # Global styles
│   │   ├── types/                    # TypeScript types
│   │   ├── api/                      # API client
│   │   ├── store/                    # State management
│   │   └── main.tsx                  # Entry point
│   ├── public/                       # Static assets
│   ├── tests/                        # Frontend tests
│   ├── package.json
│   ├── vite.config.ts               # Build configuration
│   ├── tailwind.config.js           # Styling configuration
│   └── tsconfig.json                # TypeScript configuration
├── backend/                          # Backend application
│   ├── src/
│   │   ├── api/                     # API routes/endpoints
│   │   │   ├── v1/                  # API version 1
│   │   │   └── deps.py              # Dependencies injection
│   │   ├── core/                    # Core functionality
│   │   │   ├── config.py            # Configuration
│   │   │   ├── security.py          # Security utilities
│   │   │   └── database.py          # Database setup
│   │   ├── models/                  # Database models
│   │   ├── schemas/                 # Pydantic schemas
│   │   ├── services/                # Business logic
│   │   ├── repositories/            # Data access layer
│   │   └── main.py                  # Application entry point
│   ├── tests/                       # Backend tests
│   │   ├── unit/
│   │   ├── integration/
│   │   └── conftest.py
│   ├── alembic/                     # Database migrations
│   │   └── versions/
│   ├── requirements.txt             # Python dependencies
│   └── pyproject.toml               # Project configuration
├── _ce/                             # Context Engineering directory
│   ├── .claude/
│   ├── arg/
│   ├── prp/
│   └── examples/
├── docker/
│   ├── Dockerfile.frontend
│   ├── Dockerfile.backend
│   └── docker-compose.yml
├── .env.example                     # Environment variables template
├── .gitignore
├── CLAUDE.md                        # AI coding guidelines
└── README.md                        # Project documentation
```

---

## 🔧 Implementation Blueprint

### Task 1: Project Initialization & Configuration

**Goal**: Setup basic project structure and configuration files

**Steps**:
1. Create project directory structure
2. Initialize frontend project with [framework]
3. Initialize backend project with [framework]
4. Setup Git repository and .gitignore
5. Create .env.example with required variables

**Files to Create**:
```yaml
CREATE frontend/package.json:
  - PATTERN: Standard [framework] setup
  - Dependencies: [list key dependencies]
  - Scripts: dev, build, test, lint

CREATE backend/requirements.txt:
  - PATTERN: Python project dependencies
  - Include: [framework], [ORM], [auth library], etc.

CREATE .env.example:
  - Frontend variables: VITE_API_URL, etc.
  - Backend variables: DATABASE_URL, SECRET_KEY, etc.
  - Document each variable purpose

CREATE .gitignore:
  - PATTERN: Standard [language/framework] gitignore
  - Ignore: node_modules/, __pycache__/, .env, etc.

CREATE docker-compose.yml:
  - Services: database, backend, frontend
  - PATTERN: Development environment setup
```

**Validation**:
```bash
# Verify structure created
tree -L 2

# Verify frontend runs
cd frontend && npm install && npm run dev

# Verify backend runs
cd backend && pip install -r requirements.txt && python src/main.py
```

---

### Task 2: Database Setup & Configuration

**Goal**: Setup database, ORM, and initial schema

**Steps**:
1. Configure database connection
2. Setup ORM (SQLAlchemy/Prisma/etc.)
3. Create base models
4. Setup migration system
5. Create initial migration

**Files to Create**:
```yaml
CREATE backend/src/core/database.py:
  - PATTERN: Database connection management
  - Setup connection pooling
  - Session management

  PSEUDOCODE:
    from sqlalchemy import create_engine
    from sqlalchemy.orm import sessionmaker

    # CRITICAL: Use connection pooling for production
    engine = create_engine(
        settings.DATABASE_URL,
        pool_pre_ping=True,  # GOTCHA: Prevents stale connections
        pool_size=10,
        max_overflow=20
    )

    SessionLocal = sessionmaker(...)

    def get_db():
        # Dependency injection pattern
        db = SessionLocal()
        try:
            yield db
        finally:
            db.close()

CREATE backend/src/models/__init__.py:
  - Base model with common fields
  - Timestamp mixin

CREATE backend/src/models/user.py:
  - User model based on ARG data model
  - FIELDS: [list from ARG]
  - RELATIONSHIPS: [list from ARG]

  PSEUDOCODE:
    class User(Base):
        __tablename__ = "users"

        id: UUID = Column(UUID(as_uuid=True), primary_key=True)
        email: str = Column(String, unique=True, index=True)
        hashed_password: str = Column(String)
        # ... other fields from ARG

        # PATTERN: Soft delete instead of hard delete
        is_active: bool = Column(Boolean, default=True)
        deleted_at: Optional[datetime] = Column(DateTime, nullable=True)

SETUP alembic/:
  - Initialize Alembic
  - Configure alembic.ini
  - Create initial migration
```

**Validation**:
```bash
# Test database connection
python -c "from src.core.database import engine; engine.connect()"

# Run migrations
alembic upgrade head

# Verify tables created
psql $DATABASE_URL -c "\dt"
```

---

### Task 3: Authentication & Authorization Setup

**Goal**: Implement user authentication and authorization system

**Steps**:
1. Setup password hashing
2. Implement JWT token generation
3. Create authentication endpoints
4. Setup authorization middleware
5. Create user registration/login flows

**Files to Create**:
```yaml
CREATE backend/src/core/security.py:
  - Password hashing (bcrypt/argon2)
  - JWT token creation/validation
  - Permission checking utilities

  PSEUDOCODE:
    from passlib.context import CryptContext
    from jose import JWTError, jwt

    pwd_context = CryptContext(schemes=["bcrypt"])

    def verify_password(plain: str, hashed: str) -> bool:
        return pwd_context.verify(plain, hashed)

    def create_access_token(data: dict) -> str:
        # CRITICAL: Set expiration time
        expire = datetime.utcnow() + timedelta(minutes=30)
        to_encode = {**data, "exp": expire}
        return jwt.encode(to_encode, SECRET_KEY, algorithm="HS256")

CREATE backend/src/schemas/auth.py:
  - UserCreate schema
  - UserLogin schema
  - Token schema
  - PATTERN: Pydantic validation

CREATE backend/src/api/v1/auth.py:
  - POST /auth/register
  - POST /auth/login
  - POST /auth/refresh
  - GET /auth/me (get current user)

  PSEUDOCODE:
    @router.post("/register", response_model=UserResponse)
    async def register(user_data: UserCreate, db: Session = Depends(get_db)):
        # CRITICAL: Check if user exists
        if await user_exists(user_data.email):
            raise HTTPException(409, "User already exists")

        # CRITICAL: Hash password
        hashed_password = hash_password(user_data.password)

        # Create user
        user = create_user(db, user_data, hashed_password)

        return user

CREATE backend/src/api/deps.py:
  - get_current_user dependency
  - require_role dependency

  PSEUDOCODE:
    async def get_current_user(
        token: str = Depends(oauth2_scheme),
        db: Session = Depends(get_db)
    ) -> User:
        # CRITICAL: Validate token
        payload = jwt.decode(token, SECRET_KEY)
        user_id = payload.get("sub")

        # CRITICAL: Check user exists and is active
        user = get_user_by_id(db, user_id)
        if not user or not user.is_active:
            raise HTTPException(401, "Invalid credentials")

        return user
```

**Validation**:
```bash
# Test registration
curl -X POST http://localhost:8000/api/v1/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email": "test@example.com", "password": "securepass123"}'

# Test login
curl -X POST http://localhost:8000/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email": "test@example.com", "password": "securepass123"}'

# Test protected endpoint
curl http://localhost:8000/api/v1/auth/me \
  -H "Authorization: Bearer {token}"

# Run auth tests
pytest tests/unit/test_auth.py -v
```

---

### Task 4: Frontend Core Setup

**Goal**: Setup frontend application structure, routing, and API client

**Steps**:
1. Configure build tool and TypeScript
2. Setup routing
3. Create API client
4. Setup state management
5. Create base UI components

**Files to Create**:
```yaml
CREATE frontend/src/lib/api.ts:
  - Axios/Fetch wrapper
  - Request/response interceptors
  - Error handling

  PSEUDOCODE:
    import axios from 'axios'

    const api = axios.create({
      baseURL: import.meta.env.VITE_API_URL,
      timeout: 10000,
    })

    // CRITICAL: Add auth token to requests
    api.interceptors.request.use((config) => {
      const token = localStorage.getItem('token')
      if (token) {
        config.headers.Authorization = `Bearer ${token}`
      }
      return config
    })

    // CRITICAL: Handle 401 errors
    api.interceptors.response.use(
      (response) => response,
      (error) => {
        if (error.response?.status === 401) {
          // Redirect to login
          window.location.href = '/login'
        }
        return Promise.reject(error)
      }
    )

CREATE frontend/src/types/index.ts:
  - User types
  - API response types
  - PATTERN: Match backend schemas

CREATE frontend/src/store/auth.ts:
  - Authentication state
  - Login/logout actions
  - PATTERN: [State management library] best practices

CREATE frontend/src/components/ui/:
  - Button.tsx
  - Input.tsx
  - Card.tsx
  - Modal.tsx
  - PATTERN: [UI library] components or custom components

CREATE frontend/src/components/layout/:
  - Layout.tsx (main layout wrapper)
  - Header.tsx
  - Sidebar.tsx (if applicable)
  - Footer.tsx

CREATE frontend/src/pages/:
  - Login.tsx
  - Register.tsx
  - Dashboard.tsx
  - NotFound.tsx

CREATE frontend/src/main.tsx:
  - App initialization
  - Router setup
  - Global providers
```

**Validation**:
```bash
# Build frontend
cd frontend && npm run build

# Type check
npm run type-check

# Lint
npm run lint

# Test
npm run test

# Run dev server
npm run dev
```

---

### Task 5: CI/CD Pipeline Setup

**Goal**: Automated testing, linting, and deployment pipeline

**Steps**:
1. Create GitHub Actions workflow
2. Setup test automation
3. Setup linting
4. Configure deployment

**Files to Create**:
```yaml
CREATE .github/workflows/ci.yml:
  - PATTERN: Standard CI/CD workflow

  CONTENT:
    name: CI/CD Pipeline

    on:
      push:
        branches: [main, develop]
      pull_request:
        branches: [main, develop]

    jobs:
      backend-tests:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v3
          - name: Setup Python
            uses: actions/setup-python@v4
            with:
              python-version: '3.11'
          - name: Install dependencies
            run: |
              cd backend
              pip install -r requirements.txt
          - name: Run linting
            run: |
              cd backend
              ruff check .
              mypy .
          - name: Run tests
            run: |
              cd backend
              pytest tests/ -v --cov

      frontend-tests:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v3
          - name: Setup Node
            uses: actions/setup-node@v3
            with:
              node-version: '18'
          - name: Install dependencies
            run: |
              cd frontend
              npm ci
          - name: Run linting
            run: |
              cd frontend
              npm run lint
          - name: Run tests
            run: |
              cd frontend
              npm run test
          - name: Build
            run: |
              cd frontend
              npm run build
```

**Validation**:
```bash
# Test CI locally (if using act)
act -j backend-tests
act -j frontend-tests

# Or push to GitHub and verify workflow runs
git push origin develop
```

---

### Task 6: Docker Setup

**Goal**: Containerize application for consistent development and deployment

**Steps**:
1. Create Dockerfiles
2. Create docker-compose for development
3. Setup volumes and networking

**Files to Create**:
```yaml
CREATE docker/Dockerfile.backend:
  CONTENT:
    FROM python:3.11-slim

    WORKDIR /app

    # Install dependencies
    COPY backend/requirements.txt .
    RUN pip install --no-cache-dir -r requirements.txt

    # Copy application
    COPY backend/ .

    # Run migrations and start server
    CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]

CREATE docker/Dockerfile.frontend:
  CONTENT:
    FROM node:18-alpine as build

    WORKDIR /app

    COPY frontend/package*.json ./
    RUN npm ci

    COPY frontend/ .
    RUN npm run build

    FROM nginx:alpine
    COPY --from=build /app/dist /usr/share/nginx/html
    EXPOSE 80
    CMD ["nginx", "-g", "daemon off;"]

CREATE docker-compose.yml:
  CONTENT:
    version: '3.8'

    services:
      db:
        image: postgres:15
        environment:
          POSTGRES_DB: ${DB_NAME}
          POSTGRES_USER: ${DB_USER}
          POSTGRES_PASSWORD: ${DB_PASSWORD}
        volumes:
          - postgres_data:/var/lib/postgresql/data
        ports:
          - "5432:5432"

      backend:
        build:
          context: .
          dockerfile: docker/Dockerfile.backend
        environment:
          DATABASE_URL: postgresql://${DB_USER}:${DB_PASSWORD}@db:5432/${DB_NAME}
        depends_on:
          - db
        ports:
          - "8000:8000"
        volumes:
          - ./backend:/app

      frontend:
        build:
          context: .
          dockerfile: docker/Dockerfile.frontend
        depends_on:
          - backend
        ports:
          - "3000:80"

    volumes:
      postgres_data:
```

**Validation**:
```bash
# Build containers
docker-compose build

# Start services
docker-compose up -d

# Check services running
docker-compose ps

# View logs
docker-compose logs -f

# Test API
curl http://localhost:8000/health

# Test frontend
curl http://localhost:3000
```

---

### Task 7: Environment Configuration & Documentation

**Goal**: Complete environment setup and comprehensive documentation

**Steps**:
1. Finalize .env.example
2. Create comprehensive README
3. Setup development guidelines
4. Create deployment guide

**Files to Create**:
```yaml
CREATE .env.example:
  CONTENT:
    # Database Configuration
    DB_NAME=project_db
    DB_USER=postgres
    DB_PASSWORD=changeme
    DATABASE_URL=postgresql://postgres:changeme@localhost:5432/project_db

    # Backend Configuration
    SECRET_KEY=change-this-to-random-secret-key
    ALGORITHM=HS256
    ACCESS_TOKEN_EXPIRE_MINUTES=30
    BACKEND_CORS_ORIGINS=["http://localhost:3000"]

    # Frontend Configuration
    VITE_API_URL=http://localhost:8000/api/v1

    # [Additional services from ARG]
    # [Service specific environment variables]

CREATE README.md:
  SECTIONS:
    - Project overview
    - Technology stack
    - Prerequisites
    - Installation steps
    - Running locally
    - Running with Docker
    - Testing
    - Deployment
    - Project structure
    - Contributing guidelines

CREATE DEVELOPMENT.md:
  SECTIONS:
    - Development setup
    - Code style guidelines
    - Git workflow
    - Testing requirements
    - PR process

CREATE DEPLOYMENT.md:
  SECTIONS:
    - Deployment prerequisites
    - Environment variables
    - Database migrations
    - Deployment steps for [hosting platform]
    - Rollback procedures
```

**Validation**:
```bash
# Verify .env.example is complete
cat .env.example

# Verify README has all sections
cat README.md

# Test fresh installation following README
# (in a new directory or VM)
```

---

## 🧪 Validation Loop

### Level 1: Syntax & Style

**Backend**:
```bash
# Navigate to backend
cd backend

# Install dev dependencies
pip install ruff mypy pytest

# Check code style
ruff check . --fix

# Type checking
mypy src/

# Expected: No errors
```

**Frontend**:
```bash
# Navigate to frontend
cd frontend

# Lint
npm run lint

# Type check
npm run type-check

# Expected: No errors
```

---

### Level 2: Unit Tests

**Backend Tests**:
```bash
cd backend

# Run all tests
pytest tests/ -v --cov=src --cov-report=term-missing

# Minimum coverage target: 80%

# Key test files to create:
CREATE tests/unit/test_auth.py:
  - Test password hashing
  - Test JWT token creation/validation
  - Test user registration
  - Test user login

CREATE tests/unit/test_models.py:
  - Test user model creation
  - Test model relationships
  - Test model validation

CREATE tests/integration/test_api.py:
  - Test registration endpoint
  - Test login endpoint
  - Test protected endpoint access
```

**Frontend Tests**:
```bash
cd frontend

# Run all tests
npm run test

# Key test files to create:
CREATE tests/components/Auth.test.tsx:
  - Test login form validation
  - Test registration form
  - Test auth state management

CREATE tests/api/client.test.ts:
  - Test API client initialization
  - Test request interceptors
  - Test error handling
```

---

### Level 3: Integration Testing

**Manual Testing Checklist**:
```bash
# Start all services
docker-compose up -d

# Test 1: Database connection
docker-compose exec backend python -c "from src.core.database import engine; print(engine.connect())"
# Expected: Connection object

# Test 2: Backend health check
curl http://localhost:8000/health
# Expected: {"status": "healthy"}

# Test 3: User registration
curl -X POST http://localhost:8000/api/v1/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email": "test@example.com", "password": "SecurePass123!", "full_name": "Test User"}'
# Expected: User object with ID

# Test 4: User login
curl -X POST http://localhost:8000/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email": "test@example.com", "password": "SecurePass123!"}'
# Expected: Access token

# Test 5: Protected endpoint
TOKEN="[token from login]"
curl http://localhost:8000/api/v1/auth/me \
  -H "Authorization: Bearer $TOKEN"
# Expected: Current user data

# Test 6: Frontend loads
curl http://localhost:3000
# Expected: HTML content

# Test 7: Frontend can reach backend
# Open http://localhost:3000 in browser
# Try to register and login
# Expected: Successful registration and login flow
```

---

### Level 4: Deployment Testing

```bash
# Test production build
cd backend
pip install -r requirements.txt
uvicorn src.main:app --host 0.0.0.0 --port 8000

cd frontend
npm run build
npm run preview

# Verify no console errors
# Verify API calls work
# Verify authentication flow works
```

---

## ✅ Final Validation Checklist

### Project Setup
- [ ] Directory structure matches specification
- [ ] Git repository initialized
- [ ] .gitignore configured correctly
- [ ] .env.example contains all required variables

### Backend
- [ ] Backend server starts without errors
- [ ] Database connection successful
- [ ] Migrations run successfully
- [ ] Authentication endpoints work
- [ ] Protected routes require authentication
- [ ] All backend tests pass
- [ ] No linting errors
- [ ] No type errors
- [ ] API documentation generated (Swagger/OpenAPI)

### Frontend
- [ ] Frontend builds successfully
- [ ] Dev server runs without errors
- [ ] Routing works correctly
- [ ] API client configured correctly
- [ ] Authentication flow works (register/login/logout)
- [ ] Protected routes redirect unauthenticated users
- [ ] All frontend tests pass
- [ ] No linting errors
- [ ] No type errors
- [ ] Responsive design works

### Infrastructure
- [ ] Docker containers build successfully
- [ ] docker-compose starts all services
- [ ] Services can communicate with each other
- [ ] Volumes persist data correctly

### CI/CD
- [ ] GitHub Actions workflow runs successfully
- [ ] All tests pass in CI
- [ ] Linting passes in CI
- [ ] Build succeeds in CI

### Documentation
- [ ] README.md is comprehensive
- [ ] Installation steps are clear
- [ ] All environment variables documented
- [ ] Architecture documented
- [ ] API endpoints documented

### Security
- [ ] Passwords are hashed
- [ ] JWT tokens have expiration
- [ ] CORS configured correctly
- [ ] SQL injection prevention in place
- [ ] XSS prevention in place
- [ ] Environment variables not committed

---

## 🚀 Post-Implementation Steps

### 1. Code Review
- Review all generated code
- Check for security vulnerabilities
- Verify best practices followed
- Ensure code is well-documented

### 2. Performance Testing
- Test API response times
- Test frontend load times
- Identify bottlenecks
- Optimize if needed

### 3. Security Audit
- Run security scanning tools
- Check for common vulnerabilities
- Verify authentication/authorization
- Test input validation

### 4. Documentation Review
- Verify README accuracy
- Test installation steps
- Update any outdated information
- Add missing documentation

---

## 🐛 Common Issues & Solutions

### Issue 1: Database Connection Fails
**Symptoms**: Cannot connect to database
**Solutions**:
- Verify DATABASE_URL is correct
- Check database service is running
- Verify database credentials
- Check network connectivity

### Issue 2: JWT Token Validation Fails
**Symptoms**: 401 errors on protected routes
**Solutions**:
- Verify SECRET_KEY matches between environments
- Check token expiration
- Verify token format in Authorization header
- Check JWT algorithm matches

### Issue 3: CORS Errors
**Symptoms**: Frontend cannot reach backend API
**Solutions**:
- Verify BACKEND_CORS_ORIGINS includes frontend URL
- Check backend CORS middleware configuration
- Verify request headers
- Check browser console for specific CORS error

### Issue 4: Build Fails
**Symptoms**: npm run build or docker build fails
**Solutions**:
- Clear node_modules and reinstall
- Check Node/Python version compatibility
- Verify all dependencies in package.json/requirements.txt
- Check for syntax errors

---

## 📊 Success Metrics

### Completion Criteria
- ✅ All validation checklist items completed
- ✅ All tests passing (100% of tests)
- ✅ Code coverage > 80%
- ✅ No linting or type errors
- ✅ Documentation complete
- ✅ Application runs in production mode
- ✅ CI/CD pipeline successful

### Quality Metrics
- **Code Coverage**: Target > 80%
- **Build Time**: < 5 minutes
- **API Response Time**: < 200ms (p95)
- **Frontend Load Time**: < 2 seconds
- **Lighthouse Score**: > 90

---

## 🔗 References & Resources

### Framework Documentation
- [Primary framework docs]
- [Database/ORM docs]
- [Authentication library docs]

### Best Practices
- [Security best practices]
- [API design guidelines]
- [Testing strategies]

### Tools & Libraries
- [Build tools documentation]
- [Testing frameworks]
- [CI/CD platforms]

---

## 📝 Notes for AI Implementation

### Critical Reminders
- Follow CLAUDE.md guidelines strictly
- Use existing patterns from _ce/examples/
- Validate after each major step
- Don't skip error handling
- Write tests as you implement features
- Document complex logic with comments
- Use type hints/annotations throughout

### Implementation Order
1. Start with backend foundation (DB, auth)
2. Create API endpoints
3. Write backend tests
4. Setup frontend structure
5. Implement frontend features
6. Write frontend tests
7. Setup Docker and CI/CD
8. Final documentation pass

### When in Doubt
- Check ARG document for clarification
- Search official documentation
- Look for similar patterns in _ce/examples/
- Ask for clarification if requirements unclear
- Prioritize security and best practices

---

**Confidence Score: [8-10]/10**

This initial setup PRP provides comprehensive guidance for setting up a production-ready application foundation with all necessary components, validation steps, and best practices.
