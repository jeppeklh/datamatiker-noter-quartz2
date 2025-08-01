---
aliases:
  - Rapid Application Development
---
>[!tldr] Definition
**RAD (Rapid Application Development)** er en systemudviklingsmetode, der fokuserer på at levere brugbar software hurtigt gennem korte iterationer og tæt samarbejde med kunder. I modsætning til traditionelle modeller (fx vandfaldsmodellen) prioriterer RAD hastighed og fleksibilitet uden at ofre kvalitet.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=502&selection=21,0,25,7|p.466]]

---
## Kerneprincipper
---
- **Korte iterationer**: Udvikling opdeles i faser på uger/måneder med hyppige leverancer.
- **Konstant kundefeedback**: Kunder tester løbende og justerer krav undervejs.
- **Tidsboxing (Timeboxing)**: Fast deadline for hver iteration (omfang kan justeres).
- **Små teams**: 2-6 personer for hurtig kommunikation.
- **Prototyping**: Hurtige mockups til at afklare krav.
- **Fokus på genbrug**: Eksisterende kode/rammer bruges, hvor det er muligt.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=503&selection=13,0,13,14|p.467]]
## James Martin RAD (Original Model)
---
1. **Kravplanlægning**: Overordnede mål og krav aftales.
2. **Brugerdesign**: Kunder og udviklere designer sammen via workshops/prototyper.
3. **Konstruktion**: Udvikling med løbende feedback.
4. **Overgang (Cutover)**: Implementering og support.

![[JamesMartinRAD.png]]
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=506&selection=8,0,8,16|p.470]]
## Fordele
---
- Hurtigere leverance af funktionel software.
- Mindre risiko for fejlfortolkede krav.
- Fleksibilitet til ændringer undervejs.
- Tidlig fejlafhjælpning gennem konstant test.

## Ulemper
---
- Uegnet til store projekter (kommunikation bliver kompleks).
- Kræver erfarne udviklere og dedikerede kunder.
- Design kan blive suboptimalt pga. korte deadlines.
- Svær at planlægge budget/tid på forhånd.

## Misforståelser om RAD
---
- **RAD ≠ værktøjer**: Visse udviklingsværktøjer kaldes "RAD", men metoden handler om proces, ikke teknologi.
- **Ikke kun prototyping**: RAD inkluderer også strukturerede faser som kravgenskabelse.

## Iteration 0 (Startfasen)
---
Kort forberedelsesfase inden første iteration:
- Opsætning af miljø (værktøjer, servere).
- Indledende kravindsamling.
- Teamet samles og roller defineres.
[[Rod Stephens - Beginning Software Engineering (2022, Wiley) - libgen.li.pdf#page=504&selection=48,0,50,1|p.468]]
## Konklusion
---
RAD passer bedst til projekter, hvor kravene er flydende, og hastighed er altafgørende. Metoden kræver tæt samarbejde mellem udviklere og brugere, men kan reducere risikoen for at levere forkerte løsninger.