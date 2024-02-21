# Домашнее задание к занятию «Управление доступом» - `Мальцев Виктор`

---

Задание 1. Создайте конфигурацию для подключения пользователя

    1. Создайте и подпишите SSL-сертификат для подключения к кластеру.
    2. Настройте конфигурационный файл kubectl для подключения.
    3. Создайте роли и все необходимые настройки для пользователя.
    4. Предусмотрите права пользователя. Пользователь может просматривать логи подов и их конфигурацию (kubectl logs pod <pod_id>, kubectl describe pod <pod_id>).
    5. Предоставьте манифесты и скриншоты и/или вывод необходимых команд.


Ответ:

1. Генерация сертификатов:

    openssl genrsa -out user.key 2048

    openssl req -new -key user.key -out user.csr -subj "/CN=user/O=group"

2. Подписание сертификатов:

    openssl x509 -req -in user.csr -CA /var/snap/microk8s/current/certs/ca.crt -CAkey /var/snap/microk8s/current/certs/ca.key -CAcreateserial -out user.crt -days 500

3. Конфиг kubectl:

![alt text](https://github.com/vmmaltsev/screenshot/blob/main/Screenshot_146.png)

4. Манифесты в файлах








