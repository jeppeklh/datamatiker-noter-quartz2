## Virksomhedsprofil for GodTur
GodTur er en online turismevirksomhed etableret i 2017, der har revolutioneret markedsføringen i turismebranchen ved at fokusere på sociale medier som den primære platform for kundeinteraktion. Virksomheden har oplevet markant vækst, især efter COVID-19-krisen, og opnåede en omsætning på over 1 million EUR i 2022, med forventning om at stige til 1,5 millioner EUR i 2023.

---

## Arbejdsgang
GodTur gør rejseoplevelsen enkel og effektiv. Kunderne kan kontakte virksomheden via WhatsApp eller messenger-tjenester for at forespørge om og købe rejser. Efter at have delt deres personlige oplysninger modtager de en elektronisk faktura via Stripe, som muliggør nem betaling med kreditkort. Efter betalingen modtager kunden e-billetter og hotelreservationer direkte via e-mail.

For at sikre en god kundeoplevelse leverer virksomheden også digitale rejseguider, der beskriver attraktioner og de bedste restauranter samt en rejseplan over transport fra lufthavnen til hotellet og en kortoversigt over hotellets beliggenhed og omgivelser.

---

## Virksomhedens driftsmodel
GodTur tilbyder lavprisrejser uden faste kontorlokaler, hvilket gør det muligt at holde omkostningerne nede. Rejserne består typisk af korte ophold på budgetvenlige hoteller med brug af lavprisflyselskaber. GodTur tilbyder også kundetilpassede rejsepakker.

---

## Kundebase og vækst
Virksomheden har målrettet sine markedsføringsindsatser mod nye kundesegmenter ved at bruge grundlæggerens arabiske sprogfærdigheder. Dette har resulteret i hurtig vækst, først via Facebook-markedsføring i Sydsverige og senere udvidelse til flere europæiske lande. I dag har virksomheden over 100.000 følgere på tværs af sine sociale medieplatforme og en kundedatabase med 20.000 aktive kontakter.

---

## Fremtidige planer og teknologiske ambitioner
GodTur arbejder på at lancere en ny avanceret platform, Gotorz, der vil fungere som en selvbetjeningsportal for kunder og en teknologi, der kan sælges til rejsebureauer, især i Mellemøsten.

---

## Problemstilling for projektet
Hvordan kan GodTur udvikle en webapplikation, der integrerer data fra både flyselskabers API og hotellers API for at skabe en samlet og overskuelig rejsepakke, som præsenteres for kunden som én samlet

reservation? Systemet skal være designet, så det skjuler de enkelte detaljer om fly og hotel for kunden, og det samlede tilbud præsenteres på en enkel måde. Integration af betalingssystemer og forbedret UI/UX betragtes som en ekstra bonus.

---

## Kravspecifikation
- Systemdesign og funktionalitet:
	- Integration med eksterne API'er:
	- Implementere integrationer, der kan hente og kombinere data fra flyselskabers API og hotellers API.
	- Aggregere og præsentere data som én samlet rejsepakke med en samlet pris uden visning af individuelle detaljer.

- Brugerstyring og roller:
	- Brugerroller: Implementere brugerroller som almindelige kunder, admin-brugere og salgsmedarbejdere.
	- Brugeroprettelse og login: Systemet skal understøtte oprettelse af brugerkonti, login og sessionstyring.
	- Adgangskontrol: Rollebaseret adgangsstyring skal sikre, at hver brugerrolle har passende tilladelser og funktioner.

- Funktioner for kunder:
	- Søgning og booking: Mulighed for at søge efter og booke rejser samt oprette sig som bruger.
	- Ordrehistorik: Mulighed for at se tidligere og kommende reservationer.
	- Betalingsproces: Integration af sikre betalingsløsninger med mulighed for at gemme betalingsoplysninger til fremtidig brug (bonusfunktion).
	- Chatfunktion: En realtidschat, hvor kunder kan sende beskeder til hinanden. Chatten kan organiseres som én-til-én eller gruppechat baseret på fælles interesser, destinationer, eller rejseplaner.

- Funktioner for admin-brugere:
	- Brugeradministration: Admins skal kunne administrere brugerprofiler, tildele roller og nulstille adgangskoder.
	- Overvågning af aktivitet: Adgang til aktuelle og historiske reservationer med mulighed for filtrering.

- Funktioner for salgsmedarbejdere:
	- Support: Adgang til kunders bookinginformation for at kunne yde effektiv support.
	- Kommunikation: Værktøjer til at sende notifikationer eller e-mails om ændringer i reservationer.
	- Dashboard: Et tilpasset dashboard med overblik over bookinger og kundehenvendelser.

- Brugervenlighed og UI/UX:
	- Design: En intuitiv brugergrænseflade, der er nem at navigere og tilpasset de forskellige brugertyper.
	- Responsivt design: Implementering af et responsivt layout, der fungerer optimalt på forskellige enheder (bonusfunktion).

- Datasikkerhed og compliance:
	- Adgangslogning: Implementering af logning af brugeraktivitet for øget sikkerhed og muliggørelse af audits.
	- GDPR-compliance: Sikre behandling af persondata, med mulighed for at brugere kan tilgå og slette deres oplysninger.

- Teknologi og arkitektur:
	- Framework og sprog: Udvikling i ASP.NET Core og Blazor til frontend.
	- Database: Microsoft SQL Server og Entity Framework til dataopbevaring.
	- Cloud og sikkerhed: Brug af Microsoft Azure til cloud-tjenester, hosting og sikkerhed.

- Udvidelsesmuligheder:
	- Flersprogssupport: Understøttelse af flere sprog, så systemet kan tilpasses til forskellige brugergrupper og regioner.

