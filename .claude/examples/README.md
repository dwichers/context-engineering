# Examples Directory

This directory is intended for **code examples, UI components, frameworks, templates and repositories** that you want to use as references or inspiration for your project.

## 📁 What can you place here?

### 1. Code Examples
- Code snippets you have found
- Implementation patterns die je wilt volgen
- Best practice voorbeelden

### 2. UI Component Libraries
- Downloaded UI component templates
- Design system examples
- Component code van andere projecten

### 3. Framework Templates
- Starter templates for your tech stack
- Boilerplate code
- Project structure examples

### 4. Repository Clones
- Clone complete repositories with good patterns
- Example projects with similar features
- Reference implementations

### 5. Design Assets
- Wireframes
- Mockups
- Design system documentation
- UI/UX patterns

## 🎯 How to use?

### When making Initial ARG
In your Initial ARG document, refer to examples here:
```markdown
## References & Inspiratie

### Repository Voorbeelden
- examples/[repo-name]/ - Goede project structure voor [framework]

### UI Components
- examples/ui-components/ - Component library patterns
```

### When generating PRPs
The AI will automatically scan this directory for relevant patterns and examples that match your tech stack.

### When implementing
Refer to specific files:
```python
# PATTERN: Follow examples/auth-example/auth.py
```

## 📝 Structure Suggestions

```
.claude/examples/
├── ui-components/           # UI component examples
│   ├── buttons/
│   ├── forms/
│   └── layouts/
├── auth-patterns/          # Authentication examples
│   ├── jwt-example/
│   └── oauth-example/
├── api-patterns/           # API design patterns
│   ├── rest-api/
│   └── graphql/
├── database-patterns/      # Database schemas
│   ├── migrations/
│   └── models/
├── testing-patterns/       # Test examples
│   ├── unit-tests/
│   └── integration-tests/
└── frameworks/             # Framework-specific examples
    ├── fastapi-starter/
    ├── react-template/
    └── nextjs-boilerplate/
```

## ⚠️ Important

- **Licenses**: Be aware of licenses when copying code
- **Attribution**: Document where code comes from
- **Updates**: Keep examples up-to-date with your project requirements
- **Cleanup**: Remove examples that are no longer relevant

## 💡 Tips

1. **Organiseer per category**: Make subdirectories per type example
2. **Add README's**: Explain why each example is useful
3. **Highlight key patterns**: Mark the most important parts to copy
4. **Version awareness**: Note version numbers of frameworks/libraries

## 🔗 External Resources

If you don't want to clone the entire repository, you can also add links to:
- GitHub repositories
- Documentation sites
- Blog posts with examples
- Video tutorials
- Design inspiration (Dribbble, Behance)

Add these links to your ARG documents under the "References" section.
