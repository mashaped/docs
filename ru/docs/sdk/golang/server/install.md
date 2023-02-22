# Установка и запуск

```shell
go get github.com/green-api/whatsapp-api-webhook-server-golang
```

#### Установка и запуск примера

Установка:

```shell
wget https://raw.githubusercontent.com/green-api/whatsapp-api-webhook-server-golang/master/examples/main.go
```

Запуск:

```shell
go run main.go
```

#### Импорт

```
import (
	"github.com/green-api/whatsapp-api-webhook-server-golang/pkg"
)
```

#### Как инициализировать объект

Атрибут WebhookToken является опциональным.

```
webhook := pkg.Webhook{
    Address:      ":80",
    Pattern:      "/",
}
```

#### Запуск сервера

Функция StartServer принимает функцию-обработчик. Функция-обработчик должна содержать 1
параметр (`body map[string]interface{}`). При получении нового уведомления ваша функция-обработчик будет выполнена.

```
_ := webhook.StartServer(func(body map[string]interface{}) {
    fmt.Println(body)
})
```
