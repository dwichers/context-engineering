# Feature Requirements Generator (ARG) Template

## 📌 Feature Metadata

**Feature Number**: [Automatisch gegenereerd nummer op basis van volgorde]
**Feature Name**: [Korte, beschrijvende naam]
**Priority**: [Critical / High / Medium / Low]
**Estimated Complexity**: [Low / Medium / High / Very High]
**Dependencies**: [Lijst van andere features waar deze feature van afhankelijk is]

---

## 🎯 Feature Overview

### Feature Description
[Gedetailleerde beschrijving van wat deze feature doet en waarom het belangrijk is]

### User Story
**As a** [type gebruiker]
**I want** [actie/functionaliteit]
**So that** [voordeel/resultaat]

### Business Value
[Waarom is deze feature belangrijk voor het product/business?]

---

## ✅ Acceptance Criteria

### Functionele Requirements
- [ ] [Criterium 1 - wat moet de feature kunnen doen]
- [ ] [Criterium 2]
- [ ] [Criterium 3]
- [ ] [Criterium 4]

### Non-functionele Requirements
- [ ] [Performance requirement - bijvoorbeeld: response time < 200ms]
- [ ] [Security requirement]
- [ ] [Accessibility requirement]
- [ ] [Usability requirement]

---

## 🔧 Technical Specifications

### Affected Components

#### Frontend Components
- **Component 1**: [Naam van component en wat het doet]
  - Location: [filepath waar het moet komen]
  - Responsibility: [wat doet dit component]
  - Dependencies: [andere components die het gebruikt]

- **Component 2**: [Naam en beschrijving]
  - Location: [filepath]
  - Responsibility: [...]
  - Dependencies: [...]

#### Backend Components
- **API Endpoint 1**: [bijvoorbeeld: POST /api/users/register]
  - Location: [filepath waar het moet komen]
  - Responsibility: [wat doet deze endpoint]
  - Request Schema: [beschrijf input]
  - Response Schema: [beschrijf output]

- **Service/Business Logic**: [Naam van service]
  - Location: [filepath]
  - Responsibility: [wat doet deze service]

#### Database Changes
- **New Tables**:
  - `table_name`: [beschrijving van nieuwe tabel]
    - Columns: [lijst van kolommen met types]
    - Indexes: [welke indexes]
    - Relationships: [foreign keys, etc.]

- **Modified Tables**:
  - `existing_table`: [welke wijzigingen]
    - Add columns: [nieuwe kolommen]
    - Modify columns: [gewijzigde kolommen]
    - Add indexes: [nieuwe indexes]

- **Migrations**:
  - [Beschrijf migratie strategie]

---

## 🎨 UI/UX Specifications

### User Interface Elements
- **New Pages/Views**:
  1. [Pagina naam]: [beschrijving van layout en componenten]
  2. [Pagina naam]: [beschrijving]

- **Modified Pages/Views**:
  1. [Bestaande pagina]: [wat wordt er gewijzigd]

### User Flow
```
[Beschrijf de stappen die een gebruiker doorloopt]
1. Gebruiker klikt op [...]
2. Systeem toont [...]
3. Gebruiker vult [...] in
4. Systeem valideert en [...]
5. Gebruiker ziet [...]
```

### Wireframes/Mockups
- [Link naar Figma/design tool]
- [Screenshot of beschrijving van UI]
- [Interactie patterns die gevolgd moeten worden]

### Design Patterns te Volgen
- [Referentie naar bestaande componenten uit de codebase]
- [Design system guidelines]
- [Accessibility patterns]

---

## 🔌 API Specifications

### New Endpoints

#### Endpoint 1
```yaml
Method: POST
Path: /api/v1/resource
Description: [Wat doet deze endpoint]

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
[Herhaal bovenstaande structuur]

### Modified Endpoints
- **Endpoint**: [welke endpoint wordt aangepast]
  - Changes: [wat verandert er]
  - Backward Compatibility: [is het backward compatible?]
  - Deprecation Strategy: [indien van toepassing]

---

## 📊 Data Model

### New Models/Entities

#### Model 1: [ModelName]
```python
# Voorbeeld voor Python/SQLAlchemy
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
[Herhaal structuur]

### Modified Models
- **Model Name**: [welke wijzigingen]
  - New fields: [...]
  - Modified fields: [...]
  - Removed fields: [... met migratie strategie]

