# Как принимать webhook endpoint уведомления на локальной машине

Для получения уведомлений Вам необходимо иметь статический адрес для запросов с нашего сервера, это возможно реализовать с помощью приложения ngrok.
Оно позволяет создать временный статический адрес и перенаправлять запросы с него на локальную машину. Данный механизм удобен для отладки вашего кода.

### Установка

Перейдите на сайт [ngrok](https://ngrok.com) зарегестрируйтесь и скачайте ngrok.

Установите пакеты для работы с примером
```
npm i express body-parser   
```
### Import 

Есть несколько способов импортировать библиотеку в проект

Используя классический javascript 
```
const express = require("express");
```
Используя ES6 javascript 
```
import express from "express";
```
Используя typescript 
```
import * as express from "express";
```

### Как принять webhook endpoint уведомление на локальной машине

Полный пример можно посмотреть по ссылке: [SampleReceiveWebhook.js](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/SampleReceiveWebhook.js)

Запустите пример используя команду:

```shell
node SampleReceiveWebhook.js  
```
В новом терминала запустите ngrok:

```shell
ngrok http 80  
```
В строке вы увидите адрес, который необходимо указать в настройках инстанса

> Forwarding ```http://32c4-146-158-66-240.ngrok-free.app -> http://localhost:80 ```

Так уведомление будет перенаправленно Вам на локальную машину.

> для завершения работы примера нажмите Ctrl+C

### Пример

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