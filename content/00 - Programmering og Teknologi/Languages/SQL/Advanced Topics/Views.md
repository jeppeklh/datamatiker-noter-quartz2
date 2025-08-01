tags: #Programmering #SQL #AdvancedTopicsSQL

## Definition 
---
Et **SQL View** er en virtuel tabel, som oprettes ved hjælp af en [[SELECT]]-sætning. 
Det indeholder ikke selv data, men fungerer som en gemt forespørgsel, der henter [[Data|data]] fra en eller flere [[Table|tabeller]]. 

Et view præsenterer et udsnit af [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|Database]], hvor du kan kombinere, filtrere og formatere data uden at ændre de underliggende tabeller
Views kan bruges til at skjule kompleksiteten af databaser eller præsentere data på en mere brugervenlig måde.
## Syntax
---
```sql
CREATE VIEW view_navn AS
SELECT kolonne1, kolonne2, ...
FROM tabel_navn
WHERE betingelse;
```
Når viewet er oprettet, kan det behandles som en virtuel tabel, og forespørgsler kan udføres mod det på samme måde som med en almindelig tabel.
### Eksempel 1: View for studenterfremmøde
---
Vi bruger samme eksempel som fra [[Database Design]]
![[Databasemodel eksempel 4.png]]

Vi kan oprette et view, der viser alle studerende med deres tilstedeværelse i hver lektion.
```sql
CREATE VIEW student_attendance AS
SELECT s.Email AS StudentEmail, p.FirstName, p.LastName, l.Date, sub.Title AS SubjectTitle
FROM PARTICIPANT_LESSON pl
JOIN STUDENT s ON pl.Email = s.Email
JOIN LESSON l ON pl.LessonId = l.LessonId
JOIN SUBJECT sub ON l.SubjectId = sub.SubjectId
JOIN PARTICIPANT p ON s.Email = p.Email;
```

Dette view viser for hver studerende deres navn, datoen for hver lektion, og hvilken fag lektionen var for. 
Du kan bruge dette view til at lave hurtige rapporter over fremmøde for studerende.

Dette udtrækker fremmødeoplysninger for studerende, der har deltaget i Programming-lektioner:
```SQL
SELECT * 
FROM student_attendance 
WHERE SubjectTitle = 'Programming';
```

### Eksempel 2: View for Lektioner i et Semester
---
Vi kan også oprette et view, der viser alle lektioner for et givet semester og hvilket fag de hører til.
```SQL
CREATE VIEW Lessons_Semester AS
SELECT l.LessonId, l.Date, sub.Title AS SubjectTitle, sem.Number AS Semester
FROM LESSON l
JOIN SUBJECT sub ON l.SubjectId = sub.SubjectId
JOIN SEMESTER sem ON sub.SemesterId = sem.SemesterId;
```

Dette view kan bruges til at få overblik over, hvilke lektioner der afholdes i hvert semester, og hvilket fag de er en del af. 
Det er nyttigt for at planlægge semestre og lektioner.

Dette henter alle lektioner, der er planlagt i det første semester.
```SQL
SELECT * 
FROM Lessons_Semester 
WHERE Semester = 1;
```

## Syntaks for at ændre et View
---
```SQL
ALTER VIEW view_navn AS
SELECT kolonne1, kolonne2, ...
FROM tabel_navn
WHERE betingelse;
```

### Eksempel: Opdatering af View for Studenterfremmøde
---
```SQL
ALTER VIEW student_attendance AS
SELECT s.Email AS StudentEmail, p.FirstName, p.LastName, l.Date, sub.Title AS SubjectTitle, sem.Number AS Semester
FROM PARTICIPANT_LESSON pl
JOIN STUDENT s ON pl.Email = s.Email
JOIN LESSON l ON pl.LessonId = l.LessonId
JOIN SUBJECT sub ON l.SubjectId = sub.SubjectId
JOIN PARTICIPANT p ON s.Email = p.Email
JOIN SEMESTER sem ON sub.SemesterId = sem.SemesterId;
```

## Sletning af View
---
```SQL
DROP VIEW view_navn;
```


## Hvorfor Views
---
 - Views hjælper med at forenkle komplekse forespørgsler ved at gemme gentagne forespørgsler i en virtuel tabel, som kan bruges flere gange. 

- Views kan anvendes til at forbedre datasikkerheden ved at begrænse brugeradgangen til specifikke felter eller rækker i tabellerne, hvilket betyder, at følsomme data kan beskyttes uden at ændre i den underliggende struktur.

- Views kan også bidrage til at forbedre ydeevnen, da de kan optimere dataudtræk og reducere kompleksiteten for brugerne.

- Views kan sikre konsistens i rapportering og dataanalyse ved at levere et prædefineret og konsistent datagrundlag.

## Related Topics
---
- [[Uge43 - Views & Stored Procedures|Views & Stored Procedures Opgaver]]
- [[Stored Procedures]]

## Resources
---
- [Views Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_20/scormcontent/index.html#/lessons/LCK_1MxidSYHZeTq3XdkQ6YH2sPFjgL_)
- [SQL Tables vs Views Video](https://www.youtube.com/watch?v=2FtS4G7QrzQ&ab_channel=DashboardGear)
- [How to create a View Video](https://www.youtube.com/watch?v=VfBz6niUFMo&ab_channel=TomFragale-MicrosoftCertifiedTrainer-Author)