### Validation Rules
- `field1`: [validatie regels - bijvoorbeeld: required, min length 3, max length 50]
- `field2`: [validatie regels - bijvoorbeeld: must be positive integer]
- `field3`: [validatie regels - bijvoorbeeld: valid email format]

---

## 🔒 Security Considerations

### Authentication & Authorization
- **Who can access this feature?**: [Welke rollen/gebruikers]
- **Permission checks needed**: [Welke checks op welke niveau]
- **Sensitive data**: [Welke data moet extra beschermd worden]

### Input Validation
- [ ] All user inputs are validated
- [ ] SQL injection prevention
- [ ] XSS prevention
- [ ] CSRF protection (voor state-changing operations)

### Data Protection
- [ ] Encryption at rest: [welke data]
- [ ] Encryption in transit: [HTTPS, TLS]
- [ ] PII handling: [personal identifiable information]
- [ ] Audit logging: [wat moet gelogd worden]

---

## 📈 Performance Considerations

### Expected Load
- **Concurrent Users**: [aantal verwachte simultane gebruikers]
- **Requests per Second**: [verwachte RPS]
- **Data Volume**: [hoeveel data wordt verwerkt]

### Performance Targets
- **API Response Time**: [bijvoorbeeld: p95 < 200ms]
- **Page Load Time**: [bijvoorbeeld: < 2 seconden]
- **Database Query Time**: [bijvoorbeeld: < 50ms]

### Optimization Strategies
- [ ] Database indexing strategy
- [ ] Caching strategy (Redis, CDN, etc.)
- [ ] Pagination for large datasets
- [ ] Lazy loading voor UI
- [ ] Query optimization
- [ ] Background jobs voor heavy operations

---

## 🧪 Testing Strategy

### Unit Tests
- **Coverage Target**: [bijvoorbeeld: > 80%]
- **Key Test Cases**:
  1. [Test case beschrijving - happy path]
  2. [Test case - edge case]
  3. [Test case - error handling]

### Integration Tests
- **Test Scenarios**:
  1. [End-to-end scenario 1]
  2. [Integration met external service]
  3. [Database operations]

### E2E Tests
- **User Flows to Test**:
  1. [Complete user journey 1]
  2. [Complete user journey 2]

### Manual Test Cases
1. [Test case 1]: [stappen om handmatig te testen]
2. [Test case 2]: [stappen]

---

## 🔗 Dependencies & Integration

### Internal Dependencies
- **Features**: [Lijst van andere features die eerst geïmplementeerd moeten zijn]
  - Feature #[nummer]: [waarom is dit een dependency]

- **Components**: [Bestaande componenten die gebruikt worden]
  - Component naam: [filepath en hoe het gebruikt wordt]

### External Dependencies
- **Libraries/Packages**:
  - `package-name@version`: [waarom nodig, wat doet het]
  - `package-name@version`: [beschrijving]

- **APIs/Services**:
  - [Service naam]: [wat wordt er mee gedaan]
  - API Documentation: [link]
  - Rate Limits: [indien van toepassing]

### Breaking Changes
- [ ] Geen breaking changes
- [ ] Breaking changes met migratie pad:
  - [Beschrijf breaking change en hoe te migreren]

---

## 🚀 Implementation Plan

### Step 1: [Fase naam - bijvoorbeeld: Database Setup]
**Tasks**:
- [ ] Create migration for new tables
- [ ] Add indexes
- [ ] Test migration locally
**Estimated Time**: [bijvoorbeeld: 2 uur]

### Step 2: [Fase naam - bijvoorbeeld: Backend Implementation]
**Tasks**:
- [ ] Create data models/schemas
- [ ] Implement business logic
- [ ] Create API endpoints
- [ ] Add validation
- [ ] Write unit tests
**Estimated Time**: [bijvoorbeeld: 1 dag]

### Step 3: [Fase naam - bijvoorbeeld: Frontend Implementation]
**Tasks**:
- [ ] Create UI components
- [ ] Implement state management
- [ ] Add API integration
- [ ] Add form validation
- [ ] Write component tests
**Estimated Time**: [bijvoorbeeld: 1 dag]

### Step 4: [Fase naam - bijvoorbeeld: Integration & Testing]
**Tasks**:
- [ ] Integration tests
- [ ] E2E tests
- [ ] Manual testing
- [ ] Bug fixes
**Estimated Time**: [bijvoorbeeld: 4 uur]

