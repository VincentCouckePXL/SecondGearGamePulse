# Gekozen Technologie

## Overzicht
Voor het **GamePulse**-project is gekozen voor een moderne, schaalbare en onderhoudbare technologie-stack die geschikt is voor data-intensieve webapplicaties. De gekozen technologieën ondersteunen **snelle ontwikkeling**, **herbruikbare componenten** en **goede integratie met externe API’s**. Zowel front-end als back-end worden modulair opgebouwd, zodat toekomstige uitbreidingen eenvoudig kunnen worden geïmplementeerd.

---

## Front-end

De front-end wordt ontwikkeld als **webapplicatie** in **TypeScript**, omdat:
- TypeScript statische typecontrole biedt, waardoor fouten vroegtijdig kunnen worden opgespoord.
- De codebasis beter onderhoudbaar en schaalbaarder is in vergelijking met puur JavaScript.

Er wordt gekozen voor een **component-gebaseerd framework**.  
**Voorkeursframework:** **React**  
**Alternatieven:** Vue.js of Angular

### Motivatie
- **React** biedt een declaratieve aanpak en een grote community met rijke bibliotheken.
- **Herbruikbare UI-componenten** maken consistente ontwikkeling mogelijk.
- **Integratie met RESTful API’s** en moderne tools zoals Redux of React Query maakt het eenvoudig om dynamische data op te halen en te beheren.
- **Responsieve lay-out** via CSS-frameworks (Tailwind CSS of Bootstrap) om ondersteuning te bieden voor meerdere schermformaten.

---

## Back-end

De back-end wordt ontwikkeld in **Java**, gebruikmakend van **Spring Boot** als kernframework.

### Motivatie
- **Spring Boot** biedt een robuust ecosysteem voor REST API’s, beveiliging en database-integratie.
- Ondersteunt **Object Georiënteerde Ontwikkeling** en **Dependency Injection**, wat zorgt voor duidelijke modulair gestructureerde code.
- **Uitbreidbaarheid:** eenvoudig om nieuwe microservices of modules toe te voegen zonder impact op bestaande functionaliteit.
- **Betrouwbaarheid:** Java is stabiel, volwassen en veelgebruikt in enterprise-omgevingen.

### Mogelijke componenten
- **Spring Web:** voor RESTful API’s
- **Spring Security:** voor authenticatie en autorisatie
- **Spring Data JPA:** voor database-interactie (met PostgreSQL of MySQL)
- **JUnit & Mockito:** voor unit- en integratietests

---

## Database

De applicatie maakt gebruik van een **relationele database** (voorkeur: **PostgreSQL**) vanwege:
- Sterke ondersteuning voor complexe query’s en data-integriteit.
- Open-source karakter en goede compatibiliteit met Java/Spring.
- Mogelijkheid tot uitbreiden met JSONB-velden voor semi-gestructureerde data (bijvoorbeeld externe API-resultaten).

---

## Projectmanagement

Het ontwikkelproces volgt een **Agile-aanpak** met iteratieve opleveringen en korte feedbackcycli.

### Tools
- **Trello** voor backlogbeheer, sprintplanning en Kanban-bordvisualisatie.
- **GitHub** of **GitLab** voor versiebeheer, code reviews en issue tracking.
- **Markdown-documentatie** binnen de repository voor transparante kennisdeling.

---

## Versiebeheer

Versiebeheer gebeurt met **Git**.
- Elke feature of bugfix wordt ontwikkeld in een aparte branch.
- **Pull requests** worden gebruikt voor review en integratie.
- **Release tags** worden toegepast per iteratie (`iteratie1`, `iteratie2`, …).
- Branch naming conventies en commit messages volgen vaste richtlijnen voor consistentie.