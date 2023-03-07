# Как получать входящие уведомления

### Установка

Не забудьте создать модуль:

```shell
go mod init example
```

Установка:

```shell
go get github.com/green-api/whatsapp-api-client-golang
```

### Импорт

```
import (
	"github.com/green-api/whatsapp-api-client-golang/pkg/api"
	"github.com/green-api/whatsapp-api-client-golang/pkg/webhook"
)
```

### Примеры

#### Как инициализировать объект

```
GreenAPI := api.GreenAPI{
    IDInstance:       "1234",
    APITokenInstance: "bde035edae3fc00bc116bd112297908d8145e5ba8decc5d884",
}
```

Обратите внимание, что ключи можно получать из переменных среды:

```
IDInstance := os.Getenv("ID_INSTANCE")
APITokenInstance := os.Getenv("API_TOKEN_INSTANCE")
```

#### Как получать входящие уведомления

Чтобы начать получать уведомления, нужно передать функцию-обработчик в GreenAPIWebhook.Start(). Функция-обработчик
должна содержать 1 параметр (`body map[string]interface{}`). При получении нового уведомления ваша функция-обработчик
будет выполнена. Чтобы перестать получать уведомления, нужно вызвать функцию GreenAPIWebhook.Stop().

Ссылка на пример: [webhook/main.go](
https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go
).

```
GreenAPIWebhook := webhook.GreenAPIWebhook{
    GreenAPI: GreenAPI,
}

GreenAPIWebhook.Start(func(body map[string]interface{}) {
    fmt.Println(body)
})
```

### Запуск приложения

```shell
go run main.go
```

### Список примеров

| Описание                             | Ссылка на пример                                                                                                                  |
|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Как создать группу                   | [createGroup/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/createGroup/main.go)           |
| Как отправить файл загрузкой с диска | [sendFileByUpload/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendFileByUpload/main.go) |
| Как отправить файл по ссылке         | [sendFileByURL/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendFileByURL/main.go)       |
| Как отправить сообщение              | [sendMessage/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendMessage/main.go)           |
| Как получать входящие уведомления    | [webhook/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go)                   | 
