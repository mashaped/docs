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

Request to API should be executed at:
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

## Work order

1. Create an instance by [createInstance](./createInstance.md) method
2. Authorize a new instance on your phone. To do this go to your [personal area](https://console.green-api.com) and scan a QR-code.

    Additionally, the display of a QR code can be implemented in the interface of your software product. To do this, it is recommended to use the code examples below:

    * Getting a QR-code through [HTTP-request](https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExampleQRCode.html)

    * Getting a QR-code via [web-socket](https://github.com/green-api/whatsapp-api-client/blob/master/examples/browserExampleQRCodeWebsocket.html)

    * Getting a QR-code in [1С](https://green-api.com/integrations/1c.html)

    * Также реализовано получение QR-кода на отдельной странице в Интернете: 
    ```
    https://qr.green-api.com/waInstance{idInstance}/{apiTokenInstance}
    ```
    > idInstance and apiTokenInstance may be obtained by the [createInstance](./createInstance.md) and [getInstances](./getInstances.md) methods.

3. The instance is ready for work. To send and get messages use API methods according to [documentation](../api/index.md)
