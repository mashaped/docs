# GetSettings

Метод предназначен для получения текущих настроек аккаунта.

## Запрос {#request}

Для получения текущих настроек аккаунта требуется выполнить запрос по адресу:
```
GET https://api.green-api.com/waInstance{{idInstance}}/GetSettings/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`wid` | **string** | Идентификатор аккаунта в WhatsApp
`countryInstance` | **string** | Код страны аккаунта по стандарту [ISO 3166-2](https://ru.wikipedia.org/wiki/ISO_3166-2)
`typeAccount` | **string** | Тип аккаунта, возможные значения: `trial`, `production`, `vip`
`webhookUrl` | **string** | URL для получения входящих уведомлений
`webhookUrlToken` | **string** | Токен для подключения к вашему вебхук серверу
`delaySendMessagesMilliseconds` | **integer** | [Интервал отправки сообщений](../send-messages-delay.md) в миллисекундах
`markIncomingMessagesReaded` | **string** | Отмечать входящие сообщения прочитанными или нет, возможные значения: `yes`, `no`. Игнорируется, если markIncomingMessagesReadedOnReply в значении 'yes'.
`markIncomingMessagesReadedOnReply` | **string** | Отмечать входящие сообщения прочитанными при отправке сообщения в чат через API, возможные значения: `yes`, `no`. Если в значении 'yes', то настройка markIncomingMessagesReaded игнорируется.
`outgoingWebhook` | **string** | Получать уведомления о статусах отправки/доставки/прочтении исходящих сообщений, возможные значения: `yes`, `no`
`outgoingMessageWebhook` | **string** | Получать уведомления о сообщениях, отправленных с телефона, возможные значения: `yes`, `no`
`stateWebhook` | **string** | Получать уведомления об изменении состояния авторизации аккаунта, возможные значения: `yes`, `no`
`incomingWebhook` | **string** | Получать уведомления о входящих сообщениях и файлах, возможные значения: `yes`, `no`
`deviceWebhook` | **string** | Получать уведомления об устройстве (телефоне) и уровне заряда батареи, возможные значения: `yes`, `no`
`statusInstanceWebhook` | **string** | Получать уведомления об изменении состояния соединения сокета аккаунта, возможные значения: `yes`, `no`
`sendFromUTC` | **string** | Получить настройку аккаунта интервал отправки из очереди в промежуток времени ОТ указанного (Внимание, время указано в UTC), возможные значения: `09:00`
`sendToUTC` | **string** |  Получить настройку аккаунта интервал отправки из очереди в промежуток времени ДО указанного (Внимание, время указано в UTC), возможные значения: `12:00`

### Пример тела ответа {#response-example-body}

```json
{
    "wid": "11001234567@c.us", 
    "countryInstance": "ru",
    "typeAccount": "vip",
    "webhookUrl": "https://mysite.com/webhook/green-api/",
    "webhookUrlToken": "",
    "delaySendMessagesMilliseconds": 3000,
    "markIncomingMessagesReaded": "yes",
    "markIncomingMessagesReadedOnReply": "no",
    "outgoingWebhook": "yes",
    "outgoingMessageWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no",
    "statusInstanceWebhook": "yes",
    "sendFromUTC": "12:00",
    "sendToUTC": "18:00"
}
```

### Ошибки GetSettings {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getSettings/{{apiTokenInstance}}"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```