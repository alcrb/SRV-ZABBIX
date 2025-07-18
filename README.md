# Stack Zabbix + Prometheus + Grafana + cAdvisor + AlertManager + Caddy

## Description

Cette stack Docker Compose intègre :

- Zabbix server, web, agent, MariaDB
- Prometheus avec node-exporter et cAdvisor
- AlertManager pour alertes Prometheus
- Grafana configuré pour utiliser Zabbix et Prometheus comme datasources (plugin Zabbix à installer manuellement)
- Caddy comme reverse proxy HTTPS

---

## Déploiement

1. Cloner ce dépôt
2. Modifier les fichiers `alertmanager.yml` et `Caddyfile` avec tes infos SMTP et domaine
3. Lancer la stack :

```bash
docker-compose up -d
```

4. Accéder aux interfaces :

- Grafana : https://<IP>/grafana (login admin/admin123)
- Zabbix Web : https://<IP>/zabbix
- Prometheus : https://<IP>/prometheus
- AlertManager : https://<IP>/alertmanager
- cAdvisor : https://<IP>/cadvisor

---

## Configuration Grafana

- Installer le plugin Zabbix depuis le UI Grafana (Configuration → Plugins)
- Ajouter les datasources :
  - Zabbix (http://zabbix-server:10051)
  - Prometheus (http://prometheus:9090)

---

## Notes

- Adapter les mots de passe dans `docker-compose.yml`
- Adapter les configurations SMTP et domaine dans `alertmanager.yml` et `Caddyfile`