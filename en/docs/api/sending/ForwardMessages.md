# ForwardMessages

The method is intended for forwarding messages to a personal or group chat.
The forwarded messages will be added to the send queue. The message will be kept for 24 hours in the queue and will be sent immediately after phone authorization.
The rate at which messages are sent from the queue is managed by [Message sending delay](../send-messages-delay.md) parameter.

## Request {#request}

For forwarding, you need to make a request to:
```
POST https://api.green-api.com/waInstance{{idInstance}}/forwardMessages/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

| Parameter    | Type              | Mandatory | Description                                                         |
|--------------|-------------------|-----------|---------------------------------------------------------------------|
| `chatId`     | **string**        | Yes       | [Chat Id](../chat-id.md), from which the message is being forwarded |
| `chatIdFrom` | **string**        | Yes       | [Chat Id](../chat-id.md), where the message is forwarded            |
| `messages`   | **array<string>** | Yes       | Collection of IDs of forwarded messages                             |

### Request body example {#request-example-body}

Forwarding a message to a chat:
```json
{
    "chatId": "11001234567@c.us",
    "chatIdFrom": "11001234567@c.us",
    "messages": [
       "BAE587FA1CECF760",
       "BAE5608BC86F2B59"
    ]
}
```

## Response {#response}

### Response parameters {#response-parameters}

| Parameter  | Type              | Description          |
|------------|-------------------|----------------------|
| `messages` | **array<string>** | Ids of sent messages |

### Response body example {#response-example-body}

```json
{
  "messages": [
    "BAE5DBB8DEABDA22",
    "BAE5BBA9BE3142D8"
  ]
}
```
### Recipient display example {#recieve-example}

![Example of a forwarded message](../../assets/forward-message.jpg 'Example of a forwarded message')

### ForwardMessages errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## curl example

```
curl --location --request POST 'https://api.green-api.com/waInstance{{idInstance}}/forwardMessages/{{apiTokenInstance}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chatId": "11001234567@c.us",
    "chatIdFrom": "11001234567@c.us",
    "messages": [
        "BAE587FA1CECF760",
        "BAE5608BC86F2B59"
    ]
}'
```