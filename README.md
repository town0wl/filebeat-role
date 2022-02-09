Filebeat role
=========

Роль для установки, начальной конфигурации и запуска Filebeat в виде сервиса на хостах с ОС: Debian, Ubuntu, CentOS, RHEL.

Requirements
------------

Поддерживаются только ОС семейств debian и EL.

Role Variables
--------------

| Variable name | Default | Description |
|-----------------------|----------|-------------------------|
| filebeat_version | "7.14.0" | Параметр, который определяет какой версии Filebeat будет установлен |
| filebeat_install_type | remote | При установке значения 'remote' загрузка дистрибутива происходит через управляющий хост ansible |
| elastic_service_ip | Cчитывается из ansible facts хоста с именем ***elastic-host*** | IP-адрес сервиса Elasticsearch |
| kibana_service_ip | Cчитывается из ansible facts хоста с именем ***kibana-host*** | IP-адрес сервиса Kibana |

Tags
--------------

Первоначальная конфигурация Filebeat включает создание шаблонов в Elasticsearch и дашбордов в Kibana. Задачи этого этапа предназначены для однократного выполнения и помечены тегами **never** и **firstrun**.

Example Playbook
----------------

    - hosts: all
      roles:
         - { role: filebeat-role }

License
-------

BSD
