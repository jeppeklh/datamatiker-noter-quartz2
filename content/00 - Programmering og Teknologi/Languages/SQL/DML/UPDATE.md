tags: #Programmering #SQL #SQLBasics #Statement

> [!tldr] Definition
> ``UPDATE``-sætningen giver dig mulighed for at ændre værdierne i bestemte kolonner i en tabel baseret på en betingelse.

---

## Syntax
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

---

### Example
```sql
UPDATE PARTICIPANT
SET FirstName = 'Johan'
WHERE Email = 'jens@example.com';
```
Denne sætning opdaterer FirstName til "Johan" for den deltager, hvis e-mail er`` jens@example.com``.

---

## Opdatering af flere rækker
Hvis du vil ændre SemesterId for alle deltagere til 2:
```SQL
UPDATE PARTICIPANT
SET SemesterId = 2;
```

Hvis du vil opdatere alle deltagere i 1. semester til et nyt semester (for eksempel 2. semester), kan du bruge en UPDATE-sætning, hvor du angiver en betingelse med WHERE-klau­sulen for kun at målrette de rækker, hvor SemesterId er 1:

```SQL
UPDATE PARTICIPANT
SET SemesterId = 2
WHERE SemesterId = 1;
```

---

## Opdatering af flere kolonner i en enkelt række
Hvis du skal opdatere både fornavn og efternavn for en deltager:
```SQL
UPDATE PARTICIPANT
SET FirstName = 'Peter', LastName = 'Jensen'
WHERE Email = 'jens@example.com';
```

---

## Related Topics
- [[SQL Syntax|SQL Syntax]]
- [[SELECT]]
- [[INSERT]]
- [[DELETE]]
- [[CREATE TABLE]]
- [[ALTER TABLE]]
- [[DROP TABLE]]

---

## Resources
- [DDL Læringsobjekt (UPDATE)](https://scorm.itslearning.com/data/3289/C20150/ims_import_14/scormcontent/index.html#/lessons/k027wp9IyBDD0tJCNtpU6qedY5XVhJNK)
- 