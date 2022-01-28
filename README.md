Filebeat role
=========

Роль для установки, начальной конфигурации и запуска Filebeat на хостах с ОС: Debian, Ubuntu, CentOS, RHEL.

Requirements
------------

Поддерживаются только ОС семейств debian и EL.

Role Variables
--------------

| Variable name | Default | Description |
|-----------------------|----------|-------------------------|
| filebeat_version | "7.14.0" | Параметр, который определяет какой версии Filebeat будет установлен |
| filebeat_install_type | remote | При установке значения 'remote' загрузка дистрибутива происходит через управляющий хост ansible |

Dependencies
--------------

Для начальной конфигурации Filebeat (/etc/filebeat/filebeat.yml) используются IP-адреса сервера Elasticsearch и сервера Kibana, которые считываются из ansible facts хостов с именем **elastic-host** и **kibana-host** соответственно.

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
