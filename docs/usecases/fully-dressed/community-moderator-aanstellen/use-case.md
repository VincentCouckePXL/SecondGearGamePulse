# Fully Dressed Use Case: Aanstellen van een Moderator binnen een Community

**Actors:**
- **Primary Actor:** Community Eigenaar (Gebruiker)
- **Secondary Actor:** Systeem, Geselecteerde Gebruiker

**Pre-conditions:**
- De community-eigenaar is succesvol ingelogd in het systeem.
- De gebruiker heeft de rol van eigenaar in de betreffende community.
- De te promoveren gebruiker is reeds lid van de community.

**Post-conditions:**
- De geselecteerde gebruiker is toegevoegd als moderator binnen de community.
- Het systeem-logboek bevat een record van de wijziging van de rol.
- De nieuwe moderator krijgt toegang tot de moderatiefuncties binnen de community.

**Description:** Een community-eigenaar stelt een bestaande gebruiker aan als moderator binnen zijn community om taken zoals contentbeheer en ledenbeheer te ondersteunen.

**Scenario:**

| Actor Action                                                      | System Response                                                                          |
|-------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| 1. Community-eigenaar navigeert naar de community-instellingen.   | 1. Systeem toont de beheermodule met ledenlijst en roltoewijzingen.                      |
| 2. Eigenaar selecteert de optie “Moderator toevoegen”.            | 2. Systeem toont een lijst van leden die nog geen moderatorrechten hebben.               |
| 3. Eigenaar kiest een gebruiker uit de lijst.                     | 3. Systeem vraagt bevestiging voor de rolwijziging.                                      |
| 4. Eigenaar bevestigt de actie.                                   | 4. Systeem wijzigt de rol van de gebruiker naar “Moderator” en registreert de wijziging. |
| 5. Eigenaar keert terug naar het ledenoverzicht.                  | 5. Systeem toont de bijgewerkte lijst met de nieuwe rolstatus van de gebruiker.          |

**Additional Information:**
- **Goal:** De community-eigenaar kan leden binnen zijn community promoveren tot moderator om moderatietaken te delegeren.
- **Overview:** Deze use case beschrijft het proces waarbij een eigenaar een bestaande gebruiker extra rechten toekent.
- **Cross-References:** ...