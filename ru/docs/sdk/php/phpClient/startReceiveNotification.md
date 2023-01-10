# Как обрабатывать входящие уведомления
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
Полный пример можно посмотреть по ссылке: [receiveNotification.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/receiveNotification.php)

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

#### Получение входящих сообщений через HTTP API

Общая концепция получения данных в Green API описана [здесь](https://green-api.com/docs/api/receiving/)
Для старта получения сообщений через HTTP API требуется выполнить метод библиотеки:

```
greenApi.webhooks.startReceivingNotifications(onEvent)
```

onEvent - ваш метод, который должен содержать параметры:

| Параметр    | Описание                           |
|-------------|------------------------------------|
| typeWebhook | тип полученного сообщения (строка) |
| body        | тело сообщения (json)              |

Типы и форматы тел сообщений [здесь](https://green-api.com/docs/api/receiving/notifications-format/)

Этот метод будет вызываться при получении входящего сообщения. Далее обрабатываете сообщения согласно бизнес-логике вашей системы.

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
