# Идентификатор чата и корреспондента

В Green&nbsp;API поддерживается два вида чатов - [личный чат](#cus) и [групповой чат](#gus).
Личный чат используется для отправки персональных сообщений получателю. Групповой чат используется для организации общения нескольких участников в одной группе. Для работы с групповыми чатами в Green&nbsp;API предусмотрены соответствующие методы. 
Перед отправкой сообщения в личный или групповой чат требуется получить идентификатор чата.

## Идентификатор корреспондента {#corr}
Идентификатор корреспондента используется для идентификации получателя в исходящих сообщениях и для идентификации отправителя во входящих сообщениях, а также в любых других методах API, в которых требуется идентифицировать корреспондента. Формат идентификатора корреспондента совпадает с идентификатором [личного чата](#cus).

## Личный чат {#cus}
Формат идентификатора личного чата формирутся по шаблону `00000000000@c.us`, где вместо нулей `00000000000` требуется использовать номер телефона получателя. Телефон следует указывать полностью, с кодом страны и без пробелов. Например:

```
11001234567@c.us
```

## Групповой чат {#gus}
Идентификатор группового чата представляет собой строку вида `00000000000-XXXXXXXXXX@g.us` или `XXXXXXXXXXXXXXXXX@g.us`. Например:

```
11001234567-1581234048@g.us
120363043968066561@g.us
```

Идентификатор группового чата может быть получен различными методами Green&nbsp;API, например:

- [Создать группу](groups/CreateGroup.md)
- [Получить журнал отправленных сообщений](journals/LastOutgoingMessages.md)
- [Получить журнал входящих сообщений](journals/LastIncomingMessages.md)
- [Входящее сообщение: Текст](receiving/notifications-format/incoming-message/TextMessage.md)
- и др.

> **Важно**
>
> Идентификатор группового чата **НЕ требуется** формировать самостоятельно. Он формируется системой автоматически и возвращается различными методами Green&nbsp;API.
