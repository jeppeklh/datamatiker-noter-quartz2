 tags: #Systemudvikling
> [!tldr] Definition
> Der er mange forskellige forhold, der kan true it-systemers og datas sikkerhed. For at virksomheden kan håndtere alle disse mulige risici, er det vigtigt at danne sig et overblik over det samlede risikobillede, så man kan sætte ind, der hvor risikoen er størst, og ikke spilder tid og kræfter på at imødegå eller kompensere for ubetydelige risici.

Når en sådan samlet risikovurdering er foretaget, vil virksomheden have et godt grundlag for at prioritere hvor og hvor mange ressourcer, der skal anvendes på it-sikkerhed. 
Der udarbejdes en handlingsplan, som beskriver de aktiviteter, der skal sættes i gang for at opnå et passende sikkerhedsniveau.

---

## Udarbejdelse af risikovurdering
Her vises en model til udarbejdelse af en samlet risikovurdering:
![[Risikovurdering.png]]

For hver af de relevante hændelser vurderes tre forhold:

1. Den **økonomiske konsekvens**: hvad koster det for virksomheden, hvis hændelsen sker?

2. Virksomhedens sårbarhed: hvor godt er virksomheden beskyttet mod hændelsen?

3. Truslen: hvor sandsynligt er det, at virksomheden udsættes for hændelsen?

Ud fra disse tre vurderinger vurderes den samlede risiko for den enkelte hændelse. 
På baggrund af dette kan der opstilles et samlet risikobillede med hændelserne sorteret efter hvor stor en risiko, de udgør for virksomheden.

 På baggrund af denne samlede risikovurdering kan virksomheden så opstille en handlingsplan for de aktiviteter, der skal sættes i gang for at sikre det rette niveau af it-sikkerhed.

---

### Trin 1: Identificer hændelser, der kan true it-sikkerheden
![[Risikovurdering trin 1.png]]
Der kan dels være tale om uheld med hændelig baggrund og dels om bevidste handlinger, som har forsætlig baggrund. 
Både de forsætlige og de hændelige hændelser kan have deres oprindelse enten inde fra virksomheden selv eller fra forhold eller personer udenfor virksomheden. 
Det kan f.eks være tyveri af it-udstyr begået af medarbejdere eller udenforstående, eller tab af data på grund af fejl på backup-medier, som virksomheden selv eller anden part er ansvarlig for.   

Derudover kan de hændelige hændelser have en rent fysisk oprindelse som f.eks. brand eller oversvømmelse.

For at vurdere risici for den konkrete virksomhed må man overveje alle disse typer af hændelser, så man ender med en lang liste af hændelser, som eventuelt kan udgøre en risiko.

 Det er ikke sikkert, at man skal arbejde videre med alle hændelserne, men det er væsentligt, at man ikke sorterer en hændelse fra, før man er rimeligt sikker på, at den ikke er relevant for virksomheden – de værste katastrofer sker tit pga. noget, man ikke har tænkt på!

##### Eksempeller på valge hændelser
- Der udbryder brand i kopirum med destruktion af serverne til følge.
- Tab af væsentlige data i økonomistyringssystemet som følge af utilstrækkelig backup
- Tab af historiske data i lager/logistik systemet som følge af virusangreb
- Betroet medarbejder misbruger bankapplikation. Et eksempel på hændelser, der kan vare valgt

---

### Trin 2: Vurder økonomisk konsekvens
For hver hændelse skal det vurderes, hvad det vil koste virksomheden, hvis hændelsen er sket, og der er opstået maksimal skade.
Det er selvfølgelig forskelligt fra virksomhed til virksomhed, hvor store tab, man kan tåle at lide. Derfor må man indlede med at fastsætte, hvor grænsen går mellem hhv. en lav og en mellem økonomisk konsekvens og en mellem og en høj økonomisk konsekvens.

![[Risikovurdering økonomiske konsekvenser1.png]]

Der skal sættes et beløb for, hvad det vil koste virksomheden, hvis hændelsen er sket, og den maksimale skade er sket. 
Dvs. der skal tages højde for f.eks. omkostninger til nyindkøb, omkostninger til nøddrift, tab i produktion, salgstab, forøgede lønomkostninger og manglende ordretilgang.

---

### Trin 3: Vurder sårbarhed
![[Risikovurdering vurder sårbarhed.png]]
Det skal også vurderes, hvor sårbar virksomheden er overfor hver af hændelserne: dvs. hvordan er virksomheden stillet, hvis hændelsen står for døren, og snarest mulig forsøger at ”komme ind”. 

For at vurdere sårbarheden, skal man se på, hvad virksomheden allerede gør/har gjort for at sikre sig mod den pågældende hændelse. 
Det kan f.eks. være, at der er installeret antivirus software eller at der kode på alle dørene til de lokaler, hvor it-udstyret befinder sig.

---

### Trin 4: Vurder trussel
![[Risikovurdering Vurder trussel.png]]
For at vurdere truslen, skal man tænke på hvor stor sandsynligheden er for at hændelsen sker. 

Der vil være hændelser, som kan have fatale konsekvenser f.eks. oversvømmelse i serverrummet, men hvis rummet er placeret på 3. sal er det ikke særlig sandsynligt – dvs. truslen er lav.

---

### Trin 5: Opstil samlet risikovurdering
Når den økonomiske konsekvens, sårbarheden og truslen for er vurderet hver for sig, skal dette samles til en vurdering af risikoen for hver enkelt hændelse.

Først vurderes den økonomiske risiko ved at vælge den højeste værdi for hver hændelse
Derefter kombineres dette resultat med vurderingen af sårbarhed efter dette skema.

Det giver dette resultrat:
![[Risikovurdering delresultat.png]]

Delresultatet fra punkt 2 kombineres med vurderingen af truslen.
Hvilket giver den samlede risiko for hver enkelt hændelse:
![[Risikovurdering samlet risiko.png]]

---

## Handlingsplan
Med udgangspunkt i den samlede risikovurdering skal der nu ses på, hvad der kan gøres for at opnå et tilstrækkeligt niveau af sikkerhed.

![[Risikovurdering Handlingsplan.png]]

Det er ikke tilstrækkeligt at gennemføre en risikovurdering en enkelt gang: det er også nødvendigt at sørge for, at risikovurderingen og handlingsplanen revurderes jævnligt (f.eks. hvert år), og at der følges op på gennemførelsen og effekten af handlingsplanens foranstaltninger.

Derfor vil det være en god ide at udpege en (eller flere - afhængigt af virksomhedens størrelse, kompleksitet og afhængighed af it) it-sikkerhedsansvarlig.

---

## Related Topics
- Link
- 

---

## Resources
- [Risikoanalyse Læringsobjekt](https://rise.articulate.com/share/3OFhzndjv3iHVsNDbNguD9Bs9zs4CN8q#/lessons/ErvldP_S0g8T5vbPdpVPuxUDyveWzU9J)
- 