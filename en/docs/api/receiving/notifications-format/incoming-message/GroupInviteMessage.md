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
      "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQY/9k="
    }
  }
}
```
