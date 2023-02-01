# How to receive incoming notifications

### Installation

```shell
go get github.com/green-api/whatsapp-api-client-golang
```

### Import

```
import (
	"github.com/green-api/whatsapp-api-client-golang/pkg/api"
	"github.com/green-api/whatsapp-api-client-golang/pkg/webhook"
)
```

### Examples

#### How to initialize an object

```
GreenAPI := api.GreenAPI{
    IDInstance:       "1234",
    APITokenInstance: "bde035edae3fc00bc116bd112297908d8145e5ba8decc5d884",
}
```

Note that keys can be obtained from environment variables:

```
IDInstance := os.Getenv("ID_INSTANCE")
APITokenInstance := os.Getenv("API_TOKEN_INSTANCE")
```

#### How to receive incoming notifications

To start receiving incoming webhooks, you need to send a handler function to GreenAPIWebhook.Start(). The handler
function should have 1 parameter (`body map[string]interface{}`). When you receive a new notification, your handler
function will be executed. To stop receiving incoming webhooks, you need to call GreenAPIWebhook.Stop().

Link to
example: [webhook/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go).

```
GreenAPIWebhook := webhook.GreenAPIWebhook{
    GreenAPI: GreenAPI,
}

GreenAPIWebhook.Start(func(body map[string]interface{}) {
    typeWebhook := body["typeWebhook"]
    if typeWebhook == "incomingMessageReceived" {
        senderData := body["senderData"]
        chatId := senderData.(map[string]interface{})["chatId"]

        response, _ := GreenAPI.Methods().Sending().SendMessage(map[string]interface{}{
            "chatId":  chatId,
            "message": "Any message",
        })

        GreenAPIWebhook.Stop()
    }
})
```

#### Running main.go

```shell
go run main.go
```

### List of examples

| Description                           | Link to example                                                                                                                   |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| How to create a group                 | [createGroup/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/createGroup/main.go)           |
| How to send an attachment             | [sendFileByUpload/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendFileByUpload/main.go) |
| How to send an attachment by URI      | [sendFileByURL/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendFileByURL/main.go)       |
| How to send a message                 | [sendMessage/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendMessage/main.go)           |
| How to receive incoming notifications | [webhook/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go)                   |
