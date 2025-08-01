---
aliases:
  - LLD
---
>[!tldr] Definition
Low Level Design fokuserer på designet af kode og den interne struktur i systemet. Her ser du systemet som en "white box", hvilket betyder, at du kigger ind i systemets indre virkemåde og ser, hvordan de enkelte dele – såsom klasser og metoder – samarbejder.

> ([[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=191&selection=47,1,55,1|Rod Stephens p.155]])
> High- level design focuses on what. Low-level design begins to focus on how.


---

## Formål og Fokus
---
- **Detaljeret intern struktur:**  
  LLD handler om at beskrive, hvad der sker inde i systemet, når en bruger interagerer med det. Det inkluderer:
  - Hvordan brugerinteraktioner bevæger sig gennem systemet.
  - Hvordan koden er opdelt i klasser, metoder og andre enheder.
  
- **Artefakter til programmører:**  
  De artefakter, du udarbejder i LLD, skal kunne fungere som grundlag for programmørerne, der skal implementere systemets kode. Sproget i disse dokumenter er engelsk.

- **En del af den samlede udviklingsproces:**  
  Selvom de fleste detaljer om LLD læres i programmeringsundervisningen, er LLD en integreret del af systemudviklingsprocessen og understøtter overgangen fra design til implementering.


## Systemet som White Box
---
I LLD betragtes systemet som en gennemsigtig kasse, hvor du ser de interne mekanismer og processer. Derudover har du fokus på:

- **Designmønstre:**  
  Implementering af anerkendte designmønstre kan bidrage til et robust og velstruktureret system. Eksempler på designmønstre inkluderer:
  - GRASP
  - SOLID
  - **Gang of Four**

  Valget af designmønstre bør afstemmes med systemkrav, constraints og de overordnede formål med dine teknikker.


## Kvalitetssikring
---
Når du kvalitetssikrer dit LLD, skal du fokusere på to hovedspørgsmål:

1. **Laver du det rigtige system?**  
   - Der skal være direkte sporbarhed til dine [[Repo/01 - Systemudvikling og virksomhed/Systemudviklingsmetoder/Proces/High Level Design|High Level Design]]-artefakter, så du sikrer, at LLD bygger videre på den konceptuelle forståelse og de krav, der er fastlagt i HLD.

2. **Laver du systemet rigtigt?**  
   - Hvert LLD-artefakt skal opfylde fastsatte kvalitetskriterier, der sikrer, at designet er fagligt korrekt og implementerbart. Disse kriterier skal understøtte en robust, vedligeholdelsesvenlig og korrekt opbygget kodebase.



Ved at fokusere på både de interne strukturer og kvalitetssikringen af dine LLD-artefakter sikrer du, at systemet ikke blot bliver designet korrekt på overfladen, men også fungerer optimalt i praksis.

## Resourser
---
- [Fokusområde Læringsobjekt (LLD)](https://rise.articulate.com/share/C9x7c641Qf8pDgT76Nqqy6ykP99dRgRJ#/lessons/IHDGRK5qcsNgB0DY7Cxi8q8JCxh-jftP)