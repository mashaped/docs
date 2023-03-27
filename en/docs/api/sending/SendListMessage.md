# Send List Message

The method is aimed for sending a message with a select button from a list of values to a personal or a group chat. 
The message will be added to the send queue. The message will be kept for 24 hours in the queue and will be sent immediately after phone authorization.
The rate at which messages are sent from the queue is managed by [Message sending delay](../send-messages-delay.md) parameter.

## Request {#request}

To send a message, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/SendListMessage/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Features when working with buttons {#features}

- there can be from 3 to 10 inclusive;
- button title length is up to 24 characters;
- menu item titles may be repeated.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Chat Id](../chat-id.md)
`message` | **string** | Yes | Message text. Emoji 😃 characters supported
`title` | **string** | No | Message title.
`footer` | **string** | No | Message footer. Useful for visually highlighting text related to buttons.
`buttonText` | **string** | Yes | select list button text
`sections` | **array** | Yes | select list values
`quotedMessageId` | **string** | No | Quoted message ID. If present, the message will be sent quoting the specified chat message
`archiveChat` | **boolean** | No | Archives the chat to which the message was sent.  Takes value: true|false

`sections` array parameters

Parameter | Type | Description
----- | ----- | -----
`title` | **string** | select list title
`rows` | **array** | select list values

`rows` array parameters

Parameter | Type | Description
----- | ----- | -----
`title` | **string** | list value text
`rowId` | **string** |list value Id


> The maximum length of a text message is 4096 characters

### Request body example {#request-example-body}

Sending a message to a personal chat:
```json
{
    "chatId": "11001234567@c.us",
    "message": "Message text",
    "title": "title",
    "footer": "footer",
    "buttonText": "Action list",
    "sections": [
        {
            "title": "Section 1",
            "rows": [
                {
                    "title": "Option 1",
                    "rowId": "option1"
                },
                {
                    "title": "Option 2",
                    "rowId": "option2",
                    "description": "Description"
                }
            ]
        },
        {
            "title": "Section 2",
            "rows": [
                {
                    "title": "Option 3",
                    "rowId": "option3"
                },
                {
                    "title": "Option 4",
                    "rowId": "option4",
                    "description": "Description"
                }
            ]
        }
    ]
}
```

## Response {#response}

### Response parameters {#response-parameters}

Parameter | Type |  Description
----- | ----- | -----
`idMessage ` | **string** | Sent message Id 

### Response body example {#response-example-body}

```json
{
    "idMessage": "3EB0C767D097B7C7C030"
}
```
### Recipient display example {#recieve-example}

![Пример списка выбора](../../assets/list-of-action.jpeg 'Пример списка выбора')

### SendMessage errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

??? warning "Possible mistakes"

    When using the SendListMessage method, messages may not be displayed on the web, desktop, and mobile versions of the application. The ability to send messages with buttons is implemented by us in a low-level way. The official WhatsApp-Web client does not provide the functionality of sending buttons. To a large extent, the stability of the SendListMessage method does not depend on us, WhatsApp constantly makes changes to their work.

    We recommend that you always duplicate buttons with regular messages.

    > For example, use numbers to define choices.

    > Choose an action:

    > 1 - action 1

    > 2 - action 2

    > 3 - action 3

## curl example

```
curl --location --request POST 'https://api.green-api.com/waInstance{{idInstance}}/sendListMessage/{{apiTokenInstance}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chatId": "11001234567@c.us",
    "message": "Message text",
    "buttonText": "Action list",
    "title": "title",
    "footer": "footer",
    "sections": [
        {
            "title": "Section 1",
            "rows": [
                {
                    "title": "Option 1",
                    "rowId": "option1"
                },
                {
                    "title": "Option 2",
                    "rowId": "option2",
                    "description": "Description"
                }
            ]
        },
        {
            "title": "Secton 2",
            "rows": [
                {
                    "title": "Option 3",
                    "rowId": "option3"
                },
                {
                    "title": "Option 4",
                    "rowId": "option4",
                    "description": "Description"
                }
            ]
        }
    ]
}'
```