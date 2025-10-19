# Feature Implementation - Product Requirements Prompt (PRP)

**Generated from**: `$ARGUMENTS`
**Generated on**: [Date]
**Feature Name**: [Name from ARG document]
**Feature Number**: [Number from ARG]
**Priority**: [Priority from ARG]

---

## 🎯 Purpose

Dit PRP document beschrijft de complete implementatie van feature: [Feature Name]

## Core Principles

1. **Context is King**: Include ALL necessary documentation, examples, and caveats
2. **Validation Loops**: Provide executable tests/lints the AI can run and fix
3. **Information Dense**: Use keywords and patterns from the codebase
4. **Progressive Success**: Start simple, validate, then enhance
5. **Global Rules**: Follow all rules in CLAUDE.md

---

## 📋 Feature Overview

### Goal
[Extract from ARG: What needs to be built - be specific about the end state]

### Why
[Extract from ARG: Business value]
- **Business Value**: [Impact on product/business]
- **User Impact**: [How users benefit]
- **Integration**: [How it fits with existing features]
- **Problems Solved**: [Specific problems this addresses]

### What
[Extract from ARG: User-visible behavior and technical requirements]

### User Story
**As a** [user type from ARG]
**I want** [functionality from ARG]
**So that** [benefit from ARG]

---

## ✅ Success Criteria

[Extract all acceptance criteria from ARG document]

### Functional Requirements
- [ ] [Requirement 1 from ARG]
- [ ] [Requirement 2 from ARG]
- [ ] [Requirement 3 from ARG]

### Non-functional Requirements
- [ ] [Performance requirement from ARG]
- [ ] [Security requirement from ARG]
- [ ] [Accessibility requirement from ARG]

---

## 📚 All Needed Context

### Documentation & References

```yaml
# Framework & Library Documentation
- url: [Relevant framework docs for this feature]
  why: [Specific sections needed]
  critical: [Key insights]

- url: [Library documentation]
  why: [What you need to know]
  critical: [Common pitfalls to avoid]

# API Documentation (if feature uses external APIs)
- url: [API documentation URL]
  why: [Endpoints and methods needed]
  critical: [Rate limits, authentication, quirks]

# Internal Codebase References
- file: [path/to/similar/feature.py]
  why: [Pattern to follow for this implementation]
  critical: [What to replicate, what to avoid]

- file: [path/to/component/to/modify.tsx]
  why: [Existing component that will be extended]
  critical: [Current implementation details]

# Examples from _ce/examples/
- file: _ce/examples/[relevant-example]
  why: [Pattern this demonstrates]
  critical: [Best practices to follow]

# Design & UI References
- url: [Figma/design link if available]
  why: [UI/UX specifications]

- file: _ce/examples/[ui-component-example]
  why: [UI pattern to follow]
```

### Current Codebase Structure

```bash
# Run `tree -L 3 -I 'node_modules|__pycache__|.git'` to get current structure
[Paste relevant portion of codebase tree showing affected areas]
```

### Files Affected by This Feature

```bash
# Files to be created
CREATE backend/src/api/v1/[feature-name].py
CREATE backend/src/models/[feature-model].py
CREATE backend/src/schemas/[feature-schema].py
CREATE backend/src/services/[feature-service].py
CREATE frontend/src/pages/[FeaturePage].tsx
CREATE frontend/src/components/[FeatureComponent].tsx
CREATE frontend/src/api/[feature-api].ts

# Files to be modified
MODIFY backend/src/api/v1/__init__.py
MODIFY frontend/src/routes/index.tsx
MODIFY [other files from ARG]

# Tests to be created
CREATE backend/tests/unit/test_[feature].py
CREATE backend/tests/integration/test_[feature]_api.py
CREATE frontend/tests/[Feature].test.tsx
```

### Known Gotchas & Library Quirks

```python
# CRITICAL: [From ARG - framework-specific gotchas]
# CRITICAL: [From codebase analysis - existing patterns to follow]
# GOTCHA: [Common mistakes to avoid]
# GOTCHA: [Library version compatibility issues]
# PATTERN: [Established pattern in codebase to replicate]
```

---

## 🏗️ Implementation Blueprint

### Data Models and Structure

[Extract from ARG - database changes and models]

#### Database Changes

