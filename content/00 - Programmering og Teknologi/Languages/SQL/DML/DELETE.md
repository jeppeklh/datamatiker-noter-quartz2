tags: #Programmering #SQL #SQLBasics #Statement

## Definition 
---
DELETE-sætningen giver dig mulighed for at fjerne bestemte rækker fra din [[Repo/00 - Programmering og Teknologi/Languages/SQL/Basics/Database|database]] baseret på specifikke betingelser.
## Syntax
---
```sql
DELETE FROM table_name
WHERE condition;
```
### Example
---
Lad os antage, at du vil slette en deltager fra PARTICIPANT-tabellen, hvis Email-adressen er ``student@example.com``.
```SQL
DELETE FROM PARTICIPANT
WHERE Email = 'student@example.com';
```

## Sletning af flere rækker
---
Hvis du vil slette alle deltagere fra PARTICIPANT-tabellen, der tilhører 1. semester.
```SQL
DELETE FROM PARTICIPANT
WHERE SemesterId = 1;
```

## Related Topics
---
- [[SQL Syntax|SQL Syntax]]
- [[SELECT]]
- [[INSERT]]
- [[UPDATE]]
- [[CREATE TABLE]]
- [[ALTER TABLE]]
- [[DROP TABLE]]

## Resources
---
- [DDL Læringsobjekt (DELETE)](https://scorm.itslearning.com/data/3289/C20150/ims_import_14/scormcontent/index.html#/lessons/KlnHrkqVt6pv5ORcfQtK9O43ivOQyKqJ)
- [DELETE YouTube Video](https://www.youtube.com/watch?v=51aUxr8WM-8)