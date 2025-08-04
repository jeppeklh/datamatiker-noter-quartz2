### **Overordnet proces:**

Diagrammet repræsenterer en ferieplanlægningsproces, som involverer tre primære aktører (swim lanes):

1. **Medarbejdere**:
    
    - De er ansvarlige for at indtaste deres ferieønsker i systemet.
    - Hvis de overskrider fristen, modtager de besked og instrueres i at kontakte deres leder direkte.
2. **Alfa Laval-systemet**:
    
    - Registrerer input fra medarbejderne og håndterer beregning af et ferieplanforslag.
    - Sender påmindelser eller opdateringer til både medarbejdere og ledere.
    - Understøtter lederen med visualisering og status over ferieinput.
3. **Ledere**:
    
    - De skaber og administrerer ferieperioder, sikrer at alle medarbejdere har indgivet ønsker, og godkender endelige ferieplaner.
    - Hvis medarbejdere mangler at indtaste ønsker, kan lederen manuelt indtaste dem i systemet.

---

### **Procesgennemgang**:

1. **Medarbejdere får besked**:
    
    - Processen starter med, at medarbejderne får besked om at indtaste deres ferieønsker inden en given dato.
2. **Medarbejder input**:
    
    - Medarbejdere logger deres ferieønsker i systemet.
    - Hvis ikke alle medarbejdere indtaster ønsker inden fristen, får lederen besked om, hvem der mangler, og kan indtaste manglende ønsker.
3. **Lederens rolle**:
    
    - Lederen opretter en ferieperiode med en start- og slutdato og definerer, hvor mange der kan holde ferie ad gangen.
    - Når input fra medarbejderne er samlet, kan lederen indtaste ekstra bemandingskrav i systemet (f.eks. procent af minimumsbemanding).
4. **Ferieplanberegning**:
    
    - Systemet udarbejder et ferieplanforslag baseret på input fra medarbejdere og lederens kriterier.
5. **Godkendelse**:
    
    - Lederen gennemgår og godkender ferieplanforslaget.
    - Efter godkendelse offentliggøres den færdige ferieplan til medarbejderne.

---

### **Vigtige flows i modellen**:

- **Parallelle aktiviteter**:
    
    - Systemet sender både påmindelser og registrerer ferieinput samtidig, hvilket sikrer effektivitet i processen.
- **Manglende input**:
    
    - Hvis medarbejdere ikke indtaster ferieønsker, træder lederen ind og tager handling. Dette sikrer, at processen kan fortsætte uden forsinkelser.
- **Automatiserede funktioner**:
    
    - Beregningen af ferieplanforslaget er automatiseret, hvilket reducerer fejl og sparer tid.