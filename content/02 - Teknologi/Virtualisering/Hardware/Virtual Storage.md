> [!tldr] Definition
Denne note dækker to hovedaspekter af virtuel lagring: de filtyper, der benyttes i virtualiseringsmiljøer, og de underliggende filsystemer, som fysisk lagring er baseret på.

## Filtyper i Virtualisering
---
- **Specifikke filformater:**  
  Forskellige hypervisorer anvender ofte deres egne filformater for virtuelle maskiner. Nogle af de mest almindelige formater inkluderer:
  - **VDI** (Virtual Disk Image)
  - **VHDX** (Virtual Hard Disk Extended)
  - **VMDK** (Virtual Machine Disk)
  - **HDD** (Hypervisor Disk Drive)

- **Kompatibilitet:**  
  Hvis to hypervisorer benytter samme filtype, indikerer det en høj grad af kompatibilitet, hvilket gør det nemmere at overføre virtuelle maskiner mellem platformene. Dog bruger de fleste hypervisorer deres egne unikke formater, og det kan være udfordrende at åbne en VM fra en hypervisor i en anden. Der findes tredjepartsværktøjer, der kan konvertere mellem formater, men disse bør undgås i produktionsmiljøer på grund af tidsforbrug og potentiel risiko for datatab.

## Filsystemer for Virtuel Lagring
---
- **Almindelige filsystemer:**  
  De filsystemer, der typisk anvendes til at lagre filerne for virtuelle maskiner, omfatter:
  - **VMFS** (Virtual Machine File System)
  - **NFS** (Network File System)
  - **NTFS** (New Technology File System)
  - **Raw Device Mapping (RDM)**

- **Kompatibilitet og ydeevne:**  
  Mange hypervisorer understøtter mere end ét filsystem, men ikke alle er kompatible med samtlige. Det er derfor vigtigt at kontrollere, at det filsystem, din organisation er afhængig af, understøttes af den valgte hypervisor.

## Lokalt vs. Netværksbaseret Lagring
---
- **Lokal lagring:**  
  Egner sig, hvis der kun køres én virtuel maskine på en fysisk host.  
- **Netværkslagring:**  
  Ved kørsel af flere virtuelle maskiner på samme host kan lokal lagring hurtigt blive en flaskehals. Her anbefales brug af netværkslagringsløsninger som SAN eller NAS, som ofte leverer bedre ydeevne og højere throughput for virtuelle miljøer.


## Resourcer
---
- [Virtualisering LinkedIn Kursus (Virtual Storage)](https://www.linkedin.com/learning/learning-virtualization-13945890/understanding-virtual-storage?resume=false&u=57075649)