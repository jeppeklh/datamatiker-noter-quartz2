---
aliases:
  - Værktøjer
---

Denne note giver en kort introduktion til de mest anvendte værktøjer til system- og netværksovervågning. Hvert værktøj har sine styrker, og i praksis kombineres ofte flere for at få komplet indsigt i infrastruktur, applikationer og netværkstrafik.

---

## Prometheus
---
> [!tldr] Definition
Open-source system til metrics-indsamling og overvågning. Samler data fra applikationer og systemer via “pull” på HTTP-endpoints og understøtter alarmer ved tærskelværdier. Ideel i DevOps-miljøer og til microservices.

**Eksempel på scraping-endpoint:**  
```yaml
scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
```
**Link:**  
[https://prometheus.io](https://prometheus.io)


## Grafana
---
> [!tldr] Definition
Dashboard-platform til visualisering af data fra fx Prometheus, InfluxDB og andre kilder. Understøtter realtidsgrafer, advarsler og paneler med drill-down.

**Eksempel på panel-opsætning:**
- Vælg “Prometheus” som datakilde
- Angiv en PromQL-forespørgsel, fx:
```PromQL
rate(http_requests_total[5m])
```
**Link:**  
[https://grafana.com](https://grafana.com)


## Nagios
---
> [!tldr] Definition 
Klassisk overvågningsværktøj der kører aktive tjek af servere, netværksenheder og services. Understøtter e-mail/SMS-alarmer, tjek via plugins og konfigurationsbaseret opsætning.

**Link:**  
[https://www.nagios.org](https://www.nagios.org)

## htop
---
> [!tldr] Definition
Interaktivt kommandolinje-værktøj til at overvåge CPU-, hukommelses- og processforbrug i realtid. Brugervenligt interface med mulighed for at sortere, dræbe processer mv.

**Installation (Ubuntu WSL):**
```bash
sudo apt update && sudo apt install -y htop
```

## iotop
---
> [!tldr] Definition
Viser disk I/O per proces i realtid. Hjælper med at identificere processer, der belaster disken mest.

**Installation (Ubuntu WSL):**
```bash
sudo apt install -y iotop
```

## nethogs
---
> [!tldr] Definition
CLI-værktøj til at se netværksforbrug pr. proces. Giver hurtigt overblik over, hvilke programmer der bruger mest båndbredde.

**Installation (Ubuntu WSL):**
```bash
sudo apt install -y nethogs
```

## Wireshark
---
> [!tldr] Definition
Grafisk packet-sniffer til dybdegående analyse af netværkstrafik. Understøtter filtre, protokol-dekodning og eksport af pakker til analyse.

**Link:**  
[https://www.wireshark.org](https://www.wireshark.org)

## Resourcer
---
- [Systemovervågning Læringsobjekt (Værktøjer)](https://rise.articulate.com/share/D1gjA2qJXZ-26St6GmaYkyLrrCe2_UAs#/lessons/bQqoXkr8_6t8f_SgK8bmc9qO7mQEkAzs)