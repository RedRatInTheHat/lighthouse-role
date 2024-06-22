Role Name
=========

В очень упрощённом виде скачивает и устанавливает [LightHouse](https://github.com/VKCOM/lighthouse.git).<br/>
Для корректной работы требует предустановленного Nginx.

Requirements
------------

* Ansible core 2.16.7 и выше.
* На стороне хоста: 
    * SSH service;
    * Python версии, [соответствующей Ansible core](https://docs.ansible.com/ansible/latest/reference_appendices/release_and_maintenance.html#ansible-core-support-matrix);
    * RPM-based дистрибутив (требуется yum в качестве пакетного менеджера);
    * Nginx.

Role Variables
--------------

[defaults/main.yml](defaults/main.yml)

| Параметр | Default | Что это |
|----------|---------|---------|
| lighthouse_version | "d701335" | Версия LightHouse: commit, tag или branch |
| lighthouse_directory | "/srv/www/lighthouse" | Директория, в которой будет размещаться Lighthouse. Должна совпадать с директорией, указанной в конфигурации Nginx |

[vars/main.yml](vars/main.yml)

| Параметр | Default | Что это |
|----------|---------|---------|
| lighthouse_repository | "https://github.com/VKCOM/lighthouse.git" | Репозиторий, из которого будет скачан Lighthouse |

Dependencies
------------

Предварительно требуется установить Nginx.

Templates and files
-------------------

Для настройки отображения Lighthouse небходимо внести изменения в шаблон конфигурации Nginx [templates/vector.yaml.j2](templates/vector.yaml.j2).

Example Playbook
----------------

```yml
- hosts: lighthouse
  roles:
    - lighthouse-role
```
