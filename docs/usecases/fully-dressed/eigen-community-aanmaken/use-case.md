# Fully Dressed Use Case: Aanmaken van een Eigen Community

**Actors:**
- **Primary Actor:** Gebruiker
- **Secondary Actor:** Systeem

**Stakeholders**
- **gebruiker**: Wil een nieuwe community maken om iets te bespreken met andere gebruikers van het platform
- **Andere gebruikers**: Willen duidelijk en relevante communities kunnen vinden.

**Pre-conditions:**
- Gebruiker is succesvol ingelogd in het systeem.
- Er bestaat geen andere community met dezelfde naam
- Gebruiker mag niet geblokeerd zijn door de administrators

**Post-conditions:**
- [Instance creation] Een nieuwe ``Community`` is aangemaakt en opgeslagen in het systeem.
- [Association formed] De ``User`` wordt ingesteld als ``CommunityOwner`` van de ``Community``.
- [Attribute modification] Er wordt een ``ModeratorList<User>`` aangemaakt en de ``CommunityOwner`` wordt hieraan toegevoegd.
- De community is zichtbaar in het algemene community-overzicht.

**Description:** Een gebruiker maakt een eigen community aan waarin andere gebruikers kunnen deelnemen, posten en interageren.

**Trigger:** Gebruiker klikt op "nieuwe community aanmaken"

**Scenario:**

| Actor Action                                                        | System Response                                                                                                               |
|---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| 1. Gebruiker navigeert naar overzichtspagina van game               | 1. Systeem geeft overzichtspagina weer                                                                                        |
| 2. Gebruiker navigeert naar de sectie “Communities”.                | 2. Systeem toont een overzicht van bestaande communities met knoppen “join” en “nieuwe community maken”.                      |
| 3. Gebruiker klikt op “Nieuwe community aanmaken”.                  | 3. Systeem toont een formulier met velden voor naam, beschrijving en regels.                                                  |
| 4. Gebruiker vult de vereiste velden in en bevestigt.               | 4. Systeem valideert de ingevoerde data (unieke naam, verplichte velden).                                                     |
| 5. Gebruiker vult optionele velden zoals tags en afbeelding.        | 5. Systeem toont real-time feedback zoals “banner geüpload”, “tag toegevoegd”.                                                |
| 6. Gebruiker klikt op “community aanmaken”.                         | 6. Systeem voert server-side validatie uit: unieke naam, verplichte velden, beschrijving ≤ 1500 karakters.                    |
| 7. —                                                                | 7. Systeem koppelt gebruiker automatisch als Eigenaar en Moderator.                                                           |
| 8. —                                                                | 8. Systeem toont bevestigingsscherm: “Community succesvol aangemaakt”. De nieuwe communitypagina opent.                       |
| 9. Gebruiker bekijkt communitypagina.                               | 9. Systeem toont lege community met start opties: leden uitnodigen, regels bewerken, banner instellen, moderators aanstellen. |

**Additional Information:**
**Alternatieve stromen:**

- A3.1: Community naam al in gebruik
  - Systeem detecteert dubbele naam.
  - Systeem toont melding: “Community naam is al in gebruik” met suggesties:
    - <naam>_official
    - <naam>_community
    - <naam>2025
  - Gebruiker kiest andere naam en gaat verder.

- A3.2: Ongeldige community naam
  - Gebruik van verboden tekens of te kort/te lang.
  - Systeem toont specifieke foutmelding zoals:
    - “Naam moet tussen 3 en 50 karakters zijn.”
    - “Speciale tekens niet toegestaan.”

- A0.1: Gebruiker annuleert proces
  - Op elk moment klikt gebruiker Annuleren.
  - Systeem vraagt: “Weet je zeker dat je wilt stoppen?”
  - Indien bevestigd: systeem verwijdert ongeslagen input.

- A3.3: Beschrijving ontbreekt of te lang
  - Systeem toont foutmelding:
    - “Beschrijving mag niet leeg zijn.”
    - “Beschrijving mag maximaal 1500 karakters bevatten.”

- A5.1: Afbeelding upload fout
  - Ongeldig formaat (geen jpg/png/webp)
  - Bestand te groot
  - Systeem toont fouten zoals:
    - “Afbeelding moet kleiner zijn dan 5 MB.”

- A5.2: Ongeldige tag
  - Gebruiker probeert een tag toe te voegen die verboden tekens bevat, of lang is (>30 tekens).
  - Systeem valideert de tag en detecteert de fout.
  - Systeem toont een duidelijke foutmelding, bijvoorbeeld:
    - "Tag mag alleen letters, cijfers en underscores bevatten."
    - "Tag moet tussen 1 en 30 tekens zijn."

- A3.4: Gebruiker geblokkeerd voor het aanmaken van communities
  - Systeem detecteert platform restrictie.
  - Toont foutmelding: “Je kunt op dit moment geen nieuwe communities aanmaken.”

- A0.2: Timeout of netwerkfout bij aanmaken
  - Systeem toont melding: “Er ging iets mis. Probeer opnieuw.”
  - Community wordt niet aangemaakt.

- **Goal:** Gebruikers kunnen eigen communities aanmaken om specifieke interesses of thema’s te groeperen.
- **Overview:** Deze use case behandelt het proces voor het initiëren van een nieuwe community en de automatische roltoewijzing van eigenaar.
- **Cross-References:**
  - Community moderator aanstellen
  - Aansluiten bij community
