# ForwardMessages

Метод предназначен для пересылки сообщений в личный или групповой чат.
Пересылаемое сообщение будет добавлено в очередь на отправку. Сообщение на отправку хранится 24 часа в очереди и будет отправлено сразу же после авторизации телефона. 
Скорость отправки сообщений из очереди регулирует параметр [Интервал отправки сообщений](../send-messages-delay.md).

## Запрос {#request}

Для отправки требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/forwardMessages/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

| Параметр          | Тип               | Обязательный | Описание                                                               |
|-------------------|-------------------|--------------|------------------------------------------------------------------------|
| `chatId`          | **string**        | Да           | [Идентификатор чата](../chat-id.md), с которого пересылается сообщение |
| `chatIdFrom`      | **string**        | Да           | [Идентификатор чата](../chat-id.md), куда пересылается сообщение       |
| `messages`        | **array<string>** | Да           | Коллекция идентификаторов пересылаемых сообщений                       |

### Пример тела запроса {#request-example-body}

Отправка сообщения в чат:
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

## Ответ {#response}

### Поля ответа {#response-parameters}

| Поле       | Тип               | Описание                              |
|------------|-------------------|---------------------------------------|
| `messages` | **array<string>** | Идентификаторы отправленных сообщений |

### Пример тела ответа {#response-example-body}

```json
{
  "messages": [
    "BAE5DBB8DEABDA22",
    "BAE5BBA9BE3142D8"
  ]
}
```
### Пример отображения у получателя {#recieve-example}

![Пример пересланного сообщения](../../assets/forward-message.jpg 'Пример пересланного сообщения')

### Ошибки ForwardMessages {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

## Пример curl

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