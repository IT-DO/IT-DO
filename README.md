<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/hero.svg?v=5">
  <source media="(prefers-color-scheme: light)" srcset="assets/hero-light.svg?v=5">
  <img alt="Anton Kurishchev — системный администратор Linux, Санкт-Петербург, открыт к предложениям" src="assets/hero.svg?v=5" width="100%">
</picture>

<p align="center">
  <a href="mailto:it-3@yandex.ru">it-3@yandex.ru</a> ·
  <a href="#инфраструктура">инфраструктура</a> ·
  <a href="#проекты">проекты</a> ·
  <a href="#опыт">опыт</a>
</p>

> [!TIP]
> **Открыт к предложениям** · системный администратор Linux, в том числе смешанная среда · Санкт-Петербург (офис или гибрид) либо удалённо.

## Кто я

Боевой магазин на 55 000 SKU работает на одном Proxmox-хосте. Бэкапы уезжают на отдельный Proxmox Backup Server, а о переполненном диске или упавшей машине мне сообщает Telegram раньше, чем кто-то позвонит.

Умею и Windows: поднимал лес Active Directory из двух доменов, гонял домены в виртуалках Hyper-V, политики раскидывал через GPO.

Всё, что повторяется, заворачиваю в плейбуки Ansible и манифесты k3s. Конфиги стенда лежат в открытых репозиториях.

Ищу позицию системного администратора, Linux или смешанная среда: Санкт-Петербург, офис или гибрид, либо удалённо.

## Инфраструктура

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/homelab.svg?v=5">
  <source media="(prefers-color-scheme: light)" srcset="assets/homelab-light.svg?v=5">
  <img alt="Homelab: узел n100 на Proxmox VE 9.2 — восемь гостей (HAOS, bitclimat, Kuber, hermes-agent, PBS, prometheus, zabbix, ansible) с vCPU, RAM и дисками, четыре хранилища" src="assets/homelab.svg?v=5" width="100%">
</picture>

<sub>Не рисунок «для красоты»: значения сняты с узла через API.[^1]</sub>

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

## Опыт

<details>
<summary><b>Фриланс с 2023 и homelab — подробнее</b></summary>

| Период | Роль | Задачи |
|---|---|---|
| фев 2023 — н.в. | Инфраструктура, фриланс | `ultra-med.ru`, `bitclimat.ru`: серверы, деплой, TLS, бэкапы, миграции без простоя |
| 2023 — н.в. | Homelab 24/7 | Proxmox VE, k3s, Prometheus/Zabbix, PBS, Ansible — стенд, на котором проверяются решения до прода |

Как обычно идёт работа:

```mermaid
flowchart LR
    A[Заявка] --> B[Аудит:<br/>что и где живёт]
    B --> C[План и риски]
    C --> D[IaC:<br/>роли и манифесты]
    D --> E[Мониторинг<br/>и алерты]
    E --> F[Бэкапы +<br/>проверка восстановления]
    F --> G[Документация<br/>и передача]
```

</details>

---

<div align="center">

**Резюме, рекомендации и разбор любого проекта — по запросу.**<br>
<sub>Готов к техническому интервью и разбору домашнего стенда в прямом эфире.</sub>

</div>

[^1]: `GET /api2/json/cluster/resources` на узле `n100`, Proxmox VE 9.2, снимок от 1 ноября 2026.
