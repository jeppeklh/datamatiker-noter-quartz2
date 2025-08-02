---
aliases:
  - 1NF
---
tags: #Programmering #SQL

> [!tldr] Definition
> For at en tabel skal være i den første normale form, skal den følge følgende 4 regler:
>
> 1. En tabel er i 1NF, hvis den kun indeholder atomære værdier.
>    
> 2. Værdier gemt i en kolonne skal være af samme domæne (samme datatype). 
>    
> 3. Alle kolonner i en tabel skal have unikke navne. 
>    
> 4. Og rækkefølgen, som data opbevares i, burde ikke betyde noget.

---

## Example

|   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|
|**Student_ID**|**Name**|**Contact**|**College**|**Course**|**Teacher**|**Rank**|
|100|Jens|73009348, 11111111|UCL|Programming, Systemudvikling|Thomas, Lene|2|
|102|Patrick|73009015|UCL|Programming|Thomas|2|
|103|Pia|73009367|UCL|Programming|Thomas|2|

---

### Atomære værdier
Nogle celler i tabellen indeholder flere værdier, som bryder den første regel i 1NF.
Til at løse problemet, skal vi lave tabellen om, hvor de flere værdier bliver opdelt i nye rækker eller kolonner.

Der blev tilføjet en ny kolonne Contact til at persistere den anden kontakt oplysninger. Der blev også opdelt Course og Teacher i ny række.

|                |          |          |             |             |                 |             |          |
| -------------- | -------- | -------- | ----------- | ----------- | --------------- | ----------- | -------- |
| **Student_ID** | **Name** | Contract | **Contact** | **College** | **Course**      | **Teacher** | **Rank** |
| 100            | Jens     | 73009348 | 11111111    | UCL         | Programming     | Thomas      | 2        |
| 100            | Jens     | 73009348 | 11111111    | UCL         | Systemudvikling | Lene        | 2        |
| 102            | Patrick  | 73009015 |             | UCL         | Programming     | Thomas      | 2        |
| 103            | Pia      | 73009367 |             | UCL         | Programming     | Thomas      | 2        |


---

### Kolonner i en tabel skal have unikke navne
Nu har vi to kolonner, der har det samme navn. Det bryder 1NF.

Den kan løses på at kalde de to kolonner forskellige navne, som Contact1 og Contact2. 
Men denne løsning er ikke optimal, fordi hvis en studerende har for eksempel 5 kontakt oplysninger, er det en god ide, at have en liste af Contact kolonner i tabellen, kun for at persistere de oplysninger for få studerende?  
  
Nej den er ikke en god ide, hvad er så løsningen til det. Løsningen er at opdele tabellen i to tabeller og forbinde dem med en fremmednøgle. Se nedenfor.

![[Den første normalform eksempel.png]]

---

## Related Topics
- Link 

---

## Resources
- Link
- 