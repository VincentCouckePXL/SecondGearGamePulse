# GamePulse - Uitgewerkte Casual Use Cases

## Authenticatie Use Cases
___
### Use Case: Registratie
**Actors:** Gebruiker, Systeem  
**Description:** Nieuwe gebruiker registreert account  
**Main Scenario:**
1. Gebruiker klikt "Register" op login pagina
2. Systeem toont registratieformulier
3. Gebruiker vult in: email, gebruikersnaam, wachtwoord, bevestig wachtwoord
4. Gebruiker accepteert terms & conditions
5. Systeem valideert invoer en controleert unieke email/gebruikersnaam
6. Systeem creëert nieuw account en verstuurt verificatie email
7. Gebruiker bevestigt email via link
8. Systeem logt gebruiker automatisch in

**Alternative Scenarios:**
- Email al in gebruik: 
  - Systeem geeft foutmelding "Email is al geregistreerd"
- Gebruikersnaam niet beschikbaar:
  - Systeem suggereert alternatieve gebruikersnamen
- Zwak wachtwoord:
  - Systeem toont wachtwoord vereisten
- Bevestiging wachtwoord komt niet overeen:
  - De twee ingevoerde wachtwoorden verschillen, systeem toont foutmelding: "Bevestigingswachtwoord komt niet overeen met gekozen wachtwoord"

___
### Use Case: Inloggen
**Actors:** Gebruiker, Systeem  
**Description:** Bestaande gebruiker logt in op platform  
**Main Scenario:**
1. Gebruiker navigeert naar login pagina
2. Gebruiker voert email/gebruikersnaam en wachtwoord in
3. Systeem authenticeert credentials
4. Systeem start geauthenticeerde sessie
5. Gebruiker wordt doorgestuurd naar dashboard

**Alternative Scenarios:**
- Onjuiste credentials:
  - Systeem toont "Ongeldige login gegevens"
- Vergeten wachtwoord:
  - Gebruiker kan "Wachtwoord vergeten" flow starten
- Account geblokkeerd:
  - Systeem toont "Account geblokkeerd wegens verdachte activiteit"
___
### Use Case: Wachtwoord Reset

**Actors:** Gebruiker, Systeem, Email Service   
**Description:** Gebruiker reset vergeten wachtwoord via email verificatie  
**Pre-conditions:** Gebruiker heeft een geregistreerd account met geverifieerd email adres  

**Main Scenario:**
1. Gebruiker klikt "Wachtwoord vergeten?" op login pagina
2. Systeem toont wachtwoord reset formulier
3. Gebruiker voert email adres in
4. Systeem valideert email format en zoekt bijbehorend account
5. Systeem genereert unieke reset token met expiry tijd (1 uur)
6. Systeem verstuurt email met reset link naar gebruiker
7. Gebruiker ontvangt email en klikt op reset link
8. Systeem valideert reset token en toont wachtwoord reset pagina
9. Gebruiker voert nieuw wachtwoord in (tweemaal voor bevestiging)
10. Systeem valideert wachtwoord en zijn sterkte
11. Systeem update wachtwoord hash in database
12. Systeem invalideert alle bestaande sessies van gebruiker
13. Systeem toont bevestigingsmelding "Wachtwoord succesvol gewijzigd"
14. Gebruiker wordt doorgestuurd naar login pagina

**Alternative Scenarios:**
- Onbekend Email Adres:
  - Gebruiker voert email in dat niet in systeem geregistreerd is, systeem toont melding: "Indien dit email adres bij ons bekend is, ontvangt u een reset link"
- Ongeldige Reset Token:
  -  Gebruiker klikt op verlopen reset link (ouder dan 1 uur), systeem toont foutmelding: "Reset link is verlopen of ongeldig"
- Meerdere Reset Pogingen:
  - Gebruiker vraagt meerdere reset emails aan binnen korte tijd, systeem toont "Te veel pogingen, probeer het later opnieuw"
- Zwak wachtwoord:
  - Systeem toont wachtwoord vereisten
- Bevestiging wachtwoord komt niet overeen:
  - De twee ingevoerde wachtwoorden verschillen, systeem toont foutmelding: "Bevestigingswachtwoord komt niet overeen met gekozen wachtwoord"
