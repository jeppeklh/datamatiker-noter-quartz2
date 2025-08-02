
En af fordelene ved virtualisering er de ekstra muligheder, den giver for disaster recovery. De fleste [[Hypervisor|hypervisorer]] inkluderer værktøjer, der gør det muligt at gemme en virtuel maskines tilstand på et givent tidspunkt – ofte kaldet **snapshots** eller **checkpoints** – som senere kan bruges til at gendanne maskinen.

---

## Snapshots / Checkpoints
> [!tldr] Definition
> Et snapshot (eller checkpoint) er en lagret kopi af en virtuel maskines tilstand, inklusive data, konfiguration og hukommelse, på et bestemt tidspunkt.

##### Anvendelse:
  Snapshots bruges ofte før vigtige administrative opgaver, som f.eks. installation af en service pack. Hvis der opstår problemer efter ændringen, kan systemet hurtigt rulles tilbage til den stabile tilstand, snapshot'et repræsenterer.

##### Begrænsninger og Overvejelser
  - **Diskplads:** Et snapshot kræver betydelig diskplads, ofte svarende til størrelsen af hele den virtuelle disk. Flere snapshots kan hurtigt akkumuleres til en stor mængde data.
  - **Ydeevne:** Når der tages ændringer på en virtuel maskine med eksisterende snapshots, skal hypervisoren skrive ændringerne til både den kørende maskine og til snapshot-filen(erne). Dette kan medføre en performance-nedgang.
  - **Backup vs. Snapshot:**  
    Snapshots er typisk gemt på samme fysiske lagerenhed som den virtuelle maskine, hvilket betyder, at de ikke beskytter mod hardwarefejl. Derfor bør snapshots ikke erstatte traditionelle backups, som bør gemmes på separate medier.

---

## Resourcer
- [Virtualisering LinkedIn Kursus (Disaster Recovery)](https://www.linkedin.com/learning/learning-virtualization-13945890/disaster-recovery?autoSkip=true&resume=false&u=57075649)

