
- **Nøglebudskaber:**    
    - Seks almindelige deployment-strategier: **Big Bang, Rolling, Recreate, Canary, Blue/Green, Shadow**
    - Valg af strategi afhænger af: applikationens kompleksitet, teamets færdigheder, risikotolerance, ressourceforbrug og ønsket nedetid.
    - **Feature Flags** skiller deployment fra release, hvilket giver fleksibilitet og reducerer risici.

- **Baggrund:**
    - Traditionelle deployment-strategier krævede typisk ekstra infrastruktur (fx load balancers, flere Kubernetes-klustre).

    - Med feature management kan du skifte fra hardware-centrerede til kode-centrerede løsninger, hvilket reducerer omkostninger og kompleksitet.



## Deployment vs. Releases
---
- **Traditionelt:**
    - **Release:** Frysning af kode og klar til produktion – efter en validering i staging.
    - **Deployment:** Flytningen af koden til produktion, hvilket gør applikationen "live".

- **Moderne tilgang med feature flags:**
    - **Deployment kommer før release:** Koden er deployeret, men nye funktioner aktiveres via feature flags.
    - **Feature-for-feature release:** Giver mulighed for gradvis aktivering af nye funktioner uden at påvirke alle brugere med det samme.




## De 6 Deployment Strategier
---
### 1. Big Bang Deployment
---
- **Beskrivelse:**
    - Hele applikationen deployeres på én gang, så alle brugere bliver ramt samtidig.

- **Fordele:**
    - Enkel og hurtig implementering.

- **Ulemper:**
    - Høj risiko – hvis der opstår problemer, berøres alle brugere.
    - Komplekst rollback for hele systemet.
    - Traditionelt med nedetid under deployment.

- **Brug med Feature Flags:**
    - Feature flags kan implementeres som en "kill switch" for hurtigt at deaktivere hele releasen eller aktivere nye funktioner gradvist.



### 2. Rolling Deployment
---
- **Beskrivelse:**
    - Ændringer rulles gradvist ud til en lille procentdel af brugerne, indtil alle er opdateret.

- **Fordele:**
    - Mindre risiko, da eventuelle problemer kun påvirker en lille gruppe.
    - Nemmere rollback: Trafikken kan hurtigt omdirigeres til den tidligere version.

- **Ulemper:**
    - Mere kompleks at styre, da trafikfordelingen skal håndteres omhyggeligt (fx "sticky sessions").

- **Brug med Feature Flags:**
    - Automatiseret gradvis aktivering via fx LaunchDarkly, der kan stoppe rollout, hvis der registreres problemer.



### 3. Recreate Deployment
---
- **Beskrivelse:**
    - Den tidligere version stoppes og hele miljøet genopbygges med den nye version.

- **Fordele:**
    - Simpel og forudsigelig proces.

- **Ulemper:**
    - Kræver nedetid.
    - Rollback kan være kompliceret.
    - Ofte bedst egnet til ikke-produktionsmiljøer (fx dev eller QA).


### 4. Canary Deployment
---
- **Beskrivelse:**
    - Kun et lille segment af brugerne udsættes for den nye version (navnet refererer til “canary in the coal mine”).

- **Fordele:**
    - Tidlig fejldetektion.
    - Brugerfeedback fra en lille, målrettet gruppe (fx "power users").
    - Mulighed for nem rollback, når kun få brugere er ramt.

- **Ulemper:**
    - Kan kræve ekstra opsætning for at målrette specifikke brugergrupper.
    - Kan øge kompleksiteten, hvis der skal styres flere infrastruktursæt.


### 5. Blue/Green Deployment
---
- **Beskrivelse:**
    - To identiske miljøer: den nuværende ("blue") og den nye version ("green").
    - Trafikken omdirigeres til "green", når den nye version er testet.

- **Fordele:**
    - Næsten nul nedetid.
    - Enkel og hurtig rollback, da den gamle version stadig er kørende.
    - Muliggør test i produktion.

- **Ulemper:**
    - Kræver investering i dobbelt infrastruktur (selvom nogle ressourcer kan deles).

- **Brug med Feature Flags:**
    - Med feature flags kan du simulere blue/green uden at have to fuldstændigt separate miljøer.


### 6. Shadow Deployment
---
- **Beskrivelse:**
    - Den nye version kører parallelt med den eksisterende, hvor rigtige forespørgsler kopieres til den nye version og analyseres, uden at brugeren oplever ændringer.

- **Fordele:**
    - Mulighed for at teste den nye version under reel belastning.
    - Ingen indvirkning på den faktiske brugeroplevelse.

- **Ulemper:**
    - Komplekst setup – kræver duplikering af trafik og ekstra monitoreringsinfrastruktur.
    - Øget overhead ved at administrere to miljøer sideløbende.

- **Brug med Feature Flags:**
    - Feature flags kan hjælpe med hurtigt at aktivere eller deaktivere den nye version, hvis tester viser problemer.



## Overvejelser ved Valg af Deployment Strategi
---
Når du skal vælge en deployment-strategi, bør du tage højde for følgende faktorer:

- **Applikationsegenskaber:**
    - **Størrelse og kompleksitet:** En simpel applikation kan ofte klare sig med en enkel strategi, mens komplekse systemer kan have brug for blue/green eller canary deployments.
    - **Toleranceniveau for nedetid:** Applikationer med lav tolerance for nedetid (fx e-handel) kræver strategier med minimal eller ingen nedetid.

- **Teamets kapacitet:**
    - **Færdigheder og erfaring:** Mere komplekse strategier kræver typisk specialiserede kompetencer.
    - **Ressourcer:** Både menneskelige og finansielle ressourcer spiller ind – fx er blue/green krævende, hvis du skal køre to fuldstændige miljøer.

- **Deployment Goals:**
    - **Release Frequency:** Hvis du deployerer ofte, kan progressive strategier som rolling eller canary være at foretrække.
    - **Brugerimpact og risikotolerance:** Strategier, der begrænser risikoen ved at ramme en mindre brugergruppe (fx canary), er attraktive, hvis risikotolerancen er lav.
    - **Rollback muligheder:** Hurtige og pålidelige rollback-mekanismer er essentielle ved kritiske applikationer.
    

## Rollen for Feature Flags
---
- **Separation af Deployment og Release:**
    - Med feature flags kan kode deployeres til produktion, men de nye funktioner aktiveres først, når de er klar, hvilket reducerer risikoen for fejl og nedetid.

- **Forbedret Risikostyring:**
    - Mulighed for øjeblikkelig deaktivering af fejlbehæftede funktioner uden en fuldstændig rollback af hele systemet.

- **Fleksibilitet:**
    - Feature flags gør det muligt at starte med en canary-udrulning og efterfølgende skifte til en rolling deployment, alt efter hvordan testresultaterne udfolder sig.
    
## Resourcer
---
- [6 Deployment strategies](https://launchdarkly.com/blog/deployment-strategies/)