
## Principper
---
### 1. **Proactivity**

- **Definition**: Implement data protection measures early, anticipating risks before they arise.
- **Example**: The cinema's database system is designed with automatic alerts to notify administrators of any unusual access attempts, preventing potential data breaches.

### 2. **Default Privacy (Standardindstilling)**

- **Definition**: Ensure that data protection is the default setting, requiring no additional action from users.
- **Example**: When creating a customer profile, the cinema database automatically limits data visibility to only what is necessary for booking, without requiring users to adjust settings.

### 3. **Privacy by Design (Integreret i designet)**

- **Definition**: Incorporate privacy features into the system from the beginning, not as an afterthought.
- **Example**: The cinema database encrypts all customer data upon entry and stores it securely, with privacy considerations built into the initial design.

### 4. **Full Functionality (Fuld funktionalitet)**

- **Definition**: Balance data protection with system functionality, ensuring no compromise on either.
- **Example**: The cinema's booking system allows users to easily manage their bookings while ensuring their personal data is protected through encryption and access controls.

### 5. **End-to-End Security (Vugge-til-grav)**

- **Definition**: Protect data throughout its entire lifecycle—from collection to deletion.
- **Example**: Customer data in the cinema database is securely collected, stored, and deleted after a specified retention period, ensuring no residual data is left unprotected.

### 6. **Transparency (Synlighed og gennemsigtighed)**

- **Definition**: Ensure all data processing activities are visible and understandable to users.
- **Example**: The cinema provides clear, accessible privacy policies on how customer data is used and allows customers to view and manage their data within their profile.

### 7. **User-Centricity (Brugerorienteret)**

- **Definition**: Prioritize user needs and rights, providing clear information and control over their data.
- **Example**: The cinema app allows customers to easily opt in or out of marketing communications and to view and delete their personal data at any time.

### 8. **Accountability (Ansvarlighed)**

- **Definition**: Be able to demonstrate compliance with GDPR principles.
- **Example**: The cinema keeps detailed logs of data access and processing activities, ensuring they can provide evidence of GDPR compliance if required.

### 9. **Purpose Limitation (Formålsbegrænsning)**

- **Definition**: Collect and process personal data only for specific, legitimate purposes.
- **Example**: The cinema only collects customer email addresses for sending booking confirmations and does not use them for unrelated marketing purposes without explicit consent.

### 10. **Data Minimization (Dataminimering)**

- **Definition**: Only collect data that is necessary for the specified purpose.
- **Example**: The cinema database collects only the customer's name and email for booking, avoiding unnecessary data like home address unless required for a specific service.

### 11. **Lawfulness, Fairness, and Transparency (Lovlighed, rimelighed og gennemsigtighed)**

- **Definition**: Process personal data legally, fairly, and transparently.
- **Example**: The cinema obtains explicit consent from customers before storing their data and clearly explains how their data will be used.

### 12. **Accuracy (Rigtighed)**

- **Definition**: Keep personal data accurate and up-to-date.
- **Example**: The cinema database prompts customers to update their contact information regularly to ensure accurate records.

### 13. **Integrity and Confidentiality (Integritet og fortrolighed)**

- **Definition**: Protect data from unauthorized access and ensure its accuracy and reliability.
- **Example**: The cinema's system uses strong passwords, encryption, and regular security audits to safeguard customer data.

### 14. **Storage Limitation (Opbevaringsbegrænsning)**

- **Definition**: Keep personal data only as long as necessary for its purpose.
- **Example**: The cinema automatically deletes customer data after one year if no further bookings are made, ensuring data is not stored longer than needed.

## Krav og guidelines
---
### 1. **Kravindsamling**

- **Proaktivitet**:
    
    - **Krav**: Identificer og dokumentér alle potentielle databeskyttelsesrisici tidligt i processen.
    - **Guideline**: Inkludér sikkerhed og persondatabeskyttelse som faste punkter i alle kravspecifikationer.
