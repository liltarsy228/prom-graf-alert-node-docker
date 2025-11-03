Prometheus + Grafana + Alertmanager + Node Exporter (Host & Docker)

Инструкция по установке и настройке:

1) Добавьте хост для Node Exporter в Ansible

В файле /etc/ansible/hosts добавьте:
[node-exporter-hosts]
<IP_хоста>

2) Настройте Prometheus для мониторинга Node Exporter вне Docker

В файле docker-stack/prometheus/config/prometheus.yml измените IP:
- job_name: 'node_outside'
  static_configs:
    - targets: ['<IP_хоста>:9100']

3) Запустите стек Docker

Находясь в папке docker-stack, выполните:
docker compose up -d


4) Настройте Alertmanager для уведомлений

В файле docker-stack/alertmanager/config/alertmanager.yml измените token и chat_id для вашего чата.
