# Examples Directory

Deze directory is bedoeld voor **code voorbeelden, UI componenten, frameworks, templates en repository's** die je wilt gebruiken als referentie of inspiratie voor je project.

## 📁 Wat kun je hier plaatsen?

### 1. Code Voorbeelden
- Code snippets die je hebt gevonden
- Implementation patterns die je wilt volgen
- Best practice voorbeelden

### 2. UI Component Libraries
- Downloaded UI component templates
- Design system examples
- Component code van andere projecten

### 3. Framework Templates
- Starter templates voor je tech stack
- Boilerplate code
- Project structure examples

### 4. Repository Clones
- Kloon complete repositories met goede patterns
- Example projecten met vergelijkbare features
- Reference implementations

### 5. Design Assets
- Wireframes
- Mockups
- Design system documentation
- UI/UX patterns

## 🎯 Hoe te gebruiken?

### Bij het maken van Initial ARG
In je Initial ARG document, refereer naar voorbeelden hier:
```markdown
## References & Inspiratie

### Repository Voorbeelden
- _ce/examples/[repo-name]/ - Goede project structure voor [framework]

### UI Components
- _ce/examples/ui-components/ - Component library patterns
```

### Bij het genereren van PRPs
De AI zal automatisch deze directory scannen voor relevante patterns en voorbeelden die passen bij je tech stack.

### Bij het implementeren
Refereer naar specifieke files:
```python
# PATTERN: Follow _ce/examples/auth-example/auth.py
```

## 📝 Structuur Suggesties

```
_ce/examples/
├── ui-components/           # UI component voorbeelden
│   ├── buttons/
│   ├── forms/
│   └── layouts/
├── auth-patterns/          # Authentication voorbeelden
│   ├── jwt-example/
│   └── oauth-example/
├── api-patterns/           # API design patterns
│   ├── rest-api/
│   └── graphql/
├── database-patterns/      # Database schemas
│   ├── migrations/
│   └── models/
├── testing-patterns/       # Test voorbeelden
│   ├── unit-tests/
│   └── integration-tests/
└── frameworks/             # Framework-specific examples
    ├── fastapi-starter/
    ├── react-template/
    └── nextjs-boilerplate/
```

## ⚠️ Belangrijk

- **Licenties**: Let op licenties bij het kopiëren van code
- **Attributie**: Documenteer waar code vandaan komt
- **Updates**: Houd voorbeelden up-to-date met je project requirements
- **Cleanup**: Verwijder voorbeelden die niet meer relevant zijn

## 💡 Tips

1. **Organiseer per category**: Maak subdirectories per type voorbeeld
2. **Voeg README's toe**: Leg uit waarom elk voorbeeld nuttig is
3. **Highlight key patterns**: Markeer de belangrijkste parts om te kopiëren
4. **Version awareness**: Noteer versie nummers van frameworks/libraries

## 🔗 Externe Resources

Als je niet de hele repository wilt clonen, kun je ook links toevoegen aan:
- GitHub repositories
- Documentation sites
- Blog posts met voorbeelden
- Video tutorials
- Design inspiration (Dribbble, Behance)

Voeg deze links toe in je ARG documenten onder de "References" sectie.