**New Tables** (if applicable):
```sql
-- From ARG document
CREATE TABLE [table_name] (
    id UUID PRIMARY KEY,
    [field1] VARCHAR(255) NOT NULL,
    [field2] INTEGER,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_[field]_lookup ON [table_name]([field]);
```

**Modified Tables** (if applicable):
```sql
-- Migrations needed
ALTER TABLE [existing_table] ADD COLUMN [new_field] [TYPE];
CREATE INDEX idx_[new_field] ON [existing_table]([new_field]);
```

#### Backend Models

```python
# PATTERN: Follow existing model structure from codebase

# backend/src/models/[feature_model].py
from sqlalchemy import Column, String, Integer, ForeignKey
from sqlalchemy.orm import relationship
from src.models.base import BaseModel  # PATTERN: Use existing base

class [FeatureModel](BaseModel):
    __tablename__ = "[table_name]"

    # Fields from ARG
    [field1] = Column(String(255), nullable=False, index=True)
    [field2] = Column(Integer, nullable=True)

    # PATTERN: Relationships following existing conventions
    [related_id] = Column(UUID, ForeignKey("[other_table].id"))
    [related] = relationship("[OtherModel]", back_populates="[feature]")

    # CRITICAL: Add validation if needed
    # CRITICAL: Add indexes for queried fields
```

#### Pydantic Schemas

```python
# backend/src/schemas/[feature_schema].py
from pydantic import BaseModel, Field, validator

class [Feature]Create(BaseModel):
    [field1]: str = Field(..., min_length=1, max_length=255)
    [field2]: Optional[int] = Field(None, ge=0)

    # PATTERN: Validators following existing schema patterns
    @validator('[field1]')
    def validate_field1(cls, v):
        # CRITICAL: Input validation
        return v

class [Feature]Response(BaseModel):
    id: UUID
    [field1]: str
    [field2]: Optional[int]
    created_at: datetime

    class Config:
        from_attributes = True  # PATTERN: For SQLAlchemy models
```

#### Frontend Types

```typescript
// frontend/src/types/[feature].ts
// PATTERN: Match backend schemas

export interface [Feature] {
  id: string
  [field1]: string
  [field2]: number | null
  createdAt: string
}

export interface [Feature]CreateInput {
  [field1]: string
  [field2]?: number
}
```

---

### Task List - Implementation Steps

[Extract and expand implementation plan from ARG]

#### Task 1: Database Migration & Models

**Goal**: Create database schema and ORM models

**Steps**:
1. Create Alembic migration for database changes
2. Create SQLAlchemy models
3. Create Pydantic schemas for validation

**Files to Create/Modify**:
```yaml
CREATE backend/alembic/versions/[timestamp]_[feature_name].py:
  - PATTERN: Follow existing migration pattern
  - Add new tables/columns from ARG
  - Add indexes for performance

CREATE backend/src/models/[feature_model].py:
  - PATTERN: Follow src/models/user.py structure
  - Define model with fields from ARG
  - Add relationships
  - Add constraints

CREATE backend/src/schemas/[feature_schema].py:
  - PATTERN: Follow existing schema patterns
  - Create input schemas
  - Create response schemas
  - Add validators
```

**Pseudocode**:
```python
# Migration
def upgrade():
    # PATTERN: Use existing migration pattern
    op.create_table(
        '[table_name]',
        sa.Column('id', UUID(), primary_key=True),
        sa.Column('[field]', sa.String(255), nullable=False),
        # ... other columns from ARG
    )
    # CRITICAL: Add indexes for queried fields
    op.create_index('idx_[field]', '[table_name]', ['[field]'])
```

**Validation**:
```bash
# Create and run migration
alembic revision --autogenerate -m "Add [feature] tables"
alembic upgrade head

# Verify tables created
psql $DATABASE_URL -c "\d [table_name]"

# Test model creation
python -c "from src.models.[feature_model] import [Model]; print([Model].__table__)"
```

---

#### Task 2: Backend Business Logic

**Goal**: Implement service layer with business logic

**Steps**:
1. Create service functions
2. Implement CRUD operations
3. Add business logic validation
4. Handle edge cases

**Files to Create/Modify**:
```yaml
CREATE backend/src/services/[feature_service].py:
  - PATTERN: Follow existing service patterns
  - Implement from ARG implementation plan
  - Add error handling
  - Add logging

MODIFY backend/src/services/__init__.py:
  - Export new service functions
```

