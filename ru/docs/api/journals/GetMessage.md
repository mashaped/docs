# GetMessage

Метод возвращает сообщение чата.

## Запрос {#request}

Для получения сообщения требуется выполнить запрос по адресу:
```
POST https://api.green-api.com/waInstance{{idInstance}}/getMessage/{{apiTokenInstance}}
```

Для получения параметров запроса `idInstance` и `apiTokenInstance` обратитесь к разделу [Перед началом работы](../../before-start.md#parameters).

### Параметры запроса {#request-parameters}

| Параметр    | Тип        | Обязательный | Описание                                                                                          |
|-------------|------------|--------------|---------------------------------------------------------------------------------------------------|
| `chatId`    | **string** | Да           | [Идентификатор личного или группового чата](../chat-id.md), сообщение которого требуется получить |
| `idMessage` | **string** | Да           | ID сообщения                                                                                      |

### Пример тела запроса {#request-example-body}

Запрос сообщения:
```json
{
  "chatId": "120363043968066561@g.us",
  "idMessage": "BAE5F4886F6F2D05"
}
```

## Ответ {#response}

Ответ содержит полученное или отправленное сообщение в чате.

### Поля ответа {#response-parameters}

Объект с полями:

| Поле                  | Тип                                                        | Описание                                                                                                        |
|-----------------------|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `idMessage`           | **string**                                                 | Идентификатор входящего сообщения                                                                               |
| `timestamp`           | **integer**                                                | Время принятия сообщения в UNIX-формате                                                                         |
| `typeMessage`         | **string**                                                 | Тип сообщения, возможные значения:                                                                              |
|                       | `textMessage` - текстовое сообщение                        |                                                                                                                 |
|                       | `imageMessage` - сообщение с изображением                  |                                                                                                                 |
|                       | `videoMessage` - видео сообщение                           |                                                                                                                 |
|                       | `documentMessage` - сообщение с файлом документа           |                                                                                                                 |
|                       | `audioMessage` - аудио сообщение                           |                                                                                                                 |
|                       | `locationMessage` - сообщение геолокации                   |                                                                                                                 |
|                       | `contactMessage` - сообщение с контактом                   |                                                                                                                 |
|                       | `extendedTextMessage` - сообщение со ссылкой и превью      |                                                                                                                 |
|                       | `quotedMessage` - сообщение с цитированием (УСТАРЕЛО)      |                                                                                                                 |
|                       | `buttonsMessage` - сообщение с кнопками                    |                                                                                                                 |
|                       | `templateMessage` - сообщение с шаблонными кнопками        |                                                                                                                 |
|                       | `listMessage` - сообщение с кнопкой со списком             |                                                                                                                 |
|                       | `buttonsResponseMessage` - ответ с кнопками                |                                                                                                                 |
|                       | `templateButtonsReplyMessage` - ответ с фигурными кнопками |                                                                                                                 |
|                       | `listResponseMessage` - ответ со списком                   |                                                                                                                 |
| `chatId`              | **string**                                                 | [Идентификатор чата](../chat-id.md), в котором получено сообщение                                               |
| `senderId`            | **string**                                                 | [Идентификатор](../chat-id.md#corr) отправителя сообщения                                                       |
| `senderName`          | **string**                                                 | Имя отправителя сообщения                                                                                       |
| `textMessage`         | **string**                                                 | Текст сообщения, если `typeMessage`=`textMessage`                                                               |
| `downloadUrl`         | **string**                                                 | Ссылка на скачивание файла, если `typeMessage` = `imageMessage`/`videoMessage`/`documentMessage`/`audioMessage` |
| `caption`             | **string**                                                 | Описание файла                                                                                                  |
| `location`            | **object**                                                 | Объект о структуре локации                                                                                      |
| `contact`             | **object**                                                 | Объект о структуре контакта                                                                                     |
| `extendedTextMessage` | **object**                                                 | Объект с текстовым сообщением (расширенный)                                                                     |
| `quotedMessage`       | **object**                                                 | Объект данных о цитируемом сообщении. Присутствует только, если само сообщение является цитатой                 |

Поля объекта `location`:

| Поле            | Тип        | Описание                                |
|-----------------|------------|-----------------------------------------|
| `nameLocation`  | **string** | Название локации                        |
| `address`       | **string** | Адрес локации                           |
| `latitude`      | **double** | Широта локации                          |
| `longitude`     | **double** | Долгота локации                         |
| `jpegThumbnail` | **string** | Превью изображения в `base64` кодировке |

Поля объекта `contact`:

| Поле          | Тип        | Описание                                     |
|---------------|------------|----------------------------------------------|
| `displayName` | **string** | Отображаемое имя контакта                    |
| `vcard`       | **string** | Структура VCard (визитной карточки контакта) |

Поля объекта `extendedTextMessage`:

| Поле            | Тип        | Описание                                |
|-----------------|------------|-----------------------------------------|
| `text`          | **string** | Текст ссылки                            |
| `description`   | **string** | Описание ссылки                         |
| `title`         | **string** | Заголовок ссылки                        |
| `previewType`   | **string** | Тип превью ссылки                       |
| `jpegThumbnail` | **string** | Превью изображения в `base64` кодировке |
| `stanzaId`      | **string** | ID цитируемого сообщения                |
| `participant`   | **string** | ID чата получателя                      |

### Пример тела ответа {#response-example-body}

```json
    {
        "idMessage": "DE8CFFA93B95237B077F8FA08331A0B5",
        "timestamp": 1587129319,
        "typeMessage": "textMessage",
        "chatId": "11001234567@c.us",
        "senderId": "11001234567@c.us",
        "senderName": "Николай",
        "textMessage": "Привет"
    }
```
```json
    {
        "idMessage": "EA0BD1AE042DC4F3609867126309D67C",
        "timestamp": 1587147598,
        "typeMessage": "imageMessage",
        "chatId": "11001234567@c.us",
        "senderId": "11001234567@c.us",
        "senderName": "Николай",
        "downloadUrl": "https://api.green-api.com/waInstance1234/downloadFile/EA1BD1AE042DC4F3609867126309D67C",
        "caption": "Как тебе?"
    }
```
```json
    {
        "idMessage": "DE8CFFA93B95237B077F8FA08331A0B5",
        "timestamp": 1587129319,
        "typeMessage": "locationMessage",
        "chatId": "71234567891@c.us",
        "senderId": "1234567891@c.us",
        "senderName": "Николай",
        "location": {
            "nameLocation": "Я здесь, приезжай",
    	    "address": "614111, Perm",
            "latitude": 53.9370129,
            "longitude": 54.8728409,
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wB=="
        }
    }
```
```json
    {
        "idMessage": "DE8CFFA93B95237B077F8FA08331A0B5",
        "timestamp": 1587129319,
        "typeMessage": "contactMessage",
        "chatId": "1234567891@c.us",
        "senderId": "71234567891@c.us",
        "senderName": "Николай",
        "contact": {
            "displayName": "Виктор Петров",
    	    "vcard": "BEGIN:VCARD\nVERSION:3.0\nN:Андреевич;Виктор;;;\nFN:Виктор Андреевич\nORG:Image\nTITLE:\nitem1.TEL;waid=79099291652:+7 123 456-78-91\nitem1.X-ABLabel:Мобильный\nEND:VCARD"
        }
    }
```
```json
    {
        "idMessage": "DE8CFFA93B95237B077F8FA08331A0B5", 
        "timestamp": 1587129319,
        "typeMessage": "extendedTextMessage",
        "chatId": "1234567891@c.us",
        "senderId": "71234567891@c.us",
        "senderName": "Николай",
        "extendedTextMessage": {
            "text": "https://www.youtube.com/watch?v=9lO06Zxhu8*8*",
    	    "description": "Ролик",
            "title": "Офигенный ролик",
            "previewType": "video",
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wB=="
        }
    }
```
```json
    {
        "idMessage": "6195B3523153621DFDFC184D3317E80D",
        "timestamp": 1603182280,
        "typeMessage": "quotedMessage",
        "chatId": "71234567891@c.us",
        "senderId": "71234567891@c.us",
        "senderName": "Мой",
        "textMessage": "Цитата тест",
        "extendedTextMessage": {
            "stanzaId": "3A6424373F90A939B3C8",
            "participant": "71987654321@c.us"
        }
    }
```

### Ошибки GetMessage {#errors}

Перечень общих для всех методов ошибок смотрите в разделе [Стандартные ошибки](../common-errors.md)

| Код HTTP | Идентификатор ошибки  | Описание             |
|----------|-----------------------|----------------------|
| 400      | `chatId not found`    | chatID не найдено    |
| 400      | `ID message notfound` | IDMessage не найдено |

## Пример кода на Python  {#request-example-python}

```python
import requests

url = "https://api.green-api.com/waInstance{{idInstance}}/getMessage/{{apiTokenInstance}}"

payload = "{\r\n\"chatId\": \"120363043968066561@g.us\, \"idMessage\": \"BAE5F4886F6F2D05\" \"r\n}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```
