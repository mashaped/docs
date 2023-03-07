# Как создать группу

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

#### Как создать группу

Ссылка на пример: [createGroup/main.go](
https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/createGroup/main.go
).

```
response, _ := GreenAPI.Methods().Groups().CreateGroup("groupName", []string{
    "11001234567@c.us",
    "11002345678@c.us",
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
