# Как принять и обработать уведомления используя сервер
### Установка
```
npm i @green-api/whatsapp-api-client express body-parser   
```
### Import 
Есть несколько способов импортировать библиотеку в проект

Используя классический javascript 
```
const whatsAppClient = require("@green-api/whatsapp-api-client");
```
Используя ES6 javascript 
```
import whatsAppClient from "@green-api/whatsapp-api-client";
```
Используя typescript 
```
import * as whatsAppClient from "@green-api/whatsapp-api-client";
```
#### Как инициализировать объект

Храните Ваши авторизационные данные отдельно от кода. Библиотека позволяет создать файл с произвольным именем и местом в следующем формате: 
```
API_TOKEN_INSTANCE = "MY_API_TOKEN_INSTANCE"
ID_INSTANCE = "MY_ID_INSTANCE"
```
Передать ключи, можно используя пример ниже:
``` js
const restAPI = whatsAppClient.restAPI(({
    credentialsPath: "examples\\credentials"
}))
```
### Примеры

Полный пример можно посмотреть по ссылке: [ReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveWebhook.js)

#### Как принять и обработать уведомления используя сервер
Работает только в node js на базе express

``` js
const whatsAppClient = require("@green-api/whatsapp-api-client");
const express = require("express");
const bodyParser = require("body-parser");

// Receive webhook
(async () => {
    try {

        const app = express();
        const webHookAPI = whatsAppClient.webhookAPI(app, '/')
        app.use(bodyParser.json());

        webHookAPI.onIncomingMessageText((data, idInstance, idMessage, sender, typeMessage, textMessage) => {
            console.log(`Incoming Notification data ${JSON.stringify(data)}`)
        });

        app.listen(80, async () => {
            console.log(`Started. App listening on port 80!`)
        });
    } catch (error) {
        console.error(error);
        process.exit(1);
    }
})();

```
### Полный список примеров

Описание |  Модуль
----- | ----- 
Пример отправки текста используя Async| [SendWhatsAppMessageAsync.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageAsync.js)
Пример отправки текста используя Callback| [SendWhatsAppMessageCallback.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppMessageCallback.js)
Пример отправки картинки по URL | [SendWhatsAppFileUrl.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUrl.js)
Пример отправки картинки загрузкой с диска | [SendWhatsAppFileUpload.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SendWhatsAppFileUpload.js)
Пример получения входящего уведомления методом receiveNotification| [ReceiveNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveNotifications.js)
Пример получения webhook endpoint уведомления на локальной машине| [SampleReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SampleReceiveWebhook.js)
Пример получения входящих уведомлений через webhook service REST API | [StartReceivingNotifications.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/StartReceivingNotifications.js)
Пример получения входящих уведомлений на сервер| [ReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/ReceiveWebhook.js)
Пример получения QR кода по HTTP | [getQRCode.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCode.js)
Пример получения QR кода по websocket| [getQRCodeWebsocket.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/getQRCodeWebsocket.js)