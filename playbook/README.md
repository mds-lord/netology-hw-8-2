# README #

Этот плейбук предназначен для развертывания связки elasticsearch+kibana на 
одном хосте и logstash на втором хосте

В нём последовательно устанавливаются Java JDK, Elasticsearch Kibana и Logstash.

## Подготовка и использование

В директории с плейбуком необходимо создать поддиректорию files и скачать в неё 
дистрибутивы [Java](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) и 
[Kibana](https://www.elastic.co/downloads/kibana)


Для запуска необходимо определить следующие переменные (в квадратных скобках указан 
путь до файла со значениями по умолчанию):

````
[./group_vars/elastic/vars.yml]
  elastic_version: "7.10.1"  # версия Elasticsearch
  kibana_version: "7.10.2"  # версия Kibana
[group_vars/all/vars.yml]
  java_jdk_version: 11.0.9  # версия jdk Java
  java_oracle_jdk_package: jdk-11.0.9_linux-x64_bin.tar.gz  # название архива с jdk
[group_vars/logstash/vars.yml]
  logstash_version: "7.10.2"  # версия Logstash
````
## Запуск плейбука

````
ansible-playbook site.yml -i inventory/prod.yml 
````
## Примечание

Запуск тестировался на двух докер контейнерах, поэтому для определения ip адреса использовался 
локальный запуск докера и публикация порта elasticsearch на контейнере с elastic.
Адрес контейнера с elasticsearch и порт подставляются в конфиг logstash автоматически.
