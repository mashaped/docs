# How to run the web server

### Installation

Do not forget to create a module:

```shell
go mod init example
```

Installation:

```shell
go get github.com/green-api/whatsapp-api-webhook-server-golang
```

### Import

```
import (
	"github.com/green-api/whatsapp-api-webhook-server-golang/pkg"
)
```

### Examples

#### How to initialize an object

The WebhookToken attribute is optional.

```
webhook := pkg.Webhook{
    Address:      ":80",
    Pattern:      "/",
}
```

#### How to run the web server

The StartServer function takes a handler function. The handler function must have 1
parameter (`body map[string]interface{}`). When a new notification is received, your handler function will be executed.

Link to example: [main.go](
https://github.com/green-api/whatsapp-api-webhook-server-golang/blob/master/examples/main.go
).

```
_ := webhook.StartServer(func(body map[string]interface{}) {
    fmt.Println(body)
})
```

### Running the application

```shell
go run main.go
```
