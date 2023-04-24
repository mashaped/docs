# SendTemplate

The method is aimed for sending a template message from the official API. It is useful for bulk emailing. To send this type of a message, you must have or previously create a message template. If you do not have your own template, then we can help you. For this, please contact us via email support@green-api.com or in any other convenient way.

## Request {#request}

To send a message, you have to execute a request at:
```
POST https://api.green-api.com/waInstance{{idInstance}}/sendTemplate/{{apiTokenInstance}}
```

For `idInstance` and `apiTokenInstance` request parameters, refer to [Before you start](../../before-start.md#parameters) section.

### Request parameters {#request-parameters}

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`chatId` | **string** | Yes | [Chat Id](../chat-id.md)
`namespace` | **string** | Yes | Name of the names space from the official API
`namespace` | **string** | Yes | Message template name
`languageCode` | **string** | Yes | Message template localization language code
`params` | **array** | No | Array of parameters used in the template. Mandatory if the template uses parameters
`quotedMessageId` | **string** | No | Quoted message ID. If present, the message will be sent quoting the specified chat message

`params` array parameters

Parameter | Type | Description
----- | ----- | -----
`default` | **string** | default parameter value


### Request body example {#request-example-body}

Sending a message to a personal chat:
```json
{
    "chatId": "11001234567@c.us",
    "namespace": "not_existing_namespace",
    "name": "not_existing_template",
    "languageCode": "ru",
    "params": [
        {"default": "Dear customer"}
    ]
}

```
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

### Errors {#errors}

For a list of errors common to all methods, refer to [Common errors](../common-errors.md) section

## curl example  {#request-example-curl}

```
curl --location --request POST 'https://api.green-api.com/waInstance{{idInstance}}/sendTemplate/{{apiTokenInstance}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chatId": "11001234567@c.us",
    "namespace": "not_existing_namespace",
    "name": "not_existing_template",
    "languageCode": "ru",
    "params": [
        {"default": "Dear customer"}
    ]
}
'
```
