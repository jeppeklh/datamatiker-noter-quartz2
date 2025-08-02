tags: #Programmering #SQL

> [!tldr] Definition
> Anomali betyder inkonsistens i mønsteret fra den normale form. 
> Aomalier henviser til uregelmæssigheder eller uoverensstemmelser i [[Data|dataene]], der kan påvirke deres integritet, nøjagtighed og pålidelighed. 

I [[R-DBMS]] betyder anomali, at inkonsistensen opstod i [[Relationer|relationen]] under de operationer, der blev udført på.

---

## Indsætningsanormalier
Problemer, der opstår, når man forsøger at indsætte data i en tabel, men ikke kan gøre det uden at inkludere urelaterede data.

---

### Example
Hvis der skal indsættes en ny studerende, og kursus ikke er ved at blive besluttet endnu, vil indsættelse ikke være mulig, før kursus er besluttet for den studerende. 
Ellers bliver man nødt til at indsætte null ved kursus.

---

## Opdateringsanormalier
Problemer, der opstår, når man opdaterer data i en tabel, og det resulterer i inkonsistens, fordi de samme data skal opdateres flere steder.

---

### Example
Antag, at kollegiets rangering ændres, så vil ændringer skulle være overalt i databasen, hvilket vil være tidskrævende og beregningsmæssigt dyrt.

---

## Sletningsanormalier
Problemer, der opstår, når man sletter data fra en tabel, og det resulterer i tab af urelaterede data.

---

### Example
Hvis et kursus slettes, går oplysningerne om underviseren tabt, selvom underviseren stadig arbejder der.

---

## Related Topics
- Link
- 

---

## Resources
- Link
- 