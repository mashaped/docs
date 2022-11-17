# How to get a qr code
### Installation
```
npm i @green-api/whatsapp-api-client
```
### Import 
There are several ways how to import the library to a project
Using standard javascript 
```
const whatsAppClient = require("@green-api/whatsapp-api-client");
```
Using ES6 javascript 
```
import whatsAppClient from "@green-api/whatsapp-api-client";
```
Using typescript 
```
import * as whatsAppClient from "@green-api/whatsapp-api-client";
```
#### How to initialize an object

Store your authorization data separate from the code. The library allows you to create a file with an arbitrary name and location in the following format: 
```
API_TOKEN_INSTANCE = "MY_API_TOKEN_INSTANCE"
ID_INSTANCE = "MY_ID_INSTANCE"
```
You can pass the keys using the below example:
``` js
const restAPI = whatsAppClient.restAPI(({
    credentialsPath: "examples\\credentials"
}))
```
### Examples

You may see the full example at: [getQRCode.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCode.js)

#### How to get a qr code

``` js
import whatsAppClient from '@green-api/whatsapp-api-client'

(async () => {
    const restAPI = whatsAppClient.restAPI(({
        idInstance: process.env.ID_INSTANCE,
        apiTokenInstance: process.env.API_TOKEN_INSTANCE
    }))
    const response = await restAPI.instance.qr();
})();
```
### The full list of examples

Description |  Module
----- | ----- 
Example of sending text using Async| [SendWhatsAppMessageAsync.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageAsync.js)
Example of sending text using Callback| [SendWhatsAppMessageCallback.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageCallback.js)
Example of sending a picture by URL | [SendWhatsAppFileUrl.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUrl.js)
Example of sending a picture by uploading from the disk | [SendWhatsAppFileUpload.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUpload.js)
Example of receiving an incoming notification with the receiveNotification method| [ReceiveNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveNotifications.js)
Пример получения входящих уведомлений через webhook service REST API | [StartReceivingNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/StartReceivingNotifications.js)
Пример получения входящих уведомлений на сервер| [ReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveWebhook.js)
Example of getting a QR code via HTTP | [getQRCode.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCode.js)
Example of getting a QR code via websocket| [getQRCodeWebsocket.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCodeWebsocket.js)
