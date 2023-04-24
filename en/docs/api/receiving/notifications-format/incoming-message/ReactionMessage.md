# Incoming reaction message

This section describes `messageData` object incoming webhook format for incoming reaction message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section.

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `reactionMessage`

## Webhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

| Parameter          | Type        | Description                                                                                                                                       |
| ----------------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `typeMessage`     | **string** | Incoming message type. For messages of this type the parameter takes on the value: `reactionMessage`|
|`extendedTextMessageData` | **object** | Incoming reaction message data object  |                                                                                           |
| `quotedMessage`   | **object** | Quoted message data object. The message the correspondent has reacted to   |

`extendedTextMessageData` object parameters

Parameter | Type | Description
----- | ----- | -----
`text` | **string** | Reaction (emoji) to the message


`quotedMessage` object parameters

| Parameter     | Type        | Description            |
| ------------- | ---------- | ------------------- |
| `stanzaId` | **string** | quoted message id |
| `participant` | **string** | quoted message sender's id |
| `typeMessage` | **string** | quoted message type |

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
    "typeMessage": "reactionMessage",
    "extendedTextMessageData": {
      "text": "👍"
    },
    "quotedMessage": {
      "stanzaId": "A16014FAC9F5382E7B9CEEFEF1FFEB6F",
      "participant": "79001234568@c.us"
    }
  }
}
```