___
### Use Case: Logout
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker beëindigt huidige sessie  
**Main Scenario:**
1. Gebruiker klikt op profiel avatar
2. Gebruiker selecteert "Uitloggen"
3. Systeem beëindigt sessie
4. Systeem verwijdert authenticatie tokens
5. Gebruiker wordt doorgestuurd naar home pagina
___
## Profiel Management Use Cases

### (Fully Dressed) Use Case: Profile Instellen
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker stelt initieel profiel in na registratie  
**Main Scenario:**
1. Na registratie toont systeem profiel setup wizard
2. Gebruiker kiest avatar/upload profielfoto
3. Gebruiker voert bio/informatie in
4. Gebruiker selecteert favoriete genres
5. Gebruiker kiest voorkeursplatformen
6. Gebruiker stelt privacy instellingen in
7. Systeem slaat profiel op
___
### Use Case: Profile Aanpassen
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker wijzigt bestaande profielinstellingen  
**Main Scenario:**
1. Gebruiker navigeert naar profiel instellingen
2. Gebruiker bewerkt profiel informatie
3. Systeem toont preview van wijzigingen
4. Gebruiker bevestigt wijzigingen
5. Systeem update profiel in database
___
## Community Use Cases

### Use Case: Community Deelnemen
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker wordt lid van een community  
**Main Scenario:**
1. Gebruiker bekijkt community pagina
2. Gebruiker klikt "JOIN"
3. Systeem voegt gebruiker toe aan community leden
4. Gebruiker ontvangt community notificaties
5. Gebruiker verschijnt in community ledenlijst

**Alternative Scenarios:**
- Geblokkeerde gebruiker:
  - Systeem toont "Je kunt niet deelnemen aan deze community"
___
### Use Case: Community Verlaten
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker verlaat een community  
**Main Scenario:**
1. Gebruiker navigeert naar community pagina
2. Gebruiker klikt "Verlaat Community"
3. Systeem toont bevestigingsdialoog
4. Gebruiker bevestigt actie
5. Systeem verwijdert gebruiker uit community leden
6. Gebruiker verliest toegang tot private community content
___
### (Fully Dressed) Use Case: Eigen Community Aanmaken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker creëert nieuwe community  
**Main Scenario:**
1. Gebruiker navigeert naar "Create Community"
2. Gebruiker vult community details in: naam, beschrijving
3. Gebruiker vult community regels en guidelines in
4. Systeem valideert community naam (uniek)
5. Systeem creëert nieuwe community
6. Gebruiker wordt automatisch eigenaar en moderator
___
### Use Case: Eigen Community Verwijderen
**Actors:** Gebruiker, Systeem  
**Description:** Eigenaar verwijdert zijn/haar community  
**Main Scenario:**
1. Gebruiker navigeert naar eigen community beheer
2. Gebruiker selecteert "Delete Community"
3. Systeem toont waarschuwing voor verwijdering welke impact dit zal hebben (verlies alle posts, leden, etc.)
4. Gebruiker bevestigt met typing community naam
5. Systeem archiveert community data
6. Systeem verwijdert community permanent na 30 dagen
___
### (Fully Dressed) Use Case: Moderator Aanstellen
**Actors:** Community Eigenaar, Systeem  
**Description:** Eigenaar wijst moderator aan voor community  
**Main Scenario:**
1. Eigenaar bekijkt community ledenlijst
2. Eigenaar selecteert gebruiker voor moderator rol
3. Systeem toont moderator rechten en verantwoordelijkheden
4. Eigenaar bevestigt aanstelling
5. Systeem update gebruiker rol naar moderator
6. Nieuwe moderator ontvangt notificatie
___
# Community Bericht Use Cases

### Use Case: Bericht Plaatsen
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker plaatst een nieuw bericht in community chat  
**Main Scenario:**
1. Gebruiker navigeert naar community chat sectie
2. Gebruiker klikt in bericht invoerveld
3. Gebruiker typt bericht inhoud (max 1500 karakters)
4. Gebruiker kan afbeelding toevoegen
5. Gebruiker klikt "Versturen"
6. Systeem valideert bericht (niet leeg, binnen lengtelimiet, geen vulgair taalgebruik)
7. Systeem publiceert bericht in community chat feed
8. Bericht wordt real-time getoond aan alle online community leden
9. Systeem registreert bericht in database met timestamp en auteur

