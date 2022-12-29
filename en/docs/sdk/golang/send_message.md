# How to send a message

### Installation

```shell
go get github.com/green-api/whatsapp-api-client-golang/v1
```

### Example of sending a message

If an API method has optional parameters, you have to pass JSON to the library method (`map[string]interface{}`).

Link to
example: [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/send_message/main.go).

```go
package main

import (
	"fmt"
	"log"
	"os"

	"github.com/green-api/whatsapp-api-client-golang/v1/pkg/api"
)

func main() {
	IDInstance := os.Getenv("ID_INSTANCE")
	APITokenInstance := os.Getenv("API_TOKEN_INSTANCE")

	GreenAPI := api.GreenAPI{
		IDInstance:       IDInstance,
		APITokenInstance: APITokenInstance,
	}

	response, err := GreenAPI.Methods().Sending().SendMessage(map[string]interface{}{
		"chatId":  "79373263431@c.us",
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
