# Как отправить сообщение

### Установка

```shell
go get github.com/green-api/whatsapp-api-client-golang
```

### Пример отправки сообщения

Если у метода API есть необязательные параметры, то в метод библиотеки нужно передавать JSON (`map[string]interface{}`).

Ссылка на
пример: [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/send_message/main.go).

```go
package main

import (
	"fmt"
	"log"
	"os"

	"github.com/green-api/whatsapp-api-client-golang/pkg/api"
)

func main() {
	IDInstance := os.Getenv("ID_INSTANCE")
	APITokenInstance := os.Getenv("API_TOKEN_INSTANCE")

	GreenAPI := api.GreenAPI{
		IDInstance:       IDInstance,
		APITokenInstance: APITokenInstance,
	}

	response, err := GreenAPI.Methods().Sending().SendMessage(map[string]interface{}{
		"chatId":  "79001234567@c.us",
		"message": "Any message",
	})
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(response)
}
```

### Список примеров

| Описание                | Ссылка на пример                                                                                                    |
|-------------------------|---------------------------------------------------------------------------------------------------------------------|
| Как создать группу      | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/create_group/main.go)        |
| Как отправить вложение  | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/send_file_by_upload/main.go) |
| Как отправить сообщение | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/send_message/main.go)        |
| Использование webhook   | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go)             | 