**Alternative Scenarios:**
- Als bericht leeg is:
  - Systeem toont waarschuwing "Bericht mag niet leeg zijn"
- Als bericht te lang is:
  - Systeem telt karakters en voorkomt verzenden, toont waarschuwing "bericht mag maximaal 1500 karakters lang zijn"
- Als gebruiker geblokkeerd is:
  - Systeem toont "Je kunt geen berichten plaatsen in deze community"
---
### Use Case: Berichten Bekijken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker bekijkt berichten in community chat  
**Main Scenario:**
1. Gebruiker opent community chat pagina
2. Systeem laadt laatste 100 berichten (laden wanneer community geopend wordt) met oneindig scrollen (lazy loading) en pagination (in de zin van telkens 100 nieuwe berichten inladen)
3. Gebruiker ziet berichten met auteur, timestamp en emoji reacties
4. Gebruiker scrolt door berichtgeschiedenis
5. Nieuwe berichten verschijnen automatisch onderaan
6. Gebruiker kan op emoji reacties klikken om te zien wie gereageerd heeft

**Alternative Scenarios:**
- Bij trage verbinding:
  - Systeem toont skeleton loading screens
- Bij eerste bezoek:
  - Systeem toont welkomstbericht met community regels
---
### Use Case: Bericht Bewerken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker bewerkt eigen bericht in community chat  
**Main Scenario:**
1. Gebruiker hovert over eigen bericht
2. Gebruiker klikt "Bewerken" (potlood icoon)
3. Systeem toont bericht in bewerkmodus met karakter teller
4. Gebruiker past bericht inhoud aan
5. Gebruiker klikt "Opslaan" om wijzigingen te bevestigen
6. Systeem update bericht in database
7. Bericht wordt gemarkeerd als "Bewerkt"
8. Alle community leden zien de bijgewerkte versie

**Alternative Scenarios:**
- Als bewerkingstijd verstreken is (30 min):
  - Systeem toont "Bewerken niet meer mogelijk"
- Als bericht al emoji reacties heeft:
  - Systeem behoudt alle reacties na bewerking
---
### Use Case: Bericht Verwijderen
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker verwijdert eigen bericht uit community chat  
**Main Scenario:**
1. Gebruiker hovert over eigen bericht
2. Gebruiker klikt "Verwijderen"
3. Systeem toont bevestigingsdialoog "Weet je zeker dat je dit bericht wilt verwijderen?"
4. Gebruiker bevestigt verwijdering
5. Systeem verwijdert bericht inhoud uit database
6. Andere gebruikers zien "[Bericht verwijderd]" placeholder
7. Placeholder behoudt timestamp en toont "Verwijderd door auteur"

**Alternative Scenarios:**
- Als moderator bericht verwijdert:
  - Placeholder toont "Verwijderd door moderator"
---
### Use Case: Emoji Reactie Toevoegen
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker voegt emoji reactie toe aan community bericht  
**Main Scenario:**
1. Gebruiker hovert over een bericht
2. Gebruiker klikt "Emoji toevoegen"
3. Systeem toont emoji picker met populaire opties
4. Gebruiker selecteert gewenste emoji
5. Systeem voegt emoji reactie toe aan bericht
6. Emoji teller wordt verhoogd
7. Gebruiker kan op dezelfde emoji klikken om reactie te verwijderen

**Alternative Scenarios:**
- Als gebruiker al gereageerd heeft:
  - Klikken verwijdert bestaande reactie
- Als bericht verwijderd is:
  - Systeem toont "Kan niet reageren op verwijderd bericht"
---
### Use Case: Emoji Reacties Bekijken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker bekijkt wie welke emoji reacties heeft gegeven  
**Main Scenario:**
1. Gebruiker hover over emoji reactie onder een bericht
2. Gebruiker klikt op emoji reactie voor volledige lijst
3. Systeem toont modal met alle gebruikers die deze reactie gegeven hebben
4. Gebruiker kan door de lijst scrollen
5. Modal toont reactie timestamp indien beschikbaar

