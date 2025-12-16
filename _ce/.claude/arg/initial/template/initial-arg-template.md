# Initial Application Requirements Generator (ARG) Template

## 📋 Project Overview

### Project Name
[Name of the application/website]

### Project Type
- [ ] Web Application
- [ ] Mobile Application
- [ ] Desktop Application
- [ ] API/Backend Service
- [ ] Full-stack Application
- [ ] Other: ___________

### Brief Description
[Short description of the idea in 2-3 sentences]

---

## 🎯 Main Goal & Problem

### What is the main goal of this application?
[Describe the primary objective and what you want to achieve]

### What problem does it solve?
[Describe the problem users experience and how this solves it]

### Who is this application for?
[Describe the target audience(s)]

---

## 🔧 Technical Stack

### Frontend
- **Framework/Library**: [e.g., React, Vue, Angular, Svelte, Next.js]
- **Styling**: [e.g., Tailwind CSS, styled-components, SCSS, CSS Modules]
- **State Management**: [e.g., Redux, Zustand, Context API, Pinia]
- **UI Component Library**: [e.g., shadcn/ui, Material-UI, Ant Design, custom]
- **Build Tool**: [e.g., Vite, Webpack, Turbopack]

### Backend
- **Framework**: [e.g., FastAPI, Django, Express.js, NestJS, Flask]
- **Database**: [e.g., PostgreSQL, MongoDB, MySQL, SQLite, Supabase]
- **ORM/ODM**: [e.g., Prisma, SQLAlchemy, Mongoose, Drizzle]
- **Authentication**: [e.g., JWT, OAuth2, Auth0, Supabase Auth, NextAuth]
- **API Type**: [e.g., REST, GraphQL, tRPC, gRPC]

### Infrastructure & Deployment
- **Hosting Frontend**: [e.g., Vercel, Netlify, CloudFlare Pages]
- **Hosting Backend**: [e.g., Railway, Render, AWS, DigitalOcean]
- **CI/CD**: [e.g., GitHub Actions, GitLab CI, Jenkins]
- **Containerization**: [e.g., Docker, Docker Compose, Kubernetes]

### Additional Services
- **File Storage**: [e.g., AWS S3, Cloudinary, Supabase Storage]
- **Email Service**: [e.g., SendGrid, Mailgun, Resend]
- **Analytics**: [e.g., Google Analytics, Plausible, Mixpanel]
- **Monitoring**: [e.g., Sentry, LogRocket, DataDog]

---

## 📦 Core Functionalities