### Step 5: [Fase naam - bijvoorbeeld: Documentation & Deployment]
**Tasks**:
- [ ] Update API documentation
- [ ] Update user documentation
- [ ] Code review
- [ ] Deploy to staging
- [ ] QA testing
- [ ] Deploy to production
**Estimated Time**: [bijvoorbeeld: 2 uur]

---

## 📚 Documentation Requirements

### Code Documentation
- [ ] Inline comments voor complexe logic
- [ ] Function/method docstrings
- [ ] Type hints/annotations
- [ ] README updates indien nodig

### API Documentation
- [ ] OpenAPI/Swagger specs updated
- [ ] Example requests/responses
- [ ] Error codes documented

### User Documentation
- [ ] Feature beschrijving in user guide
- [ ] Screenshots/video's indien relevant
- [ ] FAQ updates
- [ ] In-app help/tooltips

---

## 🐛 Error Handling

### Expected Errors
1. **Error Type**: [bijvoorbeeld: Validation Error]
   - **Trigger**: [wat veroorzaakt deze error]
   - **User Message**: [wat ziet de gebruiker]
   - **Handling**: [hoe wordt het afgehandeld]
   - **Logging**: [wat wordt er gelogd]

2. **Error Type**: [bijvoorbeeld: Network Error]
   - **Trigger**: [...]
   - **User Message**: [...]
   - **Handling**: [retry logic, fallback]
   - **Logging**: [...]

### Edge Cases
1. [Edge case 1]: [hoe wordt dit afgehandeld]
2. [Edge case 2]: [hoe wordt dit afgehandeld]

---

## 🔄 Rollback Strategy

### Rollback Triggers
- [Wanneer moet er een rollback gebeuren]
- [Welke metrics/errors triggeren een rollback]

### Rollback Steps
1. [Stap 1 - bijvoorbeeld: Revert deployment]
2. [Stap 2 - bijvoorbeeld: Rollback database migration]
3. [Stap 3 - bijvoorbeeld: Clear caches]

### Data Migration Rollback
- [Hoe om te gaan met data die tijdens de feature is aangemaakt]
- [Backward compatibility overwegingen]

---

## 📊 Success Metrics

### Quantitative Metrics
- **Usage Metrics**:
  - [Metric 1 - bijvoorbeeld: Number of users using feature per day]
  - [Metric 2 - bijvoorbeeld: Conversion rate]

- **Performance Metrics**:
  - [Metric 1 - bijvoorbeeld: Average response time]
  - [Metric 2 - bijvoorbeeld: Error rate]

### Qualitative Metrics
- **User Feedback**: [Hoe wordt feedback verzameld]
- **User Satisfaction**: [Survey, NPS, etc.]

### Monitoring & Alerts
- [ ] Setup monitoring voor key metrics
- [ ] Configure alerts voor error rates
- [ ] Setup performance monitoring
- [ ] Log aggregation voor debugging

---

## 🤔 Open Questions

### Technical Questions
1. [Vraag over implementatie detail dat nog onduidelijk is]
2. [Vraag over technische keuze]

### Design Questions
1. [Vraag over UI/UX beslissing]
2. [Vraag over user flow]

### Business Questions
1. [Vraag over scope of prioriteit]
2. [Vraag over edge case handling]

---

## 🔗 References

### Code Examples
- [Link naar vergelijkbare feature in codebase]
- [Link naar external code example]
- [Repository met goede patterns]

### Documentation
- [Link naar library docs]
- [Link naar API docs]
- [Link naar design system]

### Design References
- [Link naar Figma/design]
- [Link naar vergelijkbare UI in andere apps]

---

## 💡 Additional Notes

[Ruimte voor extra opmerkingen, constraints, of belangrijke context die niet in bovenstaande secties past]

---

## ✅ Completion Checklist

- [ ] Feature beschrijving is compleet en duidelijk
- [ ] Acceptance criteria zijn gedefinieerd
- [ ] Technical specifications zijn uitgewerkt
- [ ] UI/UX is beschreven (met wireframes/mockups indien beschikbaar)
- [ ] API specifications zijn gedocumenteerd
- [ ] Data model wijzigingen zijn beschreven
- [ ] Security considerations zijn geadresseerd
- [ ] Performance considerations zijn gedocumenteerd
- [ ] Testing strategy is uitgewerkt
- [ ] Dependencies zijn geïdentificeerd
- [ ] Implementation plan is gemaakt
- [ ] Error handling is beschreven
- [ ] Success metrics zijn gedefinieerd
- [ ] Open vragen zijn gedocumenteerd
- [ ] References zijn toegevoegd
