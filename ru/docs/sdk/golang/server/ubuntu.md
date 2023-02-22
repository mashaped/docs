# Пример подготовки среды на Ubuntu Server

Обновим систему:

```shell
sudo apt update
sudo apt upgrade -y
```

Настроим брандмауэр:

Разрешим соединение по SSH:

```shell
sudo ufw allow ssh
```

Базовые правила:

```shell
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Разрешаем соединения по HTTP и HTTPS:

```shell
sudo ufw allow http
sudo ufw allow https
```

Активируем брандмауэр:

```shell
sudo ufw enable
```
