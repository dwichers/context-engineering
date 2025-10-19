# Generate Initial ARG Document

Genereer een gestructureerd Initial ARG (Application Requirements Generator) document op basis van het idee van de gebruiker.

## User Input: $ARGUMENTS

Dit bevat de beschrijving van het applicatie/website idee.

---

## Process

### Step 1: Begrijp het Idee

Lees de gebruikersinput en identificeer:
- Wat wil de gebruiker bouwen?
- Welke problemen lost het op?
- Wie is de doelgroep?
- Zijn er al technische voorkeuren genoemd?

### Step 2: Interactieve Vragenronde

Stel gerichte vragen om een compleet beeld te krijgen. Gebruik de template `_ce/arg/initial/template/initial-arg-template.md` als leidraad voor welke informatie nodig is.

**Belangrijke vraaggebieden**:

1. **Project Scope & Goals**
   - Wat is het hoofddoel?
   - Welk probleem lost dit op?
   - Wie zijn de eindgebruikers?
   - Wat zijn de must-have features vs nice-to-have?

2. **Technical Stack Preferences**
   - Frontend: Heeft de gebruiker voorkeur voor React, Vue, Svelte, Next.js?
   - Backend: Python (FastAPI, Django), Node.js (Express, NestJS)?
   - Database: PostgreSQL, MongoDB, MySQL?
   - Hosting: Vercel, AWS, Railway?
   - Heeft de gebruiker al ervaring met bepaalde technologieën?

3. **UI/UX Verwachtingen**
   - Zijn er design voorbeelden of inspiratie?
   - Welke styling approach (Tailwind, CSS-in-JS, component library)?
   - Dark mode ondersteuning?
   - Mobile-first of desktop-first?

4. **Features & Functionaliteit**
   - Welke core features zijn absoluut noodzakelijk?
   - Welke features kunnen later toegevoegd worden?
   - Zijn er gebruikersrollen (admin, user, etc.)?
   - Welke integraties zijn nodig (APIs, payment, etc.)?

5. **Data & Storage**
   - Wat voor data moet opgeslagen worden?
   - Zijn er relaties tussen data entities?
   - Hoeveel gebruikers/data volume verwacht?

6. **Security & Compliance**
   - Welke security requirements?
   - Privacy vereisten (GDPR)?
   - User authentication nodig?

7. **Timeline & Resources**
   - Wat is de gewenste timeline?
   - Wordt dit een MVP of volledige applicatie?
   - Zijn er budget constraints?

**Strategie voor vragen stellen**:
- Stel 3-5 vragen per ronde
- Maak vragen specifiek en actionable
- Bied multiple choice waar mogelijk (maar sta andere input toe)
- Gebruik AskUserQuestion tool voor gestructureerde vragen
- Itereer totdat je genoeg informatie hebt

### Step 3: Verwerk Antwoorden

Na elke vragenronde:
1. Verwerk de antwoorden in je begrip van het project
2. Identificeer gaps in informatie
3. Stel volgende ronde vragen indien nodig
4. Herhaal totdat je een compleet beeld hebt

### Step 4: Genereer ARG Document

Wanneer je voldoende informatie hebt:

1. **Lees de template**:
   ```bash
   Read _ce/arg/initial/template/initial-arg-template.md
   ```

2. **Vul alle secties in** met de verzamelde informatie:
   - Project Overview (naam, type, beschrijving)
   - Hoofddoel & Probleem
   - Technische Stack (volledig gespecificeerd)
   - Core Functionaliteiten (geprioriteerd)
   - Gebruikersrollen & Permissies
   - UI/UX Design (met referenties)
   - Externe Integraties
   - Data Model
   - Security & Compliance
   - Performance & Scalability
   - Testing & Quality
   - Platforms & Devices
   - Development Phases
   - Deployment & Operations
   - Documentation Requirements
   - Open Questions (voor dingen die nog onduidelijk zijn)
   - References & Inspiratie

3. **Genereer bestandsnaam**:
   - Format: `YYYY-MM-DD-[project-naam]-initial-arg.md`
   - Bijvoorbeeld: `2024-03-15-ecommerce-platform-initial-arg.md`

4. **Sla op in juiste locatie**:
   ```
   _ce/arg/initial/[generated-filename].md
   ```

### Step 5: Review & Confirmation

