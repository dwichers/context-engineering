# Execute Feature PRP

Implement a feature according to the Feature PRP document.

## PRP File: $ARGUMENTS

This must be the path to the feature PRP document: `.claude/prp/feature/[filename].md`

---

## Execution Process

### Step 1: Load PRP & Context

1. **Read the Feature PRP**:
   ```bash
   Read $ARGUMENTS
   ```

2. **Understand all context**:
   - Feature goal and success criteria
   - All documentation references
   - Implementation blueprint
   - Validation gates
   - Known gotchas

3. **Check dependencies**:
   - If PRP lists dependency features, verify they're implemented
   - If not, alert user:
   ```
   ⚠️ Dependency Warning:
   This feature depends on:
   - Feature #[X]: [Name]

   Please implement dependencies first.
   ```

4. **Analyze affected files**:
   - Note files to create
   - Note files to modify
   - Check if files already exist (avoid conflicts)

### Step 2: ULTRATHINK & Planning

**CRITICAL**: Plan thoroughly before implementing.

1. **Create comprehensive task list** using TodoWrite:
   ```
   Based on PRP tasks, typically:
   - Task 1: Database migration (if needed)
   - Task 2: Backend models/schemas
   - Task 3: Backend business logic
   - Task 4: API endpoints
   - Task 5: Frontend API client
   - Task 6: Frontend UI components
   - Task 7: State management (if needed)
   - Task 8: Testing (unit + integration)
   - Task 9: Documentation
   - Task 10: Final validation
   ```

2. **Identify integration points**:
   - Existing code to integrate with
   - Existing patterns to follow
   - Existing tests to update

3. **Plan backwards compatibility**:
   - Breaking changes?
   - Migration strategy?
   - Rollback plan?

### Step 3: Execute Implementation

**Work through each task systematically**:

#### For Each Task:

1. **Mark task as in_progress** (Only ONE at a time!)

2. **Read task details from PRP**:
   - Goal
   - Steps
   - PATTERN references
   - CRITICAL notes
   - Pseudocode

3. **Implement the task following PRP**:

   **If CREATE file**:
   - Follow PATTERN reference from PRP
   - Implement as specified
   - Add proper error handling
   - Add logging if appropriate
   - Add docstrings/comments

   **If MODIFY file**:
   - Read existing file first
   - Find correct insertion point
   - PRESERVE existing functionality
   - Follow existing code style
   - Maintain backward compatibility

4. **Write tests alongside implementation**:
   - Unit tests for new functions/classes
   - Integration tests for API endpoints
   - Component tests for UI

5. **Run task-level validation**:
   ```bash
   # From PRP validation for this task
   [Run specific validation commands]
   ```

6. **Fix issues before proceeding**:
   - Iterate until task validation passes
   - Don't move forward with broken code

7. **Mark task completed** IMMEDIATELY

#### Task-Specific Guidelines:

**Database Migration (if needed)**:
```bash
# Create migration
alembic revision --autogenerate -m "Add [feature] tables"

# Review migration file
# - Check column types correct
# - Verify indexes added
# - Check foreign keys

# Run migration
alembic upgrade head

# Verify in database
psql $DATABASE_URL -c "\d [table_name]"
```

**Backend Models/Schemas**:
```python
# Follow existing model patterns
# Example from PRP:
class [FeatureModel](Base):
    __tablename__ = "[table]"

    # PATTERN: Follow existing base model
    id = Column(UUID(as_uuid=True), primary_key=True, default=uuid4)

    # Fields from PRP
    [field1] = Column(String(255), nullable=False, index=True)

    # CRITICAL: Add created_at/updated_at if pattern exists
    created_at = Column(DateTime, default=datetime.utcnow)
    updated_at = Column(DateTime, default=datetime.utcnow, onupdate=datetime.utcnow)

    # Relationships from PRP
    ...
```

**Backend Business Logic**:
```python
# Follow service layer pattern from codebase
# From PRP pseudocode:

async def create_[feature](
    db: Session,
    data: [Feature]Create,
    user_id: UUID
) -> [FeatureModel]:
    """
    Create new [feature].

    Args:
        db: Database session
        data: Validated input data
        user_id: ID of creating user

    Returns:
        Created [feature] model

    Raises:
        ValueError: If validation fails
        PermissionError: If user lacks permission
    """
    # CRITICAL: Validate business rules (from PRP)
    # PATTERN: Follow existing validation pattern

    # Implementation from PRP pseudocode
    ...

    # PATTERN: Log important actions
    logger.info(f"Created [feature] {result.id}")

    return result
```

**API Endpoints**:
```python
# Follow existing router patterns
# From PRP API specifications:

@router.post(
    "/",
    response_model=[Feature]Response,
    status_code=status.HTTP_201_CREATED,
    summary="Create [feature]"
)
async def create_[feature](
    data: [Feature]Create,
    db: Session = Depends(get_db),
    current_user: User = Depends(get_current_user)
):
    """
    Create new [feature].

    Requires authentication.
    """
    try:
        result = await [feature_service].create_[feature](
            db=db,
            data=data,
            user_id=current_user.id
        )
        return result
    except ValueError as e:
        raise HTTPException(400, detail=str(e))
    except PermissionError:
        raise HTTPException(403, detail="Access denied")
```

