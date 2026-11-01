<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/hero.svg?v=5">
  <source media="(prefers-color-scheme: light)" srcset="assets/hero-light.svg?v=5">
  <img alt="Anton Kurishchev — системный администратор Linux, Санкт-Петербург, открыт к предложениям" src="assets/hero.svg?v=5" width="100%">
</picture>

<p align="center">
  <a href="mailto:it-3@yandex.ru">it-3@yandex.ru</a> ·
  <a href="#инфраструктура">инфраструктура</a> ·
  <a href="#проекты">проекты</a>
</p>

> [!TIP]
> **Открыт к предложениям** · системный администратор Linux, в том числе смешанная среда · Санкт-Петербург (офис или гибрид) либо удалённо.

## Кто я

Боевой магазин на 55 000 SKU работает на одном Proxmox-хосте. Бэкапы уезжают на отдельный Proxmox Backup Server, а о переполненном диске или упавшей машине мне сообщает Telegram раньше, чем кто-то позвонит.

Умею и Windows: поднимал лес Active Directory из двух доменов, гонял домены в виртуалках Hyper-V, политики раскидывал через GPO.

## Инфраструктура

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/homelab.svg?v=5">
  <source media="(prefers-color-scheme: light)" srcset="assets/homelab-light.svg?v=5">
  <img alt="Homelab: узел n100 на Proxmox VE 9.2 — восемь гостей (HAOS, bitclimat, Kuber, hermes-agent, PBS, prometheus, zabbix, ansible) с vCPU, RAM и дисками, четыре хранилища" src="assets/homelab.svg?v=5" width="100%">
</picture>

## Проекты

| Проект | Что доказывает |
|---|---|
| **[homelab-ansible](https://github.com/IT-DO/homelab-ansible)** | инвентарь по группам, идемпотентные роли, безопасный rollout и `--check` перед продом |
| **[k3s-manifests](https://github.com/IT-DO/k3s-manifests)** | примитивы Kubernetes: Deployment, Service, Ingress, PVC, requests/limits |
| **[homelab-docker](https://github.com/IT-DO/homelab-docker)** | compose-стек с reverse proxy и метриками; порты закрыты, пароль обязателен |
| **[crypto-monitor](https://github.com/IT-DO/crypto-monitor)** | Python и внешнее API: планировщик, бэктест, алерты в Telegram |

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