**Alternative Scenarios:**
- Bij veel reacties:
  - Systeem toont "en X anderen" met lazy loading
---
## Social Use Cases

### Use Case: Games Volgen
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker volgt game voor updates  
**Main Scenario:**
1. Gebruiker bekijkt game detail pagina
2. Gebruiker klikt "Follow Game"
3. Systeem voegt game toe aan gebruiker's gevolgde games
4. Gebruiker ontvangt notificaties bij game updates
5. Game verschijnt in lijst van favoriete games
___
### (Fully Dressed) Use Case: Gebruiker Volgen
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker volgt andere gebruiker  
**Main Scenario:**
1. Gebruiker bekijkt ander gebruikersprofiel
2. Gebruiker klikt "Follow"
3. Systeem voegt toe aan 'volgend' lijst
4. Gevolgde gebruiker ontvangt notificatie
5. Activiteiten verschijnen in lijst van gevolgde gebruikers hun activiteiten
___
### Use Case: Gebruikersprofiel Bekijken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker bekijkt profiel van andere gebruiker of eigen profiel met alle bijbehorende informatie  
**Main Scenario:**
1. Gebruiker navigeert naar profiel pagina via zoekfunctie, community ledenlijst of directe URL
2. Systeem laadt profiel basisinformatie (gebruikersnaam, profielfoto, lid sinds datum, wishlist)
3. Systeem toont profiel header met volgers/volgend aantallen en interactie knoppen
4. Systeem toont bio sectie met persoonlijke beschrijving en favoriete genres
5. Systeem toont activiteit feed met recente reviews en community posts
6. Systeem toont gaming statistieken (totaal gespeelde games, gemiddelde review score)
7. Systeem toont sociale connecties en gemeenschappelijke interesses
8. Gebruiker kan door verschillende profiel secties navigeren via tab interface

**Alternative Scenarios:**
- Profiel is privé:
    - Systeem toont "Dit profiel is privé" melding, beperkte basisinformatie wordt getoond
- Niet-bestaan profiel:
    - Gebruiker navigeert naar ongeldig profiel URL, systeem toont "Profiel niet gevonden" error pagina
- Geblokkeerde gebruiker:
    - Gebruiker probeert profiel te bekijken van iemand die hen geblokkeerd heeft, systeem toont "Je hebt geen toegang tot dit profiel"
- Eigen profiel bekijken:
    - Systeem toont bewerkingsopties en privé statistieken, dit betekent preview modus hoe profiel eruit ziet voor anderen
---
### Use Case: Gebruiker Zoeken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker zoekt naar andere gebruikers op het platform  
**Main Scenario:**
1. Gebruiker navigeert naar zoekbalk in header of zoekpagina
2. Gebruiker voert zoekterm in (gebruikersnaam, display naam)
3. Systeem toont real-time zoeksuggesties tijdens typen
4. Gebruiker selecteert zoekresultaat of drukt Enter
5. Systeem toont zoekresultaten pagina met gebruikerslijst
6. Gebruiker toont per resultaat: profielfoto, gebruikersnaam, gemeenschappelijke connecties
7. Gebruiker kan filteren op activiteit status (online, recent actief)
8. Gebruiker selecteert gebruiker uit resultaten om naar profiel te navigeren

**Alternative Scenarios:**
- Geen resultaten gevonden:
    - Systeem toont "Geen gebruikers gevonden" met suggesties voor alternatieve zoektermen
- Meerdere gebruikers met dezelfde naam:
    - Systeem toont onderscheidende informatie (lid sinds, aantal volgers, gemeenschappelijke vrienden)
- Zoekterm te kort:
    - Systeem toont melding "Voer minimaal 3 karakters in" bij zoektermen korter dan 3 karakters
- Geblokkeerde gebruikers:
    - Gebruikers die de zoeker geblokkeerd hebben worden niet getoond in resultaten
- Privé profielen:
    - Gebruikers met privéprofielen worden getoond met beperkte informatie
---
## Game Discovery Use Cases

