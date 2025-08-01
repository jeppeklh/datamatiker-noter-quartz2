## Scenarie
---
En virksomhed med 25 ansatte ønsker et netværk, der:

- Giver adgang til internettet.
- Muliggør deling af ressourcer som printere og filer.
- Tilbyder trådløs adgang til bærbare computere.
- Er sikkert og skalerbart til 50 ansatte.
---
### Netværksdesign
---
1. **Nødvendigt udstyr**:
    
    - [[Router]]: For at forbinde virksomhedens netværk til internettet.
    - [[Repo/02 - Teknologi/Netværk/Netværksudstyr/Liste af Udstyr/Switch|Switches]]: Til at forbinde stationære computere, printere og servere.
    - [[Access Point|Access Points]]: Til trådløs adgang for bærbare.
    - [[Firewall]]: For at sikre netværket.
    - **Server**: Til filopbevaring og backup.
    - [[Netværkskabel|Netværkskabler]]: Til at forbinde udstyret.

2. **Netværkslayout**:
    
    - [[Router]]: Placeret mellem [[Modem]] og netværk.
    - [[Repo/02 - Teknologi/Netværk/Netværksudstyr/Liste af Udstyr/Switch|Switches]]: Forbundet til routeren og enheder.
    - [[Access Point|Access Points]]: Strategisk placeret for maksimal dækning.
    - **Server**: Forbundet til switchen.

3. **IP-adressering**:
    
    - Brug et privat IP-område, f.eks. `192.168.1.0/24`.
    - Tildel:
        - [[Router]]: `192.168.1.1` (gateway).
        - Server: `192.168.1.2`.
        - Printere: `192.168.1.10-19`.
        - Klienter: `192.168.1.20-99`.
4. **Sikkerhed**:
    
    - [[Firewall]]: Installeres mellem netværket og internettet.
    - **Wi-Fi**: Brug WPA3-sikkerhed.
    - **VLANs**: Segmentér netværket for at adskille kritiske ressourcer fra gæsteadgang.