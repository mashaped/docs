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
`idInstance` | __int__ | mandatory parameter | account instance id

### Request body example

```json
{
    "idInstance": 1101000000
}
```

## Response 

### Response parameters 

Parameter | Type |  Description
----- | ----- | ----- 
`deleteInstanceAccount` | __boolean__ |account instance deletion flag

### Response body example 

If successful, in response to the request, you get a JSON string with HTTP 200 status of the below form:

```json
{
    "deleteInstanceAccount": true
}
```

In case of failure, you get a response with HTTP 200 status 200, a JSON string with a code and description of the error is returned in the response body:

```json
{
    "code": 401,
    "description": "Unauthorized"
}
```
