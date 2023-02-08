# Входящее сообщение опроса

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения опроса. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md).

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `pollMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

| Параметр              | Тип        | Описание                                                                                        |
| --------------------- | ---------- | ----------------------------------------------------------------------------------------------- |
| `typeMessage`         | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `pollMessage`       |
| `pollCreationMessage` | **object** | Объект данных о сообщении опроса                                                                |

Поля объекта `pollCreationMessage`

| Параметр                 | Тип         | Описание            |
| ------------------------ | ----------- | ------------------- |
| `name`                   | **string**  | Название опроса     |
| `options`                | **object**  | Объект данных о вариантах выбора опроса |
| `selectableOptionsCount` | **number**  | Количество выбираемых вариантов |

Поля объекта `options`

| Параметр                 | Тип         | Описание            |
| ------------------------ | ----------- | ------------------- |
| `optionName`             | **string**  | Название варианта выбора |

### Пример тела уведомления {#webhook-example-body}

```json
{
  "typeWebhook": "incomingMessageReceived",
  "instanceData": {
    "idInstance": 1234,
    "wid": "11001234567@c.us",
    "typeInstance": "whatsapp"
  },
  "timestamp": 1588091580,
  "idMessage": "F7AEC1B7086ECDC7E6E45923F5EDB825",
  "senderData": {
    "chatId": "79001234568@c.us",
    "sender": "79001234568@c.us",
	"chatName": "Green API",
    "senderName": "Green API"
  },
  "messageData": {
    "typeMessage": "pollMessage",
    "pollCreationMessage": {
      "name": "Poll Name",
      "options": [
        {
          "optionName": "Variant 1"
        },
        {
          "optionName": "Variant 2"
        }
      ],
      "selectableOptionsCount": 0
    }
  }
}
```
