# 1C WhatsApp processing model

[1C processing model](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf) for integration of 1С with WhatsAPP messenger via API of [green-api.com](https://green-api.com) service. You can also use [configuration sources in xml download format](https://github.com/green-api/whatsapp-api-client-1c). To use the library you have to get a registration token and an account id in the [personal area](https://console.green-api.com). There is a free developer account tariff plan.

#### Download a processing model

You can download a processing model here [![Скачать](../../assets/button_download.svg)](https://github.com/green-api/whatsapp-1c-example/releases/download/1.0/GreenAPI.epf)

After starting the processing model in 1C, you will have to enter the instance ID and authorization token

![`Скриншот`](https://github.com/green-api/whatsapp-api-client-1c/blob/master/media/Screenshort.png?raw=true)

#### Requirements
1С platform not lower than 8.3.10 version

#### API

You can find REST API documentation by [url](https://green-api.com/docs/api/). The library is a wrapper for REST API, so the documentation at the above url applies to the library as well.

#### Authorization

To send a message or to execute some other Green-API method, you have to have the WhatsApp account in the phone application to be authorized. To authorize your account please go to the [personal area](https://console.green-api.com) and scan a QR-code using the WhatsApp application.

#### [How to send a text message](sendmessage.md)
#### [How to send a text message to a group](sendmessagegroup.md)
#### [How to receive a message](receivenotification.md)

#### Service methods documentation

[Service methods documentation](https://green-api.com/docs/api/)

#### Installation of a processing model from sources

The sources in the repository are xml downloads from the 1C configurator of 8.3.16 version in the compatibility mode with 8.3.10 version. Download the sources from the repository and upload them into the configurator using the command Configuration -> Upload configuration from files

#### License

Licensed under MIT terms. Please see file [LICENSE](https://github.com/green-api/whatsapp-api-client-1c/blob/master/LICENSE)
