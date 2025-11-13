###  Fully Dressed Use Case: Blokkeren van een gerapporteerde gebruiker
**Actors:**
- **Primary Actor:** Administrator
- **Secondary Actor:** Systeem

**Pre-conditions:**
- Administrator is succesvol geauthenticeerd in het systeem.
- Er bestaan één of meer rapporten die betrekking hebben op een specifieke gebruiker.
- De gerapporteerde gebruiker is actief en heeft nog toegang tot het platform.

**Post-conditions:**
- De gerapporteerde gebruiker is succesvol geblokkeerd.
- Het rapport dat aanleiding gaf tot de blokkering wordt bijgewerkt naar de status “afgehandeld”.
- Het systeem registreert de blokkering en reden in een moderatie-logboek.
- Wanneer de gebruiker zou willen inloggen heeft de gebruiker enkel toegang tot een appeal page

**Description:** Administrator bekijkt rapporten over een gebruiker en voert een blokkering uit indien de melding gegrond is.
**Scenario:**

| Actor Action                                                                | System Response                                                                                                                                |
|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| 1. Administrator navigeert naar het moderatie-dashboard of rapportbeheer.   | 	1. Systeem toont een overzicht van alle ontvangen rapporten, inclusief rapporterende gebruiker, doelgebruiker, reden en status.               |
| 2. Administrator filtert rapporten op type “gebruiker”.                     | 	2. Systeem toont enkel rapporten die betrekking hebben op gebruikersaccounts.                                                                 |
| 3. Administrator selecteert een specifiek rapport over een gebruiker.       | 	3. Systeem toont de details van het rapport en het profiel van de gerapporteerde gebruiker.                                                   |
| 4. Administrator beoordeelt de inhoud en besluit de gebruiker te blokkeren. | 	4. Systeem vraagt om bevestiging en toont de mogelijke redenen voor blokkering (schending richtlijnen, spam, haatspraak, etc.).               |
| 5. Administrator bevestigt de blokkering en selecteert de reden.            | 	5. Systeem voert de blokkering uit, markeert het gebruikersaccount als “geblokkeerd” en wijzigt de status van het rapport naar “afgehandeld”. |
| 6. Administrator keert terug naar het overzicht.                            | 	6. Systeem toont de bijgewerkte rapportlijst met geüpdatete statusinformatie.                                                                 |

**Additional information**
- **Goal:** De administrator kan, op basis van gebruikersrapporten, een gebruiker blokkeren die de platformrichtlijnen overtreedt.
- **Overview:** Deze use case beschrijft het proces waarin een administrator een gerapporteerde gebruiker beoordeelt en, indien nodig, blokkeert. Het systeem registreert de actie en werkt de status van het rapport automatisch bij.
- **Cross References:** ...

