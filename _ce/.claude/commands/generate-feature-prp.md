# Generate Feature PRP Document

Generate a comprehensive Feature PRP (Product Requirements Prompt) document based on a Feature ARG document.

## ARG Document Path: $ARGUMENTS

This must be the path to the feature ARG document: `arg/feature/[filename].md`

---

## Process

### Step 1: Load Context

1. **Read Feature ARG**:
   ```bash
   Read $ARGUMENTS
   ```

2. **Read Initial ARG** (for project context):
   ```bash
   Read arg/initial/[initial-arg-file].md
   ```

3. **Check Dependencies**:
   - If feature has dependencies, read those feature ARGs too
   - Understand what's already implemented
   - Note integration points

4. **Analyze Codebase**:
   ```bash
   # Get current structure
   tree -L 3 -I 'node_modules|__pycache__|.git|dist|build'

   # Search for affected files
   Find files mentioned in ARG
   ```

### Step 2: Research Phase

**CRITICAL**: Research must be focused on HOW to implement this specific feature.

#### 2.1 Framework-Specific Research

For the technical stack (from Initial ARG):

1. **Feature-Specific Patterns**:
   - Search "[framework] [feature type] implementation"
   - Example: "FastAPI email notifications"
   - Example: "React form validation patterns"

2. **Integration Documentation**:
   - If feature uses external API, search integration guides
   - Rate limiting patterns
   - Error handling best practices

3. **Database Migration Patterns**:
   - Search migration strategies for the framework
   - Backward compatibility patterns
   - Data migration examples

#### 2.2 External API/Service Research

If feature integrates with external services:

```yaml
# Example for SendGrid:
- url: https://docs.sendgrid.com/api-reference
  sections:
    - Authentication
    - Send Email API
    - Templates API
  critical:
    - Rate limits: 100 req/sec
    - Authentication: API Key in header
    - Async sending recommended

# Document for EVERY external service
```

#### 2.3 Similar Implementation Research

Search for:
- Open-source projects with similar feature
- GitHub code examples
- Blog posts with gotchas
- Stack Overflow common pitfalls

#### 2.4 Codebase Pattern Analysis

Analyze existing code:
- How are similar features implemented?
- What patterns to follow?
- What libraries are already used?
- What testing patterns exist?

### Step 3: Generate Feature PRP

1. **Read PRP template**:
   ```bash
   Read prp/feature/template/feature-prp-template.md
   ```

2. **Extract from ARG**:
   - Feature metadata (number, name, priority)
   - Goal, Why, What
   - Success criteria
   - All technical specifications

3. **Add Research Findings**:
   - Documentation URLs
   - Code examples
   - Gotchas discovered
   - Best practices

4. **Create Detailed Implementation Blueprint**:

   For each implementation step from ARG:

   **Task Format**:
   ```yaml
   Task N: [Task Name]

   Goal: [What this task accomplishes]

   Steps:
     1. [Detailed step]
     2. [Detailed step]

   Files to Create/Modify:
     CREATE path/to/file.ext:
       - PATTERN: [Reference to similar file or doc]
       - [What it should contain]
       - [Key methods/functions]

     MODIFY path/to/existing.ext:
       - FIND pattern: [What to look for]
       - ADD: [What to add]
       - PRESERVE: [What not to change]

   Pseudocode:
     [Detailed pseudocode with CRITICAL notes]

   Validation:
     [Commands to run to verify task complete]
   ```

### Step 4: Create Comprehensive Validation Loops

**Level 1: Syntax & Style**
```bash
# Specific commands for this project's stack
cd backend && ruff check . && mypy .
cd frontend && npm run lint && npm run type-check
```

**Level 2: Unit Tests**
```bash
# Test commands for new feature code
pytest tests/unit/test_[feature]_*.py -v --cov
npm run test -- [Feature].test
```

**Level 3: Integration Tests**
```bash
# Test feature integration
pytest tests/integration/test_[feature]_api.py -v
# Manual API testing commands
curl -X POST http://localhost:8000/api/v1/[endpoint]...
```

**Level 4: E2E Tests**
```bash
# Manual test checklist
[ ] User can [action 1]
[ ] User can [action 2]
[ ] Error case [X] shows correct message
[ ] Performance: [metric] < [target]
```

### Step 5: Document Known Issues & Solutions

Based on research:

```markdown
## Common Issues & Solutions

### Issue 1: [Common pitfall from research]
**Symptoms**: [What user sees]
**Cause**: [Why it happens]
**Solution**: [How to fix]

### Issue 2: [Framework-specific gotcha]
**Symptoms**: [Description]
**Solution**: [Fix with code example]
```

### Step 6: Generate Filename & Save

1. **Generate filename**:
   ```
   Format: [number]-[feature-name]-feature-prp.md
   Example: 003-email-notifications-feature-prp.md
   ```

2. **Save**:
   ```
   Location: prp/feature/[filename].md
   ```

### Step 7: Quality Check & Confidence Score

Assess PRP on:
- [ ] All context from ARG included
- [ ] Research findings documented
- [ ] Implementation tasks are concrete and detailed
- [ ] Pseudocode for complex parts provided
- [ ] Validation loops are executable
- [ ] Integration with existing code clear
- [ ] Dependencies handled
- [ ] Error scenarios covered
- [ ] Security implications addressed

