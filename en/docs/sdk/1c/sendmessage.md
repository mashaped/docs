# Как отправить текстовое сообщение
### Установка
1. [Скачать обработку](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf) в формате epf
2. Подключиться к сервису через встроенный в обработку помощник или  самостоятельно через сайт [green-api.com](https://green-api.com/). Получить ``API Token`` и ``ID Instance``
3. Запустить в браузере или тонком клиенте и указать параметры подключения (``API Token`` и ``ID Instance``)
4. Сканировать QR код с мобильного телефона WhatsApp (Меню чаты -> Иконка всех функций -> Связанные устройства -> Привязка устройства)
6. В форме обработки нажать кнопку ``Проверить подключение``. Поле формы статус должно изменится на "Подключен"

![`Проверить подключение`](https://github.com/green-api/whatsapp-api-client-1c/blob/master/media/Login.png?raw=true)

### Использование обработки в собственных конфигурациях

Обработка имеет программный интерфейс, оформленный в соответствии со [стандартами разработки 1С](https://its.1c.ru/db/v8std). Вы можете встроить ее в свою конфигурацию и вызывать АПИ на сервере через создание объекта.

### Примеры

#### Как отправить текстовое сообщения используя обработку

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