**Pseudocode**:
```python
# backend/src/services/[feature_service].py
from sqlalchemy.orm import Session
from src.models.[feature_model] import [FeatureModel]
from src.schemas.[feature_schema] import [Feature]Create

async def create_[feature](
    db: Session,
    [feature]_data: [Feature]Create,
    user_id: UUID
) -> [FeatureModel]:
    """
    Create new [feature] instance.

    Args:
        db: Database session
        [feature]_data: Input data
        user_id: Current user ID

    Returns:
        Created [feature] model instance

    Raises:
        ValueError: If validation fails
        PermissionError: If user lacks permission
    """
    # CRITICAL: Validate business rules from ARG
    # PATTERN: Follow existing validation patterns

    # CRITICAL: Check permissions if needed
    # if not has_permission(user_id, "create_[feature]"):
    #     raise PermissionError("Insufficient permissions")

    # Create instance
    [feature] = [FeatureModel](
        **[feature]_data.dict(),
        created_by_id=user_id
    )

    db.add([feature])
    db.commit()
    db.refresh([feature])

    # PATTERN: Log important actions
    logger.info(f"Created [feature] {[feature].id} by user {user_id}")

    return [feature]

# PATTERN: Implement other CRUD operations
async def get_[feature](db: Session, [feature]_id: UUID) -> Optional[[FeatureModel]]:
    # CRITICAL: Add proper error handling
    pass

async def update_[feature](db: Session, [feature]_id: UUID, data: dict):
    # CRITICAL: Validate ownership/permissions
    pass

async def delete_[feature](db: Session, [feature]_id: UUID, user_id: UUID):
    # CRITICAL: Soft delete vs hard delete based on ARG requirements
    pass
```

**Validation**:
```bash
# Unit test the service
pytest backend/tests/unit/test_[feature]_service.py -v

# Expected: All tests pass
```

---

#### Task 3: API Endpoints

**Goal**: Create REST API endpoints for the feature

**Steps**:
1. Create API router
2. Implement endpoints from ARG
3. Add authentication/authorization
4. Add request validation

**Files to Create/Modify**:
```yaml
CREATE backend/src/api/v1/[feature].py:
  - PATTERN: Follow existing router patterns
  - Implement endpoints from ARG
  - Add auth dependencies
  - Add OpenAPI documentation

MODIFY backend/src/api/v1/__init__.py:
  - Include new router

MODIFY backend/src/main.py:
  - May need to update CORS or middleware
```

**Pseudocode**:
```python
# backend/src/api/v1/[feature].py
from fastapi import APIRouter, Depends, HTTPException, status
from sqlalchemy.orm import Session
from typing import List

from src.api.deps import get_db, get_current_user
from src.models.user import User
from src.schemas.[feature_schema] import [Feature]Create, [Feature]Response
from src.services import [feature_service]

router = APIRouter(prefix="/[features]", tags=["[features]"])

@router.post(
    "/",
    response_model=[Feature]Response,
    status_code=status.HTTP_201_CREATED,
    summary="Create new [feature]"
)
async def create_[feature](
    [feature]_data: [Feature]Create,
    db: Session = Depends(get_db),
    current_user: User = Depends(get_current_user)
):
    """
    Create a new [feature].

    - **[field1]**: Required field description
    - **[field2]**: Optional field description
    """
    # CRITICAL: Validate input
    # PATTERN: Use service layer for business logic
    try:
        [feature] = await [feature_service].create_[feature](
            db=db,
            [feature]_data=[feature]_data,
            user_id=current_user.id
        )
        return [feature]
    except ValueError as e:
        raise HTTPException(
            status_code=status.HTTP_400_BAD_REQUEST,
            detail=str(e)
        )
    except PermissionError as e:
        raise HTTPException(
            status_code=status.HTTP_403_FORBIDDEN,
            detail=str(e)
        )

@router.get(
    "/{[feature]_id}",
    response_model=[Feature]Response,
    summary="Get [feature] by ID"
)
async def get_[feature](
    [feature]_id: UUID,
    db: Session = Depends(get_db),
    current_user: User = Depends(get_current_user)
):
    """Get a specific [feature] by ID."""
    [feature] = await [feature_service].get_[feature](db, [feature]_id)

    if not [feature]:
        raise HTTPException(
            status_code=status.HTTP_404_NOT_FOUND,
            detail="[Feature] not found"
        )

    # CRITICAL: Check access permissions if needed
    # if [feature].created_by_id != current_user.id and not current_user.is_admin:
    #     raise HTTPException(403, "Access denied")

    return [feature]

# PATTERN: Implement other endpoints from ARG
# - GET /[features]/ - List with pagination
# - PUT /[features]/{id} - Update
# - DELETE /[features]/{id} - Delete
```

