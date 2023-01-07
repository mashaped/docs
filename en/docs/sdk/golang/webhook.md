# How to use webhook

### Installation

```shell
go get github.com/green-api/whatsapp-api-client-golang
```

### Example of sending a message

To start receiving events, you need to pass a handler function to GreenAPIWebhook.Start(). The handler function should
have 1 parameter (`body map[string]interface{}`). When a new event is received, your handler function will be executed.
To stop receiving events, you need to call GreenAPIWebhook.Stop().

Link to
example: [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go).

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

## List of examples

| Description                          | Link to example                                                                                                     |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Creating a group                     | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/create_group/main.go)        |
| Sending a message                    | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/send_message/main.go)        |
| Sending a message with an attachment | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/send_file_by_upload/main.go) |
| Using webhook                        | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go)             |