- **Formålsbegrænsning**:
    
    - **Krav**: Definér klare og specifikke formål for dataindsamling.
    - **Guideline**: Hver eneste databehandlingsaktivitet skal knyttes til et klart formål, som skal dokumenteres.
- **Dataminimering**:
    
    - **Krav**: Indsaml kun de data, der er absolut nødvendige for at opfylde det definerede formål.
    - **Guideline**: Lav en data audit for at sikre, at unødvendige data ikke indsamles eller lagres.

### 2. **High-Level Design**

- **Standardindstilling (Default Privacy)**:
    
    - **Krav**: Standardindstillingerne i systemet skal altid beskytte brugerens data bedst muligt.
    - **Guideline**: Design brugergrænseflader, så brugere ikke aktivt skal ændre indstillinger for at beskytte deres data.
- **Privacy by Design**:
    
    - **Krav**: Integrér databeskyttelse i alle systemkomponenter og funktioner fra starten.
    - **Guideline**: Inddrag privacy-experter i designfasen for at sikre, at databeskyttelse er en central del af systemarkitekturen.
- **Synlighed og gennemsigtighed**:
    
    - **Krav**: Gør det tydeligt og let for brugere at forstå, hvordan deres data bruges.
    - **Guideline**: Udvikl intuitive interfaces og dokumentation, der tydeligt forklarer databehandling og indsamling.

### 3. **Low-Level Design**

- **Integreret i designet (Privacy by Design)**:
    
    - **Krav**: Privacy skal være en kernekomponent i alle tekniske beslutninger.
    - **Guideline**: Implementer kryptering, anonymisering og pseudonymisering som standardmetoder i datalagring og -transmission.
- **Integritet og fortrolighed**:
    
    - **Krav**: Sikr, at data forbliver nøjagtige og beskyttede mod uautoriseret adgang.
    - **Guideline**: Brug adgangskontrolmekanismer og krypteringsprotokoller for at sikre dataintegritet og fortrolighed.
- **Opbevaringsbegrænsning**:
    
    - **Krav**: Data skal kun opbevares så længe, som det er nødvendigt for det specificerede formål.
    - **Guideline**: Design mekanismer til automatisk sletning af data efter udløb af deres opbevaringsperiode.

### 4. **Programmering**

- **Fuld funktionalitet**:
    
    - **Krav**: Implementér løsninger, der balancerer privacy og brugervenlighed uden kompromiser.
    - **Guideline**: Test for at sikre, at privacy-funktioner ikke skaber friktion i brugeroplevelsen.
- **Rigtighed**:
    
    - **Krav**: Sikr, at alle data i systemet er korrekte og opdaterede.
    - **Guideline**: Implementér validerings- og verifikationsrutiner for at kontrollere datakvalitet ved input.
- **Ansvarlighed**:
    
    - **Krav**: Dokumentér alle processer, der vedrører persondatahåndtering, så de kan revideres.
    - **Guideline**: Implementér logning af alle databehandlingsaktiviteter og inkluder dem i revisionsspor.

### **Output: Liste over Kvalitetskrav/Guidelines**

1. **Tidlig identifikation og dokumentation af databeskyttelsesrisici**.
2. **Definér og dokumentér klare formål for dataindsamling**.
3. **Indsaml kun nødvendige data (dataminimering)**.
4. **Default privacy-indstillinger i systemdesign**.
5. **Integrér databeskyttelse i systemets arkitektur (Privacy by Design)**.
6. **Udvikl brugervenlige grænseflader med klare databeskyttelsesinformationer**.
7. **Anvend kryptering, anonymisering og adgangskontrol i tekniske løsninger**.
8. **Implementér automatisk datadestruktion efter opbevaringsperiode**.
9. **Balancér privacy og funktionalitet uden at kompromittere brugeroplevelsen**.
10. **Sikring af datakvalitet gennem valideringsrutiner**.
11. **Dokumentation og logning af databehandlingsaktiviteter for ansvarlighed**.

