# Incoming poll message

This section describes `messageData` object incoming webhook format for incoming poll message. For a description of the general format of incoming webhooks, refer to [Incoming Messages](Webhook-IncomingMessageReceived.md) section.

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `pollMessage`

## Webkhook {#webhook}

### Webhook parameters {#webhook-parameters}

`messageData` object parameters

| Parameter             | Type       | Description                                                                                     |
| --------------------- | ---------- | ----------------------------------------------------------------------------------------------- |
| `typeMessage`         | **string** | Incoming message type. For messages of this type the parameter takes on the value `pollMessage`.    |
| `pollCreationMessage` | **object** | Poll message data object                                                                        |

`pollCreationMessage`  object parameters

| Parameter                | Type        | Description         |
| ------------------------ | ----------- | ------------------- |
| `name`                   | **string**  | Poll name          |
| `options`                | **object**  | Poll options data object |
| `selectableOptionsCount` | **number**  | Selectable options number |

`options` object parameters

| Parameter                 | Type         | Description         |
| ------------------------- | ------------ | ------------------- |
| `optionName`              | **string**   | Option name  |

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
