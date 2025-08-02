tags: #Programmering #SQL #SQLBasics

> [!tldr] Definition
> SQL data types define the type of data that can be stored in a [[Table]] column. 

Each column in a [[Table]] is assigned a data type, which determines the kind of data it can hold.

---

## Common Data Types
- [[string]]
- [[int]]
- [[double]] 
- [[float]] 
- [[decimal]]
- [[char]]
- [[bool]]

| C#-datatype (alias)         | Bit-størrelse | .NET-datatype                   | SQL-datatype              | Kommentar                                         |
| --------------------------- | ------------- | ------------------------------- | ------------------------- | ------------------------------------------------- |
| **int**                     | 32-bit        | System.Int32                    | **Int**                   | Cell 5                                            |
| **char**                    | 16-bit        | System.Char                     | **NChar(1), NVarChar(1)** | Cell 10                                           |
| **char[]**   <br>**string** | 32-bit        | System.Array  <br>System.String | **NChar(*), NVarChar(*)** | Unicode-tekstkarakter  <br>(fast/variabel længde) |
| **double**                  | 64-bit        | System.Double                   | **Float**                 | Unicode-tekstkarakter  <br>(fast/variabel længde) |
| **DateTime**                | 64-bit        | System.DateTime                 | **DateTime2**             |                                                   |
| **DateOnly**                | ?             | System.DateOnly                 | **Date**                  | Ny i .NET 6                                       |
| **TimeOnly**                | ?             | System.TimeOnly                 | **Time**                  | Ny i .NET 6                                       |
| **bool**                    | 8-bit         | System.Boolean                  | **Bit**                   |                                                   |
NChar repræsenterer i SQL Server en fastlængde-tekststreng og NVarChar en variabellængde-tekststreng.

En string er i realiteten et (mere styret) array af char. Skulle man have lyst til at repræsentere dette eksplicit, dvs. som char[] i C#, så vælges i begge tilfælde enten NChar(*) eller NVarChar(*) som SQL-datatyper, hvor * angiver det antal tegn, tekststren­gen skal indeholde.

Der er i SQL-Server ingen repræsentation for en enkelt karakter, så en char repræsenteres med en tekststreng med længden 1. 
Dette kan gøres på en af to måder: enten med NChar(1) eller med NVarChar(1).

NVarChar understøtter Unicode(andre end standard tegn. eks. Arabisk, Kyrrylisk, emojis osv.)
VarChar gør ikke. 

---

## Related Topics
- [[SQL Syntax|SQL Syntax]]
- [[Constraints]]
- [[SQL Standards]]

---

## Resources
- Link
- 