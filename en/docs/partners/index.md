# To Partners

The partnership scheme of cooperation involves deeper integration with the service and work with a larger number of instances on your side:

* API instances management

* Postpaid cooperation plan (from the second month of cooperation)

* Daily billing (for created and non-deleted instances)

* Personal support chat 

> In case of any questions in regard to the partnership scheme and additional conditions, please send us a message to support@green-api.com or chat on the website.

## Getting a partnership token

You may get a partnership API-token via support@green-api.com Green API technical support.

## Methods testing

For testing methods we recommend to use the [Postman for partners](https://github.com/green-api/partners-green-api-postman-collection) collection.

> To work with the collection, you must first get a partnership API token via support@green-api Green API technical support.
>
> Справка по [установке Postman](../postman-collection.md)

## Request format 

Обращение к API производится по адресу:
```
https://api.green-api.com/partner/{method}/{partnerToken}
```

>{method} - (string) - API method name;
>
>{partnerToken} - (string) - partner's token, you get it via Green API technical support (support@green-api.com);
 
## API methods available for partners

[createInstance](./createInstance.md) - method for creating a messanger account instance on the partner's part

[deleteInstanceAccount](./deleteInstanceAccount.md) - method for deleting a partner's account instance

[getInstances](./getInstances.md) - method returns all the accounts instances created by the partner

## Порядок работы

1. Создайте инстанс методом [createInstance](./createInstance.md)
2. Авторизуйте новый инстанс на телефоне. Для этого перейдите в [личный кабинет](https://console.green-api.com) и сканируйте QR-код.

    Дополнительно отображение QR-кода можно реализовать в интерфейсе Вашего программного продукта. Для этого рекомендуется воспользоваться примерами кода ниже:

    * Получение QR-кода через [HTTP-запрос](https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExampleQRCode.html)

    * Получение QR-кода через [web-socket](https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExampleQRCodeWebsocket.html)

    * Получение QR-кода в [1С](https://green-api.com/integrations/1c.html)

    * Также реализовано получение QR-кода на отдельной странице в Интернете: 
    ```
    https://qr.green-api.com/waInstance{idInstance}/{apiTokenInstance}
    ```
    > idInstance и apiTokenInstance могут быть получены методами [createInstance](./createInstance.md) и [getInstances](./getInstances.md).

3. Инстанс готов к работе. Для отправки и получения сообщений используйте методы API согласно [документации](../api/index.md)
