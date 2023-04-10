# How to receive and process a notification using a server
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

You may see the full example at: [ReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveWebhook.js)

#### How to receive and process a notification using a server
Only works in node js with express based

``` js
import whatsAppClient from '@green-api/whatsapp-api-client'
import express from "express";
import bodyParser from 'body-parser';

(async () => {
    try {

        // Set http url where webhooks will be sent to. 
        // Url must have a public address.
        await restAPI.settings.setSettings({
            webhookUrl: 'MY_HTTP_SERVER:3000/webhooks'
        });

        const app = express();
        app.use(bodyParser.json());
        const webHookAPI = whatsAppClient.webhookAPI(app, '/webhooks')

        // Subscribe to the webhook event upon a message receipt
        webHookAPI.onIncomingMessageText((data, idInstance, idMessage, sender, typeMessage, textMessage) => {
            console.log(`outgoingMessageStatus data ${data.toString()}`)
        });

        // Start a web server with a public address
        app.listen(3000, async () => {
            console.log(`Started. App listening on port 3000!`)

            const restAPI = whatsAppClient.restAPI(({
                idInstance: MY_ID_INSTANCE,
                apiTokenInstance: MY_API_TOKEN_INSTANCE
            }));
            // Send a text message to trigger webhook events
            const response = await restAPI.message.sendMessage("79999999999@c.us", null, "hello world");
    
        });
    } catch (error) {
        console.error(error);
        process.exit(1);
    }
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
Example of receiving a webhook endpoint notification on the local machine| [SampleReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SampleReceiveWebhook.js)
Example of receiving incoming notifications via webhook service REST API | [StartReceivingNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/StartReceivingNotifications.js)
Example of receiving incoming notifications to a server| [ReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveWebhook.js)
Example of getting a QR code via HTTP | [getQRCode.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCode.js)
Example of getting a QR code via websocket| [getQRCodeWebsocket.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCodeWebsocket.js)
