# Incoming contacts array message
This section describes `messageData` object incoming webhook format for incoming contacts array message. For a description of the general format of incoming webhooks, refer to [Incoming messages](Webhook-IncomingMessageReceived.md) section.

To get incoming webhooks of this type, two conditions must be true:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `contactsArrayMessage`

## Webhook {#webhook}

### Webhok parameters {#webhook-parameters}

`messageData` object parameters

| Parameter             | Type        | Description                                                                                        |
| -------------------- | ---------- | ----------------------------------------------------------------------------------------------- |
| `typeMessage`        | **string** | Incoming message type. For messages of this type the parameter takes on the value `contactsArrayMessage` |
| `contacts` | **object** | Incoming contact data object.                                                              |
| `quotedMessage`      | **object** | Quoted message data object. Present only if the message itself is a quote |
|`isForwarded` | **boolean** | Whether the message is forwarded, takes on values true/false|
|`forwardingScore` | **integer** | Number of message forwards|

`contacts` object parameters

| Parameter      | Type        | Description                                     |
| ------------- | ---------- | -------------------------------------------- |
| `displayName` | **string** | Displayed contact name                 |
| `vcard`       | **string** | СVCard structure (contact visit card) |


`quotedMessage` object parameters

| Parameter      | Type        | Description                             |
| ------------- | ---------- | ------------------------------------ |
| `stanzaId`    | **string** | quoted message id             |
| `participant` | **string** | quoted message sender's id |
| `typeMessage` | **string** | quoted message type            |

The rest of the fields are filled depending on the type of the quoted message and are identical to the fields of incoming messages described in [Incoming messages](Webhook-IncomingMessageReceived.md)

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
    "typeMessage": "ContactsArrayMessage",
    "contacts":  [
		{
			"displayName": "Victor Andreevich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Mobile\nEND:VCARD"
		},
		{
			"displayName": "Oleg edrosovich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Mobile\nEND:VCARD"
		}
    ],
	"forwardingScore": 4,
    "isForwarded": true
    }
  }
}
```

### Contacts array and text message quote incoming message webhook body example {#webhook-example-body1}

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
    "typeMessage": "ContactsArrayMessage",
    "contacts":  [
		{
			"displayName": "Victor Andreevich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Mobile\nEND:VCARD"
		},
		{
			"displayName": "Oleg edrosovich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Mobile\nEND:VCARD"
		}
    ],
	"forwardingScore": 4,
    "isForwarded": true
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79001235696@c.us",
      "typeMessage": "textMessage",
      "textMessage": "Hello"
    }
  }
}
```

### Contacts array and audio/video/document quote incoming message webhook body example {#webhook-example-body2}

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
    "typeMessage": "ContactsArrayMessage",
    "contacts":  [
		{
			"displayName": "Victor Andreevich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Мобильный\nEND:VCARD"
		},
		{
			"displayName": "Oleg edrosovich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Mobile\nEND:VCARD"
		}
    ],
	"forwardingScore": 4,
    "isForwarded": true
    },
    "quotedMessage": {
         "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
         "participant": "79061230000@c.us",
         "typeMessage": "imageMessage",
         "downloadUrl": "",
          "caption": "",
          "jpegThumbnail": ""
    }
  }
```

### Contacts array and contact quote incoming message webhook body example {#webhook-example-body3}

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
    "typeMessage": "ContactsArrayMessage",
    "contacts":  [
		{
			"displayName": "Victor Andreevich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich, Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Mobile\nEND:VCARD"
		},
		{
			"displayName": "Oleg edrosovich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:MobileND\nEND:VCARD"
		}
    ],
	"forwardingScore": 4,
    "isForwarded": true
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79061230000@c.us",
      "typeMessage": "contactMessage",
      "contact": {
        "displayName": "Green-Api",
        "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Green-Api\nitem1.TEL;waid=79001230000\nitem1.X-ABLabel:Mobile\nEND:VCARD"
      }
    }
  }
}
```
### Contacts array and location quote incoming message webhook body example {#webhook-example-body4}

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
    "typeMessage": "ContactsArrayMessage",
    "contacts":  [
		{
			"displayName": "Victor Andreevich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Mobile\nEND:VCARD"
		},
		{
			"displayName": "Oleg edrosovich",
			"vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Andreevich;Victor;;;\nFN:Victor Andreevich\nORG:Image\nTITLE:\nitem1.TEL;waid=79001234569:+7 900 123-45-69\nitem1.X-ABLabel:Mobile\nEND:VCARD"
		}
    ],
	"forwardingScore": 4,
    "isForwarded": true
    },
    "quotedMessage": {
      "stanzaId": "9A73322488DCB7D9689A6112F2528C9D",
      "participant": "79060002233@c.us",
      "typeMessage": "locationMessage",
      "location": {
        "nameLocation": "",
        "address": "",
        "jpegThumbnail": "",
        "latitude": 72.5922702,
        "longitude": 45.6645388
      }
    }
  }
}
```
