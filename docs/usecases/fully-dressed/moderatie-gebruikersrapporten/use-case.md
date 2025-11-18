### Fully Dressed Use Case: Behandelen van gebruikersrapporten

**Actors:**
- **Primary Actor:** Administrator
- **Secondary Actor:** Systeem
- **Offstage Actors:** Gemelde gebruiker, meldende gebruiker

**Pre-conditions:**
- Administrator is succesvol geauthenticeerd en beschikt over admin-rechten.
- Er bestaan één of meerdere openstaande rapporten.
- Elk rapport verwijst naar een gebruiker, review of community.

**Post-conditions:**
- Het geselecteerde rapport heeft een nieuwe status: *afgehandeld* of *ongeldig*.
- Een moderatie-actie (indien uitgevoerd) is geregistreerd in het moderatie-logboek.
- Systeemstatus van betrokken entiteiten kan gewijzigd zijn (bijv. gebruiker geblokkeerd, content verwijderd).
- Eventuele notificaties zijn verzonden naar relevante gebruikers.

**Description:**  
Administrator verwerkt een gebruikersrapport door de inhoud te bekijken, de betrokken entiteiten te evalueren en een passende moderatie-actie te selecteren.

---

### Scenario (Main Success Path)

| Actor Action                                                                | System Response                                                                                                                                                                                                                                            |
|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1. Administrator opent het adminpanel en navigeert naar “Openstaande rapporten”. | 1. Systeem toont een gesorteerde lijst van openstaande rapporten met type, melder, timestamp en status.                                                                                                                                                    |
| 2. Administrator selecteert een rapport.                                    | 2. Systeem toont alle details van het geselecteerde rapport.                                                                                                                                                                                               |
| 3. Administrator opent de gerapporteerde entiteit (user/review/community). | 3. Systeem toont de inhoud van de entiteit.                                                                                                                                                                                                                |
| 4. Administrator kiest een moderatie-actie (bv. waarschuwing, tijdelijke/ permanente blokkering, verwijderen van content, markeren als ongeldig). | 4. Het systeem navigeert de administrator terug naar de report overview page. Daarna voert het Systeem de actie uit. Ook registreert het systeem de actie in het logboek, markeert het rapport als afgehandeld en verzendt relevante notificaties. |                                                                                                               |

---

### Alternative Flows

#### A4.1 – Rapport ongeldig of onvoldoende informatie
- Administrator markeert rapport als "ongeldig".
- Systeem sluit het rapport zonder verdere moderatie-acties.

#### A4.2 – Gerelateerde content bestaat niet meer
- Systeem meldt dat de onderliggende entiteit niet langer bestaat.
- Administrator markeert rapport als afgehandeld.

#### A4.3 – Administrator annuleert moderatie-actie
- Administrator annuleert bij de bevestigingsstap.
- Systeem keert terug naar het rapportdetailscherm.

#### A4.4 – Systeemfout bij uitvoeren van de actie
- Systeem toont foutmelding en voert de actie niet uit.
- Rapport blijft open. Administrator kan het later opnieuw proberen.

---

### Additional Information

- **Goal:** De administrator beoordeelt gebruikersrapporten en voert consistente, traceerbare moderatie-acties uit om de platformintegriteit te bewaken.
- **Overview:** Deze use case behandelt het volledige moderatieproces voor rapporten, inclusief ophalen, inspecteren, beslissen, uitvoeren van acties en loggen.
- **Cross-References:**
  - UC: Gebruiker Opvragen
  - UC: Chat Opvragen
  - UC: Community Opvragen
  - UC: Review Opvragen
  - UC: Neem Actie Tegen Gebruiker
  - UC: Permanently block user
  - UC: Tijdelijk block user
  - UC: Ondbind Community
  - UC: Verwijder Review
  - UC: Waarschuw User
  - UC: Waarschuw Community
  - UC: Verwijder Community
  - UC: Dismiss
  - UC: Notify Relevant Users