1. Toon een samenvatting van het gegenereerde document
2. Highlight eventuele open vragen of aannames
3. Vraag of de gebruiker tevreden is of aanpassingen wil

### Step 6: Next Steps Guidance

Informeer de gebruiker over de volgende stappen:
```
✅ Initial ARG document gegenereerd: _ce/arg/initial/[filename].md

Volgende stappen:
1. Review het document en vul eventuele open vragen in
2. Genereer een Initial PRP met: /generate-initial-prp _ce/arg/initial/[filename].md
3. Voer het Initial PRP uit met: /execute-initial _ce/prp/initial/[prp-filename].md
```

---

## Important Guidelines

### DO:
- ✅ Stel gerichte, specifieke vragen
- ✅ Gebruik AskUserQuestion voor multiple choice vragen
- ✅ Itereer totdat je een compleet beeld hebt
- ✅ Vul ALLE secties van de template in (gebruik "TBD" voor echt onbekende info)
- ✅ Prioriteer features (must-have vs nice-to-have)
- ✅ Documenteer aannames duidelijk
- ✅ Geef realistische schattingen voor development phases
- ✅ Denk aan security en performance vanaf het begin

### DON'T:
- ❌ Genereer geen document zonder voldoende informatie
- ❌ Maak geen aannames zonder deze te documenteren
- ❌ Sla geen belangrijke secties over
- ❌ Kies geen technologieën zonder input van gebruiker
- ❌ Negeer geen security of performance overwegingen
- ❌ Creëer geen onrealistische timeline verwachtingen

---

## Example Interaction Flow

```
User: /initial "Ik wil een task management app bouwen"

AI: Interessant! Laat me je wat vragen stellen om een goed beeld te krijgen:

[Gebruikt AskUserQuestion tool]
Question 1: "Wat is het hoofddoel van deze task management app?"
Options:
  - Personal productivity (individuele gebruikers)
  - Team collaboration (teams/bedrijven)
  - Both (zowel persoonlijk als team gebruik)

Question 2: "Heb je voorkeur voor een frontend framework?"
Options:
  - React + Next.js
  - Vue + Nuxt
  - Svelte + SvelteKit
  - Anders (specificeer)

Question 3: "Welke backend technologie spreekt je aan?"
Options:
  - Python (FastAPI)
  - Node.js (Express/NestJS)
  - Geen voorkeur (stel het beste voor)

[Na antwoorden, volgende ronde vragen over features, data model, etc.]

[Uiteindelijk genereert ARG document]

AI: ✅ Initial ARG document gegenereerd: _ce/arg/initial/2024-03-15-task-management-initial-arg.md

Het document bevat:
- Volledige technical stack specificatie
- 12 core features (8 must-have, 4 nice-to-have)
- Data model met 5 entities
- Security & compliance requirements
- Development phases (estimated 8 weeks)

Open vragen gedocumenteerd:
- Integratie met Google Calendar/Outlook?
- Payment gateway voor premium features?

Volgende stap:
/generate-initial-prp _ce/arg/initial/2024-03-15-task-management-initial-arg.md
```

---

## Quality Checklist

Before generating the final ARG document, ensure:

- [ ] Alle secties van template zijn ingevuld
- [ ] Technical stack is volledig gespecificeerd
- [ ] Features zijn geprioriteerd (must/should/nice-to-have)
- [ ] Data model is beschreven met relaties
- [ ] Security requirements zijn gespecificeerd
- [ ] Open vragen zijn gedocumenteerd
- [ ] Development phases hebben realistische estimaties
- [ ] Referenties en inspiratie zijn toegevoegd (indien beschikbaar)
- [ ] Bestandsnaam volgt naming convention
- [ ] Document is opgeslagen in _ce/arg/initial/

---

## Success Criteria

Het /initial commando is succesvol wanneer:

1. ✅ Alle noodzakelijke informatie is verzameld via structured questioning
2. ✅ Een compleet ARG document is gegenereerd volgens template
3. ✅ Het document bevat voldoende detail voor PRP generatie
4. ✅ Open vragen en aannames zijn duidelijk gedocumenteerd
5. ✅ Gebruiker begrijpt de volgende stappen

---

**Remember**: De kwaliteit van het Initial ARG document bepaalt de kwaliteit van het hele project. Neem de tijd om alle informatie goed te verzamelen!