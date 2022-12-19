# Как отправить текстовое сообщение
### Установка
```
composer require green-api/whatsapp-api-client-php
```
### Import 
```
require 'vendor\autoload.php';
```
### Примеры
Пример отправки текста | [sendTextMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendTextMessage.php)

#### Как инициализировать объект

```
$greenApi = new GreenApiClient( ID_INSTANCE, API_TOKEN_INSTANCE );
```
Обратите внимание, что ключи можно получать из переменных среды:
```
<?php
require 'vendor/autoload.php';

define( "ID_INSTANCE", getenv("ID_INSTANCE" ));
define( "API_TOKEN_INSTANCE", getenv("API_TOKEN_INSTANCE") );
```
#### Как отправить текстовое сообщения на номер WhatsApp

```
$result = $greenApi->sending->sendMessage('11001234567@c.us', 'Message text');
```
### Полный список примеров

| Описание                                             | Модуль                                                                                                                                   |
|------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Пример отправки текста                               | [sendTextMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendTextMessage.php)                     |
| Пример отправки картинки по URL                      | [sendPictureByLink.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByLink.php)                 |
| Пример отправки картинки загрузкой с диска           | [sendPictureByUpload.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByUpload.php)             |
| Пример создание группы и отправка сообщения в группу | [createGroupAndSendMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/createGroupAndSendMessage.php) |
| Пример получения входящих уведомлений                | [receiveNotification.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/receiveNotification.php)             |