### Use Case: Games Zoeken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker zoekt naar specifieke games  
**Main Scenario:**
1. Gebruiker gebruikt zoekbalk in header
2. Gebruiker voert zoekterm in
3. Systeem toont real-time zoeksuggesties
4. Gebruiker selecteert zoekresultaat of drukt Enter
5. Systeem toont zoekresultaten met filters
6. Gebruiker kan resultaten sorteren op relevantie, rating, etc.
___
### Use Case: Games Vergelijken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker vergelijkt meerdere games side-by-side  
**Main Scenario:**
1. Gebruiker selecteert games voor vergelijking (max 4)
2. Gebruiker klikt "Compare Games"
3. Systeem toont comparison dashboard
4. Gebruiker ziet vergelijking van prijs, ratings, features
5. Gebruiker kan specifieke categorieën expanderen
6. Gebruiker kan direct doorklikken naar game details
___
## Wishlist Use Cases

### Use Case: Wishlist Create
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker voegt game toe aan wishlist  
**Main Scenario:**
1. Gebruiker bekijkt game detail pagina
2. Gebruiker klikt "Add to Wishlist"
3. Systeem voegt game toe aan persoonlijke wishlist
4. Systeem start monitoring voor prijsdalingen
5. Gebruiker ontvangt bevestiging
___
### Use Case: Wishlist Read
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker bekijkt persoonlijke wishlist  
**Main Scenario:**
1. Gebruiker navigeert naar "My Wishlist"
2. Systeem toont alle wishlist games
3. Gebruiker ziet huidige prijzen en prijsgeschiedenis
4. Gebruiker kan sorteren op toegevoegd datum, prijs, etc.
5. Systeem toont prijs alerts voor wishlist items
___
### Use Case: Wishlist Update
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker bewerkt wishlist
**Main Scenario:**
1. Gebruiker opent wishlist beheer
2. Gebruiker stelt prijs alerts in per game
3. Gebruiker voegt notities toe aan wishlist items
4. Systeem slaat wijzigingen op
___
### Use Case: Wishlist Delete
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker verwijdert game van wishlist  
**Main Scenario:**
1. Gebruiker opent wishlist
2. Gebruiker hovert over game item
3. Gebruiker klikt "Verwijderen"
4. Systeem verwijdert game uit wishlist
5. Systeem stopt prijs monitoring voor deze game
___
## Review Use Cases

### Use Case: Review Create
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker schrijft review voor game  
**Main Scenario:**
1. Gebruiker navigeert naar game detail pagina
2. Gebruiker klikt "Schrijf Review"
3. Systeem toont review formulier
4. Gebruiker vult rating, titel en beschrijving in
5. Gebruiker kan pros/cons toevoegen
6. Systeem publiceert review en update game gemiddelde
___
### Use Case: Review Read
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker leest reviews voor game  
**Main Scenario:**
1. Gebruiker scrollt naar review sectie op game pagina
2. Systeem toont gepagineerde reviews
3. Gebruiker kan filteren op rating, helpfulness, datum
4. Gebruiker leest volledige review content
___
### Use Case: Review Update
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker bewerkt eigen review  
**Main Scenario:**
1. Gebruiker navigeert naar eigen review
2. Gebruiker klikt "Edit Review"
3. Systeem toont bewerkingsinterface
4. Gebruiker past rating of content aan
5. Systeem update review en herberekent game gemiddelde
6. Review wordt gemarkeerd als "Bewerkt"
___
### Use Case: Review Delete
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker verwijdert eigen review  
**Main Scenario:**
1. Gebruiker navigeert naar eigen review
2. Gebruiker klikt "Delete Review"
3. Systeem toont bevestigingsdialoog
4. Gebruiker bevestigt verwijdering
5. Systeem verwijdert review en herberekent game gemiddelde
___
### Use Case: Review Liken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker markeert review als helpful  
**Main Scenario:**
1. Gebruiker leest review
2. Gebruiker klikt "Behulpzaam" button
3. Systeem registreert like
4. Review helpfulness score wordt verhoogd
___
### Use Case: Review Disliken
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker markeert review als not helpful  
**Main Scenario:**
1. Gebruiker leest review
2. Gebruiker klikt "Niet behulpzaam" button
3. Systeem registreert dislike
4. Review helpfulness score wordt verlaagd
___
### Use Case: Review Reporten
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker rapporteert ongepaste review  
**Main Scenario:**
1. Gebruiker klikt "Report" op review
2. Systeem toont report redenen menu
3. Gebruiker selecteert reden (spam, harassment, etc.)
4. Gebruiker vult optionele toelichting in
5. Systeem logt report en notificeert moderators
6. Gebruiker ontvangt bevestiging
___
## Gebruiker Interactie Use Cases

