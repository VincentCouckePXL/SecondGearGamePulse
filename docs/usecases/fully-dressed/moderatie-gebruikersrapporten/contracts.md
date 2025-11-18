# Contracten voor Moderatie Gebruikersrapporten

## Contract voor wijzigStatus(RaportStatus)
   
**Operation**  
wijzigStatus(status: RaportStatus): void

**Cross-References**
- Use Case: Rapport Status Beheer
- SSD: Rapport Werkstroom

**Preconditions**
- Een rapport moet actief zijn en geladen in het systeem
- De gebruiker moet gemachtigd zijn om rapportstatussen te wijzigen
- De nieuwe status moet verschillen van de huidige status

**Postconditions**
- [Attribute modification] Rapport.status werd bijgewerkt naar de nieuwe status
- [Instance creation] Een StatusWijziging geschiedenisrecord werd aangemaakt
- [Event triggering] Een statuswijzigingsgebeurtenis werd geactiveerd voor notificaties

---

## Contract voor blokkeer()

**Operation**  
blokkeer(): void

**Cross-References**
- Use Case: Rapport Beveiliging
- SSD: Rapport Access Control

**Preconditions**
- Het rapport moet bestaan en actief zijn
- Het rapport mag niet reeds geblokkeerd zijn
- De gebruiker moet beheerdersrechten hebben

**Postconditions**
- [Attribute modification] Rapport.isGeblokkeerd werd true
- [Attribute modification] Rapport.blokkeerDatum werd ingesteld op huidige datum/tijd
- [State change] Rapport ging naar "geblokkeerd" staat
- [Permission revocation] Schrijftoegang werd ingetrokken voor normale gebruikers

---

## Contract voor blokkeerTot(eindDatum)

**Operation**  
blokkeerTot(eindDatum: DateTime): void

**Cross-References**
- Use Case: Tijdelijke Rapport Restrictie
- SSD: Scheduled Access Control

**Preconditions**
- Het rapport moet bestaan en actief zijn
- eindDatum moet in de toekomst liggen
- De gebruiker moet beheerdersrechten hebben
- Er mag geen actieve blokkering zijn die later eindigt

**Postconditions**
- [Attribute modification] Rapport.isGeblokkeerd werd true
- [Attribute modification] Rapport.blokkeerDatum werd ingesteld op huidige datum/tijd
- [Attribute modification] Rapport.blokkeerEindDatum werd ingesteld op eindDatum
- [Instance creation] Een geplande deblokkeringsjob werd aangemaakt
- [Permission revocation] Schrijftoegang werd ingetrokken tot eindDatum