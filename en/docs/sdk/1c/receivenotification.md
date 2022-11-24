# How to receive a message
### Installation
1. [Download a processing model](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf) in the epf format
2. Connect to the service through the assistant built into the processing model or via [green-api.com](https://green-api.com/) web site. Get ``API Token`` and ``ID Instance``
3. Launch in a browser or thin client and specify connection parameters (``API Token`` and ``ID Instance``)
4. Scan QR code с мобильного телефона WhatsApp (Меню чаты -> Иконка всех функций -> Связанные устройства -> Привязка устройства)
6. В форме обработки нажать кнопку ``Проверить подключение``. Поле формы статус должно изменится на "Подключен"

![`Проверить подключение`](https://github.com/green-api/whatsapp-api-client-1c/blob/master/media/Login.png?raw=true)

### Using a processing model in your own configurations

The processing model has a software interface designed in accordance with [1C development standards](https://its.1c.ru/db/v8std). You can build it into your configuration and call the API on the server by initializing an object.

### Examples

#### How to receive a message using a processing model

![`Получение сообщения`](https://github.com/green-api/whatsapp-api-client-1c/blob/master/media/Receiving.png?raw=true)

1. Go to the ``Receiving Messages`` tab
2. Click on the ``Receive a message`` button. If a message has been sent, then the ``Message body`` parameter will be filled in with the data in JSON format. If there are no messages sent, then the processing model will wait 20 seconds to receive a message.

### The full list of examples

Description |  Module
----- | ----- 
1C demo processing model for WhatsApp| [GreenAPI.epf](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf)
Sources of 1C processing model for WhatsApp| [whatsapp-api-client-1c](https://github.com/green-api/whatsapp-api-client-1c)