### Use Case: Andere Gebruiker Blokkeren
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker blokkeert interactie met andere gebruiker  
**Main Scenario:**
1. Gebruiker navigeert naar ander gebruikersprofiel
2. Gebruiker klikt "Block User"
3. Systeem toont bevestigingsdialoog met impact wat deze actie inhoudt
4. Gebruiker bevestigt blokkering
5. Systeem verbreekt alle connecties tussen gebruikers
6. Gebruiker ziet geen reviews of community chats van geblokkeerde gebruiker meer
___
### Use Case: Andere Gebruiker Rapporteren
**Actors:** Gebruiker, Systeem  
**Description:** Gebruiker rapporteert ongepast gedrag van andere gebruiker  
**Main Scenario:**
1. Gebruiker navigeert naar ander gebruikersprofiel
2. Gebruiker klikt "Report User"
3. Systeem toont report formulier met categorieën
4. Gebruiker selecteert type misbruik en voegt details toe
5. Gebruiker uploadt bewijs (screenshots, etc.)
6. Systeem logt report en escalate naar moderators
___
## Moderator Use Cases

### Use Case: Community Posts Deleten
**Actors:** Moderator, Systeem  
**Description:** Moderator verwijdert ongepaste community post  
**Main Scenario:**
1. Moderator bekijkt gerapporteerde posts queue
2. Moderator beoordeelt post content
3. Moderator selecteert "Delete Post"
4. Systeem toont verwijderingsreden menu
5. Moderator selecteert reden en kan optioneel notitie toevoegen
6. Systeem verwijdert post en notificeert auteur
7. Auteur ontvangt reden en optionele notitie
---
### Use Case: Gebruiker Blokkeren in Community

**Actors:** Community Eigenaar, Community Moderator, Gebruiker, Systeem  
**Description:** Community eigenaar of moderator blokkeert een gebruiker van deelname aan de community  
**Main Scenario:**
1. Eigenaar/moderator bekijkt community beheer dashboard
2. Eigenaar/moderator zoekt naar specifieke gebruiker in ledenlijst
3. Eigenaar/moderator selecteert "Blokkeer Gebruiker" bij de betreffende gebruiker
4. Systeem toont blokkeringsconfiguratie dialoog
5. Eigenaar/moderator kiest blokkeringsduur (tijdelijk/permanent) en voert reden in
6. Eigenaar/moderator bevestigt de blokkering
7. Systeem verwijdert gebruiker uit community leden
8. Systeem voorkomt verdere deelname van gebruiker aan community
9. Gebruiker ontvangt notificatie over blokkering met reden
10. Systeem logt de blokkering in moderation history

**Alternative Scenarios:**
- Als de gebruiker op dit moment actief is in community chat:
  - Systeem verbreekt onmiddellijk chatverbinding en toont "Je bent geblokkeerd van deze community"
- Als de gebruiker eigenaar probeert te blokkeren:
  - Systeem toont foutmelding "Je kunt de community eigenaar niet blokkeren"
- Als de blokkering permanent is: 
  - Systeem archiveert alle content van de gebruiker in de community
- Als de gebruiker al geblokkeerd is:
  - Systeem toont "Deze gebruiker is reeds geblokkeerd" en opties om blokkering aan te passen
---
# Use Case: Gebruiker Deblokkeren in Community

