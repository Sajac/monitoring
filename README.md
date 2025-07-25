# Мониторинг Grafana + Prometheus + Logstash
Система мониторинга Grafana + Prometheus + Logstash для сбора метрик через logstash-exporter

# Предварительные требования 
Должны быть установлены docker, docker-compose, ansible, git<br>

# Установка 
Скопируйте на сервер репозиторий: 
```
git clone https://github.com/Sajac/monitoring.git
```
Перейдите в папку с проектом и запустите установку:
```
cd monitoring
ansible-playbook site.yml
```
Проверка, что все контейнера запустились:
```
docker ps 
```
# Инструкция Grafana
Для просмотра метрик необходимо подключиться к Grafana `http://serverip` стандартный логин/пароль для входа `admin/admin` и настроить Connections => Data Sources => Add Data source => Prometheus => в поле Prometheus server URL ввести `http://prometheus:9090` => внизу страницы Save & test.<br>
Перейти в раздел Drilldown => Metrics, где отображены все доступные метрики.<br>
Выборочно метрики, например, `process_virtual_memory_bytes`,`process_cpu_seconds_total` можно посмотреть в разделе Explore.

# Логи контейнеров 
Логи всех контейнеров хранятся отдельно на сервере в формате `container_name.log` и доступны по пути `/var/log/logstash`.