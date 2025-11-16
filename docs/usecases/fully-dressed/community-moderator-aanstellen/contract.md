Actoren: Community Eigenaar, Systeem, Geselecteerde Gebruiker

Input:
- Community ID (impliciet uit context)
- Gebruiker ID van te promoveren lid
- Bevestiging van actie (boolean)

Output:
- Lijst van beschikbare leden voor promotie
- Bevestigingsdialoog met geselecteerde gebruiker details
- Succesmelding bij voltooide actie
- Bijgewerkte ledenlijst met rolindicatoren

Precondities:
- Community Eigenaar is geauthenticeerd en ingelogd
- Eigenaar heeft 'eigenaar' rol in de community
- Te promoveren gebruiker is lid van de community
- Te promoveren gebruiker heeft nog geen moderator rechten
- Community bestaat en is actief

Postcondities:
- Gebruiker rol is gewijzigd naar 'moderator' in de community
- Audit log bevat record van rolwijziging
- Nieuwe moderator heeft toegang tot moderatiefuncties
- Notificatie is verstuurd naar nieuwe moderator

Voorwaarden:
- Alleen community eigenaar kan moderators aanstellen
- Gebruiker is niet geblokkeerd in het systeem
