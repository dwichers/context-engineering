# Feature Requirements Generator (ARG) Template

## 📌 Feature Metadata

**Feature Number**: [Automatically generated number based on order]
**Feature Name**: [Short, descriptive name]
**Priority**: [Critical / High / Medium / Low]
**Estimated Complexity**: [Low / Medium / High / Very High]
**Dependencies**: [List of other features this feature depends on]

---

## 🎯 Feature Overview

### Feature Description
[Detailed description of what this feature does and why it's important]

### User Story
**As a** [type of user]
**I want** [action/functionality]
**So that** [benefit/result]

### Business Value
[Why is this feature important for the product/business?]

---

## ✅ Acceptance Criteria

### Functional Requirements
- [ ] [Criterion 1 - what the feature must be able to do]
- [ ] [Criterion 2]
- [ ] [Criterion 3]
- [ ] [Criterion 4]

### Non-functional Requirements
- [ ] [Performance requirement - e.g., response time < 200ms]
- [ ] [Security requirement]
- [ ] [Accessibility requirement]
- [ ] [Usability requirement]

---

## 🔧 Technical Specifications

### Affected Components

#### Frontend Components
- **Component 1**: [Component name and what it does]
  - Location: [filepath where it should go]
  - Responsibility: [what does this component do]
  - Dependencies: [other components it uses]

- **Component 2**: [Name and description]
  - Location: [filepath]
  - Responsibility: [...]
  - Dependencies: [...]

#### Backend Components
- **API Endpoint 1**: [e.g., POST /api/users/register]
  - Location: [filepath where it should go]
  - Responsibility: [what does this endpoint do]
  - Request Schema: [describe input]
  - Response Schema: [describe output]

- **Service/Business Logic**: [Service name]
  - Location: [filepath]
  - Responsibility: [what does this service do]

#### Database Changes
- **New Tables**:
  - `table_name`: [description of new table]
    - Columns: [list of columns with types]
    - Indexes: [which indexes]
    - Relationships: [foreign keys, etc.]

- **Modified Tables**:
  - `existing_table`: [which changes]
    - Add columns: [new columns]
    - Modify columns: [modified columns]
    - Add indexes: [new indexes]

- **Migrations**:
  - [Describe migration strategy]

---

## 🎨 UI/UX Specifications

### User Interface Elements
- **New Pages/Views**:
  1. [Page name]: [description of layout and components]
  2. [Page name]: [description]

- **Modified Pages/Views**:
  1. [Existing page]: [what is being changed]

### User Flow
```
[Describe the steps a user goes through]
1. User clicks on [...]
2. System shows [...]
3. User fills in [...]
4. System validates and [...]
5. User sees [...]
```

### Wireframes/Mockups
- [Link to Figma/design tool]
- [Screenshot or UI description]
- [Interaction patterns to follow]

### Design Patterns to Follow
- [Reference to existing components from codebase]
- [Design system guidelines]
- [Accessibility patterns]

---

## 🔌 API Specifications

### New Endpoints

#### Endpoint 1
```yaml
Method: POST
Path: /api/v1/resource
Description: [What this endpoint does]

Headers:
  Authorization: Bearer {token}
  Content-Type: application/json

Request Body:
  {
    "field1": "string",
    "field2": "number",
    "field3": {
      "nested": "object"
    }
  }

Response (200 OK):
  {
    "id": "uuid",
    "field1": "string",
    "created_at": "timestamp"
  }

Response (400 Bad Request):
  {
    "error": "Validation error",
    "details": ["field1 is required"]
  }

Response (401 Unauthorized):
  {
    "error": "Authentication required"
  }
```

#### Endpoint 2
[Repeat above structure]

### Modified Endpoints
- **Endpoint**: [which endpoint is being modified]
  - Changes: [what's changing]
  - Backward Compatibility: [is it backward compatible?]
  - Deprecation Strategy: [if applicable]

---

## 📊 Data Model

### New Models/Entities

#### Model 1: [ModelName]
```python
# Example for Python/SQLAlchemy
class ModelName:
    id: UUID
    field1: str
    field2: int
    field3: Optional[str]
    created_at: datetime
    updated_at: datetime

    # Relationships
    related_model: Relationship["OtherModel"]

    # Constraints
    # Unique constraint on field1
    # Foreign key to other_table.id
```

#### Model 2: [ModelName]
[Repeat structure]

### Modified Models
- **Model Name**: [which changes]
  - New fields: [...]
  - Modified fields: [...]
  - Removed fields: [... with migration strategy]

### Validation Rules
- `field1`: [validation rules - e.g., required, min length 3, max length 50]
- `field2`: [validation rules - e.g., must be positive integer]
- `field3`: [validation rules - e.g., valid email format]

---

## 🔒 Security Considerations

### Authentication & Authorization
- **Who can access this feature?**: [Which roles/users]
- **Permission checks needed**: [Which checks at which level]
- **Sensitive data**: [Which data needs extra protection]

### Input Validation
- [ ] All user inputs are validated
- [ ] SQL injection prevention
- [ ] XSS prevention
- [ ] CSRF protection (for state-changing operations)

### Data Protection
- [ ] Encryption at rest: [which data]
- [ ] Encryption in transit: [HTTPS, TLS]
- [ ] PII handling: [personal identifiable information]
- [ ] Audit logging: [what should be logged]

---

## 📈 Performance Considerations

### Expected Load
- **Concurrent Users**: [number of expected simultaneous users]
- **Requests per Second**: [expected RPS]
- **Data Volume**: [how much data is processed]

### Performance Targets
- **API Response Time**: [e.g., p95 < 200ms]
- **Page Load Time**: [e.g., < 2 seconds]
- **Database Query Time**: [e.g., < 50ms]

### Optimization Strategies
- [ ] Database indexing strategy
- [ ] Caching strategy (Redis, CDN, etc.)
- [ ] Pagination for large datasets
- [ ] Lazy loading for UI
- [ ] Query optimization
- [ ] Background jobs for heavy operations

---

## 🧪 Testing Strategy

### Unit Tests
- **Coverage Target**: [e.g., > 80%]
- **Key Test Cases**:
  1. [Test case description - happy path]
  2. [Test case - edge case]
  3. [Test case - error handling]

### Integration Tests
- **Test Scenarios**:
  1. [End-to-end scenario 1]
  2. [Integration with external service]
  3. [Database operations]

### E2E Tests
- **User Flows to Test**:
  1. [Complete user journey 1]
  2. [Complete user journey 2]

### Manual Test Cases
1. [Test case 1]: [steps to manually test]
2. [Test case 2]: [steps]

---

## 🔗 Dependencies & Integration

### Internal Dependencies
- **Features**: [List of other features that must be implemented first]
  - Feature #[number]: [why is this a dependency]

- **Components**: [Existing components that are used]
  - Component name: [filepath and how it's used]

### External Dependencies
- **Libraries/Packages**:
  - `package-name@version`: [why needed, what it does]
  - `package-name@version`: [description]

- **APIs/Services**:
  - [Service name]: [what it's used for]
  - API Documentation: [link]
  - Rate Limits: [if applicable]

### Breaking Changes
- [ ] No breaking changes
- [ ] Breaking changes with migration path:
  - [Describe breaking change and how to migrate]

---

## 🚀 Implementation Plan

### Step 1: [Phase name - e.g., Database Setup]
**Tasks**:
- [ ] Create migration for new tables
- [ ] Add indexes
- [ ] Test migration locally
**Estimated Time**: [e.g., 2 hours]

### Step 2: [Phase name - e.g., Backend Implementation]
**Tasks**:
- [ ] Create data models/schemas
- [ ] Implement business logic
- [ ] Create API endpoints
- [ ] Add validation
- [ ] Write unit tests
**Estimated Time**: [e.g., 1 day]

### Step 3: [Phase name - e.g., Frontend Implementation]
**Tasks**:
- [ ] Create UI components
- [ ] Implement state management
- [ ] Add API integration
- [ ] Add form validation
- [ ] Write component tests
**Estimated Time**: [e.g., 1 day]

### Step 4: [Phase name - e.g., Integration & Testing]
**Tasks**:
- [ ] Integration tests
- [ ] E2E tests
- [ ] Manual testing
- [ ] Bug fixes
**Estimated Time**: [e.g., 4 hours]

### Step 5: [Phase name - e.g., Documentation & Deployment]
**Tasks**:
- [ ] Update API documentation
- [ ] Update user documentation
- [ ] Code review
- [ ] Deploy to staging
- [ ] QA testing
- [ ] Deploy to production
**Estimated Time**: [e.g., 2 hours]

---

## 📚 Documentation Requirements

### Code Documentation
- [ ] Inline comments for complex logic
- [ ] Function/method docstrings
- [ ] Type hints/annotations
- [ ] README updates if needed

### API Documentation
- [ ] OpenAPI/Swagger specs updated
- [ ] Example requests/responses
- [ ] Error codes documented

### User Documentation
- [ ] Feature description in user guide
- [ ] Screenshots/videos if relevant
- [ ] FAQ updates
- [ ] In-app help/tooltips

---

## 🐛 Error Handling

### Expected Errors
1. **Error Type**: [e.g., Validation Error]
   - **Trigger**: [what causes this error]
   - **User Message**: [what the user sees]
   - **Handling**: [how it's handled]
   - **Logging**: [what gets logged]

2. **Error Type**: [e.g., Network Error]
   - **Trigger**: [...]
   - **User Message**: [...]
   - **Handling**: [retry logic, fallback]
   - **Logging**: [...]

### Edge Cases
1. [Edge case 1]: [how is this handled]
2. [Edge case 2]: [how is this handled]

---

## 🔄 Rollback Strategy

### Rollback Triggers
- [When should a rollback happen]
- [Which metrics/errors trigger a rollback]

### Rollback Steps
1. [Step 1 - e.g., Revert deployment]
2. [Step 2 - e.g., Rollback database migration]
3. [Step 3 - e.g., Clear caches]

### Data Migration Rollback
- [How to handle data created during the feature]
- [Backward compatibility considerations]

---

## 📊 Success Metrics

### Quantitative Metrics
- **Usage Metrics**:
  - [Metric 1 - e.g., Number of users using feature per day]
  - [Metric 2 - e.g., Conversion rate]

- **Performance Metrics**:
  - [Metric 1 - e.g., Average response time]
  - [Metric 2 - e.g., Error rate]

### Qualitative Metrics
- **User Feedback**: [How is feedback collected]
- **User Satisfaction**: [Survey, NPS, etc.]

### Monitoring & Alerts
- [ ] Setup monitoring for key metrics
- [ ] Configure alerts for error rates
- [ ] Setup performance monitoring
- [ ] Log aggregation for debugging

---

## 🤔 Open Questions

### Technical Questions
1. [Question about implementation detail that's still unclear]
2. [Question about technical choice]

### Design Questions
1. [Question about UI/UX decision]
2. [Question about user flow]

### Business Questions
1. [Question about scope or priority]
2. [Question about edge case handling]

---

## 🔗 References

### Code Examples
- [Link to similar feature in codebase]
- [Link to external code example]
- [Repository with good patterns]

### Documentation
- [Link to library docs]
- [Link to API docs]
- [Link to design system]

### Design References
- [Link to Figma/design]
- [Link to similar UI in other apps]

---

## 💡 Additional Notes

[Space for extra comments, constraints, or important context that doesn't fit in the above sections]

---

## ✅ Completion Checklist

- [ ] Feature description is complete and clear
- [ ] Acceptance criteria are defined
- [ ] Technical specifications are detailed
- [ ] UI/UX is described (with wireframes/mockups if available)
- [ ] API specifications are documented
- [ ] Data model changes are described
- [ ] Security considerations are addressed
- [ ] Performance considerations are documented
- [ ] Testing strategy is detailed
- [ ] Dependencies are identified
- [ ] Implementation plan is created
- [ ] Error handling is described
- [ ] Success metrics are defined
- [ ] Open questions are documented
- [ ] References are added
