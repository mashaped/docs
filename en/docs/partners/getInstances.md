# GetInstances

The method is aimed for getting all the account instances created by the partner.

## Request

To get all the account instances you have to execute a GET request at:
```
https://api.green-api.com/partner/getInstances/{partnerToken}
```
>For `partnerToken`request parameter please contact Green API technical support (support@green-api.com) with a request to get a partnership API-token.

## Response

### Response parameters 

Parameter | Type |  Description
----- | ----- | ----- 
`idInstance` | **int** | account instance id
`apiTokenInstance` | **string** | account instance API token
`typeInstance` | **string** | messenger type for account instance
`timeCreated` | **string** | instance creation time

### Response body example 

If successful, in response to the request, you get a JSON string with HTTP 200 status of the below form:
```json
[
    {
        "idInstance": 1101728004,
        "name": "Instance 1101728004",
        "typeInstance": "whatsapp",
        "typeAccount": "",
        "partnerUserUiid": "",
        "timeCreated": "2022-06-03T18:39:44",
        "timeDeleted": "0001-01-01T00:00:00",
        "apiTokenInstance": "1f2485e80f474293b935f77d78c64e76fa4bdceb417a4998a4",
        "deleted": false,
        "tariff": "PARTNER_23",
        "expirationDate": "2022-06-09T18:39:44",
        "isExpired": false
    },
    {
        "idInstance": 1101728204,
        "name": "Instance 1101728204",
        "typeInstance": "whatsapp",
        "typeAccount": "",
        "partnerUserUiid": "",
        "timeCreated": "2022-06-07T10:36:48",
        "timeDeleted": "2022-06-07T10:37:00",
        "apiTokenInstance": "35d8b4907f8e494289b1d5f999e3582940ceffc413bf4a76b1",
        "deleted": true,
        "tariff": "PARTNER_23",
        "expirationDate": "2022-06-08T10:36:48",
        "isExpired": false
    },
    {
        "idInstance": 1101728478,
        "name": "Instance 1101728478",
        "typeInstance": "whatsapp",
        "typeAccount": "",
        "partnerUserUiid": "",
        "timeCreated": "2022-06-08T09:12:13",
        "timeDeleted": "2022-06-08T09:19:04",
        "apiTokenInstance": "c8b0474542154e0ead529eb3861ca5f483c346eb00564f64a7",
        "deleted": true,
        "tariff": "PARTNER_23",
        "expirationDate": "2022-06-09T09:12:13",
        "isExpired": false
    }
]
```

> To get accounts instances parameters, use the corresponing [API methods](../api/account/index.md).

In case of failure, a response with HTTP 400 status and an error text is returned.
 
