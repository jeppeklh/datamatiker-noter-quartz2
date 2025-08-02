> [!tldr] Definition
> CIDR bruges til mere fleksibel tildeling af [[IP-adresser]], der ikke afhænger af klasser (A, B, C).

---

## Notation
En [[IP-adresser|ip-adresse]] efterfulgt af en skråstreg `/` og et tal, som angiver netværksdelens længde i bits.
- F.eks. `192.168.1.0/24`: De første 24 bits er netværksdelen.

> [!example] Eksempel på CIDR og [[Subnetmasker|subnetmaske]]:
>| CIDR | Subnetmaske     | IP-adresser | Brugbare IP'er |
> | ---- | --------------- | ----------- | -------------- |
> | /8   | 255.0.0.0       | 16.777.216  | 16.777.214     |
> | /16  | 255.255.0.0     | 65.536      | 65.534         |
> | /24  | 255.255.255.0   | 256         | 254            |
> | /28  | 255.255.255.240 | 16          | 14             |
>

---

## Fordele ved CIDR
- Fleksibel netværksopdeling: Kan opdele store netværk i små subnets eller samle små netværk i større.
- Effektiv udnyttelse af [[IP-adresser]]: Reducerer spild ved kun at tildele nødvendige adresser.
- Simplificeret routing: Flere subnetværk kan kombineres i én rute (supernetting).

---

> [!example] Praktisk Eksempel
> - **Netværk**: `192.168.1.0/26`
>- **Analyse**:
 > 	 - Subnetmaske: `255.255.255.192`
   > 	 - Antal adresser: `64`
   > 	 - Brugbare adresser: `62` (2 reserveres til netværks- og broadcastadresse).

---

## Resourser
- [Netværk Læringsobjekt (CIDR)](https://scorm.itslearning.com/data/3289/C20150/ims_import_29/scormcontent/index.html#/lessons/iWCDu6UTr_MK5uAt8zdNLa37K2CT0QQ3)



