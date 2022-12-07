# Работа с методами партнеров

## Тестирование методов

Для проверки методов рекомендуем использовать коллекцию [Postman для партнеров.](https://github.com/green-api/partners-green-api-postman-collection)

> Для работы с коллекцией требуется предварительно получить API-ключ партнера через техподдержку Green API (support@green-api.com).
>
> Справка по [установке Postman](../postman-collection.md)

## Формат запроса 

Обращение к API производится по адресу:
```
https://api.green-api.com/partner/{method}/{partnerToken}
```

>{method} - (string) - название метода API;
>
>{partnerToken} - (string) - токен партнера, получается отдельно через техподдержку Green API (support@green-api.com);
 
## Доступные методы API для партнеров

[createInstance](./createInstance.md) - метод создания инстанса аккаунта мессенджера от имени партнера

[deleteInstanceAccount](./deleteInstanceAccount.md) - метод удаляет инстанс аккаунта партнера

[getInstances](./getInstances.md) - метод возвращает все инстансы аккаунтов созданных партнером

## Порядок работы

1. Создайте инстанс методом [createInstance](./createInstance.md)
2. Авторизуйте новый инстанс на телефоне. Для этого перейдите в [личный кабинет](https://console.green-api.com) и сканируйте QR-код.

    Дополнительно отображение QR-кода можно реализовать в интерфейсе Вашего программного продукта. Для этого рекомендуется воспользоваться примерами кода ниже:

    * Получение QR-кода через HTTP-запрос: 
    ```
    https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExampleQRCode.html
    ```

    * Получение QR-кода через web-socket: 
    ```
    https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExampleQRCodeWebsocket.html
    ```

    * Получение QR-кода в 1С: 
    ```
    https://green-api.com/integrations/1c.html
    ```

    * Также реализовано получение QR-кода на отдельной странице в Интернете: 
    ```
    https://qr.sw.slonbook.com/waInstance{idInstance}/{apiTokenInstance}
    ```
    > idInstance и apiTokenInstance могут быть получены методами [createInstance](./createInstance.md) и [getInstances](./getInstances.md).

3. Инстанс готов к работе. Для отправки и получения сообщений используйте методы API согласно [документации](../api/index.md)
