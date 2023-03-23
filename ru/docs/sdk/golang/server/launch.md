# Как запустить веб-сервер

### Установка

Не забудьте создать модуль:

```shell
go mod init example
```

Установка:

```shell
go get github.com/green-api/whatsapp-api-webhook-server-golang
```

### Импорт

```
import (
	"github.com/green-api/whatsapp-api-webhook-server-golang/pkg"
)
```

### Примеры

#### Как инициализировать объект

Атрибут WebhookToken является опциональным.

```
webhook := pkg.Webhook{
    Address:      ":80",
    Pattern:      "/",
}
```

#### Как запустить веб-сервер

Функция StartServer принимает функцию-обработчик. Функция-обработчик должна содержать 1
параметр (`body map[string]interface{}`). При получении нового уведомления ваша функция-обработчик будет выполнена.

Ссылка на пример: [main.go](
https://github.com/green-api/whatsapp-api-webhook-server-golang/blob/master/examples/main.go
).

```
_ := webhook.StartServer(func(body map[string]interface{}) {
    fmt.Println(body)
})
```

### Запуск приложения

```shell
go run main.go
```
