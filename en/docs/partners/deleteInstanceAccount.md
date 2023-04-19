# DeleteInstanceAccount

The method is aimed for deleting an instance of the partners's account.

## Request

To delete an instance on the partner's part you have to execute a POST request at:
```
https://api.green-api.com/partner/deleteInstanceAccount/{partnerToken}
```
>For `partnerToken`request parameter please contact Green API technical support (support@green-api.com) with a request to get a partnership API-token.

### Request parameters

Parameter | Type | Mandatory | Description
----- | ----- | ----- | -----
`idInstance` | __int__ | обязательный параметр | идентификатор инстанса аккаунта

### Request body example

```json
{
    "idInstance": 1101000000
}
```

## Response 

### Response parameters 

Поле | Тип |  Описание
----- | ----- | ----- 
`deleteInstanceAccount` | __boolean__ |флаг удаления инстанса аккаунта

### Response body example 

В случае успеха, в ответ на запрос, отдается JSON строка следующего вида с HTTP статусом 200:

```json
{
    "deleteInstanceAccount": true
}
```

В случае неудачи, отдается ответ с HTTP статусом 200, в теле ответа отдается JSON строка с кодом и описанием ошибки:

```json
{
    "code": 401,
    "description": "Unauthorized"
}
```
