# How to send a file by uploading from the disk
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
You may see the full example at: [sendPictureByUpload.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByUpload.php)

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

####  How to send a file by uploading from the disk

```
$result = $greenApi->sending->sendFileByUpload('11001234567@c.us',
        'C:\Games\PicFromDisk.png', 'PicFromDisk.jpg', 'Picture from disk');
```
### The full list of examples

| Description                                                    | Module                                                                                                                                   |
|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Example of sending text                                        | [sendTextMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendTextMessage.php)                     |
| Example of sending a picture by URL                            | [sendPictureByLink.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByLink.php)                 |
| Example of sending a picture by uploading from the disk        | [sendPictureByUpload.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByUpload.php)             |
| Example of a group creation and sending a message to the group | [createGroupAndSendMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/createGroupAndSendMessage.php) |
| Example of incoming webhooks receiving                         | [receiveNotification.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/receiveNotification.php)             |