**Validation**:
```bash
# Test endpoints manually
# Start server
uvicorn src.main:app --reload

# Test create
curl -X POST http://localhost:8000/api/v1/[features]/ \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"[field1]": "value", "[field2]": 123}'

# Expected: 201 Created with [feature] object

# Test get
curl http://localhost:8000/api/v1/[features]/{id} \
  -H "Authorization: Bearer $TOKEN"

# Expected: 200 OK with [feature] object

# Run integration tests
pytest backend/tests/integration/test_[feature]_api.py -v
```

---

#### Task 4: Frontend API Client

**Goal**: Create frontend API client for the feature

**Steps**:
1. Create API client functions
2. Add TypeScript types
3. Handle errors
4. Add loading states

**Files to Create/Modify**:
```yaml
CREATE frontend/src/api/[feature].ts:
  - PATTERN: Follow existing API client pattern
  - Mirror backend endpoints
  - Add error handling

CREATE frontend/src/types/[feature].ts:
  - PATTERN: Match backend schemas
  - Export types for components
```

**Pseudocode**:
```typescript
// frontend/src/api/[feature].ts
import { api } from './client'
import type { [Feature], [Feature]CreateInput } from '../types/[feature]'

export const [feature]Api = {
  // PATTERN: Follow existing API client patterns

  async create([feature]Data: [Feature]CreateInput): Promise<[Feature]> {
    // CRITICAL: Handle errors consistently
    try {
      const response = await api.post<[Feature]>('/[features]/', [feature]Data)
      return response.data
    } catch (error) {
      // PATTERN: Use existing error handling
      throw handleApiError(error)
    }
  },

  async getById(id: string): Promise<[Feature]> {
    const response = await api.get<[Feature]>(`/[features]/${id}`)
    return response.data
  },

  async list(params?: { page?: number; limit?: number }): Promise<[Feature][]> {
    const response = await api.get<[Feature][]>('/[features]/', { params })
    return response.data
  },

  async update(id: string, data: Partial<[Feature]CreateInput>): Promise<[Feature]> {
    const response = await api.put<[Feature]>(`/[features]/${id}`, data)
    return response.data
  },

  async delete(id: string): Promise<void> {
    await api.delete(`/[features]/${id}`)
  },
}
```

**Validation**:
```bash
# Type check
cd frontend && npm run type-check

# Test API client
npm run test -- [feature].test.ts
```

---

#### Task 5: Frontend UI Components

**Goal**: Implement UI components for the feature

**Steps**:
1. Create page component
2. Create feature-specific components
3. Add form validation
4. Add loading/error states
5. Style components

**Files to Create/Modify**:
```yaml
CREATE frontend/src/pages/[FeaturePage].tsx:
  - PATTERN: Follow existing page structure
  - Implement user flow from ARG

CREATE frontend/src/components/[FeatureForm].tsx:
  - PATTERN: Follow existing form patterns
  - Add validation
  - Add error handling

CREATE frontend/src/components/[FeatureList].tsx:
  - PATTERN: Follow existing list patterns
  - Add pagination if needed
  - Add loading states

MODIFY frontend/src/routes/index.tsx:
  - Add new routes
```

