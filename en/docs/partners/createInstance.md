# CreateInstance

The method is aimed for creating a messenger account instance on the partner's part.

## Request

To create an account instance on the partner's part you have to execute a POST request at:
```
https://api.green-api.com/partner/createInstance/{partnerToken}
```

>For `partnerToken`request parameter please contact Green API technical support (support@green-api.com) with a request to get a partnership API-token.

### Request parameters

Допускается указывать параметры выборочно. Хотя бы один параметр должен быть указан.

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`webhookUrl`| __string__ | optional | URL for sending webhook notifications
`webhookUrlToken` | __string__ | optional | Token for connection to your webhook server;
`delaySendMessagesMilliseconds` | __integer__ | optional | message sending delay in milliseconds, default is 3000 msec, minimum is 500 msec
`markIncomingMessagesReaded` | __string__ | optional | mark incoming messages as read or not (“yes”/”no”), default is “no”. Ignored if markIncomingMessagesReadedOnReply is “yes”
`markIncomingMessagesReadedOnReply` | __string__ | optional |  mark incoming messages as read or not (“yes”/”no”) when posting a message to the chat, default is “no” (incoming messages are not marked as read)
`outgoingWebhook` | __string__ | optional | Получать уведомления о статусах отправки/доставки/прочтении исходящих сообщений, возможные значения: “yes”, “no”. По умолчанию “no”
`outgoingMessageWebhook` | __string__ | необязательный | Получать уведомления о сообщениях, отправленных с телефона, возможные значения: “yes”, “no”.  По умолчанию “no”
`stateWebhook` | __string__ | необязательный | Получать уведомления об изменении состояния авторизации аккаунта, возможные значения: “yes”, “no”. По умолчанию “no”
`incomingWebhook` | __string__ | необязательный | Получать уведомления о входящих сообщениях и файлах, возможные значения: “yes”, “no”. По умолчанию “no”
`deviceWebhook` | __string__ | необязательный | Получать уведомления об устройстве (телефоне) и уровне заряда батареи, возможные значения: “yes”, “no”. По умолчанию “no”
`stateWebhook` | __string__ | необязательный | Получать уведомления об изменении состояния авторизации аккаунта, возможные значения: “yes”, “no”. По умолчанию “no”
`outgoingAPIMessageWebhook` | __string__ | необязательный | Получать уведомления о сообщениях, отправленных из API, возможные значения: “yes”, “no”.  По умолчанию “no”
`keepOnlineStatus` | __string__ | необязательный | Отображать статус инстанса “В сети”. Возможные значения: “yes”, “no”. По умолчанию “no”. Примечание: При включенной настройке не будут приходить звуковые уведомления о новых сообщениях на телефонный аппарат, подключенный к API


### Пример тела запроса

```json
{
    "webhookUrl": "https://mysite.com/webhook/green-api/",
    "webhookUrlToken": "f93537eb3e8fed66847b5bd",
    "delaySendMessagesMilliseconds": 1000,
    "markIncomingMessagesReaded": "no",
    "markIncomingMessagesReadedOnReply": "no",
    "outgoingAPIMessageWebhook": "yes",
    "outgoingWebhook": "yes",
    "outgoingMessageWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no",
    "stateWebhook": "no",
    "keepOnlineStatus": "no"
}
```

## Ответ 

### Поля ответа 

Поле | Тип |  Описание
----- | ----- | ----- 
`idInstance` | **int** | идентификатор инстанса аккаунта
`apiTokenInstance` | **string** | токен API инстанса аккаунта
`typeInstance` | **string** | тип мессенджера для инстанса аккаунта

### Пример тела ответа 

В случае успеха, в ответ на запрос, отдается JSON строка следующего вида с HTTP статусом 200:

```json
{
    "idInstance": 1101728000,
    "apiTokenInstance": "c1b0474542144e0ead529eb4861ca5f583c346eb00564f64a7",
    "typeInstance": "whatsapp"
}
```
В случае неудачи, отдается ответ с HTTP статусом 200, в теле ответа отдается JSON строка с кодом и описанием ошибки:

```json
{
    "code": 401,
    "description": "Unauthorized"
}
```
