# Входящее сообщение-реакция

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения со стикером. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md).

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `stickerMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

| Параметр          | Тип        | Описание                                                                                                                                       |
| ----------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `typeMessage`     | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение: `stickerMessage`|
|`fileMessageData` | **object** | Объект данных о принятом стикере  |                                                                                                            |
| `quotedMessage`   | **object** | Объект данных о цитируемом сообщении  |

Поля объекта `fileMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`downloadUrl` | **string** | Ссылка на стикер
`jpegThumbnail` | **string** | Предпросмотр изображения в base64 |
`isAnimated` | **boolean** | Является ли стикер анимированным |
| `mimeType` | **string** | Тип файла, согласно класификации [Media Types](https://www.iana.org/assignments/media-types/media-types.xhtml) |
|`isForwarded` | **boolean** | Является ли сообщение пересланным, принимает значения true/false
|`forwardingScore` | **integer** | Количество пересылок сообщения


Поля объекта `quotedMessage`

| Параметр      | Тип        | Описание            |
| ------------- | ---------- | ------------------- |
| `stanzaId` | **string** | id цитируемого сообщения |
| `participant` | **string** | id отправителя цитируемого сообщения |
| `typeMessage` | **string** | Тип цитируемого сообщения |

Остальные поля заполняются в зависимости от типа цитируемого сообщения и идентичны полям входящих сообщений описаннных в разделе [Входящие сообщения](Webhook-IncomingMessageReceived.md)

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
    "chatName": "Грин",
    "sender": "79001234568@c.us",
    "senderName": "Грин"
  },
  "messageData": {
    "typeMessage": "stickerMessage",
    "fileMessageData": {
      "downloadUrl": "https://sw-media.storage.yandexcloud.net/9901742665/607dde0a-01dc-4dd9-8afb-707cbf610943.webp",
      "jpegThumbnail": "",
      "isAnimated": true,
      "mimeType": "image/webp",
      "forwardingScore": 1,
      "isForwarded": true
    },
    "quotedMessage": {
      "stanzaId": "A16014FAC9F5382E7B9CEEFEF1FFEB6F",
      "participant": "79001234568@c.us"
    }
  }
}
```