**Actors:** Community Eigenaar, Community Moderator, Gebruiker, Systeem  
**Description:** Community eigenaar of moderator heft blokkering van gebruiker op   
**Main Scenario:**
1. Eigenaar/moderator navigeert naar "Geblokkeerde Gebruikers" in community beheer
2. Eigenaar/moderator zoekt naar de geblokkeerde gebruiker
3. Eigenaar/moderator selecteert "Deblokkeer Gebruiker"
4. Systeem toont bevestigingsdialoog met blokkeringsgeschiedenis
5. Eigenaar/moderator bevestigt de deblokkering
6. Systeem herstelt gebruiker's toegang tot de community
7. Systeem verwijdert blokkeringsrestricties
8. Gebruiker ontvangt notificatie over deblokkering
9. Gebruiker kan opnieuw deelnemen aan community activiteiten
10. Systeem logt de deblokkering in moderation history

**Alternative Scenarios:**
- Als de blokkering automatisch was verlopen:
  - Systeem toont "Blokkering is reeds verlopen" en biedt optie voor handmatige bevestiging
- Als de gebruiker meerdere communities beheert:
  - Systeem toont waarschuwing "Deze gebruiker beheert X communities, wees zeker van deblokkering"
- Als er lopende reports zijn tegen de gebruiker:
  - Systeem toont waarschuwing met details van actieve reports
- Als deblokkering tijdens community evenement plaatsvindt:
  - Systeem geeft optie om beperkte toegang te verlenen tot na het evenement
___
## Administrator Use Cases

### Use Case: Gebruiker Blokkeren
**Actors:** Administrator, Systeem  
**Description:** Admin blokkeert gebruiker account platform-breed  
**Main Scenario:**
1. Admin navigeert naar gebruiker beheer
2. Admin zoekt specifieke gebruiker
3. Admin selecteert "Block User"
4. Systeem toont blokkeringsopties (tijdelijk/permanent)
5. Admin kiest duur en voegt reden toe
6. Systeem blokkeert account en logt actie
7. Gebruiker ontvangt notificatie van blokkering
___
### Use Case: Reviews Verwijderen
**Actors:** Administrator, Systeem  
**Description:** Admin verwijdert review wegens policy violation  
**Main Scenario:**
1. Admin bekijkt gerapporteerde reviews queue
2. Admin beoordeelt review content
3. Admin selecteert "Delete Review"
4. Systeem update game rating statistieken
5. Admin kan optioneel gebruiker waarschuwen
6. Review wordt gearchiveerd voor records
___
### Use Case: Community Verwijderen
**Actors:** Administrator, Systeem  
**Description:** Admin verwijdert community wegens policy violations  
**Main Scenario:**
1. Admin bekijkt community reports
2. Admin onderzoekt community activiteit
3. Admin selecteert "Delete Community"
4. Systeem toont impact warning (verlies alle content)
5. Admin bevestigt met reden
6. Admin kan community eigenaar sanctioneren indien nodig
7. Systeem archiveert community data
8. Community leden ontvangen notificatie
___
### Use Case: Community bericht Verwijderen
**Actors:** Administrator, Systeem  
**Description:** Admin verwijdert bericht uit community  
**Main Scenario:**
1. Admin bekijkt escalated content reports
2. Admin beoordeelt bericht content
3. Admin selecteert "Verwijder bericht"
4. Systeem verwijdert bericht voor de hele community
5. Admin kan gebruiker sanctioneren indien nodig
6. Actie wordt gelogd in moderatie geschiedenis
---
### (Fully Dressed) Use Case: Bekijken van gerapporteerde content
**Actors:**
 - **Primary Actor:** Administrator
 - **Secondary Actor:** Systeem    
**Main scenario:**
1. Administrator navigeert naar het moderatie-dashboard of rapportbeheer. Systeem toont een overzichtspagina van alle ontvangen rapporten, inclusief datum, rapporterende gebruiker, type content, en status
2. Administrator selecteert filtercriteria (naam, datum, type content, reden voor rapportatie, ...). Systeem past de filters toe en vernieuwt de pagina met overeenkomende meldingen.
3. Administrator kiest een specifiek rapport uit de lijst. Systeem laadt de inhoud van het geselecteerde rapport.
4. Administrator onderneemt actie (verwijderen van review of berichten, blokkeren van gebruiker, markeren als spam rapport, ...). Systeem voert de gekozen actie uit, wijzigt de status van het rapport en logt de actie.

**Alternative scenarios:**
- Als er geen gerapporteerde content is
  - Systeem toont melding "Er is geen gerapporteerde content"