**Pseudocode**:
```typescript
// frontend/src/pages/[FeaturePage].tsx
import { useState, useEffect } from 'react'
import { useNavigate } from 'react-router-dom'
import { [feature]Api } from '../api/[feature]'
import { [Feature]Form } from '../components/[FeatureForm]'
import { toast } from '../lib/toast'

export function [Feature]Page() {
  const [loading, setLoading] = useState(false)
  const [error, setError] = useState<string | null>(null)
  const navigate = useNavigate()

  // PATTERN: Follow existing state management patterns

  const handleCreate = async (data: [Feature]CreateInput) => {
    setLoading(true)
    setError(null)

    try {
      // CRITICAL: Validate data client-side
      const [feature] = await [feature]Api.create(data)

      // PATTERN: User feedback
      toast.success('[Feature] created successfully')

      // PATTERN: Navigation after success
      navigate(`/[features]/${[feature].id}`)
    } catch (err) {
      // CRITICAL: Error handling
      const message = err instanceof Error ? err.message : 'Failed to create [feature]'
      setError(message)
      toast.error(message)
    } finally {
      setLoading(false)
    }
  }

  return (
    <div className="container mx-auto p-6">
      <h1 className="text-2xl font-bold mb-6">Create [Feature]</h1>

      {error && (
        <div className="bg-red-50 border border-red-200 text-red-800 px-4 py-3 rounded mb-4">
          {error}
        </div>
      )}

      <[Feature]Form
        onSubmit={handleCreate}
        loading={loading}
      />
    </div>
  )
}

// frontend/src/components/[FeatureForm].tsx
import { useForm } from 'react-hook-form'
import { zodResolver } from '@hookform/resolvers/zod'
import { z } from 'zod'
import { Button } from './ui/Button'
import { Input } from './ui/Input'

// PATTERN: Zod validation matching backend
const [feature]Schema = z.object({
  [field1]: z.string().min(1, 'Field is required').max(255),
  [field2]: z.number().optional(),
})

type [Feature]FormData = z.infer<typeof [feature]Schema>

interface [Feature]FormProps {
  onSubmit: (data: [Feature]FormData) => Promise<void>
  loading?: boolean
  initialData?: Partial<[Feature]FormData>
}

export function [Feature]Form({ onSubmit, loading, initialData }: [Feature]FormProps) {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm<[Feature]FormData>({
    resolver: zodResolver([feature]Schema),
    defaultValues: initialData,
  })

  return (
    <form onSubmit={handleSubmit(onSubmit)} className="space-y-4">
      <div>
        <label htmlFor="[field1]" className="block text-sm font-medium mb-1">
          [Field1 Label]
        </label>
        <Input
          id="[field1]"
          {...register('[field1]')}
          error={errors.[field1]?.message}
          disabled={loading}
        />
      </div>

      {/* Add other fields from ARG */}

      <Button type="submit" loading={loading}>
        {initialData ? 'Update' : 'Create'} [Feature]
      </Button>
    </form>
  )
}
```

**Validation**:
```bash
# Run dev server and test UI
npm run dev

# Manual testing:
# 1. Navigate to /[features]/new
# 2. Fill form with valid data - should succeed
# 3. Fill form with invalid data - should show errors
# 4. Submit form - should create [feature] and redirect
# 5. Check responsive design

# Run component tests
npm run test -- [Feature].test.tsx
```

---

#### Task 6: State Management (if needed)

**Goal**: Add state management for the feature if complex state needed

**Steps**:
1. Create state slice/store
2. Add actions/reducers
3. Connect to components

**Files to Create/Modify**:
```yaml
CREATE frontend/src/store/[feature]Slice.ts:
  - PATTERN: Follow existing store patterns
  - Add state for [feature] data
  - Add actions for CRUD operations

MODIFY frontend/src/store/index.ts:
  - Add new slice to store
```

**Pseudocode**:
```typescript
// Only if using Redux/Zustand/etc and ARG specifies need for global state

// Example with Zustand
import { create } from 'zustand'
import { [feature]Api } from '../api/[feature]'

interface [Feature]State {
  [features]: [Feature][]
  loading: boolean
  error: string | null
  fetchAll: () => Promise<void>
  create: (data: [Feature]CreateInput) => Promise<[Feature]>
  // ... other actions
}

export const use[Feature]Store = create<[Feature]State>((set, get) => ({
  [features]: [],
  loading: false,
  error: null,

  fetchAll: async () => {
    set({ loading: true, error: null })
    try {
      const [features] = await [feature]Api.list()
      set({ [features], loading: false })
    } catch (error) {
      set({ error: error.message, loading: false })
    }
  },

  create: async (data) => {
    set({ loading: true, error: null })
    try {
      const [feature] = await [feature]Api.create(data)
      set((state) => ({
        [features]: [...state.[features], [feature]],
        loading: false,
      }))
      return [feature]
    } catch (error) {
      set({ error: error.message, loading: false })
      throw error
    }
  },
}))
```

---

#### Task 7: Testing

**Goal**: Comprehensive testing for the feature

