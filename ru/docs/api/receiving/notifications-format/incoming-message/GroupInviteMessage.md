# Входящее сообщение приглашение в группу

В данном разделе описывается формат входящего уведомления объекта `messageData` для входящего сообщения приглашения в группу. Для получения описания общего формата входящих уведомлений обратитесь к разделу [Входящие сообщения](Webhook-IncomingMessageReceived.md).

Для получения входящих уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `groupInviteMessage`

## Уведомление {#webhook}

### Формат уведомления {#webhook-parameters}

Поля объекта `messageData`

| Параметр          | Тип        | Описание                                                                                                                                       |
| ----------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `typeMessage`     | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение: `groupInviteMessage`|
|`groupInviteMessageData` | **object** | Объект данных о принятом сообщении приглашении в группу |                                                                                                            |
| `quotedMessage`   | **object** | Объект данных о цитируемом сообщении. |

Поля объекта `groupInviteMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`groupJid` | **string** | chatId Группы
`inviteCode` | **string** | Код приглашения
`inviteExpiration` | **string** | Срок действия приглашения
`groupName` | **string** | Название группы
`caption` | **string** | Описание сообщения
`name` | **string** | Имя отправителя
`jpegThumbnail` | **string** |  Предпросмотр изображения в base64


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
    "typeMessage": "groupInviteMessage",
    "groupInviteMessageData": {
      "groupJid": "79099197688-1506012221@g.us",
      "inviteCode": "a7E5WU/g7rmjaQnv",
      "inviteExpiration": "0",
      "groupName": "Махловка, рисование 4-6",
      "caption": "Приглашение в мою группу WhatsApp",
      "name": "myname",
      "jpegThumbnail": "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"
    }
  }
}
```
