###  Fully Dressed Use Case: Bekijken van gerapporteerde content
**Actors:**
- **Primary Actor:** Administrator
- **Secondary Actor:** Systeem

**Pre-conditions:**
- Administrator is succesvol geauthenticeerd in het systeem.
- Er bestaat één of meer meldingen (rapporten) die door gebruikers zijn ingediend.
- De gerapporteerde content (berichten, review of gebruiker) is nog beschikbaar in het systeem.

**Post-conditions:**
- Administrator heeft de details van één of meerdere rapporten bekeken.
- De status van een rapport kan worden bijgewerkt (vb: "niet geopend", "in behandeling", "afgehandeld")
- Het systeem registreert de beoordeling of actie van de administrator in een moderatie-logboek

**Description:** Admin bekijkt de rapports die gemaakt zijn door de gebruikers

**Scenario:**

| Actor Action                                                                                                                     | System Response                                                                                                                       |
|----------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| 1. Administrator navigeert naar het moderatie-dashboard of rapportbeheer                                                         | 1. Systeem toont een overzichtspagina van alle ontvangen rapporten, inclusief datum, rapporterende gebruiker, type content, en status |
| 2. Administrator selecteert filtercriteria (datum, type content, reden voor rapportering, ...)                                   | 2. Systeem past de filters toe en vernieuwt de pagina met overeenkomennde meldingen.                                                  |
| 3. Administrator kiest een specifiek rapport uit de lijst.                                                                       | 3. Systeem laadt de inhoud van het geselecteerde rapport.                                                                             |
| 4. Administrator onderneemt actie (verwijderen van review of berichten, blokkeren van gebruiker, markeren als spam rapport, ...) | 4. Systeem voert de gekozen actie uit, wijzigt de status van het rapport en logt de actie.                                            |

**Additional information**
- **Goal:** De administrator kan meldingen van ongepaste of verdachte content beoordelen en passende moderatieacties ondernemen.
- **Overview:** Deze use case beschrijft het proces waarin een administrator gebruikersrapporten over content bekijkt en opvolgt via het moderatiesysteem, met mogelijkheden tot filteren, beoordelen en actie ondernemen.
- **Cross-References:** ...