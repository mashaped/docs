# Получение уведомлений через HTTP API

Получать входящие уведомления (сообщения, статусы) можно через HTTP API запросы по аналогии, как реализованы остальные методы Green API. При этом гарантируется хронологический порядок следования уведомлений в той последовательности, в которой они были получены [FIFO](https://ru.wikipedia.org/wiki/FIFO). Все входящие уведомления сохраняются в очереди и ожидают своего получения в течение 24 часов.

Для получения входящих уведомлений требуется выполнить последовательно вызов двух методов [ReceiveNotification](technology-http-api/ReceiveNotification.md) и [DeleteNotification](technology-http-api/DeleteNotification.md). Метод [ReceiveNotification](technology-http-api/ReceiveNotification.md) выполняет получение входящего уведомления. Метод [DeleteNotification](technology-http-api/DeleteNotification.md) подтверждает успешное получение и обработку уведомления. Подробнее о методах смотрите в соответствующих разделах [ReceiveNotification](technology-http-api/ReceiveNotification.md) и [DeleteNotification](technology-http-api/DeleteNotification.md).

> Срок хранения входящих уведомлений составляет 24 часа.

## Видеоинструкция

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/5HmhPCbzFgg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</center>

## Настройка аккаунта

Перед получением входящих уведомлений требуется выполнить настройку аккаунта. Настройка аккаунта может быть выполнена [программно](#SetSettings) с использованием метода [SetSettings](../account/SetSettings.md), либо [интерактивно](#cabinet) в интерфейсе личного кабинета.

### Настройка методом [SetSettings](../account/SetSettings.md) {#SetSettings}

Для настройки получения входящих уведомлений по технологии HTTP API требуется оставить пустым параметр `webhookUrl`.

Также требуется указать какие виды уведомлений необходимо получать. Для включения входящих уведомлений по видам, а также для указания параметра `webhookUrl` воспользуйтесь методом [SetSettings](../account/SetSettings.md).

#### Пример тела запроса метода [SetSettings](../account/SetSettings.md)

```json
{
    "webhookUrl": "",
    "outgoingWebhook": "yes",
    "stateWebhook": "yes",
    "incomingWebhook": "yes"
}
```

### Настройка в личном кабинете {#cabinet}

Настройку получения входящих уведомлений можно также выполнить интерактивно. Для этого перейдите в [Личный кабинет](https://console.green-api.com) и выберите требуемый аккаунт. Будут отображены текущее состояние инстанса и настройки для получения входящих уведомлений. Что бы поменять настройки необходимо нажать кнопку изменить на панеле инстанса. Текущие настройки можно будет поменять на панеле уведомлений см. рис. Укажите значение параметра `webhookUrl`, а также переключатели по видам уведомлений. Нажмите на кнопку "Сохранить изменения" для применения настроек.

![Настройки входящих уведомлений](../../assets/technology-http-api.png "Настройки входящих уведомлений")

## Получение входящих уведомлений

После выполнения настройки аккаунта можно приступать к получению уведомлений методами [ReceiveNotification](technology-http-api/ReceiveNotification.md) и [DeleteNotification](technology-http-api/DeleteNotification.md). Пример кода получения уведомлений на [NodeJS](https://nodejs.org) можно посмотреть в файле [ReceiveNotifications](https://github.com/green-api/whatsapp-api-client/blob/master/examples/ReceiveNotifications.js).

Подробное описание формата входящих уведомлений представлено в разделе [Формат входящих уведомлений](notifications-format/index.md).