**Backend Tests**:
```yaml
CREATE backend/tests/unit/test_[feature]_service.py:
  - Test create_[feature]
  - Test get_[feature]
  - Test update_[feature]
  - Test delete_[feature]
  - Test edge cases
  - Test error handling

CREATE backend/tests/integration/test_[feature]_api.py:
  - Test POST /[features]/
  - Test GET /[features]/{id}
  - Test GET /[features]/
  - Test PUT /[features]/{id}
  - Test DELETE /[features]/{id}
  - Test authentication requirements
  - Test authorization checks
```

**Frontend Tests**:
```yaml
CREATE frontend/tests/components/[FeatureForm].test.tsx:
  - Test form rendering
  - Test form validation
  - Test form submission
  - Test error states

CREATE frontend/tests/pages/[FeaturePage].test.tsx:
  - Test page rendering
  - Test user flows
  - Test API integration
  - Test error handling
```

**Test Examples**:
```python
# backend/tests/unit/test_[feature]_service.py
import pytest
from src.services.[feature_service] import create_[feature], get_[feature]
from src.schemas.[feature_schema] import [Feature]Create

@pytest.mark.asyncio
async def test_create_[feature]_success(db_session, test_user):
    """Test successful [feature] creation."""
    # Arrange
    data = [Feature]Create(
        [field1]="test value",
        [field2]=123
    )

    # Act
    [feature] = await create_[feature](
        db=db_session,
        [feature]_data=data,
        user_id=test_user.id
    )

    # Assert
    assert [feature].id is not None
    assert [feature].[field1] == "test value"
    assert [feature].[field2] == 123
    assert [feature].created_by_id == test_user.id

@pytest.mark.asyncio
async def test_create_[feature]_validation_error(db_session, test_user):
    """Test [feature] creation with invalid data."""
    # Arrange
    data = [Feature]Create([field1]="")  # Invalid

    # Act & Assert
    with pytest.raises(ValueError):
        await create_[feature](db_session, data, test_user.id)

# More tests...
```

```typescript
// frontend/tests/components/[FeatureForm].test.tsx
import { render, screen, fireEvent, waitFor } from '@testing-library/react'
import { [Feature]Form } from '../[FeatureForm]'

describe('[FeatureForm]', () => {
  it('renders form fields', () => {
    render(<[Feature]Form onSubmit={jest.fn()} />)

    expect(screen.getByLabelText(/[field1]/i)).toBeInTheDocument()
    expect(screen.getByRole('button', { name: /create/i })).toBeInTheDocument()
  })

  it('shows validation errors for invalid input', async () => {
    render(<[Feature]Form onSubmit={jest.fn()} />)

    const submitButton = screen.getByRole('button', { name: /create/i })
    fireEvent.click(submitButton)

    await waitFor(() => {
      expect(screen.getByText(/field is required/i)).toBeInTheDocument()
    })
  })

  it('calls onSubmit with valid data', async () => {
    const onSubmit = jest.fn()
    render(<[Feature]Form onSubmit={onSubmit} />)

    fireEvent.change(screen.getByLabelText(/[field1]/i), {
      target: { value: 'test value' },
    })

    fireEvent.click(screen.getByRole('button', { name: /create/i }))

    await waitFor(() => {
      expect(onSubmit).toHaveBeenCalledWith({
        [field1]: 'test value',
      })
    })
  })
})
```

**Validation**:
```bash
# Run all backend tests
cd backend
pytest tests/ -v --cov=src/services/[feature_service] --cov=src/api/v1/[feature]

# Target coverage: > 80%

# Run all frontend tests
cd frontend
npm run test -- [Feature]

# E2E test manually:
# 1. Start backend and frontend
# 2. Complete full user flow from ARG
# 3. Verify all acceptance criteria met
```

---

#### Task 8: Documentation

**Goal**: Document the feature

**Files to Create/Modify**:
```yaml
UPDATE README.md:
  - Add feature to feature list
  - Add any new setup steps

CREATE docs/features/[feature-name].md:
  - User guide for the feature
  - API documentation
  - Examples

UPDATE backend API docs:
  - Ensure OpenAPI/Swagger docs are complete
  - Add example requests/responses

ADD inline documentation:
  - Docstrings for all functions
  - Comments for complex logic
```

---

## 🧪 Validation Loop

### Level 1: Syntax & Style

**Backend**:
```bash
cd backend

# Linting
ruff check . --fix

# Type checking
mypy src/

# Expected: No errors
```