**Frontend API Client**:
```typescript
// Follow existing API client pattern
// From PRP:

export const [feature]Api = {
  async create(data: [Feature]CreateInput): Promise<[Feature]> {
    try {
      const response = await api.post<[Feature]>('/[features]/', data)
      return response.data
    } catch (error) {
      throw handleApiError(error)
    }
  },

  // Other methods from PRP...
}
```

**Frontend UI Components**:
```typescript
// Follow existing component patterns
// From PRP UI specifications:

export function [Feature]Form({ onSubmit, loading }: Props) {
  const {
    register,
    handleSubmit,
    formState: { errors }
  } = useForm<[Feature]FormData>({
    resolver: zodResolver([feature]Schema)
  })

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      {/* Fields from PRP */}
      <Input
        label="[Field Label]"
        {...register('[field]')}
        error={errors.[field]?.message}
        disabled={loading}
      />

      <Button type="submit" loading={loading}>
        Create [Feature]
      </Button>
    </form>
  )
}
```

**Testing**:
```python
# Backend unit tests - from PRP test cases

@pytest.mark.asyncio
async def test_create_[feature]_success(db_session, test_user):
    """Test successful [feature] creation."""
    # Arrange
    data = [Feature]Create(
        [field1]="test value"
    )

    # Act
    result = await create_[feature](
        db=db_session,
        data=data,
        user_id=test_user.id
    )

    # Assert
    assert result.id is not None
    assert result.[field1] == "test value"
    assert result.created_by_id == test_user.id

@pytest.mark.asyncio
async def test_create_[feature]_validation_error(db_session, test_user):
    """Test validation error handling."""
    data = [Feature]Create([field1]="")  # Invalid

    with pytest.raises(ValueError):
        await create_[feature](db_session, data, test_user.id)

# Integration tests - from PRP

async def test_create_[feature]_endpoint(client, auth_headers):
    """Test POST /[features]/ endpoint."""
    response = await client.post(
        "/api/v1/[features]/",
        json={"[field1]": "test"},
        headers=auth_headers
    )

    assert response.status_code == 201
    data = response.json()
    assert data["[field1]"] == "test"
```

```typescript
// Frontend tests - from PRP

describe('[FeatureForm]', () => {
  it('validates input correctly', async () => {
    render(<[Feature]Form onSubmit={jest.fn()} />)

    fireEvent.click(screen.getByRole('button', { name: /create/i }))

    await waitFor(() => {
      expect(screen.getByText(/required/i)).toBeInTheDocument()
    })
  })

  it('submits valid data', async () => {
    const onSubmit = jest.fn()
    render(<[Feature]Form onSubmit={onSubmit} />)

    fireEvent.change(screen.getByLabelText(/field/i), {
      target: { value: 'test value' }
    })
    fireEvent.click(screen.getByRole('button', { name: /create/i }))

    await waitFor(() => {
      expect(onSubmit).toHaveBeenCalledWith({
        field1: 'test value'
      })
    })
  })
})
```

### Step 4: Progressive Validation

**After Backend Implementation**:
```bash
cd backend

# Linting
ruff check . --fix
mypy .

# Unit tests for this feature
pytest tests/unit/test_[feature]*.py -v --cov

# Integration tests
pytest tests/integration/test_[feature]_api.py -v

# Manual API test
curl -X POST http://localhost:8000/api/v1/[features]/ \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"[field]": "test"}'
```

**After Frontend Implementation**:
```bash
cd frontend

# Linting
npm run lint

# Type checking
npm run type-check

# Tests
npm run test -- [Feature]

# Manual UI test
npm run dev
# Navigate to /[features] and test manually
```

### Step 5: Comprehensive Validation

Run ALL validation levels from PRP:

**Level 1: Syntax & Style**
```bash
[Execute Level 1 commands from PRP]
# MUST pass with 0 errors
```

**Level 2: Unit Tests**
```bash
[Execute Level 2 commands from PRP]
# MUST achieve >80% coverage for new code
# ALL tests must pass
```

**Level 3: Integration Tests**
```bash
[Execute Level 3 commands from PRP]
# Test all API endpoints work
# Test database operations work
# Test external integrations work (if any)
```

**Level 4: E2E Testing**
```bash
# From PRP E2E checklist:
[ ] User can access feature
[ ] User can create [resource]
[ ] User can view [resource]
[ ] User can edit [resource]
[ ] User can delete [resource]
[ ] Validation shows errors correctly
[ ] Success messages displayed
[ ] Loading states work
[ ] Error states handled
[ ] UI is responsive
```

### Step 6: Fix Issues & Iterate

