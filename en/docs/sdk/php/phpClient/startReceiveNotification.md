# How to handle incoming notifications
### Installation

Before adding the [green-api package](https://packagist.org/packages/green-api/whatsapp-api-client-php), you need to install [composer](https://getcomposer.org) (php dependency manager).

```
composer require green-api/whatsapp-api-client-php
```
### Import 
```
require './vendor/autoload.php';
```
### Examples
You may see the full example at: [receiveNotification.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/receiveNotification.php)

#### How to initialize an object

```
$greenApi = new GreenApiClient( ID_INSTANCE, API_TOKEN_INSTANCE );
```
Please note that keys can be obtained from environment variables:
```
<?php
require './vendor/autoload.php';

define( "ID_INSTANCE", getenv("ID_INSTANCE" ));
define( "API_TOKEN_INSTANCE", getenv("API_TOKEN_INSTANCE") );
```

#### Receiving incoming messages by HTTP API

The general concept of receiving data in the Green API is described [here](https://green-api.com/en/docs/api/receiving/)
To start receiving messages by the HTTP API, you need to execute the library method:

```
greenApi.webhooks.startReceivingNotifications(onEvent)
```

onEvent - your method which should contain parameters:

| Parameter   | Description                    |
|-------------|--------------------------------|
| typewebhook | received message type (string) |
| body        | message body (json)            |

Message body types and formats [here](https://green-api.com/en/docs/api/receiving/notifications-format/)

This method will be called when an incoming message is received. Next, process messages according to the business logic of your system.

### The full list of examples

| Description                                                    | Module                                                                                                                                   |
|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Example of sending text                                        | [sendTextMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendTextMessage.php)                     |
| Example of sending a picture by URL                            | [sendPictureByLink.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByLink.php)                 |
| Example of sending a picture by uploading from the disk        | [sendPictureByUpload.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByUpload.php)             |
| Example of a group creation and sending a message to the group | [createGroupAndSendMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/createGroupAndSendMessage.php) |
| Example of incoming webhooks receiving                         | [receiveNotification.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/receiveNotification.php)             |
