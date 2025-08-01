>[!tldr] Definition
Sikring af det fremstillede produkt lever op til de krav og det design, vi har beskrevet. 
>
Målet med test er ikke nødvendigvis at skabe et fejlfrit system, men at være bevidste om potentielle fejl og vide, hvordan de skal håndteres.

---

## Formål

- **Verificere krav og design:**  
  Test skal sikre, at systemet lever op til de krav og den konceptuelle forståelse, som er fastlagt i [[Repo/01 - Systemudvikling og virksomhed/Systemudviklingsmetoder/Proces/High Level Design|High Level Design]] og [[Repo/01 - Systemudvikling og virksomhed/Systemudviklingsmetoder/Proces/Low Level Design|Low Level Design]].

- **Håndtering af uventede situationer:**  
  Udover at teste, at systemet virker under forventede forhold, skal man også undersøge, hvad der sker, når der opstår uventede input eller situationer.

---

## Testniveauer

Testning kan udføres på flere niveauer, hvor hvert niveau har sit specifikke formål:

1. **Test på det konceptuelle niveau (Black Box Testing):**  
   - Test, om systemet opfører sig som forventet i forhold til [[Repo/01 - Systemudvikling og virksomhed/Systemudviklingsmetoder/Proces/Kravindsamling|krav]] og [[Repo/01 - Systemudvikling og virksomhed/Systemudviklingsmetoder/Proces/High Level Design|HLD]].
   - Brugeren tester systemet uden at kigge ind i den interne kode.

2. **Test på det designmæssige niveau (Grey Box Testing):**  
   - Test af sammenhængen og integrationen mellem systemets dele, som beskrevet i [[Repo/01 - Systemudvikling og virksomhed/Systemudviklingsmetoder/Proces/Low Level Design|LLD]].
   - Her vurderes, om processerne bevæger sig gennem koden, som planlagt, uden at gå i detaljer med den enkelte kodelinje.

3. **Test på programmeringsniveau (White Box Testing):**  
   - Test af selve koden for at sikre, at den virker korrekt, er struktureret og overholder best practice.
   - Giver mulighed for at inspicere koden i detaljer.

> **Bemærk:** Formålet med de forskellige testniveauer er at afdække, hvad der præcis skal testes, og det bør afspejles i de testteknikker, du har valgt i din systemudviklingsmetode.

---

## Testplan

For at opnå et tilstrækkeligt fokus på test anbefales det at udarbejde en testplan, der indeholder:
- **Testdesign:** Hvornår og hvordan tests udformes/skabes.
- **Testgennemførelse:** Hvornår tests køres, og hvem (eller hvilken rolle) der er ansvarlig for at udføre dem.

Testplanen afhænger både af den overordnede systemudviklingsmetode og den valgte procesmodel, som kan påvirke timingen for både testdesign og testgennemførelse.

---

## Kvalitetssikring af Test

For at sikre, at testene er effektive og dækker de nødvendige aspekter, skal du:

- **[[Validering]]:**  
  Sørge for, at testene er sporbare tilbage til de oprindelige krav. Det handler om at sikre, at du tester de rigtige ting.

- **[[Verificering]]:**  
  Bekræfte, at testene udføres korrekt i forhold til deres tiltænkte formål.

Ved at kombinere test på flere niveauer med en veldefineret testplan og løbende kvalitetssikring, kan du tidligt opdage fejl og dermed forhindre, at de spreder sig i systemet.

## Resourser
---
- [Fokusområde Læringsobjekt (Test)](https://rise.articulate.com/share/C9x7c641Qf8pDgT76Nqqy6ykP99dRgRJ#/lessons/Gd6kIHcvWgcNX90QA0dyKB33N83Jexgj)