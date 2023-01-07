# Как использовать webhook

### Установка

```shell
go get github.com/green-api/whatsapp-api-client-golang
```

### Пример использования технологии webhook

Чтобы начать получать события, нужно передать функцию-обработчик в GreenAPIWebhook.Start(). Функция-обработчик должна
содержать 1 параметр (`body map[string]interface{}`). При получении нового события ваша функция-обработчик будет
выполнена. Чтобы перестать получать события, нужно вызвать функцию GreenAPIWebhook.Stop().

Ссылка на
пример: [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go).

```go
package main

import (
	"fmt"
	"log"
	"os"

	"github.com/green-api/whatsapp-api-client-golang/pkg/api"
	"github.com/green-api/whatsapp-api-client-golang/pkg/webhook"
)

func main() {
	IDInstance := os.Getenv("ID_INSTANCE")
	APITokenInstance := os.Getenv("API_TOKEN_INSTANCE")

	GreenAPI := api.GreenAPI{
		IDInstance:       IDInstance,
		APITokenInstance: APITokenInstance,
	}

	GreenAPIWebhook := webhook.GreenAPIWebhook{
		GreenAPI: GreenAPI,
	}

	GreenAPIWebhook.Start(func(body map[string]interface{}) {
		typeWebhook := body["typeWebhook"]
		if typeWebhook == "incomingMessageReceived" {
			senderData := body["senderData"]
			chatId := senderData.(map[string]interface{})["chatId"]

			response, err := GreenAPI.Methods().Sending().SendMessage(map[string]interface{}{
				"chatId":  chatId,
				"message": "Any message",
			})
			if err != nil {
				log.Fatal(err)
			}

			fmt.Println(response)

			GreenAPIWebhook.Stop()
		}
	})
}
```

### Список примеров

| Описание                | Ссылка на пример                                                                                                    |
|-------------------------|---------------------------------------------------------------------------------------------------------------------|
| Как создать группу      | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/create_group/main.go)        |
| Как отправить вложение  | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/send_file_by_upload/main.go) |
| Как отправить сообщение | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/send_message/main.go)        |
| Использование webhook   | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go)             | 
