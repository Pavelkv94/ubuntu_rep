# ELK Stack Setup Guide

## Шаг 1: Установка и настройка Filebeat на удалённом сервере

### Установка Filebeat

```bash
sudo apt update
sudo apt install filebeat
```

### Настройка конфигурации

Отредактируйте файл конфигурации:

```bash
sudo nano /etc/filebeat/filebeat.yml
```

Добавьте следующую конфигурацию:

```yaml
filebeat.inputs:
  - type: log
    enabled: true
    paths:
      - /var/log/nginx/access.log
      - /var/log/nginx/error.log

output.logstash:
  hosts: ["<IP_домашнего_сервера>:5044"]
```

### Перезапуск службы

```bash
sudo systemctl restart filebeat
```

## Шаг 2: Настройка ELK Stack на домашнем сервере через Docker Compose

### Подготовка директорий

Запуск докер-компоуз

Установите правильные права доступа для Elasticsearch:

```bash
sudo chown -R 1000:1000 /home/<user>/docker/esdata
```

### Настройка Logstash

Создайте файл конфигурации pipeline:

```bash
# Создать файл /home/<user>/docker/logstash/pipeline/logstash.conf
```

Содержимое файла `logstash.conf`:

```ruby
input {
  beats {
    port => 5044
  }
}

filter {
  grok {
    match => { "message" => "%{COMBINEDAPACHELOG}" }
  }
  date {
    match => [ "timestamp", "dd/MMM/yyyy:HH:mm:ss Z" ]
  }
}

output {
  elasticsearch {
    hosts => ["http://elasticsearch:9200"]
    index => "nginx-logs-%{+YYYY.MM.dd}"
  }
}
```