# Fully Dressed Use Case: Volgen van een Andere Gebruiker

**Actors:**
- **Primary Actor:** Gebruiker (Volger)
- **Secondary Actor:** Systeem, Doelgebruiker

**Pre-conditions:**
- De gebruiker is succesvol ingelogd in het systeem.
- De doelgebruiker heeft een openbaar profiel of accepteert volgers.
- De volger volgt de doelgebruiker nog niet.

**Post-conditions:**
- De volger volgt de doelgebruiker succesvol.
- De doelgebruiker ontvangt een melding van de nieuwe volger (indien meldingen actief zijn).
- Het systeem-logboek bevat een registratie van de volging.

**Description:** Een gebruiker besluit een andere gebruiker te volgen om op de hoogte te blijven van diens activiteiten, posts of recensies.

**Scenario:**

| Actor Action                                                      | System Response                                                                              |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| 1. Gebruiker navigeert naar het profiel van een andere gebruiker. | 1. Systeem toont het profiel met algemene informatie en de “Volg”-knop.                      |
| 2. Gebruiker klikt op “Volg”.                                     | 2. Systeem controleert of de gebruiker reeds gevolgd wordt.                                  |
| 3. Systeem detecteert dat de gebruiker nog niet gevolgd wordt.    | 3. Systeem registreert de nieuwe volging in de database.                                     |
| 4. Gebruiker ziet bevestiging dat de actie succesvol was.         | 4. Systeem toont “Volgend” status en stuurt optioneel een notificatie naar de doelgebruiker. |
| 5. Gebruiker kan de volging op elk moment ongedaan maken.         | 5. Systeem verwijdert de relatie indien de gebruiker kiest voor “Ontvolgen”.                 |

**Additional Information:**
- **Goal:** Gebruikers kunnen elkaar volgen om interactie en communityvorming te bevorderen.
- **Overview:** Deze use case beschrijft het proces van volgen en ontvolgen tussen gebruikers, inclusief notificatie en statusbeheer.
- **Cross-References:** ...