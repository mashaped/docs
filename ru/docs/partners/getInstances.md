# GetInstances

Метод предназначен для получения всех инстансов аккаунтов созданных партнером.

## Запрос

Для получения всех инстансов аккаунта требуется выполнить GET запрос по адресу:
```
https://api.green-api.com/partner/getInstances/{partnerToken}
```
>Получение параметра запроса `partnerToken` происходит через техподдержку Green API (support@green-api.com) с запросом получить API-ключ партнера.

## Ответ 

### Поля ответа 

Поле | Тип |  Описание
----- | ----- | ----- 
`idInstance` | **int** | идентификатор инстанса аккаунта
`apiTokenInstance` | **string** | токен API инстанса аккаунта
`typeInstance` | **string** | тип мессенджера для инстанса аккаунта
`timeCreated` | **string** | время создания инстанса

### Пример тела ответа 

В случае успеха, в ответ на запрос, отдается JSON строка следующего вида с HTTP статусом 200:
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

> Для получения параметров инстансов аккаунтов, используются соответствующие [методы API](../api/account/index.md).

В случае неудачи, отдается ответ с HTTP статусом 400 и текстом ошибки.
 