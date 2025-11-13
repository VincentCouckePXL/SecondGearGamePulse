###  Fully Dressed Use Case: Profiel Instellen
**Actors:** 
- **Primary Actor:** Gebruiker
- **Secondary Actor:** Systeem  
**Pre-conditions:** 
- De gebruiker heeft reeds een account aangemaakt     
- De gebruiker heeft dit account nog niet gepersonaliseerd
**Post-conditions:**    
- De gebruiker heeft een gepersonaliseerd account, aangepast naar zijn wensen

**Description:** Gebruiker personaliseert profiel na registratie
**Scenario:**

| Actor Action                         | System Response                                                                                 |
|--------------------------------------|-------------------------------------------------------------------------------------------------|
| 1. Heeft geregistreerd (preconditie) | 1. Toont setup wizard                                                                           |
| 2. Kiest avatar/upload foto          | 2. Controleert of foto gevoelige inhoud bevat (indien upload) en profiel avatar wordt geupdatet |
| 3. Schrijft biografie                | 3. Kijkt na of biografie niet langer is dan toegelaten en Profiel biografie wordt geupdatet     |
| 4. Kiest favoriete platformen        | 4. Profiel voorkeursplatformen wordt geupdatet                                                  |
| 5. Stelt privacy-instellingen in     | 5. Profiel privacy-instellingen worden opgeslagen                                               |

**Additional information**
- **Goal:** Een profiel kan gepersonaliseerd worden naar de wensen van de gebruiker
- **Overview:** Deze use case beschrijft het proces van de personalisatie van een gebruiker zijn profiel. Het beschrijft zowel de gebruikersacties en de achterliggende systeemacties die genomen worden.
- **Cross-References:** 
  - Registratie
  - Profiel aanpassen