# CreateInstance

The method is aimed for creating a messenger account instance on the partner's part.

## Request

To create an account instance on the partner's part you have to execute a POST request at:
```
https://api.green-api.com/partner/createInstance/{partnerToken}
```

>For `partnerToken`request parameter please contact Green API technical support (support@green-api.com) with a request to get a partnership API-token.

### Request parameters

Selective specification of parameters is allowed. At least one parameter must be specified.

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`webhookUrl`| __string__ | optional | URL for sending webhook notifications
`webhookUrlToken` | __string__ | optional | Token for connection to your webhook server;
`delaySendMessagesMilliseconds` | __integer__ | optional | message sending delay in milliseconds, default is 3000 msec, minimum is 500 msec
`markIncomingMessagesReaded` | __string__ | optional | mark incoming messages as read or not (“yes”/”no”), default is “no”. Ignored if markIncomingMessagesReadedOnReply is “yes”
`markIncomingMessagesReadedOnReply` | __string__ | optional |  mark incoming messages as read or not (“yes”/”no”) when posting a message to the chat, default is “no” (incoming messages are not marked as read)
`outgoingWebhook` | __string__ | optional | Get notifications about outgoing messages sending/delivering/reading statuses, possible variants: “yes”, “no”. Default is “no”
`outgoingMessageWebhook` | __string__ | optional | Get notifications about messages sent from the phone, possible variants: “yes”, “no”.  Default is “no”
`stateWebhook` | __string__ | optional | Get notifications about the account authorization state change, possible variants: “yes”, “no”. Default is “no”
`incomingWebhook` | __string__ | optional | Get notifications about incoming messages and files, possible variants: “yes”, “no”. Default is “no”
`deviceWebhook` | __string__ | optional | Get notifications about the device (phone) and battery level, possible variants: “yes”, “no”. Default is “no”
`stateWebhook` | __string__ | optional | Get notifications about the account authorization state change, possible variants: “yes”, “no”. Default is “no”
`outgoingAPIMessageWebhook` | __string__ | optional | Get notifications about messages sent via API, possible variants: “yes”, “no”.  Default is “no”
`keepOnlineStatus` | __string__ | optional | Display the instance status “Online”. Possible variants: “yes”, “no”. Default is “no”. Note: If the setting is on, sound notifications about new messages will not be sent to the telephone connected to API


### Request body example

```json
{
    "webhookUrl": "https://mysite.com/webhook/green-api/",
    "webhookUrlToken": "f93537eb3e8fed66847b5bd",
    "delaySendMessagesMilliseconds": 1000,
    "markIncomingMessagesReaded": "no",
    "markIncomingMessagesReadedOnReply": "no",
    "outgoingAPIMessageWebhook": "yes",
    "outgoingWebhook": "yes",
    "outgoingMessageWebhook": "yes",
    "incomingWebhook": "yes",
    "deviceWebhook": "no",
    "stateWebhook": "no",
    "keepOnlineStatus": "no"
}
```

## Response

### Response parameters 

Parameter | Type |  Description
----- | ----- | ----- 
`idInstance` | **int** | account instance id
`apiTokenInstance` | **string** | account instance API token
`typeInstance` | **string** | messenger type for account instance

### Response bdy example 

If successful, in response to the request, you get a JSON string with HTTP 200 status of the below form:

```json
{
    "idInstance": 1101728000,
    "apiTokenInstance": "c1b0474542144e0ead529eb4861ca5f583c346eb00564f64a7",
    "typeInstance": "whatsapp"
}
```
In case of failure, you get a response with HTTP 200 status, a JSON string with a code and description of the error is returned in the response body:

```json
{
    "code": 401,
    "description": "Unauthorized"
}
```
