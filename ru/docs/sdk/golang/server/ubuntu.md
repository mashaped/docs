# Пример подготовки среды для Ubuntu Server

### Обновление системы

Обновим систему:

```shell
sudo apt update
sudo apt upgrade -y
```

### Брандмауэр

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

### Установка

Не забудьте создать модуль:

```shell
go mod init example
```

Установка:

```shell
go get github.com/green-api/whatsapp-api-webhook-server-golang
```

### Примеры

Загрузим и запустим наш веб-сервер в качестве примера:

Загрузка примера:

```shell
wget https://raw.githubusercontent.com/green-api/whatsapp-api-webhook-server-golang/master/examples/main.go
```

Запуск приложения:

```shell
go run main.go
```