**Frontend**:
```bash
cd frontend

# Linting
npm run lint

# Type checking
npm run type-check

# Expected: No errors
```

---

### Level 2: Unit Tests

```bash
# Backend unit tests
cd backend
pytest tests/unit/test_[feature]*.py -v --cov

# Minimum coverage: 80%
# Expected: All tests pass

# Frontend unit tests
cd frontend
npm run test -- [Feature]

# Expected: All tests pass
```

---

### Level 3: Integration Tests

```bash
# Backend integration tests
cd backend
pytest tests/integration/test_[feature]_api.py -v

# Test all endpoints
# Expected: All tests pass, all endpoints working

# Frontend integration
npm run test:integration

# Expected: Components integrate correctly with API
```

---

### Level 4: End-to-End Testing

**Manual E2E Test Checklist**:
```bash
# Start all services
docker-compose up -d

# Test complete user flow from ARG
[ ] User can navigate to [feature]
[ ] User can create new [feature]
[ ] User can view [feature] list
[ ] User can view [feature] details
[ ] User can edit [feature]
[ ] User can delete [feature]
[ ] Validation works correctly
[ ] Error messages are clear
[ ] Loading states work
[ ] UI is responsive
[ ] All acceptance criteria met
```

---

## ✅ Final Validation Checklist

### Implementation Complete
- [ ] All files from task list created
- [ ] All files modified as needed
- [ ] Database migrations run successfully
- [ ] No linting errors (backend & frontend)
- [ ] No type errors (backend & frontend)

### Testing Complete
- [ ] All unit tests pass
- [ ] All integration tests pass
- [ ] E2E tests pass
- [ ] Code coverage > 80%
- [ ] Manual testing complete

### Functionality Complete
- [ ] All acceptance criteria from ARG met
- [ ] All functional requirements implemented
- [ ] All non-functional requirements met
- [ ] Error handling implemented
- [ ] Edge cases handled

### Security & Performance
- [ ] Input validation implemented
- [ ] Authorization checks in place
- [ ] No security vulnerabilities
- [ ] Performance targets met (from ARG)
- [ ] No N+1 queries
- [ ] Proper indexing in database

### Documentation
- [ ] Code is well-documented
- [ ] API documentation updated
- [ ] User documentation created (if needed)
- [ ] README updated
- [ ] Inline comments for complex logic

### Integration
- [ ] Feature integrates with existing features
- [ ] No breaking changes (or documented migration path)
- [ ] UI consistent with design system
- [ ] API follows existing patterns

---

## 🐛 Common Issues & Solutions

### Issue 1: [Common issue from ARG or codebase analysis]
**Symptoms**: [Description]
**Solutions**:
- [Solution 1]
- [Solution 2]

### Issue 2: [Another common issue]
**Symptoms**: [Description]
**Solutions**:
- [Solution 1]
- [Solution 2]

---

## 📊 Success Metrics

[From ARG document]

### Quantitative Metrics
- [Metric 1]: [Target]
- [Metric 2]: [Target]

### Qualitative Metrics
- [Metric 1]: [How to measure]
- [Metric 2]: [How to measure]

### Monitoring
- [ ] Setup monitoring for [key metric]
- [ ] Configure alerts for [error conditions]
- [ ] Track [usage metric]

---

## 🔗 References

### Documentation
- [Link to relevant docs]
- [Link to API reference]

### Code Examples
- [Link to similar feature in codebase]
- [Link to pattern to follow]

### Design
- [Link to design files]
- [Link to UI examples]

---

## 💡 Additional Notes

[Any additional context from ARG that doesn't fit above sections]

---

## 📝 Notes for AI Implementation

### Critical Reminders
- Follow CLAUDE.md guidelines strictly
- Use patterns from existing codebase
- Validate after each task
- Write tests alongside implementation
- Don't skip error handling
- Match backend schemas with frontend types
- Follow security best practices

### Implementation Order
1. Database & models first
2. Backend services
3. API endpoints
4. Backend tests
5. Frontend API client
6. Frontend UI
7. Frontend tests
8. Integration testing
9. Documentation

### When in Doubt
- Check ARG document for requirements
- Look for similar patterns in codebase
- Search official documentation
- Ask for clarification if unclear

---

**Confidence Score: [7-10]/10**

[Brief explanation of confidence level and any uncertainties]
