---
aliases:
  - Open Systems Interconnection
  - OSI
---
> [!tldr] Definition
> OSI-modellen opdeler netværkskommunikation i **syv lag** for at standardisere, hvordan data sendes og modtages.

---

## De syv lag
1. **Fysisk (Physical)**: Hardware som kabler og signaler.
2. **Datalink (Data Link)**: Pålidelig dataoverførsel (f.eks. MAC-adresser).
3. **Netværk (Network)**: Routing af data (f.eks. IP-adresser).
4. **Transport (Transport)**: Pålidelig dataoverførsel (f.eks. TCP).
5. **Session (Session)**: Oprettelse og afslutning af sessioner.
6. **Præsentation (Presentation)**: Kryptering og datakonvertering.
7. **Applikation (Application)**: Netværkstjenester for applikationer (f.eks. HTTP).

> [!example]  Eksempel: Email afsendelse
> Når du sender en e-mail via f.eks. **SMTP**:
>1. **Applikationslaget (SMTP - Simple Mail Transfer Protocol)**  
    >	- Din mailklient (Gmail, Outlook) sender en e-mail via en mailserver.
>2. **Præsentationslaget**  
    >	- Kryptering og formatering af e-mailens tekst og vedhæftninger.
>3. **Sessionslaget**
    >	- Holder sessionen åben mellem din computer og mailserveren.
>4. **Transportlaget (TCP, port 25/465/587)**  
    >	- **TCP** opdeler e-mailen i pakker og sikrer, at de ankommer korrekt.
>5. **Netværkslaget (IP)**  
    >	- Pakkerne får en **afsender- og modtager-IP-adresse** (din computer og mailserverens IP).
>6. **Datalinklaget (Ethernet, Wi-Fi)**  
    >	- Data sendes som rammer til den nærmeste router.
>7. **Fysisk lag (Kabelforbindelse, Wi-Fi, fiberoptik)**  
    >	- Data bevæger sig som elektriske signaler eller radiobølger over netværket.
>
> Når e-mailen når frem til modtagerens mailserver, bliver den **hentet via POP3 eller IMAP**, og processen kører i omvendt rækkefølge.

---

## Fordele ved OSI-modellen
- Skaber et fælles sprog for netværk.
- Gør fejlfinding enklere.

![[OSIModel.png]]

---

## Relation til TCP/IP-modellen
![[OSIvsTCPIP.png]]

---

## Resourser
[Netværksmodeller Læringsobjekt](https://scorm.itslearning.com/data/3289/C20150/ims_import_29/scormcontent/index.html#/lessons/BSmTZbYth9KXah_URHzMGletI5zXtfWe)

![[OSIBeskrivende.png]]