**If ANY validation fails**:

1. **Identify root cause**:
   - Read error message carefully
   - Check PRP for related gotchas
   - Search relevant documentation

2. **Fix properly**:
   - Fix root cause, not symptoms
   - Maintain code quality
   - Follow established patterns

3. **Re-validate**:
   - Run same validation again
   - Verify fix worked
   - Check for side effects

4. **Iterate until perfect**:
   - Don't compromise on quality
   - All validations must pass

### Step 7: Final Validation Checklist

From PRP's final validation checklist:

```bash
# Implementation Complete
[ ] All files created as specified
[ ] All files modified correctly
[ ] Database migrations run successfully
[ ] No linting errors
[ ] No type errors

# Testing Complete
[ ] All unit tests pass
[ ] All integration tests pass
[ ] E2E tests pass
[ ] Code coverage > 80%
[ ] Manual testing complete

# Functionality Complete
[ ] All acceptance criteria met (from ARG)
[ ] All functional requirements implemented
[ ] All non-functional requirements met
[ ] Error handling implemented
[ ] Edge cases handled

# Security & Performance
[ ] Input validation implemented
[ ] Authorization checks in place
[ ] No security vulnerabilities
[ ] Performance targets met
[ ] No N+1 queries
[ ] Proper database indexing

# Documentation
[ ] Code well-documented
[ ] API documentation updated
[ ] README updated (if needed)
[ ] Inline comments for complex logic

# Integration
[ ] Integrates with existing features
[ ] No breaking changes (or documented)
[ ] UI consistent with design system
[ ] Follows existing API patterns
```

**CRITICAL**: ALL items must be checked.

### Step 8: Review PRP Again

**Re-read Feature PRP** to ensure:
- All tasks completed
- All acceptance criteria met
- All integration points addressed
- All gotchas handled
- All validation passed

### Step 9: Update Documentation

If needed:
- Update README with new feature
- Update API documentation
- Add user guide section
- Document configuration changes

### Step 10: Completion Report

```
✅ Feature Implementation Complete!

Feature: [Name] (Feature #[Number])
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📋 Summary:
[Brief description of what was implemented]

✅ Acceptance Criteria Met:
[List all criteria from ARG with checkmarks]

📁 Files Created:
[List new files]

📝 Files Modified:
[List modified files]

🗄️ Database Changes:
[List migrations, new tables, modified columns]

🔌 New API Endpoints:
[List endpoints with methods]

🎨 New UI Components:
[List components]

📊 Test Coverage:
- Unit Tests: [X]/[Y] passing ([Z]% coverage)
- Integration Tests: [A]/[B] passing
- E2E Tests: ✅ All scenarios passed

✅ Validation Results:
- Linting: ✅ Pass
- Type Checking: ✅ Pass
- Unit Tests: ✅ Pass
- Integration Tests: ✅ Pass
- E2E Tests: ✅ Pass

🚀 How to Use:

[Brief usage instructions or example]

🎯 Next Steps:

Feature ready! You can now:
1. Implement next feature (if available)
2. Add new feature: /generate-feature-arg "[description]"
3. Commit changes: git add . && git commit -m "feat: implement [feature]"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Important Guidelines

### DO:
- ✅ Read Feature PRP completely before starting
- ✅ Verify dependencies implemented first
- ✅ Use TodoWrite to track tasks
- ✅ Only ONE task in_progress at a time
- ✅ Follow ALL patterns from PRP
- ✅ Write tests alongside implementation
- ✅ Run validation progressively
- ✅ Fix issues immediately
- ✅ PRESERVE existing functionality when modifying
- ✅ Follow existing code style
- ✅ Add proper error handling
- ✅ Document complex logic
- ✅ Test edge cases
- ✅ Update existing tests if needed
- ✅ Re-read PRP before marking complete

### DON'T:
- ❌ Skip dependency check
- ❌ Implement without reading PRP fully
- ❌ Skip tasks or take shortcuts
- ❌ Break existing functionality
- ❌ Ignore CRITICAL notes
- ❌ Skip error handling
- ❌ Skip writing tests
- ❌ Move forward with failing validation
- ❌ Ignore linting/type errors
- ❌ Hardcode values (use config)
- ❌ Create breaking changes without migration path
- ❌ Mark complete without all validation passing

---

## Success Criteria

The /execute-feature command is successful when:

1. ✅ ALL tasks from PRP completed
2. ✅ ALL acceptance criteria from ARG met
3. ✅ ALL validation gates pass
4. ✅ ALL tests pass (>80% coverage for new code)
5. ✅ NO linting or type errors
6. ✅ NO breaking changes (or documented migration)
7. ✅ Feature integrates correctly with existing code
8. ✅ Complete user flow works
9. ✅ Documentation updated
10. ✅ Final validation checklist 100% checked
11. ✅ PRP re-read and verified complete

---

**Remember**: A well-implemented feature integrates seamlessly and follows all established patterns!
