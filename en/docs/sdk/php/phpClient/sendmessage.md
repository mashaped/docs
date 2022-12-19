# How to send a text message
### Installation
```
composer require green-api/whatsapp-api-client-php
```
### Import 
```
require 'vendor\autoload.php';
```
### Examples
You may see the full example at: [sendTextMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendTextMessage.php)


#### How to initialize an object

```
$greenApi = new GreenApiClient( ID_INSTANCE, API_TOKEN_INSTANCE );
```
Please note that keys can be obtained from environment variables:
```
<?php
require 'vendor/autoload.php';

define( "ID_INSTANCE", getenv("ID_INSTANCE" ));
define( "API_TOKEN_INSTANCE", getenv("API_TOKEN_INSTANCE") );
```
#### How to send a text message to a WhatsApp number

```
$result = $greenApi->sending->sendMessage('11001234567@c.us', 'Message text');
```
### The full list of examples

| Description                                                    | Module                                                                                                                                   |
|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Example of sending text                                        | [sendTextMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendTextMessage.php)                     |
| Example of sending a picture by URL                            | [sendPictureByLink.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByLink.php)                 |
| Example of sending a picture by uploading from the disk        | [sendPictureByUpload.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/sendPictureByUpload.php)             |
| Example of a group creation and sending a message to the group | [createGroupAndSendMessage.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/createGroupAndSendMessage.php) |
| Example of incoming webhooks receiving                         | [receiveNotification.php](https://github.com/green-api/whatsapp-api-client-php/blob/master/examples/receiveNotification.php)             |
