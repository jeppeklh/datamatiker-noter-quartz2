
> [!tldr] Definition
Logfiler fungerer som systemets hukommelse – de registrerer, hvad der sker, hvornår og hvorfor. 
>
At kunne indsamle, centralisere og analysere logs er essentielt for fejlsøgning, performance-tuning og sikkerhedsovervågning.


## Centrale begreber
---

| Begreb           | Forklaring                                                                                   |
|------------------|----------------------------------------------------------------------------------------------|
| **System logs**  | Information om operativsystem og kerneprocesser (boot, services, drivers)                    |
| **Application logs** | Logs fra brugerdefinerede eller tredjepartsapplikationer (API-kald, transaktioner)        |
| **Security logs**| Registrering af loginforsøg, adgangskontrol og systemændringer                               |
| **Log rotation** | Automatisk arkivering og sletning af gamle logfiler for at undgå diskplads-mangel            |
| **Log level**    | Alvorlighedsgrad (fx DEBUG, INFO, WARNING, ERROR, CRITICAL) – styrer, hvad der logges og vises |

**Eksempel — JSON-log:**
```json
{
  "timestamp": "2025-04-27T14:32:10Z",
  "level": "ERROR",
  "service": "auth-service",
  "message": "User login failed",
  "userId": "12345",
  "ip": "192.0.2.10"
}
```



## Centraliseret loghåndtering
---
I stedet for at sprede logfiler på hver enkelt server anvendes en logpipeline:

1. **Shipment** (Filebeat, Fluentd, Logstash…)
2. **Processing** (parsing, berigelse, filtering)
3. **Storage & Indeksering** (Elasticsearch, InfluxDB, Loki…)
4. **Søgning & Visualisering** (Kibana, Grafana, Graylog…)
    

Fordele:

- Konsolideret søgning på tværs af services
- Skalerbar opbevaring og replikering
- Hurtig query-performance via indekser
- Mulighed for at lave dashboards og alerts på logdata


## 6. Best Practices
---
- **Strukturerede logs**: Brug JSON eller GELF frem for fri tekst
- **Kontekst**: Inkluder trace- og correlation IDs for at følge en anmodning tværs gennem mikrotjenester

- **Log levels**    
    - DEBUG til udvikling/diagnostik
    - INFO til normale hændelser
    - WARNING til mistænkelige tilstande
    - ERROR/CRITICAL til funktionelle fejl

- **Retention og rotation**:    
    - Automatisk arkivering og sletning (f.eks. via Elasticsearch ILM eller logrotate)
    - Opbevar kritiske logs længere (sikkerhed, compliance)

- **Sikkerhed**:    
    - Beskyt logtransport (TLS)
    - Maskér følsomme data (PII, tokens) inden shipping


## Resourcer
---
- [Systemovervågning Læringsobjekt (Log og loganalyse)](https://rise.articulate.com/share/D1gjA2qJXZ-26St6GmaYkyLrrCe2_UAs#/lessons/aAxCE41hyUWLjlfqy-rInZXSir2zk6h-)
- [Logging Practical guide](https://assets-global.website-files.com/626ad01a9cdb24688668c02e/6308d44b5388c8411a78833b_LogDNA-eBook-Troubleshoot-in-Production_compressed.pdf)