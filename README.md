# Ansible-Playbooks

## Разработать ansible playbook выполняющий следующий функционал:

 

1) Проверяет статус сервиса на хосте ( сервис на выбор, например Nginx)

2) Если сервис доступен, записать сообщение "{Время проверки}: OK" в логфайл ( Расположение файла на выбор)

3) Если сервис недоступен, записать сообщение "{Время проверки}: Сервис недоступен"

4) Запустить сервис

   4.1 Если сервис стал доступен, записать сообщение "{Время проверки}: Сервис успешно запущен" в логфайл

   4.2 Если сервис по-прежнему недоступен, отправить Email оповещение с текстом: "{Время проверки}: {Сервис} {Статус сервиса}" + записать сообщение в логфайл

 

## Необходимо разработать ansible playbook выполняющий следующий функционал:

 

Выполняет архивацию логов на группе серверов, логи хранятся в директориях:

/opt/log/service_log/accounting, /opt/log/service_log/authoriz, /opt/log/service_log/authentic.

Имена файлов складываются из названия директории и даты, например: accounting_20220101.log

Логи за второе полугодие 2022 года архивировать не нужно, т.е. только по 30.06.2022.

Исходные файлы сразу после архивации необходимо удалить.

Необходимо учесть, что дата последнего изменения лог-файла может не соответствовать дате указанной в названии файла.


## Запуск
Ubuntu:

Обновите систему и устанвоите зависимости:
```
sudo apt update
sudo apt install software-properties-common
```
Устанвоите Ansimble
```
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y
```

CentOS:
```
sudo yum install epel-release -y
sudo yum install ansible -y
```

В файле inventory.ini необходимо указать группу серверов, с которыми будет работать playbook

В файле playbook1.yaml необходимо указать свои данные от smtp сервера:
```
smtp_server: smtp.example.com
smtp_port: 587
smtp_user: "user@example.com"
smtp_password: "password"
email_recipient: "recipient@example.com"
```

Запустите нужный playbook командой:
```
ansible-playbook -i inventory.ini *playbook_name*.yaml
```