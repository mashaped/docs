# How to receive webhook endpoint notifications on the local machine

To receive notifications, you need to have a static address for requests from our server, this can be implemented using the ngrok application.
It allows you to create a temporary static address and redirect requests from it to the local machine. This mechanism is convenient for debugging your code.

### Installation

Go to [ngrok](https://ngrok.com) register and download ngrok.

Install packages to work with the example
```
npm i express body-parser   
```
### Import 

There are several ways to import a library into a project

Using classic javascript
```
const express = require("express");
```
Using ES6 javascript
```
import express from "express";
```
Using typescript
```
import * as express from "express";
```

### How to receive a webhook endpoint notification on the local machine

The full example can be viewed here: [SampleReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SampleReceiveWebhook.js)

Run the example using the command:

```shell
node SampleReceiveWebhook.js  
```
In a new terminal, run ngrok:

```shell
ngrok http 80  
```
In the line you will see the address that must be specified in the instance settings

> Forwarding ```http://32c4-146-158-66-240.ngrok-free.app -> http://localhost:80 ```

So the notification will be redirected to your local machine.

> to end the example, press Ctrl+C

### Example

``` js
const express = require('express');
const bodyParser = require('body-parser');

(async () => {
  try {

    const app = express();
    const port = 80;

    app.use(bodyParser.json());
    app.post('/', (req, res) => {
      console.log(req.body);
      res.status(200).send('');
    });
    
    
    app.listen(port, () => {
      console.log(`Server is listening on port ${port}`);
    });
  } catch (error) {
      console.error(error);
      process.exit(1);
  }
})();

```
### Full list of examples

Description | Module
----- | -----
An example of sending text using Async| [SendWhatsAppMessageAsync.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageAsync.js)
Example of sending text using Callback| [SendWhatsAppMessageCallback.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageCallback.js)
Example of sending a picture by URL | [SendWhatsAppFileUrl.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUrl.js)
An example of sending a picture by loading from a disk | [SendWhatsAppFileUpload.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUpload.js)
An example of receiving an incoming notification using the receiveNotification| [ReceiveNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveNotifications.js)
Example of receiving a webhook endpoint notification on the local machine| [SampleReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SampleReceiveWebhook.js)
Example of receiving incoming notifications via webhook service REST API | [StartReceivingNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/StartReceivingNotifications.js)
Example of receiving incoming notifications on the server| [ReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveWebhook.js)
An example of obtaining a QR code via HTTP | [getQRCode.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCode.js)
An example of receiving a QR code via websocket| [getQRCodeWebsocket.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCodeWebsocket.js)