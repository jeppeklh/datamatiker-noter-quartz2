
> [!tldr] Definition
> Validering handler om at sikre, at systemet **giver den ønskede værdi** til kunden/brugeren.  
> - Intet krav “glemmes”  
> - Ingen uønsket ekstra-funktionalitet  
> - Ingen “tangentfejl” (forkert funktionalitet)

---

### Sporbarhed og den røde tråd
- **Sporbarhed**: Hvert artefakt i udviklingsprocessen skal kunne kobles tilbage til et kundekrav.  
- **Rød tråd**: Fra kravindsamling → design → implementering → test → færdigt produkt.

---

### Eksempler på valideringsaktiviteter
For hvert artefakt stiller du spørgsmål som fx:

1. **Business Model Canvas (BMC)**  
   - Kan kunden/brugeren genkende og relatere til modellen?  
   - Svarer modellen til den virkelige verden?

2. **Business Case (BC)**  
   - Understøtter business casen det ønskede område i BMC’en?  
   - Er det ønskede område tydeligt beskrevet?

3. **Business Proces Model (BPM)**  
   - Fremgår den beskrevne forretningsproces af business casen?  
   - Er der overensstemmelse med beskrivelsen i BC?

4. **Use Case (UC)**  
   - Er UC’en en del af en systeminteraktion i BPM?  
   - Stemmer aktør og swimlane overens med BPM?  
   - Lever UC’en den ønskede værdi fra BPM?

5. **Domænemodel**  
   - Bruger klasser og attributter korrekt domæne-jargon?  
   - Stammer termerne fra en use case?

6. **System Sequence Diagram (SSD)**  
   - Matcher SSD’et 1:1 med UC (samme aktør, interaktioner, alternativer)?

7. **Operation Contract (OC)**  
   - Beskriver OC’en en interaktion fra SSD?  
   - Bruges de samme domæne-begreber som i domænemodellen?

8. **Specification Diagram (SD)**  
   - Stammer SD’en fra en SSD-interaktion + tilhørende OC?  
   - Overensstemmelse mellem OC og SD (operation, pre/post-conditions)?

9. **Design Class Diagram (DCD)**  
   - Overensstemmelse mellem UI-lag, use cases og evt. wireframes?  
   - Forretningslogik (klasser/metoder) spores tilbage til use cases?  
   - Sammenhæng med domænemodel (navngivning, attributter)?

1. **Implementering (klasser, metoder, kald)**  
    - Findes klasserne/metoderne som beskrevet i DCD/SD?  
    - Stemmer parametre og signaturer overens med designet?

---

### Eksempel på “rød tråd” gennem artefakter
**Krav**: Brugeren skal kunne oprette en profil med navn og e-mail.  
 1. **UC** “Opret profil” → aktør “Bruger” → flow: indtast navn, indtast e-mail.  
 2. **Domænemodel** → `User`-klasse med attributter `name`, `email`.  
3.  **SSD** → beskrevne beskeder: `enterName()`, `enterEmail()`, `submit()`.  
4.  **OC** på `createUser(name,email)` med pre/post-conditions.  
5.  **DCD** → `UserService.createUser(String name, String email)`.  
6.  **Implementering** → klasse og metode med nøjagtigt samme signatur og logik.  
7.  **Test** → automatiseret test, der sender en profil-oprettelsesanmodning og tjekker, at databasen indeholder de indtastede værdier.

---

### Validering alene er ikke nok!
- Et fuldt kvalitetsbillede kræver også **verificering**:
  - Stabilitet, sikkerhed, ydeevne, skalérbarhed  
  - Interne kvalitetskriterier, arkitekturmæssig korrekthed

**Næste skridt**: [[Verificering]] – tests, reviews og automatisering for at sikre korrekthed “på dybden”.

---

## Resourcer
- [Validering og Verificering Læringobjekt (Validering)](https://rise.articulate.com/share/yGM2iQz7nvEApmTC2NUBqtcmqts_AovC#/lessons/39EkJsOd3V9ZGPyJgm5ThCaCcaF-RtJu)