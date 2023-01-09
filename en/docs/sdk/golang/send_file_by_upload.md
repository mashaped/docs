# How to send a message with an attachment

### Installation

```shell
go get github.com/green-api/whatsapp-api-client-golang
```

### Example of sending a message with an attachment

To send an attachment, you need to give the path to the attachment.

Link to
example: [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/send_file_by_upload/main.go).

```go
package main

import (
	"fmt"
	"log"
	//"os"

	"github.com/green-api/whatsapp-api-client-golang/pkg/api"
)

func main() {
	//You can set environment variables in your OS
	//
	//IDInstance := os.Getenv("ID_INSTANCE")
	//APITokenInstance := os.Getenv("API_TOKEN_INSTANCE")

	GreenAPI := api.GreenAPI{
		IDInstance:       "IDInstance",
		APITokenInstance: "APITokenInstance",
	}

	response, err := GreenAPI.Methods().Sending().SendFileByUpload("example.png", map[string]interface{}{
		"chatId": "11001234567@c.us",
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
| Receiving incoming webhooks          | [main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go)             |