### Essential Features (Must-have)
1. [Feature 1 - describe what it does and why it's essential]
2. [Feature 2]
3. [Feature 3]
...

### Important Features (Should-have)
1. [Feature 1 - describe what it does]
2. [Feature 2]
...

### Optional Features (Nice-to-have)
1. [Feature 1 - describe what it does]
2. [Feature 2]
...

---

## 👥 User Roles & Permissions

### Roles
- **[Role 1]**: [Description of this role and what they can do]
- **[Role 2]**: [Description of this role and what they can do]

### Permission Matrix
| Feature/Action | Role 1 | Role 2 | Role 3 |
|----------------|--------|--------|--------|
| [Action 1]     | ✅     | ✅     | ❌     |
| [Action 2]     | ✅     | ❌     | ❌     |

---

## 🎨 UI/UX Design

### Design System
- **Color Scheme**: [e.g., Dark mode, Light mode, Custom theme]
- **Typography**: [e.g., Inter, Roboto, System fonts]
- **Design Inspiration**: [Links to examples, Dribbble, Behance, existing apps]

### Layout & Navigation
- **Navigation Type**: [e.g., Sidebar, Top navbar, Bottom tabs, Drawer]
- **Responsive Design**: [Describe mobile-first approach or desktop-first]
- **Key Pages/Views**:
  1. [Page 1 - describe layout and components]
  2. [Page 2]
  ...

### References & Examples
- [Link to design mockups if available]
- [Link to similar applications]
- [Screenshots or wireframes if available]

---

## 🔌 External Integrations & APIs

### Required Integrations
1. **[Service Name]**: [Why needed, what it does]
   - API Documentation: [Link]
   - Authentication Method: [API Key, OAuth, etc.]

2. **[Service Name]**: [Description]
   - API Documentation: [Link]
   - Authentication Method: [Method]

### Optional Integrations
1. [Integration name and description]

---

## 📊 Data Model & Structure

### Main Entities
1. **[Entity 1 - e.g., User]**
   - Fields: [username, email, password, role, created_at]
   - Relationships: [Has many posts, belongs to organization]

2. **[Entity 2 - e.g., Post]**
   - Fields: [title, content, author_id, status, published_at]
   - Relationships: [Belongs to User, has many Comments]

3. **[Entity 3]**
   - Fields: [...]
   - Relationships: [...]

### Relationships between Entities
```
[Simple diagram or description of relationships]
User (1) -> (N) Posts
Post (1) -> (N) Comments
User (N) <- (N) Organizations (Many-to-Many)
```

---

## 🔒 Security & Compliance

### Security Requirements
- [ ] Input validation & sanitization
- [ ] SQL injection prevention
- [ ] XSS protection
- [ ] CSRF protection
- [ ] Rate limiting
- [ ] Data encryption (at rest / in transit)
- [ ] Secure password hashing

### Compliance
- [ ] GDPR compliance
- [ ] Cookie consent
- [ ] Privacy policy
- [ ] Terms of service
- [ ] Data retention policy

---

## 📈 Performance & Scalability

### Performance Targets
- **Page Load Time**: [e.g., < 2 seconds]
- **API Response Time**: [e.g., < 200ms for 95th percentile]
- **Concurrent Users**: [e.g., 1000 simultaneous users]

### Scalability Considerations
- [How should the app scale? Horizontal/Vertical]
- [Database sharding needed?]
- [CDN usage?]
- [Caching strategy?]

---

## 🧪 Testing & Quality

### Testing Strategy
- [ ] Unit Tests (coverage target: __%)
- [ ] Integration Tests
- [ ] E2E Tests (tool: ____________)
- [ ] Performance Tests
- [ ] Security Tests

### Quality Standards
- [Code quality tools: ESLint, Prettier, Ruff, etc.]
- [Type checking: TypeScript, mypy, etc.]
- [Documentation requirements]

---

## 📱 Platforms & Devices

### Supported Platforms
- [ ] Web (Desktop)
- [ ] Web (Mobile)
- [ ] iOS Native App
- [ ] Android Native App
- [ ] Progressive Web App (PWA)

### Browser Support
- [ ] Chrome (last 2 versions)
- [ ] Firefox (last 2 versions)
- [ ] Safari (last 2 versions)
- [ ] Edge (last 2 versions)

---

## 🎬 Development Phases

### Phase 1: Foundation (Initial Setup)
- [Project setup & structure]
- [Authentication & Authorization]
- [Database schema & migrations]
- [Basic UI components]
- **Estimated Duration**: [e.g., 2 weeks]

### Phase 2: Core Features
- [Feature 1]
- [Feature 2]
- [Feature 3]
- **Estimated Duration**: [e.g., 4 weeks]

### Phase 3: Advanced Features
- [Feature 4]
- [Feature 5]
- **Estimated Duration**: [e.g., 3 weeks]

### Phase 4: Polish & Launch
- [Testing & bug fixes]
- [Performance optimization]
- [Documentation]
- [Deployment]
- **Estimated Duration**: [e.g., 1 week]

---

## 🚀 Deployment & Operations

### Deployment Strategy
- **Deployment Type**: [e.g., Continuous Deployment, Manual deploys]
- **Environments**: [Development, Staging, Production]
- **Rollback Strategy**: [How to handle failed deploys?]

### Monitoring & Maintenance
- **Uptime Monitoring**: [Tool/Service]
- **Error Tracking**: [Tool/Service]
- **Logging**: [Tool/Service]
- **Backup Strategy**: [How often, where stored]

---

## 📚 Documentation Requirements

### Developer Documentation
- [ ] README with setup instructions
- [ ] API documentation (Swagger/OpenAPI)
- [ ] Architecture decision records (ADRs)
- [ ] Database schema documentation
- [ ] Deployment guide

### User Documentation
- [ ] User guide/manual
- [ ] FAQ
- [ ] Video tutorials
- [ ] In-app help/tooltips

---

## 🤔 Open Questions & Considerations

### Technical Uncertainties
1. [Question about technical choice that is still unclear]
2. [Question about implementation detail]

### Design Uncertainties
1. [Question about UI/UX decision]
2. [Question about user flow]

### Business Uncertainties
1. [Question about feature priority]
2. [Question about budget/timeline]

---

## 🔗 References & Inspiration

### Similar Projects
- [Link to similar project 1 - what can we learn from this?]
- [Link to similar project 2]

### Templates & Starters
- [Link to template/boilerplate that can be used]
- [Link to UI kit]

### Repository Examples
- [Link to GitHub repo showing good patterns]
- [Link to code examples]

---

## 💡 Additional Notes

[Space for extra comments, constraints, or important context that doesn't fit in the above sections]

---

## ✅ Completion Checklist

- [ ] All sections are filled in
- [ ] Technical stack is clearly defined
- [ ] Core features are identified and prioritized
- [ ] Data model is described
- [ ] Security requirements are specified
- [ ] Open questions are documented
- [ ] References and examples are added
- [ ] Document is reviewed and complete
