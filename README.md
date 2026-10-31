<div align="center">
  <img src="assets/hero.svg" alt="Anton Kurishchev — Linux / DevOps engineer" width="100%" />
</div>

<p align="center">
  <a href="mailto:it-3@yandex.ru"><img src="https://img.shields.io/badge/OPEN_TO_WORK-SRE_%2F_DevOps-238636?style=for-the-badge&labelColor=0D1117" alt="open to work" /></a>
  <a href="mailto:it-3@yandex.ru"><img src="https://img.shields.io/badge/email-it--3%40yandex.ru-EA4335?style=for-the-badge&logo=gmail&logoColor=white&labelColor=0D1117" alt="email" /></a>
  <img src="https://img.shields.io/badge/Saint_Petersburg-remote-58A6FF?style=for-the-badge&logo=googlemaps&logoColor=white&labelColor=0D1117" alt="location" />
</p>

---

## Кто я

Linux / DevOps-инженер, **3+ года практики**. Строю и обслуживаю инфраструктуру как код: виртуализация, Kubernetes, мониторинг, бэкапы, автоматизация. Веду собственный homelab **24/7** — это не учебный стенд, а рабочая среда с боевой нагрузкой.

Ищу роль **Linux / DevOps / SRE** в Санкт-Петербурге или удалённо.

## Homelab 24/7 — 8 гостей на одном узле

**Proxmox VE 9** · узел `n100` (Intel N100, 24/7) · 8 гостей · 5 хранилищ

```text
n100
├── 100  HAOS ........... умный дом (Home Assistant OS)
├── 101  web-prod ....... боевой сайт клиента · Nginx + TLS
├── 102  Kuber .......... кластер k3s
├── 103  hermes-agent ... AI-агент · автоматизация и алерты
├── 104  PBS ............ Proxmox Backup Server
├── 200  prometheus ..... метрики, scrape 15s
├── 201  zabbix ......... мониторинг железа, триггеры
└── 202  ansible ........ control node · IaC

хранилища: local · local-lvm · ceph-vmstore · PBS-Server · localnetwork
```

| Слой | Что развёрнуто | Что это даёт |
|---|---|---|
| **Гипервизор** | Proxmox VE 9, 8 гостей, 5 хранилищ | плотная упаковка на одном N100: сервисы изолированы, ресурсы не пересекаются |
| **Прод** | `101 web-prod` — Nginx + TLS | боевая нагрузка: виртуальные хосты, сертификаты, логи, обновления без простоя |
| **Оркестрация** | `102 Kuber` — k3s | Deployment / Service / Ingress / PVC, деплой и откат через манифесты |
| **Наблюдаемость** | `200 prometheus` + `201 zabbix` | метрики приложений и железа, триггеры, алерты в Telegram |
| **Бэкапы** | `104 PBS` + хранилище `PBS-Server` | инкрементальный бэкап гостей на отдельном узле + проверка восстановления |
| **IaC** | `202 ansible` | инвентарь по группам, идемпотентные роли, `--check` перед продом |
| **Хранение** | `ceph-vmstore` | Ceph RBD как бэкенд дисков VM вместо локального LVM |
| **Агент** | `103 hermes-agent` | автоматизация рутины: сбор метрик, алерты, отчёты |

```mermaid
flowchart LR
    PM["200 · Prometheus"] -.->|scrape| WP["101 · web-prod"]
    PM -.->|scrape| K3["102 · Kuber"]
    ZB["201 · Zabbix"] -.->|агенты| WP
    ZB -->|алерты| TG(["📨 Telegram"])
    PBS["104 · PBS"] -.->|бэкап| WP
    PBS -.->|бэкап| K3
    AN["202 · Ansible"] -.->|playbooks| K3
```

Отдельный PBS-узел вместо бэкапа «на тот же диск» и Ceph RBD под диски VM — два решения, которые чаще всего ломаются в домашних стендах, и оба здесь сделаны осознанно.

## Проекты

| Проект | Стек | Что демонстрирует |
|---|---|---|
| **[crypto-monitor](https://github.com/IT-DO/crypto-monitor)** | Python · Binance API · Telegram | мониторинг рынка, бэктест и paper-trading: работа с внешним API, планировщик, алерты |
| **[homelab-ansible](https://github.com/IT-DO/homelab-ansible)** | Ansible | инфраструктура как код: инвентарь по группам, идемпотентные роли, безопасный rollout |
| **[k3s-manifests](https://github.com/IT-DO/k3s-manifests)** | Kubernetes | примитивы k8s: Deployment, Service, Ingress (Traefik), PVC, requests/limits |
| **[homelab-docker](https://github.com/IT-DO/homelab-docker)** | Docker Compose | сервисный стек: reverse proxy, Prometheus, Grafana, node-exporter |

## Стек

| Домен | Инструменты |
|---|---|
| **ОС** | Linux (Ubuntu, CentOS, Debian), Windows Server |
| **Виртуализация** | Proxmox VE, VMware, Hyper-V |
| **Контейнеры** | Docker, Kubernetes (k3s), Docker Compose |
| **Мониторинг** | Prometheus, Grafana, Zabbix, Alertmanager |
| **Автоматизация** | Ansible, Bash, Python, Git |
| **Веб / сеть** | Nginx, Traefik, TLS, DNS, DHCP, VLAN, VPN, firewall |
| **Прочее** | PostgreSQL, SQL Server, Active Directory, REST API, Ceph |

## Как я работаю

- **Всё как код.** Конфиги и манифесты в Git, ручные правки — исключение, а не правило.
- **Мониторинг с первого дня.** Сервис без метрик и алертов — это сервис, о падении которого узнают пользователи.
- **Бэкап без проверки восстановления — не бэкап.** Регулярно восстанавливаю из копий.
- **Сначала `--check`.** На хостах с боевой нагрузкой изменения проверяются до применения.
- **Документирую.** README в каждом репозитории: схема, запуск, ограничения.

## GitHub

<p align="center">
  <img height="150" src="https://github-readme-stats.vercel.app/api?username=IT-DO&show_icons=true&theme=tokyonight&hide_title=true&hide_border=true&hide=issues" alt="stats" />
  <img height="150" src="https://streak-stats.demolab.com/?user=IT-DO&theme=tokyonight&hide_border=true" alt="streak" />
</p>

---

<div align="center">

**Открыт к работе** · Linux / DevOps / SRE · Санкт-Петербург / удалённо

[it-3@yandex.ru](mailto:it-3@yandex.ru) · резюме по запросу

</div>
