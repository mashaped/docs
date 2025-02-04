# UpdateGroupName

Метод изменяет наименование группового чата.

## Запрос {#request}

Для изменения наименования группового чата требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/UpdateGroupName/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

Параметр | Тип | Обязательный | Описание
----- | ----- | ----- | -----
`groupId` | **string** | Да | [Идентификатор группового чата](../chat-id.md#gus)
`groupName` | **string** | Да | Наименование группового чата

### Пример тела запроса {#request-example-body}

```json
{
    "groupId": "120363043968066561@g.us",
    "groupName": "Group created by Green API+"
}
```

## Ответ {#response}

### Поля ответа {#response-parameters}

Поле | Тип |  Описание
----- | ----- | ----- 
`updateGroupName` | **boolean** | Флаг изменения названия группы

### Пример тела ответа {#response-example-body}

```json
{
    "updateGroupName": true
}
```

### Ошибки UpdateGroupName {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/updateGroupName/{{apiTokenInstance}}"

payload = "{\r\n    \"groupId\": \"120363043968066561@g.us\",\r\n    \"groupName\":\"Group created by Green API\"\r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```