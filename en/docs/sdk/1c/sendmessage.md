# How to send a text message
### Installation
1. [Download a processing model](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf) in the epf format
2. Connect to the service through the assistant built into the processing model or via [green-api.com](https://green-api.com/) web site. Get ``API Token`` and ``ID Instance``
3. Launch in a browser or thin client and specify connection parameters (``API Token`` and ``ID Instance``)
4. Scan QR code from your WhatsApp mobile phone. (Chats menu -> All functions icon -> Linked devices -> Device linking)
6. In the processing model form click the ``Check connection`` button. The form status parameter should change to "Connected"

![`Проверить подключение`](https://github.com/green-api/whatsapp-api-client-1c/blob/master/media/Login.png?raw=true)

### Using a processing model in your own configurations

The processing model has a software interface designed in accordance with [1C development standards](https://its.1c.ru/db/v8std). You can build it into your configuration and call the API on the server by initializing an object.

### Examples

#### How to send a text message using a processing model

![`Отправка сообщения`](https://github.com/green-api/whatsapp-api-client-1c/blob/master/media/Sending.png?raw=true)

1. Go to the ``Sending Messages`` tab
2. Specify the recipient's phone number and message text
3. Click the `Send text` button

#### How to send a text message using your own configuration

```bsl

API = Processing models.GreenAPI.Create();
API.IdInstance = "YOUR_INSTANCE";
API.ApiToken = "YOUR_TOKEN";
Response = API.SendText("79001234567", "Hello"); 

```
### The full list of examples

Description |  Module
----- | ----- 
1C demo processing model for WhatsApp| [GreenAPI.epf](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf)
Sources of 1C processing model for WhatsApp| [whatsapp-api-client-1c](https://github.com/green-api/whatsapp-api-client-1c)
