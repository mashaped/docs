# How to send a message

### Installation

Do not forget to create a module:

```shell
go mod init example
```

Installation:

```shell
go get github.com/green-api/whatsapp-api-client-golang
```

### Import

```
import (
	"github.com/green-api/whatsapp-api-client-golang/pkg/api"
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

#### How to send a message

If an API method has optional parameters, you have to pass JSON to the library method (`map[string]interface{}`).

Link to example: [sendMessage/main.go](
https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendMessage/main.go
).

```
response, _ := GreenAPI.Methods().Sending().SendMessage(map[string]interface{}{
    "chatId":  "11001234567@c.us",
    "message": "Any message",
})
```

### Running the application

```shell
go run main.go
```

### List of examples

| Description                                   | Link to example                                                                                                                   |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| How to create a group                         | [createGroup/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/createGroup/main.go)           |
| How to send a file by uploading from the disk | [sendFileByUpload/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendFileByUpload/main.go) |
| How to send a file by URL                     | [sendFileByURL/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendFileByURL/main.go)       |
| How to send a message                         | [sendMessage/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/sendMessage/main.go)           |
| How to receive incoming notifications         | [webhook/main.go](https://github.com/green-api/whatsapp-api-client-golang/blob/master/examples/webhook/main.go)                   |
