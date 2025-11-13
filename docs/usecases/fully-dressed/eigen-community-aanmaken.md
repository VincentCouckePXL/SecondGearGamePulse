# Fully Dressed Use Case: Aanmaken van een Eigen Community

**Actors:**
- **Primary Actor:** Gebruiker
- **Secondary Actor:** Systeem

**Preconditions:**
- De gebruiker is succesvol ingelogd in het systeem.
- De gebruiker heeft geen actieve community met dezelfde naam.

**Postconditions:**
- Een nieuwe community is aangemaakt en geregistreerd in het systeem.
- De gebruiker krijgt automatisch de rol van community-eigenaar.
- De community is zichtbaar in het algemene community-overzicht.

**Description:** Een gebruiker maakt een eigen community aan waarin andere gebruikers kunnen deelnemen, posten en interageren.

**Scenario:**

| Actor Action                                          | System Response                                                                                   |
|-------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| 1. Gebruiker navigeert naar de sectie “Communities”.  | 1. Systeem toont een overzicht van bestaande communities en de optie “Nieuwe community maken”.    |
| 2. Gebruiker klikt op “Nieuwe community maken”.       | 2. Systeem toont een formulier voor naam, beschrijving, en privacy-instellingen.                  |
| 3. Gebruiker vult de vereiste velden in en bevestigt. | 3. Systeem valideert de ingevoerde data (unieke naam, verplichte velden).                         |
| 4. Gebruiker bevestigt de creatie.                    | 4. Systeem maakt de community aan, koppelt de gebruiker als eigenaar en toont de communitypagina. |

**Additional Information:**
- **Goal:** Gebruikers kunnen eigen communities aanmaken om specifieke interesses of thema’s te groeperen.
- **Overview:** Deze use case behandelt het proces voor het initiëren van een nieuwe community en de automatische roltoewijzing van eigenaar.
- **Cross References:** UC-AssignModerator, UC-JoinCommunity.
