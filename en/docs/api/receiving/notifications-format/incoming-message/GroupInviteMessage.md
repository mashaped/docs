# Group invitation incoming message

This section describes `messageData` object incoming webhook format for group invitation incoming message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section.

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `groupInviteMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

| Parameter          | Type        | Description                                                                                                                                      |
| ----------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `typeMessage`     | **string** | Incoming message type. For messages of this type the parameter takes on the value: `groupInviteMessage`|
|`groupInviteMessageData` | **object** | Incoming group invitation message data object  |                                                                                                            |
| `quotedMessage`   | **object** | Quoted message data object. |

`groupInviteMessageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`groupJid` | **string** | Group chatId
`inviteCode` | **string** | Invitation code
`inviteExpiration` | **string** | Invitation expiration 
`groupName` | **string** | Group name
`caption` | **string** | Message caption
`name` | **string** | Sender's name
`jpegThumbnail` | **string** |  Image preview in base64


`quotedMessage` object parameters

| Parameter      | Type        | Description            |
| ------------- | ---------- | ------------------- |
| `stanzaId` | **string** | quoted message id |
| `participant` | **string** | quoted message sender's id |
| `typeMessage` | **string** | quoted  message type |

The rest of the fields are filled depending on the type of the quoted message and are identical to the fields of incoming messages described in [Incoming messages](Webhook-IncomingMessageReceived.md) section

### Webhook body example {#webhook-example-body}

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
    "chatName": "Green",
    "sender": "79001234568@c.us",
    "senderName": "Green"
  },
  "messageData": {
    "typeMessage": "groupInviteMessage",
    "groupInviteMessageData": {
      "groupJid": "79099197688-1506012221@g.us",
      "inviteCode": "a7E5WU/g7rmjaQnv",
      "inviteExpiration": "0",
      "groupName": "Makhlovka, drawing 4-6",
      "caption": "Invitation to my WhatsApp group",
      "name": "myname",
      "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQY/9k="
    }
  }
}
```
