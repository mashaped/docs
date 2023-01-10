# Как создать группу и отправить в неё сообщение
### Установка

Перед добавлением [пакета green-api](https://packagist.org/packages/green-api/whatsapp-api-client-php), необходимо установить менеджер зависимостей php [composer](https://getcomposer.org)

```
composer require green-api/whatsapp-api-client-php
```
### Import 
```
require './vendor/autoload.php';
```
### Примеры
Полный пример можно посмотреть по ссылке: [createGroupAndSendMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/createGroupAndSendMessage.php)

#### Как инициализировать объект

```
$greenApi = new GreenApiClient( ID_INSTANCE, API_TOKEN_INSTANCE );
```
Обратите внимание, что ключи можно получать из переменных среды:
```
<?php
require './vendor/autoload.php';

define( "ID_INSTANCE", getenv("ID_INSTANCE" ));
define( "API_TOKEN_INSTANCE", getenv("API_TOKEN_INSTANCE") );
```

#### Как создать группу и отправить в неё сообщение

```
$chatIds = [
	'11001234567@c.us'
];
$resultCreate = $greenApi->groups->createGroup('GroupName', $chatIds );

if ($resultCreate->code == 200)
	$resultSend = $greenApi->sending->sendMessage($resultCreate->data->chatId, 
	    'Message text');
```

ВАЖНО: Если попытаться создать группу с несуществующим номером, WhatsApp 
может заблокировать номер отправителя. Номер в примере не существует.

#### Запуск index.php

```
php -S localhost:8080
```

### Полный список примеров

| Описание                                             | Модуль                                                                                                                                   |
|------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Пример отправки текста                               | [sendTextMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendTextMessage.php)                     |
| Пример отправки картинки по URL                      | [sendPictureByLink.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByLink.php)                 |
| Пример отправки картинки загрузкой с диска           | [sendPictureByUpload.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByUpload.php)             |
| Пример создание группы и отправка сообщения в группу | [createGroupAndSendMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/createGroupAndSendMessage.php) |
| Пример получения входящих уведомлений                | [receiveNotification.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/receiveNotification.php)             |
