# How to send a text message from a browser
### Installation
```
<script type="text/javascript" src="https://unpkg.com/@green-api/whatsapp-api-client/lib/whatsapp-api-client.min.js"></script>
```
### Import 
Using the browser javascript 
```
<script src="https://unpkg.com/@green-api/whatsapp-api-client/lib/whatsapp-api-client.min.js"></script>
```
#### How to initialize an object

Store your authorization data separate from the code. The library allows you to create a file with an arbitrary name and location in the following format: 
```
API_TOKEN_INSTANCE = "MY_API_TOKEN_INSTANCE"
ID_INSTANCE = "MY_ID_INSTANCE"
```
You can pass the keys using the below example:
``` js
const restAPI = whatsAppClient.restAPI(({
    credentialsPath: "examples\\credentials"
}))
```
### Examples

A complex example of sending messages and getting notifications from a browser| [browserExample.html](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/browserExample.html)

#### How to send a text message to a WhatsApp number

Using  js script
``` 
<script src="https://unpkg.com/@green-api/whatsapp-api-client/lib/whatsapp-api-client.min.js"></script>
<script>
    const restAPI = whatsAppClient.restAPI(({
        idInstance: "YOUR_ID_INSTANCE",
        apiTokenInstance: "YOUR_API_TOKEN_INSTANCE"
    }))
    restAPI.message.sendMessage("79999999999@c.us", null, "hello world")
    .then((data) => {
        console.log(data);
    }).catch((reason) =>{
        console.error(reason);
    });
</script>
```
### The full list of examples

Description |  Module
----- | ----- 
Complex example of sending messages and getting notifications from a browser| [browserExample.html](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/browserExample.html)
Example of getting a QR code via HTTP | [browserExampleQRCode.html](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/browserExampleQRCode.html)
Example of getting a QR code via websocket| [browserExampleQRCodeWebsocket.html](https://github.com/green-api/whatsapp-api-client-js/blob/master/examples/browserExampleQRCodeWebsocket.html)