**Score PRP on scale 1-10**:
- 8-10: Can implement in one pass
- 6-7: May need minor clarifications
- <6: Need more detail or research

### Step 8: User Guidance

```
✅ Feature PRP generated: prp/feature/[filename].md

The PRP contains:
- Implementation blueprint with [X] concrete tasks
- [Y] documentation references
- [Z] code examples and patterns
- Complete validation loop for self-checking

Confidence Score: [score]/10
[Rationale]

Affected Files:
- CREATE: [list of new files]
- MODIFY: [list of modified files]

Dependencies:
- Features: [list]
- Libraries: [list]

Estimated Implementation Time: [estimate]

Next step:
/execute-feature prp/feature/[filename].md

This will:
1. [Task 1 summary]
2. [Task 2 summary]
...
N. Run validation & tests
```

---

## Important Guidelines

### DO:
- ✅ Research specific implementation patterns for this feature
- ✅ Document all external API details (rate limits, auth, etc.)
- ✅ Reference existing code patterns from codebase
- ✅ Provide detailed pseudocode for complex logic
- ✅ Define clear validation steps per task
- ✅ Document integration with dependent features
- ✅ Include database migration strategy
- ✅ Plan backward compatibility if needed
- ✅ Address security implications
- ✅ Consider performance impact

### DON'T:
- ❌ Skip research on external services
- ❌ Assume patterns without checking codebase
- ❌ Forget about database migration rollback
- ❌ Miss integration testing scenarios
- ❌ Ignore existing test patterns
- ❌ Skip error handling documentation
- ❌ Forget about monitoring/logging
- ❌ Miss edge cases from ARG

---

## PRP Quality Checklist

### Context & Research
- [ ] Feature ARG fully analyzed
- [ ] Initial ARG context included
- [ ] Dependency features reviewed
- [ ] Codebase patterns identified
- [ ] Framework documentation researched
- [ ] External API docs included
- [ ] Similar implementations found
- [ ] Gotchas documented

### Implementation Blueprint
- [ ] All tasks from ARG included
- [ ] Tasks in logical order
- [ ] Files to create/modify specified
- [ ] Patterns referenced
- [ ] Pseudocode for complex parts
- [ ] Database migrations planned
- [ ] API endpoints detailed
- [ ] UI components specified

### Testing & Validation
- [ ] Unit test requirements clear
- [ ] Integration test scenarios defined
- [ ] E2E test checklist provided
- [ ] Validation commands executable
- [ ] Coverage targets set

### Integration & Dependencies
- [ ] Dependency features noted
- [ ] Integration points clear
- [ ] Breaking changes identified
- [ ] Migration path defined (if needed)
- [ ] Backward compatibility addressed

### Technical Details
- [ ] Security considerations addressed
- [ ] Performance implications noted
- [ ] Error handling planned
- [ ] Logging strategy defined
- [ ] Monitoring requirements specified

---

## Example Output Structure

```markdown
# Feature Implementation - Product Requirements Prompt (PRP)

**Generated from**: arg/feature/003-email-notifications-feature-arg.md
**Generated on**: 2024-03-15
**Feature Name**: Email Notifications
**Feature Number**: 003
**Priority**: High

## Purpose
Implement email notification system for task assignments using SendGrid.

## Feature Overview
[From ARG]

## Success Criteria
[From ARG]

## All Needed Context

### Documentation & References
```yaml
# SendGrid API
- url: https://docs.sendgrid.com/api-reference/mail-send/mail-send
  why: Email sending API, template usage
  critical: Rate limit 100 req/sec, requires API key

# FastAPI Background Tasks
- url: https://fastapi.tiangolo.com/tutorial/background-tasks/
  why: Async email sending pattern
  critical: Use BackgroundTasks for non-blocking

# Existing Codebase
- file: backend/src/services/user_service.py
  why: Pattern for service layer implementation
  critical: Follow same error handling pattern
```

### Known Gotchas
```python
# CRITICAL: SendGrid requires API key in X-API-KEY header
# CRITICAL: FastAPI BackgroundTasks for async email sending
# GOTCHA: Email sending can fail - need retry logic
# PATTERN: Use Celery for production (already in stack)
```

## Implementation Blueprint

### Task 1: Database Migration for Notifications
[Detailed task with pseudocode]

### Task 2: SendGrid Integration Service
[Detailed task with pseudocode]

### Task 3: Notification API Endpoints
[Detailed task with pseudocode]

[... etc ...]

## Validation Loop
[Executable validation commands]

**Confidence Score: 8/10**

High confidence because:
- SendGrid well-documented
- FastAPI background tasks pattern clear
- Similar service layer exists
- Dependencies (Task Management) implemented

Minor concern:
- Email template management needs refinement
```

---

## Success Criteria

The /generate-feature-prp command is successful when:

1. ✅ Complete PRP document according to template
2. ✅ All necessary research completed
3. ✅ Implementation tasks are concrete and executable
4. ✅ Validation loops are executable
5. ✅ Integration with existing code is clear
6. ✅ Dependencies are addressed
7. ✅ Confidence score is realistic
8. ✅ Document saved in correct location
9. ✅ User understands next steps

---

**Remember**: A good Feature PRP integrates seamlessly with the existing codebase and follows established patterns!
