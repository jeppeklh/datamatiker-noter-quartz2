---
aliases:
  - Alerting
  - Automatisering
---

> [!tldr] Definition
Alerting og automatisering handler om at reagere straks og effektivt, når overvågningssystemet opdager afvigelser eller fejl. 
>
God alerting sikrer, at de rette personer og systemer informeres, mens automatisering kan forsøge at rette problemer uden manuel indgriben.

Når overvågningsdata (metrics, logs mv.) indikerer et problem, skal der reageres hurtigt – helst automatisk. Alerting sender besked til de ansvarlige, og automatisering (auto-repair) forsøger at afhjælpe problemet uden manuel indgriben.  

## Centrale begreber
---

| Begreb           | Forklaring                                                                                |
| ---------------- | ----------------------------------------------------------------------------------------- |
| **Alert**        | Besked der udløses, når en måling overstiger eller falder under en tærskel                |
| **Alert Rule**   | Regeldefinering med betingelser (`expr`), varighed (`for`) og metadata (annotations)      |
| **Notification** | Kanal til levering af alerts (e-mail, SMS, webhook, Slack, PagerDuty mv.)                 |
| **Silencing**    | Midlertidig undertrykkelse af alerts, fx under planlagt nedetid eller vedligehold         |
| **Auto-repair**  | Automatiserede handlinger (scripts, playbooks) der forsøger at rette problemet automatisk |


## Hvorfor alerting og automatisering?
---
- **Reduceret MTTR** (Mean Time To Repair): Hurtigere opdagelse og respons  
- **Proaktiv drift**: Problemer løses, før brugere opdager dem  
- **Skalerbarhed**: Automatisering frigiver driftsressourcer til mere komplekse opgaver  
- **Konsistens**: Ensartede trin ved fejl, færre menneskelige fejl  

## Arkitektur og workflow
---
1. **Datakilde**  
   - Prometheus, InfluxDB, application logs, netværkssniffers  
2. **Evaluering**  
   - Grafana Alerting / Prometheus Alertmanager tjekker “expr” med fast interval  
3. **Alert Rule**  
   - Definition af betingelser (`expr`), varighed (`for`), metadata (annotations, labels)  
4. **Alertmanager**  
   - Samler, de-duplikerer og ruter alerts  
5. **Notification**  
   - E-mail, Slack, SMS, webhook, PagerDuty  
6. **Silencing**  
   - Midlertidig undertrykkelse ved planlagt vedligehold  
7. **Auto-repair**  
   - Scripts, Kubernetes probes, CI/CD pipelines der udfører “self-healing”  



## Eksempel: Grafana Alert Rule
---
```yaml
apiVersion: 1
groups:
  - name: webapp-alerts
    interval: 1m
    rules:
      - uid: high-latency
        title: “Høj responstid på webapp”
        condition: |
          when
            query('A', '5m', now) > 0.5
        data:
          - refId: A
            relativeTimeRange:
              from: 5m
              to: 0s
            datasourceUid: prom
            model:
              expr: rate(http_request_duration_seconds_bucket{job="webapp"}[5m])
        for: 2m
        noDataState: OK
        execErrState: Alerting
        annotations:
          summary: "Responstid > 0.5s i mere end 2 minutter"
          description: "Tjek service performance og eventuelt scale-out."
        labels:
          severity: critical
```

- **condition**: PromQL-udtryk der evalueres
- **for**: Hvor længe reglen skal være true, før alerten udløses
- **annotations**: Menneske-læsbar besked
- **labels**: Bruges til routing i Alertmanager

## Notification-eksempel: Slack
---
I Alertmanager-konfiguration (`alertmanager.yml`):
```yml
receivers:
  - name: 'team-slack'
    slack_configs:
      - channel: '#alerts'
        send_resolved: true
        title: '{{ .CommonAnnotations.summary }}'
        text: |
          *Alert:* {{ .CommonLabels.alertname }}
          *Severity:* {{ .CommonLabels.severity }}
          *Details:* {{ .CommonAnnotations.description }}
route:
  receiver: 'team-slack'
  group_by: ['severity']
```

## Automatisering (Auto-repair)
---
### Brug af scripts

Eksempel: Genstart Docker-container ved crash:
```bash
#!/usr/bin/env bash
CONTAINER="webapp"
STATUS=$(docker inspect -f '{{.State.Status}}' $CONTAINER)
if [ "$STATUS" != "running" ]; then
  echo "Genstarter $CONTAINER..."
  docker restart $CONTAINER
fi
```
Køres som Cron-job eller af en alert webhook
## Resourcer
---
- [Systemovervågning Læringobjekt (Alerting og automatisering)](https://rise.articulate.com/share/D1gjA2qJXZ-26St6GmaYkyLrrCe2_UAs#/lessons/DJd9-txjje_Y34bL2bspI9_VEdp3T6bM)

