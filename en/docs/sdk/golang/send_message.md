# How to send a message

### Installation

```shell
go get github.com/green-api/whatsapp-api-client-golang
```

### Example of sending a message

If an API method has optional parameters, you have to pass JSON to the library method (`map[string]interface{}`).

```go
package main

import (
	"fmt"
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

	response := GreenAPI.Methods().Sending().SendMessage(map[string]interface{}{
		"chatId":  "79001234567@c.us",
		"message": "Any message",
	})

	fmt.Println(response)
}
```
